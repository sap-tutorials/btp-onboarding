---
author_name: Nagesh Caparthy, Oliver Stiefbold
author_profile: https://github.com/nagesh-caparthy
keywords: About BTP Business Technology Platform
auto_validation: true
primary_tag: software-product>sap-business-technology-platform
tags: [ software-product>SAP BTP, Cloud Foundry runtime and environment, tutorial>beginner, tutorial>tutorial, topic>cloud ]
time: 15
parser: v2
---

# Create a Cloud Foundry Subaccount with a Booster

This tutorial of the mission "Get Started with SAP BTP Enterprise Account" guides you through your first steps to create your first Subaccount in your SAP BTP Global Enterprise Account with the help of an SAP BTP Booster.


### Use a Booster for creating a Cloud Foundry Subaccount

A Subaccount in a SAP BTP Global Account is the place where you run your BTP services. You need at least one.

You can create a Subaccount either manually, which you can do later in the mission, or use an SAP BTP **Booster**. A booster is a wizard-based step-by-step BTP cockpit UI for achieving defined tasks in configuration. In this tutorial, you will use the Booster "Prepare an Account for Development", which will create a Subaccount and enable Cloud Foundry (CF) in this Subaccount.

If you do not need a Subaccount anymore, you can also delete it.

You can find boosters under the navigation entry "Boosters" in your global account.

 <!-- border -->![Find Boosters](images/3_1_find_boosters.png)



### Run Booster "Prepare an Account for Development”

In this tutorial, you are using the booster **"Prepare an Account for Development”** which will create a Subaccount and enable Cloud Foundry (CF) in this Subaccount.

Step by step, the booster assigns a curated set of entitlements, creates a subaccount, configures services, and sets up authorizations. 

In the background, it enables Cloud Foundry, creates a Cloud Foundry organization, one Cloud Foundry space for this Organization, and assigns users to the Subaccount and specific roles.

In the boosters overview, select the booster "Prepare an Account for Development", read the "Overview" description, and check the required "components". An Entitlement of "Cloud Foundry Runtime" is required for this Booster, which means your Global Account is entitled to use Cloud Foundry runtime. 


#### Procedure

Press **Start** to run the booster.

 <!-- border -->![Find Boosters](images/3_2_choose_booster.png)



### Booster Step 1 - Check Prerequisites

The prerequisites will be checked and marked as green if authorizations and entitlements are fulfilled. Click "Next" to continue.

 <!-- border -->![Check Prerequisite in Booster Step 1](images/3_3_booster_step1.png)

Click "Next" to continue.

### Booster Step 2 - Set Up Subaccount

Provide your details in the booster form:

1. A subaccount name of your choice.

2. Choose Provider (Note: Only multi-cloud providers support Cloud Foundry runtime. SAP Data Center cannot be selected).

3. Region (Choose a region near your location)
4. Subdomain (Note: Subdomain name is used as URL access and it cannot be changed once created).
5. Org name of your choice
6. Provide a Space name (typically DEV, TEST, or PROD)

7. Click on **Next**.


 <!-- border -->![Find Boosters](images/3_4_booster_step2.png)


### Booster Step 3 - Add Users

Provide subaccount admin users and the developers who will be accessing the system. Click on Next.

 <!-- border -->![Find Boosters](images/3_5_booster_step3.png)


### Step 4 - Review and Run Booster

Check the summary of the subaccount details before you execute the booster.

Press **"Finish"** and the booster will be executed.

 <!-- border -->![Find Boosters](images/3_6_booster_step4.png)



You should be able to see that your booster is executed successfully.

 <!-- border -->![Booster success message](images/3_7_booster_success.png)

After completion, the subaccount can be accessed for further configuration and development.





