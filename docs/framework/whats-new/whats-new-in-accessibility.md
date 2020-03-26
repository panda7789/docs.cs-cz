---
title: Co je nového v usnadnění v rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: 4243599f44749e7b38ebe78ca88b8ec2a9390650
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249718"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="67883-102">Co je nového v usnadnění v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="67883-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="67883-103">Rozhraní .NET Framework má za cíl zpřístupnit aplikace uživatelům.</span><span class="sxs-lookup"><span data-stu-id="67883-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="67883-104">Funkce usnadnění umožňují aplikaci poskytovat uživatelům asistenční technologie odpovídající prostředí.</span><span class="sxs-lookup"><span data-stu-id="67883-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="67883-105">Počínaje rozhraním .NET Framework 4.7.1 obsahuje rozhraní .NET Framework velké množství vylepšení usnadnění, která vývojářům umožňují vytvářet přístupné aplikace.</span><span class="sxs-lookup"><span data-stu-id="67883-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="67883-106">Přepínače přístupnosti</span><span class="sxs-lookup"><span data-stu-id="67883-106">Accessibility switches</span></span>

<span data-ttu-id="67883-107">Aplikaci můžete nakonfigurovat tak, aby se přihlásila k funkcím usnadnění přístupu, pokud cílí na rozhraní .NET Framework 4.7 nebo starší verzi, ale běží v rozhraní .NET Framework 4.7.1 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="67883-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="67883-108">Aplikaci můžete také nakonfigurovat tak, aby používala starší funkce (a nevyužívala funkce usnadnění), pokud cílí na rozhraní .NET Framework 4.7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="67883-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="67883-109">Každá verze rozhraní .NET Framework, která obsahuje funkce usnadnění přístupu, [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) má přepínač [`<runtime>`](../configure-apps/file-schema/runtime/index.md) usnadnění specifický pro verzi, který přidáte do prvku v části konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="67883-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="67883-110">Podporované přepínače jsou následující:</span><span class="sxs-lookup"><span data-stu-id="67883-110">The following are the supported switches:</span></span>

