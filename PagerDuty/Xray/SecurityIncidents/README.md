# PagerDuty + JFrog Xray Integration Benefits
* **Proactively manage security and compliance** across the software development and release lifecycle.  Receive early notifications within PagerDuty on vulnerabilities and compliance violations impacting artifacts, builds and components before releasing to production.      
* **Customize notifications** Configure granular policies within JFrog Xray based on type of violation, severity, and receive notifications on repositories, builds or release bundles of interest.
* **Granular Visibility** Receive a continuously updated list of impacted components and their associated dependencies as part of the notification payload sent by JFrog Xray to PagerDuty.  

# How it Works
* Users will install the JFrog Xray integration application from within the PagerDuty Service Directory and receive a URL to setup the PagerDuty webhook within JFrog Xray
* JFrog Xray will utilize the PagerDuty webhook trigger to send notifications to PagerDuty.  Users will be able to configure their rules and set up watch policies for repositories, builds and release bundles within JFrog Xray and associate these rules with the PagerDuty webhook trigger. 
* Once the webhook is configured within JFrog Xray, an incident will be sent to the PagerDuty service whenever security or license violation occurs.
* Xray performs a recheck of all watched resources and any found violations will send an event to a service in PagerDuty. Events from Xray will trigger a new incident on the corresponding PagerDuty service, or group as alerts into an existing incident.

# Requirements
* PagerDuty integration requires an admin base role for account authorization. If you do not have this role, please reach out to an Admin or Account Owner within your organization to configure the integration.
* JFrog Xray requires an Admin based role with administrative privileges to configure the integration.  If you do not have this role, please reach out to an Admin or Account Owner within your organization to configure the integration.

# Support
If you need help with this integration, please contact `partner_support@jfrog.com`

# Integration Walkthrough
## In PagerDuty
Add JFrog Xray integration to an existing PagerDuty service or create a new service by following the steps below

### Integrating With a PagerDuty Service
1. From the **Configuration** menu, select **Services**.
2. There are two ways to add an integration to a service:
   * **If you are adding your integration to an existing service**: Click the **name** of the service you want to add the integration to. Then, select the **Integrations** tab and click the **New Integration** button.
   * **If you are creating a new service for your integration**: Please read our documentation in section [Configuring Services and Integrations](https://support.pagerduty.com/docs/services-and-integrations#section-configuring-services-and-integrations) and follow the steps outlined in the [Create a New Service](https://support.pagerduty.com/docs/services-and-integrations#section-create-a-new-service) section, selecting ***JFrog Xray + PagerDuty Notifications*** as the **Integration Type** in step 4. Continue with the In  ***JFrog Xray Setup***  section (below) once you have finished these steps.
3. Enter an **Integration Name** in the format `JFrog` and select  ***JFrog Xray + PagerDuty Notifications***  from the Integration Type menu.
4. Click the **Add Integration** button to save your new integration. You will be redirected to the Integrations tab for your service.
5. An **Integration Key** will be generated on this screen. Click on the integration name next to the integration key and copy the **integration URL** in a safe place as it will be used when you configure the integration with  ***JFrog Xray + PagerDuty Notifications***  in the next section.
![integrations](integration.png)

## In JFrog Xray
1. Navigate to **Xray Security & Compliance** in JFrog Platform’s **Administration** section and click on it
![step1](step1.png)
2. Click on **Webhooks** in the **General** tile
3. Create a **new webhook** for pagerduty
![new webhook](new_webhook.png)
4. Enter **Webhook Name**
5. Enter **URL** (URL is the Events API endpoint from pagerduty) _ex: https://events.pagerduty.com/integration/<integration_id>/enqueue_
6. Click **Save**
7. Navigate to **Security and Compliance** in JFrog Platform’s **Application** section and select **Policies**
![step7](step7.png)
8. Next, specify the **policy name** and select **security** from the dropdown list below policy name
![step8](step8.png)
9. Next, create a **new rule** for the policy by clicking on the **New Rule** to the right
![new rule](new_rule.png)
10. Enter a **rule name**
11. In the **criteria** section, select the **minimal severity** or the **cvss score**. Violations in Xray are filtered based on this criteria and sent to pagerduty
12. In the **Automatic Actions** section, select **Trigger Webhook** checkbox and select the webhook that you created above for pagerduty
13. Click on **Save**
![step13](step13.png)
14. A policy rule is created with the rule name sepecified in Step10
15. Click **create** to create a policy with name specified in Step8
16. Navigate to **watches** in the **Security and Compliance** section on the left
![step16](step16.png)
17. Create a **new watch** or edit an existing watch
18. In order to create a new watch, click on the **New Watch** present at the top right corner of the screen
19. Enter the **name** and description of the watch
20. In **Manage Resources** section, click on **Add repositories** or **Add Builds** or **Add Bundles** and then include the resource that you want to watch from the available resources and click **Save**
21. In the **Assigned policies** section, Click on **Manage policies** towards the right and include the policy created in Step15 and click **Save**
22. Click **Save** to save the watch
23. You’ll see the watch in the list of watches
24. To manually trigger a watch, click on the **play button** and this will start sending any violations related to the watch to pagerduty
![step24](step24.png)

# How to Uninstall
1. Find the integration to delete by navigating to **Services** and selecting **Service Directory**
2. Select the service with your integration and navigate to **Integrations** tab
3. Navigate to the integration by clicking on the integration name (**JFrog Xray + PagerDuty Notifications**)
4. Click on the **Delete Integration** button on the top right corner