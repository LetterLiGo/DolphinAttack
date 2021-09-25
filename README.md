# What is DolphinAttack?
Speech recognition systems such as Siri or Google Now have become an increasingly popular human-computer interaction method, and have turned various systems into voice controllable systems. Prior work on attacking VCS shows that the hidden voice commands that are incomprehensible to people can control the systems. Hidden voice commands, though ‘hidden’, are nonetheless audible. In this work, we design a **completely inaudible** attack, *DolphinAttack*, that modulates voice commands on ultrasonic carriers (e.g., frequency > 20 kHz) to achieve inaudibility. By leveraging the nonlinearity of the microphone circuits, the modulated low frequency audio commands can be successfully demodulated, recovered, and more importantly interpreted by the speech recognition systems. We validate DolphinAttack on popular speech recognition systems, including Siri, Google Now, Samsung S Voice, Huawei, HiVoice, Cortana and Alexa. By injecting a sequence of inaudible voice commands, we show a few proof-of-concept attacks, which include activating Siri to initiate a FaceTime call on iPhone, activating Google Now to switch the phone to the airplane mode, and even manipulating the navigation system in an Audi automobile. We propose hardware and software defense solutions. We validate that it is feasible to detect *DolphinAttack* by classifying the audios using supported vector machine (SVM), and suggest to re-design voice controllable systems to be resilient to inaudible voice command attacks.

