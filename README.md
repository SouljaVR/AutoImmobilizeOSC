# AutoImmobilizeOSC
Fixes [remote IK jitter issue in VRChat](https://feedback.vrchat.com/vrchat-ik-20/p/network-jitter-with-ik) when using half-body/full-body tracking.

[**DOWNLOAD LATEST VERSION**](https://github.com/SouljaVR/AutoImmobilizeOSC/releases/download/1.0.0/AutoImmobilize.By.BigSoulja.v1.0.0.unitypackage)

## AutoImmobilizeOSC In Action:

This is the networked view just to be clear. **NOT LOCAL**. Everyone sees you like this without my prefab. Under 20 ping for both players.

![image](https://github.com/SouljaVR/AutoImmobilizeOSC/blob/main/AutoImmobilizeOFF_ExampleOpti.gif)![image](https://github.com/SouljaVR/AutoImmobilizeOSC/blob/main/AutoImmobilizeON_ExampleOpti.gif)

## How To Install:

1. Import the Unity package into your Unity avatar project. Download is available under releases.
2. Merge `Locomotion Controller` to the existing base controller of your avatar. If your avatar doesnt have one, get one, and merge this to it. If you add this controller directly it will break desktop/half body walking animations. You can use WetCat's LocomotionFix or GoGo Locomotion by Franada as a base.
3. Merge `FX Controller` with your existing FX Controller. If your avatar doesnt have one, you are fine to add the controller to the avatar directly.

You can use [Avatars 3.0 Manager](https://github.com/VRLabs/Avatars-3.0-Manager) by VRLabs or [Controller Editor](https://dreadrith.gumroad.com/l/CEditor) By Dreadrith to merge controllers with ease.

4. Add the following parameters to your avatars VRC Parameters:

![image](https://user-images.githubusercontent.com/97592971/202193385-9ca8a054-4883-4558-b5e9-2c7f35cc4704.png)

`AutoImmobilize` - Default State = False (Saved Parameter)

`LeftThumbStick` - Default State = False (Unsaved Parameter) (OSC Parameter controlled by ThumbParamsOSC)

`immobilize` - Default State = False (Unsaved Parameter)

There is also a parameters template in the package you can merge with your own.

5. Add the 'AutoImmobilizeMainMenu' expression menu to your avatars menu.
6. Avatar setup is done. Now you will need to download 'ThumbParamsOSC' by 'I5UCC'. [Download Here](https://github.com/I5UCC/VRCThumbParamsOSC)
7. Ensure 'ThumbParamsOSC' is sending bools for the left joystick of your controller. It is not necessary to send any other parameters. Read the documentation for ThumbParamsOSC to see how to do this. By default, the app will work fine without extra configuration, but its better to only send necessary data over OSC to avoid hitting bandwidth limits. Especially necessary if using with other OSC applications.

![image](https://user-images.githubusercontent.com/97592971/202195547-ea515d34-1202-4c78-9586-ab62edeee1d9.png)

8. Enable OSC in VRChat (Open expressions wheel > Options > OSC > Enable OSC)

9. Profit??

## How to use/Test if it works:

Enable the 'Auto Immobilize Toggle' on the left side of the menu. If it is working correctly, the immobilize icon on the right will toggle itself off when your finger rests on the joystick of your controller/joystick is moved. This allows your avatar to freely move around as normal. But you will be in an immobilized state when your finger is not touching/moving the left controller joystick.

![image](https://github.com/SouljaVR/AutoImmobilizeOSC/blob/main/AutoImmobilize_ExampleOpti.gif)

If this is working, you should also check your avatar debug menu and ensure `Locomotion` is disabling itself when your finger is not moving/resting on the left controller joystick. If for some reason it isnt working like below, it may be conflicting with another system on your avatar that controls `VRC Animator Locomotion Control`. You can try moving the layers for my system right under the base layer on both controllers to fix this.

![image](https://github.com/SouljaVR/AutoImmobilizeOSC/blob/main/Locomotion_test_ExampleOpti.gif)

If you see neither of the above working, it probably means OSC isnt working. Check the OSC debug menu to confirm. If you aren't recieving signals from 'ThumbParamsOSC', Restart VRChat and try again. If it still isnt working, do the following:

- Open 'Run' in Windows (Windows Key + R)
- Type in `%AppData%`
- Navigate to `AppData\LocalLow\VRChat\VRChat` and delete the **contents** of the OSC folder.
- Restart VRChat and it should all work now.

## Things to note/Drawbacks

- You can also **manually** immobilize yourself by turning off the 'Auto Immobilze Toggle' on the left, and just toggling the icon on the right manually yourself.

- This is created for Write Defaults **OFF** however I don't see why this wouldnt work with them on. You can enable write defaults for all the states that come with this prefab and see what happens. Or if you want to trigger me just mix them with WD ON states lol.

- Immobilization will not function on desktop. It **can**, but that is useless so I made it so it wont even if the toggles are on.

- Immobilization may not work with *some* avatar setups if `Locomotion Animations` are enabled. But if you're using full-body, why would you use this anyway? You can disable this in the VRChat quick menu IK settings.

- This **IS** Quest Compatible, however you only need to add this to the PC variant of your avatar. It will show for Quest users too. It also shows for your fallback avatar, so you dont need to be quest compatible at all for these benefits. This will not work on Quest-only avatars however (unless you can find a way to trigger the `LeftThumbStick` parameter on Quest.)

- While in an immobilized state, you cannot rotate your view left/right with the right controller joystick. You can easily combat this by resting your thumb on the left joystick while trying to turn, it becomes second nature after a while. OVR Playspace turning also works fine. You could also add extra conditions to my system that check for the `RightThumbStick` too, but I personally prefer it the way it is for better consistency. I tend to play with my right stick a lot.

- You may modify the system and/or add it to any avatar including sold avatars, however you must leave my name in the submenu as it currently is. Please do not claim this as your own work.

## What if my joystick touch capacitance is broken?

- Doesn't matter. ThumbParamsOSC will also trigger the `LeftThumbStick` boolean when the joystick is moved slightly.

If you need any help with this, feel free to message me on Discord. BigSoulja#8888

If this helped you and you want to show appreciation, feel free to star this repository. Or you could [buy me a coffee!](https://ko-fi.com/bigsoulja) Anything is really appreciated.

## Credits:

[I5UCC](https://github.com/I5UCC) For [ThumbParamsOSC](https://github.com/I5UCC/VRCThumbParamsOSC) - Thank you.
