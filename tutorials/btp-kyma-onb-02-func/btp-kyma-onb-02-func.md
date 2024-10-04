---
keywords: Set up SAP BTP, Kyma runtime
parser: v2
time: 30
tags: [ tutorial>beginner ]
primary_tag: topic>sap-community
author_name: Gaurav Abbi, Oliver Stiefbold
---

# Create a "Hello-World" Kyma Function and a microservice

<!-- description -->Once the SAP BTP, Kyma Runtime is entitled and enabled it's time to enable the Kyma module "Serverless", so you can start creating your first function and microservice in Kyma.

In this tutorial, you will use Kyma dashboard to add the Serverless module and create a Kyma function with a microservice.

## You will learn

  - How to enter Kyma dashboard
  - How to create a Kyma Function
  - How to create a Kyma microservice

## Prerequisites

You have created and set up your "SAP BTP, Kyma Environment" either manually or by Quick Account Setup.

### Enter Kyma dashboard

1. In your subaccount go to **Services > Instances and Subscriptions**.

2. Sroll down to **Environments** and choose the three dots **...** in the Kyma Environment line. Then, choose **Go to Dashboard**.

3. If you use the pre-configured shared SAP Cloud Identity Services tenant, SAP ID service, as an identity provider in your enterprise or trial account, the Two-Factor Authentication is enabled and will be enforced.

    Go to your authenticator application on your mobile device and add a new account. Once you scan the QR Code, a password to access Kyma will be created. Enter the password in the **Passcode** field.

    ![Enter your authenticator app password](images/2_10_kyma_2fa.png)

Congratulations, you are in Kyma dashboard!

![Your Kyma Dasboard, Cluster Details](images/2_11_kyma_dashboard.png)

### Enable the Serverless module

1. In Kyma dashboard choose **Modify Modules**. This view lists your Kyma module.

    ![Your Kyma Dasboard, Cluster Details](images/2_12_kyma_modules.png)

    > **Note:** When you enable Kyma, it is provisioned with the default modules added:
    > - The **Istio** module is a service mesh with Kyma-specific configuration.
    > - The **API Gateway** module provides functionalities that allow you to expose and secure APIs.
    > - Within the **SAP BTP Operator** module, BTP Manager installs the SAP BTP service operator that allows you to consume SAP BTP services from your Kubernetes cluster using Kubernetes-native tools.

