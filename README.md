## Datadog-OpenShift integration

The Datadog cartridge for Openshift will enable you to install the Datadog Agent on your Openshift gears and start collect metrics from your different applications. This cartridge supports both scalable and non-scalable apps.

### Requirements

 * An OpenShift application
 * The OpenShift RHC client tool: https://www.openshift.com/get-started#cli
 * A Datadog account: http://www.datadoghq.com


### How to install the Datadog cartridge

1. Get your Datadog API key here https://app.datadoghq.com/account/settings#api and define the  'DATADOG_API_KEY' environment variable in your OpenShift application:
  ```
  rhc set-env DATADOG_API_KEY=your_api_key -a myapp
  ``` 

2. Add the cartridge to your gear:
  ```
  rhc cartridge-add http://cartreflect-claytondev.rhcloud.com/github/datadog/datadog-openshift -a myapp
  ```

3. At this point, the Agent should now be running on your gear. You should see your host appear in the list on the "Infrastructure" page on Datadog. You can start configuring your integrations to send metrics and events on Datadog. See here the list of the available integrations with associated configuration instructions: https://app.datadoghq.com/account/settings.


4. Ssh to your gear to work with the agent:
  ```
  ssh XXXXXXXXX@myapp.rhcloud.com
  ```
If you have trouble connecting to your gear, read the documentation here: https://www.openshift.com/developers/remote-access

  You can use several commands to interact with the Agent:
  * Start the Agent
    ```
    datadog/bin/control start
    ```
  * Stop the Agent
    ```
    datadog/bin/control stop
    ```
  * Restart the Agent
    ```
    datadog/bin/control restart
    ```
  * Get the status of the Agent
    ```
    datadog/bin/control status
    ```
  * Get detailed information about the Agent
    ```
    datadog/bin/control info
    ```

  Configuration files for the integrations are located here:
    ```
    cd datadog/dd-agent/agent/conf.d/
    ```

### Note on scalable apps

In the case of a scalable app, the Datadog Agent will be installed and configured automatically on every new gear created for scalibility purpose.


### More information about the Datadog Agent

See the detailed documentation on our website:
http://docs.datadoghq.com/guides/basic_agent_usage/
