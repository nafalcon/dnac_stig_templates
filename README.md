# DISA STIG DNAC TEMPLATES
## Overview
This Repository contains Composite Template Sequences that apply the large majority of the DISA Security and Technical Implementation Guidlines (STIG) to Campus network switches and routers.  The templates are compatible with standard L2 network environments.  They are not fully compatible with SDA enabled architectures at this time.

Composite Templates:

Import your DNA Center's compatible file as a project.

1. DNAC_DISA_STIG_Templates_2.3.3.json
   - Compatible with DNA Center 2.3.3+
2. DNAC_DISA_STIG_Templates_2.3.5.json
   - Compatible with DNA Center 2.3.5+

Regular Templates:
   - Contains the Regular Templates that are currently packaged within the Composite Template json files.

Referenced DISA STIGs:
1. Cisco IOS XE Switch L2S STIG
2. Cisco IOS Switch L2S STIG
3. Cisco IOS XE Switch RTR STIG
4. Cisco IOS Switch RTR STIG
5. Cisco IOS XE Switch NDM STIG
6. Cisco IOS Switch NDM STIG

## Intent Based Networking
This project used multiple templates in a sequence to deploy Intent in combination with the Design Settings and Policies deployed within the UI. These templates can be used in Onboarding (PnP) or Day N methods. Day N methods are designed for making ongoing changes and may require 'no' statements depending on the configuration construct being modified.

The intention of this repository is to provide a means to accelerate the implementation of Campus Network DISA STIG Automation with DNA Center.  It is not intended to be a 100% solution, as every network is unique.  However, it covers a large extent of the provided guidlines.

## Importing the Templates (v2.3.3+)

The template structure assumes that "Device Controllability" is enabled in DNA Center and it is integrated with Cisco ISE.  To ensure a smooth deployment, the Network settings must be configured for the sites in your Network Design.

##### Navigate to Design/Network Settings

![Alt text](/pics/net_settings1.png?raw=true "Network Settings")

##### Ensure the RADIUS and TACACS servers are configured in the settings as required for each site

![Alt text](/pics/net_settings2.png?raw=true "Select Servers")

##### Ensure the DNA Center device credentials are assigned to each site as necessary

Note - The CLI credential that DNA Center uses to access devices must also be configured in you TACACS server.

![Alt text](/pics/dev_creds.png?raw=true "Select Servers")

##### Navigate to Tools/Template Editor

![Alt text](/pics/templates1.png?raw=true "Template Editor")

##### Import the project json file by selecting the "+" at the top left of the screen

![Alt text](/pics/import_project.png?raw=true "Import Project")

##### Select the json file and import (DNAC_DISA_STIG_Templates_2.3.3.json)

![Alt text](/pics/import_project2.png?raw=true "Import Project")

All of the pre-defined template sequences and accompanying templates will be available in DNA Center after the import.  You should see the below new folders and the templates contained within.  

   ##### DayN STIG Templates
   - Platform agnostic templates that can be used on routers or switches.  These templates would likely be considred "baseline".  The expectation is that 
   they would be maintained by a higher authority.
   ##### Switch DayN Templates
   - Templates that can be used only on switches.  These templates would likely be considred "baseline". The expectation is that 
   they would be maintained by a higher authority.
   ##### Site Local Templates
   - Templates maintained by individual sites to meet their own unique requirements.  The expectation is that their modification and use would be 
   restricted via site based RBAC once supported. 
   ##### Template Sequences
   - In this case, provisioning templates will always be part of a sequence, even if the sequence only contains a single template.

Care was taken to ensure modularity where configurations are not duplicated in multiple files.  When a change is made to a single template, every instance where it is used will be updated.

# Prepping the Templates for use

Most of the templates are ready for deployment immediately after import.  Note that some of the freshly imported templates require modification before use in each environment.  It's necessary to go through each one and make the requred updates to meet the intent of your network environment.  The following will attempt to outline each.

A good place to start is the "1 STIG L2 Switch" Template Sequence.  Begin by navigating to "Template Sequences/1 STIG L2 Switch".  Once opened, there will be a list of templates that would be implemented in sequence.  

![Alt text](/pics/template_sequence.png?raw=true "Template Sequences")

Note that by default, when a template in a sequence fails, that template stops and the process moves to the next one int the sequence.


