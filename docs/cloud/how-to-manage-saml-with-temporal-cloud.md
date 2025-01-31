---
id: saml
title: How to manage SAML authentication with Temporal Cloud
sidebar_label: SAML
sidebar_position: 7
description: Integrate a SAML identity provider with your Temporal Cloud account.
slug: /cloud/saml
toc_max_heading_level: 4
keywords:
- how-to
- introduction
- security
- temporal cloud
tags:
- how-to
- introduction
- security
- temporal-cloud
---

<!-- THIS FILE IS GENERATED. DO NOT EDIT THIS FILE DIRECTLY -->

To authenticate the users of your Temporal Cloud account, you can connect an identity provider (IdP) to your account by using Security Assertion Markup Language (SAML) 2.0.

:::info

Enabling this feature adds a charge to your account.
For more information, contact your account manager.

:::

## Integrate SAML with your Temporal Cloud account

1. Locate your <a class="tdlp" href="/cloud/namespaces#temporal-cloud-account-id">Temporal Cloud Account Id<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Temporal Cloud Account Id?</span><br /><br /><span class="tdlppd">A Temporal Cloud Account Id is a unique identifier for a customer.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/cloud/namespaces#temporal-cloud-account-id">Learn more</a></span></span></a>.
   One way to do so is to sign in to Temporal Cloud and find your <a class="tdlp" href="/cloud/namespaces#temporal-cloud-namespace-id">Namespace Id<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">What is a Cloud Namespace Id?</span><br /><br /><span class="tdlppd">A Cloud Namespace Id is a globally unique identifier for a Namespace in Temporal Cloud.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/cloud/namespaces#temporal-cloud-namespace-id">Learn more</a></span></span></a>.
   The Account Id is the five or six characters following the period (.), such as `f45a2`.
   You will need the Account Id to construct your callback URL and your entity identifier.
1. Configure SAML with your IdP by following one of these sets of instructions:
   - <a class="tdlp" href="#configure-saml-with-azure-ad">Microsoft Azure Active Directory (Azure AD)<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">How to configure SAML with Azure AD</span><br /><br /><span class="tdlppd">To use Azure AD as your SAML IdP, create an Azure AD Enterprise application.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="#configure-saml-with-azure-ad">Learn more</a></span></span></a>
   - <a class="tdlp" href="#configure-saml-with-okta">Okta<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">How to configure SAML with Okta</span><br /><br /><span class="tdlppd">To use Okta as your SAML IdP, configure a new Okta application integration.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="#configure-saml-with-okta">Learn more</a></span></span></a>
1. <a class="tdlp" href="#finish-saml-configuration">Share your connection information with us and test your connection.<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">How to finish your SAML configuration</span><br /><br /><span class="tdlppd">To finish your SAML configuration, send us the sign-in URL, X.509 certificate, and IdP domains and then test your connection.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="#finish-saml-configuration">Learn more</a></span></span></a>

## How to configure SAML with Azure AD {#configure-saml-with-azure-ad}

If you want to use the general Microsoft login mechanism, you don't need to set up SAML with Azure AD.
Just select **Continue with Microsoft** on the Temporal Cloud sign-in page.

To use Azure AD as your SAML IdP, create an Azure AD Enterprise application.