2. Choose **Add** to open the **Add Modules** view. Select **serverless** and choose **Add**.

   ![Browsing modules](images/2_13_add_module.png)

    > **NOTE:** In this tutorial you use the Serverless module from the default release channel, namely the regular channel. You can also choose the fast channel. For more information, see [Kyma Release Channels](https://help.sap.com/docs/btp/sap-business-technology-platform/kyma-s-modular-approach?locale=en-US).

3. Once the module's state is `Ready`, go to **Namespaces** and choose the **default** namespace.

    ![The Kyma module is ready](images/2_16_default_namespace_selected.png)

4. Within the namespace, go to **Workloads > Functions**, the newly created option that comes with the Serverless module.

    ![Functions are now available](images/2_17_workloads_functions.png)

    Congratulations! Now you can create serverless Functions in Kyma.

### Create a "Hello-World" Kyma Function

1. In the **Functions** view, choose **Create**.

2. Fill in the form in the **Create Function** view using the following details and choose **Create**.

   - **Template**: `default`
   - **Name**: for example, `hello-world`
   - **Language**: `JavaScript`
   - **Runtime**: `node.js 20`
   - **Function Profile**: `XS`

   ![kyma function](images/2_18_function_edit.png)
  
3. Creating a Function takes a few seconds. Select the newly created **hello-world** Function and switch to the **Configuration** tab. As it does not have any APIRules yet, you need to create one to define the rules of accessing the Function using APIs.

    ![kyma function no api rules](images/2_20_no_api_rules.png)

4. Go to **Discovery and Network > API Rules** and choose **Create**.

    ![kyma api](images/2_21_api_rule_create.png)

5. Fill in the form in the **Create API Rule** view using the following details and choose **Create**

   - **Name**: for example, `hello-rule`
   - **Service Name**: the `hello-world` Function
   - **Port**: `80`
   - Leave the pre-defined details in the **Gateway** section
   - **Host**, for example, `hello-host`
   - Leave the pre-defined details in the **Rules** section

    ![kyma api rule](images/2_22_hello_rule.png)

6. The "hello-rule" APIRule is created. Click on the **Host** URL to execute your Function in a browser window.

    ![kyma api](images/3_3_kyma_api_4.png)

    A browser window will open showing the following result:

     **`Hello World from the Kyma Function hello-world running on nodejs20!`**

### Deploy a microservice on Kyma

You already know how to deploy and expose a Function. You can do the same with a container microservice.

To deploy a microservice, you will use the **orders-service** from Kyma examples. It is available:

   - in [GitHub](https://github.com/kyma-project/examples/blob/main/orders-service/README.md), or
   - as a Docker image on Google Container Registry `eu.gcr.io/kyma-project/develop/orders-service:68a58069`.

This tutorial shows how to deploy a microservice using the Docker image.

1. Open Kyma dashboard, and go to a **Namespace**, for example, **default**.

2. Go to **Workloads > Deployments** and choose **Create**.

3. Fill in the form in the **Create Deployments** view using the following details and then choose **Create**.

   - **Name**: `orders-deployment`
   - **Docker Image**: `eu.gcr.io/kyma-project/develop/orders-service:68a58069`
   - Optionally, provide the following parameters to save resources:

    | Profile | Value | Profile | Value |
    | :--- | ---: | :--- | ---: |
    | Memory requests | 10Mi | Memory limits   | 32Mi |
    | CPU requests (m) | 16m | CPU limits (m)  | 20m  |

You created the **orders-deployment** Deployment. To confirm that the operation was successful, check the **Status** field is showing **1/1** Pods running.

### Create a Service

Once you have the Deployment ready, you can create a Kubernetes Service to allow other Kubernetes resources to communicate with your microservice.

1. Go to **Discovery and Network > Services** and choose **Create**.

2. Fill in the form in the **Create Service** view using the following details and then choose **Create**.

    - **Name**: `orders-service`
    - **app**: `orders-deployment`
    - Add a port using the following parameters:
        - **Name**: `orders-port`
        - **Protocol**: `TCP`
        - **Port**: `80`
        - **Target Port**: `8080` (or other)
        - **Application Protocol**: `http`

You created a new service, called **orders-service**.

### Expose the microservice

You cannot access and test your new `orders-service` yet from outside of the cluster. To expose the microservice, first, you must create an **API Rule** for it, just like you did to expose your Function.

1. Go to **Discovery and Network > API Rules** and choose **Create**.

2. Fill in the form in the **Create API Rule** view using the following details and choose **Create**

   - **Name**: `orders-apirule`
   - **HTTP Request Timeout**: `30` (or any up to `3900`)
   - **Service Name**: `orders-service`
   - **Port**: `80`
   - Leave the pre-defined details in the **Gateway** section
   - **Host**: choose your host from the dropdown menu and replace the wildcard (*) with a name, for example, `orders-host`
   - Leave the pre-defined details in the **Rules** section

3. The `orders-apirule` is created. Wait for the **Status** to be `OK`.

4. Click on the **Host** URL to execute the Service in a browser window. A browser will open but the link will be empty because the underlying Docker image has no home page. Extend the URL by adding the **/orders** string.

    For example:
    URL: `https://orders-host.c-123456.kyma.ondemand.com/` has to become
    URL: `https://orders-host.c-123456.kyma.ondemand.com/orders`

5. If you extend the URL correctly, you can see your orders: **`[]`**. It is empty, as you have not created orders in this tutorial so far.

#### Create sample content for your Service

1. In the terminal call your service using curl. Replace `${APP_URL}` with your `orders-host` URL, for example, `https://orders-host.b1234567.kyma.ondemand.com/`.

    ```bash
    curl -X GET ${APP_URL}/orders -k`
    ```

    The result should be still **`[]`**.

2. Place an order using curl replacing the `${APP_URL}` with your `orders-host` URL:

    > **NOTE:** Windows users should use a Linux-like bash, for example, Git Bash to be able to copy and paste the sample code.

    ```bash
    curl -X POST ${APP_URL}/orders -k \
      -H "Content-Type: application/json" -d \
      '{
          "consignmentCode": "76272727",
          "orderCode": "76272725",
          "consignmentStatus": "PICKUP_COMPLETE"
      }'
    ```

3. Call your `orders-service` in your browser again. The `orders-service` will return the order:

    `[{"orderCode":"76272725","consignmentCode":"76272727","consignmentStatus":"PICKUP_COMPLETE"}]`

    For a complete guide on how to run the `orders-service`, see [the example repository in GitHub](https://github.com/kyma-project/examples/blob/main/orders-service/README.md)

Congratulations, you created and exposed your first microservice!
