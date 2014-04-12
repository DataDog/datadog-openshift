## Monitoring Openshift with Datadog

The Datadog cartridge lets you install the Datadog Agent on your gears and collect metrics from your apps. This cartridge supports both scalable and non-scalable apps.

### Requirements

 * An OpenShift app
 * The OpenShift RHC [client tool](https://www.openshift.com/get-started#cli)
 * A [Datadog](http://www.datadoghq.com) account


### How to install the Datadog cartridge

1. Get your Datadog API key [here](https://app.datadoghq.com/account/settings#api) and define the `DATADOG_API_KEY` environment variable in your OpenShift app:
  
  ```shell
  rhc set-env DATADOG_API_KEY=your_api_key -a myapp
  ``` 

1. Add the cartridge to your gear:

  ```shell
  rhc cartridge-add http://cartreflect-claytondev.rhcloud.com/github/datadog/datadog-openshift -a myapp
  ```
1. Ssh to your gear to work with the agent:
  ```
  ssh XXXXXXXXX@myapp.rhcloud.com
  ```
If you have trouble connecting to your gear, read [this guide](https://www.openshift.com/developers/remote-access).

  You can use several commands to interact with the Agent:
  * Start the Agent
    ```
    $OPENSHIFT_DATADOG_DIR/bin/control start
    ```
  * Stop the Agent
    ```
    $OPENSHIFT_DATADOG_DIR/bin/control stop
    ```
  * Restart the Agent
    ```
    $OPENSHIFT_DATADOG_DIR/bin/control restart
    ```
  * Get the status of the Agent
    ```
    $OPENSHIFT_DATADOG_DIR/bin/control status
    ```
  * Get detailed information about the Agent
    ```
    $OPENSHIFT_DATADOG_DIR/bin/control info
    ```

  Configuration files for the integrations are located here:
    ```
    cd $OPENSHIFT_DATADOG_DIR/dd-agent/agent/conf.d/
    ```
    
1. At this point, the Agent should be running on the gear and appear on the [Infrastructure Overview](https://app.datadoghq.com/infrastructure). You can configure integrations in Datadog to monitor databases, caches, etc. [Here](https://app.datadoghq.com/account/settings) the list of the available integrations, complete with configuration instructions.

### Scalable apps

In the case of a scalable app, the Datadog Agent will be installed and configured automatically on every new gear created for scalibility purpose.

### More information about the Datadog Agent

See the detailed documentation on our website:
http://docs.datadoghq.com/guides/basic_agent_usage/
