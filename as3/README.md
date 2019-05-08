
This directory contains AS3 declarations to add configuration either via BIG-IP or BIG-IQ (look at name of file for which one).  If it is a BIG-IQ file, make sure to adjust the name of the BIG-IP referenced in the declararion for it to run smootly.

Currently all files specify the schema as of roday (5/8/2019) for validation of the JSON.  As that file is updated, the schema line needs to be updated too.  This is for use in Visual Studio to validate the JSON, which is helpful to show in a demo and in the real world.

In order to run, use POSTMAN to POST the declarations to:
     https://{{host}}/mgmt/shared/appsvcs/declare

Substitute the {{host}} with IP address of BIG-IP or BIG-IQ.

For this to work, must install 'as3' on BIG-IP.  See following for more details on AS3, including the installation of rpm:
     https://clouddocs.f5.com/products/extensions/f5-appsvcs-extension/latest/

In order to wipe the slate clean of all AS3 configuration, send DELETE to same URL:
     https://{{host}}/mgmt/shared/appsvcs/declare/
