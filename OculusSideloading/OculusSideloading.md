# The guide to allow yourself to sideload any app on your Oculus Quest
This guide is highly inspired by the Getting Started Guide of VRP [here](https://vrpirates.wiki/general_information/getting-started)<br>
And in general, the VRP wiki is a great source of information for the Quest, so I recommend you to check it out using these links:
- [VRP Wiki](https://t.me/VRPirates)
- [VRP Discord](https://discord.gg/DcfEpwVa4a)
- [VRP Telegram](https://t.me/VRPirates)

## Before you start

- [ ] Make sure you have a PC running Windows (Mac and Linux are not supported for this guide)
- [ ] Make sure you have either a Quest 2 or Quest 3
- [ ] Make sure your Quest is linked to your phone and you have the Oculus app installed
- [ ] Make sure you have a stable internet connection
- [ ] Make sure you have a USB-C cable to connect your Quest to your PC

## Index

- [Step 1: Enable Developer Mode](#step-1-enable-developer-mode)
    - [Step 1.1: Create an organization](#step-1-1-create-an-organization)
    - [Step 1.2: Verify your account](#step-1-2-verify-your-account)
    - [Step 1.3: Enable Developer Mode on your Quest](#step-1-3-enable-developer-mode-on-your-quest)
- [Step 2: Install ADB Drivers (Windows only)](#step-2-install-adb)
- [Step 3: Sailing the high seas](#step-3-alternate-using-rookie)
  - [Step 3.1: Install Rookie](#step-3-1-install-rookie)
  - [Step 3.2: Sideload an app](#step-3-2-sideload-an-app)

## Step 1: Enable Developer Mode

## Step 1.1: Create an organization

1. Open the [Oculus Organization Dashboard](https://dashboard.oculus.com/organizations/create/)
2. Create an organization

## Step 1.2: Verify your account

1. Go to [the developer verification website](https://developer.oculus.com/manage/verify/)
2. If prompted, log in with your Oculus account
3. Verify your account using either a phone number (recommended) or a credit card
4. Do not delete the verification method even after you have verified your account else you will lose access to developer mode (which is required for sideloading)

## Step 1.3: Enable Developer Mode on your Quest

1. Open the Oculus app on your phone
2. Open your Quest from the devices list
3. Go to Headset Settings
4. Go to Developer Settings
5. Enable Developer Mode or Debug Mode (name may vary)

## Step 2: Install ADB Drivers (Windows only)

1. Go [here](https://developer.oculus.com/downloads/package/oculus-adb-drivers/) and download the Oculus ADB Drivers
2. To install the drivers, extract the zip file and right-click on `android_winusb.inf` and click on Install.
3. Reboot your PC

## Step 3: Using SideQuest

### Step 3.1: Install Rookie

1. Go to [the VRP download page](https://vrpirates.wiki/general_information/vrp-downloads)
2. Download the latest version of Rookie Sideloader
3. Create a folder on your PC to host Rookie and make sure it is excluded from your antivirus
4. Extract the Rookie zip file to the folder you created

### Step 3.2: Sideload an app

1. Connect your Quest to your PC using a USB-C cable
2. Make sure your Quest is unlocked 
3. Run `Sideloader Launcher.exe` or `AndroidSideloader.exe` from the folder containing Rookie
4. In your Quest, allow USB debugging when prompted
5. In Rookie, double-click on the app you want to sideload and wait for it to finish
6. The app should now be installed on your Quest and you can find it in the Unknown Sources section of your library

**Congratulations! You've successfully installed Rookie and are able to sideload any app to your Quest !**

## Credits and software used

Made with ❤️ by [Ano0002](https://github.com/ano0002/)

- [VRP Wiki](https://vrpirates.wiki/)