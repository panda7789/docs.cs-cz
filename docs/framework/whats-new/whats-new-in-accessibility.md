---
title: What's new in accessibility in the .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: 681328af3f3624a8398d5125b952593f2c0510c7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427631"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="b1205-102">What's new in accessibility in the .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b1205-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="b1205-103">The .NET Framework aims at making applications more accessible for your users.</span><span class="sxs-lookup"><span data-stu-id="b1205-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="b1205-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span><span class="sxs-lookup"><span data-stu-id="b1205-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="b1205-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span><span class="sxs-lookup"><span data-stu-id="b1205-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="b1205-106">Accessibility switches</span><span class="sxs-lookup"><span data-stu-id="b1205-106">Accessibility switches</span></span>

<span data-ttu-id="b1205-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span><span class="sxs-lookup"><span data-stu-id="b1205-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="b1205-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span><span class="sxs-lookup"><span data-stu-id="b1205-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="b1205-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span><span class="sxs-lookup"><span data-stu-id="b1205-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="b1205-110">The following are the supported switches:</span><span class="sxs-lookup"><span data-stu-id="b1205-110">The following are the supported switches:</span></span>

|<span data-ttu-id="b1205-111">Version</span><span class="sxs-lookup"><span data-stu-id="b1205-111">Version</span></span>|<span data-ttu-id="b1205-112">Přepínač</span><span class="sxs-lookup"><span data-stu-id="b1205-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="b1205-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="b1205-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="b1205-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="b1205-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="b1205-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="b1205-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="b1205-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="b1205-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="b1205-117">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="b1205-117">.NET Framework 4.8</span></span>|<span data-ttu-id="b1205-118">"Switch.UseLegacyAccessibilityFeatures.3"</span><span class="sxs-lookup"><span data-stu-id="b1205-118">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="b1205-119">Taking advantage of accessibility enhancements</span><span class="sxs-lookup"><span data-stu-id="b1205-119">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="b1205-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span><span class="sxs-lookup"><span data-stu-id="b1205-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="b1205-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span><span class="sxs-lookup"><span data-stu-id="b1205-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="b1205-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="b1205-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="b1205-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1205-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="b1205-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span><span class="sxs-lookup"><span data-stu-id="b1205-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="b1205-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span><span class="sxs-lookup"><span data-stu-id="b1205-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="b1205-126">Restoring legacy behavior</span><span class="sxs-lookup"><span data-stu-id="b1205-126">Restoring legacy behavior</span></span>

<span data-ttu-id="b1205-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span><span class="sxs-lookup"><span data-stu-id="b1205-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="b1205-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span><span class="sxs-lookup"><span data-stu-id="b1205-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="b1205-129">What's new in accessibility in .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="b1205-129">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="b1205-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span><span class="sxs-lookup"><span data-stu-id="b1205-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="b1205-131">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1205-131">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="b1205-132">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b1205-132">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="b1205-133">Windows Workflow Foundation (WF) workflow designer</span><span class="sxs-lookup"><span data-stu-id="b1205-133">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a><span data-ttu-id="b1205-134">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1205-134">Windows Forms</span></span>

<span data-ttu-id="b1205-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span><span class="sxs-lookup"><span data-stu-id="b1205-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="b1205-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span><span class="sxs-lookup"><span data-stu-id="b1205-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="b1205-137">**UIA LiveRegions Support in Labels and StatusStrips**</span><span class="sxs-lookup"><span data-stu-id="b1205-137">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="b1205-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span><span class="sxs-lookup"><span data-stu-id="b1205-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="b1205-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span><span class="sxs-lookup"><span data-stu-id="b1205-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="b1205-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span><span class="sxs-lookup"><span data-stu-id="b1205-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="b1205-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span><span class="sxs-lookup"><span data-stu-id="b1205-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="b1205-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span><span class="sxs-lookup"><span data-stu-id="b1205-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="b1205-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span><span class="sxs-lookup"><span data-stu-id="b1205-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="b1205-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span><span class="sxs-lookup"><span data-stu-id="b1205-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

```csharp
using System;
using System.Windows.Forms;
using System.Windows.Forms.Automation;

namespace WindowsFormsApplication
{
   public partial class UserControl1 : UserControl, IAutomationLiveRegion
   {
      public UserControl1()
      {
         InitializeComponent();
      }

      public AutomationLiveSetting AutomationLiveSetting { get; set; }
      private AutomationLiveSetting IAutomationLiveRegion.GetLiveSetting()
      {
         return this.AutomationLiveSetting;
      }

      protected override void OnTextChanged(EventArgs e)
      {
         base.OnTextChanged(e);
         AutomationNotifications.UiaRaiseLiveRegionChangedEvent(this.AccessibilityObject);
      }
   }
}
```

