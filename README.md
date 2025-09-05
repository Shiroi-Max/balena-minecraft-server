![Balena Server Logo](images/logo.png)

# Minecraft Server
**Starter project enabling you a Minecraft Server using just a Raspberry Pi 5.**

This project has been tested on a Raspberry Pi 5 8GB.

## Hardware required

* Raspberry Pi 5
* A fan or cooling system to prevent lag caused by throttling
* A 16GB or greater micro SD Card
* Power supply

## Software required

* A download of this project
* Software to flash an SD card ([balenaEtcher](https://balena.io/etcher))
* A free [balenaCloud](https://balena.io/cloud) account
* The [balena CLI tools](https://github.com/balena-io/balena-cli/blob/master/INSTALL.md)

## Setup and use :stars:

To run this project is as simple as deploying it to a balenaCloud application; no additional configuration is required.

### Setup the device :cd:

* Sign up for or login to the [balenaCloud dashboard](https://dashboard.balena-cloud.com)
* Create an application, selecting the correct device type for your Raspberry Pi
* Add a device to the application, enabling you to download the OS
* Flash the downloaded OS to your SD card with [balenaEtcher](https://balena.io/etcher)
* Power up the board and check it's online in the dashboard

### One Click Deployment

You can deploy this server with one click with the button below. Or, you can follow the manual deployment instructions in the next section.

[![](https://balena.io/deploy.svg)](https://dashboard.balena-cloud.com/deploy?repoUrl=https://github.com//Shiroi-Max/balena-minecraft-server)

### Manually Deploy this application :airplane:

* Install the [balena CLI tools](https://github.com/balena-io/balena-cli/blob/master/INSTALL.md)
* Login with `balena login`
* Download this project and from the project directory run `balena push <appName>` where `<appName>` is the name you gave your balenaCloud application in the first step.

## Connect to the terminal :satellite:

The server has no console input option in the cloud dashboard, so you need `RCON`. The port is `25575` and the password is `balena`. It is a protocol for connecting to the server.
There are many clients, but you can pick one here:

* mcrcon: https://github.com/Tiiffi/mcrcon/releases (NOTE: You will need for starting this script this batch file if you are using windows (Just paste it in the unzipped directory.): https://github.com/AlexProgrammerDE/RCON-Script/blob/master/launch.bat)

* Minecraft Server RCON: https://alexprogrammerde.github.io/Minecraft-Server-RCON.rar

## Connect to the file-directory :satellite:

You can connect to the server and change your serverfiles. I recommend using a tool like [WinSCP](https://winscp.net/) or if you are using OSX or a linux distribution you can use [Filezilla](https://filezilla-project.org/).  The IP Address to connect to is the local IP assigned to your device (without the quotes), the protocol to choose is SCP (If you got the choice), the port number is 22, the username is “root” (again, without the quotes) and the password is “balena” (no quotes). The files are in the folder named “serverfiles” at the root directory, you can double click to open that directory and browse the files in there.

**NOTE:** You can also change your SCP password by setting the `SCP_PASSWORD` Environment Variable within balenaCloud.  On the left, simply click on “Device Variables” and then click the “Add Variable” button. Give it a name of `SCP_PASSWORD`, and set the value to your password. 

## Custom RAM (optional) :link:

Devices like the Raspberry Pi 5 8GB or the 16GB model have enough RAM to run the server with more RAM (the default value used by balena Minecraft server is 4GB). If you set `RAM` to a value like `6G`, `8G`, or `10G` it will have the specified amount of RAM available.

## Play worldwide (optional) :earth_americas:

Once you’ve perfected the setup of your server on your local network, you might be interested in unveiling your server to the rest of the world! Here’s how you can enable remote access and allow players to connect via the Internet.

![NO-IP Picture](images/NO-IP.png)

If you’d like to allow friends outside your local network to join your server, you’ll need to set up dynamic DNS (DDNS) to expose your Pi to the outside world. This example uses a service called No-IP, which has a free tier for people who want to try DDNS out, though other options and methods do exist as well. In the case of this example, you will need to: 

* Create an account with [No-IP](https://www.noip.com/sign-up) by visiting their website.
* After creating the account and logging in, create a Hostname (example: balena.serverminecraft.net) by [following their documentation](https://www.noip.com/support/knowledgebase/getting-started-with-no-ip-com/).
* Set up Port Forwarding: You will need to route your Minecraft traffic to port 25565 on your Pi. To do this, you will log in to your home router and setup Port Forwarding. This step varies by particular brand of modem or router, but the No-IP documentation does a good job of describing the process [here](https://www.noip.com/support/knowledgebase/general-port-forwarding-guide/). You may need to follow instructions specific to your modem or router if the No-IP documentation does not contain your particular type.
* Optional: You can log in to No-IP with your router to keep the IP Address current in case it changes. That allows the router to connect automatically to No-IP. Here is a [guide by No-IP](https://www.noip.com/support/knowledgebase/how-to-configure-ddns-in-router/) on how to accomplish this.
* Paste your public / external internet address in the box labeled IP Address into the No-IP dashboard. You're done. 👍

For a deeper look at setting up remote access, please [reference this guide](https://www.noip.com/support/knowledgebase/getting-started-with-no-ip-com/) (Note: You can skip the DUC part).
