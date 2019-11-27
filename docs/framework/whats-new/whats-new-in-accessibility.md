---
title: Co je nového v přístupnosti v .NET Framework
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
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="f7372-102">Co je nového v přístupnosti v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f7372-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="f7372-103">.NET Framework se zaměřuje na zajištění přístupnosti aplikací pro vaše uživatele.</span><span class="sxs-lookup"><span data-stu-id="f7372-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="f7372-104">Funkce usnadnění umožňují aplikaci poskytovat vhodné prostředí pro uživatele technologie usnadnění.</span><span class="sxs-lookup"><span data-stu-id="f7372-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="f7372-105">Počínaje .NET Framework 4.7.1 .NET Framework obsahuje velký počet vylepšení usnadnění, která vývojářům umožňují vytvářet přístupné aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7372-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="f7372-106">Přepínače přístupnosti</span><span class="sxs-lookup"><span data-stu-id="f7372-106">Accessibility switches</span></span>

<span data-ttu-id="f7372-107">Aplikaci můžete nakonfigurovat tak, aby se přihlásila k funkcím přístupnosti, pokud cílíte .NET Framework 4,7 nebo starší verzi, ale běží na .NET Framework 4.7.1 nebo novějším.</span><span class="sxs-lookup"><span data-stu-id="f7372-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="f7372-108">Pokud cílíte .NET Framework 4.7.1 nebo novější, můžete aplikaci nakonfigurovat tak, aby používala starší funkce (a nevyužila výhody funkcí usnadnění).</span><span class="sxs-lookup"><span data-stu-id="f7372-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="f7372-109">Každá verze .NET Framework, která zahrnuje funkce usnadnění, má přepínač dostupnosti specifický pro verzi, který přidáte do prvku [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) v části [`<runtime>`](../configure-apps/file-schema/runtime/index.md) konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7372-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="f7372-110">Podporovány jsou následující přepínače:</span><span class="sxs-lookup"><span data-stu-id="f7372-110">The following are the supported switches:</span></span>

