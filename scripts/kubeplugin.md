## Using a plugin

### To use a plugin, make the plugin executable:

$ sudo chmod +x ./scripts/kubeplugin

### and place it anywhere in your PATH:

$ sudo mv ./scripts/kubeplugin /usr/local/bin

# You may now invoke your plugin as a kubectl command:

kubectl kubeplugin
