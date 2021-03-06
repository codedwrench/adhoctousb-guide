AdhocToUSB Guide for Windows 10 by plus#3034
============================================

# Requirements

- PSP (any model should work)
- Memory Stick PRO Duo
- USB A to Mini USB Cable
- Xlink Kai [[here](http://www.teamxlink.co.uk/)]
- 6.60/6.61 PRO-C2 (Recommended) or 6.60/6.61 ME CFW
- Administrator privileges

# Part A: Setting Up the PC

## Step 1 - Microsoft Loopback Adapter
First we'll install the Loopback Adapter used by adhoctousb's Bridge program.

  1. Press the Windows button and R at the same time or search for `run` in the start menu in this menu type `hdwwiz`. 
 
  2. Click next and then select `Install the hardware that I manually select from a list (Advanced)`.

  3. This will bring up a list of Hardware types, scroll and find `Network Adapters`. Next.

  4. On the left will be a list of Manufacturers, click on Microsoft then on the right select the `Microsoft KM-TEST Loopback Adapter`. Click next again and it should install.

## Step 2 - Configuring Xlink Kai

Now open your start menu and search for `Configure Kai`.
  
In the configuration tool look for Network Adapter change this to `MS NDIS 6.0 LoopBack Driver`. *(If you don't see this you may have to reinstall WinPcap from their [website](https://www.winpcap.org/install/default.htm).)*  

Just click Save and restart Kai to be sure that its applied.

To test this check the Metrics tabs at the top of the Web UI, and look for Ethernet Adapter it should say `MS NDIS 6.0 LoopBack Driver` while in this menu make sure Reachable says Yes. *(You may have to look up a tutorial for port forwarding Kai or Enabling UPNP in your router)*

# Part B: Setting Up the PSP

## Step 3 - Installing the AdhocToUSB Plugin

Connect your PSP to the computer. *(If you have CFW im assuming you know how to put it into USB Mode.)*

In the included software bundle open the AdhocToUSB folder and transfer `AdhocToUSB.prx` to the `seplugins` folder, if it doesnt exist create it at the root of your PSP directory *(not in any folders)*  

Afterwards open `GAME.txt` in the `seplugins` folder, once again if it doesnt exist create it.  

Now type:  

`ms0:/seplugins/AdhocToUSB.prx 1` (for PSP 1000/2000/3000)  
or  
`ef0:/seplugins/AdhocToUSB.prx 1` (for PSP GO (E1000))

*Note: Only one plugin can use the USB port at a time, do not try to use this and for example RemoteJoyLite at the same time.*

# Part C: Setting Up the PC (Continued)

## Step 4 - Disabling Driver Signature Verification

[Use this guide](https://www.howtogeek.com/167723/how-to-disable-driver-signature-verification-on-64-bit-windows-8.1-so-that-you-can-install-unsigned-drivers/)

## Step 5 - Installing the PSP Type B Drivers

Connect the PSP to your computer via USB, start a game with Adhoc multiplayer and activate it. *(when you see the wireless light come on you're good)*

Back on PC, open the software package again and navigate to LibUSB/bin/, then run `inf-wizard.exe` as administrator, if you have your PSP in game you should see `PSP Type B`, click on that and then click next until it asks you to choose a location. Select the Type B folder provided in the software package, click save, then Install Now, it should install successfully.

At this point I highly advise that you open up the Admin PowerShell and type `bcdedit /set testsigning off` and re-enable Secure Boot if you had to disable it, the PSP drivers will still work.

# Part D: Profit

To go online from now, Open Xlink Kai then go to the associated game lobby for your game, afterwards on PSP activate Adhoc multiplayer while connected to your PC then start the Bridge.exe in the AdhocToUSB folder, *(you may want to make a shortcut to this file)* now finally select the Loopback Adapter, if it shows the FFFFFFF error just restart it, but it usually doesn't affect connectivity. If you get any timeout error notice thats simply lag and can be ignored.

Have fun using your PSP Online.


## Troubleshooting
- I'm getting an error about: MSVCP140.dll, VCRUNTIME140.dll or VCRUNTIME140_1.dll
   - Install [Microsoft Visual C++ Redistributable for Visual Studio 2015, 2017 and 2019](https://aka.ms/vs/16/release/vc_redist.x64.exe)
   
- I'm getting an error about: "Operation not supported or unimplemented on this platform"
   - The libUSBK driver is not installed correctly, make sure the plugin is enabled and a game is running when installing the driver using Zadig
   
- Receivebuffer got to over 50! or Sendbuffer got to over 50! ?
   - This is a normal warning, there could be some added latency while playing
 
- Could set configuration: Entity not found
   - This usually happens when you installed the wrong driver, reinstall the driver
