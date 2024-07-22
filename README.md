# PPPwn_cpp_sr
C++ rewrite of PPPwn (PlayStation 4 PPPoE RCE) with steps to run from Mac M series<br/>
<i>Note:</i> Credit for the original files for C++ rewrite goes to [xfangfang](https://github.com/xfangfang/PPPwn_cpp)

# Features

- Smaller binary size
- A wide range of CPU architectures and systems are supported
- Run faster under Windows (more accurate sleep time)
- Restart automatically when failing
- Can be compiled as a library integrated into your application

# Steps to crack ps4 11.00 using MAC silicon (M series)

1. Goto [PPPwn_cpp](https://github.com/xfangfang/PPPwn_cpp)
2. Scroll down until you see ‘Nightly Builds’ and press on the Nightly Link.
3. Download the required version for your machine, I used `aarch64-macos-none`
4. Alternatively to skip steps 1, 2 & 3 download https://nightly.link/xfangfang/PPPwn_cpp/workflows/ci.yaml/main/aarch64-macos-none.zip directly & unzip.<br/> You will get `pppwn` executable file.
5. Now goto [PPPwn-Lite](https://github.com/PSGO/PPPwn-Lite/releases) & download the `PPPwn-Lite-v5.6-0711.zip` then unzip it & in `PPPwn-Lite-v5.6-0711/PPPwn/stage1/1100/` folder you will get `stage1.bin` file.
6. Now goto [GoldHEN_v2.4b17.3](https://github.com/GoldHEN/GoldHEN/releases/tag/2.4b17.2) & download `GoldHEN_v2.4b17.3`, unzip the package & in `GoldHEN_v2.4b17.3/pppnw_stage2` you will get the `stage2_11.00.bin` file.
7. Now create a folder `PPPwn` inside Downloads folder & copy-paste the pppwn file from step 4, `stage1.bin` from step 5 and `stage2_11.00.bin` from step 6.
8. You should now have 3 files in `PPPwn` folder - `pppwn` , `Stage1.bin` , `Stage2_11.00.bin`
9. Make sure you have `goldhen.bin` on the root of a USB stick and is inserted into the PS4 (get `goldhen.bin` from `GoldHEN_v2.4b17.3` folder that you had earlier downloaded in step 6).
10. <i>NOTE:</i> USB Stick should be formatted to <b>Exfat</b>, please make sure during formatting the USB stick, you select with the scheme "Master Boot Record" & not with scheme GUI, because otherwise at stage 4 of the PPPwn will be "done" and on the PS4 you will see a notification "PPPwned" but Goldhen won't be installed in your ps4.
11. Now download [Wireshark](https://www.wireshark.org/download.html) & make sure you download the "mac os arm disk image"
12. Install Wireshark and then follow the prompts to install ChmodBPF. <br/>This will give bpf root access.
13. Now connect your Macbook with ps4 using ethernet cable, also don't forget to connect the USB stick to your ps4. <br/>
Now open Wireshark in your mac & since you're using a Ethernet Adapter you will need to change interface `en0` to interface `enX` - Replace X with number Ethernet Adapter is using, to check use WireShark.
14. To run the exploit for 11.00, copy the following to Terminal:
15. `sudo <Drag pppwn here - NOT THE FOLDER> --interface en0 --fw 1100 --stage1 "Drag Stage1.bin here" --stage2 "Drag Stage2_11.00.bin here" --auto-retry`<br/>
Press enter, enter password, press Enter, Select ‘Test Connection’ on PS4.<br/>
Make sure you are using Stage1 and Stage2 for 11.00
16. Example:
```
sudo /Users/user.name/Downloads/PPPwn/pppwn --interface en6 --fw 1100 --stage1 /Users/user.name/Downloads/PPPwn/stage1.bin --stage2 /Users/user.name/Downloads/PPPwn/stage2_11.00.bin --auto-retry
```

## Credits
All files & binaries are sources from: 
- [xfangfang](https://github.com/xfangfang/PPPwn_cpp)
- [PPPwn-Lite](https://github.com/PSGO/PPPwn-Lite)
- [GoldHEN](https://github.com/GoldHEN/GoldHEN)