<span data-ttu-id="b1205-145">**UIA notification events**</span><span class="sxs-lookup"><span data-stu-id="b1205-145">**UIA notification events**</span></span>

<span data-ttu-id="b1205-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span><span class="sxs-lookup"><span data-stu-id="b1205-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="b1205-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span><span class="sxs-lookup"><span data-stu-id="b1205-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="b1205-148">In can also be useful to notify of the progress of some process that may take a long time.</span><span class="sxs-lookup"><span data-stu-id="b1205-148">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="b1205-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span><span class="sxs-lookup"><span data-stu-id="b1205-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span></span>

<span data-ttu-id="b1205-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span><span class="sxs-lookup"><span data-stu-id="b1205-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="b1205-151">**ToolTips on keyboard access**</span><span class="sxs-lookup"><span data-stu-id="b1205-151">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="b1205-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span><span class="sxs-lookup"><span data-stu-id="b1205-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="b1205-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span><span class="sxs-lookup"><span data-stu-id="b1205-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="b1205-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span><span class="sxs-lookup"><span data-stu-id="b1205-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1"/>
   </startup>
   <runtime>
      <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false  -->
      <!-- Please note that disabling Switch.UseLegacyAccessibilityFeatures, Switch.UseLegacyAccessibilityFeatures.2 and Switch.UseLegacyAccessibilityFeatures.3 is required to disable Switch.System.Windows.Forms.UseLegacyToolTipDisplay -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false"/>
   </runtime>
</configuration>
```

<span data-ttu-id="b1205-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span><span class="sxs-lookup"><span data-stu-id="b1205-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![Screenshot of tooltip when user navigates to button with the keyboard.](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="b1205-157">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b1205-157">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="b1205-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span><span class="sxs-lookup"><span data-stu-id="b1205-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="b1205-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span><span class="sxs-lookup"><span data-stu-id="b1205-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="b1205-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span><span class="sxs-lookup"><span data-stu-id="b1205-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="b1205-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span><span class="sxs-lookup"><span data-stu-id="b1205-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="b1205-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span><span class="sxs-lookup"><span data-stu-id="b1205-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="b1205-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span><span class="sxs-lookup"><span data-stu-id="b1205-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="b1205-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span><span class="sxs-lookup"><span data-stu-id="b1205-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="b1205-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1205-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b1205-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span><span class="sxs-lookup"><span data-stu-id="b1205-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="b1205-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span><span class="sxs-lookup"><span data-stu-id="b1205-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="b1205-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span><span class="sxs-lookup"><span data-stu-id="b1205-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="b1205-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span><span class="sxs-lookup"><span data-stu-id="b1205-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="b1205-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span><span class="sxs-lookup"><span data-stu-id="b1205-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="b1205-171">The resulting text selection looks like this:</span><span class="sxs-lookup"><span data-stu-id="b1205-171">The resulting text selection looks like this:</span></span>

![Screenshot of the app running with the words Hello World selected.](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

<span data-ttu-id="b1205-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span><span class="sxs-lookup"><span data-stu-id="b1205-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="b1205-174">**Support for the UIAutomation ControllerFor property**</span><span class="sxs-lookup"><span data-stu-id="b1205-174">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="b1205-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span><span class="sxs-lookup"><span data-stu-id="b1205-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="b1205-176">This property is commonly used for Auto-suggest accessibility.</span><span class="sxs-lookup"><span data-stu-id="b1205-176">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="b1205-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span><span class="sxs-lookup"><span data-stu-id="b1205-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="b1205-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span><span class="sxs-lookup"><span data-stu-id="b1205-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="b1205-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span><span class="sxs-lookup"><span data-stu-id="b1205-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="b1205-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1205-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b1205-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span><span class="sxs-lookup"><span data-stu-id="b1205-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

```csharp
public class AutoSuggestTextBox: TextBox
{
   protected override AutomationPeer OnCreateAutomationPeer()
   {
      return new AutoSuggestTextBoxAutomationPeer(this);
   }

   public ListBox SuggestionListBox;
}

internal class AutoSuggestTextBoxAutomationPeer : TextBoxAutomationPeer
{
   public AutoSuggestTextBoxAutomationPeer(AutoSuggestTextBox owner) : base(owner)
   {
   }