1. Sign in to the [Microsoft Azure AD portal](https://portal.azure.com/).
1. On the home page, under **Manage Azure Active Directory**, select **View**.
1. On the **Overview** page near the top, select **Add > Enterprise application**.
1. On the **Browse Azure AD Gallery** page near the top, select **Create your own application**.
1. In the **Create your own application** pane, provide a name for your application (such as `temporal-cloud`) and select **Integrate any other application you don't find in the gallery**.
1. Select **Save**.
1. In the **Getting Started** section, select **2. Set up single sign on**.
1. On the **Single sign-on** page, select **SAML**.
1. In the **Basic SAML Configuration** section of the **SAML-based Sign-on** page, select **Edit**.
1. In **Identifier (Entity ID)**, enter the following entity identifier, including your Account Id where indicated:

   ```bash
   urn:auth0:prod-tmprl:ACCOUNT_ID-saml
   ```

   A correctly formed entity identifier looks like this:

   ```bash
   urn:auth0:prod-tmprl:f45a2-saml
   ```

1. In **Reply URL (Assertion Consumer Service URL)**, enter the following callback URL, including your Account Id where indicated:

   ```bash
   https://login.tmprl.cloud/login/callback?connection=ACCOUNT_ID-saml
   ```

   A correctly formed callback URL looks like this:

   ```bash
   https://login.tmprl.cloud/login/callback?connection=f45a2-saml
   ```

1. You can leave the other fields blank.
   Near the top of the pane, select **Save**.
1. In the **Attributes & Claims** section, select **Edit**.
1. We require the user's full email address when connecting to Temporal.
   In the **Required claim** section, set **emailaddress** and **name**.
   Verify that **Unique User Identifier (NameID)** is set to `user.userprincipalname [nameid-format:emailAddress]`.
1. Collect information that you need to send to us:
   - In the **SAML Certificates** section of the **SAML-based Sign-on** page, select the download link for **Certificate (Base64)**.
   - In the **Set up _APPLICATION_NAME_** section of the **SAML-based Sign-on** page, copy the value of **Login URL**.

To finish setting up Azure AD as your SAML IdP, see <a class="tdlp" href="#finish-saml-configuration">Finish SAML configuration<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">How to finish your SAML configuration</span><br /><br /><span class="tdlppd">To finish your SAML configuration, send us the sign-in URL, X.509 certificate, and IdP domains and then test your connection.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="#finish-saml-configuration">Learn more</a></span></span></a>.

## How to configure SAML with Okta {#configure-saml-with-okta}

To use Okta as your SAML IdP, configure a new Okta application integration.

1. Sign in to the [Okta Admin Console](https://www.okta.com/login/).
1. In the left navigation pane, select **Applications > Applications**.
1. On the **Applications** page, select **Create App Integration**.
1. In the **Create a new app integration** dialog, select **SAML 2.0** and then select **Next**.
1. On the **Create SAML Integration** page in the **General Settings** section, provide a name for your application (such as `temporal-cloud`) and then select **Next**.
1. In the **Configure SAML** section in **Single sign on URL**, enter the following callback URL, including your Account Id where indicated:

   ```bash
   https://login.tmprl.cloud/login/callback?connection=ACCOUNT_ID-saml
   ```

   A correctly formed callback URL looks like this:

   ```bash
   https://login.tmprl.cloud/login/callback?connection=f45a2-saml
   ```

1. In **Audience URI (SP Entity ID)**, enter the following entity identifier, including your Account Id where indicated:

   ```bash
   urn:auth0:prod-tmprl:ACCOUNT_ID-saml
   ```

   A correctly formed entity identifier looks like this:

   ```bash
   urn:auth0:prod-tmprl:f45a2-saml
   ```

1. We require the user's full email address when connecting to Temporal.
   - In **Name ID format**, select `EmailAddress`.
   - In **Attribute Statements**, set **email** and **name**.
1. Select **Next**.
1. In the **Feedback** section, select **Finish**.
1. On the **Applications** page, select the name of the application integration you just created.
1. On the application integration page, select the **Sign On** tab.
1. Under **SAML Setup**, select **View SAML setup instructions**.
1. Collect information that you need to send to us:
   - Copy the IdP settings.
   - Download the active certificate.

To finish setting up Okta as your SAML IdP, see the next section, <a class="tdlp" href="#finish-saml-configuration">Finish SAML configuration<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">How to finish your SAML configuration</span><br /><br /><span class="tdlppd">To finish your SAML configuration, send us the sign-in URL, X.509 certificate, and IdP domains and then test your connection.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="#finish-saml-configuration">Learn more</a></span></span></a>.

## How to finish your SAML configuration {#finish-saml-configuration}

After you configure SAML with your IdP, we can finish the configuration on our side.
<a class="tdlp" href="/cloud/support#support-ticket">Create a support ticket<span class="tdlpiw"><img src="/img/link-preview-icon.svg" alt="Link preview icon" /></span><span class="tdlpc"><span class="tdlppt">How to create a ticket for Temporal Support</span><br /><br /><span class="tdlppd">To request assistance from Temporal Support, create a ticket in Zendesk.</span><span class="tdlplm"><br /><br /><a class="tdlplma" href="/cloud/support#support-ticket">Learn more</a></span></span></a> that includes the following information:

- The sign-in URL from your application
- The X.509 SAML sign-in certificate
- One or more IdP domains to map to the SAML connection

Generally, the provided IdP domain is the same as the domain for your email address.
You can provide multiple IdP domains.

When you receive confirmation from us that we have finished configuration, log in to Temporal Cloud.
This time, though, enter your email address in **Enterprise identity** and select **Continue**.
Do not select **Continue with Google** or **Continue with Microsoft**.
You will be redirected to the authentication page of your IdP.
