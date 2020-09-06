# Project Pix Art Messenger

The [Pix Art Messenger](https://jabber.pix-art.de/) is an Android Jabber Client. This project extends the messenger to support the
(not officially specified) room configuration `muc#roomconfig_videoroom`. If present in the discovery information, the value is considered to be an URL to a Jitsi conference room. A video icon is displayed and a click directly opens a conference activity.

To use the extended functionality, the mentioned room configuration must be present. Since this is a non standard extension, a modified XMPP server is needed to provide the necessary information.

A further extension can be to derive a conference room name from the MUC Jabber ID and use a public jitsi server like [meet.golem.de](https://meet.golem.de/).

The Jitsi call is generic and can be used in any app. Just include the two classes

	org.jitsi.meet.sdk.JitsiMeetConferenceOptions
	org.jitsi.meet.sdk.JitsiMeetUserInfo

into the project. Configure the options and call the `launch` method with an appropriate context:

	new JitsiMeetConferenceOptions.Builder().setUserInfo(userInfos).setRoom(videoRoom).build().launch(activity);

(taken from `ConversionFragment`).

All icons are based on emojis designed by [OpenMoji - the open-source emoji and icon project](https://openmoji.org/).


### Installation

The repository consists of two parts: The jitsi folder contains
an Android Studio Project introducing a simple app with just
one activity starting the Jitsi Conference from an appropriate intent. For a documentation I refer to [the Jitsi Meet project](https://github.com/jitsi/jitsi-meet/) and documentation on the [Jitsi home page](https://jitsi.org/).

The second part overrides code in the [Pix Art Messenger repository on GitHub](https://github.com/kriztan/Pix-Art-Messenger). Just clone the original repository (in version 2.5.2) and copy the code. Build the messenger and install.


