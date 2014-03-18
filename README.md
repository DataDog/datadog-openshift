The Datadog cartridge for Openshift will enable you to install the Datadog Agent on your Openshift gears and start collect metrics from your different applications.

### How to install the Datadog cartridge

Before adding the Datadog cartridge, make sure you have installed **python 2.6 or above** on your gear.

1. Add the cartridge to your gear.


2. Ssh to your gear:
  ```
  ssh 532b190a5004463582000119@myapp.rhcloud.com
  ```

3. Then install the Agent by running the following command:
  ```
  datadog/bin/control install YOUR_API_KEY
  ```
  You will find your API key here: https://app.datadoghq.com/account/settings#api

### More information about the Datadog Agent

See the detailed documentation on our website:
http://docs.datadoghq.com/guides/basic_agent_usage/
