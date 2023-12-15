---
author_name: Oliver Stiefbold
author_profile: https://github.com/Gituserneumann
keywords: About BTP Business Technology Platform
auto_validation: true
primary_tag: products>sap-business-technology-platform
tags: [ products>sap-business-technology-platform, tutorial>beginner, topic>cloud ]
time: 15
parser: v2
---

# Create a Cloud Foundry Subaccount manually

This tutorial of the mission "Get Started with SAP BTP Enterprise Account" guides you through your first steps to create your first Subaccount in your SAP BTP Global Enterprise Account and do the initial configurations.

A Subaccount in a SAP BTP Global Account is the place where you run your BTP services. You need at least one. 

If you have already created one subaccount using a booster, you can create a second manually. Don´t worry, you can delete subaccounts, which you do not need anymore.


### Create a Subaccount manually


Creating a subaccount can be one of the easy tasks, however, one has to keep in mind the Hosting region, Naming conventions, Account Model, Labels, Authorizations, etc...

Before you start creating your subaccounts, we recommend understanding the basic details in this blog - [SAP BTP Cockpit – Global Account Technical Overview](https://blogs.sap.com/2022/01/04/sap-btp-onboarding-series-sap-btp-cockpit-global-account-technical-overview/) - section 3 and if you want to know about the account models and directories, you can read - [How to Determine your Account Model](https://blogs.sap.com/2021/12/17/sap-btp-onboarding-series-how-to-determine-your-account-model/).


#### Procedure

Now let us take a look at the details on creating the Subaccount manually.

1. From your global account home page, Click on the "Create" drop-down button, choose Subaccount.

2. Specify a display name.

3. (Optional) Specify a description.

4. Select the region, environment, and infrastructure provider of the new subaccount according to your account plan. 
   Additional fields appear according to the selected environment. Select settings as required.

    **Note:** In a subaccount in the Cloud Foundry environment, the subdomain that you specify can be any string. The subdomain can contain only lowercase letters and digits, and hyphens (not allowed in the beginning or at the end) and must be unique within the Cloud Foundry environment of SAP BTP. 

5. (Optional) To use beta features in the subaccount, select "Enable beta features".

6. Save your changes.

    <!-- border -->![](images/3_9_suba_manual.png)


#### Result

A new tile appears on the Global Account page with the subaccount details. 

For more information see SAP Help Portal, [Create a Subaccounts](https://help.sap.com/docs/btp/sap-business-technology-platform/create-subaccount). 




### Enable Cloud Foundry Environment in Your Subaccount

After you have created your subaccount you need to enable the runtimes of the subaccount. Runtimes can be either **Cloud Foundry, Kyma or ABAP**. 

In this tutorial you will enable **Cloud Foundry**. Guides for the other runtimes can be found in dedicated tutorials or missions.



#### Procedure

1. Open your BTP Cockpit.
2. Select the subaccount, you just created.

3. Select **Cloud Foundry Environment** in the tab navigation.

4. Check the button "Enable Cloud Foundry".
   
    <!-- border -->![Enable Cloud Foundry](images/3_10_enable_cf.png)

5. A form opens. Keep the preconfigured values or change the following entries: 

    - **Plan**: One of the Service Plans you are entitled to (e.g. standard, or free)
    - **Landscape**: Some Regions have more than one Landscape.
    - **Instance Name**: Consider a CLI-friendly name 
    - **Org Name**: Each Cloud Foundry environment has exactly one Organization.
   
    <!-- border -->![Fill out Cloud Foundry form](images/3_11_enable_2.png)

6. Choose `Create`.

7. The Cloud Foundry Environment will be created.
   
    Note your API Endpoint. Copy and call it in a browser. You will need it in other tutorials. 

    Note: You still have no Cloud Foundry "Spaces". You will need at least one.

    <!-- border -->![](images/3_11_enable_3.png)


### Create Spaces in your Cloud Foundry Environment

After you have enabled Cloud Foundry runtime, you can create a space. There is no limit to how many spaces you can have within one org.

Spaces e.g. can be used to separate dev from test and prod environment. A typical setup for a BTP environment is the Staged Development Environment with DEV, TEST, and PROD landscape for each project.

For more information, see SAP Help - [Setting Up Your Account Model](https://help.sap.com/docs/btp/best-practices/setting-up-your-account-model?locale=en-US).

#### Procedure

1. In your subaccount overview page, choose "Cloud Foundry Environment" again.

2. Press the button `Create Space`.

3. A popup form opens.

4. Provide a name  (choose "dev" if you have no name).

    <!-- border -->![Create Spaces](images/3_12_spaces.png)

5. Keep the **space roles** as preconfigured and choose `Create`.

6. Congratulations you now have a configured Cloud Foundry Environment.

    <!-- border -->![Create Spaces](images/3_13_spaces_2.png)


For more information, see [Managing Spaces](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/managing-spaces?locale=en-US) on SAP Help Portal.


### Add Members to Subaccount


The default **SAP BTP identity provider** and application identity provider of SAP BTP is the **SAP ID service**. Trust to SAP ID service in your subaccount is pre-configured by default, so you can start using it without further configuration. 

For more information about SAP ID Service see [SAP Help Portal](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/default-identity-provider?locale=en-US).

For more information, or on how to establish trust with your custom identity provider, start the Discovery Center mission [Establish single sign-on to your cloud solutions](https://discovery-center.cloud.sap/missiondetail/3114/3151/).



#### Users

If you want to grant authorizations to users from the SAP ID service in your subaccount, you must ensure that they have a user account in the SAP ID service.

For more information see [Working with Users](https://help.sap.com/docs/btp/sap-business-technology-platform/working-with-users). 


#### Roles and Role Collections

Roles determine which functions in the cockpit users can view and access, and which actions they can initiate.

SAP BTP offers predefined "Role Collections", which are sufficient for this mission.

For more information see [Working with Role Collections](https://help.sap.com/docs/btp/sap-business-technology-platform/working-with-role-collections)). 



#### Procedure

1. Open the SAP BTP cockpit.

2. Choose the subaccount to which you'd like to add users.

3. In the navigation pane, choose "Security" and then "Users".

    <!-- border -->![add subaccount members](images/4_1_suba_members.png)

4. All members currently assigned to the subaccount are shown in a list.

5. Choose `Create`.

6. Enter the user ID and e-mail address.

7. Choose the identity provider where the user is stored. The dropdown list displays the identity providers configured in the trust configuration of your subaccount.

8. `Save` your changes.


You can now proceed to assign role collections to the new user. Browse the list of available Role Collections by clicking on "Role Collections".





### Delete a Subaccount

If you want to delete your subaccount, e.g. because it was a test or sandbox subaccount, you can delete unused subaccounts.

>**Note:** Only subaccount administrators can remove such content from a subaccount.



#### Procedure

1. Login to SAP BTP Cockpit.
2. Choose the subaccount that you want to delete.
3. The subaccount doesn't contain any active subscriptions, service instances, brokers, or platforms.
4. Choose `Delete Subaccount` and confirm the operation.