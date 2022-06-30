---
title: "Setting Up the Sun Wireless Toolkit, version 2.5.2"
date: 2022-06-29T21:20:50-04:00
draft: false
---

# Setting Up the Sun Wireless Toolkit, version 2.5.2
Below are the steps I took for installing the Sun WTK, on a Windows XP virtual machine.

The virtual machine part might not be needed, though I haven't tried this yet.

## VirtualBox and Windows XP

![The initial "Welcome to Setup" screen from the Windows XP installer](welcome-to-setup-yaaaaay.png)

Obviously, you're going to need an installation CD. (you should get one by your own, but if you really want a link, "WinXPProSP3x86" on IA)

You will also have to set up a new VM. On VirtualBox:
- Create new machine
- Name it whatever you want, set OS to "Windows XP (32-bit)"
- Create virtual hard drive (10GB is enough)
- Set RAM size (I set 2048 MB, but might be lower depending on what your host machine has)
- Mount the installation ISO
- Go through the setup as usual

![The Windows XP desktop with a different wallpaper, after installation was finished.](byebye-to-setup-aw-man.png)

Yipee! We need drivers, though...

Machine > Insert Guest Additions CD.

If nothing shows up, go into My Computer, and you should see the VirtualBox icon in the file explorer.

You will be now installing Guest Additions. If the installer freezes while installing, try disconnecting the VM from the internet. (that did the trick for me)

After installer is done, reboot and you've installed VirtualBox and Windows XP!

You might want to set up shared folders for the next section, though...
## Java Development Kit (JDK)
Before installing the WTK, we're going to need a JDK otherwise the installer will complain:
> Unable to locate J2SE Development Kit (JDK) (5.0 or later).

Older versions can be downloaded at Oracle, though you'll need a account in order to download the installer...

Fortunately, [There's a mirror of the JDK version 7 at oldversion.com](http://www.oldversion.com/windows/java-platform-7-sdk).

I've also uploaded another mirror via IPFS, in case the file above gets deleted: [QmXUxKGf9TAvwtyQCqNCmcRZS7KvceS7SDesnm7zKa1t8A](https://ipfs.io/ipfs/QmXUxKGf9TAvwtyQCqNCmcRZS7KvceS7SDesnm7zKa1t8A?filename=jdk-7-windows-i586.exe) (please pin, thanks!)

## Sun Wireless Toolkit (WTK)
Same with JDK, it can be download at Oracle, but an account is needed. [There's a mirror uploaded on Discord](https://cdn.discordapp.com/attachments/527605871107375119/627295049406873622/sun_java_wireless_toolkit-2.5.2_01-win.exe).

IPFS: [QmWtrqMehkvfuPKBiQdFUV73P4UXtAFnHP1reZ5S5Agdwa](https://ipfs.io/ipfs/QmWtrqMehkvfuPKBiQdFUV73P4UXtAFnHP1reZ5S5Agdwa?filename=sun_java_wireless_toolkit-2.5.2_01-win.exe)

I disabled Product Updates.

After installation is done, you might want to create a shortcut of C:\\Documents and Settings\\{your username}\\j2mewtk\\2.5.2 for easy access to projects.

And we've installed the WTK! Now let's compile something!!

## Hello, world!
After WTK has started, click on New Project, then:
- set Project Name to whatever you want, I set it "hello world".
- set MIDlet Class Name to the path of your main MIDlet class. If it's invalid.helloworld.HelloWorld you will need to create invalid/helloworld/HelloWorld.java in the sources folder.

After creating the new project, the settings for that project will show up. You can press OK.

Go to the WTK folder (the one that I created a shortcut of)/apps/{project name}/src/{folders}, then create the .java file (in the example above it would be HelloWorld.java)

If you can't create a file ending with .java, In Explorer, go to Tools>Folder Options>View and disable "Hide extensions for known file types".

Inside the .java file, write the following:

```
package invalid.helloworld; // you might want to edit this

import javax.microedition.midlet.MIDlet;
import javax.microedition.lcdui.Form;
import javax.microedition.lcdui.Display;

public class HelloWorld extends MIDlet { // and this
	public void startApp() {
		Form form = new Form("Hello world?");
		form.append("Hello World!!!");

		Display.getDisplay(this).setCurrent(form);
	}

	public void pauseApp() {}

	public void destroyApp(boolean unconditional) {}
}
```

On the WTK, click Compile, and it should finish as "Build complete".
Press run, and a simulator window might show up. When it shows the list of MIDlets of your project, press enter, and...
![Hello, World! inside the Sun WTK Simulator](hello-world.png)

**YESSSSSSSSSSSS!!!!** The WTK seems to work correctly!

If you got this far, Congratulations!

If you got stuck on a section, please, talk about in a chatroom! Or repo issue!

## Other stuff
You might want to install Notepad++ if you want a slightly more fancier text editor.