---
keywords: Set up SAP BTP, Kyma runtime
parser: v2
time: 30
tags: [ tutorial>beginner ]
primary_tag: topic>sap-community
author_name: Gaurav Abbi, Oliver Stiefbold
---

# Set up SAP BTP, Kyma Runtime

<!-- description --> SAP BTP, Kyma runtime provides a fully managed Kubernetes runtime based on the open-source project Kyma.
With this cloud-native solution, developers can extend SAP solutions with serverless Functions and combine them with containerized microservices.

## You will learn

  - How to create a subaccount for enterprise accounts or enter a trial subaccount
  - How to entitle your subaccount to use Kyma runtime
  - Enable Kyma runtime

## Prerequisites

An SAP BTP enterprise account with unused Kyma entitlement or an SAP BTP trial account.

## Intro

> **NOTE:** If you follow this tutorial as part of a mission from SAP Discovery Center, consider using the Quick Account Setup instead as it completes the steps outlined here for you. However, if you prefer to do the steps manually, this tutorial is for you.

[SAP BTP, Kyma runtime](https://help.sap.com/docs/btp/sap-business-technology-platform/kyma-environment?version=Cloud) provides a fully managed Kubernetes runtime based on the open-source project [Kyma](https://kyma-project.io/#/). With this cloud-native solution, developers can extend SAP solutions with serverless Functions and combine them with containerized microservices.

### Create a subaccount for Kyma runtime

You can use an existing subaccount of your SAP BTP global enterprise account and enable Kyma, or create a new subaccount for this tutorial.

In this step, you create a new subaccount for your Kyma runtime.

> **NOTE:** In an SAP BTP **trial account**, a subaccount with Kyma entitlement is already preconfigured. You could create another subaccount in trial, but you it will not have unused entitlements to use Kyma. You need to delete the Kyma entitlement in the preconfigured subaccount first.

1. Navigate to your Global Account Account Explorer, the home page of your global account. Select **Create > Subaccount**.

   ![Create a new subaccount](images/22_1_createsub.png)

2. Enter the **Display Name** and your preferred **Region**.

   For more details about Regions where Kyma is available, see [Discovery Center](https://discovery-center.cloud.sap/serviceCatalog/kyma-runtime?region=all) and [Regions for the Kyma Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions-for-kyma-environment) in SAP Help Portal.

   Optional: You may also change the name of your **Subdomain**. The subdomain will become a part of the URL for accessing applications that you subscribe to from this subaccount. The subdomain must be unique across all subaccounts in the same region. Uppercase and lowercase will not differentiate subdomains.

   ![Provide details for the subaccount](images/22_2_createsub.png)

3. Once created, go to the subaccount and scroll down to **Entitlements**.

   - If you use an SAP BTP trial account, you are already entitled to use the **Kyma runtime** service.
   - If you use an SAP BTP enterprise account, you are not yet entitled to use the **Kyma runtime** service.

### Entitle your subaccount to use Kyma runtime

If you use an SAP BTP enterprise account, you are not yet entitled to use the **Kyma runtime** service.

1. In your global account, navigate to **Entitlements > Entity Assignments**.

2. In the **Subaccounts/Directories** field, enter the name of the newly created subaccount. When you search for "Kyma" you will see no existing entitlements for that subaccount. Select **Configure Entitlements**.  

    ![Kyma Entitlement](images/2_1_kyma_entitlement_1.png)

3. To configure the subaccount entitlements, choose **Add Service Plans**.

    ![add Serviceplan Kyma](images/2_2_kyma_entitlement_2.png)

4. In the pop-up window, search for "Kyma" within **All Solutions**. Select **Kyma Runtime** and choose one of the available plans. To confirm, choose **Add 1 Service Plan**.

    ![Add Service Kyma Plan](images/2_3_kyma_addsplan_1.png)

5. Optionally, increase your **Subaccount Assignment**. For the tutorial purposes, 1 unit is enough. To confirm the settings, choose **Save**.

    ![Save your Settings](images/2_4_kyma_addsplan_2.png)

6. You entitled your subaccount to use Kyma runtime.

    ![Check Kyma Entitlements](images/2_5_kyma_entitled.png)

### Enable Kyma in your subaccount

Once your subaccount is entitled to use Kyma runtime, you can enable Kyma in your subaccount.

1. Enter your subaccount.

    ![Enter your Subaccount for Kyma](images/2_6_kymasub_goto_1.png)

2. From your subaccount **Overview** page, go to **Kyma Environment** and choose **Enable Kyma**.

    ![Enable Kyma](images/2_7_kymasub_enable_1.png)

3. In the pop-up wizard, complete the Basic Info section. Select the **Plan** that will define the Infrustructure Provider, and leave the generated **Instance Name**, **Cluster Name**, and **Region**. Choose **Next**.

    ![Step 1 of teh Kyma Wizard](images/2_8_kymasub_enable_2.png)

4. Leave the default values in the **Additional Parameters** section and choose **Next**.

    ![Step 2 of the Kyma Wizard](images/2_8_kymasub_enable_3.png)

5. Review the instance details and choose **Create**.

    ![Step 3 of teh Kyma Wizard](images/2_8_kymasub_enable_4.png)

6. The Kyma cluster is being created. It can take a while.

    ![Creation of Kyma Cluster will take some time](images/2_8_kymasub_enable_5.png)

7. Once the cluster is created you will see a link to enter Kyma dashboard.

    ![Link to Enter Kyma Dashbord](images/2_9_kyma_gotodashboard.png)

Congratulations! You enabled SAP BTP, Kyma runtime.