   protected override List<AutomationPeer> GetControlledPeersCore()
   {
      List<AutomationPeer> controlledPeers = new List<AutomationPeer>();
      AutoSuggestTextBox owner = Owner as AutoSuggestTextBox;
      controlledPeers.Add(UIElementAutomationPeer.CreatePeerForElement(owner.SuggestionListBox));
      return controlledPeers;
   }
}
```

<span data-ttu-id="b1205-182">**Tooltips on keyboard access**</span><span class="sxs-lookup"><span data-stu-id="b1205-182">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="b1205-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span><span class="sxs-lookup"><span data-stu-id="b1205-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="b1205-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span><span class="sxs-lookup"><span data-stu-id="b1205-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="b1205-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span><span class="sxs-lookup"><span data-stu-id="b1205-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="b1205-186">The following is a sample application configuration file:</span><span class="sxs-lookup"><span data-stu-id="b1205-186">The following is a sample application configuration file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.UseLegacyToolTipDisplay=false" />
   </runtime>
</configuration>
```

<span data-ttu-id="b1205-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span><span class="sxs-lookup"><span data-stu-id="b1205-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="b1205-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span><span class="sxs-lookup"><span data-stu-id="b1205-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="b1205-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span><span class="sxs-lookup"><span data-stu-id="b1205-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="b1205-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span><span class="sxs-lookup"><span data-stu-id="b1205-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="b1205-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span><span class="sxs-lookup"><span data-stu-id="b1205-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="b1205-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span><span class="sxs-lookup"><span data-stu-id="b1205-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="b1205-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span><span class="sxs-lookup"><span data-stu-id="b1205-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="b1205-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span><span class="sxs-lookup"><span data-stu-id="b1205-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="b1205-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span><span class="sxs-lookup"><span data-stu-id="b1205-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="b1205-196">This can be accomplished in two ways:</span><span class="sxs-lookup"><span data-stu-id="b1205-196">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="b1205-197">By using dependency properties.</span><span class="sxs-lookup"><span data-stu-id="b1205-197">By using dependency properties.</span></span>

  <span data-ttu-id="b1205-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1205-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b1205-199">A developer can use XAML to set their values:</span><span class="sxs-lookup"><span data-stu-id="b1205-199">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="b1205-200">By overriding AutomationPeer virtual methods.</span><span class="sxs-lookup"><span data-stu-id="b1205-200">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="b1205-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span><span class="sxs-lookup"><span data-stu-id="b1205-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="b1205-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span><span class="sxs-lookup"><span data-stu-id="b1205-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

  ```csharp
  public class MyButtonAutomationPeer : ButtonAutomationPeer
  {
    protected override int GetSizeOfSetCore()
    {
        // Call into your own logic to provide a value for SizeOfSet
        return CalculateSizeOfSet();
    }

    protected override int GetPositionInSetCore()
    {
        // Call into your own logic to provide a value for PositionInSet
        return CalculatePositionInSet();
    }
  }
  ```

<span data-ttu-id="b1205-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span><span class="sxs-lookup"><span data-stu-id="b1205-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="b1205-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span><span class="sxs-lookup"><span data-stu-id="b1205-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="b1205-205">Automatic values are not affected by virtualization.</span><span class="sxs-lookup"><span data-stu-id="b1205-205">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="b1205-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span><span class="sxs-lookup"><span data-stu-id="b1205-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="b1205-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="b1205-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="b1205-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span><span class="sxs-lookup"><span data-stu-id="b1205-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
   </runtime>
