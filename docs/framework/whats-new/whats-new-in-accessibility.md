---
title: Co je nového v usnadnění přístupu v rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: afd4b77529f64852e77926b7fecc0e15033e7735
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052691"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="b4365-102">Co je nového v usnadnění přístupu v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b4365-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="b4365-103">Rozhraní .NET Framework, zaměřuje na zpřístupnění aplikace více uživatelům.</span><span class="sxs-lookup"><span data-stu-id="b4365-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="b4365-104">Funkce usnadnění umožnit aplikaci pro zajištění odpovídající prostředí pro uživatele technologie pro usnadnění.</span><span class="sxs-lookup"><span data-stu-id="b4365-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="b4365-105">Od verze rozhraní .NET Framework 4.7.1, rozhraní .NET Framework obsahuje velké množství vylepšení přístupnosti, které umožňují vývojářům vytvářet aplikace přístupné.</span><span class="sxs-lookup"><span data-stu-id="b4365-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="b4365-106">Usnadnění přepínače</span><span class="sxs-lookup"><span data-stu-id="b4365-106">Accessibility switches</span></span>

<span data-ttu-id="b4365-107">Můžete nakonfigurovat aplikaci tak, aby přihlašují funkce pro usnadnění přístupu, pokud cílí na .NET Framework 4.7 nebo starší verzi, ale běží na rozhraní .NET Framework 4.7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="b4365-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="b4365-108">Můžete také konfigurovat aplikace pro použití funkce starší verze (a ne Využijte výhod funkce pro usnadnění přístupu), pokud se zaměřuje na rozhraní .NET Framework 4.7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="b4365-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="b4365-109">Každá verze rozhraní .NET Framework, která zahrnuje funkce pro usnadnění přístupu má specifické pro verzi usnadnění přepínač, který přidáte do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) oddílu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4365-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="b4365-110">Tady jsou podporované přepínače:</span><span class="sxs-lookup"><span data-stu-id="b4365-110">The following are the supported switches:</span></span>