|<span data-ttu-id="67883-111">Version</span><span class="sxs-lookup"><span data-stu-id="67883-111">Version</span></span>|<span data-ttu-id="67883-112">Přepínač</span><span class="sxs-lookup"><span data-stu-id="67883-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="67883-113">Rozhraní .NET 4.7.1</span><span class="sxs-lookup"><span data-stu-id="67883-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="67883-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="67883-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="67883-115"> .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="67883-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="67883-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="67883-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="67883-117"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="67883-117">.NET Framework 4.8</span></span>|<span data-ttu-id="67883-118">"Switch.UseLegacyAccessibilityFeatures.3"</span><span class="sxs-lookup"><span data-stu-id="67883-118">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="67883-119">Využití vylepšení přístupnosti</span><span class="sxs-lookup"><span data-stu-id="67883-119">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="67883-120">Nové funkce usnadnění jsou ve výchozím nastavení povoleny pro aplikace, které cílí na rozhraní .NET Framework 4.7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="67883-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="67883-121">Kromě toho aplikace, které cílí na starší verzi rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.7.1 nebo novější, se [`<runtime>`](../configure-apps/file-schema/runtime/index.md) mohou odhlásit z chování přístupnosti `false`starší verze (a tím využít vylepšení usnadnění) přidáním přepínačů do [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvku v části konfiguračního souboru aplikace a nastavením jejich hodnoty na .</span><span class="sxs-lookup"><span data-stu-id="67883-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="67883-122">Následující text ukazuje, jak se přihlásit k vylepšením přístupnosti zavedeným v rozhraní .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="67883-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="67883-123">Pokud se rozhodnete přihlásit k funkcím usnadnění v novější verzi rozhraní .NET Framework, musíte se také explicitně přihlásit k funkcím z dřívějších verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67883-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="67883-124">Konfigurace aplikace tak, aby využívala vylepšení usnadnění v rozhraní .NET Framework 4.7.1 a 4.7.2, vyžaduje následující [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek:</span><span class="sxs-lookup"><span data-stu-id="67883-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="67883-125">Konfigurace aplikace tak, aby využívala vylepšení usnadnění v rozhraní .NET Framework 4.7.1, 4.7.2 a 4.8, vyžaduje následující [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek:</span><span class="sxs-lookup"><span data-stu-id="67883-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="67883-126">Obnovení chování starší verze</span><span class="sxs-lookup"><span data-stu-id="67883-126">Restoring legacy behavior</span></span>

<span data-ttu-id="67883-127">Aplikace, které cílí na verze rozhraní .NET Framework začínající 4.7.1, mohou [`<runtime>`](../configure-apps/file-schema/runtime/index.md) zakázat funkce usnadnění přidáním přepínačů `true`do [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvku v části konfiguračního souboru aplikace a nastavením jejich hodnoty na .</span><span class="sxs-lookup"><span data-stu-id="67883-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="67883-128">Například následující konfigurace se odhlásí z funkcí usnadnění zavedených v rozhraní .NET Framework 4.7.2:</span><span class="sxs-lookup"><span data-stu-id="67883-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="67883-129">Co je nového v usnadnění v rozhraní .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="67883-129">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="67883-130">Rozhraní .NET Framework 4.8 obsahuje nové funkce usnadnění v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="67883-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="67883-131">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67883-131">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="67883-132">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="67883-132">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="67883-133">Návrhář pracovních postupů Nadace pracovního postupu systému Windows (WF)</span><span class="sxs-lookup"><span data-stu-id="67883-133">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a><span data-ttu-id="67883-134">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67883-134">Windows Forms</span></span>

<span data-ttu-id="67883-135">V rozhraní .NET Framework 4.8 přidá Windows Forms podporu pro LiveRegions a události oznámení pro mnoho běžně používaných ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="67883-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="67883-136">Přidává také podporu pro popisky, když uživatel přejde na ovládací prvek pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="67883-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="67883-137">**Podpora UIA LiveRegions v popiscích a stavových proužcích**</span><span class="sxs-lookup"><span data-stu-id="67883-137">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="67883-138">UIA LiveRegions umožňují vývojářům aplikací upozornit programy pro čtení z obrazovky na změnu textu v ovládacím prvku, který je umístěn na rozdíl od umístění, kde uživatel pracuje.</span><span class="sxs-lookup"><span data-stu-id="67883-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="67883-139">To je užitečné například <xref:System.Windows.Forms.StatusStrip> pro ovládací prvek, který zobrazuje stav připojení.</span><span class="sxs-lookup"><span data-stu-id="67883-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="67883-140">Pokud je připojení přerušeno a stav se změní, může vývojář chtít upozornit program pro čtení z obrazovky.</span><span class="sxs-lookup"><span data-stu-id="67883-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="67883-141">Počínaje rozhraním .NET Framework 4.8 implementuje windows forms <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.StatusStrip> u iia liveregions pro ovládací prvky i ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="67883-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="67883-142">Například následující kód používá LiveRegion <xref:System.Windows.Forms.Label> v `label1`ovládacím prvku s názvem :</span><span class="sxs-lookup"><span data-stu-id="67883-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="67883-143">Předčítání oznamuje "Ready" bez ohledu na to, kde uživatel pracuje s aplikací.</span><span class="sxs-lookup"><span data-stu-id="67883-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="67883-144">Můžete také implementovat jako <xref:System.Windows.Forms.UserControl> LiveRegion:</span><span class="sxs-lookup"><span data-stu-id="67883-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

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

<span data-ttu-id="67883-145">**Události oznámení UIA**</span><span class="sxs-lookup"><span data-stu-id="67883-145">**UIA notification events**</span></span>

<span data-ttu-id="67883-146">Událost Oznámení UIA, která byla zavedena v aktualizaci Windows 10 Fall Creators Update, umožňuje vaší aplikaci vyvolat událost UIA, což vede k tomu, že Předčítání jednoduše dělá oznámení na základě textu, který zadáte s událostí, aniž byste museli mít odpovídající ovládací prvek v ui.</span><span class="sxs-lookup"><span data-stu-id="67883-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="67883-147">V některých případech se jedná o jednoduchý způsob, jak výrazně zlepšit dostupnost aplikace.</span><span class="sxs-lookup"><span data-stu-id="67883-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="67883-148">V může být také užitečné upozornit na průběh některého procesu, který může trvat dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="67883-148">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="67883-149">Další informace o událostech oznámení UIA najdete v tématu [Může vaše aplikace klasické pracovní plochy využít novou událost oznámení o uznaci?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span><span class="sxs-lookup"><span data-stu-id="67883-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span></span>

<span data-ttu-id="67883-150">Následující příklad vyvolá [událost oznámení](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span><span class="sxs-lookup"><span data-stu-id="67883-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="67883-151">**Popisy nástrojů pro přístup pomocí klávesnice**</span><span class="sxs-lookup"><span data-stu-id="67883-151">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="67883-152">V aplikacích, které cílí na rozhraní .NET Framework 4.7.2 a starší verze, lze aktivovat [pouze popis ovládacího prvku,](xref:System.Windows.Forms.ToolTip) který se zobrazí přesunutím ukazatele myši do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="67883-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="67883-153">Počínaje rozhraním .NET Framework 4.8 může uživatel klávesnice aktivovat popisek ovládacího prvku zaostřením ovládacího prvku pomocí kláves y Tab nebo kláves se šipkami pomocí modifikačních kláves nebo bez něj.</span><span class="sxs-lookup"><span data-stu-id="67883-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="67883-154">Toto konkrétní vylepšení usnadnění vyžaduje další [přepínač AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span><span class="sxs-lookup"><span data-stu-id="67883-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

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

<span data-ttu-id="67883-155">Následující obrázek znázorňuje popis, když uživatel vybral tlačítko s klávesnicí.</span><span class="sxs-lookup"><span data-stu-id="67883-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![Snímek obrazovky s popisem, když uživatel přejde na tlačítko pomocí klávesnice.](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="67883-157">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="67883-157">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="67883-158">Počínaje rozhraním .NET Framework 4.8 obsahuje wpf řadu vylepšení usnadnění.</span><span class="sxs-lookup"><span data-stu-id="67883-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="67883-159">**Předčítání obrazovky již neoznamují prvky s viditelností Sbalené nebo Skryté**</span><span class="sxs-lookup"><span data-stu-id="67883-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="67883-160">Prvky se sbalenou nebo skrytou viditelností již program pro čtení z obrazovky neoznamují.</span><span class="sxs-lookup"><span data-stu-id="67883-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="67883-161">Uživatelská rozhraní, která obsahují prvky s viditelnost <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> nebo <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> mohou být zkresleny programy pro čtení z obrazovky, pokud jsou oznámeny uživateli.</span><span class="sxs-lookup"><span data-stu-id="67883-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="67883-162">Počínaje rozhraním .NET Framework 4.8 již WPF neobsahuje sbalené nebo skryté prvky v ovládacím zobrazení stromu UIAutomation, takže programy pro čtení z obrazovky již nemohou tyto prvky oznamovat.</span><span class="sxs-lookup"><span data-stu-id="67883-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="67883-163">**Vlastnost SelectionTextBrush pro použití s výběrem textu nezaloženým na Adorneru**</span><span class="sxs-lookup"><span data-stu-id="67883-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="67883-164">V rozhraní .NET Framework 4.7.2 wpf <xref:System.Windows.Controls.TextBox> přidal <xref:System.Windows.Controls.PasswordBox> možnost kreslit a výběr textu bez použití vrstvy Adorner.</span><span class="sxs-lookup"><span data-stu-id="67883-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="67883-165">Barva popředí vybraného textu v tomto scénáři <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>byla dána .</span><span class="sxs-lookup"><span data-stu-id="67883-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="67883-166">Rozhraní .NET Framework 4.8 `SelectionTextBrush`přidá novou vlastnost , která umožňuje vývojářům vybrat konkrétní stopu pro vybraný text při použití výběru textu nezaložené na Adorner.</span><span class="sxs-lookup"><span data-stu-id="67883-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="67883-167">Tato vlastnost funguje <xref:System.Windows.Controls.Primitives.TextBoxBase>pouze na -derived ovládací prvky a <xref:System.Windows.Controls.PasswordBox> ovládací prvek v aplikacích WPF s non-Adorner-založené výběr textu povolena.</span><span class="sxs-lookup"><span data-stu-id="67883-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="67883-168">Nefunguje na ovládací <xref:System.Windows.Controls.RichTextBox> prvek.</span><span class="sxs-lookup"><span data-stu-id="67883-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="67883-169">Pokud není povolen výběr textu na bázi Adorner, tato vlastnost je ignorována.</span><span class="sxs-lookup"><span data-stu-id="67883-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="67883-170">Chcete-li použít tuto vlastnost, jednoduše ji přidejte do kódu XAML a použijte příslušnou stopu nebo vazbu.</span><span class="sxs-lookup"><span data-stu-id="67883-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="67883-171">Výsledný výběr textu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="67883-171">The resulting text selection looks like this:</span></span>

![Snímek obrazovky aplikace spuštěné se slovy Hello World selected.](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

<span data-ttu-id="67883-173">Můžete kombinovat použití `SelectionBrush` vlastností `SelectionTextBrush` a generovat libovolnou kombinaci barev pozadí a popředí, kterou považujete za vhodnou.</span><span class="sxs-lookup"><span data-stu-id="67883-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="67883-174">**Podpora vlastnosti UIAutomation ControllerFor**</span><span class="sxs-lookup"><span data-stu-id="67883-174">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="67883-175">`ControllerFor` UIAutomation vlastnost vrátí pole automatizace prvků, které jsou manipulovány prvkautomatizace, který podporuje tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="67883-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="67883-176">Tato vlastnost se běžně používá pro automatické navrhování usnadnění přístupu.</span><span class="sxs-lookup"><span data-stu-id="67883-176">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="67883-177">`ControllerFor`se používá, když prvek automatizace ovlivňuje jeden nebo více segmentů uživatelského rozhraní aplikace nebo plochy.</span><span class="sxs-lookup"><span data-stu-id="67883-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="67883-178">V opačném případě je obtížné přidružit dopad operace ovládacího prvku s prvky uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67883-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="67883-179">Tato funkce přidává možnost pro ovládací prvky poskytnout hodnotu `ControllerFor` pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="67883-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="67883-180">Rozhraní .NET Framework 4.8 přidává <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>novou virtuální metodu . .</span><span class="sxs-lookup"><span data-stu-id="67883-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="67883-181">Chcete-li zadat `ControllerFor` hodnotu vlastnosti, jednoduše přepsat `List<AutomationPeer>` tuto metodu a <xref:System.Windows.Automation.Peers.AutomationPeer>vrátit pro ovládací prvky, s nimiž se manipuluje tímto :</span><span class="sxs-lookup"><span data-stu-id="67883-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

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

<span data-ttu-id="67883-182">**Popisy k přístupu z klávesnice**</span><span class="sxs-lookup"><span data-stu-id="67883-182">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="67883-183">V rozhraní .NET Framework 4.7.2 a starších verzích se popisky zobrazují pouze v případě, že uživatel najedete kurzorem myši nad ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="67883-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="67883-184">V rozhraní .NET Framework 4.8 se popisky zobrazují také na fokusklávesnice a také pomocí klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="67883-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="67883-185">Chcete-li tuto funkci povolit, aplikace musí cílit na rozhraní `Switch.UseLegacyAccessibilityFeatures.3` .NET Framework 4.8 nebo opt-in pomocí přepínačů a `Switch.UseLegacyToolTipDisplay` [AppContext.](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)</span><span class="sxs-lookup"><span data-stu-id="67883-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="67883-186">Následuje ukázkový konfigurační soubor aplikace:</span><span class="sxs-lookup"><span data-stu-id="67883-186">The following is a sample application configuration file:</span></span>

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

<span data-ttu-id="67883-187">Po povolení se všechny ovládací prvky, které obsahují popisek, zobrazí, jakmile ovládací prvek obdrží fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="67883-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="67883-188">Popisek lze v průběhu času nebo při změně fokusu klávesnice zavřít.</span><span class="sxs-lookup"><span data-stu-id="67883-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="67883-189">Uživatelé mohou také ručně zavřít popisek pomocí nové klávesové zkratky Ctrl + Shift + F10.</span><span class="sxs-lookup"><span data-stu-id="67883-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="67883-190">Jakmile je popisek zamítnut, lze jej znovu zobrazit pomocí stejné klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="67883-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="67883-191">[Popisky pásu karet](xref:System.Windows.Controls.Ribbon.RibbonToolTip) na <xref:System.Windows.Controls.Ribbon.Ribbon> ovládacích prvcích se při fokusu klávesnice nezobrazují; zobrazují se pouze pomocí klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="67883-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="67883-192">**Přidána podpora vlastností SizeOfSet a PositionInSet UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="67883-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="67883-193">Windows 10 představil dvě nové vlastnosti UIAutomation `SizeOfSet` a `PositionInSet`, které používají aplikace k popisu počtu položek v sadě.</span><span class="sxs-lookup"><span data-stu-id="67883-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="67883-194">UIAutomation klientské aplikace, jako jsou programy pro čtení z obrazovky pak dotaz aplikace pro tyto vlastnosti a oznámit přesnou reprezentaci uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="67883-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="67883-195">Počínaje rozhraním .NET Framework 4.8 wpf zpřístupňuje tyto dvě vlastnosti UIAutomation v aplikacích WPF.</span><span class="sxs-lookup"><span data-stu-id="67883-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="67883-196">Toho lze dosáhnout dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="67883-196">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="67883-197">Pomocí vlastností závislostí.</span><span class="sxs-lookup"><span data-stu-id="67883-197">By using dependency properties.</span></span>

  <span data-ttu-id="67883-198">WPF přidá dvě nové <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> vlastnosti závislostí a <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="67883-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="67883-199">Vývojář může použít XAML k nastavení jejich hodnot:</span><span class="sxs-lookup"><span data-stu-id="67883-199">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="67883-200">Přepsáním AutomationPeer virtuální metody.</span><span class="sxs-lookup"><span data-stu-id="67883-200">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="67883-201">A <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtuální metody byly přidány do třídy AutomationPeer.</span><span class="sxs-lookup"><span data-stu-id="67883-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="67883-202">Vývojář může poskytnout `SizeOfSet` hodnoty `PositionInSet` pro a přepsáním těchto metod, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="67883-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

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

<span data-ttu-id="67883-203">Kromě toho položky v <xref:System.Windows.Controls.ItemsControl> instancích poskytují hodnotu pro tyto vlastnosti automaticky bez další akce od vývojáře.</span><span class="sxs-lookup"><span data-stu-id="67883-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="67883-204">Pokud <xref:System.Windows.Controls.ItemsControl> je seskupena, kolekce skupin je reprezentována jako sada a každá skupina se počítá jako samostatná sada, přičemž každá položka uvnitř této skupiny poskytuje své umístění uvnitř této skupiny a velikost skupiny.</span><span class="sxs-lookup"><span data-stu-id="67883-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="67883-205">Automatické hodnoty nejsou ovlivněny virtualizací.</span><span class="sxs-lookup"><span data-stu-id="67883-205">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="67883-206">I v případě, že položka není realizována, je stále započítána do celkové velikosti sady a ovlivňuje pozici v sadě položek na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="67883-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="67883-207">Automatické hodnoty jsou k dispozici pouze v případě, že aplikace cíle .NET Framework 4.8.</span><span class="sxs-lookup"><span data-stu-id="67883-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="67883-208">U aplikací, které cílí na starší verzi rozhraní `Switch.UseLegacyAccessibilityFeatures.3` .NET Framework, můžete nastavit [přepínač AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), jak je znázorněno v následujícím souboru App.config:</span><span class="sxs-lookup"><span data-stu-id="67883-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

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

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="67883-209">Návrhář pracovních postupů Nadace pracovního postupu systému Windows (WF)</span><span class="sxs-lookup"><span data-stu-id="67883-209">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="67883-210">Návrhář pracovního postupu obsahuje následující změny v rozhraní .NET Framework 4.8:</span><span class="sxs-lookup"><span data-stu-id="67883-210">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="67883-211">Uživatelům používajícím Předčítání se zobrazí vylepšení popisků případu FlowSwitch.</span><span class="sxs-lookup"><span data-stu-id="67883-211">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="67883-212">Uživatelům používajícím Předčítání se zobrazí vylepšení v popisech tlačítek.</span><span class="sxs-lookup"><span data-stu-id="67883-212">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="67883-213">Uživatelům, kteří zvolí motivy s vysokým kontrastem, se zobrazí vylepšení viditelnosti návrháře pracovních postupů a jeho ovládacích prvků, jako jsou lepší kontrastní poměry mezi prvky a výraznější výběrová pole používaná pro prvky fokusu.</span><span class="sxs-lookup"><span data-stu-id="67883-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="67883-214">Pokud vaše aplikace cílí na rozhraní .NET Framework 4.7.2 nebo `Switch.UseLegacyAccessibilityFeatures.3` starší verzi, `false` můžete se k těmto změnám přihlásit nastavením [přepínače AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="67883-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="67883-215">Další informace naleznete v části [Využití vylepšení usnadnění](#taking-advantage-of-accessibility-enhancements) v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="67883-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="67883-216">Co je nového v usnadnění v rozhraní .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="67883-216">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="67883-217">Rozhraní .NET Framework 4.7.2 obsahuje nové funkce usnadnění v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="67883-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="67883-218">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67883-218">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="67883-219">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="67883-219">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="67883-220">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67883-220">Windows Forms</span></span>

<span data-ttu-id="67883-221">**Barvy definované oS v motivech s vysokým kontrastem**</span><span class="sxs-lookup"><span data-stu-id="67883-221">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="67883-222">Počínaje rozhraním .NET Framework 4.7.2 používá systém Windows Forms barvy definované operačním systémem v motivech s vysokým kontrastem.</span><span class="sxs-lookup"><span data-stu-id="67883-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="67883-223">To má vliv na následující ovládací prvky:</span><span class="sxs-lookup"><span data-stu-id="67883-223">This affects the following controls:</span></span>

- <span data-ttu-id="67883-224">Šipka rozevíracího <xref:System.Windows.Forms.ToolStripDropDownButton> seznamu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="67883-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="67883-225">Ovládací <xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.RadioButton> prvky <xref:System.Windows.Forms.CheckBox> <xref:System.Windows.Forms.ButtonBase.FlatStyle> a <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> ovládací <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>prvky s nastavenou na nebo .</span><span class="sxs-lookup"><span data-stu-id="67883-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="67883-226">Dříve nebyly vybrané barvy textu a pozadí kontrastní a byly těžko čitelné.</span><span class="sxs-lookup"><span data-stu-id="67883-226">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="67883-227">Ovládací prvky <xref:System.Windows.Forms.GroupBox> obsažené v <xref:System.Windows.Forms.Control.Enabled> rámci, `false`který má svou vlastnost nastavenou na .</span><span class="sxs-lookup"><span data-stu-id="67883-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="67883-228">Ovládací <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripComboBox>prvky <xref:System.Windows.Forms.ToolStripDropDownButton> , a ovládací prvky, které mají zvýšený kontrastní poměr světelnosti v režimu vysokého kontrastu.</span><span class="sxs-lookup"><span data-stu-id="67883-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="67883-229">Vlastnost <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="67883-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="67883-230">**Vylepšení předčítání**</span><span class="sxs-lookup"><span data-stu-id="67883-230">**Narrator improvements**</span></span>

<span data-ttu-id="67883-231">Počínaje rozhraním .NET Framework 4.7.2 je podpora předčítání vylepšena takto:</span><span class="sxs-lookup"><span data-stu-id="67883-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="67883-232">Oznamuje hodnotu vlastnosti <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> při oznámení textu <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="67883-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="67883-233">Označuje, <xref:System.Windows.Forms.ToolStripMenuItem> kdy má <xref:System.Windows.Forms.Control.Enabled> vlastnost `false`nastavena na .</span><span class="sxs-lookup"><span data-stu-id="67883-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="67883-234">Poskytuje zpětnou vazbu o stavu <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> zaškrtávacího políčka, když je vlastnost nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="67883-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="67883-235">Pořadí fokusu režimu skenování předčítání je konzistentní s vizuálním pořadím ovládacích prvků v dialogovém okně stahování ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="67883-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="67883-236">**Vylepšení datagridview**</span><span class="sxs-lookup"><span data-stu-id="67883-236">**DataGridView improvements**</span></span>

<span data-ttu-id="67883-237">Počínaje rozhraním .NET Framework 4.7.2 ovládací <xref:System.Windows.Forms.DataGridView> prvek zavedl následující vylepšení usnadnění:</span><span class="sxs-lookup"><span data-stu-id="67883-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="67883-238">Řádky lze seřadit pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="67883-238">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="67883-239">Uživatel může použít klávesu F3 k řazení podle aktuálního sloupce.</span><span class="sxs-lookup"><span data-stu-id="67883-239">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="67883-240">Pokud <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> je hodnota <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>nastavena na , záhlaví sloupce změní barvu, aby označilo aktuální sloupec jako karty uživatele prostřednictvím buněk v aktuálním řádku.</span><span class="sxs-lookup"><span data-stu-id="67883-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="67883-241">Vlastnost <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> vrátí správný nadřazený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="67883-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="67883-242">**Vylepšené vizuální podněty**</span><span class="sxs-lookup"><span data-stu-id="67883-242">**Improved visual cues**</span></span>

- <span data-ttu-id="67883-243">Ovládací <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.CheckBox> prvky a <xref:System.Windows.Forms.ButtonBase.Text> s prázdnou vlastností zobrazí indikátor fokusu, když obdrží fokus.</span><span class="sxs-lookup"><span data-stu-id="67883-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="67883-244">**Vylepšená podpora mřížky vlastností**</span><span class="sxs-lookup"><span data-stu-id="67883-244">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="67883-245">Podřízené <xref:System.Windows.Forms.PropertyGrid> prvky ovládacího prvku nyní vrátí a `true` pro <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> vlastnost pouze v případě, že propertyGrid element je povolena.</span><span class="sxs-lookup"><span data-stu-id="67883-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="67883-246">Podřízené <xref:System.Windows.Forms.PropertyGrid> prvky `false` ovládacího <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> prvku vrátí a pro vlastnost pouze v případě, že propertygrid element může změnit uživatel.</span><span class="sxs-lookup"><span data-stu-id="67883-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="67883-247">**Vylepšená navigace pomocí klávesnice**</span><span class="sxs-lookup"><span data-stu-id="67883-247">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="67883-248">Ovládací <xref:System.Windows.Forms.ToolStripButton> prvek umožňuje zaostření, pokud je obsažen v <xref:System.Windows.Forms.ToolStripPanel> rámci, který má <xref:System.Windows.Forms.ToolStripPanel.TabStop> vlastnost nastavenou na`true`</span><span class="sxs-lookup"><span data-stu-id="67883-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="67883-249">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="67883-249">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="67883-250">**Změny ovládacích prvků CheckBox a RadioButton**</span><span class="sxs-lookup"><span data-stu-id="67883-250">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="67883-251">V rozhraní .NET Framework 4.7.1 a <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> starších verzích wpf a <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> ovládací prvky mají nekonzistentní a v klasické a vysoké kontrastní motivy nesprávné fokus vizuály.</span><span class="sxs-lookup"><span data-stu-id="67883-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="67883-252">K těmto problémům dochází v případech, kdy ovládací prvky nemají žádný obsah nastaven.</span><span class="sxs-lookup"><span data-stu-id="67883-252">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="67883-253">To může způsobit, že přechod mezi motivy bude matoucí a vizuální fokus bude těžko vidět.</span><span class="sxs-lookup"><span data-stu-id="67883-253">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="67883-254">V rozhraní .NET Framework 4.7.2 jsou tyto vizuály nyní konzistentnější napříč motivy a snadněji viditelné v motivech Classic a High Contrast.</span><span class="sxs-lookup"><span data-stu-id="67883-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="67883-255">**Ovládací prvky WinForms hostované v aplikaci WPF**</span><span class="sxs-lookup"><span data-stu-id="67883-255">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="67883-256">Pro ovládací prvek WinForms hostovaný v aplikaci WPF v rozhraní .NET Framework 4.7.1 a starších verzích nemohli uživatelé z <xref:System.Windows.Forms.Integration.ElementHost> vrstvy WinForms out out z vrstvy WinForms, pokud je prvním nebo posledním ovládacím prvkem v této vrstvě ovládací prvek WPF.</span><span class="sxs-lookup"><span data-stu-id="67883-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="67883-257">V rozhraní .NET Framework 4.7.2 mohou uživatelé nyní out out vrstvy WinForms.</span><span class="sxs-lookup"><span data-stu-id="67883-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="67883-258">Automatizované aplikace, které spoléhají na fokus, však nemusí fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="67883-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="67883-259">Co je nového v usnadnění v rozhraní .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="67883-259">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="67883-260">Rozhraní .NET Framework 4.7.1 obsahuje nové funkce usnadnění v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="67883-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="67883-261">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="67883-261">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="67883-262">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67883-262">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="67883-263">ASP.NET webové ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="67883-263">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="67883-264">Nástroje sady .NET SDK</span><span class="sxs-lookup"><span data-stu-id="67883-264">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="67883-265">Návrhář pracovních postupů nadace Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="67883-265">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="67883-266">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="67883-266">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="67883-267">**Vylepšení čtečky obrazovky**</span><span class="sxs-lookup"><span data-stu-id="67883-267">**Screen reader improvements**</span></span>

<span data-ttu-id="67883-268">Pokud jsou povolena vylepšení usnadnění přístupu, obsahuje rozhraní .NET Framework 4.7.1 následující vylepšení, která ovlivňují programy pro čtení z obrazovky:</span><span class="sxs-lookup"><span data-stu-id="67883-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="67883-269">V rozhraní .NET Framework 4.7 <xref:System.Windows.Controls.Expander> a starších verzích byly ovládací prvky oznámeny programy pro čtení z obrazovky jako tlačítka.</span><span class="sxs-lookup"><span data-stu-id="67883-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="67883-270">Počínaje rozhraním .NET Framework 4.7.1 jsou správně oznámeny jako rozbalitelné/sbalitelné skupiny.</span><span class="sxs-lookup"><span data-stu-id="67883-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="67883-271">V rozhraní .NET Framework 4.7 <xref:System.Windows.Controls.DataGridCell> a starších verzích byly ovládací prvky programy pro čtení z obrazovky označeny jako "vlastní".</span><span class="sxs-lookup"><span data-stu-id="67883-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="67883-272">Počínaje rozhraním .NET Framework 4.7.1 jsou nyní správně oznámeny jako buňka datové mřížky (lokalizované).</span><span class="sxs-lookup"><span data-stu-id="67883-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="67883-273">Počínaje rozhraním .NET Framework 4.7.1 programy pro <xref:System.Windows.Controls.ComboBox>čtení z obrazovky oznamují název upravitelného .</span><span class="sxs-lookup"><span data-stu-id="67883-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="67883-274">V rozhraní .NET Framework 4.7 <xref:System.Windows.Controls.PasswordBox> a starších verzích byly ovládací prvky oznámeny jako "žádná položka v zobrazení" nebo měly jinak nesprávné chování.</span><span class="sxs-lookup"><span data-stu-id="67883-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="67883-275">Tento problém je vyřešen počínaje rozhraním .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="67883-275">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="67883-276">**Podpora pro UIAutomation LiveRegion**</span><span class="sxs-lookup"><span data-stu-id="67883-276">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="67883-277">Programy pro čtení z obrazovky, jako je Předčítání, pomáhají lidem číst obsah ui aplikace, obvykle pomocí výstupu převodu textu na řeč obsahu ui, který má fokus.</span><span class="sxs-lookup"><span data-stu-id="67883-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="67883-278">Pokud se však prvek uživatelského rozhraní změní a nemá fokus, uživatel nemusí být upozorněn a může chybět důležité informace.</span><span class="sxs-lookup"><span data-stu-id="67883-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="67883-279">Živé regiony se zaměřují na řešení tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="67883-279">Live regions aim at solving this problem.</span></span> <span data-ttu-id="67883-280">Vývojář je může použít k informování čtečky obrazovky nebo jiného klienta UIAutomation, že byla provedena důležitá změna prvku uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67883-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="67883-281">Program pro čtení z obrazovky se pak může rozhodnout, jak a kdy o této změně informuje uživatele.</span><span class="sxs-lookup"><span data-stu-id="67883-281">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="67883-282">Pro podporu živých oblastí byla do WPF přidána následující api:</span><span class="sxs-lookup"><span data-stu-id="67883-282">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="67883-283">Pole <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> a, která identifikují vlastnost **LiveSetting** a událost **LiveRegionChanged.**</span><span class="sxs-lookup"><span data-stu-id="67883-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="67883-284">Lze je nastavit pomocí XAML.</span><span class="sxs-lookup"><span data-stu-id="67883-284">They can be set by using XAML.</span></span>

- <span data-ttu-id="67883-285">**AutomationProperties.LiveSetting** připojené vlastnosti, která informuje čtečku obrazovky o významu změny uživatelského rozhraní pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="67883-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="67883-286">Vlastnost, <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> která identifikuje **AutomationProperties.LiveSetting** připojené vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="67883-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="67883-287">Metoda, <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> která může být přepsána poskytnout **LiveSetting** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="67883-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="67883-288">Metody <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> a, které získat a nastavit **LiveSetting** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="67883-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="67883-289">Výčet, <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> který definuje následující možné **LiveSetting** hodnoty:</span><span class="sxs-lookup"><span data-stu-id="67883-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="67883-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="67883-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="67883-291">Prvek neodesílá oznámení, pokud došlo ke změně obsahu živé oblasti.</span><span class="sxs-lookup"><span data-stu-id="67883-291">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="67883-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="67883-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="67883-293">Prvek odesílá nepřerušitelná oznámení, pokud došlo ke změně obsahu živé oblasti.</span><span class="sxs-lookup"><span data-stu-id="67883-293">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="67883-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="67883-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="67883-295">Prvek odešle přerušená oznámení, pokud došlo ke změně obsahu živé oblasti.</span><span class="sxs-lookup"><span data-stu-id="67883-295">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="67883-296">LiveRegion můžete vytvořit nastavením **AutomationProperties.LiveSetting** vlastnost na prvek zájmu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="67883-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="67883-297">Když se změní data v živé oblasti a potřebujete informovat program pro čtení z obrazovky, explicitně vyvoláte událost, jak je znázorněno v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="67883-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="67883-298">**Vysoký kontrast**</span><span class="sxs-lookup"><span data-stu-id="67883-298">**High contrast**</span></span>

<span data-ttu-id="67883-299">Počínaje rozhraním .NET Framework 4.7.1 bylo u různých ovládacích prvků WPF provedeno zlepšení vysokého kontrastu.</span><span class="sxs-lookup"><span data-stu-id="67883-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="67883-300">Nyní jsou viditelné <xref:System.Windows.SystemParameters.HighContrast%2A> při nastavení motivu.</span><span class="sxs-lookup"><span data-stu-id="67883-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="67883-301">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="67883-301">These include:</span></span>

- <span data-ttu-id="67883-302"><xref:System.Windows.Controls.Expander>Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="67883-302"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="67883-303">Vizuální fokus <xref:System.Windows.Controls.Expander> pro ovládací prvek je nyní viditelný.</span><span class="sxs-lookup"><span data-stu-id="67883-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="67883-304">Vizuály <xref:System.Windows.Controls.ComboBox>klávesnice<xref:System.Windows.Controls.ListBox>pro <xref:System.Windows.Controls.RadioButton> , a ovládací prvky jsou také viditelné.</span><span class="sxs-lookup"><span data-stu-id="67883-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="67883-305">Například:</span><span class="sxs-lookup"><span data-stu-id="67883-305">For example:</span></span>

  <span data-ttu-id="67883-306">Před:</span><span class="sxs-lookup"><span data-stu-id="67883-306">Before:</span></span>

  ![Snímek obrazovky ovládacího prvku expanderu s fokusem a bez fokusu vizuálu](./media/whats-new-in-accessibility/expander-control-before.png)

  <span data-ttu-id="67883-308">Po:</span><span class="sxs-lookup"><span data-stu-id="67883-308">After:</span></span>

  ![Snímek obrazovky ovládacího prvku expander s fokusem zobrazující tečkovanou čáru kolem textu ovládacího prvku](./media/whats-new-in-accessibility/expander-control-after.png)

- <span data-ttu-id="67883-310"><xref:System.Windows.Controls.CheckBox>a <xref:System.Windows.Controls.RadioButton> ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="67883-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="67883-311">Text v <xref:System.Windows.Controls.CheckBox> ovládacích prvcích a <xref:System.Windows.Controls.RadioButton> je nyní lépe vidět, když je vybrán v motivech s vysokým kontrastem.</span><span class="sxs-lookup"><span data-stu-id="67883-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="67883-312">Například:</span><span class="sxs-lookup"><span data-stu-id="67883-312">For example:</span></span>

  <span data-ttu-id="67883-313">Před:</span><span class="sxs-lookup"><span data-stu-id="67883-313">Before:</span></span>

  ![Snímek obrazovky s přepínači a kontrolními tlačítky se špatnou viditelností textu na motivech s vysokým kontrastem](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  <span data-ttu-id="67883-315">Po:</span><span class="sxs-lookup"><span data-stu-id="67883-315">After:</span></span>

  ![Snímek obrazovky s přepínači a kontrolními tlačítky s lepší viditelností textu na motivy s vysokým kontrastem](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <span data-ttu-id="67883-317"><xref:System.Windows.Controls.ComboBox>Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="67883-317"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="67883-318">Počínaje rozhraním .NET Framework 4.7.1 <xref:System.Windows.Controls.ComboBox> má ohraničení zakázaného ovládacího prvku stejnou barvu jako zakázaný text.</span><span class="sxs-lookup"><span data-stu-id="67883-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="67883-319">Například:</span><span class="sxs-lookup"><span data-stu-id="67883-319">For example:</span></span>

  <span data-ttu-id="67883-320">Před:</span><span class="sxs-lookup"><span data-stu-id="67883-320">Before:</span></span>

  ![Snímek obrazovky se zakázaným rámečkem Se seznamem s textem ohraničení a ovládacích prvku v různých barvách](./media/whats-new-in-accessibility/combo-disabled-before.png)

  <span data-ttu-id="67883-322">Po:</span><span class="sxs-lookup"><span data-stu-id="67883-322">After:</span></span>

  ![Snímek obrazovky se zakázaným rámečkem ComboBox s ohraničením stejné barvy jako text ovládacího prvku](./media/whats-new-in-accessibility/combo-disabled-after.png)

  <span data-ttu-id="67883-324">Kromě toho, zdravotně a soustředěné tlačítka používají správnou barvu motivu.</span><span class="sxs-lookup"><span data-stu-id="67883-324">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="67883-325">Před:</span><span class="sxs-lookup"><span data-stu-id="67883-325">Before:</span></span>

  ![Snímek obrazovky s černým tlačítkem s šedým textem Focus Me](./media/whats-new-in-accessibility/button-theme-colors-before.png)

  <span data-ttu-id="67883-327">Po:</span><span class="sxs-lookup"><span data-stu-id="67883-327">After:</span></span>

  ![Snímek obrazovky s modrým tlačítkem s černým textem Focus Me](./media/whats-new-in-accessibility/button-theme-colors-after.png)

  <span data-ttu-id="67883-329">Nakonec v rozhraní .NET Framework 4.7 a <xref:System.Windows.Controls.ComboBox> starších verzích nastavení stylu ovládacího prvku způsobilo, že `Toolbar.ComboBoxStyleKey` šipka rozevíracího seznamu byla neviditelná.</span><span class="sxs-lookup"><span data-stu-id="67883-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="67883-330">Tento problém je vyřešen počínaje rozhraním .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="67883-330">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="67883-331">Například:</span><span class="sxs-lookup"><span data-stu-id="67883-331">For example:</span></span>

  <span data-ttu-id="67883-332">Před:</span><span class="sxs-lookup"><span data-stu-id="67883-332">Before:</span></span>

  ![Snímek obrazovky ovládacího prvku ComboBox s neviditelnou šipkou rozevíracího seznamu](./media/whats-new-in-accessibility/combo-box-style-key-before.png)

  <span data-ttu-id="67883-334">Po:</span><span class="sxs-lookup"><span data-stu-id="67883-334">After:</span></span>

  ![Snímek obrazovky ovládacího prvku ComBoxBox zobrazujícího šipku rozevíracího seznamu](./media/whats-new-in-accessibility/combo-box-style-key-after.png)

- <span data-ttu-id="67883-336"><xref:System.Windows.Controls.DataGrid>Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="67883-336"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="67883-337">Počínaje rozhraním .NET Framework 4.7.1 <xref:System.Windows.Controls.DataGrid> nyní šipka indikátoru řazení v ovládacích prvcích používá správné barvy motivu.</span><span class="sxs-lookup"><span data-stu-id="67883-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="67883-338">Například:</span><span class="sxs-lookup"><span data-stu-id="67883-338">For example:</span></span>

  <span data-ttu-id="67883-339">Před:</span><span class="sxs-lookup"><span data-stu-id="67883-339">Before:</span></span>

  ![Snímek obrazovky se šipkou indikátoru řazení před vylepšeními](./media/whats-new-in-accessibility/sort-indicator-before.png)

  <span data-ttu-id="67883-341">Po:</span><span class="sxs-lookup"><span data-stu-id="67883-341">After:</span></span>

  ![Snímek obrazovky se šipkou indikátoru řazení po vylepšeních](./media/whats-new-in-accessibility/sort-indicator-after.png)

  <span data-ttu-id="67883-343">Kromě toho v rozhraní .NET Framework 4.7 a starších verzích se výchozí styl propojení změnil na nesprávnou barvu na myši v režimech vysokého kontrastu.</span><span class="sxs-lookup"><span data-stu-id="67883-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="67883-344">To je vyřešen počínaje rozhraním .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="67883-344">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="67883-345">Podobně <xref:System.Windows.Controls.DataGrid> zaškrtávací políčko sloupce používá očekávané barvy pro zpětnou vazbu fokus klávesnice počínaje rozhraním .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="67883-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="67883-346">Před:</span><span class="sxs-lookup"><span data-stu-id="67883-346">Before:</span></span>

  ![Snímek obrazovky s odkazem na tlačítko Klikněte na mě!](./media/whats-new-in-accessibility/default-link-style-before.png)

  <span data-ttu-id="67883-349">Po:</span><span class="sxs-lookup"><span data-stu-id="67883-349">After:</span></span>

  ![Snímek obrazovky s odkazem na tlačítko Klikněte na mě!](./media/whats-new-in-accessibility/default-link-style-after.png)

<span data-ttu-id="67883-352">Další informace o vylepšení wpf usnadnění v rozhraní .NET Framework 4.7.1 naleznete [v tématu usnadnění zlepšení WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="67883-352">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="67883-353">Vylepšení usnadnění přístupu pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67883-353">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="67883-354">V rozhraní .NET Framework 4.7.1 obsahuje formuláře systému Windows (WinForms) změny usnadnění přístupu v následujících oblastech.</span><span class="sxs-lookup"><span data-stu-id="67883-354">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="67883-355">**Vylepšené zobrazení v režimu vysokého kontrastu**</span><span class="sxs-lookup"><span data-stu-id="67883-355">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="67883-356">Počínaje rozhraním .NET Framework 4.7.1 nabízejí různé ovládací prvky WinForms vylepšené vykreslování v režimech HighContrast dostupných v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="67883-356">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="67883-357">Systém Windows 10 změnil hodnoty pro některé barvy systému s vysokým kontrastem a windows forms je založen na rozhraní Windows 10 Win32.</span><span class="sxs-lookup"><span data-stu-id="67883-357">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="67883-358">Chcete-li získat nejlepší zážitek, spusťte nejnovější verzi systému Windows a přihlaste se k nejnovějším změnám operačního systému přidáním souboru app.manifest do testovací aplikace a odkomentujte řádek podporovaného operačního systému Windows 10 tak, aby vypadal takto:</span><span class="sxs-lookup"><span data-stu-id="67883-358">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

<span data-ttu-id="67883-359">Některé příklady změn s vysokým kontrastem:</span><span class="sxs-lookup"><span data-stu-id="67883-359">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="67883-360">Zaškrtnutí <xref:System.Windows.Forms.MenuStrip> položek se snadněji zobrazují.</span><span class="sxs-lookup"><span data-stu-id="67883-360">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="67883-361">Pokud je <xref:System.Windows.Forms.MenuStrip> tato možnost vybrána, zakázané položky se snadněji zobrazují.</span><span class="sxs-lookup"><span data-stu-id="67883-361">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="67883-362">Text ve <xref:System.Windows.Forms.Button> vybraném ovládacím prvku kontrastuje s barvou výběru.</span><span class="sxs-lookup"><span data-stu-id="67883-362">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="67883-363">Zakázaný text je čitelnější.</span><span class="sxs-lookup"><span data-stu-id="67883-363">Disabled text is easier to read.</span></span> <span data-ttu-id="67883-364">Například:</span><span class="sxs-lookup"><span data-stu-id="67883-364">For example:</span></span>

  <span data-ttu-id="67883-365">Před:</span><span class="sxs-lookup"><span data-stu-id="67883-365">Before:</span></span>

  ![Snímek obrazovky s aplikací, která používá různé ovládací prvky spuštěné v režimu vysokého kontrastu před vylepšením usnadnění přístupu.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png)

  <span data-ttu-id="67883-367">Po:</span><span class="sxs-lookup"><span data-stu-id="67883-367">After:</span></span>

  ![Snímek obrazovky s aplikací, která používá různé ovládací prvky spuštěné v režimu vysokého kontrastu po vylepšení usnadnění přístupu.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png)

- <span data-ttu-id="67883-369">Vylepšení vysokého kontrastu v dialogovém okně výjimky vlákna.</span><span class="sxs-lookup"><span data-stu-id="67883-369">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="67883-370">**Vylepšená podpora pro Předčítání**</span><span class="sxs-lookup"><span data-stu-id="67883-370">**Improved Narrator support**</span></span>

<span data-ttu-id="67883-371">Windows Forms v rozhraní .NET Framework 4.7.1 obsahuje následující vylepšení usnadnění pro Předčítání:</span><span class="sxs-lookup"><span data-stu-id="67883-371">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="67883-372">Ovládací <xref:System.Windows.Forms.MonthCalendar> prvek je přístupný předčítáním, stejně jako další nástroje pro automatizaci uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67883-372">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="67883-373">Ovládací <xref:System.Windows.Forms.CheckedListBox> prvek upozorní Předčítání, když se změní stav kontroly položky, aby byl uživatel upozorněn, že změnil hodnotu položky seznamu.</span><span class="sxs-lookup"><span data-stu-id="67883-373">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="67883-374">Ovládací <xref:System.Windows.Forms.DataGridViewCell> prvek hlásí Předčítání správný stav jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="67883-374">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="67883-375">Předčítání teď může <xref:System.Windows.Forms.ToolStripMenuItem> číst zakázaný text, zatímco dříve přeskakovat zakázané položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="67883-375">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="67883-376">**Vylepšená podpora vzorců usnadnění uIAutomation**</span><span class="sxs-lookup"><span data-stu-id="67883-376">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="67883-377">Počínaje rozhraním .NET Framework 4.7.1 mohou vývojáři nástrojů pro usnadnění přístupu využít běžné vzory a vlastnosti rozhraní API pro několik ovládacích prvků WinForms.</span><span class="sxs-lookup"><span data-stu-id="67883-377">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="67883-378">Mezi tato vylepšení usnadnění patří:</span><span class="sxs-lookup"><span data-stu-id="67883-378">These accessibility improvements include:</span></span>

- <span data-ttu-id="67883-379">A <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ToolStripSplitButton> nyní podporují [rozbalení/sbalit vzor](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="67883-379">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="67883-380">Nyní <xref:System.Windows.Forms.DataGridViewCheckBoxCell> podporuje [přepínací vzor](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="67883-380">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="67883-381">Ovládací <xref:System.Windows.Forms.ToolStripItem> prvek <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> podporuje vlastnost a [rozbalení/sbalit vzor](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="67883-381">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="67883-382">A <xref:System.Windows.Forms.NumericUpDown> <xref:System.Windows.Forms.DomainUpDown> ovládací prvky <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> podporují vlastnost.</span><span class="sxs-lookup"><span data-stu-id="67883-382">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="67883-383">**Vylepšené prostředí prohlížeče vlastností**</span><span class="sxs-lookup"><span data-stu-id="67883-383">**Improved property browser experience**</span></span>

<span data-ttu-id="67883-384">Počínaje rozhraním .NET Framework 4.7.1 obsahuje windows forms:</span><span class="sxs-lookup"><span data-stu-id="67883-384">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="67883-385">Lepší navigace pomocí klávesnice v různých rozbalovacích oknech výběru.</span><span class="sxs-lookup"><span data-stu-id="67883-385">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="67883-386">Snížení zbytečných zarážek tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="67883-386">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="67883-387">Lepší vykazování typů ovládacích prvku.</span><span class="sxs-lookup"><span data-stu-id="67883-387">Better reporting of control types.</span></span>
- <span data-ttu-id="67883-388">Vylepšené chování předčítání.</span><span class="sxs-lookup"><span data-stu-id="67883-388">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="67883-389">ASP.NET webové ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="67883-389">ASP.NET web controls</span></span>

<span data-ttu-id="67883-390">Počínaje rozhraními .NET Framework 4.7.1 a Visual Studio 2017 verze 15.3 ASP.NET vylepšuje způsob, jakým ASP.NET webové ovládací prvky fungují s technologií usnadnění v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="67883-390">Starting with .NET Framework 4.7.1 and Visual Studio 2017 version 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="67883-391">Změny zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="67883-391">Changes include the following:</span></span>

- <span data-ttu-id="67883-392">Změny pro implementaci chybějících vzorů usnadnění přístupu k rozhraní v ovládacích prvcích, jako je dialogové okno **Přidat pole** v **průvodci zobrazením podrobností** nebo dialogové okno **Konfigurovat zobrazení seznamu** průvodce **listview.**</span><span class="sxs-lookup"><span data-stu-id="67883-392">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="67883-393">Změny pro zlepšení zobrazení v režimu vysokého kontrastu, například **Editor polí datových stránek**.</span><span class="sxs-lookup"><span data-stu-id="67883-393">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="67883-394">Změny pro zlepšení prostředí navigace pomocí klávesnice pro ovládací prvky, například dialogové okno **Pole** v průvodci **Upravit pole operátoru** ovládacího prvku DataPager, dialogové okno **Konfigurovat kontext objektu** nebo dialogové okno **Konfigurovat výběr dat** průvodce Konfigurovat **zdroj dat.**</span><span class="sxs-lookup"><span data-stu-id="67883-394">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="67883-395">Nástroje sady .NET SDK</span><span class="sxs-lookup"><span data-stu-id="67883-395">.NET SDK Tools</span></span>

<span data-ttu-id="67883-396">Nástroj [Editor konfigurace (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) a [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) byly vylepšeny opravou různých problémů s přístupností.</span><span class="sxs-lookup"><span data-stu-id="67883-396">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="67883-397">Většina z nich byly malé problémy, jako je název, který není definován nebo některé vzory automatizace uživatelského rozhraní nejsou implementovány správně.</span><span class="sxs-lookup"><span data-stu-id="67883-397">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="67883-398">Zatímco mnoho uživatelů nebude vědět o těchto nesprávných hodnotách, zákazníci, kteří používají asistenční technologie, jako jsou programy pro čtení z obrazovky, najdou tyto nástroje sady SDK přístupnější.</span><span class="sxs-lookup"><span data-stu-id="67883-398">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="67883-399">Tato vylepšení změnit některé předchozí chování, jako je například pořadí fokusu klávesnice.</span><span class="sxs-lookup"><span data-stu-id="67883-399">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="67883-400">Návrhář pracovních postupů nadace Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="67883-400">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="67883-401">Změny usnadnění v Návrháři pracovních postupů zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="67883-401">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="67883-402">Pořadí polí se v některých ovládacích prvcích mění zleva doprava a shora dolů:</span><span class="sxs-lookup"><span data-stu-id="67883-402">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="67883-403">Okno inicializovat korelace pro <xref:System.ServiceModel.Activities.InitializeCorrelation> nastavení dat korelace pro aktivitu.</span><span class="sxs-lookup"><span data-stu-id="67883-403">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="67883-404">Okno definice obsahu <xref:System.ServiceModel.Activities.Receive>pro <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.ReceiveReply> , a aktivity.</span><span class="sxs-lookup"><span data-stu-id="67883-404">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="67883-405">Další funkce jsou k dispozici prostřednictvím klávesnice:</span><span class="sxs-lookup"><span data-stu-id="67883-405">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="67883-406">Při úpravách vlastností aktivity mohou být skupiny vlastností sbaleny pomocí klávesnice při prvním zaměření.</span><span class="sxs-lookup"><span data-stu-id="67883-406">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="67883-407">Výstražné ikony jsou přístupné pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="67883-407">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="67883-408">Tlačítko **Další vlastnosti** v okně **Vlastnosti** je přístupné pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="67883-408">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="67883-409">Uživatelé klávesnice mají přístup k položkám záhlaví v podokně **Argumenty** a **proměnné** návrháře pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="67883-409">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="67883-410">Lepší viditelnost položek s fokusem, například když:</span><span class="sxs-lookup"><span data-stu-id="67883-410">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="67883-411">Přidání řádků do datových mříží používaných návrhářem pracovních postupů a návrháři aktivit.</span><span class="sxs-lookup"><span data-stu-id="67883-411">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="67883-412">Procházení polí v <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.SendReply> a aktivity.</span><span class="sxs-lookup"><span data-stu-id="67883-412">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="67883-413">Nastavení výchozích hodnot pro proměnné nebo argumenty</span><span class="sxs-lookup"><span data-stu-id="67883-413">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="67883-414">Programy pro čtení z obrazovky nyní správně rozpoznávají:</span><span class="sxs-lookup"><span data-stu-id="67883-414">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="67883-415">Zarážky nastavené v návrháři pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="67883-415">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="67883-416">V <xref:System.Activities.Statements.FlowSwitch%601> <xref:System.Activities.Statements.FlowDecision>oblasti <xref:System.ServiceModel.Activities.CorrelationScope> , a aktivity.</span><span class="sxs-lookup"><span data-stu-id="67883-416">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="67883-417">Obsah aktivity. <xref:System.ServiceModel.Activities.Receive></span><span class="sxs-lookup"><span data-stu-id="67883-417">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="67883-418">Cílový typ aktivity. <xref:System.Activities.Statements.InvokeMethod></span><span class="sxs-lookup"><span data-stu-id="67883-418">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="67883-419">Pole se seznamem Výjimka a <xref:System.Activities.Statements.TryCatch> finally části v aktivitě.</span><span class="sxs-lookup"><span data-stu-id="67883-419">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="67883-420">Pole se seznamem Typ zprávy, rozdělovač v okně Přidat inicializační stavkovy korelace, okno Definice<xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.Send>obsahu <xref:System.ServiceModel.Activities.SendReply>a <xref:System.ServiceModel.Activities.ReceiveReply>okno Definice korelování v aktivitách zasílání zpráv ( , , , a ).</span><span class="sxs-lookup"><span data-stu-id="67883-420">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="67883-421">Přechody a přechody stavových přechodů.</span><span class="sxs-lookup"><span data-stu-id="67883-421">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="67883-422">Poznámky a konektory <xref:System.Activities.Statements.FlowDecision> na aktivity.</span><span class="sxs-lookup"><span data-stu-id="67883-422">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="67883-423">Kontextové nabídky (kliknutí pravým tlačítkem myši) pro aktivity.</span><span class="sxs-lookup"><span data-stu-id="67883-423">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="67883-424">Editory hodnot vlastností, tlačítko Vymazat hledání, tlačítka Podle kategorie a Abecední řazení a dialogové okno Editor výrazů v mřížce vlastností.</span><span class="sxs-lookup"><span data-stu-id="67883-424">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="67883-425">Procento zvětšení v Návrháři pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="67883-425">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="67883-426">Oddělovač <xref:System.Activities.Statements.Parallel> v <xref:System.Activities.Statements.Pick> a aktivity.</span><span class="sxs-lookup"><span data-stu-id="67883-426">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="67883-427">Aktivita. <xref:System.Activities.Statements.InvokeDelegate></span><span class="sxs-lookup"><span data-stu-id="67883-427">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="67883-428">Okno Vybrat typy pro aktivity slovníku (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, atd.).</span><span class="sxs-lookup"><span data-stu-id="67883-428">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="67883-429">Okno Procházet a vybrat typ rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="67883-429">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="67883-430">Popis cesty v Návrháři pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="67883-430">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="67883-431">Uživatelům, kteří zvolí motivy s vysokým kontrastem, se zobrazí mnoho vylepšení viditelnosti návrháře pracovních postupů a jeho ovládacích prvků, jako jsou lepší kontrastní poměry mezi prvky a výraznější výběrová pole používaná pro prvky fokusu.</span><span class="sxs-lookup"><span data-stu-id="67883-431">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="67883-432">Viz také</span><span class="sxs-lookup"><span data-stu-id="67883-432">See also</span></span>

- [<span data-ttu-id="67883-433">Novinky v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="67883-433">What's new in the .NET Framework</span></span>](index.md)
