.. title:: Nutanix 101 TH

.. toctree::
  :maxdepth: 2
  :caption: Contents:
  :hidden:

  pe
  dsf
  config_network
  deploy_workload
  workload_manage
  data_protection
  key_take


.. _getting_started:

#############
ยินดีต้อนรับสู่ 
#############
#################################
Nutanix 101's Honds-On Workshop
#################################

Overview
========

ใน Lab นี้จะเป็นการอธิบายและแนะนำการใช้งานในส่วนต่างๆของ Prism Element รวมไปถึงแนะนำการดูแลระบบ ไม่ว่าจะเป็น Storage,  Networking, การสร้าง VM บน AHV และการบริหารจัดการด้วย Prism 
นอกจากนั้นยังมีแนะนำการใช้งาน Data Protection รวมไปถึงการทำ Snapshots และ Replication

What's New
==========

ปัจจุบัน Nutanix AOS version 5.18.X แต่เนื่องจาก Labs ชุดนี้ถูกจัดทำขึ้นใน Nutanix AOS Version 5.11.X ดังนั้นอาจจะมีภาพ, เสียง และ เนื้อหาที่ไม่ตรงกับ Version ปัจจุบันที่ใช้ใน Labs จริง จึงต้องขออภัยไว้ ณ.ที่นี้ด้วย

Agenda
======

- Nutanix 101 Labs
    - Prism Element
    - Distributed Storage Fabric
    - Configuring Virtual Networks
    - Deploying Workloads
    - Workload Management
    - Data Protection

Introductions
=============

- Name
- Familiarity with Nutanix

Initial Setup
=============

Nutanix Workshops ใช้งานอยู่บน Nutanix Hosted POC environment. เราได้เตรียมสิ่งที่จำเป็นต้องใช้ใน Labs ไว้ให้แล้วเช่น images, networks, และ VMs.

- Take note of the *Passwords* being used.
- VPN to Nutanix Labs ด้วยข้อมูลประกอบด้านล่าง
- ผู้เรียนจะถูกแบ่งออกเป็น 3 กลุ่ม จำนวนเท่าๆ กัน

.. raw:: html

  <strong><font color="red">- **ห้าม ทำการใดๆ กับ VMs, Images, Network ใดๆ ที่ไม่ใช่สิ่งที่ผู้เรียนคนนั้นๆ สร้างใน Labs นี้</font></strong>

|

.. note::
  ภายใน Labs นี้ จะมีการยกตัวอย่างด้วย *XYZ* หรือ *Initial* อยู่บ่อยครั้ง ดังนั้นให้ผู้เรียนสังเกตุ และเปลี่ยนตัวอย่างดังกล่าวให้เป็นชื่อของผู้เรียนเอง หรือเป็น User#No. ที่ได้รับมอบหมาย

|

VPN Access Instructions
=======================

Pulse Secure VPN Client
-----------------------

#. หากผู้เรียนที่ใช้งาน Pulse Secure VPN อยู่แล้ว ให้ข้ามไปที่ขั้นตอนที่ 5
#. ไป download client เพื่อติดตั้งได้ที่:
  - Direct Download
     - `Windows 32 bit <https://noc.rmutp.ac.th/wp-content/uploads/32bitinstaller.msi>`_
     - `Windows 64 bit <https://noc.rmutp.ac.th/wp-content/uploads/64bitinstaller.msi>`_
     - `Mac OS <https://noc.rmutp.ac.th/wp-content/uploads/macinstaller.dmg>`_

#. Download and install client
#. Logout of the Web UI
#. เปิด client แล้ว ADD connection ตามข้อมูลต่อไปนี้:\
    - **Type:** Policy Secure (UAC) or Connection Server(VPN)\
    - **Name:** X-Labs - BLR
    - **Server URL:** xlv-blr.xlabs.nutanix.com\

#. Once setup, login with the supplied credentials

.. list-table::
  :widths: 50 50
  :header-rows: 1

  * - UserName
    - RTP-POC016-User01, RTP-POC016-User02, ..., BRTP-POC016-User20
  * - Password
    - ntnxTech43@!


.. _environment:

Environment Details
===================

Nutanix Workshops ใช้งานอยู่บน Nutanix Hosted POC environment. เราได้เตรียมสิ่งที่จำเป็นต้องใช้ใน Labs ไว้ให้แล้วเช่น images, networks, และ VMs.

.. list-table::
  :widths: 50 50
  :header-rows: 1

  * - Cluster Name
    - RTP-POC016
  * - Cluster IP
    - http://10.55.16.37
  * - Prism Central IP
    - http://10.55.16.39
  * - PE/PC Username
    - admin
  * - PE/PC Password
    - ntnxTech43@!
  * - CVM Username
    - nutanix
  * - CVM Password
    - ntnxTech43@!


Each cluster has a dedicated domain controller VM, **DC**, responsible for providing AD services for the **NTNXLAB.local** domain. The domain is populated with the following Users and Groups:

.. list-table::
  :widths: 25 35 40
  :header-rows: 1

  * - Group
    - Username(s)
    - Password
  * - Administrators
    - Administrator
    - nutanix/4u
  * - SSP Admins
    - adminuser01-adminuser25
    - nutanix/4u
  * - SSP Developers
    - devuser01-devuser25
    - nutanix/4u
  * - SSP Operators
    - operator01-operator25
    - nutanix/4u
  * - SSP Consumers
    - consumer01-consumer25
    - nutanix/4u
  * - SSP Custom
    - custom01-custom25
    - nutanix/4u