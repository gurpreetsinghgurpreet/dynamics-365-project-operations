---
title: Sign up for a preview subscription
description: This topic provides information about how to subscribe to and deploy Project Operations lite deployment - deal to proforma invoicing.
author: sigitac
manager: Annbe
ms.date: 10/07/2020
ms.topic: article
ms.service: dynamics-365-customerservice
ms.reviewer: kfend 
ms.author: sigitac
---

# Sign up for a preview subscription for lite deployment – deal to proforma invoicing

This topic explains how to subscribe to the preview partner offer and deploy Dynamics 365 Project Operations lite deployment - deal to proforma invoicing.

> [!NOTE]
> This process will change in upcoming releases of Project Operations.

## Prerequisites

- You'll receive an email inviting you to participate in the preview. You can request a preview on the [Project Operations website](https://dynamics.microsoft.com/en-us/project-operations/overview/).
- The user who deploys the preview must have Azure tenant global administrator rights.
- Review all terms and conditions.

## Subscribe

When you receive a [preview request](https://forms.office.com/FormsPro/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR56j8lZs0FdAvwT75_WNFyxUMkRDV1NYQU5TNjE2VjhKOVBUNVg2R0s1NC4u) approval, you'll receive two offers from Microsoft by email. These offers allow you to deploy the Project Operations Preview:

- Dynamics 365 Project Operations (CRM) - Preview Trial
- Office 365 Project Operations - Preview Trial

> [!IMPORTANT]
> Only one person, the tenant administrator, in an organization needs to perform this task. If you aren't the subscriber to this release, wait until your organization has been signed up and you've received your user credentials.

### Dynamics 365 Project Operations (CRM) - Preview Trial 

Before you begin, make sure you are logged in to a browser with the user work account in the tenant where you want the Project Operations preview.

1. Redeem the first offer code, **Dynamics 365 Project Operations (CRM) - Preview Trial** by pasting it into the browser URL.

![Redeem Offer](./media/16RedeemFirstOfferNew.png)

2. Confirm your order.
![Confirm the order](./media/17ConfirmOrderNew.png)

You'll see confirmation offer was successfully redeemed.

![Confirmation](./media/18OrderConfirmationNew.png)

### Office 365 Project Operations - Preview Trial

Repeat the same steps as with the first offer code. Make sure to add the second offer code using the same user account that was used with the first offer code.

## Assign licenses

> [!IMPORTANT]
> You'll need administrative access to your organization's Office 365 Portal to complete the following steps.

1. Go to [Microsoft 365 admin center](https://portal.office.com/) to assign the licenses to your users.

![Admin center home page](./media/14AdminPortal.png)

2. On the **Active users** page, select the users that you want to assign a license to.

![Assign Licenses](./media/15AssignLicenses.png)

3. Verify that the **Dynamics 365 Project Operations (CRM) Preview** and **Office 365 Project Operations - Preview** licenses are selected. 
4. Select **Save changes**.

## Create a new CDS environment

1. Provision a new Project Operations CDS deployment environment by following instructions in the topic, [CDS deployment model](lite-deployment.md). When you select the environment type, make sure to use **Trial (Subscription based)**.
![New environment](./media/19CreateEnvironment.png)

2. Select the **Enable Dynamics 365 apps** setting, and leave **Automatically deploy these apps** blank.  
3. Select **Save** to create the environment.

![Add database](./media/20CreateEnvironment1.png)

4. After the environment is created, install **Microsoft Dynamics 365 Project Operations** solution. 

![Install Solution](./media/21InstallSolution.png)

## Install a CDS configuration and setup demo data

Install the CDS configuration and set up demo data by following instructions in the topic, [Apply demo setup and configuration data](lite-apply-demo-setup-config-data.md).