|<span data-ttu-id="f7372-111">Verze</span><span class="sxs-lookup"><span data-stu-id="f7372-111">Version</span></span>|<span data-ttu-id="f7372-112">Přepínač</span><span class="sxs-lookup"><span data-stu-id="f7372-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="f7372-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="f7372-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="f7372-114">"Switch. UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="f7372-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="f7372-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="f7372-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="f7372-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="f7372-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="f7372-117">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="f7372-117">.NET Framework 4.8</span></span>|<span data-ttu-id="f7372-118">"Switch.UseLegacyAccessibilityFeatures.3"</span><span class="sxs-lookup"><span data-stu-id="f7372-118">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="f7372-119">Využití výhod vylepšení usnadnění přístupu</span><span class="sxs-lookup"><span data-stu-id="f7372-119">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="f7372-120">Nové funkce usnadnění jsou ve výchozím nastavení povolené pro aplikace, které cílí na .NET Framework 4.7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="f7372-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="f7372-121">Kromě toho aplikace, které cílí na starší verzi .NET Framework, ale jsou spuštěné v .NET Framework 4.7.1 nebo novější, se můžou odhlásit ze starší verze chování přístupnosti (a tím využít vylepšení přístupnosti) přidáním přepínačů do prvku [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) v části [`<runtime>`](../configure-apps/file-schema/runtime/index.md) konfiguračního souboru aplikace a nastavením jejich hodnoty na `false`.</span><span class="sxs-lookup"><span data-stu-id="f7372-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="f7372-122">V následující části se dozvíte, jak se vyjádřit k vylepšením usnadnění zavedeným v .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="f7372-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="f7372-123">Pokud se rozhodnete pro funkce přístupnosti v novější verzi .NET Framework vyjádřit, musíte se taky výslovně odhlásit k funkcím z dřívějších verzí .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f7372-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="f7372-124">Konfigurace vaší aplikace pro využívání výhod vylepšení usnadnění v .NET Framework 4.7.1 i 4.7.2 vyžaduje následující [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek:</span><span class="sxs-lookup"><span data-stu-id="f7372-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="f7372-125">Konfigurace vaší aplikace pro využívání výhod vylepšení usnadnění v .NET Framework 4.7.1, 4.7.2 a 4,8 vyžaduje následující [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek:</span><span class="sxs-lookup"><span data-stu-id="f7372-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="f7372-126">Obnovení starší verze chování</span><span class="sxs-lookup"><span data-stu-id="f7372-126">Restoring legacy behavior</span></span>

<span data-ttu-id="f7372-127">Aplikace, které cílí na verze .NET Framework začínající na 4.7.1, mohou zakázat funkce usnadnění přidáním přepínačů do [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) elementu v části [`<runtime>`](../configure-apps/file-schema/runtime/index.md) konfiguračního souboru aplikace a nastavením hodnoty na `true`.</span><span class="sxs-lookup"><span data-stu-id="f7372-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="f7372-128">Například následující konfigurace výslovný z funkcí usnadnění zavedených v .NET Framework 4.7.2:</span><span class="sxs-lookup"><span data-stu-id="f7372-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="f7372-129">Co je nového v přístupnosti v .NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="f7372-129">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="f7372-130">.NET Framework 4,8 obsahuje nové funkce pro usnadnění přístupu v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="f7372-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="f7372-131">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7372-131">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="f7372-132">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="f7372-132">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="f7372-133">Návrhář pracovního postupu programovací model Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="f7372-133">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a><span data-ttu-id="f7372-134">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7372-134">Windows Forms</span></span>

<span data-ttu-id="f7372-135">V .NET Framework 4,8 model Windows Forms přidává podporu pro události LiveRegions a Notification k mnoha běžně používaným ovládacím prvkům.</span><span class="sxs-lookup"><span data-stu-id="f7372-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="f7372-136">Pokud uživatel přejde k ovládacímu prvku pomocí klávesnice, přidá také podporu pro popisky tlačítek.</span><span class="sxs-lookup"><span data-stu-id="f7372-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="f7372-137">**Podpora UIA LiveRegions ve jmenovkách a StatusStrips**</span><span class="sxs-lookup"><span data-stu-id="f7372-137">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="f7372-138">UIA LiveRegions umožňuje vývojářům aplikací upozorňovat čtečky obrazovky na změnu textu v ovládacím prvku, který se nachází vedle místa, kde uživatel pracuje.</span><span class="sxs-lookup"><span data-stu-id="f7372-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="f7372-139">To je užitečné, například pro <xref:System.Windows.Forms.StatusStrip> ovládací prvek, který zobrazuje stav připojení.</span><span class="sxs-lookup"><span data-stu-id="f7372-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="f7372-140">Pokud se připojení vynechá a změní se stav, vývojář může chtít informovat čtečku obrazovky.</span><span class="sxs-lookup"><span data-stu-id="f7372-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="f7372-141">Počínaje .NET Framework 4,8 model Windows Forms implementuje UIA LiveRegions pro ovládací prvky <xref:System.Windows.Forms.Label> a <xref:System.Windows.Forms.StatusStrip>.</span><span class="sxs-lookup"><span data-stu-id="f7372-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="f7372-142">Například následující kód používá LiveRegion v ovládacím prvku <xref:System.Windows.Forms.Label> s názvem `label1`:</span><span class="sxs-lookup"><span data-stu-id="f7372-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="f7372-143">Narrator oznamuje "připravený" bez ohledu na to, kde uživatel interakci s aplikací.</span><span class="sxs-lookup"><span data-stu-id="f7372-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="f7372-144"><xref:System.Windows.Forms.UserControl> můžete implementovat taky jako LiveRegion:</span><span class="sxs-lookup"><span data-stu-id="f7372-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

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

<span data-ttu-id="f7372-145">**Události oznámení UIA**</span><span class="sxs-lookup"><span data-stu-id="f7372-145">**UIA notification events**</span></span>

<span data-ttu-id="f7372-146">Událost oznámení UIA zavedená ve Windows 10 vede k aktualizaci Creators Update, umožňuje vaší aplikaci vyvolat událost UIA, která vede k tomu, že v programu Narrator stačí vytvořit oznámení na základě textu, který zadáte do události, aniž by bylo nutné mít odpovídající ovládací prvek v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f7372-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="f7372-147">V některých scénářích je to jednoduchý způsob, jak výrazně zlepšit přístupnost vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7372-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="f7372-148">Aplikace může být užitečná také pro oznamování průběhu některých procesů, které mohou trvat dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="f7372-148">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="f7372-149">Další informace o událostech oznámení UIA najdete v tématu [může vaše desktopová aplikace využít novou událost oznámení uživatelského rozhraní?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span><span class="sxs-lookup"><span data-stu-id="f7372-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span></span>

<span data-ttu-id="f7372-150">Následující příklad vyvolá [událost oznámení](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span><span class="sxs-lookup"><span data-stu-id="f7372-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="f7372-151">**Popisy tlačítek při přístupu k klávesnicím**</span><span class="sxs-lookup"><span data-stu-id="f7372-151">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="f7372-152">V aplikacích, které cílí na .NET Framework 4.7.2 a starších verzí, lze [Popis](xref:System.Windows.Forms.ToolTip) ovládacího prvku aktivovat pouze přesunutím ukazatele myši do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f7372-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="f7372-153">Počínaje .NET Framework 4,8 může uživatel klávesnice aktivovat Popis ovládacího prvku tím, že zaměří ovládací prvek pomocí klávesy tabulátoru nebo kláves se šipkami s nebo bez modifikačních kláves.</span><span class="sxs-lookup"><span data-stu-id="f7372-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="f7372-154">Toto konkrétní vylepšení přístupnosti vyžaduje další [přepínač AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span><span class="sxs-lookup"><span data-stu-id="f7372-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

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

<span data-ttu-id="f7372-155">Následující obrázek znázorňuje popis tlačítka, když uživatel vybere tlačítko s klávesnicí.</span><span class="sxs-lookup"><span data-stu-id="f7372-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![Snímek obrazovky s popisem, když uživatel přejde na tlačítko s klávesnicí](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="f7372-157">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="f7372-157">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="f7372-158">Počínaje .NET Framework 4,8, WPF zahrnuje řadu vylepšení usnadnění.</span><span class="sxs-lookup"><span data-stu-id="f7372-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="f7372-159">**Narrator obrazovky již neoznamuje prvky se sbalenou nebo skrytou viditelností**</span><span class="sxs-lookup"><span data-stu-id="f7372-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="f7372-160">Prvky se sbalenou nebo skrytou viditelností již nejsou oznamovány čtečkou obrazovky.</span><span class="sxs-lookup"><span data-stu-id="f7372-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="f7372-161">Uživatelská rozhraní, která obsahují prvky s viditelností <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> nebo <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType>, mohou být vystupovat čtečkami obrazovky, pokud jsou uživateli oznámena.</span><span class="sxs-lookup"><span data-stu-id="f7372-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="f7372-162">Počínaje .NET Framework 4,8, WPF již nezahrnuje sbalené nebo skryté prvky v zobrazení ovládacích prvků stromu UIAutomation, takže čtečky obrazovky již nemohou tyto prvky oznamovat.</span><span class="sxs-lookup"><span data-stu-id="f7372-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="f7372-163">**Vlastnost SelectionTextBrush, která se má použít pro výběr textu, který není založený na Doplňky**</span><span class="sxs-lookup"><span data-stu-id="f7372-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="f7372-164">Ve .NET Framework 4.7.2 WPF přidala možnost nakreslit <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.PasswordBox> výběr textu bez použití přípravné vrstvy.</span><span class="sxs-lookup"><span data-stu-id="f7372-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="f7372-165">Barva popředí vybraného textu v tomto scénáři byla vyřízena <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7372-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="f7372-166">.NET Framework 4,8 přidá novou vlastnost `SelectionTextBrush`, která umožňuje vývojářům vybrat konkrétní štětec pro vybraný text při použití bez výběru textu založeného na doplňku.</span><span class="sxs-lookup"><span data-stu-id="f7372-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="f7372-167">Tato vlastnost funguje pouze na <xref:System.Windows.Controls.Primitives.TextBoxBase>– odvozené ovládací prvky a ovládací prvek <xref:System.Windows.Controls.PasswordBox> v aplikacích WPF s povoleným ovládacím prvkem pro výběr textu, který není založen na prvcích doplňky.</span><span class="sxs-lookup"><span data-stu-id="f7372-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="f7372-168">Nefunguje na ovládacím prvku <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="f7372-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="f7372-169">Pokud není povolený výběr textu založený na doplňku, bude tato vlastnost ignorována.</span><span class="sxs-lookup"><span data-stu-id="f7372-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="f7372-170">Chcete-li použít tuto vlastnost, jednoduše ji přidejte do kódu XAML a použijte příslušný štětec nebo vazbu.</span><span class="sxs-lookup"><span data-stu-id="f7372-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="f7372-171">Výsledný výběr textu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f7372-171">The resulting text selection looks like this:</span></span>

![Snímek obrazovky aplikace se spuštěnými slovy Hello World vybraných.](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

<span data-ttu-id="f7372-173">Můžete zkombinovat použití vlastností `SelectionBrush` a `SelectionTextBrush` k vygenerování jakékoli kombinace barev pozadí a popředí, kterou považujete za vhodnou.</span><span class="sxs-lookup"><span data-stu-id="f7372-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="f7372-174">**Podpora pro vlastnost UIAutomation ControllerFor**</span><span class="sxs-lookup"><span data-stu-id="f7372-174">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="f7372-175">Vlastnost `ControllerFor` UIAutomation vrací pole prvků automatizace, které jsou manipulovány prvkem automatizace, který tuto vlastnost podporuje.</span><span class="sxs-lookup"><span data-stu-id="f7372-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="f7372-176">Tato vlastnost se běžně používá pro usnadnění přístupu k automatickým návrhům.</span><span class="sxs-lookup"><span data-stu-id="f7372-176">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="f7372-177">`ControllerFor` se používá v případě, že prvek automatizace ovlivňuje jeden nebo více segmentů uživatelského rozhraní aplikace nebo plochy.</span><span class="sxs-lookup"><span data-stu-id="f7372-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="f7372-178">V opačném případě je těžké přidružit dopad operace řízení k prvkům uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f7372-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="f7372-179">Tato funkce přidává možnost pro ovládací prvky pro poskytnutí hodnoty vlastnosti `ControllerFor`.</span><span class="sxs-lookup"><span data-stu-id="f7372-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="f7372-180">.NET Framework 4,8 přidá novou virtuální metodu <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7372-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f7372-181">Chcete-li zadat hodnotu vlastnosti `ControllerFor`, jednoduše popište tuto metodu a vraťte `List<AutomationPeer>` ovládacích prvků, které jsou tímto <xref:System.Windows.Automation.Peers.AutomationPeer>zpracovávány:</span><span class="sxs-lookup"><span data-stu-id="f7372-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

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

<span data-ttu-id="f7372-182">**Popisy tlačítek při přístupu k klávesnicím**</span><span class="sxs-lookup"><span data-stu-id="f7372-182">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="f7372-183">V .NET Framework 4.7.2 a starších verzích se popisy tlačítek zobrazují pouze v případě, že uživatel najede myší na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f7372-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="f7372-184">V .NET Framework 4,8 se popisy tlačítek zobrazují také u fokusu klávesnice a také prostřednictvím klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="f7372-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="f7372-185">Chcete-li povolit tuto funkci, aplikace musí cílit .NET Framework 4,8 nebo se přihlásit pomocí přepínačů `Switch.UseLegacyAccessibilityFeatures.3` a `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) .</span><span class="sxs-lookup"><span data-stu-id="f7372-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="f7372-186">Následuje ukázkový konfigurační soubor aplikace:</span><span class="sxs-lookup"><span data-stu-id="f7372-186">The following is a sample application configuration file:</span></span>

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

<span data-ttu-id="f7372-187">Jakmile je tato možnost povolená, všechny ovládací prvky, které obsahují popisek, ji zobrazí, jakmile ovládací prvek dostane fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="f7372-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="f7372-188">Popis tlačítka může být v průběhu času zavřen nebo se změní fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="f7372-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="f7372-189">Uživatelé mohou popisek také zavřít ručně pomocí nové klávesové zkratky CTRL + SHIFT + F10.</span><span class="sxs-lookup"><span data-stu-id="f7372-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="f7372-190">Po odvolání ovládacího prvku ToolTip se můžete znovu zobrazit pomocí stejné klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="f7372-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="f7372-191">[Popisky pásu karet](xref:System.Windows.Controls.Ribbon.RibbonToolTip) u ovládacích prvků <xref:System.Windows.Controls.Ribbon.Ribbon> se nebudou zobrazovat u fokusu klávesnice; zobrazují se pouze prostřednictvím klávesové zkratky.</span><span class="sxs-lookup"><span data-stu-id="f7372-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="f7372-192">**Přidaná podpora vlastností SizeOfSet a PositionInSet UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="f7372-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="f7372-193">Windows 10 představil dvě nové vlastnosti UIAutomation `SizeOfSet` a `PositionInSet`, které aplikace používají k popisu počtu položek v sadě.</span><span class="sxs-lookup"><span data-stu-id="f7372-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="f7372-194">UIAutomation klientské aplikace, jako jsou čtečky obrazovky, pak mohou pro tyto vlastnosti zadat dotaz na aplikaci a oznámit přesnou reprezentaci uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7372-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="f7372-195">Počínaje .NET Framework 4,8, WPF zpřístupňuje tyto dvě vlastnosti UIAutomation v aplikacích WPF.</span><span class="sxs-lookup"><span data-stu-id="f7372-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="f7372-196">Toho lze dosáhnout dvěma způsoby:</span><span class="sxs-lookup"><span data-stu-id="f7372-196">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="f7372-197">Pomocí vlastností závislosti.</span><span class="sxs-lookup"><span data-stu-id="f7372-197">By using dependency properties.</span></span>

  <span data-ttu-id="f7372-198">WPF přidává dvě nové vlastnosti závislosti <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7372-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f7372-199">Vývojář může použít jazyk XAML k nastavení jejich hodnot:</span><span class="sxs-lookup"><span data-stu-id="f7372-199">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="f7372-200">Přepsáním virtuálních metod AutomationPeer.</span><span class="sxs-lookup"><span data-stu-id="f7372-200">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="f7372-201">Do třídy AutomationPeer byly přidány virtuální metody <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> a <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore>.</span><span class="sxs-lookup"><span data-stu-id="f7372-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="f7372-202">Vývojář může poskytnout hodnoty pro `SizeOfSet` a `PositionInSet` přepsáním těchto metod, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f7372-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

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

<span data-ttu-id="f7372-203">Kromě toho položky v instancích <xref:System.Windows.Controls.ItemsControl> poskytují hodnotu pro tyto vlastnosti automaticky bez dalšího zásahu od vývojáře.</span><span class="sxs-lookup"><span data-stu-id="f7372-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="f7372-204">Pokud se <xref:System.Windows.Controls.ItemsControl> seskupí, kolekce skupin se reprezentuje jako sada a každá skupina se počítá jako samostatná sada, přičemž každá položka v této skupině poskytuje polohu v této skupině a také velikost skupiny.</span><span class="sxs-lookup"><span data-stu-id="f7372-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="f7372-205">Automatické hodnoty nejsou virtualizací ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="f7372-205">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="f7372-206">I v případě, že položka není vytvořena, je stále započítána do celkové velikosti sady a má vliv na pozici v sadě položek na stejné úrovni.</span><span class="sxs-lookup"><span data-stu-id="f7372-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="f7372-207">Automatické hodnoty jsou poskytnuty pouze v případě, že aplikace cílí na .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="f7372-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="f7372-208">Pro aplikace, které cílí na starší verzi .NET Framework, můžete nastavit [přepínač `Switch.UseLegacyAccessibilityFeatures.3` AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), jak je znázorněno v následujícím souboru App. config:</span><span class="sxs-lookup"><span data-stu-id="f7372-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

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

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="f7372-209">Návrhář pracovního postupu programovací model Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="f7372-209">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="f7372-210">Návrhář pracovního postupu obsahuje následující změny v .NET Framework 4,8:</span><span class="sxs-lookup"><span data-stu-id="f7372-210">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="f7372-211">Uživatelům, kteří používají program Narrator, se zobrazí vylepšení popisků případu FlowSwitch.</span><span class="sxs-lookup"><span data-stu-id="f7372-211">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="f7372-212">Uživatelům, kteří používají program Narrator, se v popisech tlačítek zobrazí vylepšení.</span><span class="sxs-lookup"><span data-stu-id="f7372-212">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="f7372-213">Uživatelům, kteří si zvolí Vysoký kontrast motivům, se budou zobrazovat vylepšení viditelnosti Návrhář postupu provádění a jeho ovládacích prvků, jako jsou lepší poměry kontrastu mezi prvky a další pole výběru, která se používají pro prvky fokusu.</span><span class="sxs-lookup"><span data-stu-id="f7372-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="f7372-214">Pokud je vaše aplikace cílena .NET Framework 4.7.2 nebo starší verze, můžete se k těmto změnám vyjádřit nastavením `Switch.UseLegacyAccessibilityFeatures.3` [přepínač AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) na `false` v konfiguračním souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="f7372-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="f7372-215">Další informace najdete v části využití [vylepšení usnadnění](#taking-advantage-of-accessibility-enhancements) v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="f7372-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="f7372-216">Co je nového v přístupnosti v .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="f7372-216">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="f7372-217">.NET Framework 4.7.2 zahrnuje nové funkce pro usnadnění přístupu v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="f7372-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="f7372-218">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7372-218">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="f7372-219">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="f7372-219">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="f7372-220">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7372-220">Windows Forms</span></span>

<span data-ttu-id="f7372-221">**Barvy definované operačním systémem v motivech Vysoký kontrast**</span><span class="sxs-lookup"><span data-stu-id="f7372-221">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="f7372-222">Počínaje .NET Framework 4.7.2 model Windows Forms používá v Vysoký kontrast motivech barvy definované operačním systémem.</span><span class="sxs-lookup"><span data-stu-id="f7372-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="f7372-223">To má vliv na následující ovládací prvky:</span><span class="sxs-lookup"><span data-stu-id="f7372-223">This affects the following controls:</span></span>

- <span data-ttu-id="f7372-224">Rozevírací šipka ovládacího prvku <xref:System.Windows.Forms.ToolStripDropDownButton></span><span class="sxs-lookup"><span data-stu-id="f7372-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="f7372-225">Ovládací prvky <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> a <xref:System.Windows.Forms.CheckBox> s <xref:System.Windows.Forms.ButtonBase.FlatStyle> nastavenými na <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7372-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f7372-226">Dříve byly barvy vybraného textu a pozadí nekontrastované a bylo těžké je přečíst.</span><span class="sxs-lookup"><span data-stu-id="f7372-226">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="f7372-227">Ovládací prvky obsažené v <xref:System.Windows.Forms.GroupBox>, které mají jeho vlastnost <xref:System.Windows.Forms.Control.Enabled> nastavenou na `false`.</span><span class="sxs-lookup"><span data-stu-id="f7372-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="f7372-228">Ovládací prvky <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>a <xref:System.Windows.Forms.ToolStripDropDownButton>, které mají vyšší poměr kontrastu pro světelnost v režimu Vysoký kontrast.</span><span class="sxs-lookup"><span data-stu-id="f7372-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="f7372-229">Vlastnost <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> <xref:System.Windows.Forms.DataGridViewLinkCell></span><span class="sxs-lookup"><span data-stu-id="f7372-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="f7372-230">**Vylepšení Předčítání**</span><span class="sxs-lookup"><span data-stu-id="f7372-230">**Narrator improvements**</span></span>

<span data-ttu-id="f7372-231">Počínaje .NET Framework 4.7.2 se podpora Narrator rozšiřuje takto:</span><span class="sxs-lookup"><span data-stu-id="f7372-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="f7372-232">Oznamuje hodnotu vlastnosti <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> při oznamování textu <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="f7372-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="f7372-233">Indikuje, že <xref:System.Windows.Forms.ToolStripMenuItem> má vlastnost <xref:System.Windows.Forms.Control.Enabled> nastavenou na `false`.</span><span class="sxs-lookup"><span data-stu-id="f7372-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="f7372-234">Pokud je vlastnost <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> nastavena na `true`, poskytuje zpětnou vazbu ke stavu zaškrtávacího políčka.</span><span class="sxs-lookup"><span data-stu-id="f7372-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="f7372-235">Pořadí fokusu v režimu kontroly mluveného komentáře je konzistentní s vizuálním pořadím ovládacích prvků v dialogovém okně Stažení ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="f7372-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="f7372-236">**Vylepšení ovládacího prvku DataGridView**</span><span class="sxs-lookup"><span data-stu-id="f7372-236">**DataGridView improvements**</span></span>

<span data-ttu-id="f7372-237">Počínaje .NET Framework 4.7.2, <xref:System.Windows.Forms.DataGridView> ovládací prvek přináší následující vylepšení přístupnosti:</span><span class="sxs-lookup"><span data-stu-id="f7372-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="f7372-238">Řádky lze seřadit pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="f7372-238">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="f7372-239">Uživatel může použít klávesu F3, aby bylo možné řadit podle aktuálního sloupce.</span><span class="sxs-lookup"><span data-stu-id="f7372-239">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="f7372-240">Pokud je <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> nastaveno na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, záhlaví sloupce změní barvu tak, aby označovala aktuální sloupec jako karty uživatelů na aktuálním řádku.</span><span class="sxs-lookup"><span data-stu-id="f7372-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="f7372-241">Vlastnost <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> vrací správný nadřazený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f7372-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="f7372-242">**Vylepšené vizuální pomůcky**</span><span class="sxs-lookup"><span data-stu-id="f7372-242">**Improved visual cues**</span></span>

- <span data-ttu-id="f7372-243">Ovládací prvky <xref:System.Windows.Forms.RadioButton> a <xref:System.Windows.Forms.CheckBox> s prázdnou vlastností <xref:System.Windows.Forms.ButtonBase.Text> zobrazují indikátor fokusu, když získají fokus.</span><span class="sxs-lookup"><span data-stu-id="f7372-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="f7372-244">**Vylepšená podpora mřížky vlastností**</span><span class="sxs-lookup"><span data-stu-id="f7372-244">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="f7372-245">Podřízené prvky ovládacího prvku <xref:System.Windows.Forms.PropertyGrid> nyní vrátí `true` pro vlastnost <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> pouze v případě, že je povolen prvek PropertyGrid.</span><span class="sxs-lookup"><span data-stu-id="f7372-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="f7372-246">Podřízené prvky ovládacího prvku <xref:System.Windows.Forms.PropertyGrid> vrátí `false` pro vlastnost <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> pouze v případě, že uživatel může změnit element PropertyGrid.</span><span class="sxs-lookup"><span data-stu-id="f7372-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="f7372-247">**Vylepšená navigace klávesnicí**</span><span class="sxs-lookup"><span data-stu-id="f7372-247">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="f7372-248">Ovládací prvek <xref:System.Windows.Forms.ToolStripButton> umožňuje fokus, pokud je obsažen v <xref:System.Windows.Forms.ToolStripPanel> s vlastností <xref:System.Windows.Forms.ToolStripPanel.TabStop> nastavenou na `true`</span><span class="sxs-lookup"><span data-stu-id="f7372-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="f7372-249">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="f7372-249">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="f7372-250">**Změny ovládacích prvků CheckBox a RadioButton**</span><span class="sxs-lookup"><span data-stu-id="f7372-250">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="f7372-251">V .NET Framework 4.7.1 a starších verzích jsou ovládací prvky WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> a <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> nekonzistentní a v klasických a Vysoký kontrast motivech jsou nesprávné vizuály fokusu.</span><span class="sxs-lookup"><span data-stu-id="f7372-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="f7372-252">K těmto problémům dochází v případech, kdy ovládací prvky nemají sadu obsahu.</span><span class="sxs-lookup"><span data-stu-id="f7372-252">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="f7372-253">To může zjednodušit přechod mezi motivy a označit vizuál jako fokus.</span><span class="sxs-lookup"><span data-stu-id="f7372-253">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="f7372-254">V .NET Framework 4.7.2 jsou teď tyto vizuály v různých motivech konzistentní a snadněji viditelné v klasických a Vysoký kontrastch motivech.</span><span class="sxs-lookup"><span data-stu-id="f7372-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="f7372-255">**Ovládací prvky WinForms hostované v aplikaci WPF**</span><span class="sxs-lookup"><span data-stu-id="f7372-255">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="f7372-256">Pro ovládací prvek WinForms, který je hostován v aplikaci WPF v .NET Framework 4.7.1 a starších verzích, uživatelé nemohli kartu vymezit vrstvy WinForms, pokud je první nebo poslední ovládací prvek v této vrstvě ovládacím prvkem WPF <xref:System.Windows.Forms.Integration.ElementHost>.</span><span class="sxs-lookup"><span data-stu-id="f7372-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="f7372-257">V .NET Framework 4.7.2 uživatelé teď můžou z vrstvy WinForms vymezit kartu.</span><span class="sxs-lookup"><span data-stu-id="f7372-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="f7372-258">Automatizované aplikace, které spoléhají na fokus bez použití řídicího panelu Vrstvy WinForms, ale nemusí nadále fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="f7372-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="f7372-259">Co je nového v přístupnosti v .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="f7372-259">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="f7372-260">.NET Framework 4.7.1 zahrnuje nové funkce pro usnadnění přístupu v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="f7372-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="f7372-261">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="f7372-261">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="f7372-262">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f7372-262">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="f7372-263">Webové ovládací prvky ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f7372-263">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="f7372-264">SDK Tools .NET</span><span class="sxs-lookup"><span data-stu-id="f7372-264">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="f7372-265">Programovací model Windows Workflow Foundation (WF) Návrhář postupu provádění</span><span class="sxs-lookup"><span data-stu-id="f7372-265">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="f7372-266">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="f7372-266">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="f7372-267">**Vylepšení čtečky obrazovky**</span><span class="sxs-lookup"><span data-stu-id="f7372-267">**Screen reader improvements**</span></span>

<span data-ttu-id="f7372-268">Pokud jsou povolena vylepšení přístupnosti, .NET Framework 4.7.1 zahrnuje následující vylepšení, která ovlivňují čtečky obrazovky:</span><span class="sxs-lookup"><span data-stu-id="f7372-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="f7372-269">V .NET Framework 4,7 a starších verzích byly <xref:System.Windows.Controls.Expander> ovládací prvky ohlášeny čtečkami obrazovky jako tlačítka.</span><span class="sxs-lookup"><span data-stu-id="f7372-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="f7372-270">Počínaje .NET Framework 4.7.1 jsou správně ohlášeny jako rozbalitelné nebo Sbalitelné skupiny.</span><span class="sxs-lookup"><span data-stu-id="f7372-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="f7372-271">V .NET Framework 4,7 a starších verzích byly <xref:System.Windows.Controls.DataGridCell> ovládací prvky oznámeny čtečkami obrazovky jako "vlastní".</span><span class="sxs-lookup"><span data-stu-id="f7372-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="f7372-272">Počínaje .NET Framework 4.7.1 jsou teď správně ohlášené jako buňka datové mřížky (lokalizovaná).</span><span class="sxs-lookup"><span data-stu-id="f7372-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="f7372-273">Počínaje .NET Framework 4.7.1, čtečky obrazovky oznamuje název upravitelného <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="f7372-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="f7372-274">V .NET Framework 4,7 a dřívějších verzích byly <xref:System.Windows.Controls.PasswordBox> ovládací prvky ohlášeny jako "žádná položka v zobrazení" nebo kdyby jinak nedošlo k nesprávnému chování.</span><span class="sxs-lookup"><span data-stu-id="f7372-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="f7372-275">Tento problém je vyřešený od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="f7372-275">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="f7372-276">**Podpora UIAutomation LiveRegion**</span><span class="sxs-lookup"><span data-stu-id="f7372-276">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="f7372-277">Čtečky obrazovky, jako je Narrator, usnadňují uživatelům čtení obsahu uživatelského rozhraní aplikace, obvykle výstupem z textu na řeč, který má fokus.</span><span class="sxs-lookup"><span data-stu-id="f7372-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="f7372-278">Pokud se však prvek uživatelského rozhraní změní a nemá fokus, uživatel nemusí být upozorněn a může si vyvšimnout důležitých informací.</span><span class="sxs-lookup"><span data-stu-id="f7372-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="f7372-279">Při řešení tohoto problému se zaměřují na živé oblasti.</span><span class="sxs-lookup"><span data-stu-id="f7372-279">Live regions aim at solving this problem.</span></span> <span data-ttu-id="f7372-280">Vývojář je může použít k informování čtečky obrazovky nebo jakéhokoliv jiného klienta UIAutomation, že došlo k důležité změně v prvku uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f7372-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="f7372-281">Čtečka obrazovky pak může rozhodnout, jak a kdy se má uživatel informovat o této změně.</span><span class="sxs-lookup"><span data-stu-id="f7372-281">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="f7372-282">V rámci podpory živých oblastí byla do WPF přidána následující rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="f7372-282">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="f7372-283">Pole <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>, která identifikují vlastnost **LiveSetting** a událost **LiveRegionChanged** .</span><span class="sxs-lookup"><span data-stu-id="f7372-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="f7372-284">Lze je nastavit pomocí jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="f7372-284">They can be set by using XAML.</span></span>

- <span data-ttu-id="f7372-285">Připojená vlastnost **Vlastnosti automatizace. LiveSetting** , která informuje čtečku obrazovky o důležitosti změny uživatelského rozhraní pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="f7372-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="f7372-286">Vlastnost <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>, která identifikuje připojenou vlastnost **Vlastnosti automatizace. LiveSetting** .</span><span class="sxs-lookup"><span data-stu-id="f7372-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="f7372-287">Metoda <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>, která může být přepsána tak, aby poskytovala hodnotu **LiveSetting** .</span><span class="sxs-lookup"><span data-stu-id="f7372-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="f7372-288">Metody <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType>, které získají a nastavují hodnotu **LiveSetting** .</span><span class="sxs-lookup"><span data-stu-id="f7372-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="f7372-289">Výčet <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>, který definuje následující možné hodnoty **LiveSetting** :</span><span class="sxs-lookup"><span data-stu-id="f7372-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="f7372-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7372-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f7372-291">Element neodesílá oznámení v případě, že se změnil obsah oblasti v reálném čase.</span><span class="sxs-lookup"><span data-stu-id="f7372-291">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="f7372-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7372-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f7372-293">Element odesílá nepřerušovaná oznámení, pokud se změní obsah živé oblasti.</span><span class="sxs-lookup"><span data-stu-id="f7372-293">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="f7372-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="f7372-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="f7372-295">Element odesílá oznámení o přerušování, pokud se změní obsah živé oblasti.</span><span class="sxs-lookup"><span data-stu-id="f7372-295">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="f7372-296">LiveRegion můžete vytvořit nastavením vlastnosti **Vlastnosti automatizace. LiveSetting** u elementu Interest, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f7372-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="f7372-297">Když se data v živé oblasti změní a potřebujete informovat čtečku obrazovky, explicitně vyvoláte událost, jak je znázorněno v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="f7372-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="f7372-298">**Vysoký kontrast**</span><span class="sxs-lookup"><span data-stu-id="f7372-298">**High contrast**</span></span>

<span data-ttu-id="f7372-299">Počínaje .NET Framework 4.7.1 se v různých ovládacích prvcích WPF provedla vylepšení vysokého kontrastu.</span><span class="sxs-lookup"><span data-stu-id="f7372-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="f7372-300">Jsou nyní viditelné, když je nastaven motiv <xref:System.Windows.SystemParameters.HighContrast%2A>.</span><span class="sxs-lookup"><span data-stu-id="f7372-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="f7372-301">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="f7372-301">These include:</span></span>

- <span data-ttu-id="f7372-302">ovládací prvek <xref:System.Windows.Controls.Expander></span><span class="sxs-lookup"><span data-stu-id="f7372-302"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="f7372-303">Vizuál fokusu pro ovládací prvek <xref:System.Windows.Controls.Expander> je teď viditelný.</span><span class="sxs-lookup"><span data-stu-id="f7372-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="f7372-304">K dispozici jsou také vizuály klávesnice pro ovládací prvky <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>a <xref:System.Windows.Controls.RadioButton>.</span><span class="sxs-lookup"><span data-stu-id="f7372-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="f7372-305">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f7372-305">For example:</span></span>

  <span data-ttu-id="f7372-306">Před:</span><span class="sxs-lookup"><span data-stu-id="f7372-306">Before:</span></span> 

  ![Snímek obrazovky ovládacího prvku rozšíření s fokusem a bez vizuálu fokusu](./media/whats-new-in-accessibility/expander-control-before.png)

  <span data-ttu-id="f7372-308">Konci</span><span class="sxs-lookup"><span data-stu-id="f7372-308">After:</span></span> 

  ![Snímek obrazovky ovládacího prvku rozšíření se fokusem ukazující tečkovou čáru kolem textu ovládacího prvku](./media/whats-new-in-accessibility/expander-control-after.png)

- <span data-ttu-id="f7372-310">ovládací prvky <xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.RadioButton></span><span class="sxs-lookup"><span data-stu-id="f7372-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="f7372-311">Text v ovládacích prvcích <xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.RadioButton> se teď snáze zobrazuje, když je vybraný v motivech s vysokým kontrastem.</span><span class="sxs-lookup"><span data-stu-id="f7372-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="f7372-312">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f7372-312">For example:</span></span>

  <span data-ttu-id="f7372-313">Před:</span><span class="sxs-lookup"><span data-stu-id="f7372-313">Before:</span></span> 

  ![Snímek obrazovky s přepínači a zaškrtávacím tlačítky s nekvalitní viditelností textu u motivů s vysokým kontrastem](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  <span data-ttu-id="f7372-315">Konci</span><span class="sxs-lookup"><span data-stu-id="f7372-315">After:</span></span> 

  ![Snímek obrazovky s přepínači a zaškrtávacím tlačítky s lepší viditelností textu u motivů s vysokým kontrastem](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <span data-ttu-id="f7372-317">ovládací prvek <xref:System.Windows.Controls.ComboBox></span><span class="sxs-lookup"><span data-stu-id="f7372-317"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="f7372-318">Počínaje .NET Framework 4.7.1 je ohraničení zakázaného <xref:System.Windows.Controls.ComboBox>ho ovládacího prvku stejné barvy jako zakázaný text.</span><span class="sxs-lookup"><span data-stu-id="f7372-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="f7372-319">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f7372-319">For example:</span></span>

  <span data-ttu-id="f7372-320">Před:</span><span class="sxs-lookup"><span data-stu-id="f7372-320">Before:</span></span> 

  ![Snímek obrazovky zakázaného pole se seznamem s textem ohraničení a ovládacího prvku v různých barvách](./media/whats-new-in-accessibility/combo-disabled-before.png)

  <span data-ttu-id="f7372-322">Konci</span><span class="sxs-lookup"><span data-stu-id="f7372-322">After:</span></span>   

  ![Snímek obrazovky zakázaného pole se seznamem s ohraničením stejné barvy jako text ovládacího prvku](./media/whats-new-in-accessibility/combo-disabled-after.png)

  <span data-ttu-id="f7372-324">Kromě toho zakázaná a zaměřená tlačítka používají správnou barvu motivu.</span><span class="sxs-lookup"><span data-stu-id="f7372-324">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="f7372-325">Před:</span><span class="sxs-lookup"><span data-stu-id="f7372-325">Before:</span></span>

  ![Snímek obrazovky černého tlačítka se šedým textem, který se zaměřuje na mne](./media/whats-new-in-accessibility/button-theme-colors-before.png) 

  <span data-ttu-id="f7372-327">Konci</span><span class="sxs-lookup"><span data-stu-id="f7372-327">After:</span></span> 

  ![Snímek obrazovky s modrým tlačítkem s černým textem, který se zaměřuje na mne](./media/whats-new-in-accessibility/button-theme-colors-after.png) 

  <span data-ttu-id="f7372-329">Nakonec, v .NET Framework 4,7 a starších verzích, nastavení stylu <xref:System.Windows.Controls.ComboBox> ovládacího prvku na `Toolbar.ComboBoxStyleKey` způsobilo, že šipka rozevíracího seznamu nebude viditelná.</span><span class="sxs-lookup"><span data-stu-id="f7372-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="f7372-330">Tento problém je vyřešený od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="f7372-330">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="f7372-331">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f7372-331">For example:</span></span>

  <span data-ttu-id="f7372-332">Před:</span><span class="sxs-lookup"><span data-stu-id="f7372-332">Before:</span></span> 

  ![Snímek obrazovky ovládacího prvku ComboBox se skrytou šipkou rozevíracího seznamu](./media/whats-new-in-accessibility/combo-box-style-key-before.png) 

  <span data-ttu-id="f7372-334">Konci</span><span class="sxs-lookup"><span data-stu-id="f7372-334">After:</span></span> 

  ![Snímek obrazovky ovládacího prvku polem, který zobrazuje šipku rozevíracího seznamu.](./media/whats-new-in-accessibility/combo-box-style-key-after.png) 

- <span data-ttu-id="f7372-336">ovládací prvek <xref:System.Windows.Controls.DataGrid></span><span class="sxs-lookup"><span data-stu-id="f7372-336"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="f7372-337">Počínaje .NET Framework 4.7.1 se šipka indikátoru řazení v <xref:System.Windows.Controls.DataGrid> ovládacích prvcích nyní používá pro správné barvy motivů.</span><span class="sxs-lookup"><span data-stu-id="f7372-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="f7372-338">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f7372-338">For example:</span></span>

  <span data-ttu-id="f7372-339">Před:</span><span class="sxs-lookup"><span data-stu-id="f7372-339">Before:</span></span> 

  ![Snímek obrazovky se šipkou indikátoru řazení před vylepšeními](./media/whats-new-in-accessibility/sort-indicator-before.png) 

  <span data-ttu-id="f7372-341">Konci</span><span class="sxs-lookup"><span data-stu-id="f7372-341">After:</span></span>   

  ![Snímek obrazovky se šipkou indikátoru řazení po vylepšeních](./media/whats-new-in-accessibility/sort-indicator-after.png) 

  <span data-ttu-id="f7372-343">Kromě toho se v .NET Framework 4,7 a dřívějších verzích změnil výchozí styl propojení na nesprávnou barvu při stisknutí myši v režimech s vysokým kontrastem.</span><span class="sxs-lookup"><span data-stu-id="f7372-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="f7372-344">Tento problém se vyřeší od .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="f7372-344">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="f7372-345">Podobně <xref:System.Windows.Controls.DataGrid> sloupce Zaškrtávací políčko používá očekávané barvy zpětné vazby pro fokus klávesnice počínaje .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="f7372-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="f7372-346">Před:</span><span class="sxs-lookup"><span data-stu-id="f7372-346">Before:</span></span> 

  ![Snímek obrazovky s odkazem na něj klikněte](./media/whats-new-in-accessibility/default-link-style-before.png) 

  <span data-ttu-id="f7372-349">Konci</span><span class="sxs-lookup"><span data-stu-id="f7372-349">After:</span></span>    

  ![Snímek obrazovky s odkazem na něj klikněte](./media/whats-new-in-accessibility/default-link-style-after.png) 

<span data-ttu-id="f7372-352">Další informace o vylepšení usnadnění přístupu WPF v .NET Framework 4.7.1 najdete v tématu [vylepšení usnadnění v WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="f7372-352">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="f7372-353">Vylepšení model Windows Forms dostupnosti</span><span class="sxs-lookup"><span data-stu-id="f7372-353">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="f7372-354">V .NET Framework 4.7.1, model Windows Forms (WinForms), zahrnuje změny přístupnosti v následujících oblastech.</span><span class="sxs-lookup"><span data-stu-id="f7372-354">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="f7372-355">**Vylepšené zobrazení v režimu Vysoký kontrast**</span><span class="sxs-lookup"><span data-stu-id="f7372-355">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="f7372-356">Počínaje .NET Framework 4.7.1 různé ovládací prvky WinForms nabízejí Vylepšené vykreslování v režimech HighContrast, které jsou k dispozici v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="f7372-356">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="f7372-357">Windows 10 změnil hodnoty pro některé systémové barvy s vysokým kontrastem a model Windows Forms vychází z rozhraní Win32 pro Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f7372-357">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="f7372-358">Pro dosažení co nejlepších výsledků spusťte aplikaci v nejnovější verzi Windows a přihlaste se k nejnovějším změnám operačního systému přidáním souboru App. manifest do testovací aplikace a odkomentujte podporovanou řádku operačního systému Windows 10 tak, aby vypadala takto:</span><span class="sxs-lookup"><span data-stu-id="f7372-358">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

<span data-ttu-id="f7372-359">Mezi tyto změny vysokého kontrastu patří:</span><span class="sxs-lookup"><span data-stu-id="f7372-359">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="f7372-360">Zaškrtnutí v <xref:System.Windows.Forms.MenuStrip> položky se snáze zobrazují.</span><span class="sxs-lookup"><span data-stu-id="f7372-360">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="f7372-361">Je-li toto políčko zaškrtnuto, je snazší zobrazit zakázané položky <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="f7372-361">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="f7372-362">Text ve vybraném <xref:System.Windows.Forms.Button> ovládacím prvku se liší od barvy výběru.</span><span class="sxs-lookup"><span data-stu-id="f7372-362">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="f7372-363">Nepovolený text je snazší číst.</span><span class="sxs-lookup"><span data-stu-id="f7372-363">Disabled text is easier to read.</span></span> <span data-ttu-id="f7372-364">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f7372-364">For example:</span></span>

  <span data-ttu-id="f7372-365">Před:</span><span class="sxs-lookup"><span data-stu-id="f7372-365">Before:</span></span>

  ![Snímek obrazovky aplikace, která používá jiné ovládací prvky běžící v režimu s vysokým kontrastem před vylepšeními přístupnosti.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png) 

  <span data-ttu-id="f7372-367">Konci</span><span class="sxs-lookup"><span data-stu-id="f7372-367">After:</span></span>

  ![Snímek obrazovky aplikace, která používá jiné ovládací prvky běžící v režimu s vysokým kontrastem po vylepšeních přístupnosti.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png) 

- <span data-ttu-id="f7372-369">Vylepšení vysokého kontrastu v dialogovém okně výjimky vlákna.</span><span class="sxs-lookup"><span data-stu-id="f7372-369">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="f7372-370">**Vylepšená podpora Narrator**</span><span class="sxs-lookup"><span data-stu-id="f7372-370">**Improved Narrator support**</span></span>

<span data-ttu-id="f7372-371">Model Windows Forms v .NET Framework 4.7.1 obsahuje následující vylepšení přístupnosti pro program Narrator:</span><span class="sxs-lookup"><span data-stu-id="f7372-371">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="f7372-372">K ovládacímu prvku <xref:System.Windows.Forms.MonthCalendar> může mít přistup Nástroj Narrator a také jiné nástroje pro automatizaci uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f7372-372">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="f7372-373">Ovládací prvek <xref:System.Windows.Forms.CheckedListBox> upozorní program Narrator, když se změní stav kontroly položky, takže uživatel bude informován o tom, že změnil hodnotu položky seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7372-373">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="f7372-374">Ovládací prvek <xref:System.Windows.Forms.DataGridViewCell> oznamuje do programu Narrator správný stav jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="f7372-374">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="f7372-375">Program Narrator teď může číst zakázaný text <xref:System.Windows.Forms.ToolStripMenuItem>, zatímco dřív by přeskočil zakázané položky nabídky.</span><span class="sxs-lookup"><span data-stu-id="f7372-375">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="f7372-376">**Vylepšená podpora pro vzory usnadnění UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="f7372-376">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="f7372-377">Od .NET Framework 4.7.1 můžou vývojáři nástrojů pro usnadnění přístupu využít běžné vzory a vlastnosti přístupnosti rozhraní API pro několik ovládacích prvků WinForms.</span><span class="sxs-lookup"><span data-stu-id="f7372-377">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="f7372-378">Mezi tato vylepšení přístupnosti patří:</span><span class="sxs-lookup"><span data-stu-id="f7372-378">These accessibility improvements include:</span></span>

- <span data-ttu-id="f7372-379"><xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ToolStripSplitButton> nyní podporují [model rozbalení a sbalení](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="f7372-379">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="f7372-380"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> teď podporuje [vzor přepínacího](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)tlačítka.</span><span class="sxs-lookup"><span data-stu-id="f7372-380">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="f7372-381">Ovládací prvek <xref:System.Windows.Forms.ToolStripItem> podporuje vlastnost <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> a vzorek pro [rozbalení a sbalení](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="f7372-381">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="f7372-382">Ovládací prvky <xref:System.Windows.Forms.NumericUpDown> a <xref:System.Windows.Forms.DomainUpDown> podporují vlastnost <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name>.</span><span class="sxs-lookup"><span data-stu-id="f7372-382">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="f7372-383">**Vylepšené prostředí prohlížeče vlastností**</span><span class="sxs-lookup"><span data-stu-id="f7372-383">**Improved property browser experience**</span></span>

<span data-ttu-id="f7372-384">Počínaje .NET Framework 4.7.1 model Windows Forms zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="f7372-384">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="f7372-385">Lepší navigace pomocí klávesnice v různých oknech pro výběr rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7372-385">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="f7372-386">Snížení zbytečných zarážek tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="f7372-386">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="f7372-387">Lepší vytváření sestav typů ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="f7372-387">Better reporting of control types.</span></span>
- <span data-ttu-id="f7372-388">Vylepšené chování Předčítání.</span><span class="sxs-lookup"><span data-stu-id="f7372-388">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="f7372-389">Webové ovládací prvky ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f7372-389">ASP.NET web controls</span></span>

<span data-ttu-id="f7372-390">Počínaje .NET Framework 4.7.1 a sadou Visual Studio 2017 verze 15,3 ASP.NET vylepšuje, jak ASP.NET webové ovládací prvky fungují s technologiemi usnadnění v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f7372-390">Starting with .NET Framework 4.7.1 and Visual Studio 2017 version 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="f7372-391">Změny zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="f7372-391">Changes include the following:</span></span>

- <span data-ttu-id="f7372-392">Změny pro implementaci chybějících vzorů přístupnosti uživatelského rozhraní v ovládacích prvcích, jako je dialogové okno **Přidat pole** v průvodci **zobrazení podrobností** nebo dialogové okno **Konfigurovat ListView** průvodce **ListView** .</span><span class="sxs-lookup"><span data-stu-id="f7372-392">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="f7372-393">Změny pro zlepšení zobrazení v režimu Vysoký kontrast, jako je například **Editor polí datového pageru**.</span><span class="sxs-lookup"><span data-stu-id="f7372-393">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="f7372-394">Změny pro zlepšení prostředí navigace klávesnicí pro ovládací prvky, jako je dialogové okno **pole** v průvodci **úpravou polí stránkování** ovládacího prvku DataPager, dialogové **okno Konfigurovat ObjectContext** nebo dialogové okno **Konfigurovat výběr dat** v průvodci **konfigurací zdroje dat** .</span><span class="sxs-lookup"><span data-stu-id="f7372-394">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="f7372-395">SDK Tools .NET</span><span class="sxs-lookup"><span data-stu-id="f7372-395">.NET SDK Tools</span></span>

<span data-ttu-id="f7372-396">[Nástroj Configuration Editor (SvcConfigEditor. exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) a [nástroj Service Trace Viewer (SvcTraceViewer. exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) byly vylepšeny opravou různých problémů s přístupností.</span><span class="sxs-lookup"><span data-stu-id="f7372-396">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="f7372-397">Většina těchto došlo k malým problémům, jako je název, který není definován, nebo některé vzorce automatizace uživatelského rozhraní nejsou správně implementovány.</span><span class="sxs-lookup"><span data-stu-id="f7372-397">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="f7372-398">I když mnoho uživatelů nebude vědět o těchto nesprávných hodnotách, zákazníci, kteří používají asistenční technologie, jako jsou čtečky obrazovky, budou tyto nástroje sady SDK k dispozici podrobněji.</span><span class="sxs-lookup"><span data-stu-id="f7372-398">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="f7372-399">Tato vylepšení mění některá předchozí chování, jako je například pořadí fokusu klávesnice.</span><span class="sxs-lookup"><span data-stu-id="f7372-399">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="f7372-400">Programovací model Windows Workflow Foundation (WF) Návrhář postupu provádění</span><span class="sxs-lookup"><span data-stu-id="f7372-400">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="f7372-401">Změny přístupnosti v Návrhář postupu provádění zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="f7372-401">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="f7372-402">Pořadí karet se změní na zleva doprava a shora dolů v některých ovládacích prvcích:</span><span class="sxs-lookup"><span data-stu-id="f7372-402">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="f7372-403">Okno Inicializace korelace pro nastavení dat korelace pro aktivitu <xref:System.ServiceModel.Activities.InitializeCorrelation>.</span><span class="sxs-lookup"><span data-stu-id="f7372-403">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="f7372-404">Okno Definice obsahu pro aktivity <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>a <xref:System.ServiceModel.Activities.ReceiveReply>.</span><span class="sxs-lookup"><span data-stu-id="f7372-404">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="f7372-405">Další funkce jsou k dispozici prostřednictvím klávesnice:</span><span class="sxs-lookup"><span data-stu-id="f7372-405">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="f7372-406">Při úpravách vlastností aktivity mohou být skupiny vlastností sbaleny klávesnicí při prvním zaměření.</span><span class="sxs-lookup"><span data-stu-id="f7372-406">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="f7372-407">Ikony upozornění jsou přístupné z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="f7372-407">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="f7372-408">Tlačítko **Další vlastnosti** v okně **vlastnosti** je přístupné z klávesnice.</span><span class="sxs-lookup"><span data-stu-id="f7372-408">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="f7372-409">Uživatelé klávesnice mají přístup k položkám záhlaví v podoknech **argumenty** a **proměnné** Návrhář postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="f7372-409">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="f7372-410">Vylepšená viditelnost položek s fokusem, například když:</span><span class="sxs-lookup"><span data-stu-id="f7372-410">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="f7372-411">Přidávání řádků do datových mříží používaných návrháři Návrhář postupu provádění a aktivit.</span><span class="sxs-lookup"><span data-stu-id="f7372-411">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="f7372-412">Procházení polí v aktivitách <xref:System.ServiceModel.Activities.ReceiveReply> a <xref:System.ServiceModel.Activities.SendReply></span><span class="sxs-lookup"><span data-stu-id="f7372-412">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="f7372-413">Nastavení výchozích hodnot pro proměnné nebo argumenty</span><span class="sxs-lookup"><span data-stu-id="f7372-413">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="f7372-414">Čtečky obrazovky teď můžou správně rozpoznat:</span><span class="sxs-lookup"><span data-stu-id="f7372-414">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="f7372-415">Zarážky nastavené v Návrháři postupu.</span><span class="sxs-lookup"><span data-stu-id="f7372-415">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="f7372-416">Aktivity <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>a <xref:System.ServiceModel.Activities.CorrelationScope>.</span><span class="sxs-lookup"><span data-stu-id="f7372-416">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="f7372-417">Obsah aktivity <xref:System.ServiceModel.Activities.Receive></span><span class="sxs-lookup"><span data-stu-id="f7372-417">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="f7372-418">Cílový typ aktivity <xref:System.Activities.Statements.InvokeMethod>.</span><span class="sxs-lookup"><span data-stu-id="f7372-418">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="f7372-419">Pole se seznamem výjimek a oddíl finally v aktivitě <xref:System.Activities.Statements.TryCatch>.</span><span class="sxs-lookup"><span data-stu-id="f7372-419">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="f7372-420">Pole se seznamem typ zprávy, příčka v okně Přidat Inicializátory korelace, okno Definice obsahu a okno definice vlastnosti CorrelatesOn v aktivitách zasílání zpráv (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>a <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="f7372-420">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="f7372-421">Cíle přechodů a přechodů stavového stroje.</span><span class="sxs-lookup"><span data-stu-id="f7372-421">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="f7372-422">Poznámky a konektory <xref:System.Activities.Statements.FlowDecision> aktivity.</span><span class="sxs-lookup"><span data-stu-id="f7372-422">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="f7372-423">Místní nabídky pro aktivity v kontextu (klikněte pravým tlačítkem myši).</span><span class="sxs-lookup"><span data-stu-id="f7372-423">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="f7372-424">Editor hodnot vlastností, tlačítko Vymazat hledání, kategorie podle abecedy a abecední řazení a dialogové okno Editor výrazů v mřížce vlastností.</span><span class="sxs-lookup"><span data-stu-id="f7372-424">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="f7372-425">Procento přiblížení v Návrhář postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="f7372-425">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="f7372-426">Oddělovač v aktivitách <xref:System.Activities.Statements.Parallel> a <xref:System.Activities.Statements.Pick>.</span><span class="sxs-lookup"><span data-stu-id="f7372-426">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="f7372-427">Aktivita <xref:System.Activities.Statements.InvokeDelegate>.</span><span class="sxs-lookup"><span data-stu-id="f7372-427">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="f7372-428">Okno vybrat typy pro aktivity slovníku (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`atd.).</span><span class="sxs-lookup"><span data-stu-id="f7372-428">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="f7372-429">Okno Procházet a vybrat typ .NET.</span><span class="sxs-lookup"><span data-stu-id="f7372-429">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="f7372-430">Popis cesty v Návrhář postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="f7372-430">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="f7372-431">Uživatelům, kteří si zvolí Vysoký kontrast Themes, se zobrazí mnoho vylepšení viditelnosti Návrhář postupu provádění a jeho ovládacích prvků, jako je lepší poměr kontrastu mezi prvky a další pole výběru, která se používají pro prvky fokusu.</span><span class="sxs-lookup"><span data-stu-id="f7372-431">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="f7372-432">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7372-432">See also</span></span>

- [<span data-ttu-id="f7372-433">Co je nového v .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f7372-433">What's new in the .NET Framework</span></span>](index.md)
