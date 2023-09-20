Using storage capability to swap RAM )

As an advanced computer engineer, I'd be happy to guide you through the process of installing Swap and increasing your VPS's RAM to 8GB. Let's take it step by step:

Step 1: Check Available Disk Space
Before proceeding, check if you have enough available disk space to create the Swap file. Run the following command to see the disk usage:

```bash
df -h

```

Step 2: Create Swap File

Assuming you have enough space, create a Swap file with the following command:

```bash
sudo dd if=/dev/zero of=/swapfile bs=1M count=8192

sudo dd if=/dev/zero of=/swapfile bs=1M count=1024
```

This command will create an 8GB Swap file named "swapfile" with a block size of 1MB and a count of 8192 blocks (8GB).

Step 3: Set Permissions
Change the permissions of the Swap file to ensure it is accessible only by the root user:

```bash
sudo chmod 600 /swapfile

```

Step 4: Format the Swap File
Use the mkswap command to format the Swap file:

```bash
sudo mkswap /swapfile

```

Step 5: Activate the Swap File
Activate the Swap file using the swapon command:

```bash
sudo swapon /swapfile

```

Step 6: Enable Swap on Boot
To enable the Swap file at every boot, add an entry in the /etc/fstab file:

```bash
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab

```

Step 7: Verify Swap Configuration
To verify that the Swap file is correctly configured and in use, run the following command:

```bash
free -h

```

You should see the total available memory increased to 8GB, including the added Swap space.

Step 8: Set Swap threshold

To achieve the behavior you're looking for, where your system starts using swap when your physical RAM is nearly 90% full, you can use a combination of tools and configurations. Here's a general outline of the steps you can follow:

```bash
#!/bin/bash

# Set the threshold for RAM usage in percentage (e.g., 90%)
THRESHOLD=90

# Get current RAM usage
RAM_USAGE=$(free | awk '/Mem/ {print $3/$2 * 100.0}')

# Compare RAM usage with threshold
if (( $(bc <<< "$RAM_USAGE >= $THRESHOLD") )); then
    # Activate swap if RAM usage is above threshold
```

Step 9: Reboot (optional)
It's optional, but you can reboot your VPS to ensure all changes are applied correctly:

```bash
sudo reboot

```

After the reboot, your VPS should have 8GB of RAM, including the Swap space. Remember that Swap is slower than physical RAM, so it's still recommended to optimize your applications and consider upgrading your VPS if required for better performance.