# Asura Linux
  
[Asura Linux](https://github.com/asuralinux) was born out of the belief there is much more to do in building modern Linux systems. We want to experiment in the immutable/image-based/managed Linux space towards building Linux systems driven by the User Experience (UX).


## Purpose

Asura Linux is a project to explore the possibilities in building modern Linux systems focused on user experience enhanced by emerging technologies and concepts. These may change over time along with the rapidly evolving adjacent technology space.

At present, the key technologies and concepts of interest are as follows.
- Reproducible / Immutable Linux installations
- Multi-root capability to enable safe rollback and confident updates
- Atomic updates to avoid partial/failed update states
- Strong privacy and reasonable security by default
- Self-contained workloads
- Applications via multiple channels


## Objectives

The current objectives of the Asura Linux Project is to develop a focused Linux user experience with the following characteristics.

- An always updated stable system with rollback option
- A system with long-term upgrade option
- A system for different usage needs
- A system with strong privacy and reasonable security by default
- A system with an abundant application ecosystem
- A customizable and tweakable system
- An open source project with a surrounding active, supportive, and diverse community

Maintaining an own Linux distribution is not necessarily an objective of the Asura Linux Project. It will be done in the initial 12-month period as a vehicle for experimentation. If the results can be adopted by other distros (e.g., how [Fedora Asahi](https://asahilinux.org/2023/08/fedora-asahi-remix/) is being developed with direct contributions from [Asahi Linux](https://asahilinux.org/)), Asura Linux might not even need to remain a direct end user distribution. Therefore, that is a decision for future.


## Project History and Name

While the project concept had been an inkling for a while, it became a concrete concept in mid-2023 with the intent to improve the user experience story of how people build and use modern Linux systems.

_Asura_ in South Asian folklore and mythology are powerful and often chaotic beings (not necessarily malevolent or evil), usually depicted in juxtaposition against the heavenly _Sura_ (divine or celestial beings).

The name Asura Linux is a tongue-in-cheek reference to the realization it would not be an easy undertaking. If the current standard practice of building Linux systems is walking a blessed path (known, traveled, and relatively safe), what we set out to do likely will not be. At least, Gaveen found it amusing for a whole minute before registering the domain name.

The context for the project is explained in the *[Background](Archive/Background.md)* document. The initial version of the information in this repository also can be found as *[Asura Linux - Not-quite Project Charter](Archive/Asura%20Linux%20-%20Not-quite%20Project%20Charter.pdf)*, which also contains the initial User Stories considered to define the Objectives. 

  
## Current Status

While we are a 100% open source project, we are still in the early stages. The concept has been developed and elaborated in this document. In the coming days, these content will be made public on GitHub.

Asura Linux is not quite ready to accept contributions since the project infrastructure is being setup and the initial build systems are being tested. In the coming weeks, we will have CI/CD in place to build bootable ISO images. We will probably use GitHub Actions service initially, but [Apache BuildStream](https://buildstream.build/) is also a long-term alternative tool being considered. When we are ready to accept contributions, everything will be made public on GitHub and the project website.


## Project Promise

Asura Linux Project is still too early to set formal guidelines or governance. Therefore, instead of such, we promise you the following until we have a proper structure.

The Asura Linux Project promises are:
- Asura Linux will be open source, and it will always remain so.
- Asura Linux will be a friendly, inclusive, and welcoming community with a Code of Conduct.
- Asura Linux will collaborate with other open source projects rather than being a competitor.
- Asura Linux will value Integrity, Decency, Responsibility, Inclusion, and Excellence.

Further, we hope to write often about the process of building an image-based/managed Linux distribution. There is not too much information on how to go about such things. We believe being documented by people not used to building a shippable Linux distro, will at least be a learning experience.


## Scope

In order to achieve its objectives, Asura Linux Project aims to spend the _next 12 months (October 2023 – September 2024)_ building a Linux distribution with the following experimental features/areas.

This initial 12-month period is not an arbitrary definition. In 2022 and 2023, the _Image-based Linux Summit_ took place in September/October. As the main public forum in the Image-based Linux space, it provides an important milestone to review, discuss, and improve/develop [the Linux Userspace API (UAPI) Group](https://uapi-group.org/) specifications. By roughly aligning to this period, the Asura Linux Project also sets a timeline to review the progress, evaluate new developments in the space, and to set the scope for next year.

As Asura is meant to be experimental, any and all of the following may drastically change over time.

|**In Scope Area**|**Rationale**|**Remarks on Current Direction**|
|---|---|---|
|Developing a minimal OS core that can be updated atomically|Core should be able to be updated atomically frequently without affecting the integrity verification.|Image-based mechanism currently preferred as opposed to either libostree-based or file system (e.g., btrfs) snapshot-based mechanism.|
|Develop an image-based update mechanism|System updates should be available as images (as opposed to package updates).<br><br>If feasible, image updates should also support delta-updates for a bandwidth efficient update experience.|Composable images with image layering to be explored.<br><br>Delta-image generation is also a secondary goal.|
|Develop a boot process using systemd, Unified Kernel Images (UKI), and Discoverable Partitions|Unified Kernel Images (UKI) and Discoverable Disk Images (DDI) to be used to build immutable/verifiable components necessary for the bootable system.|UKI should make it possible to enable Secure Boot and TPM security.<br><br>Discoverable Partitions enable automatic mounting of file systems in their correct respective mount points.|
|Enable Secure Boot along with system integrity verification|UEFI / Secure Boot along with TPM-based security is desirable.<br><br>System integrity should be verified at boot.|dm-verity for integrity verification to be implemented, which should be possible if used with Discoverable Partitions.|
|Handle user overrides to default system configuration|User should be able to make changes to or override the default configuration.|System Extension images in the form of DDIs to be considered.|
|Enable applications via Flatpak and OCI container channels|Tap into the already vibrant and burgeoning community of application delivery through self-contained bundles, namely as flatpaks and OCI-compatible containers.|While package managers can be used within containers, the use of a default package manager is not planned.<br><br>Flatpak and OCI container support to be enabled by default as the primary application delivery channels.|
|Enable applications with hardware access|Enabling direct hardware access or hardware acceleration for applications to be explored.|Direct use of hardware (e.g., GPU, NIC) to be explored with specific use cases in consideration.|

While the above outlines a high-level scope to build a solid base for Asura Linux, there are more technical challenges to be considered, especially within the context of the above and the overarching goal of developing a good user experience. The major challenges identified are listed in the “Challenges” section.  


## Out of Scope

The following should not be expected from Asura Linux within the _next 12 months (October 2023 – September 2024)_. The rationale of why each area is out of scope with further remarks are as follows.

|**Out of Scope Area**|**Rationale**|**Further Remarks**|
|---|---|---|
|Being ready for production or general consumption|Making a general consumer-ready Linux distribution will take time.|Due to the level of experimental and partially implemented features, only those interested in the development of Asura Linux are expected to use it within this period.|
|Developing a new Desktop Environment|A full DE is a complex undertaking which takes a lot of time and effort.<br><br>Therefore, Asura does not have a current plan to develop an own DE.|GNOME is likely to be the default DE in scenarios where a full DE is warranted.<br><br>Other common DEs could be supported later.|
|Avoiding systemd (or developing own init system)|Despite some vocal opposition, systemd remains one of the more important pieces of infrastructure in building modern Linux systems.<br><br>Therefore, Asura does not have any plans to consider an alternative init system, nor develop one.|Necessary parts of systemd will be used by default.|
|Avoiding Wayland|Wayland is the only actively developed and maintained display server stack for Linux.<br><br>Therefore, Asura does not have a current plan to consider alternative display servers.|Wayland will be default whenever a GUI is warranted.<br><br>X.org will only be considered as a legacy fallback mechanism where a GUI is warranted.|
|Supporting multiple architectures|Enabling multiple hardware architecture support is also a resource intensive undertaking.<br><br>Therefore, Asura does not have a plan to support all architectures supported by the Linux kernel.|x86_64 is the only primary architecture planned at the initiation.<br><br>arm64 may be the second architecture to be considered, once rest of the build process is sufficiently automated.<br><br>Additional architectures (including arm64 and riscv) will only be considered in future based on demand and resource availability.|
|Supporting older hardware or older kernels|In order to reduce the workload of the project, older hardware support and old kernel support is not planned.<br><br>Therefore, Asura does not have a plan to support kernel versions before 6.1.x.|Asura will likely run newer kernel releases closer to the latest stable.<br><br>Also see _Supporting multiple architectures_.|
|Doing everything on our own|Asura Linux will not avoid open source projects due to the _Not-Invented-Here_ mindset.<br><br>While we are not merely looking for _faster horses_, we are also not interested in _reinventing the wheel_ whenever wheels are needed.<br><br>More importantly, we believe in open source collaboration.|Asura Linux aims to learn from other open source projects.<br><br>Whenever we are not sure how other open source projects are doing something, our first point of reference would be the [Fedora Linux](https://fedoraproject.org/) project.|



## Challenges

The following are some of the key challenges to be explored by the experimental nature of the immediate scope (in the next 12 months).

- An image-based approach simplifies the update/upgrade process from the current Linux user experience to something akin to a firmware upgrade of mobile phone. However, most of the users will not stop at the base system.
- They will need to install additional software, configure them according to their preference, personalize them, store their data in the system, etc. These needs do not always have convenient user experiences in current image-based Linux systems. Sometimes, the software to address the necessary UX change might not even exist.
- Users will need their system to do more than one thing or fulfill only one role. Their experimentation, entertainment, productivity, learning, and other requirements may need different software environments. The user should be able to do these tasks fearlessly.
- In addition, most existing software assume a traditional OS environment. Their complications and edge-cases with running them in an image-based OS or as a contained workload has not been well explored and usually lack support documentation.
- Ironically, the same things that are supposed to simplify UX currently make it complicated because of the gap in user experience expectation vs technological reality.
- While there is no silver bullet to change this UX gap right away, the experimentation with Asura Linux will always be user-oriented. We intend to collaborate and contribute to other open source project as well as learn from them.
- This is why Asura Linux is defined as *“a project to explore the possibilities in building modern Linux systems focused on user experience enhanced by emerging technologies and concepts.”*