</configuration>
```

<a name="wf48" />

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="b1205-209">Windows Workflow Foundation (WF) workflow designer</span><span class="sxs-lookup"><span data-stu-id="b1205-209">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="b1205-210">The workflow designer includes the following changes in .NET Framework 4.8:</span><span class="sxs-lookup"><span data-stu-id="b1205-210">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="b1205-211">Users using Narrator will see improvements in FlowSwitch case labels.</span><span class="sxs-lookup"><span data-stu-id="b1205-211">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="b1205-212">Users using Narrator will see improvements in button descriptions.</span><span class="sxs-lookup"><span data-stu-id="b1205-212">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="b1205-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span><span class="sxs-lookup"><span data-stu-id="b1205-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="b1205-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span><span class="sxs-lookup"><span data-stu-id="b1205-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="b1205-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span><span class="sxs-lookup"><span data-stu-id="b1205-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="b1205-216">What's new in accessibility in .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="b1205-216">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="b1205-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span><span class="sxs-lookup"><span data-stu-id="b1205-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="b1205-218">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1205-218">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="b1205-219">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b1205-219">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="b1205-220">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1205-220">Windows Forms</span></span>

<span data-ttu-id="b1205-221">**OS-defined colors in High Contrast themes**</span><span class="sxs-lookup"><span data-stu-id="b1205-221">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="b1205-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span><span class="sxs-lookup"><span data-stu-id="b1205-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="b1205-223">This affects the following controls:</span><span class="sxs-lookup"><span data-stu-id="b1205-223">This affects the following controls:</span></span>

- <span data-ttu-id="b1205-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span><span class="sxs-lookup"><span data-stu-id="b1205-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="b1205-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1205-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b1205-226">Previously, selected text and background colors were not contrasting and were hard to read.</span><span class="sxs-lookup"><span data-stu-id="b1205-226">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="b1205-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span><span class="sxs-lookup"><span data-stu-id="b1205-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="b1205-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span><span class="sxs-lookup"><span data-stu-id="b1205-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="b1205-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="b1205-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="b1205-230">**Narrator improvements**</span><span class="sxs-lookup"><span data-stu-id="b1205-230">**Narrator improvements**</span></span>

<span data-ttu-id="b1205-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span><span class="sxs-lookup"><span data-stu-id="b1205-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="b1205-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="b1205-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="b1205-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span><span class="sxs-lookup"><span data-stu-id="b1205-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="b1205-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span><span class="sxs-lookup"><span data-stu-id="b1205-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="b1205-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span><span class="sxs-lookup"><span data-stu-id="b1205-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="b1205-236">**DataGridView improvements**</span><span class="sxs-lookup"><span data-stu-id="b1205-236">**DataGridView improvements**</span></span>

<span data-ttu-id="b1205-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span><span class="sxs-lookup"><span data-stu-id="b1205-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="b1205-238">Rows can be sorted using the keyboard.</span><span class="sxs-lookup"><span data-stu-id="b1205-238">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="b1205-239">A user can use the F3 key in order to sort by the current column.</span><span class="sxs-lookup"><span data-stu-id="b1205-239">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="b1205-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span><span class="sxs-lookup"><span data-stu-id="b1205-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="b1205-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span><span class="sxs-lookup"><span data-stu-id="b1205-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="b1205-242">**Improved visual cues**</span><span class="sxs-lookup"><span data-stu-id="b1205-242">**Improved visual cues**</span></span>

- <span data-ttu-id="b1205-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span><span class="sxs-lookup"><span data-stu-id="b1205-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="b1205-244">**Improved Property Grid Support**</span><span class="sxs-lookup"><span data-stu-id="b1205-244">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="b1205-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span><span class="sxs-lookup"><span data-stu-id="b1205-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="b1205-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span><span class="sxs-lookup"><span data-stu-id="b1205-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="b1205-247">**Improved keyboard navigation**</span><span class="sxs-lookup"><span data-stu-id="b1205-247">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="b1205-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span><span class="sxs-lookup"><span data-stu-id="b1205-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="b1205-249">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b1205-249">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="b1205-250">**Changes to the CheckBox and RadioButton controls**</span><span class="sxs-lookup"><span data-stu-id="b1205-250">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="b1205-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span><span class="sxs-lookup"><span data-stu-id="b1205-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="b1205-252">These issues occur in cases where the controls do not have any content set.</span><span class="sxs-lookup"><span data-stu-id="b1205-252">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="b1205-253">This can make the transition between themes confusing and the focus visual hard to see.</span><span class="sxs-lookup"><span data-stu-id="b1205-253">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="b1205-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span><span class="sxs-lookup"><span data-stu-id="b1205-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="b1205-255">**WinForms controls hosted in a WPF application**</span><span class="sxs-lookup"><span data-stu-id="b1205-255">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="b1205-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span><span class="sxs-lookup"><span data-stu-id="b1205-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="b1205-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span><span class="sxs-lookup"><span data-stu-id="b1205-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="b1205-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span><span class="sxs-lookup"><span data-stu-id="b1205-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="b1205-259">What's new in accessibility in .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="b1205-259">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="b1205-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span><span class="sxs-lookup"><span data-stu-id="b1205-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="b1205-261">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b1205-261">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="b1205-262">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1205-262">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="b1205-263">ASP.NET web controls</span><span class="sxs-lookup"><span data-stu-id="b1205-263">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="b1205-264">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="b1205-264">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="b1205-265">Windows Workflow Foundation (WF) Workflow Designer</span><span class="sxs-lookup"><span data-stu-id="b1205-265">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="b1205-266">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b1205-266">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="b1205-267">**Screen reader improvements**</span><span class="sxs-lookup"><span data-stu-id="b1205-267">**Screen reader improvements**</span></span>

<span data-ttu-id="b1205-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span><span class="sxs-lookup"><span data-stu-id="b1205-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="b1205-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span><span class="sxs-lookup"><span data-stu-id="b1205-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="b1205-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span><span class="sxs-lookup"><span data-stu-id="b1205-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="b1205-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span><span class="sxs-lookup"><span data-stu-id="b1205-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="b1205-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span><span class="sxs-lookup"><span data-stu-id="b1205-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="b1205-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="b1205-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="b1205-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span><span class="sxs-lookup"><span data-stu-id="b1205-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="b1205-275">This issue is fixed starting with .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="b1205-275">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="b1205-276">**UIAutomation LiveRegion support**</span><span class="sxs-lookup"><span data-stu-id="b1205-276">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="b1205-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span><span class="sxs-lookup"><span data-stu-id="b1205-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="b1205-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span><span class="sxs-lookup"><span data-stu-id="b1205-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="b1205-279">Live regions aim at solving this problem.</span><span class="sxs-lookup"><span data-stu-id="b1205-279">Live regions aim at solving this problem.</span></span> <span data-ttu-id="b1205-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span><span class="sxs-lookup"><span data-stu-id="b1205-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="b1205-281">The screen reader can then decide how and when to inform the user of this change.</span><span class="sxs-lookup"><span data-stu-id="b1205-281">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="b1205-282">To support live regions, the following APIs have been added to WPF:</span><span class="sxs-lookup"><span data-stu-id="b1205-282">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="b1205-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span><span class="sxs-lookup"><span data-stu-id="b1205-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="b1205-284">They can be set by using XAML.</span><span class="sxs-lookup"><span data-stu-id="b1205-284">They can be set by using XAML.</span></span>

- <span data-ttu-id="b1205-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span><span class="sxs-lookup"><span data-stu-id="b1205-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="b1205-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span><span class="sxs-lookup"><span data-stu-id="b1205-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="b1205-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span><span class="sxs-lookup"><span data-stu-id="b1205-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="b1205-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span><span class="sxs-lookup"><span data-stu-id="b1205-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="b1205-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span><span class="sxs-lookup"><span data-stu-id="b1205-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="b1205-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1205-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b1205-291">The element does not send notifications if the content of the live region has changed.</span><span class="sxs-lookup"><span data-stu-id="b1205-291">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="b1205-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1205-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b1205-293">The element sends non-interruptive notifications if the content of the live region has changed.</span><span class="sxs-lookup"><span data-stu-id="b1205-293">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="b1205-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1205-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b1205-295">The element sends interruptive notifications if the content of the live region has changed.</span><span class="sxs-lookup"><span data-stu-id="b1205-295">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="b1205-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span><span class="sxs-lookup"><span data-stu-id="b1205-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="b1205-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span><span class="sxs-lookup"><span data-stu-id="b1205-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="b1205-298">**High contrast**</span><span class="sxs-lookup"><span data-stu-id="b1205-298">**High contrast**</span></span>

<span data-ttu-id="b1205-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span><span class="sxs-lookup"><span data-stu-id="b1205-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="b1205-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span><span class="sxs-lookup"><span data-stu-id="b1205-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="b1205-301">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="b1205-301">These include:</span></span>

- <span data-ttu-id="b1205-302"><xref:System.Windows.Controls.Expander> control</span><span class="sxs-lookup"><span data-stu-id="b1205-302"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="b1205-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span><span class="sxs-lookup"><span data-stu-id="b1205-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="b1205-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span><span class="sxs-lookup"><span data-stu-id="b1205-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="b1205-305">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1205-305">For example:</span></span>

  <span data-ttu-id="b1205-306">Před:</span><span class="sxs-lookup"><span data-stu-id="b1205-306">Before:</span></span> 

  ![Screenshot of the expander control with focus and no focus visual.](./media/whats-new-in-accessibility/expander-control-before.png)

  <span data-ttu-id="b1205-308">After:</span><span class="sxs-lookup"><span data-stu-id="b1205-308">After:</span></span> 

  ![Screenshot of the expander control with focus showing a dotted line around the control's text.](./media/whats-new-in-accessibility/expander-control-after.png)

- <span data-ttu-id="b1205-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span><span class="sxs-lookup"><span data-stu-id="b1205-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="b1205-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span><span class="sxs-lookup"><span data-stu-id="b1205-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="b1205-312">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1205-312">For example:</span></span>

  <span data-ttu-id="b1205-313">Před:</span><span class="sxs-lookup"><span data-stu-id="b1205-313">Before:</span></span> 

  ![Screenshot of radio and check buttons with poor text visibility on high contrast themes.](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  <span data-ttu-id="b1205-315">After:</span><span class="sxs-lookup"><span data-stu-id="b1205-315">After:</span></span> 

  ![Screenshot of radio and check buttons with better text visibility on high contrast themes.](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <span data-ttu-id="b1205-317"><xref:System.Windows.Controls.ComboBox> control</span><span class="sxs-lookup"><span data-stu-id="b1205-317"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="b1205-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span><span class="sxs-lookup"><span data-stu-id="b1205-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="b1205-319">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1205-319">For example:</span></span>

  <span data-ttu-id="b1205-320">Před:</span><span class="sxs-lookup"><span data-stu-id="b1205-320">Before:</span></span> 

  ![Screenshot of a disabled ComboBox with border and control text in different colors.](./media/whats-new-in-accessibility/combo-disabled-before.png)

  <span data-ttu-id="b1205-322">After:</span><span class="sxs-lookup"><span data-stu-id="b1205-322">After:</span></span>   

  ![Screenshot of a disabled ComboBox with border the same color as the control text.](./media/whats-new-in-accessibility/combo-disabled-after.png)

  <span data-ttu-id="b1205-324">In addition, disabled and focused buttons use the correct theme color.</span><span class="sxs-lookup"><span data-stu-id="b1205-324">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="b1205-325">Před:</span><span class="sxs-lookup"><span data-stu-id="b1205-325">Before:</span></span>

  ![Screenshot of a black button with gray text saying Focus Me.](./media/whats-new-in-accessibility/button-theme-colors-before.png) 

  <span data-ttu-id="b1205-327">After:</span><span class="sxs-lookup"><span data-stu-id="b1205-327">After:</span></span> 

  ![Screenshot of a blue button with black text saying Focus Me.](./media/whats-new-in-accessibility/button-theme-colors-after.png) 

  <span data-ttu-id="b1205-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span><span class="sxs-lookup"><span data-stu-id="b1205-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="b1205-330">This issue is fixed starting with .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="b1205-330">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="b1205-331">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1205-331">For example:</span></span>

  <span data-ttu-id="b1205-332">Před:</span><span class="sxs-lookup"><span data-stu-id="b1205-332">Before:</span></span> 

  ![Screenshot of a ComboBox control with an invisible drop-down arrow.](./media/whats-new-in-accessibility/combo-box-style-key-before.png) 

  <span data-ttu-id="b1205-334">After:</span><span class="sxs-lookup"><span data-stu-id="b1205-334">After:</span></span> 

  ![Screenshot of a ComBoxBox control displaying the drop-down arrow.](./media/whats-new-in-accessibility/combo-box-style-key-after.png) 

- <span data-ttu-id="b1205-336"><xref:System.Windows.Controls.DataGrid> control</span><span class="sxs-lookup"><span data-stu-id="b1205-336"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="b1205-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span><span class="sxs-lookup"><span data-stu-id="b1205-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="b1205-338">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1205-338">For example:</span></span>

  <span data-ttu-id="b1205-339">Před:</span><span class="sxs-lookup"><span data-stu-id="b1205-339">Before:</span></span> 

  ![Screenshot of sort indicator arrow before improvements.](./media/whats-new-in-accessibility/sort-indicator-before.png) 

  <span data-ttu-id="b1205-341">After:</span><span class="sxs-lookup"><span data-stu-id="b1205-341">After:</span></span>   

  ![Screenshot of sort indicator arrow after improvements.](./media/whats-new-in-accessibility/sort-indicator-after.png) 

  <span data-ttu-id="b1205-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span><span class="sxs-lookup"><span data-stu-id="b1205-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="b1205-344">This is resolved starting with .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="b1205-344">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="b1205-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="b1205-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="b1205-346">Před:</span><span class="sxs-lookup"><span data-stu-id="b1205-346">Before:</span></span> 

  ![Screenshot of a link saying Click Me!](./media/whats-new-in-accessibility/default-link-style-before.png) 

  <span data-ttu-id="b1205-349">After:</span><span class="sxs-lookup"><span data-stu-id="b1205-349">After:</span></span>    

  ![Screenshot of a link saying Click Me!](./media/whats-new-in-accessibility/default-link-style-after.png) 

<span data-ttu-id="b1205-352">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="b1205-352">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="b1205-353">Windows Forms accessibility improvements</span><span class="sxs-lookup"><span data-stu-id="b1205-353">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="b1205-354">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span><span class="sxs-lookup"><span data-stu-id="b1205-354">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="b1205-355">**Improved display in High Contrast mode**</span><span class="sxs-lookup"><span data-stu-id="b1205-355">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="b1205-356">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span><span class="sxs-lookup"><span data-stu-id="b1205-356">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="b1205-357">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span><span class="sxs-lookup"><span data-stu-id="b1205-357">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="b1205-358">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span><span class="sxs-lookup"><span data-stu-id="b1205-358">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

<span data-ttu-id="b1205-359">Some examples of high contrast changes include:</span><span class="sxs-lookup"><span data-stu-id="b1205-359">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="b1205-360">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span><span class="sxs-lookup"><span data-stu-id="b1205-360">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="b1205-361">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span><span class="sxs-lookup"><span data-stu-id="b1205-361">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="b1205-362">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span><span class="sxs-lookup"><span data-stu-id="b1205-362">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="b1205-363">Disabled text is easier to read.</span><span class="sxs-lookup"><span data-stu-id="b1205-363">Disabled text is easier to read.</span></span> <span data-ttu-id="b1205-364">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b1205-364">For example:</span></span>

  <span data-ttu-id="b1205-365">Před:</span><span class="sxs-lookup"><span data-stu-id="b1205-365">Before:</span></span>

  ![Screenshot of an app that uses different controls running in high contrast mode before accessibility improvements.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png) 

  <span data-ttu-id="b1205-367">After:</span><span class="sxs-lookup"><span data-stu-id="b1205-367">After:</span></span>

  ![Screenshot of an app that uses different controls running in high contrast mode after accessibility improvements.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png) 

- <span data-ttu-id="b1205-369">High contrast improvements in the Thread Exception Dialog.</span><span class="sxs-lookup"><span data-stu-id="b1205-369">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="b1205-370">**Improved Narrator support**</span><span class="sxs-lookup"><span data-stu-id="b1205-370">**Improved Narrator support**</span></span>

<span data-ttu-id="b1205-371">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span><span class="sxs-lookup"><span data-stu-id="b1205-371">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="b1205-372">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span><span class="sxs-lookup"><span data-stu-id="b1205-372">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="b1205-373">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span><span class="sxs-lookup"><span data-stu-id="b1205-373">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="b1205-374">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span><span class="sxs-lookup"><span data-stu-id="b1205-374">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="b1205-375">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span><span class="sxs-lookup"><span data-stu-id="b1205-375">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="b1205-376">**Enhanced support for UIAutomation accessibility patterns**</span><span class="sxs-lookup"><span data-stu-id="b1205-376">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="b1205-377">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span><span class="sxs-lookup"><span data-stu-id="b1205-377">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="b1205-378">These accessibility improvements include:</span><span class="sxs-lookup"><span data-stu-id="b1205-378">These accessibility improvements include:</span></span>

- <span data-ttu-id="b1205-379">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="b1205-379">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="b1205-380">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="b1205-380">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="b1205-381">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="b1205-381">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="b1205-382">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span><span class="sxs-lookup"><span data-stu-id="b1205-382">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="b1205-383">**Improved property browser experience**</span><span class="sxs-lookup"><span data-stu-id="b1205-383">**Improved property browser experience**</span></span>

<span data-ttu-id="b1205-384">Starting with .NET Framework 4.7.1, Windows Forms includes:</span><span class="sxs-lookup"><span data-stu-id="b1205-384">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="b1205-385">Better keyboard navigation through the various drop-down selection windows.</span><span class="sxs-lookup"><span data-stu-id="b1205-385">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="b1205-386">A reduction of unnecessary tab stops.</span><span class="sxs-lookup"><span data-stu-id="b1205-386">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="b1205-387">Better reporting of control types.</span><span class="sxs-lookup"><span data-stu-id="b1205-387">Better reporting of control types.</span></span>
- <span data-ttu-id="b1205-388">Improved narrator behavior.</span><span class="sxs-lookup"><span data-stu-id="b1205-388">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="b1205-389">ASP.NET web controls</span><span class="sxs-lookup"><span data-stu-id="b1205-389">ASP.NET web controls</span></span>

<span data-ttu-id="b1205-390">Starting with .NET Framework 4.7.1 and Visual Studio 2017 version 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b1205-390">Starting with .NET Framework 4.7.1 and Visual Studio 2017 version 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="b1205-391">Changes include the following:</span><span class="sxs-lookup"><span data-stu-id="b1205-391">Changes include the following:</span></span>

- <span data-ttu-id="b1205-392">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span><span class="sxs-lookup"><span data-stu-id="b1205-392">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="b1205-393">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span><span class="sxs-lookup"><span data-stu-id="b1205-393">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="b1205-394">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span><span class="sxs-lookup"><span data-stu-id="b1205-394">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="b1205-395">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="b1205-395">.NET SDK Tools</span></span>

<span data-ttu-id="b1205-396">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span><span class="sxs-lookup"><span data-stu-id="b1205-396">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="b1205-397">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span><span class="sxs-lookup"><span data-stu-id="b1205-397">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="b1205-398">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span><span class="sxs-lookup"><span data-stu-id="b1205-398">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="b1205-399">These enhancements change some previous behaviors, such as keyboard focus order.</span><span class="sxs-lookup"><span data-stu-id="b1205-399">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="b1205-400">Windows Workflow Foundation (WF) Workflow Designer</span><span class="sxs-lookup"><span data-stu-id="b1205-400">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="b1205-401">Accessibility changes in the Workflow Designer include the following:</span><span class="sxs-lookup"><span data-stu-id="b1205-401">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="b1205-402">The tab order changes to left to right and top to bottom in some controls:</span><span class="sxs-lookup"><span data-stu-id="b1205-402">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="b1205-403">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span><span class="sxs-lookup"><span data-stu-id="b1205-403">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="b1205-404">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span><span class="sxs-lookup"><span data-stu-id="b1205-404">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="b1205-405">More functions are available via the keyboard:</span><span class="sxs-lookup"><span data-stu-id="b1205-405">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="b1205-406">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span><span class="sxs-lookup"><span data-stu-id="b1205-406">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="b1205-407">Warning icons are accessible by keyboard.</span><span class="sxs-lookup"><span data-stu-id="b1205-407">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="b1205-408">The **More Properties** button in the **Properties** window is accessible by keyboard.</span><span class="sxs-lookup"><span data-stu-id="b1205-408">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="b1205-409">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span><span class="sxs-lookup"><span data-stu-id="b1205-409">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="b1205-410">Improved visibility of items with focus, such as when:</span><span class="sxs-lookup"><span data-stu-id="b1205-410">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="b1205-411">Adding rows to data grids used by the Workflow Designer and activity designers.</span><span class="sxs-lookup"><span data-stu-id="b1205-411">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="b1205-412">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span><span class="sxs-lookup"><span data-stu-id="b1205-412">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="b1205-413">Setting default values for variables or arguments</span><span class="sxs-lookup"><span data-stu-id="b1205-413">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="b1205-414">Screen readers can now correctly recognize:</span><span class="sxs-lookup"><span data-stu-id="b1205-414">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="b1205-415">Breakpoints set in the workflow designer.</span><span class="sxs-lookup"><span data-stu-id="b1205-415">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="b1205-416">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span><span class="sxs-lookup"><span data-stu-id="b1205-416">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="b1205-417">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span><span class="sxs-lookup"><span data-stu-id="b1205-417">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="b1205-418">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span><span class="sxs-lookup"><span data-stu-id="b1205-418">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="b1205-419">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span><span class="sxs-lookup"><span data-stu-id="b1205-419">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="b1205-420">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="b1205-420">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="b1205-421">State machine transitions and transitions destinations.</span><span class="sxs-lookup"><span data-stu-id="b1205-421">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="b1205-422">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span><span class="sxs-lookup"><span data-stu-id="b1205-422">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="b1205-423">The context (right-click) menus for activities.</span><span class="sxs-lookup"><span data-stu-id="b1205-423">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="b1205-424">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span><span class="sxs-lookup"><span data-stu-id="b1205-424">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="b1205-425">The zoom percentage in the Workflow Designer.</span><span class="sxs-lookup"><span data-stu-id="b1205-425">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="b1205-426">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span><span class="sxs-lookup"><span data-stu-id="b1205-426">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="b1205-427">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span><span class="sxs-lookup"><span data-stu-id="b1205-427">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="b1205-428">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span><span class="sxs-lookup"><span data-stu-id="b1205-428">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="b1205-429">The Browse and Select .NET Type window.</span><span class="sxs-lookup"><span data-stu-id="b1205-429">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="b1205-430">Breadcrumbs in the Workflow Designer.</span><span class="sxs-lookup"><span data-stu-id="b1205-430">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="b1205-431">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span><span class="sxs-lookup"><span data-stu-id="b1205-431">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="b1205-432">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1205-432">See also</span></span>

- [<span data-ttu-id="b1205-433">What's new in the .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b1205-433">What's new in the .NET Framework</span></span>](index.md)
