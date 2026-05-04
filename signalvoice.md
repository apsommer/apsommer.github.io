---
layout: page
title: SignalVoice
background: '/assets/background.webp'
---

<div style="height:40px;"></div>

<img style="display:block;margin:auto;" src="/assets/logo_banner.png" width="70%"/>

<div style="height:30px;"></div>

<p style="text-align:center;max-width:760px;margin:auto;">
SignalVoice is a voice-first Android application that delivers real-time trading signals as short spoken alerts.
Instead of monitoring charts continuously, traders can hear market events as they occur.
</p>

<div style="height:30px;"></div>

<p style="text-align:center;">
<a href="https://play.google.com/store/apps/details?id=com.sommerengineering.signalvoice">
<img src="/assets/play_store_button.png" width="192px"/>
</a>
</p>

<div style="height:20px;"></div>

<hr style="max-width:800px;margin:50px auto;">

<h2 style="text-align:center;">Signal Delivery Architecture</h2>

<p style="text-align:center;max-width:760px;margin:auto;">
SignalVoice operates as a real-time signal pipeline connecting trading platforms
to a mobile audio interface.
</p>

<div style="height:30px;"></div>

<div style="text-align:center;">
    <div style="display:inline-block;background:#434a56;padding:15px;border-radius:6px;border:1px solid #5a6270;">
        <img src="/assets/architecture.svg"
            alt="SignalVoice Architecture"
            style="max-width:520px;width:100%;height:auto;display:block;">
    </div>
</div>

<div style="height:40px;"></div>

<p style="max-width:760px;margin:auto;">
Signals originate from trading platforms such as TradingView and are delivered through a webhook backend to the Android client.
</p>

<div style="height:40px;"></div>

## Signal Generation

<p style="max-width:760px;margin:auto;">
Trading strategies generate signals on each bar close using PineScript or other indicator engines.
These systems trigger webhooks containing a short message describing the signal.
</p>

<div style="height:40px;"></div>

## Webhook Processing

<p style="max-width:760px;margin:auto;">
Incoming webhook requests are received by a lightweight Python service and validated before being written to Firebase Realtime Database.
The backend acts as a distribution layer between signal generators and mobile clients.
</p>

<div style="height:40px;"></div>

## Android Client

<p style="max-width:760px;margin:auto;">
The Android application is written in Kotlin using Jetpack Compose and a coroutine-based architecture.
Signals are persisted locally using Room to ensure reliable ordering and recovery after offline periods.
</p>

<p style="max-width:760px;margin:auto;">
Firebase Cloud Messaging delivers new events to the device, where they are inserted into the local database and processed by the application.
</p>

<div style="height:40px;"></div>

## Voice Delivery

<p style="max-width:760px;margin:auto;">
When a new signal arrives, a foreground service activates the Android Text-to-Speech engine to generate a short spoken alert describing the event.
</p>

<p style="max-width:760px;margin:auto;">
This voice-first design allows traders to monitor market activity without constantly watching charts.
</p>

<div style="height:40px;"></div>

<p style="text-align:center;">
Webhook setup instructions are available in the <a href="/setup">Setup Guide</a>.
</p>

<div style="height:60px;"></div>