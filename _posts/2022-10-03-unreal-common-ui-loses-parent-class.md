---
layout: post
title: "Unreal Common UI Loses Parent Class"
date: 2022-10-03 21:00
description: How to work around an issue with Common UI Blueprints losing their parent class in a C++ based project
categories: Game-Development
---

Recently I've been enjoying learning more about [Common UI](https://docs.unrealengine.com/5.0/en-US/common-ui-plugin-for-advanced-user-interfaces-in-unreal-engine/), the new-ish Unreal UI system that's used in Fortnite. The new widgets, input system, and navigation make it easy to quickly put together [menu flows](https://dev.epicgames.com/community/learning/tutorials/BKJ7/unreal-engine-common-ui-tutorial-create-cross-platform-ui-easily-with-this-new-ue5-system). However, every now and then in my C++ based projects Blueprint classes keep losing their parent class. The end result is that when I open my uproject all the `CommonUI.CommmonActivatableWidget`'s are corrupted. The Blueprint's themselves no longer able to be opened. Entire UI, broken. 😭

I was nearing a breaking point this weekend, contemplating going back to UMG when I stumbled across this [forum](https://forums.unrealengine.com/t/blueprint-keeps-losing-parent/538652) post. In the `Blueprint Keeps Losing Parent` post, which was unrelated to Common UI, the group comes to the conclusion that the bug is a side effect of the Live Coding feature introduced in UE 4.22. In other side projects I have Live Coding disabled as it's caused a number of frustrating issues when opening the editor. For instance working on my [intersection testing](https://github.com/coderchrismills/UnrealPlayground) demo, actors like `NearestPointToLineActor` would fail to load and would result in a broken Level file. Since then I've been disabling it, but forgot to do so in my Common UI playgrounds. Disabling Live Coding as "fixed" my issue. I just need to make sure run through Visual Studio rather than launching through the Epic Launcher. If you really need Live Coding enabled and you run into this, here's a "quick" way to fix things up. 

1. Hope you're using source control or have a backup
2. Close the editor
3. Delete corrupted blueprints
4. Rebuild from Visual Studio
5. Open the editor or launch from VS
6. Force sync / replace corrupted blueprints from backup while the editor is open

The only annoyance I've run into with this workaround is that I had to manually fix up any Blueprints that had a `Create Widget` node as the out value from them was broken. 