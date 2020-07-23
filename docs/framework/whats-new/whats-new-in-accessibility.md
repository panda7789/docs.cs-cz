---
title: Co je nového v přístupnosti v .NET Framework
description: Podívejte se, co je nového v přístupnost .NET, počínaje .NET Framework 4.7.1. Funkce usnadnění umožňují, aby aplikace poskytovala správné prostředí pro uživatele s asistenčními technologiemi.
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: 593591ca340cc130a3a6d1daa015a849b8eca0f8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925836"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="73177-104">Co je nového v přístupnosti v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="73177-104">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="73177-105">.NET Framework se zaměřuje na zajištění přístupnosti aplikací pro vaše uživatele.</span><span class="sxs-lookup"><span data-stu-id="73177-105">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="73177-106">Funkce usnadnění umožňují aplikaci poskytovat vhodné prostředí pro uživatele technologie usnadnění.</span><span class="sxs-lookup"><span data-stu-id="73177-106">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="73177-107">Počínaje .NET Framework 4.7.1 .NET Framework obsahuje velký počet vylepšení usnadnění, která vývojářům umožňují vytvářet přístupné aplikace.</span><span class="sxs-lookup"><span data-stu-id="73177-107">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="73177-108">Přepínače přístupnosti</span><span class="sxs-lookup"><span data-stu-id="73177-108">Accessibility switches</span></span>

