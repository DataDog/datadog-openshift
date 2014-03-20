The Datadog cartridge for Openshift will enable you to install the Datadog Agent on your Openshift gears and start collect metrics from your different applications.

### How to install the Datadog cartridge

Before adding the Datadog cartridge, make sure you have installed **python 2.6 or above** on your gear.

1. Add the cartridge to your gear. If you are using the RHC client tool, you would use the following command: 
  ```
  rhc cartridge-add http://cartreflect-claytondev.rhcloud.com/github/datadog/datadog-openshift -a myapp
  ```

2. ssh to your gear:
  ```
  ssh 532b190a5004463582000119@myapp.rhcloud.com
  ```
If you have trouble connecting to your gear, read the documentation here: https://www.openshift.com/developers/remote-access

3. Get your Datadog API key here https://app.datadoghq.com/account/settings#api and then install the Agent by running the following command on your gear:
  ```
  datadog/bin/control install YOUR_API_KEY
  ```

4. The agent is now running on your gear. You can use several commands to work with the Agent:
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

### More information about the Datadog Agent

See the detailed documentation on our website:
http://docs.datadoghq.com/guides/basic_agent_usage/
