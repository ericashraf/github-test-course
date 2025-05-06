## Setting a Static IP Address on Ubuntu Using NetworkManager

### Step 1: Open Terminal

Press `Ctrl+Alt+T` to open the terminal.

### Step 2: Identify the Network Connection

List all network connections managed by NetworkManager:

```sh
nmcli connection show
```

Look for the name of the connection you want to configure (e.g., `Wired connection 1`, `Home Wi-Fi`).

### Step 3: Open the Configuration File

NetworkManager stores connection settings in `/etc/NetworkManager/system-connections/`. Open the corresponding configuration file for your connection:

```sh
 cd /etc/NetworkManager/system-connections/
 
 sudo nano CONNECTION_NAME
```

Replace `CONNECTION_NAME` with the name of your network connection. Use underscores for spaces (e.g., `Wifi_connection_1`).

### Step 4: Edit the Configuration File

Add or update the following sections to configure a static IP address. Replace  `IP_ADDRESS`, `PREFIX`, `GATEWAY`, `DNS1`, and `DNS2` with your actual values.

For WiFi connection:

```ini

[ipv4]
method=manual
addresses1=IP_ADDRESS/PREFIX,GATEWAY
dns=DNS1;DNS2;
dns-search=
```

Example configuration:

```ini
[connection]
id=newton
uuid=fa4b2bd2-00f4-4449-a885-3da00d46e409
type=wifi
permissions=user:kronton2:;
timestamp=1711730628


[ipv4]
method=manual
addresses1=192.168.1.100/24,192.168.1.1
dns=8.8.8.8;
dns-search=
```

### Step 5: Save and Close the File

Save the changes and close the file by pressing `Ctrl+O` (to save), `Enter` (to confirm), and `Ctrl+X` (to exit).

### Step 6: Apply the Changes

Restart NetworkManager to apply the changes:

```sh
sudo systemctl restart NetworkManager
```

### Step 7: Verify the Configuration

Verify that the static IP has been set correctly:

```sh
ip a
```

You should see the static IP address assigned to your network interface.

### Step 8: Test the Network Connection

Ping an external IP address to ensure your network connection is working:

```sh
ping 8.8.8.8
```

### Troubleshooting

- If you encounter any issues, you can revert the changes by editing the configuration file again or restoring from a backup if you made one.
- Check the status of NetworkManager:
  ```sh
  sudo systemctl status NetworkManager
  ```

### Notes

- Ensure that the IP address you assign is within the subnet range of your network and is not already in use.
- Adjust the DNS servers in the `dns` section to your preferred DNS servers if necessary.

---

This should help you set a static IP address on your Ubuntu system using NetworkManager. Let me know if you need any further assistance!
