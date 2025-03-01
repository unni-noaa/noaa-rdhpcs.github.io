.. _globus_example:

**************
Globus Example
**************

Globus is the preferred and most efficient and robust way to transfer data between Globus Collections and Endpoints (also known as DTNs) and external storage systems. To use this service, you must have an RDHPCS NOAA account and an RSA SecureID token. You can invoke Globus functions either through a web interface or from a command line interface (CLI).  Click here to access `Globus Documentation <https://docs.globus.org/guides/>`_. 

The following is an example for the purpose of illustration, provided for people  who need to get data moving from source to destination without delay. 

What you need to have on hand
-----------------------------

+-------------------------------------------------------+-----------------------------+
| **The name and source of the destination endpoints**  | noaardhpcs#ppan_untrusted   |
|                                                       | noaardhpcs#hera             |
+-------------------------------------------------------+-----------------------------+
| **Your NOAA username**                                | Robin.Lee                   |
+-------------------------------------------------------+-----------------------------+
| **The names of filesystems exposed by the endpoints** | /collab1/data_untrusted/    |
|                                                       | /scratch1/                  |              
+-------------------------------------------------------+-----------------------------+

What you need to do
-------------------

+---------------------------------------------------------------------------+---------------------------------------+
| **1. Navigate your browser to this address**                              | https://app.globus.org                |
+---------------------------------------------------------------------------+---------------------------------------+
| **2. Login with "existing organizational login"**                         | NOAA RDHPCS                           |
+---------------------------------------------------------------------------+---------------------------------------+
| **3. In the Globus File Manager, select Collection**                      | noaardhpcs#ppan_untrusted             |
+---------------------------------------------------------------------------+---------------------------------------+
| **If necessary, authenticate with your username and password**            |                                       |
+---------------------------------------------------------------------------+---------------------------------------+
| **4. In the File Manager, select Path**                                   | /collab1/data_untrusted/Robin.Lee/... |
+---------------------------------------------------------------------------+---------------------------------------+
| **5. Repeat for second endpoint**                                         | noaardhpcs#hera/scratch1/NCEPDEV/...  |
+---------------------------------------------------------------------------+---------------------------------------+
| **6. Select the files/directories you want to transfer, and click Start** |                                       |
+---------------------------------------------------------------------------+---------------------------------------+

Using Globus Online Data Transfer
=================================

An endpoint is a file transfer location (computer/server) accessible to Globus. A collection is a server with a related access method to files. Untrusted collections can transfer data to and from anywhere. Trusted collections can transfer data to and from other trusted collections. When you log into Globus and click Collections, you can see what collections are shared with you, and also those that you share with others. Globus lets you navigate through collections to find source and target endpoints for your transfer, then select directories or files to be transferred. The transfer itself is a background process.

To copy a file, several files, or an entire directory between two systems, navigate to Globus. Locate the source and target endpoints by their given names and follow these steps:

#. Authenticate yourself to both endpoints.
#. Select the Directory Listing panel for each Endpoint.
#. Pick a directory in each panel for your source and destination.
#. Click START to initiate the transfer.

**For Example**

#. Navigate to globus.org.
#. Select “existing organizational login” NOAA RDHPCS. The File Manager page displays.
#. Select Collection, and choose the file system “noaardhpcs#ppan_untrusted”. If necessary, authenticate with username and RSA password.
#. In the File Manager, select Path: /collab1/data_untrusted/anonymous/from Orion
#. Repeat for the other endpoint: msuhpc2#Orion-dtn
#. Select files and directories, and click Start.

Globus Connect Service is available on the following RDHPCS and partner clusters:

**RDHPCS clusters with GCS**

+-------------------+------------------------------+----------------------------+-----------------------+-------------------+
| Cluster           | Display Name                 |File Systems                |Site                   | Access            |
+===================+==============================+============================+=======================+===================+
| Hera              | noaardhpcs#hera              | /scratch1/, /scratch2/     | NESCC                 | trusted hosts     |
+-------------------+------------------------------+----------------------------+-----------------------+-------------------+
| Jet               | noaardhpcs#jet               | /mnt/lfs4, /mnt/lfs5       | GSL                   | trusted hosts     |
+-------------------+------------------------------+----------------------------+-----------------------+-------------------+
| Jet               | noaardhpcs#jet_untrusted     | /mnt/lfs4/data_untrusted   | GSL                   | anywhere          |
+-------------------+------------------------------+----------------------------+-----------------------+-------------------+
| Niagara           | noaardhpcs#niagara           | /collab1/data              | NESCC                 | trusted hosts     |
+-------------------+------------------------------+----------------------------+-----------------------+-------------------+
| Niagara           | noaardhpcs#niagara_untrusted | /collab1/data_untrusted    | NESCC                 | anywhere          |
+-------------------+------------------------------+----------------------------+-----------------------+-------------------+
| PPAN              | noaardhpcs#ppan_rdtn         | /archive, /home/, /nbhome, | GFDL                  | trusted hosts     |
+-------------------+------------------------------+----------------------------+-----------------------+-------------------+
|                   |                              | /work, /ptmp               |                       |                   |
+-------------------+------------------------------+----------------------------+-----------------------+-------------------+
| PPAN              | noaardhpcs#ppan_untrusted    | /collab1/data_untrusted    | GFDL                  | anywhere          |
+-------------------+------------------------------+----------------------------+-----------------------+-------------------+
| Gaea              | ncrc#dtn                     | /lustre/f2/scratch         | NCRC                  | trusted hosts     |
+-------------------+------------------------------+----------------------------+-----------------------+-------------------+
| Orion             | Msuhpc2#Orion-dtn            | /work, /work2              | Orion DTN at MSU      | anywhere          |
+-------------------+------------------------------+----------------------------+-----------------------+-------------------+
| Hercules          | msuhpc2#Hercules             | /work, /work2              | Hercules DTN at MSU   | anywhere          |
+-------------------+------------------------------+----------------------------+-----------------------+-------------------+


