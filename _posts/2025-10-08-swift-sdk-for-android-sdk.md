---
layout: new-layouts/post
published: false
date: 2025-10-08 10:00:00
title: "Introducing Swift SDK for Android"
author: [compnerd, finagolfin, marcprux]
category: "Developer Tools"
---

Swift has matured significantly over the past decade — extending from [cloud services](https://www.swift.org/blog/swift-on-the-server-ecosystem/) to [Windows applications](https://www.swift.org/blog/swift-on-windows/), browser applications, and [microcontrollers](https://www.swift.org/blog/embedded-swift-examples/). Today, we're pleased to announce a major milestone: the Swift SDK for Android.

This release reflects many years of dedicated community effort. With the SDK now available, (editor's note: link here to downloadable SDK snapshots, once those are live) developers can begin building Android applications in Swift, opening new avenues for cross-platform development and accelerating innovation across the mobile ecosystem.

## Swift’s Android Journey: From Port to Production

Once Swift development became open source in 2015, interest in Swift on Android sparked almost immediately. Within days of the Swift Open Source Project’s launch — when the compiler and standard library were published — Zhuowei Zhang (@zhuowei) explored a [proof‑of‑concept Android port](https://lists.swift.org/pipermail/swift-dev/Week-of-Mon-20151207/000171.html). A group of engineers soon organized a systematic port: Brian Gesiak (@modocache), Tom Birch (@froody), @tienex, Will Dillon (@hpux735), and Saleem Abdulrasool (@compnerd) added a Linux ARMv7 port and, building on that foundation, refined Android support until the standard library operated fully on Android.

Momentum continued when [Geordie at Flowkey wrote about](https://medium.com/@ephemer/why-we-put-an-app-in-the-android-play-store-using-swift-96ac87c88dfc) submitting an Android app built with Swift just seven months later — among the earliest production deployments on Android- then launched [their cross-platform UIKit](https://github.com/flowkey/UIKit-cross-platform).  Amr Aboelela carried the work forward, followed by Readdle’s [writing about their Spark app](https://medium.com/android-news/swift-for-android-our-experience-and-tools-7a2f0ba58ab3) and a Swift cross‑compilation toolchain; soon after, [the community gained](https://github.com/swiftlang/swift-community-hosted-continuous-integration/pull/2) donated, hosted Continuous Integration (CI).

Saleem Abdulrasool and Daniel Rodríguez Troitiño (@drodriguez) strengthened Android support further: enhancing build infrastructure, integrating ICU into the runtime, and migrating from STLPort to libc++ in response to changes in Android’s C++ environment. They stabilized the test suite on Android and enabled remote testing, ensuring continuous validation on real devices.

Right after, @finagolfin added the Android target to the Swift Package Manager and released a complete Swift toolchain that runs natively on Android via [the Termux app](https://termux.dev).

With Swift functioning on Android, engineers from The Browser Company — Alex Lorenz (@hyp) and Saleem — advanced C++ interoperability on the platform, culminating in a shipping proof‑of‑concept library: [swift‑firebase](https://github.com/compnerd/swift-firebase). The library leverages Swift–C++ interop to expose a Swift interface for Firebase, enabling applications to share core code across platforms.

Recently, Marc Prud'hommeaux (@marcprux) from [Skip.tools](https://skip.tools) worked with @finagolfin to get CI building installable Swift SDKs from nightly Swift snapshots. This effort was used in turn by the Swift Package Index's [addition of Android](https://swiftpackageindex.com/blog/adding-wasm-and-android-compatibility-testing) to their compatibility build matrix.

These highlights capture only a fraction of a long, methodical porting journey shaped by contributions from many individuals and organizations. With the formation of the [Android workgroup](/android-workgroup/) this year, the community is aligning to accelerate and deepen Swift’s presence on Android.

With this groundwork in place, interoperability became the next priority — bridging Swift with Android’s Java and Kotlin ecosystem.

## Swift–Java Interop: Building Native Android Experiences

Android was designed to be architecture‑agnostic, relying primarily on Java — and, increasingly, Kotlin — for system interaction. While the Android Native Development Kit (NDK) exposes a broad native API surface, many platform capabilities and parts of the application lifecycle are accessible only through the Java environment.

Swift can produce native code that runs on top of the NDK runtime libraries, but native execution alone is insufficient for rich Android applications. To deliver truly native experiences, developers must interoperate with Java. One of Swift’s defining strengths is its ability to bridge languages cleanly.

[The swift‑java project](https://github.com/swiftlang/swift-java), part of the Swift Open Source ecosystem, enables bidirectional interoperability between Swift and Java. Swift’s Java interop was announced a little over a year ago at [ServerSide.swift](https://serversideswift.info), and recently Mads Odgaard (@madsodgaard) [discussed his work applying it for Android](https://youtube.com/watch?v=96IQAA7Nl8E&t=982s).

Interoperability is necessary, but not sufficient. Rigorous testing ensures the system holds up in practice.

## Testing on Android: ~99% Pass Rate (Compiler + Libraries)

Robust test suites are a cornerstone of software engineering, ensuring changes behave as intended. Compiler toolchains and platform SDKs are no exception. Swift maintains an extensive suite that verifies compiler outputs and a comprehensive set of tests covering the standard and core libraries.

Extending support to Android required the same rigor. Encouragingly, the Android effort achieves ~99% pass rates. The coverage spans static validation of compiler output and execution tests of the Swift standard and core libraries on Android, providing strong confidence in platform stability.

With the system stabilized, clear references and examples help the community move faster.

## Documentation & Samples: Guides and End‑to‑End Projects

We’re now preparing clear reference documentation: an early draft of the [getting‑started guide](https://github.com/swiftlang/swift-org-website/pull/985) (editor's note: plan to get this published soon and linked directly, not the pull request) is available and will transition to swift.org for ongoing maintenance within the Swift Open Source Project.

Practical examples are equally valuable. Andriy Druk (@andriydruk) from Readdle [has published sample projects](https://github.com/andriydruk/swift-android-samples) that demonstrate end‑to‑end application workflows on Android.

The Android SDK is available as part of the installer for Windows or as a Swift SDK for Linux and macOS.

To focus collective effort, the workgroup [defines a shared roadmap](https://github.com/orgs/swiftlang/projects/17).

<!--
- TODO: https://www.swift.org/documentation/articles/swift-android-getting-started.html
-->

## Swift on Android in Production Today

Android’s reach is immense, and has until now been the "final frontier" for Swift becoming a truly universal development language. Swift has become an attractive approach to building applications across all platforms — mobile, desktop, and server — from a single shared codebase.

Building Android apps with Swift is not just a theory. Swift is today running natively on millions of Android devices around the world, powering apps like [Spark](https://play.google.com/store/apps/details?id=com.readdle.spark), [Flowkey](https://play.google.com/store/apps/details?id=com.flowkey.app), and [Naturitas](https://play.google.com/store/apps/details?id=com.naturitas.android).

The workgroup is [advancing a vision document](https://github.com/swiftlang/swift-evolution/pull/2946) for Swift on Android, currently under review. This vision will outline priority areas and guide community efforts to maximize impact across the ecosystem.

Open source thrives on diverse contributions. Join us and help shape Swift’s evolution on Android.