## How does DolphinAttack work?
A [nonlinear system](https://en.wikipedia.org/wiki/Nonlinear_system) is a system in which the change of the output is not proportional to the change of the input. Many electronic devices, such as microphones and amplifiers, are nonlinear under certain circumstances. When a signal containing two or more frequencies passes a nonlinear system, [intermodulation](https://en.wikipedia.org/wiki/Intermodulation) happens which introduces additional signals at new frequencies. *DolphinAttack* is built on this effect. By transmitting modulated ultrasound, we can recover "audible" voice command signals from nonlinear hardware, and control the speech recognition systems. 

![DA](https://github.com/USSLab/DolphinAttack/blob/master/images/receiver.png)</a>

## Tested devices
The following devices and voice assistants have been tested in our experiments with the experimental parameters provided in our paper. The table will be kept updated.

Manufacturer | Model | OS/Version | Voice Assistant | Activation<sup>1</sup> | Recognition<sup>2</sup>
------------ | ------| -----------| --------------  | ---------------------- | ----------
Apple        | iPhone 4s          | iOS 9.3.5       | Siri            | Y           | Y
Apple        | iPhone 5s          | iOS 10.0.2      | Siri            | Y           | Y
Apple        | iPhone SE          | iOS 10.3.1, 10.3.2 | Siri         | Y           | Y
Apple        | iPhone 6s          | iOS 10.2.1      | Siri            | Y           | Y
Apple        | iPhone 6 Plus      | iOS 10.3.1      | Siri            | Y           | N
Apple        | iPhone 7 Plus      | iOS 10.3.1      | Siri            | Y           | Y
Apple        | watch              | watchOS 3.1     | Siri            | Y           | Y
Apple        | iPad mini 4        | iOS 10.2.1      | Siri            | Y           | Y
Apple        | MacBook            | macOS Sierra    | Siri            | N/A           | Y
Google       | Nexus 5X           | Android 7.1.1   | Google Now      | Y           | Y
Google       | Nexus 7            | Android 6.0.1   | Google Now      | Y           | Y
Samsung      | Galaxy S6 edge     | Android 6.0.1   | S Voice         | Y           | Y
Huawei       | Honor 7            | Android 6.0     | HiVoice         | Y           | Y
Lenovo       | ThinkPad T440p     | Windows 10      | Cortana         | Y           | Y
Amazon       | Echo               | 5589            | Alexa           | Y           | Y
Audi         | Q3                 | N/A             | N/A             | N/A           | Y

<sup>1</sup> The voice assistant/device can be activated by *DolphinAttack* voice commands.

<sup>2</sup> The voice assistant/device can recognize the *DolphinAttack* voice commands after being activated.

## How to implement the experiment?
We offered two approaches in our paper, a benchtop setup and a portable one. However, we keep receiving letters asking about the portable setup. We understand the low-cost and convience of the portable setup, but we would recommand to start with a bentchtop setup of professional equipment, if ever possible. The reason is, the nonlinearity is highly hardware dependent and can vary greatly from devices to devices, and the key of this experiment is in finding and tuning the parameters. Due to the limitations of portable setup on power, modulation precision, transducer's frequency selectivity, debugging, etc., it is hard to pinpoint the problems you will have with a portable setup. The exact models for all the benchtop equipment can be found in the reference section of our paper.

## Video demonstration
Here is a video demonstration of *DolphinAttack*. Watch more videos on our lab homepage at [usslab.org](http://usslab.org/projects/dolphinAttack.html).

<a href="http://www.youtube.com/watch?feature=player_embedded&v=21HjF4A3WE4
" target="_blank"><img src="http://img.youtube.com/vi/21HjF4A3WE4/0.jpg" 
alt="DolphinAttack Demo" width="480" height="360" border="0" /></a>

## Worried about your device?
We have informed the above manufacturers and are collaborating with them on the security patches. Before the security patches are ready, you can protect your devices from *DolphinAttack* by turning off the "voice activation" of voice assistant, such as "Hey Siri". In this way, the voice assistants can only be activated through physical touch. For more security, you can turn off the voice assistant temporarily. 

# Read our paper
* Guoming Zhang, Chen Yan, Xiaoyu Ji<sup>1</sup>, Tianchen Zhang, Taimin Zhang, Wenyuan Xu<sup>1</sup>. [**DolphinAttack: Inaudible Voice Commands**](https://dl.acm.org/citation.cfm?id=3134052). *Proceedings of the 2017 ACM SIGSAC Conference on Computer and Communications Security (CCS 2017)*, October 2017. [[pdf]](http://usslab.org/papers/CCS2017_DolphinAttack_CameraReady.pdf) [(**Best Paper Award**)](https://www.sigsac.org/ccs/CCS2017/awards.html)

  <sup>1</sup> Corresponding authors.

# In the news
* **MIT Technology Review** [Secret Ultrasonic Commands Can Control Your Smartphone, Say Researchers](https://www.technologyreview.com/s/608825/secret-ultrasonic-commands-can-control-your-smartphone-say-researchers/)
* **WIRED** [Ultrasonic Voice Commands Can Hijack Siri and Amazon Echos](https://www.wired.com/story/security-roundup-germany-election-software-is-hackable)
* **BBC** ['Dolphin' attacks fool Amazon, Google voice assistants](http://www.bbc.com/news/technology-41188557) 
* **新华社** [苹果、三星都中招——“海豚音攻击”究竟是何方神器？](http://www.xinhuanet.com/fortune/2017-10/31/c_1121881819.htm)
* **浙江大学** [对不起，你的手机被“无声”操控了](http://www.zju.edu.cn/2017/0911/c578a637706/page.htm)

<!-- # DolphinAttack Dataset
**Manifest of the "DolphinAttack Dataset".**
[DolphinAttack Dataset Download Link](https://drive.google.com/file/d/1RgXlq4UuU2QKYHqwOcDaMESR-Z_2Rzmq/view?usp=sharing)

This demo dataset is composed of 2900+ audios, which records 28 voice commands at 7 distances by 5 speakers respectively. 

The *annotation.txt* indicates the audio files list.
| phone | file_name | distance | commands |
| ---- | ---- | ---- | ---- |
| google-pixel | p00_1_1.wav | 150cm | Echo |
| huawei-nova2 | p01_2_3.wav | 30cm | 你好联想 |
| huawei-mate9 | p02_3_4.wav | 100cm | Echo |
| oppo-k3 | p05_6_1.wav | 150cm | together difficult |
| oppo-reno | p05_6_1.wav | 150cm | together difficult |

**Notes:** eg. p00_1_1.wav means <br> 
a) speaker: p00 <br>
b) commands can be located in the next table's Col 1st, Row 1st, where shows command "Echo" <br>
c) There are several repeat commands, never mind.

**A table of 28 commands**
| Col 1 | Col 2 | Col 3 | Col 4 | Col 5 | Col 6 |
| ---- | ---- | ---- | ---- | ---- | ---- |
| Echo     | Hey Cortana | 小布小布 | Hey Cortana | seriously everywhere  | together difficult |
| Computer |  小微小微 | 小欧小欧 | hey bixby | everyone hundred | didn't agreement |
| Ok Google | 你好联想 | Amazon | Computer | period anywhere | immediately connect |
| 叮咚叮咚 | 小艺小艺 | Echo | 你好问问 | unfortunately | unfortunately |
| 你好魅族 | 你好问问 | 你好YOYO | Hey Google |  |  |

**7 Distances**
- 10cm | 30cm | 60cm | 100cm | 150cm | 200cm | 300cm

**5 speakers**
- p01 | p02 | p03 | p04 | p05  -->
# Contact
* Prof. Wenyuan Xu (<wyxu@zju.edu.cn>)
* Prof. Xiaoyu Ji (<xji@zju.edu.cn>)

# Powered by
## Ubiquitous System Security Laboratory (USSLab)
<a href="http:/usslab.org">![USSLab logo](https://github.com/USSLab/DolphinAttack/blob/master/images/usslab_logo.png)</a>
## Zhejiang University 
<a href="http://www.zju.edu.cn/english/">![ZJU logo](https://github.com/USSLab/DolphinAttack/blob/master/images/zju_logo.png)</a>