<span data-ttu-id="73177-109">Aplikaci můžete nakonfigurovat tak, aby se přihlásila k funkcím přístupnosti, pokud cílíte .NET Framework 4,7 nebo starší verzi, ale běží na .NET Framework 4.7.1 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="73177-109">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="73177-110">Pokud cílíte .NET Framework 4.7.1 nebo novější, můžete aplikaci nakonfigurovat tak, aby používala starší funkce (a nevyužila výhody funkcí usnadnění).</span><span class="sxs-lookup"><span data-stu-id="73177-110">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="73177-111">Každá verze .NET Framework, která zahrnuje funkce usnadnění, má přepínač dostupnosti specifický pro verzi, který přidáte do [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvku v [`<runtime>`](../configure-apps/file-schema/runtime/index.md) části konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="73177-111">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="73177-112">Podporovány jsou následující přepínače:</span><span class="sxs-lookup"><span data-stu-id="73177-112">The following are the supported switches:</span></span>

|<span data-ttu-id="73177-113">Verze</span><span class="sxs-lookup"><span data-stu-id="73177-113">Version</span></span>|<span data-ttu-id="73177-114">Přepínač</span><span class="sxs-lookup"><span data-stu-id="73177-114">Switch</span></span>|
|---|---|
|<span data-ttu-id="73177-115">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="73177-115">.NET Framework 4.7.1</span></span>|<span data-ttu-id="73177-116">"Switch. UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="73177-116">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="73177-117"> .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="73177-117">.NET Framework 4.7.2</span></span>|<span data-ttu-id="73177-118">"Switch. UseLegacyAccessibilityFeatures. 2"</span><span class="sxs-lookup"><span data-stu-id="73177-118">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="73177-119"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="73177-119">.NET Framework 4.8</span></span>|<span data-ttu-id="73177-120">"Switch. UseLegacyAccessibilityFeatures. 3"</span><span class="sxs-lookup"><span data-stu-id="73177-120">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="73177-121">Využití výhod vylepšení usnadnění přístupu</span><span class="sxs-lookup"><span data-stu-id="73177-121">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="73177-122">Nové funkce usnadnění jsou ve výchozím nastavení povolené pro aplikace, které cílí na .NET Framework 4.7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="73177-122">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="73177-123">Kromě toho aplikace, které cílí na starší verzi .NET Framework, ale jsou spuštěné v .NET Framework 4.7.1 nebo novější, se mohou odhlásit ze starší verze chování přístupnosti (a tím využít výhod vylepšení usnadnění) přidáním přepínačů do [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvku v [`<runtime>`](../configure-apps/file-schema/runtime/index.md) části konfiguračního souboru aplikace a nastavením jejich hodnoty na `false` .</span><span class="sxs-lookup"><span data-stu-id="73177-123">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="73177-124">V následující části se dozvíte, jak se vyjádřit k vylepšením usnadnění zavedeným v .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="73177-124">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="73177-125">Pokud se rozhodnete pro funkce přístupnosti v novější verzi .NET Framework vyjádřit, musíte se taky výslovně odhlásit k funkcím z dřívějších verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="73177-125">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="73177-126">Konfigurace vaší aplikace pro využívání výhod vylepšení usnadnění v .NET Framework 4.7.1 i 4.7.2 vyžaduje následující [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span><span class="sxs-lookup"><span data-stu-id="73177-126">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="73177-127">Konfigurace vaší aplikace pro využívání výhod vylepšení usnadnění v .NET Framework 4.7.1, 4.7.2 a 4,8 vyžaduje následující [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span><span class="sxs-lookup"><span data-stu-id="73177-127">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="73177-128">Obnovení starší verze chování</span><span class="sxs-lookup"><span data-stu-id="73177-128">Restoring legacy behavior</span></span>

<span data-ttu-id="73177-129">Aplikace, které cílí na verze .NET Framework začínající na 4.7.1, mohou zakázat funkce usnadnění přidáním přepínačů do [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvku v [`<runtime>`](../configure-apps/file-schema/runtime/index.md) části konfiguračního souboru aplikace a nastavením jejich hodnoty na `true` .</span><span class="sxs-lookup"><span data-stu-id="73177-129">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="73177-130">Například následující konfigurace výslovný z funkcí usnadnění zavedených v .NET Framework 4.7.2:</span><span class="sxs-lookup"><span data-stu-id="73177-130">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="73177-131">Co je nového v přístupnosti v .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="73177-131">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="73177-132">.NET Framework 4,8 obsahuje nové funkce pro usnadnění přístupu v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="73177-132">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="73177-133">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73177-133">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="73177-134">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="73177-134">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="73177-135">Návrhář pracovního postupu programovací model Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="73177-135">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48"></a>

### <a name="windows-forms"></a><span data-ttu-id="73177-136">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73177-136">Windows Forms</span></span>

<span data-ttu-id="73177-137">V .NET Framework 4,8 model Windows Forms přidává podporu pro události LiveRegions a Notification k mnoha běžně používaným ovládacím prvkům.</span><span class="sxs-lookup"><span data-stu-id="73177-137">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="73177-138">Pokud uživatel přejde k ovládacímu prvku pomocí klávesnice, přidá také podporu pro popisky tlačítek.</span><span class="sxs-lookup"><span data-stu-id="73177-138">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="73177-139">**Podpora UIA LiveRegions ve jmenovkách a StatusStrips**</span><span class="sxs-lookup"><span data-stu-id="73177-139">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="73177-140">UIA LiveRegions umožňuje vývojářům aplikací upozorňovat čtečky obrazovky na změnu textu v ovládacím prvku, který se nachází vedle místa, kde uživatel pracuje.</span><span class="sxs-lookup"><span data-stu-id="73177-140">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="73177-141">To je užitečné například pro <xref:System.Windows.Forms.StatusStrip> ovládací prvek, který zobrazuje stav připojení.</span><span class="sxs-lookup"><span data-stu-id="73177-141">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="73177-142">Pokud se připojení vynechá a změní se stav, vývojář může chtít informovat čtečku obrazovky.</span><span class="sxs-lookup"><span data-stu-id="73177-142">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="73177-143">Počínaje .NET Framework 4,8 model Windows Forms implementuje UIA LiveRegions pro <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.StatusStrip> ovládací prvky a.</span><span class="sxs-lookup"><span data-stu-id="73177-143">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="73177-144">Například následující kód používá LiveRegion v <xref:System.Windows.Forms.Label> ovládacím prvku s názvem `label1` :</span><span class="sxs-lookup"><span data-stu-id="73177-144">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="73177-145">Narrator oznamuje "připravený" bez ohledu na to, kde uživatel interakci s aplikací.</span><span class="sxs-lookup"><span data-stu-id="73177-145">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="73177-146">Můžete také implementovat <xref:System.Windows.Forms.UserControl> jako LiveRegion:</span><span class="sxs-lookup"><span data-stu-id="73177-146">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

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

<span data-ttu-id="73177-147">**Události oznámení UIA**</span><span class="sxs-lookup"><span data-stu-id="73177-147">**UIA notification events**</span></span>

<span data-ttu-id="73177-148">Událost oznámení UIA zavedená ve Windows 10 vede k aktualizaci Creators Update, umožňuje vaší aplikaci vyvolat událost UIA, která vede k tomu, že v programu Narrator stačí vytvořit oznámení na základě textu, který zadáte do události, aniž by bylo nutné mít odpovídající ovládací prvek v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="73177-148">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="73177-149">V některých scénářích je to jednoduchý způsob, jak výrazně zlepšit přístupnost vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="73177-149">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="73177-150">Aplikace může být užitečná také pro oznamování průběhu některých procesů, které mohou trvat dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="73177-150">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="73177-151">Další informace o událostech oznámení UIA najdete v tématu [může vaše desktopová aplikace využít novou událost oznámení uživatelského rozhraní?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span><span class="sxs-lookup"><span data-stu-id="73177-151">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span></span>

<span data-ttu-id="73177-152">Následující příklad vyvolá [událost oznámení](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span><span class="sxs-lookup"><span data-stu-id="73177-152">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="73177-153">**Popisy tlačítek při přístupu k klávesnicím**</span><span class="sxs-lookup"><span data-stu-id="73177-153">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="73177-154">V aplikacích, které cílí na .NET Framework 4.7.2 a starších verzí, lze [Popis](xref:System.Windows.Forms.ToolTip) ovládacího prvku aktivovat pouze přesunutím ukazatele myši do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="73177-154">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="73177-155">Počínaje .NET Framework 4,8 může uživatel klávesnice aktivovat Popis ovládacího prvku tím, že zaměří ovládací prvek pomocí klávesy tabulátoru nebo kláves se šipkami s nebo bez modifikačních kláves.</span><span class="sxs-lookup"><span data-stu-id="73177-155">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="73177-156">Toto konkrétní vylepšení přístupnosti vyžaduje další [přepínač AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span><span class="sxs-lookup"><span data-stu-id="73177-156">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

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

<span data-ttu-id="73177-157">Následující obrázek znázorňuje popis tlačítka, když uživatel vybere tlačítko s klávesnicí.</span><span class="sxs-lookup"><span data-stu-id="73177-157">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![Snímek obrazovky s popisem, když uživatel přejde na tlačítko s klávesnicí](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="73177-159">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="73177-159">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="73177-160">Počínaje .NET Framework 4,8, WPF zahrnuje řadu vylepšení usnadnění.</span><span class="sxs-lookup"><span data-stu-id="73177-160">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="73177-161">**Narrator obrazovky již neoznamuje prvky se sbalenou nebo skrytou viditelností**</span><span class="sxs-lookup"><span data-stu-id="73177-161">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="73177-162">Prvky se sbalenou nebo skrytou viditelností již nejsou oznamovány čtečkou obrazovky.</span><span class="sxs-lookup"><span data-stu-id="73177-162">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="73177-163">Uživatelská rozhraní, která obsahují prvky s viditelností <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> nebo <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> mohou být reprezentována čtečkami obrazovky, pokud jsou uživateli oznámena.</span><span class="sxs-lookup"><span data-stu-id="73177-163">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="73177-164">Počínaje .NET Framework 4,8, WPF již nezahrnuje sbalené nebo skryté prvky v zobrazení ovládacích prvků stromu UIAutomation, takže čtečky obrazovky již nemohou tyto prvky oznamovat.</span><span class="sxs-lookup"><span data-stu-id="73177-164">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="73177-165">**Vlastnost SelectionTextBrush, která se má použít pro výběr textu, který není založený na Doplňky**</span><span class="sxs-lookup"><span data-stu-id="73177-165">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="73177-166">V .NET Framework 4.7.2 WPF přidala možnost kreslit <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.PasswordBox> vybírat text bez použití přípravné vrstvy.</span><span class="sxs-lookup"><span data-stu-id="73177-166">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="73177-167">Barva popředí vybraného textu v tomto scénáři byla vyřízena nástrojem <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="73177-167">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="73177-168">.NET Framework 4,8 přidá novou vlastnost, `SelectionTextBrush` která umožňuje vývojářům vybrat konkrétní štětec pro vybraný text při použití bez vizuálního výběru textu.</span><span class="sxs-lookup"><span data-stu-id="73177-168">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="73177-169">Tato vlastnost funguje pouze na <xref:System.Windows.Controls.Primitives.TextBoxBase> odvozených ovládacích prvcích a <xref:System.Windows.Controls.PasswordBox> ovládacím prvku v aplikacích WPF, které mají povolený výběr textu založený na nedoplňky.</span><span class="sxs-lookup"><span data-stu-id="73177-169">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="73177-170">Nefunguje na <xref:System.Windows.Controls.RichTextBox> ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="73177-170">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="73177-171">Pokud není povolený výběr textu založený na doplňku, bude tato vlastnost ignorována.</span><span class="sxs-lookup"><span data-stu-id="73177-171">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="73177-172">Chcete-li použít tuto vlastnost, jednoduše ji přidejte do kódu XAML a použijte příslušný štětec nebo vazbu.</span><span class="sxs-lookup"><span data-stu-id="73177-172">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="73177-173">Výsledný výběr textu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="73177-173">The resulting text selection looks like this:</span></span>

![Snímek obrazovky aplikace se spuštěnými slovy Hello World vybraných.](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

<span data-ttu-id="73177-175">Můžete zkombinovat použití `SelectionBrush` `SelectionTextBrush` vlastností a k vygenerování libovolné kombinace barev pozadí a popředí, kterou považujete za vhodnou.</span><span class="sxs-lookup"><span data-stu-id="73177-175">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="73177-176">**Podpora pro vlastnost UIAutomation ControllerFor**</span><span class="sxs-lookup"><span data-stu-id="73177-176">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="73177-177">Vlastnost UIAutomation `ControllerFor` vrací pole prvků automatizace, které jsou manipulovány prvkem automatizace, který tuto vlastnost podporuje.</span><span class="sxs-lookup"><span data-stu-id="73177-177">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="73177-178">Tato vlastnost se běžně používá pro usnadnění přístupu k automatickým návrhům.</span><span class="sxs-lookup"><span data-stu-id="73177-178">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="73177-179">`ControllerFor`se používá v případě, že prvek automatizace ovlivňuje jeden nebo více segmentů uživatelského rozhraní aplikace nebo plochy.</span><span class="sxs-lookup"><span data-stu-id="73177-179">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="73177-180">V opačném případě je těžké přidružit dopad operace řízení k prvkům uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="73177-180">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="73177-181">Tato funkce přidává možnost pro ovládací prvky pro poskytnutí hodnoty `ControllerFor` Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="73177-181">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="73177-182">.NET Framework 4,8 přidá novou virtuální metodu <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="73177-182">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="73177-183">Chcete-li zadat hodnotu `ControllerFor` vlastnosti, jednoduše přepište tuto metodu a vraťte se `List<AutomationPeer>` k ovládacím prvkům, které jsou zpracovávány tímto <xref:System.Windows.Automation.Peers.AutomationPeer> způsobem:</span><span class="sxs-lookup"><span data-stu-id="73177-183">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

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

<span data-ttu-id="73177-184">**Popisy tlačítek při přístupu k klávesnicím**</span><span class="sxs-lookup"><span data-stu-id="73177-184">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="73177-185">V .NET Framework 4.7.2 a starších verzích se popisy tlačítek zobrazují pouze v případě, že uživatel najede myší na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="73177-185">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="73177-186">V .NET Framework 4,8 se popisy tlačítek zobrazují také u fokusu klávesnice a také prostřednictvím klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="73177-186">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="73177-187">Chcete-li povolit tuto funkci, aplikace musí cílit .NET Framework 4,8 nebo se přihlásit pomocí `Switch.UseLegacyAccessibilityFeatures.3` `Switch.UseLegacyToolTipDisplay` přepínačů a [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) .</span><span class="sxs-lookup"><span data-stu-id="73177-187">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="73177-188">Následuje ukázkový konfigurační soubor aplikace:</span><span class="sxs-lookup"><span data-stu-id="73177-188">The following is a sample application configuration file:</span></span>

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

<span data-ttu-id="73177-189">Jakmile je tato možnost povolená, všechny ovládací prvky, které obsahují popisek, ji zobrazí, jakmile ovládací prvek dostane fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="73177-189">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="73177-190">Popis tlačítka může být v průběhu času zavřen nebo se změní fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="73177-190">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="73177-191">Uživatelé mohou popisek také zavřít ručně pomocí nové klávesové zkratky CTRL + SHIFT + F10.</span><span class="sxs-lookup"><span data-stu-id="73177-191">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="73177-192">Po odvolání ovládacího prvku ToolTip se můžete znovu zobrazit pomocí stejné klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="73177-192">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="73177-193">[Popisky pásu karet](xref:System.Windows.Controls.Ribbon.RibbonToolTip) u <xref:System.Windows.Controls.Ribbon.Ribbon> ovládacích prvků se nezobrazují na fokusu klávesnice. zobrazují se pouze prostřednictvím klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="73177-193">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="73177-194">**Přidaná podpora vlastností SizeOfSet a PositionInSet UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="73177-194">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="73177-195">Windows 10 představil dvě nové vlastnosti UIAutomation `SizeOfSet` a `PositionInSet` , které aplikace používají k popisu počtu položek v sadě.</span><span class="sxs-lookup"><span data-stu-id="73177-195">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="73177-196">UIAutomation klientské aplikace, jako jsou čtečky obrazovky, pak mohou pro tyto vlastnosti zadat dotaz na aplikaci a oznámit přesnou reprezentaci uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="73177-196">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="73177-197">Počínaje .NET Framework 4,8, WPF zpřístupňuje tyto dvě vlastnosti UIAutomation v aplikacích WPF.</span><span class="sxs-lookup"><span data-stu-id="73177-197">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="73177-198">Toho lze dosáhnout dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="73177-198">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="73177-199">Pomocí vlastností závislosti.</span><span class="sxs-lookup"><span data-stu-id="73177-199">By using dependency properties.</span></span>

  <span data-ttu-id="73177-200">WPF přidává dvě nové vlastnosti závislosti <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="73177-200">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="73177-201">Vývojář může použít jazyk XAML k nastavení jejich hodnot:</span><span class="sxs-lookup"><span data-stu-id="73177-201">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="73177-202">Přepsáním virtuálních metod AutomationPeer.</span><span class="sxs-lookup"><span data-stu-id="73177-202">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="73177-203"><xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> Virtuální metody a byly přidány do třídy AutomationPeer.</span><span class="sxs-lookup"><span data-stu-id="73177-203">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="73177-204">Vývojář může poskytnout hodnoty pro `SizeOfSet` a `PositionInSet` přepsáním těchto metod, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="73177-204">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

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

<span data-ttu-id="73177-205">Kromě toho položky v <xref:System.Windows.Controls.ItemsControl> instancích poskytují hodnotu pro tyto vlastnosti automaticky bez dalšího zásahu od vývojáře.</span><span class="sxs-lookup"><span data-stu-id="73177-205">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="73177-206">Pokud <xref:System.Windows.Controls.ItemsControl> je seskupená, kolekce skupin se reprezentuje jako sada a každá skupina se počítá jako samostatná sada, přičemž každá položka v této skupině poskytuje polohu v této skupině a také velikost skupiny.</span><span class="sxs-lookup"><span data-stu-id="73177-206">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="73177-207">Automatické hodnoty nejsou virtualizací ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="73177-207">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="73177-208">I v případě, že položka není vytvořena, je stále započítána do celkové velikosti sady a má vliv na pozici v sadě položek na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="73177-208">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="73177-209">Automatické hodnoty jsou poskytnuty pouze v případě, že aplikace cílí na .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="73177-209">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="73177-210">Pro aplikace, které cílí na starší verzi .NET Framework, můžete nastavit `Switch.UseLegacyAccessibilityFeatures.3` [přepínač AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), jak je znázorněno v následujícím souboru App.config:</span><span class="sxs-lookup"><span data-stu-id="73177-210">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

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

<a name="wf48"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="73177-211">Návrhář pracovního postupu programovací model Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="73177-211">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="73177-212">Návrhář pracovního postupu obsahuje následující změny v .NET Framework 4,8:</span><span class="sxs-lookup"><span data-stu-id="73177-212">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="73177-213">Uživatelům, kteří používají program Narrator, se zobrazí vylepšení popisků případu FlowSwitch.</span><span class="sxs-lookup"><span data-stu-id="73177-213">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="73177-214">Uživatelům, kteří používají program Narrator, se v popisech tlačítek zobrazí vylepšení.</span><span class="sxs-lookup"><span data-stu-id="73177-214">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="73177-215">Uživatelům, kteří si zvolí Vysoký kontrast motivům, se budou zobrazovat vylepšení viditelnosti Návrhář postupu provádění a jeho ovládacích prvků, jako jsou lepší poměry kontrastu mezi prvky a další pole výběru, která se používají pro prvky fokusu.</span><span class="sxs-lookup"><span data-stu-id="73177-215">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="73177-216">Pokud je vaše aplikace cílena .NET Framework 4.7.2 nebo starší verze, můžete tyto změny vyjádřit nastavením `Switch.UseLegacyAccessibilityFeatures.3` [přepínače AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na `false` v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="73177-216">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="73177-217">Další informace najdete v části využití [vylepšení usnadnění](#taking-advantage-of-accessibility-enhancements) v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="73177-217">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="73177-218">Co je nového v přístupnosti v .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="73177-218">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="73177-219">.NET Framework 4.7.2 zahrnuje nové funkce pro usnadnění přístupu v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="73177-219">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="73177-220">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73177-220">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="73177-221">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="73177-221">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="73177-222">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73177-222">Windows Forms</span></span>

<span data-ttu-id="73177-223">**Barvy definované operačním systémem v motivech Vysoký kontrast**</span><span class="sxs-lookup"><span data-stu-id="73177-223">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="73177-224">Počínaje .NET Framework 4.7.2 model Windows Forms používá v Vysoký kontrast motivech barvy definované operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="73177-224">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="73177-225">To má vliv na následující ovládací prvky:</span><span class="sxs-lookup"><span data-stu-id="73177-225">This affects the following controls:</span></span>

- <span data-ttu-id="73177-226">Rozevírací šipka <xref:System.Windows.Forms.ToolStripDropDownButton> ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="73177-226">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="73177-227"><xref:System.Windows.Forms.Button> <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.CheckBox> Ovládací prvky a s <xref:System.Windows.Forms.ButtonBase.FlatStyle> nastavením na <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="73177-227">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="73177-228">Dříve byly barvy vybraného textu a pozadí nekontrastované a bylo těžké je přečíst.</span><span class="sxs-lookup"><span data-stu-id="73177-228">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="73177-229">Ovládací prvky obsažené v rámci <xref:System.Windows.Forms.GroupBox> , které mají svou <xref:System.Windows.Forms.Control.Enabled> vlastnost nastavenou na `false` .</span><span class="sxs-lookup"><span data-stu-id="73177-229">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="73177-230"><xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripComboBox> Ovládací prvky, a, <xref:System.Windows.Forms.ToolStripDropDownButton> které mají vyšší poměr kontrastu světelnosti v režimu Vysoký kontrast.</span><span class="sxs-lookup"><span data-stu-id="73177-230">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="73177-231"><xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor>Vlastnost <xref:System.Windows.Forms.DataGridViewLinkCell> .</span><span class="sxs-lookup"><span data-stu-id="73177-231">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="73177-232">**Vylepšení Předčítání**</span><span class="sxs-lookup"><span data-stu-id="73177-232">**Narrator improvements**</span></span>

<span data-ttu-id="73177-233">Počínaje .NET Framework 4.7.2 se podpora Narrator rozšiřuje takto:</span><span class="sxs-lookup"><span data-stu-id="73177-233">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="73177-234">Oznamuje hodnotu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> vlastnosti při oznamování textu <xref:System.Windows.Forms.ToolStripMenuItem> .</span><span class="sxs-lookup"><span data-stu-id="73177-234">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="73177-235">Indikuje, že <xref:System.Windows.Forms.ToolStripMenuItem> má <xref:System.Windows.Forms.Control.Enabled> vlastnost nastavenou na `false` .</span><span class="sxs-lookup"><span data-stu-id="73177-235">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="73177-236">Pokud <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> je vlastnost nastavena na hodnotu, poskytuje zpětnou vazbu ke stavu zaškrtávacího políčka `true` .</span><span class="sxs-lookup"><span data-stu-id="73177-236">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="73177-237">Pořadí fokusu v režimu kontroly mluveného komentáře je konzistentní s vizuálním pořadím ovládacích prvků v dialogovém okně Stažení ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="73177-237">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="73177-238">**Vylepšení ovládacího prvku DataGridView**</span><span class="sxs-lookup"><span data-stu-id="73177-238">**DataGridView improvements**</span></span>

<span data-ttu-id="73177-239">Počínaje .NET Framework 4.7.2 <xref:System.Windows.Forms.DataGridView> zavedl ovládací prvek následující vylepšení přístupnosti:</span><span class="sxs-lookup"><span data-stu-id="73177-239">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="73177-240">Řádky lze seřadit pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="73177-240">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="73177-241">Uživatel může použít klávesu F3, aby bylo možné řadit podle aktuálního sloupce.</span><span class="sxs-lookup"><span data-stu-id="73177-241">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="73177-242">Když <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> je nastavená na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> , změní se barva záhlaví sloupce tak, aby označovala aktuální sloupec jako karty uživatelů na aktuálním řádku.</span><span class="sxs-lookup"><span data-stu-id="73177-242">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="73177-243"><xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType>Vlastnost objektu <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> vrátí správný nadřazený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="73177-243">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="73177-244">**Vylepšené vizuální pomůcky**</span><span class="sxs-lookup"><span data-stu-id="73177-244">**Improved visual cues**</span></span>

- <span data-ttu-id="73177-245"><xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.CheckBox> Ovládací prvky a s prázdnou <xref:System.Windows.Forms.ButtonBase.Text> vlastností zobrazují indikátor fokusu, když obdrží fokus.</span><span class="sxs-lookup"><span data-stu-id="73177-245">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="73177-246">**Vylepšená podpora mřížky vlastností**</span><span class="sxs-lookup"><span data-stu-id="73177-246">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="73177-247"><xref:System.Windows.Forms.PropertyGrid>Podřízené prvky ovládacího prvku nyní vrátí `true` <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> vlastnost pro vlastnost pouze v případě, že je povolen prvek PropertyGrid.</span><span class="sxs-lookup"><span data-stu-id="73177-247">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="73177-248"><xref:System.Windows.Forms.PropertyGrid>Podřízené prvky ovládacího prvku vrátí `false` <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> vlastnost pro vlastnost pouze v případě, že uživatel může změnit element PropertyGrid.</span><span class="sxs-lookup"><span data-stu-id="73177-248">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="73177-249">**Vylepšená navigace klávesnicí**</span><span class="sxs-lookup"><span data-stu-id="73177-249">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="73177-250"><xref:System.Windows.Forms.ToolStripButton>Ovládací prvek umožňuje fokus, pokud je obsažen v typu <xref:System.Windows.Forms.ToolStripPanel> , který má <xref:System.Windows.Forms.ToolStripPanel.TabStop> vlastnost nastavenou na hodnotu`true`</span><span class="sxs-lookup"><span data-stu-id="73177-250">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="73177-251">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="73177-251">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="73177-252">**Změny ovládacích prvků CheckBox a RadioButton**</span><span class="sxs-lookup"><span data-stu-id="73177-252">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="73177-253">V .NET Framework 4.7.1 a starších verzích <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> mají WPF a <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> Controls nekonzistentní a v klasických a vysoký kontrast motivech nesprávné vizuály fokusu.</span><span class="sxs-lookup"><span data-stu-id="73177-253">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="73177-254">K těmto problémům dochází v případech, kdy ovládací prvky nemají sadu obsahu.</span><span class="sxs-lookup"><span data-stu-id="73177-254">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="73177-255">To může zjednodušit přechod mezi motivy a označit vizuál jako fokus.</span><span class="sxs-lookup"><span data-stu-id="73177-255">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="73177-256">V .NET Framework 4.7.2 jsou teď tyto vizuály v různých motivech konzistentní a snadněji viditelné v klasických a Vysoký kontrastch motivech.</span><span class="sxs-lookup"><span data-stu-id="73177-256">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="73177-257">**Ovládací prvky WinForms hostované v aplikaci WPF**</span><span class="sxs-lookup"><span data-stu-id="73177-257">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="73177-258">Pro ovládací prvek WinForms, který je hostován v aplikaci WPF v .NET Framework 4.7.1 a starších verzích, uživatelé nemohli kartu vymezit vrstvy WinForms, pokud je první nebo poslední ovládací prvek v této vrstvě <xref:System.Windows.Forms.Integration.ElementHost> ovládacím prvkem WPF.</span><span class="sxs-lookup"><span data-stu-id="73177-258">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="73177-259">V .NET Framework 4.7.2 uživatelé teď můžou z vrstvy WinForms vymezit kartu.</span><span class="sxs-lookup"><span data-stu-id="73177-259">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="73177-260">Automatizované aplikace, které spoléhají na fokus bez použití řídicího panelu Vrstvy WinForms, ale nemusí nadále fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="73177-260">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="73177-261">Co je nového v přístupnosti v .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="73177-261">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="73177-262">.NET Framework 4.7.1 zahrnuje nové funkce pro usnadnění přístupu v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="73177-262">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="73177-263">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="73177-263">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="73177-264">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="73177-264">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="73177-265">Webové ovládací prvky ASP.NET</span><span class="sxs-lookup"><span data-stu-id="73177-265">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="73177-266">SDK Tools .NET</span><span class="sxs-lookup"><span data-stu-id="73177-266">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="73177-267">Programovací model Windows Workflow Foundation (WF) Návrhář postupu provádění</span><span class="sxs-lookup"><span data-stu-id="73177-267">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="73177-268">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="73177-268">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="73177-269">**Vylepšení čtečky obrazovky**</span><span class="sxs-lookup"><span data-stu-id="73177-269">**Screen reader improvements**</span></span>

<span data-ttu-id="73177-270">Pokud jsou povolena vylepšení přístupnosti, .NET Framework 4.7.1 zahrnuje následující vylepšení, která ovlivňují čtečky obrazovky:</span><span class="sxs-lookup"><span data-stu-id="73177-270">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="73177-271">V .NET Framework 4,7 a starších verzích <xref:System.Windows.Controls.Expander> byly ovládací prvky oznámeny čtečkami obrazovky jako tlačítka.</span><span class="sxs-lookup"><span data-stu-id="73177-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="73177-272">Počínaje .NET Framework 4.7.1 jsou správně ohlášeny jako rozbalitelné nebo Sbalitelné skupiny.</span><span class="sxs-lookup"><span data-stu-id="73177-272">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="73177-273">V .NET Framework 4,7 a dřívějších verzích <xref:System.Windows.Controls.DataGridCell> byly ovládací prvky oznámeny čtečkami obrazovky jako "vlastní".</span><span class="sxs-lookup"><span data-stu-id="73177-273">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="73177-274">Počínaje .NET Framework 4.7.1 jsou teď správně ohlášené jako buňka datové mřížky (lokalizovaná).</span><span class="sxs-lookup"><span data-stu-id="73177-274">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="73177-275">Počínaje .NET Framework 4.7.1, čtečky obrazovky oznamují název, který lze upravovat <xref:System.Windows.Controls.ComboBox> .</span><span class="sxs-lookup"><span data-stu-id="73177-275">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="73177-276">V .NET Framework 4,7 a dřívějších verzích <xref:System.Windows.Controls.PasswordBox> byly ovládací prvky oznámeny jako "žádná položka v zobrazení" nebo jinak nesprávnému chování.</span><span class="sxs-lookup"><span data-stu-id="73177-276">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="73177-277">Tento problém je vyřešený od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="73177-277">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="73177-278">**Podpora UIAutomation LiveRegion**</span><span class="sxs-lookup"><span data-stu-id="73177-278">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="73177-279">Čtečky obrazovky, jako je Narrator, usnadňují uživatelům čtení obsahu uživatelského rozhraní aplikace, obvykle výstupem z textu na řeč, který má fokus.</span><span class="sxs-lookup"><span data-stu-id="73177-279">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="73177-280">Pokud se však prvek uživatelského rozhraní změní a nemá fokus, uživatel nemusí být upozorněn a může si vyvšimnout důležitých informací.</span><span class="sxs-lookup"><span data-stu-id="73177-280">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="73177-281">Při řešení tohoto problému se zaměřují na živé oblasti.</span><span class="sxs-lookup"><span data-stu-id="73177-281">Live regions aim at solving this problem.</span></span> <span data-ttu-id="73177-282">Vývojář je může použít k informování čtečky obrazovky nebo jakéhokoliv jiného klienta UIAutomation, že došlo k důležité změně v prvku uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="73177-282">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="73177-283">Čtečka obrazovky pak může rozhodnout, jak a kdy se má uživatel informovat o této změně.</span><span class="sxs-lookup"><span data-stu-id="73177-283">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="73177-284">V rámci podpory živých oblastí byla do WPF přidána následující rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="73177-284">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="73177-285"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType>Pole a <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> , která identifikují vlastnost **LiveSetting** a událost **LiveRegionChanged** .</span><span class="sxs-lookup"><span data-stu-id="73177-285">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="73177-286">Lze je nastavit pomocí jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="73177-286">They can be set by using XAML.</span></span>

- <span data-ttu-id="73177-287">Připojená vlastnost **Vlastnosti automatizace. LiveSetting** , která informuje čtečku obrazovky o důležitosti změny uživatelského rozhraní pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="73177-287">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="73177-288"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>Vlastnost, která identifikuje vlastnost **Vlastnosti automatizace. LiveSetting** připojené.</span><span class="sxs-lookup"><span data-stu-id="73177-288">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="73177-289"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>Metoda, která může být přepsána tak, aby poskytovala hodnotu **LiveSetting** .</span><span class="sxs-lookup"><span data-stu-id="73177-289">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="73177-290"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType>Metody a <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> , které získají a nastavují hodnotu **LiveSetting** .</span><span class="sxs-lookup"><span data-stu-id="73177-290">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="73177-291"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>Výčet, který definuje následující možné hodnoty **LiveSetting** :</span><span class="sxs-lookup"><span data-stu-id="73177-291">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="73177-292"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73177-292"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="73177-293">Element neodesílá oznámení v případě, že se změnil obsah oblasti v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="73177-293">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="73177-294"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73177-294"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="73177-295">Element odesílá nepřerušovaná oznámení, pokud se změní obsah živé oblasti.</span><span class="sxs-lookup"><span data-stu-id="73177-295">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="73177-296"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73177-296"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="73177-297">Element odesílá oznámení o přerušování, pokud se změní obsah živé oblasti.</span><span class="sxs-lookup"><span data-stu-id="73177-297">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="73177-298">LiveRegion můžete vytvořit nastavením vlastnosti **Vlastnosti automatizace. LiveSetting** u elementu Interest, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="73177-298">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="73177-299">Když se data v živé oblasti změní a potřebujete informovat čtečku obrazovky, explicitně vyvoláte událost, jak je znázorněno v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="73177-299">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="73177-300">**High contrast**</span><span class="sxs-lookup"><span data-stu-id="73177-300">**High contrast**</span></span>

<span data-ttu-id="73177-301">Počínaje .NET Framework 4.7.1 se v různých ovládacích prvcích WPF provedla vylepšení vysokého kontrastu.</span><span class="sxs-lookup"><span data-stu-id="73177-301">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="73177-302">Jsou nyní viditelné, když <xref:System.Windows.SystemParameters.HighContrast%2A> je motiv nastaven.</span><span class="sxs-lookup"><span data-stu-id="73177-302">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="73177-303">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="73177-303">These include:</span></span>

- <span data-ttu-id="73177-304"><xref:System.Windows.Controls.Expander>nad</span><span class="sxs-lookup"><span data-stu-id="73177-304"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="73177-305">Vizuál fokusu pro <xref:System.Windows.Controls.Expander> ovládací prvek je nyní viditelný.</span><span class="sxs-lookup"><span data-stu-id="73177-305">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="73177-306">Vizuály klávesnice pro <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.RadioButton> ovládací prvky, a jsou viditelné také.</span><span class="sxs-lookup"><span data-stu-id="73177-306">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="73177-307">Příklad:</span><span class="sxs-lookup"><span data-stu-id="73177-307">For example:</span></span>

  <span data-ttu-id="73177-308">Před:</span><span class="sxs-lookup"><span data-stu-id="73177-308">Before:</span></span>

  ![Snímek obrazovky ovládacího prvku rozšíření s fokusem a bez vizuálu fokusu](./media/whats-new-in-accessibility/expander-control-before.png)

  <span data-ttu-id="73177-310">Po:</span><span class="sxs-lookup"><span data-stu-id="73177-310">After:</span></span>

  ![Snímek obrazovky ovládacího prvku rozšíření se fokusem ukazující tečkovou čáru kolem textu ovládacího prvku](./media/whats-new-in-accessibility/expander-control-after.png)

- <span data-ttu-id="73177-312"><xref:System.Windows.Controls.CheckBox>a <xref:System.Windows.Controls.RadioButton> ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="73177-312"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="73177-313">Text v <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.RadioButton> ovládacích prvcích a se teď snáze zobrazuje, když je vybraný v motivech s vysokým kontrastem.</span><span class="sxs-lookup"><span data-stu-id="73177-313">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="73177-314">Příklad:</span><span class="sxs-lookup"><span data-stu-id="73177-314">For example:</span></span>

  <span data-ttu-id="73177-315">Před:</span><span class="sxs-lookup"><span data-stu-id="73177-315">Before:</span></span>

  ![Snímek obrazovky s přepínači a zaškrtávacím tlačítky s nekvalitní viditelností textu u motivů s vysokým kontrastem](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  <span data-ttu-id="73177-317">Po:</span><span class="sxs-lookup"><span data-stu-id="73177-317">After:</span></span>

  ![Snímek obrazovky s přepínači a zaškrtávacím tlačítky s lepší viditelností textu u motivů s vysokým kontrastem](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <span data-ttu-id="73177-319"><xref:System.Windows.Controls.ComboBox>nad</span><span class="sxs-lookup"><span data-stu-id="73177-319"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="73177-320">Počínaje .NET Framework 4.7.1 je ohraničení zakázaného <xref:System.Windows.Controls.ComboBox> ovládacího prvku stejné barvy jako zakázaný text.</span><span class="sxs-lookup"><span data-stu-id="73177-320">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="73177-321">Příklad:</span><span class="sxs-lookup"><span data-stu-id="73177-321">For example:</span></span>

  <span data-ttu-id="73177-322">Před:</span><span class="sxs-lookup"><span data-stu-id="73177-322">Before:</span></span>

  ![Snímek obrazovky zakázaného pole se seznamem s textem ohraničení a ovládacího prvku v různých barvách](./media/whats-new-in-accessibility/combo-disabled-before.png)

  <span data-ttu-id="73177-324">Po:</span><span class="sxs-lookup"><span data-stu-id="73177-324">After:</span></span>

  ![Snímek obrazovky zakázaného pole se seznamem s ohraničením stejné barvy jako text ovládacího prvku](./media/whats-new-in-accessibility/combo-disabled-after.png)

  <span data-ttu-id="73177-326">Kromě toho zakázaná a zaměřená tlačítka používají správnou barvu motivu.</span><span class="sxs-lookup"><span data-stu-id="73177-326">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="73177-327">Před:</span><span class="sxs-lookup"><span data-stu-id="73177-327">Before:</span></span>

  ![Snímek obrazovky černého tlačítka se šedým textem, který se zaměřuje na mne](./media/whats-new-in-accessibility/button-theme-colors-before.png)

  <span data-ttu-id="73177-329">Po:</span><span class="sxs-lookup"><span data-stu-id="73177-329">After:</span></span>

  ![Snímek obrazovky s modrým tlačítkem s černým textem, který se zaměřuje na mne](./media/whats-new-in-accessibility/button-theme-colors-after.png)

  <span data-ttu-id="73177-331">Nakonec v .NET Framework 4,7 a starších verzích nastaví <xref:System.Windows.Controls.ComboBox> styl ovládacího prvku na hodnotu `Toolbar.ComboBoxStyleKey` neviditelná šipka rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="73177-331">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="73177-332">Tento problém je vyřešený od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="73177-332">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="73177-333">Příklad:</span><span class="sxs-lookup"><span data-stu-id="73177-333">For example:</span></span>

  <span data-ttu-id="73177-334">Před:</span><span class="sxs-lookup"><span data-stu-id="73177-334">Before:</span></span>

  ![Snímek obrazovky ovládacího prvku ComboBox se skrytou šipkou rozevíracího seznamu](./media/whats-new-in-accessibility/combo-box-style-key-before.png)

  <span data-ttu-id="73177-336">Po:</span><span class="sxs-lookup"><span data-stu-id="73177-336">After:</span></span>

  ![Snímek obrazovky ovládacího prvku polem, který zobrazuje šipku rozevíracího seznamu.](./media/whats-new-in-accessibility/combo-box-style-key-after.png)

- <span data-ttu-id="73177-338"><xref:System.Windows.Controls.DataGrid>nad</span><span class="sxs-lookup"><span data-stu-id="73177-338"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="73177-339">Počínaje .NET Framework 4.7.1, šipka indikátoru řazení v <xref:System.Windows.Controls.DataGrid> ovládacích prvcích teď používá správné barvy motivu.</span><span class="sxs-lookup"><span data-stu-id="73177-339">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="73177-340">Příklad:</span><span class="sxs-lookup"><span data-stu-id="73177-340">For example:</span></span>

  <span data-ttu-id="73177-341">Před:</span><span class="sxs-lookup"><span data-stu-id="73177-341">Before:</span></span>

  ![Snímek obrazovky se šipkou indikátoru řazení před vylepšeními](./media/whats-new-in-accessibility/sort-indicator-before.png)

  <span data-ttu-id="73177-343">Po:</span><span class="sxs-lookup"><span data-stu-id="73177-343">After:</span></span>

  ![Snímek obrazovky se šipkou indikátoru řazení po vylepšeních](./media/whats-new-in-accessibility/sort-indicator-after.png)

  <span data-ttu-id="73177-345">Kromě toho se v .NET Framework 4,7 a dřívějších verzích změnil výchozí styl propojení na nesprávnou barvu při stisknutí myši v režimech s vysokým kontrastem.</span><span class="sxs-lookup"><span data-stu-id="73177-345">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="73177-346">Tento problém se vyřeší od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="73177-346">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="73177-347">Podobně, <xref:System.Windows.Controls.DataGrid> sloupce Zaškrtávací políčko používá očekávané barvy zpětné vazby pro fokus klávesnice počínaje .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="73177-347">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="73177-348">Před:</span><span class="sxs-lookup"><span data-stu-id="73177-348">Before:</span></span>

  ![Snímek obrazovky s odkazem na něj klikněte](./media/whats-new-in-accessibility/default-link-style-before.png)

  <span data-ttu-id="73177-351">Po:</span><span class="sxs-lookup"><span data-stu-id="73177-351">After:</span></span>

  ![Snímek obrazovky s odkazem na něj klikněte](./media/whats-new-in-accessibility/default-link-style-after.png)

<span data-ttu-id="73177-354">Další informace o vylepšení usnadnění přístupu WPF v .NET Framework 4.7.1 najdete v tématu [vylepšení usnadnění v WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="73177-354">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="73177-355">Vylepšení model Windows Forms dostupnosti</span><span class="sxs-lookup"><span data-stu-id="73177-355">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="73177-356">V .NET Framework 4.7.1, model Windows Forms (WinForms), zahrnuje změny přístupnosti v následujících oblastech.</span><span class="sxs-lookup"><span data-stu-id="73177-356">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="73177-357">**Vylepšené zobrazení v režimu Vysoký kontrast**</span><span class="sxs-lookup"><span data-stu-id="73177-357">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="73177-358">Počínaje .NET Framework 4.7.1 různé ovládací prvky WinForms nabízejí Vylepšené vykreslování v režimech HighContrast, které jsou k dispozici v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="73177-358">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="73177-359">Windows 10 změnil hodnoty pro některé systémové barvy s vysokým kontrastem a model Windows Forms vychází z rozhraní Win32 pro Windows 10.</span><span class="sxs-lookup"><span data-stu-id="73177-359">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="73177-360">Pro dosažení co nejlepších výsledků spusťte aplikaci v nejnovější verzi Windows a přihlaste se k nejnovějším změnám operačního systému přidáním souboru App. manifest do testovací aplikace a odkomentujte podporovanou řádku operačního systému Windows 10 tak, aby vypadala takto:</span><span class="sxs-lookup"><span data-stu-id="73177-360">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

<span data-ttu-id="73177-361">Mezi tyto změny vysokého kontrastu patří:</span><span class="sxs-lookup"><span data-stu-id="73177-361">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="73177-362">Zaškrtnutí v <xref:System.Windows.Forms.MenuStrip> položkách je snazší zobrazit.</span><span class="sxs-lookup"><span data-stu-id="73177-362">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="73177-363">Je-li toto políčko zaškrtnuto, <xref:System.Windows.Forms.MenuStrip> je snazší zobrazit zakázané položky.</span><span class="sxs-lookup"><span data-stu-id="73177-363">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="73177-364">Text ve vybraném <xref:System.Windows.Forms.Button> ovládacím prvku má kontrast na barvě výběru.</span><span class="sxs-lookup"><span data-stu-id="73177-364">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="73177-365">Nepovolený text je snazší číst.</span><span class="sxs-lookup"><span data-stu-id="73177-365">Disabled text is easier to read.</span></span> <span data-ttu-id="73177-366">Příklad:</span><span class="sxs-lookup"><span data-stu-id="73177-366">For example:</span></span>

  <span data-ttu-id="73177-367">Před:</span><span class="sxs-lookup"><span data-stu-id="73177-367">Before:</span></span>

  ![Snímek obrazovky aplikace, která používá jiné ovládací prvky běžící v režimu s vysokým kontrastem před vylepšeními přístupnosti.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png)

  <span data-ttu-id="73177-369">Po:</span><span class="sxs-lookup"><span data-stu-id="73177-369">After:</span></span>

  ![Snímek obrazovky aplikace, která používá jiné ovládací prvky běžící v režimu s vysokým kontrastem po vylepšeních přístupnosti.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png)

- <span data-ttu-id="73177-371">Vylepšení vysokého kontrastu v dialogovém okně výjimky vlákna.</span><span class="sxs-lookup"><span data-stu-id="73177-371">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="73177-372">**Vylepšená podpora Narrator**</span><span class="sxs-lookup"><span data-stu-id="73177-372">**Improved Narrator support**</span></span>

<span data-ttu-id="73177-373">Model Windows Forms v .NET Framework 4.7.1 obsahuje následující vylepšení přístupnosti pro program Narrator:</span><span class="sxs-lookup"><span data-stu-id="73177-373">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="73177-374">K <xref:System.Windows.Forms.MonthCalendar> ovládacímu prvku může přicházet program Narrator a také k ostatním nástrojům pro automatizaci uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="73177-374">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="73177-375"><xref:System.Windows.Forms.CheckedListBox>Ovládací prvek upozorní program Narrator, když se změní stav kontroly položky, takže uživatel bude informován o tom, že změnil hodnotu položky seznamu.</span><span class="sxs-lookup"><span data-stu-id="73177-375">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="73177-376"><xref:System.Windows.Forms.DataGridViewCell>Ovládací prvek oznamuje do programu Narrator správný stav jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="73177-376">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="73177-377">Program Narrator teď může číst zakázaný <xref:System.Windows.Forms.ToolStripMenuItem> text, zatímco dřív by přeskočil zakázané položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="73177-377">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="73177-378">**Vylepšená podpora pro vzory usnadnění UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="73177-378">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="73177-379">Od .NET Framework 4.7.1 můžou vývojáři nástrojů pro usnadnění přístupu využít běžné vzory a vlastnosti přístupnosti rozhraní API pro několik ovládacích prvků WinForms.</span><span class="sxs-lookup"><span data-stu-id="73177-379">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="73177-380">Mezi tato vylepšení přístupnosti patří:</span><span class="sxs-lookup"><span data-stu-id="73177-380">These accessibility improvements include:</span></span>

- <span data-ttu-id="73177-381"><xref:System.Windows.Forms.ComboBox>A <xref:System.Windows.Forms.ToolStripSplitButton> teď podporuje [model rozbalení a sbalení](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="73177-381">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="73177-382"><xref:System.Windows.Forms.DataGridViewCheckBoxCell>Teď podporuje [vzor přepínacího](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)tlačítka.</span><span class="sxs-lookup"><span data-stu-id="73177-382">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="73177-383"><xref:System.Windows.Forms.ToolStripItem>Ovládací prvek podporuje <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> vlastnost a vzorek pro [rozbalení a sbalení](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="73177-383">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="73177-384"><xref:System.Windows.Forms.NumericUpDown> <xref:System.Windows.Forms.DomainUpDown> Ovládací prvky a podporují <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="73177-384">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="73177-385">**Vylepšené prostředí prohlížeče vlastností**</span><span class="sxs-lookup"><span data-stu-id="73177-385">**Improved property browser experience**</span></span>

<span data-ttu-id="73177-386">Počínaje .NET Framework 4.7.1 model Windows Forms zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="73177-386">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="73177-387">Lepší navigace pomocí klávesnice v různých oknech pro výběr rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="73177-387">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="73177-388">Snížení zbytečných zarážek tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="73177-388">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="73177-389">Lepší vytváření sestav typů ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="73177-389">Better reporting of control types.</span></span>
- <span data-ttu-id="73177-390">Vylepšené chování Předčítání.</span><span class="sxs-lookup"><span data-stu-id="73177-390">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="73177-391">Webové ovládací prvky ASP.NET</span><span class="sxs-lookup"><span data-stu-id="73177-391">ASP.NET web controls</span></span>

<span data-ttu-id="73177-392">Počínaje .NET Framework 4.7.1 a sadou Visual Studio 2017 verze 15,3 ASP.NET vylepšuje, jak ASP.NET webové ovládací prvky fungují s technologiemi usnadnění v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="73177-392">Starting with .NET Framework 4.7.1 and Visual Studio 2017 version 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="73177-393">Změny zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="73177-393">Changes include the following:</span></span>

- <span data-ttu-id="73177-394">Změny pro implementaci chybějících vzorů přístupnosti uživatelského rozhraní v ovládacích prvcích, jako je dialogové okno **Přidat pole** v průvodci **zobrazení podrobností** nebo dialogové okno **Konfigurovat ListView** průvodce **ListView** .</span><span class="sxs-lookup"><span data-stu-id="73177-394">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="73177-395">Změny pro zlepšení zobrazení v režimu Vysoký kontrast, jako je například **Editor polí datového pageru**.</span><span class="sxs-lookup"><span data-stu-id="73177-395">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="73177-396">Změny pro zlepšení prostředí navigace klávesnicí pro ovládací prvky, jako je dialogové okno **pole** v průvodci **úpravou polí stránkování** ovládacího prvku DataPager, dialogové **okno Konfigurovat ObjectContext** nebo dialogové okno **Konfigurovat výběr dat** v průvodci **konfigurací zdroje dat** .</span><span class="sxs-lookup"><span data-stu-id="73177-396">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="73177-397">SDK Tools .NET</span><span class="sxs-lookup"><span data-stu-id="73177-397">.NET SDK Tools</span></span>

<span data-ttu-id="73177-398">[Nástroj Configuration Editor (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) a [nástroj Service Trace Viewer (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) byly vylepšeny opravou různých problémů s přístupností.</span><span class="sxs-lookup"><span data-stu-id="73177-398">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="73177-399">Většina těchto došlo k malým problémům, jako je název, který není definován, nebo některé vzorce automatizace uživatelského rozhraní nejsou správně implementovány.</span><span class="sxs-lookup"><span data-stu-id="73177-399">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="73177-400">I když mnoho uživatelů nebude vědět o těchto nesprávných hodnotách, zákazníci, kteří používají asistenční technologie, jako jsou čtečky obrazovky, budou tyto nástroje sady SDK k dispozici podrobněji.</span><span class="sxs-lookup"><span data-stu-id="73177-400">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="73177-401">Tato vylepšení mění některá předchozí chování, jako je například pořadí fokusu klávesnice.</span><span class="sxs-lookup"><span data-stu-id="73177-401">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="73177-402">Programovací model Windows Workflow Foundation (WF) Návrhář postupu provádění</span><span class="sxs-lookup"><span data-stu-id="73177-402">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="73177-403">Změny přístupnosti v Návrhář postupu provádění zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="73177-403">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="73177-404">Pořadí karet se změní na zleva doprava a shora dolů v některých ovládacích prvcích:</span><span class="sxs-lookup"><span data-stu-id="73177-404">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="73177-405">Okno Inicializace korelace pro nastavení dat korelace pro <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivitu.</span><span class="sxs-lookup"><span data-stu-id="73177-405">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="73177-406">Okno Definice obsahu pro <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.Send> aktivity,, a <xref:System.ServiceModel.Activities.SendReply> <xref:System.ServiceModel.Activities.ReceiveReply> .</span><span class="sxs-lookup"><span data-stu-id="73177-406">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="73177-407">Další funkce jsou k dispozici prostřednictvím klávesnice:</span><span class="sxs-lookup"><span data-stu-id="73177-407">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="73177-408">Při úpravách vlastností aktivity mohou být skupiny vlastností sbaleny klávesnicí při prvním zaměření.</span><span class="sxs-lookup"><span data-stu-id="73177-408">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="73177-409">Ikony upozornění jsou přístupné z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="73177-409">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="73177-410">Tlačítko **Další vlastnosti** v okně **vlastnosti** je přístupné z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="73177-410">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="73177-411">Uživatelé klávesnice mají přístup k položkám záhlaví v podoknech **argumenty** a **proměnné** Návrhář postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="73177-411">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="73177-412">Vylepšená viditelnost položek s fokusem, například když:</span><span class="sxs-lookup"><span data-stu-id="73177-412">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="73177-413">Přidávání řádků do datových mříží používaných návrháři Návrhář postupu provádění a aktivit.</span><span class="sxs-lookup"><span data-stu-id="73177-413">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="73177-414">Procházení polí v <xref:System.ServiceModel.Activities.ReceiveReply> <xref:System.ServiceModel.Activities.SendReply> aktivitách a</span><span class="sxs-lookup"><span data-stu-id="73177-414">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="73177-415">Nastavení výchozích hodnot pro proměnné nebo argumenty</span><span class="sxs-lookup"><span data-stu-id="73177-415">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="73177-416">Čtečky obrazovky teď můžou správně rozpoznat:</span><span class="sxs-lookup"><span data-stu-id="73177-416">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="73177-417">Zarážky nastavené v Návrháři postupu.</span><span class="sxs-lookup"><span data-stu-id="73177-417">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="73177-418"><xref:System.Activities.Statements.FlowSwitch%601>Aktivity, <xref:System.Activities.Statements.FlowDecision> a <xref:System.ServiceModel.Activities.CorrelationScope> .</span><span class="sxs-lookup"><span data-stu-id="73177-418">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="73177-419">Obsah <xref:System.ServiceModel.Activities.Receive> aktivity</span><span class="sxs-lookup"><span data-stu-id="73177-419">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="73177-420">Cílový typ <xref:System.Activities.Statements.InvokeMethod> aktivity.</span><span class="sxs-lookup"><span data-stu-id="73177-420">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="73177-421">Pole se seznamem výjimek a oddíl finally v <xref:System.Activities.Statements.TryCatch> aktivitě.</span><span class="sxs-lookup"><span data-stu-id="73177-421">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="73177-422">Pole se seznamem typ zprávy, rozdělovač v okně Přidat Inicializátory korelace, okno Definice obsahu a okno definice vlastnosti CorrelatesOn v aktivitách zasílání zpráv ( <xref:System.ServiceModel.Activities.Receive> ,, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> a <xref:System.ServiceModel.Activities.ReceiveReply> ).</span><span class="sxs-lookup"><span data-stu-id="73177-422">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="73177-423">Cíle přechodů a přechodů stavového stroje.</span><span class="sxs-lookup"><span data-stu-id="73177-423">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="73177-424">Poznámky a konektory v <xref:System.Activities.Statements.FlowDecision> aktivitách.</span><span class="sxs-lookup"><span data-stu-id="73177-424">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="73177-425">Místní nabídky pro aktivity v kontextu (klikněte pravým tlačítkem myši).</span><span class="sxs-lookup"><span data-stu-id="73177-425">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="73177-426">Editor hodnot vlastností, tlačítko Vymazat hledání, kategorie podle abecedy a abecední řazení a dialogové okno Editor výrazů v mřížce vlastností.</span><span class="sxs-lookup"><span data-stu-id="73177-426">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="73177-427">Procento přiblížení v Návrhář postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="73177-427">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="73177-428">Oddělovač v rámci <xref:System.Activities.Statements.Parallel> a <xref:System.Activities.Statements.Pick> aktivity.</span><span class="sxs-lookup"><span data-stu-id="73177-428">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="73177-429"><xref:System.Activities.Statements.InvokeDelegate>Aktivita.</span><span class="sxs-lookup"><span data-stu-id="73177-429">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="73177-430">Okno vybrat typy pro aktivity slovníku ( `Microsoft.Activities.AddToDictionary<TKey,TValue>` , `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>` atd.).</span><span class="sxs-lookup"><span data-stu-id="73177-430">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="73177-431">Okno Procházet a vybrat typ .NET.</span><span class="sxs-lookup"><span data-stu-id="73177-431">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="73177-432">Popis cesty v Návrhář postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="73177-432">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="73177-433">Uživatelům, kteří si zvolí Vysoký kontrast Themes, se zobrazí mnoho vylepšení viditelnosti Návrhář postupu provádění a jeho ovládacích prvků, jako je lepší poměr kontrastu mezi prvky a další pole výběru, která se používají pro prvky fokusu.</span><span class="sxs-lookup"><span data-stu-id="73177-433">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="73177-434">Viz také</span><span class="sxs-lookup"><span data-stu-id="73177-434">See also</span></span>

- [<span data-ttu-id="73177-435">Novinky v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="73177-435">What's new in the .NET Framework</span></span>](index.md)