**RDHPCS Object Stores in the Cloud**

+-------------------------------------------+---------------------------------+
| Endpoint/Collection                       | Description                     |
+===========================================+=================================+
| noaardhpcs#cloud_aws_rdhpcs_projects      | AWS Cloud RDHPCS endpoint       |
+-------------------------------------------+---------------------------------+
| noaardhpcs#cloud_azure_rdhpcs_projects    | Azure Cloud RDHPCS endpoint     |
+-------------------------------------------+---------------------------------+
| noaardhpcs#cloud_gcp_rdhpcs_projects      | Google Cloud RDHPCS endpoint    |
+-------------------------------------------+---------------------------------+

NOAA RDHPCS Globus Endpoint Types
=================================

NOAA RDHPCS Globus Endpoints are either ‘’trusted’’ or ‘’untrusted’’. 

* All RDHPCS systems provide DTN’s
* DTNs have full access to the back-end file systems.
* DTNs only accept connections from pre-authorized sites. If your site can’t access the DTNs and you need that capability, submit a help desk ticket. If the security team approves, your site will be pre-authorized.

.. note::

    It is preferable to use trusted endpoints for data transfer whenever possible.

NOAA RDHPCS UDTN’s (Globus Untrusted Endpoint)
==============================================

UDTNs can accept connections and transfer data to and from any location. UDTNs have access to a specific directory of the back-end file system, where files can be staged solely for the purpose of transferring data.
Since your project space is not accessible from the UTDN, transferring data to and from RDHPCS systems using the UDTN’s is a two-step process.

#. Copy the data out of your project space to the staging area and then pull data out of the UDTN from the remote machine.
#. To transfer data back to the RDHPCS system, push the data to the UDTN, then copy the file(s) from the staging area to your project space.

NOAA RDHPCS Object Stores in the Cloud
======================================

RDHPCS maintains Cloud Stores in Microsoft Azure, Amazon S3, and Google Cloud.  From the Globus perspective, connecting to these types of resources is identical to any other endpoints serving DTNs. The RDHPCS Globus plan offers connectors to access data to and from a public site available via AWS resources.

#. navigate to globus.org.
#. Select “existing organizational login” NOAA RDHPCS. The File Manager page displays.
#. Select Collection, and search for NOAARDHPCS# collections.
#. Once you can see the file lists, you can use the “File Manager” to move the files between the desired endpoints.

Globus Command Line Interface (CLI)
===================================

The CLI is available on Jet, Hera, and Niagara.
If you would like to use Globus-cli, either on your personal machine or on a system where globus-cli is not installed, you can install it easily . Instructions to install and use the Globus CLI are available `here <https://docs.globus.org/cli/GlobusCLI>`_.

Transferring Data to and from Your Computer
===========================================

To transfer data from your laptop/workstation to a NOAA RDHPCS system, you can

* use scp to a NOAA RDHPCS DTN (using pre-configured ssh port tunnels)
* use scp to a NOAA RDHPCS UDTN
* use Globus Connect Personal to transfer data between a NOAA RDHPCS UDTN and your local laptop/workstation.

NOAA RDHPCS considers your laptop/workstation as a Globus Untrusted Endpoint.

Some benefits of using Globus Connect Personal with UDTNs:

* Data can be transferred directly between your computer and an Untrusted Endpoint.
* Faster transfer rates as compared to scp and sftp.
* Data transfers automatically suspends and resumes as your computer goes to sleep, wakes up, or reboots.

The mechanism for transferring data between your laptop/workstation (Untrusted Endpoint) and a NOAA RDHPCS UDTN is exactly the same.
See `<Globus Connect Personal <https://www.globus.org/globus-connect-personal>`_ for information about setting up your laptop/workstation as a Globus Personal Endpoint.

GFDL Data Services
==================

* GFDL Data Services strive to make GFDL research data publicly available to the broader community, using FAIR (Findable, Accessible, Interoperable, Reusable) principles to help further science and the economy forward.
* GFDL Data Services provides a unified repository of datasets that support climate research of interest to lab researchers. The repository is known as the Unified Data Archive.
* GFDL Data Services helps build a community that leverages data management best practices to build analytics, workflows, etc. 

If you need assistance with any of the above, email oar.gfdl.workflow@noaa.gov.

GFDL Data Digital Object Identifier (DOI) Policy
================================================

Sharing NOAA data as openly and widely as possible, maximizing its utilization by NOAA partners, stakeholders, and the public, is foundational to NOAA’s mission, and thus central to NOAA’s Data Strategy. The complete GFDL Policy pertaining to externally facing data may be found `here. <gfdl-data-digital-object-identifier-doi-policy>`_ 

Data hosted in the GFDL Data portal servers is accessible through Globus, and available on request through the data hosting request forms. The Data Hosting Request (for papers, collaborations, other projects) (google.com) is accessible `here <https://docs.google.com/forms/d/e/1FAIpQLScH-2mMLHesN6DJlxLEVU6Kg8wXEKvEr-JgB_5nXchjCDrYww/viewform>`_. 

The requester will be notified of the globus url when  the request is completed



















-------

#. Navigate to globus.org.
#. Select “existing organizational login” NOAA RDHPCS. The File Manager page displays.
#. Select Collection, and choose the file system “noaardhpcs#niagara_untrusted”. If necessary, authenticate with username and RSA password.
#. In the File Manager, select Path: /collab1/data_untrusted/anonymous/from Orion
#. Repeat for the other endpoint: msuhpc2#Orion-dtn
#. Select files and directories, and click Start.