|<span data-ttu-id="b4365-111">Version</span><span class="sxs-lookup"><span data-stu-id="b4365-111">Version</span></span>|<span data-ttu-id="b4365-112">Přepínač</span><span class="sxs-lookup"><span data-stu-id="b4365-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="b4365-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="b4365-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="b4365-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="b4365-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="b4365-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="b4365-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="b4365-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="b4365-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="b4365-117">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="b4365-117">.NET Framework 4.8</span></span>|<span data-ttu-id="b4365-118">"Switch.UseLegacyAccessibilityFeatures.3"</span><span class="sxs-lookup"><span data-stu-id="b4365-118">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="b4365-119">Využití výhod vylepšení přístupnosti</span><span class="sxs-lookup"><span data-stu-id="b4365-119">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="b4365-120">Nové funkce pro usnadnění přístupu se ve výchozím nastavení pro aplikace, které jsou cíleny na rozhraní .NET Framework 4.7.1 povolená nebo novější.</span><span class="sxs-lookup"><span data-stu-id="b4365-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="b4365-121">Kromě toho aplikace, které cílí na starší verzi rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.7.1 nebo později se můžou rozhodnout ze starší verze usnadnění chování (a tím využít výhod vylepšení přístupnosti) tak, že přidáte přepínače [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) oddílu konfiguračního souboru aplikace a nastavení jejich hodnoty na `false`.</span><span class="sxs-lookup"><span data-stu-id="b4365-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="b4365-122">Následující ukazuje, jak můžete vyjádřit výslovný souhlas vylepšení přístupnosti zavedena v rozhraní .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="b4365-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="b4365-123">Pokud budete chtít povolit funkce usnadnění v novější verzi rozhraní .NET Framework, musíte také explicitně připojíte k funkcím z předchozích verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b4365-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="b4365-124">Konfigurace aplikace využít k vylepšení přístupnosti v obou rozhraní .NET Framework 4.7.1 a 4.7.2 vyžaduje následující [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span><span class="sxs-lookup"><span data-stu-id="b4365-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="b4365-125">Vaše aplikace využívat vylepšení přístupnosti v rozhraní .NET Framework 4.7.1 4.7.2 a 4.8 konfigurace vyžaduje následující [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span><span class="sxs-lookup"><span data-stu-id="b4365-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="b4365-126">Obnovit starší chování</span><span class="sxs-lookup"><span data-stu-id="b4365-126">Restoring legacy behavior</span></span>

<span data-ttu-id="b4365-127">Aplikací s cílovou verzí rozhraní .NET Framework 4.7.1 počínaje může zakázat funkce pro usnadnění přístupu přidáním přepínače [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) část konfigurační soubor aplikace a nastavení jejich hodnoty na `true`.</span><span class="sxs-lookup"><span data-stu-id="b4365-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="b4365-128">Například následující konfigurace výslovný představena v rozhraní .NET Framework 4.7.2 funkce pro usnadnění přístupu:</span><span class="sxs-lookup"><span data-stu-id="b4365-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="b4365-129">Co je nového v usnadnění v rozhraní .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="b4365-129">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="b4365-130">4.8 rozhraní .NET framework zahrnuje nové funkce pro usnadnění přístupu v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="b4365-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="b4365-131">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4365-131">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="b4365-132">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b4365-132">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="b4365-133">Návrháře pracovních postupů Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="b4365-133">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a><span data-ttu-id="b4365-134">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4365-134">Windows Forms</span></span>

<span data-ttu-id="b4365-135">Windows Forms v rozhraní .NET Framework 4.8, přidává podporu pro LiveRegions a oznámení události pro mnoho běžně používaných ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="b4365-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="b4365-136">Taky přidává podporu pro popisy tlačítek, když uživatel přejde k ovládacímu prvku pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="b4365-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="b4365-137">**Podpora LiveRegions UIA v popiscích a StatusStrips**</span><span class="sxs-lookup"><span data-stu-id="b4365-137">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="b4365-138">UIA LiveRegions umožňují vývojářům aplikací oznámit čtečky obrazovky změny textu v ovládacím prvku, který se nachází mimo umístění, kde uživatel pracuje.</span><span class="sxs-lookup"><span data-stu-id="b4365-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="b4365-139">To je užitečné, například <xref:System.Windows.Forms.StatusStrip> ovládací prvek, který se zobrazuje stav připojení.</span><span class="sxs-lookup"><span data-stu-id="b4365-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="b4365-140">Pokud připojení se ukončí a změní stav, vývojář může být vhodné upozornit čtečka obrazovky.</span><span class="sxs-lookup"><span data-stu-id="b4365-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="b4365-141">Od verze rozhraní .NET Framework 4.8, Windows Forms implementuje UIA LiveRegions pro obě <xref:System.Windows.Forms.Label> a <xref:System.Windows.Forms.StatusStrip> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="b4365-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="b4365-142">Například následující kód používá LiveRegion v <xref:System.Windows.Forms.Label> ovládací prvek s názvem `label1`:</span><span class="sxs-lookup"><span data-stu-id="b4365-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="b4365-143">Program Předčítání oznamuje bez ohledu na to, kde uživatel pracuje s aplikací "Připraveno".</span><span class="sxs-lookup"><span data-stu-id="b4365-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="b4365-144">Můžete také implementovat vaše <xref:System.Windows.Forms.UserControl> jako LiveRegion:</span><span class="sxs-lookup"><span data-stu-id="b4365-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

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

<span data-ttu-id="b4365-145">**Oznámení události modelu UIA**</span><span class="sxs-lookup"><span data-stu-id="b4365-145">**UIA notification events**</span></span>

<span data-ttu-id="b4365-146">UIA oznámení události, zavedená ve Windows 10 Fall Creators Update, umožňuje aplikaci, aby se vyvolala událost UIA, které vede k Předčítání jednoduše provedení na základě textu oznámení zadejte s událostí, aniž byste museli mít odpovídající ovládací prvek v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b4365-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="b4365-147">V některých scénářích je to jednoduchý způsob, jak výrazně zlepšit dostupnost vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4365-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="b4365-148">V může rovněž hodit oznámení o průběhu nějaký proces, který může trvat dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="b4365-148">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="b4365-149">Další informace o událostech UIA oznámení, naleznete v tématu [vaši desktopovou aplikaci využít novou událost oznámení uživatelského rozhraní?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span><span class="sxs-lookup"><span data-stu-id="b4365-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span></span>

<span data-ttu-id="b4365-150">V následujícím příkladu vyvolává [událost oznámení](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span><span class="sxs-lookup"><span data-stu-id="b4365-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="b4365-151">**Popisy tlačítek na klávesnici přístup**</span><span class="sxs-lookup"><span data-stu-id="b4365-151">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="b4365-152">V aplikacích, které jsou cíleny na rozhraní .NET Framework 4.7.2 a předchozími verzemi, ovládací prvek [popisek](xref:System.Windows.Forms.ToolTip) pouze se dá spouštět na pop up přesunutím ukazatele myši do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b4365-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="b4365-153">Od verze rozhraní .NET Framework 4.8, můžete uživatele klávesnice ovládacího prvku pomocí klávesy Tab nebo klávesy se šipkami, s nebo bez něj modifikační klávesy se zaměříte aktivovat ovládací prvek tooltip.</span><span class="sxs-lookup"><span data-stu-id="b4365-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="b4365-154">Toto vylepšení přístupnosti konkrétní vyžaduje další [přepínač AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span><span class="sxs-lookup"><span data-stu-id="b4365-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

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

<span data-ttu-id="b4365-155">Následující obrázek znázorňuje popis tlačítka, když uživatel vybral nějaké tlačítko pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="b4365-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![Popis tlačítka, když uživatel přejde na tlačítka pomocí klávesnice](media/tooltip.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="b4365-157">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b4365-157">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="b4365-158">Od verze rozhraní .NET Framework 4.8, WPF obsahuje několik vylepšení přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="b4365-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="b4365-159">**Programy pro čtení obrazovky obrazovky už oznamujeme prvky s sbalené nebo skrytý viditelnost**</span><span class="sxs-lookup"><span data-stu-id="b4365-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="b4365-160">Prvky s sbaleném nebo skrytý viditelností jsou už jsme oznámili čtečka obrazovky.</span><span class="sxs-lookup"><span data-stu-id="b4365-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="b4365-161">Uživatelská rozhraní, které obsahují prvky s viditelnost <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> nebo <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> může být neuvede nepravdivý pomocí čtečky obrazovky pokud jejich oznámení uživateli.</span><span class="sxs-lookup"><span data-stu-id="b4365-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="b4365-162">Od verze rozhraní .NET Framework 4.8, WPF již obsahuje sbalený nebo skrytý prvky v ovládacím zobrazení stromu vlastnosti UIAutomation tak čtečky obrazovky můžete oznamujeme už tyto prvky.</span><span class="sxs-lookup"><span data-stu-id="b4365-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="b4365-163">**Vlastnost SelectionTextBrush pro použití s doplněk pro úpravy na základě výběru textu**</span><span class="sxs-lookup"><span data-stu-id="b4365-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="b4365-164">V rozhraní .NET Framework 4.7.2 přidány WPF umožňuje nakreslit <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.PasswordBox> výběr textu bez použití vrstvy pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="b4365-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="b4365-165">Barva popředí vybraného textu v tomto scénáři byl určený <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4365-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b4365-166">Rozhraní .NET framework 4.8 přidá nová vlastnost `SelectionTextBrush`, který umožňuje vývojářům vybrat konkrétní štětec vybraný text při použití jiných doplněk pro úpravy na základě výběru textu.</span><span class="sxs-lookup"><span data-stu-id="b4365-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="b4365-167">Tato vlastnost funguje pouze na <xref:System.Windows.Controls.Primitives.TextBoxBase>-odvozené ovládací prvky a <xref:System.Windows.Controls.PasswordBox> ovládacího prvku v aplikaci WPF se výběr nezaložené doplněk pro úpravy textu povoleno.</span><span class="sxs-lookup"><span data-stu-id="b4365-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="b4365-168">Nelze použít u <xref:System.Windows.Controls.RichTextBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b4365-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="b4365-169">Pokud není povolen výběr nezaložené doplněk pro úpravy textu, tato vlastnost se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="b4365-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="b4365-170">Tuto vlastnost používat, jednoduše ho přidejte do kódu XAML a použijte příslušné štětce nebo vazby.</span><span class="sxs-lookup"><span data-stu-id="b4365-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="b4365-171">Výsledný text výběru vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="b4365-171">The resulting text selection looks like this:</span></span>

![Popis tlačítka, když uživatel přejde na tlačítka pomocí klávesnice](media/selectiontextbrush-property.png)

<span data-ttu-id="b4365-173">Můžete kombinovat používání `SelectionBrush` a `SelectionTextBrush` vlastnosti, které chcete generovat žádné na pozadí a popředí barva kombinaci, která uznáte za vhodné.</span><span class="sxs-lookup"><span data-stu-id="b4365-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="b4365-174">**Podpora pro vlastnost vlastnosti UIAutomation ControllerFor**</span><span class="sxs-lookup"><span data-stu-id="b4365-174">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="b4365-175">Pro vlastnosti UIAutomation `ControllerFor` vlastnost vrací pole Pohyb mezi elementy automatizace, které jsou manipulovat automatizace elementu, který podporuje tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b4365-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="b4365-176">Tato vlastnost se obvykle používá pro automatické návrhy usnadnění přístupu.</span><span class="sxs-lookup"><span data-stu-id="b4365-176">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="b4365-177">`ControllerFor` používá se při automatizaci prvek má vliv na jeden nebo více segmentů aplikace uživatelského rozhraní nebo plochy.</span><span class="sxs-lookup"><span data-stu-id="b4365-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="b4365-178">V opačném případě se těžko přidružit dopad operace ovládací prvky uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b4365-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="b4365-179">Tato funkce přidává možnost zadat hodnotu pro ovládací prvky `ControllerFor` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b4365-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="b4365-180">Rozhraní .NET framework 4.8 přidá novou virtuální metodou, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4365-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b4365-181">K zadání hodnoty pro `ControllerFor` vlastnost, jednoduše přepsat tuto metodu a vrátí `List<AutomationPeer>` pro ovládací prvky se manipulovat situace <xref:System.Windows.Automation.Peers.AutomationPeer>:</span><span class="sxs-lookup"><span data-stu-id="b4365-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

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

<span data-ttu-id="b4365-182">**Popisy tlačítek na klávesnici přístup**</span><span class="sxs-lookup"><span data-stu-id="b4365-182">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="b4365-183">Popisy tlačítek v rozhraní .NET Framework 4.7.2 a dřívějších verzích, zobrazují jenom v případě, že uživatel najede myší na ovládací prvek myší do.</span><span class="sxs-lookup"><span data-stu-id="b4365-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="b4365-184">V rozhraní .NET Framework 4.8 také zobrazit popisy tlačítek na fokus klávesnice i pomocí klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="b4365-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="b4365-185">Pokud chcete tuto funkci povolit, aplikace musí cílit na .NET Framework 4.8 nebo vyjádřit výslovný souhlas s použitím `Switch.UseLegacyAccessibilityFeatures.3` a `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) přepínače.</span><span class="sxs-lookup"><span data-stu-id="b4365-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="b4365-186">Následuje ukázkový soubor konfigurace aplikace:</span><span class="sxs-lookup"><span data-stu-id="b4365-186">The following is a sample application configuration file:</span></span>

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

<span data-ttu-id="b4365-187">Po povolení všechny ovládací prvky, které obsahují popis ji zobrazit, když ovládací prvek dostane fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="b4365-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="b4365-188">Popisek je možné zavřít v čase nebo při změně fokusu klávesnice.</span><span class="sxs-lookup"><span data-stu-id="b4365-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="b4365-189">Uživatelé můžou taky zavřít popis ručně pomocí nové klávesové zkratky, Ctrl + Shift + F10.</span><span class="sxs-lookup"><span data-stu-id="b4365-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="b4365-190">Jakmile se zavře popis tlačítka se může zobrazovat znovu pomocí stejné klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="b4365-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="b4365-191">[Popisy tlačítek pásu karet] (xref:System.Windows.Controls.Ribbon.RibbonToolTips > na <xref:System.Windows.Controls.Ribbon.Ribbon> ovládací prvky se nezobrazí na fokus klávesnice, zobrazí pouze pomocí klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="b4365-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTips> on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="b4365-192">**Přidání podpory pro SizeOfSet a vlastnosti PositionInSet UIAutomation vlastnosti**</span><span class="sxs-lookup"><span data-stu-id="b4365-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="b4365-193">Windows 10 zavedené dvě nové vlastnosti vlastnosti UIAutomation `SizeOfSet` a `PositionInSet`, které se aplikace používají k popisu počet položek v objektu set.</span><span class="sxs-lookup"><span data-stu-id="b4365-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="b4365-194">Vlastnosti UIAutomation klientské aplikace jako čtečky obrazovky můžete dotazovat aplikace pro tyto vlastnosti a oznamujeme přesnou reprezentací uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4365-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="b4365-195">Od verze rozhraní .NET Framework 4.8, WPF zpřístupňuje tyto dvě vlastnosti do vlastnosti UIAutomation v aplikaci WPF.</span><span class="sxs-lookup"><span data-stu-id="b4365-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="b4365-196">Můžete to provést dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="b4365-196">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="b4365-197">Pomocí vlastnosti závislosti.</span><span class="sxs-lookup"><span data-stu-id="b4365-197">By using dependency properties.</span></span>

   <span data-ttu-id="b4365-198">WPF přidá dva nové vlastnosti závislosti <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4365-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b4365-199">Vývojáři mohou využít k nastavení jejich hodnot XAML:</span><span class="sxs-lookup"><span data-stu-id="b4365-199">A developer can use XAML to set their values:</span></span>

   ```xaml
   <Button AutomationProperties.SizeOfSet="3"
     AutomationProperties.PositionInSet="1">Button 1</Button>

   <Button AutomationProperties.SizeOfSet="3"
     AutomationProperties.PositionInSet="2">Button 2</Button>

   <Button AutomationProperties.SizeOfSet="3"
     AutomationProperties.PositionInSet="3">Button 3</Button>
   ```

- <span data-ttu-id="b4365-200">Tak, že přepíšete AutomationPeer virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="b4365-200">By overriding AutomationPeer virtual methods.</span></span>

   <span data-ttu-id="b4365-201"><xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> a <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtuální metody byl přidán do třídy AutomationPeer.</span><span class="sxs-lookup"><span data-stu-id="b4365-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="b4365-202">Vývojář můžete zadat hodnoty pro `SizeOfSet` a `PositionInSet` tak, že přepíšete těchto metod, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b4365-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

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

<span data-ttu-id="b4365-203">Kromě toho položky v <xref:System.Windows.Controls.ItemsControl> instancí zadejte hodnotu pro tyto vlastnosti automaticky bez další akce od vývojáře.</span><span class="sxs-lookup"><span data-stu-id="b4365-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="b4365-204">Pokud <xref:System.Windows.Controls.ItemsControl> je seskupeny, kolekci skupin je reprezentována jako sada a každá skupina se přitom počítá jako samostatné sady s každou položku v rámci této skupiny poskytování jeho pozice v této skupině, jakož i velikost skupiny.</span><span class="sxs-lookup"><span data-stu-id="b4365-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="b4365-205">Automatické hodnoty nejsou ovlivněny virtualizace.</span><span class="sxs-lookup"><span data-stu-id="b4365-205">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="b4365-206">I v případě, že není realizované položku, se stále počítá směrem k celkové velikosti sady a má vliv na pozici v sadě položek na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="b4365-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="b4365-207">Automatické hodnoty jsou zobrazeny pouze, pokud aplikace cílí na .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="b4365-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="b4365-208">Pro aplikace, které jsou cíleny na starší verzi rozhraní .NET Framework, můžete nastavit `Switch.UseLegacyAccessibilityFeatures.3` [přepínač AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), jak je znázorněno v následujícím souboru App.config:</span><span class="sxs-lookup"><span data-stu-id="b4365-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

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

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="b4365-209">Návrháře pracovních postupů Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="b4365-209">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="b4365-210">Návrhář pracovního postupu obsahuje následující změny v rozhraní .NET Framework 4.8:</span><span class="sxs-lookup"><span data-stu-id="b4365-210">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="b4365-211">Uživatele, kteří používají Narrator, se zobrazí vylepšení v popiscích případu FlowSwitch.</span><span class="sxs-lookup"><span data-stu-id="b4365-211">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="b4365-212">Uživatele, kteří používají Předčítání uvidí vylepšení v popisu tlačítka.</span><span class="sxs-lookup"><span data-stu-id="b4365-212">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="b4365-213">Vylepšení v zobrazení návrháře pracovních postupů a jeho ovládacích prvků, jako je lepší kontrastní poměr mezi elementy a snadněji postřehnutelné zaškrtávacími políčky použitých pro elementy fokus uvidí uživatelé, kteří se rozhodnou vysoký kontrast – motivy.</span><span class="sxs-lookup"><span data-stu-id="b4365-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="b4365-214">Pokud vaše aplikace cílí na rozhraní .NET Framework 4.7.2 nebo starší verzi, můžete se rozhodnout do těchto změn tak, že nastavíte `Switch.UseLegacyAccessibilityFeatures.3` [přepínač AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) k `false` v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4365-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="b4365-215">Další informace najdete v tématu [využívat vylepšené přístupnosti](#taking-advantage-of-accessibility-enhancements) části v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="b4365-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="b4365-216">Co je nového v usnadnění v rozhraní .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="b4365-216">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="b4365-217">Rozhraní .NET framework 4.7.2 zahrnuje nové funkce pro usnadnění přístupu v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="b4365-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="b4365-218">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4365-218">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="b4365-219">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b4365-219">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="b4365-220">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4365-220">Windows Forms</span></span>

<span data-ttu-id="b4365-221">**Operační systém definovaných barev v Vysokokontrastních motivech**</span><span class="sxs-lookup"><span data-stu-id="b4365-221">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="b4365-222">Počínaje rozhraním .NET Framework 4.7.2, Windows Forms používá barvám definovaným v Vysokokontrastních motivech v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="b4365-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="b4365-223">Tato akce ovlivní následující ovládací prvky:</span><span class="sxs-lookup"><span data-stu-id="b4365-223">This affects the following controls:</span></span>

- <span data-ttu-id="b4365-224">Na šipku rozevíracího seznamu <xref:System.Windows.Forms.ToolStripDropDownButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b4365-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="b4365-225"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> a <xref:System.Windows.Forms.CheckBox> ovládací prvky s <xref:System.Windows.Forms.ButtonBase.FlatStyle> nastavena na <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4365-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b4365-226">Dříve vybrané barvy textu a pozadí nebyly kontrastní a bylo obtížné číst.</span><span class="sxs-lookup"><span data-stu-id="b4365-226">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="b4365-227">Ovládací prvky obsažené v rámci <xref:System.Windows.Forms.GroupBox> , který má jeho <xref:System.Windows.Forms.Control.Enabled> nastavenou na `false`.</span><span class="sxs-lookup"><span data-stu-id="b4365-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="b4365-228"><xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, A <xref:System.Windows.Forms.ToolStripDropDownButton> ovládací prvky, které mají zvýšené světelnost kontrastní poměr v režimu s vysokým kontrastem.</span><span class="sxs-lookup"><span data-stu-id="b4365-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="b4365-229"><xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> Vlastnost <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="b4365-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="b4365-230">**Vylepšení programu Předčítání**</span><span class="sxs-lookup"><span data-stu-id="b4365-230">**Narrator improvements**</span></span>

<span data-ttu-id="b4365-231">Počínaje rozhraním .NET Framework 4.7.2, je program Předčítání podpory rozšířeného následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b4365-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="b4365-232">Představuje hodnotu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> při uvedení text <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="b4365-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="b4365-233">Označuje, kdy <xref:System.Windows.Forms.ToolStripMenuItem> má jeho <xref:System.Windows.Forms.Control.Enabled> nastavenou na `false`.</span><span class="sxs-lookup"><span data-stu-id="b4365-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="b4365-234">Poskytuje zpětnou vazbu týkající se stavu zaškrtávacího políčka při <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="b4365-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="b4365-235">Program Předčítání na režim kontroly fokus pořadí je konzistentní s visual pořadí ovládacích prvků v dialogovém okně stahování ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="b4365-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="b4365-236">**Vylepšení ovládacího prvku DataGridView**</span><span class="sxs-lookup"><span data-stu-id="b4365-236">**DataGridView improvements**</span></span>

<span data-ttu-id="b4365-237">Počínaje rozhraním .NET Framework 4.7.2, <xref:System.Windows.Forms.DataGridView> ovládací prvek přináší následující vylepšení přístupnosti:</span><span class="sxs-lookup"><span data-stu-id="b4365-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="b4365-238">Lze seřadit řádky pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="b4365-238">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="b4365-239">Uživatele můžete použít klávesy F3 k řazení podle aktuální sloupce.</span><span class="sxs-lookup"><span data-stu-id="b4365-239">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="b4365-240">Když <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, záhlaví sloupce se změní barvu označující aktuální sloupec jako karty uživatele mezi buňkami v aktuálním řádku.</span><span class="sxs-lookup"><span data-stu-id="b4365-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="b4365-241"><xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> Vlastnost <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> vrátí správné nadřazený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="b4365-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="b4365-242">**Vylepšené vizuální prvky**</span><span class="sxs-lookup"><span data-stu-id="b4365-242">**Improved visual cues**</span></span>

- <span data-ttu-id="b4365-243"><xref:System.Windows.Forms.RadioButton> a <xref:System.Windows.Forms.CheckBox> ovládací prvky s prázdnou <xref:System.Windows.Forms.ButtonBase.Text> vlastnost zobrazit indikátor fokus, když obdrží fokus.</span><span class="sxs-lookup"><span data-stu-id="b4365-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="b4365-244">**Podpora vylepšené vlastnost mřížky**</span><span class="sxs-lookup"><span data-stu-id="b4365-244">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="b4365-245"><xref:System.Windows.Forms.PropertyGrid> Ovládací prvek nyní návratový podřízené prvky `true` pro <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> vlastnost, jenom když je povolený prvku PropertyGrid.</span><span class="sxs-lookup"><span data-stu-id="b4365-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="b4365-246"><xref:System.Windows.Forms.PropertyGrid> Ovládacích prvků podřízené návratový `false` pro <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> vlastnost pouze v případě, že uživatel může změnit prvku PropertyGrid.</span><span class="sxs-lookup"><span data-stu-id="b4365-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="b4365-247">**Navigace pomocí kláves vylepšené**</span><span class="sxs-lookup"><span data-stu-id="b4365-247">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="b4365-248"><xref:System.Windows.Forms.ToolStripButton> Ovládací prvek umožňuje fokus, pokud je obsažen v <xref:System.Windows.Forms.ToolStripPanel> , který má <xref:System.Windows.Forms.ToolStripPanel.TabStop> vlastnost nastavena na hodnotu `true`</span><span class="sxs-lookup"><span data-stu-id="b4365-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="b4365-249">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b4365-249">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="b4365-250">**Změny ovládacích prvků CheckBox a ovládacího prvku RadioButton**</span><span class="sxs-lookup"><span data-stu-id="b4365-250">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="b4365-251">V rozhraní .NET Framework 4.7.1 a předchozími verzemi, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> a <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> ovládací prvky mají nekonzistentní a v modelu Classic a Vysoký kontrast motivy, nesprávné fokus vizuály.</span><span class="sxs-lookup"><span data-stu-id="b4365-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="b4365-252">Těmto problémům dochází v případech, ve kterém ovládací prvky nemají žádné sadu obsahu.</span><span class="sxs-lookup"><span data-stu-id="b4365-252">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="b4365-253">Přechod mezi motivy matoucí a vizuál se fokus může být špatně vidět.</span><span class="sxs-lookup"><span data-stu-id="b4365-253">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="b4365-254">V rozhraní .NET Framework 4.7.2 tyto vizuály jsou teď víc konzistentní v rámci celého motivy a snadněji viditelné v modelu Classic a Vysoký kontrast – motivy.</span><span class="sxs-lookup"><span data-stu-id="b4365-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="b4365-255">**Ovládacích prvků WinForms hostované v aplikaci WPF**</span><span class="sxs-lookup"><span data-stu-id="b4365-255">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="b4365-256">Pro ovládací prvek WinForms je hostován v aplikaci WPF v rozhraní .NET Framework 4.7.1 a dřívějších verzích, uživatelé nelze kartu z vrstvy WinForms Pokud je první nebo poslední ovládací prvek v této vrstvě WPF <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b4365-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="b4365-257">V rozhraní .NET Framework 4.7.2 uživatelé mohou nyní na kartě mimo vrstvě WinForms.</span><span class="sxs-lookup"><span data-stu-id="b4365-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="b4365-258">Automatizované aplikace, které spoléhají na fokus nikdy uvození WinForms vrstvy, ale už nemusí fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="b4365-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="b4365-259">Co je nového v usnadnění v rozhraní .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="b4365-259">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="b4365-260">Rozhraní .NET framework 4.7.1 zahrnuje nové funkce pro usnadnění přístupu v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="b4365-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="b4365-261">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b4365-261">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="b4365-262">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4365-262">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="b4365-263">Webové ovládací prvky ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b4365-263">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="b4365-264">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="b4365-264">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="b4365-265">Windows Workflow Foundation (WF), návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="b4365-265">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="b4365-266">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="b4365-266">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="b4365-267">**Vylepšení čtečky obrazovky**</span><span class="sxs-lookup"><span data-stu-id="b4365-267">**Screen reader improvements**</span></span>

<span data-ttu-id="b4365-268">Pokud jsou povolené vylepšení přístupnosti, rozhraní .NET Framework 4.7.1 zahrnuje následující vylepšení, které ovlivňují čtečky obrazovky:</span><span class="sxs-lookup"><span data-stu-id="b4365-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="b4365-269">V rozhraní .NET Framework 4.7 a předchozími verzemi <xref:System.Windows.Controls.Expander> ovládací prvky byly oznamovaný čtečkami obrazovky jako tlačítka.</span><span class="sxs-lookup"><span data-stu-id="b4365-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="b4365-270">Od verze rozhraní .NET Framework 4.7.1, jejich správně oznámení jako rozšíření/sbalitelné skupiny.</span><span class="sxs-lookup"><span data-stu-id="b4365-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="b4365-271">V rozhraní .NET Framework 4.7 a předchozími verzemi <xref:System.Windows.Controls.DataGridCell> ovládací prvky byly oznamovaný čtečkami obrazovky jako "vlastní".</span><span class="sxs-lookup"><span data-stu-id="b4365-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="b4365-272">Od verze rozhraní .NET Framework 4.7.1, že jsou nyní správně uvolněné jako buňka datové mřížky (lokalizované).</span><span class="sxs-lookup"><span data-stu-id="b4365-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="b4365-273">Od verze rozhraní .NET Framework 4.7.1, čtečky obrazovky oznamujeme název upravitelné <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="b4365-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="b4365-274">V rozhraní .NET Framework 4.7 a předchozími verzemi <xref:System.Windows.Controls.PasswordBox> ovládací prvky byly uvolněné jako "žádné položky v zobrazení" nebo měl jinak nesprávné chování.</span><span class="sxs-lookup"><span data-stu-id="b4365-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="b4365-275">Tento problém vyřešen, od verze rozhraní .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="b4365-275">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="b4365-276">**Vlastnosti UIAutomation LiveRegion podpory**</span><span class="sxs-lookup"><span data-stu-id="b4365-276">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="b4365-277">Čtečky obrazovky, jako jsou například lidé pomoc programu Předčítání číst obsah uživatelského rozhraní aplikace, obvykle převod textu na řeč výstupní obsah uživatelského rozhraní, který má fokus.</span><span class="sxs-lookup"><span data-stu-id="b4365-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="b4365-278">Pokud ale prvku uživatelského rozhraní se změní a nemá fokus, uživatel nemusí být upozorněni a přijít o důležité informace.</span><span class="sxs-lookup"><span data-stu-id="b4365-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="b4365-279">Živé oblastech zaměřené na řešení tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="b4365-279">Live regions aim at solving this problem.</span></span> <span data-ttu-id="b4365-280">Vývojář můžete využít k informování čtečky obrazovky nebo jakéhokoli klienta vlastnosti UIAutomation, který byl proveden důležité změny prvku uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b4365-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="b4365-281">Čtečka obrazovky se můžete rozhodnout používat jak a kdy informovat uživatele o této změně.</span><span class="sxs-lookup"><span data-stu-id="b4365-281">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="b4365-282">Pro podporu živé oblastí, jsme přidali následující rozhraní API k použití WPF:</span><span class="sxs-lookup"><span data-stu-id="b4365-282">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="b4365-283"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> pole, které identifikovat **LiveSetting** vlastnost a **LiveRegionChanged** událostí.</span><span class="sxs-lookup"><span data-stu-id="b4365-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="b4365-284">Můžete třeba nastavit pomocí XAML.</span><span class="sxs-lookup"><span data-stu-id="b4365-284">They can be set by using XAML.</span></span>

- <span data-ttu-id="b4365-285">**AutomationProperties.LiveSetting** přidružená vlastnost, která informuje o čtečka obrazovky významné změny uživatelského rozhraní pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="b4365-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="b4365-286"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Vlastnost, která identifikuje **AutomationProperties.LiveSetting** přidružená vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b4365-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="b4365-287"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Metodu, která může být potlačena za účelem poskytují **LiveSetting** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b4365-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="b4365-288"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> metody, které get a set **LiveSetting** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b4365-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="b4365-289"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Výčet, který definuje následující možné **LiveSetting** hodnoty:</span><span class="sxs-lookup"><span data-stu-id="b4365-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="b4365-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4365-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b4365-291">Element neodešle oznámení, pokud došlo ke změně obsahu aktivní oblast.</span><span class="sxs-lookup"><span data-stu-id="b4365-291">The element does not send notifications if the content of the live region has changed.</span></span>
   - <span data-ttu-id="b4365-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4365-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b4365-293">Element odešle-interruptive oznámení, pokud došlo ke změně obsahu aktivní oblast.</span><span class="sxs-lookup"><span data-stu-id="b4365-293">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

   - <span data-ttu-id="b4365-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4365-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="b4365-295">Element odešle interruptive oznámení, pokud došlo ke změně obsahu aktivní oblast.</span><span class="sxs-lookup"><span data-stu-id="b4365-295">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="b4365-296">Můžete vytvořit LiveRegion nastavením **AutomationProperties.LiveSetting** vlastnosti prvku, která vás zajímá, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b4365-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="b4365-297">Při změně dat v živé oblasti a je potřeba informovat čtečky obrazovky, můžete explicitně vyvolat událost, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b4365-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="b4365-298">**Vysoký kontrast**</span><span class="sxs-lookup"><span data-stu-id="b4365-298">**High contrast**</span></span>

<span data-ttu-id="b4365-299">Od verze rozhraní .NET Framework 4.7.1, vylepšení ve vysokém kontrastu byly provedeny na různé ovládací prvky WPF.</span><span class="sxs-lookup"><span data-stu-id="b4365-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="b4365-300">Jsou nyní viditelné při <xref:System.Windows.SystemParameters.HighContrast%2A> je nastavený.</span><span class="sxs-lookup"><span data-stu-id="b4365-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="b4365-301">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="b4365-301">These include:</span></span>

- <span data-ttu-id="b4365-302"><xref:System.Windows.Controls.Expander> Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b4365-302"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="b4365-303">Visual pro zaměření <xref:System.Windows.Controls.Expander> je nyní ovládací prvek viditelný.</span><span class="sxs-lookup"><span data-stu-id="b4365-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="b4365-304">Vizuály klávesnice pro <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, a <xref:System.Windows.Controls.RadioButton> ovládací prvky jsou také viditelné.</span><span class="sxs-lookup"><span data-stu-id="b4365-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="b4365-305">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b4365-305">For example:</span></span>

    <span data-ttu-id="b4365-306">Před:</span><span class="sxs-lookup"><span data-stu-id="b4365-306">Before:</span></span> 

    ![Rozšíření – ovládací prvek s fokusem před vylepšení přístupnosti](media/expander-before.png)

    <span data-ttu-id="b4365-308">Po:</span><span class="sxs-lookup"><span data-stu-id="b4365-308">After:</span></span> 

    ![Rozšíření – ovládací prvek s fokusem po vylepšení přístupnosti](media/expander-after.png)

- <span data-ttu-id="b4365-310"><xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.RadioButton> ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="b4365-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

    <span data-ttu-id="b4365-311">Text <xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.RadioButton> ovládacích prvků je teď snazší zjistit při výběru v vysokokontrastních motivech.</span><span class="sxs-lookup"><span data-stu-id="b4365-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="b4365-312">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b4365-312">For example:</span></span>

    <span data-ttu-id="b4365-313">Před:</span><span class="sxs-lookup"><span data-stu-id="b4365-313">Before:</span></span> 

    ![Vysoký kontrast – přepínač s fokusem před vylepšení přístupnosti](media/radio-button-before.png)

    <span data-ttu-id="b4365-315">Po:</span><span class="sxs-lookup"><span data-stu-id="b4365-315">After:</span></span> 

    ![Vysoký kontrast – přepínač s fokusem po vylepšení přístupnosti](media/radio-button-after.png)

- <span data-ttu-id="b4365-317"><xref:System.Windows.Controls.ComboBox> Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b4365-317"><xref:System.Windows.Controls.ComboBox> control</span></span>

    <span data-ttu-id="b4365-318">Od verze rozhraní .NET Framework 4.7.1, ohraničení zakázané <xref:System.Windows.Controls.ComboBox> ovládací prvek se stejnou barvu jako neaktivního textu.</span><span class="sxs-lookup"><span data-stu-id="b4365-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="b4365-319">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b4365-319">For example:</span></span>

    <span data-ttu-id="b4365-320">Před:</span><span class="sxs-lookup"><span data-stu-id="b4365-320">Before:</span></span> 

     ![Pole se seznamem zakázané ohraničení a text před vylepšení přístupnosti](media/combo-disabled-before.png)

    <span data-ttu-id="b4365-322">Po:</span><span class="sxs-lookup"><span data-stu-id="b4365-322">After:</span></span>   

     ![Pole se seznamem zakázané ohraničení a text po vylepšení přístupnosti](media/combo-disabled-after.png)

    <span data-ttu-id="b4365-324">Kromě toho tlačítka zakázáno a zaměřují se používají Barva motivu správné.</span><span class="sxs-lookup"><span data-stu-id="b4365-324">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="b4365-325">Před:</span><span class="sxs-lookup"><span data-stu-id="b4365-325">Before:</span></span>

    ![Tlačítko barvy motivu před vylepšení přístupnosti](media/button-themes-before.png) 

    <span data-ttu-id="b4365-327">Po:</span><span class="sxs-lookup"><span data-stu-id="b4365-327">After:</span></span> 

    ![Tlačítko barvy motivu po vylepšení přístupnosti](media/button-themes-after.png) 

    <span data-ttu-id="b4365-329">Nakonec v rozhraní .NET Framework 4.7 a předchozími verzemi, nastavení <xref:System.Windows.Controls.ComboBox> stylu ovládacího prvku na `Toolbar.ComboBoxStyleKey` způsobila na šipku rozevíracího seznamu byla neviditelná.</span><span class="sxs-lookup"><span data-stu-id="b4365-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="b4365-330">Tento problém vyřešen, od verze rozhraní .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="b4365-330">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="b4365-331">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b4365-331">For example:</span></span>

    <span data-ttu-id="b4365-332">Před:</span><span class="sxs-lookup"><span data-stu-id="b4365-332">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey před vylepšení přístupnosti](media/comboboxstylekey-before.png) 

    <span data-ttu-id="b4365-334">Po:</span><span class="sxs-lookup"><span data-stu-id="b4365-334">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey po vylepšení přístupnosti](media/comboboxstylekey-after.png) 

- <span data-ttu-id="b4365-336"><xref:System.Windows.Controls.DataGrid> Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="b4365-336"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="b4365-337">Od verze rozhraní .NET Framework 4.7.1, šipku indikátor řazení v <xref:System.Windows.Controls.DataGrid> řídí teď používá opravte barvy motivu.</span><span class="sxs-lookup"><span data-stu-id="b4365-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="b4365-338">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b4365-338">For example:</span></span>

    <span data-ttu-id="b4365-339">Před:</span><span class="sxs-lookup"><span data-stu-id="b4365-339">Before:</span></span> 

    ![Šipka řazení před vylepšení přístupnosti](media/sort-indicator-before.png) 

    <span data-ttu-id="b4365-341">Po:</span><span class="sxs-lookup"><span data-stu-id="b4365-341">After:</span></span>   

    ![Řazení šipka po vylepšení přístupnosti](media/sort-indicator-after.png) 

    <span data-ttu-id="b4365-343">Kromě toho v rozhraní .NET Framework 4.7 a dřívějších verzích výchozí styl odkaz změnit k nesprávné barvě po pozastavení ukazatele myši v režimu vysokého kontrastu.</span><span class="sxs-lookup"><span data-stu-id="b4365-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="b4365-344">Tento problém nevyřeší, od verze rozhraní .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="b4365-344">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="b4365-345">Obdobně <xref:System.Windows.Controls.DataGrid> sloupce zaškrtávací políčko používá očekávané barvy pro zpětnou vazbu fokus klávesnice, která je od verze rozhraní .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="b4365-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="b4365-346">Před:</span><span class="sxs-lookup"><span data-stu-id="b4365-346">Before:</span></span> 

    ![DataGrid – výchozí odkaz styl před vylepšení přístupnosti](media/default-link-style-before.png) 

    <span data-ttu-id="b4365-348">Po:</span><span class="sxs-lookup"><span data-stu-id="b4365-348">After:</span></span>    

    ![DataGrid – výchozí odkaz styl po vylepšení přístupnosti](media/default-link-style-after.png) 

<span data-ttu-id="b4365-350">Další informace o vylepšení přístupnosti WPF v rozhraní .NET Framework 4.7.1 najdete v tématu [vylepšení přístupnosti v subsystému WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="b4365-350">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="b4365-351">Vylepšení přístupnosti Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b4365-351">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="b4365-352">V rozhraní .NET Framework 4.7.1 Windows Forms (WinForms) zahrnuje usnadnění změny v následujících oblastech.</span><span class="sxs-lookup"><span data-stu-id="b4365-352">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="b4365-353">**Vylepšené zobrazení v režim s vysokým kontrastem**</span><span class="sxs-lookup"><span data-stu-id="b4365-353">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="b4365-354">Od verze rozhraní .NET Framework 4.7.1, různých ovládacích prvků WinForms nabízí vylepšené vykreslování v režimech funkce Vysoký kontrast v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="b4365-354">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="b4365-355">Windows 10 došlo ke změně hodnoty pro některé vysoký kontrast – barvy system a Windows Forms je založená na platformě Windows 10 Win32.</span><span class="sxs-lookup"><span data-stu-id="b4365-355">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="b4365-356">Pro dosažení co nejlepších výsledků spusťte na nejnovější verzi Windows a vyjádřit výslovný souhlas s nejnovějšími změnami operačního systému tak, že přidáte soubor app.manifest v aplikaci test a zrušení comment Windows 10 nepodporují řádku operačního systému tak, aby následující:</span><span class="sxs-lookup"><span data-stu-id="b4365-356">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

<span data-ttu-id="b4365-357">Mezi příklady vysoký kontrast – změny patří:</span><span class="sxs-lookup"><span data-stu-id="b4365-357">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="b4365-358">Značek zaškrtnutí v <xref:System.Windows.Forms.MenuStrip> položky jsou usnadňuje zobrazení.</span><span class="sxs-lookup"><span data-stu-id="b4365-358">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="b4365-359">Pokud je vybráno, zakázané <xref:System.Windows.Forms.MenuStrip> položky jsou usnadňuje zobrazení.</span><span class="sxs-lookup"><span data-stu-id="b4365-359">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="b4365-360">Text ve vybrané <xref:System.Windows.Forms.Button> řídit liší od tradičnější barvu výběru.</span><span class="sxs-lookup"><span data-stu-id="b4365-360">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="b4365-361">Neaktivní text je lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="b4365-361">Disabled text is easier to read.</span></span> <span data-ttu-id="b4365-362">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b4365-362">For example:</span></span>

    <span data-ttu-id="b4365-363">Před:</span><span class="sxs-lookup"><span data-stu-id="b4365-363">Before:</span></span>

    ![Neaktivní text před vylepšení přístupnosti](media/wf-disabled-before.png) 

    <span data-ttu-id="b4365-365">Po:</span><span class="sxs-lookup"><span data-stu-id="b4365-365">After:</span></span>

    ![Neaktivní text po vylepšení přístupnosti](media/wf-disabled-after.png) 

- <span data-ttu-id="b4365-367">Vysoký kontrast – vylepšení v dialogovém okně výjimky vlákna.</span><span class="sxs-lookup"><span data-stu-id="b4365-367">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="b4365-368">**Vylepšená podpora Předčítání**</span><span class="sxs-lookup"><span data-stu-id="b4365-368">**Improved Narrator support**</span></span>

<span data-ttu-id="b4365-369">Windows Forms v rozhraní .NET Framework 4.7.1 zahrnuje následující vylepšení přístupnosti Narrator:</span><span class="sxs-lookup"><span data-stu-id="b4365-369">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="b4365-370"><xref:System.Windows.Forms.MonthCalendar> Ovládací prvek je přístupný podle program Předčítání, a další nástroje pro automatizaci uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b4365-370">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="b4365-371"><xref:System.Windows.Forms.CheckedListBox> Ovládací prvek upozorní Předčítání při změně stavu zaškrtnutí položky tak, že se uživatel dozví, že jste se změnil hodnotu ovládacího prvku položky seznamu.</span><span class="sxs-lookup"><span data-stu-id="b4365-371">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="b4365-372"><xref:System.Windows.Forms.DataGridViewCell> Ovládací prvek sestavy Předčítání správný stav jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="b4365-372">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="b4365-373">Program Předčítání teď dokáže číst zakázáno <xref:System.Windows.Forms.ToolStripMenuItem> text, zatímco dříve by přeskočit prostřednictvím položky nabídky zakázané.</span><span class="sxs-lookup"><span data-stu-id="b4365-373">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="b4365-374">**Vylepšená podpora pro vlastnosti UIAutomation usnadnění vzory**</span><span class="sxs-lookup"><span data-stu-id="b4365-374">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="b4365-375">Od verze rozhraní .NET Framework 4.7.1, můžou využívat technologie usnadnění vývoje sofwaru bez běžných vzorů pro usnadnění rozhraní API a vlastnosti pro několik ovládacích prvků WinForms.</span><span class="sxs-lookup"><span data-stu-id="b4365-375">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="b4365-376">Vylepšení usnadnění přístupu patří:</span><span class="sxs-lookup"><span data-stu-id="b4365-376">These accessibility improvements include:</span></span>

- <span data-ttu-id="b4365-377"><xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ToolStripSplitButton> teď podporují [Rozbalit/sbalit vzor](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="b4365-377">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="b4365-378"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> Teď podporuje [vzoru přepínání](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="b4365-378">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="b4365-379"><xref:System.Windows.Forms.ToolStripItem> Podporuje ovládací prvek <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> vlastnost a [Rozbalit/sbalit vzor](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="b4365-379">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="b4365-380"><xref:System.Windows.Forms.NumericUpDown> a <xref:System.Windows.Forms.DomainUpDown> řídí podporu <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b4365-380">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="b4365-381">**Vylepšené vlastnost prohlížeče prostředí**</span><span class="sxs-lookup"><span data-stu-id="b4365-381">**Improved property browser experience**</span></span>

<span data-ttu-id="b4365-382">Od verze rozhraní .NET Framework 4.7.1, Windows Forms obsahuje:</span><span class="sxs-lookup"><span data-stu-id="b4365-382">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="b4365-383">Lepší navigaci pomocí klávesnice prostřednictvím různých windows rozevíracího seznamu výběru.</span><span class="sxs-lookup"><span data-stu-id="b4365-383">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="b4365-384">Snížení zbytečné tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="b4365-384">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="b4365-385">Lepší vytváření sestav, typů ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="b4365-385">Better reporting of control types.</span></span>
- <span data-ttu-id="b4365-386">Vylepšené Předčítání chování.</span><span class="sxs-lookup"><span data-stu-id="b4365-386">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="b4365-387">Webové ovládací prvky ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b4365-387">ASP.NET web controls</span></span>

<span data-ttu-id="b4365-388">Od verze rozhraní .NET Framework 4.7.1 a Visual Studio 2017 15.3, ASP.NET zlepšuje, jak fungují ovládací prvky technologie ASP.NET webové technologie usnadnění v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b4365-388">Starting with .NET Framework 4.7.1 and Visual Studio 2017 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="b4365-389">Změny patří:</span><span class="sxs-lookup"><span data-stu-id="b4365-389">Changes include the following:</span></span>

- <span data-ttu-id="b4365-390">Změny pro implementaci chybějící vzory usnadnění přístupu uživatelského rozhraní v ovládacích prvcích, jako je třeba **přidat pole** dialogového okna v **zobrazení podrobností o** průvodce, nebo **konfigurace ListView** dialogové okno **ListView** průvodce.</span><span class="sxs-lookup"><span data-stu-id="b4365-390">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="b4365-391">Změny s cílem zobrazit v režimu vysokého kontrastu, jako je třeba **Editor pole stránkování dat**.</span><span class="sxs-lookup"><span data-stu-id="b4365-391">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="b4365-392">Změny pro zlepšení navigace klávesnice, prostředí pro ovládací prvky, jako je třeba **pole** dialogového okna v **úpravy polí stránkování** průvodce ovládací prvek DataPager **Konfigurovat ObjectContext**  dialogového okna, nebo **Konfigurovat výběr dat** dialogové okno **konfigurace zdroje dat** průvodce.</span><span class="sxs-lookup"><span data-stu-id="b4365-392">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="b4365-393">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="b4365-393">.NET SDK Tools</span></span>

<span data-ttu-id="b4365-394">[Nástroj Configuration Editor (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) a [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) byly vylepšeny opravou různých usnadnění.</span><span class="sxs-lookup"><span data-stu-id="b4365-394">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="b4365-395">Většina z nich byly malé problémy, jako je název nedefinují nebo určité vzory pro automatizaci uživatelského rozhraní nebyl správně implementována.</span><span class="sxs-lookup"><span data-stu-id="b4365-395">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="b4365-396">Přestože mnoho uživatelů nebude vědět o těchto nesprávné hodnoty, zákazníci, kteří používají podpůrnou technologií, jako je čtečky obrazovky najdete tyto sady SDK nástroje přístupnější.</span><span class="sxs-lookup"><span data-stu-id="b4365-396">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="b4365-397">Tato vylepšení změnit některé předchozí chování, jako je například pořadí fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="b4365-397">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="b4365-398">Windows Workflow Foundation (WF), návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="b4365-398">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="b4365-399">Usnadnění změny v Návrháři postupu provádění, patří:</span><span class="sxs-lookup"><span data-stu-id="b4365-399">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="b4365-400">Změní pořadí zleva doprava a shora dolů v některé ovládací prvky:</span><span class="sxs-lookup"><span data-stu-id="b4365-400">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="b4365-401">Okno Inicializace korelace pro korelaci dat pro nastavení <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b4365-401">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="b4365-402">V okně Definice obsahu <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b4365-402">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="b4365-403">Další funkce jsou k dispozici prostřednictvím klávesnice:</span><span class="sxs-lookup"><span data-stu-id="b4365-403">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="b4365-404">Při úpravě vlastností aktivity, skupiny vlastností můžete sbalit pomocí klávesnice, zaměřuje prvním.</span><span class="sxs-lookup"><span data-stu-id="b4365-404">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="b4365-405">Varovné ikony jsou přístupné pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="b4365-405">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="b4365-406">**Více vlastností** tlačítko **vlastnosti** okno přístupný pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="b4365-406">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="b4365-407">Uživatelé klávesnice můžete přistupovat k položky hlavičky v **argumenty** a **proměnné** podoken návrháře postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="b4365-407">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="b4365-408">Vylepšená viditelnost položek s fokusem, jako např. kdy:</span><span class="sxs-lookup"><span data-stu-id="b4365-408">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="b4365-409">Přidání řádků do datových mřížek používají návrháři návrháře pracovních postupů a aktivit.</span><span class="sxs-lookup"><span data-stu-id="b4365-409">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="b4365-410">Procházíte polí <xref:System.ServiceModel.Activities.ReceiveReply> a <xref:System.ServiceModel.Activities.SendReply> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b4365-410">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="b4365-411">Nastavení výchozích hodnot proměnných nebo argumentů</span><span class="sxs-lookup"><span data-stu-id="b4365-411">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="b4365-412">Čtečky obrazovky nyní správně rozpozná:</span><span class="sxs-lookup"><span data-stu-id="b4365-412">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="b4365-413">Zarážky nastavené v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="b4365-413">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="b4365-414"><xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, A <xref:System.ServiceModel.Activities.CorrelationScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b4365-414">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="b4365-415">Obsah <xref:System.ServiceModel.Activities.Receive> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b4365-415">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="b4365-416">Cílový typ pro <xref:System.Activities.Statements.InvokeMethod> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b4365-416">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="b4365-417">Pole se seznamem výjimek a nakonec v části <xref:System.Activities.Statements.TryCatch> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b4365-417">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="b4365-418">Pole se seznamem typ zprávy, rozdělovač v okně Přidat inicializátory korelace, okno Definice obsahu a okno definice vlastnosti CorrelatesOn v zasílání zpráv aktivity (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, a <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="b4365-418">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="b4365-419">Stavový stroj přechody a přechody cíle.</span><span class="sxs-lookup"><span data-stu-id="b4365-419">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="b4365-420">Poznámky a konektory na <xref:System.Activities.Statements.FlowDecision> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b4365-420">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="b4365-421">(Klikněte pravým tlačítkem) kontextové nabídky pro aktivity.</span><span class="sxs-lookup"><span data-stu-id="b4365-421">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="b4365-422">Do editorů hodnot vlastnost, tlačítko Vymazat hledání, podle kategorie a tlačítka abecední řazení a dialogové okno Editor výrazů v mřížce vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b4365-422">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="b4365-423">Procento zvětšení v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="b4365-423">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="b4365-424">Oddělovač v <xref:System.Activities.Statements.Parallel> a <xref:System.Activities.Statements.Pick> aktivity.</span><span class="sxs-lookup"><span data-stu-id="b4365-424">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="b4365-425"><xref:System.Activities.Statements.InvokeDelegate> Aktivity.</span><span class="sxs-lookup"><span data-stu-id="b4365-425">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="b4365-426">V okně vyberte typy aktivit slovník (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`atd.).</span><span class="sxs-lookup"><span data-stu-id="b4365-426">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="b4365-427">Okno Procházet a vybrat typ .NET.</span><span class="sxs-lookup"><span data-stu-id="b4365-427">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="b4365-428">V Návrháři pracovních postupů s popisem cesty.</span><span class="sxs-lookup"><span data-stu-id="b4365-428">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="b4365-429">Uživatelé, kteří se rozhodnou vysoký kontrast – motivy uvidí řady vylepšení v zobrazení návrháře pracovních postupů a jeho ovládacích prvků, jako je lepší kontrastní poměr mezi elementy a snadněji postřehnutelné zaškrtávacími políčky použitých pro elementy fokus.</span><span class="sxs-lookup"><span data-stu-id="b4365-429">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4365-430">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4365-430">See also</span></span>

- [<span data-ttu-id="b4365-431">Co je nového v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b4365-431">What's new in the .NET Framework</span></span>](whats-new.md)
