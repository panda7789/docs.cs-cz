---
title: "Co je nového v usnadnění v rozhraní .NET Framework"
ms.custom: updateeachrelease
ms.date: 10/13/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6a6759ae285f2dd101bddf71ea8e5ca792e87df
ms.sourcegitcommit: 957c696f25e39f923a827fc3ad5e8ab72768838c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2018
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="9738b-102">Co je nového v usnadnění v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9738b-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="9738b-103">Rozhraní .NET Framework se zaměřuje na provedení další accessibile pro vaše uživatele aplikace.</span><span class="sxs-lookup"><span data-stu-id="9738b-103">The .NET Framework aims at making applications more accessibile for your users.</span></span> <span data-ttu-id="9738b-104">Funkce usnadnění povolit aplikace a poskytuje příslušné prostředí pro uživatele technologie usnadnění.</span><span class="sxs-lookup"><span data-stu-id="9738b-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="9738b-105">Od verze rozhraní .NET Framework 4.7.1, rozhraní .NET Framework obsahuje velké množství vylepšení přístupnosti, které umožňují vývojářům vytvářet aplikace přístupná.</span><span class="sxs-lookup"><span data-stu-id="9738b-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

<span data-ttu-id="9738b-106">Nové funkce pro usnadnění přístupu jsou povolené ve výchozím nastavení pro aplikace, které cílí na rozhraní .NET Framework 4.7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="9738b-106">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="9738b-107">Kromě toho aplikace, které cílení na dřívější verzi rozhraní .NET Framework, ale běží na rozhraní .NET Framework 4.7.1 a později se můžete rozhodnout ze starší verze usnadnění chování (a tím vyjádřit výslovný souhlas k vylepšení přístupnosti v rozhraní .NET Framework 4.7.1) podle Přidání následující přepínač tak, aby [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element v [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) oddílu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="9738b-107">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby opt in to the accessibility improvements in the .NET Framework 4.7.1) by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="9738b-108">Podobně můžete zakázat funkce usnadnění přidáním následující přepínač tak, aby aplikace, které cílové verze rozhraní .NET Framework, počínaje 4.7.1 [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element v [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) oddílu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="9738b-108">Similarly, applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding the following switch to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="9738b-109">Co je nového v usnadnění v rozhraní .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="9738b-109">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="9738b-110">Rozhraní .NET Framework 4.7.1 zahrnuje nové funkce usnadnění v těchto oblastech:</span><span class="sxs-lookup"><span data-stu-id="9738b-110">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="9738b-111">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="9738b-111">Windows Presentation Foundation (WPF)</span></span>](#windows-presentation-foundation-wpf)

- [<span data-ttu-id="9738b-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9738b-112">Windows Forms</span></span>](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="9738b-113">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="9738b-113">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="9738b-114">**Vylepšení čtečky obrazovky**</span><span class="sxs-lookup"><span data-stu-id="9738b-114">**Screen reader improvements**</span></span>

<span data-ttu-id="9738b-115">Pokud jsou povolené vylepšení přístupnosti, rozhraní .NET Framework 4.7.1 obsahuje následující vylepšení, které ovlivňují čtečky obrazovky:</span><span class="sxs-lookup"><span data-stu-id="9738b-115">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="9738b-116">V rozhraní .NET Framework 4.7 a dřívějších verzích <xref:System.Windows.Controls.Expander> ovládací prvky byly oznamují čtečky obrazovky jako tlačítka.</span><span class="sxs-lookup"><span data-stu-id="9738b-116">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="9738b-117">Od verze rozhraní .NET Framework 4.7.1, že jsou správně oznámila jako rozšíření, sbalitelné skupiny.</span><span class="sxs-lookup"><span data-stu-id="9738b-117">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="9738b-118">V rozhraní .NET Framework 4.7 a dřívějších verzích <xref:System.Windows.Controls.DataGridCell> ovládací prvky byly oznamují čtečky obrazovky jako "vlastní".</span><span class="sxs-lookup"><span data-stu-id="9738b-118">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="9738b-119">Od verze rozhraní .NET Framework 4.7.1, se nyní správně odesílány zpět jako buňky v mřížce dat (lokalizované).</span><span class="sxs-lookup"><span data-stu-id="9738b-119">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="9738b-120">Od verze rozhraní .NET Framework 4.7.1, čtečky obrazovky oznamujeme název upravitelné <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="9738b-120">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="9738b-121">V rozhraní .NET Framework 4.7 a dřívějších verzích <xref:System.Windows.Controls.PasswordBox> ovládací prvky byly oznámí jako "žádná položka v zobrazení", nebo byl jinak nesprávné chování.</span><span class="sxs-lookup"><span data-stu-id="9738b-121">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="9738b-122">Tento problém vyřešen, od verze rozhraní .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="9738b-122">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>     

<span data-ttu-id="9738b-123">**Vlastnosti UIAutomation LiveRegion podpory**</span><span class="sxs-lookup"><span data-stu-id="9738b-123">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="9738b-124">Čtečky obrazovky například Předčítání pomoci ostatním uživatelům číst obsah uživatelského rozhraní aplikace, obvykle je výstup uživatelského rozhraní obsah, který je aktivní.</span><span class="sxs-lookup"><span data-stu-id="9738b-124">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="9738b-125">Ale pokud prvku uživatelského rozhraní se změní a nemá fokus, uživatel nemusí být upozorněni a může dojít důležité informace.</span><span class="sxs-lookup"><span data-stu-id="9738b-125">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="9738b-126">Za provozu oblasti cílem řešení tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="9738b-126">Live regions aim at solving this problem.</span></span> <span data-ttu-id="9738b-127">Vývojář může je použít k informování čtečky obrazovky nebo jakéhokoli klienta vlastnosti UIAutomation, který byl proveden důležité změně prvku uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9738b-127">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="9738b-128">Čtečky obrazovky můžete pak rozhodnout, jak a kdy k informování uživatelů této změny.</span><span class="sxs-lookup"><span data-stu-id="9738b-128">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="9738b-129">Pro podporu za provozu oblasti, byly přidány následující rozhraní API k použití WPF:</span><span class="sxs-lookup"><span data-stu-id="9738b-129">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="9738b-130"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> pole, které identifikovat **LiveSetting** vlastnost a **LiveRegionChanged** událostí.</span><span class="sxs-lookup"><span data-stu-id="9738b-130">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="9738b-131">Můžete být nastavit s použitím jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="9738b-131">They can be set by using XAML.</span></span>

- <span data-ttu-id="9738b-132">**AutomationProperties.LiveSetting** přidružená vlastnost, která informuje o čtečky obrazovky významné změny uživatelského rozhraní pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="9738b-132">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="9738b-133"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Vlastnost, která ji identifikuje **AutomationProperties.LiveSetting** přidružená vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9738b-133">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="9738b-134"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Metodu, která může být potlačena za účelem poskytování **LiveSetting** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9738b-134">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="9738b-135"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> metody, které získání a nastavení **LiveSetting** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9738b-135">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="9738b-136"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Výčtu, který definuje následující možné **LiveSetting** hodnoty:</span><span class="sxs-lookup"><span data-stu-id="9738b-136">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="9738b-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9738b-137"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9738b-138">Element neodešle oznámení, pokud došlo ke změně obsahu oblasti za provozu.</span><span class="sxs-lookup"><span data-stu-id="9738b-138">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="9738b-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9738b-139"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9738b-140">Element odešle-interruptive oznámení, pokud došlo ke změně obsahu oblasti za provozu.</span><span class="sxs-lookup"><span data-stu-id="9738b-140">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="9738b-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9738b-141"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9738b-142">Element odešle interruptive oznámení, pokud došlo ke změně obsahu oblasti za provozu.</span><span class="sxs-lookup"><span data-stu-id="9738b-142">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="9738b-143">Můžete vytvořit LiveRegion nastavením **AutomationProperties.LiveSetting** vlastnost v elementu zajímat, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9738b-143">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="9738b-144">Při změně dat v oblasti za provozu a je nutné informovat čtečky obrazovky, explicitně zvýšíte událost, jak znázorňuje následující ukázka.</span><span class="sxs-lookup"><span data-stu-id="9738b-144">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="9738b-145">**Vysoký kontrast**</span><span class="sxs-lookup"><span data-stu-id="9738b-145">**High contrast**</span></span>

<span data-ttu-id="9738b-146">Od verze rozhraní .NET Framework 4.7.1, vysoký kontrast vylepšily do různých ovládacích prvků WPF.</span><span class="sxs-lookup"><span data-stu-id="9738b-146">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="9738b-147">Jsou nyní viditelné při <xref:System.Windows.SystemParameters.HighContrast%2A> motiv nastavena.</span><span class="sxs-lookup"><span data-stu-id="9738b-147">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="9738b-148">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="9738b-148">These include:</span></span>

- <span data-ttu-id="9738b-149"><xref:System.Windows.Controls.Expander>ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="9738b-149"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="9738b-150">Visual pro zaměřuje <xref:System.Windows.Controls.Expander> ovládací prvek je nyní viditelné.</span><span class="sxs-lookup"><span data-stu-id="9738b-150">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="9738b-151">Vizuály klávesnice pro <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, a <xref:System.Windows.Controls.RadioButton> ovládací prvky jsou také viditelné.</span><span class="sxs-lookup"><span data-stu-id="9738b-151">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="9738b-152">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9738b-152">For example:</span></span>

    <span data-ttu-id="9738b-153">Před:</span><span class="sxs-lookup"><span data-stu-id="9738b-153">Before:</span></span> 
    
    ![Ovládací prvek Expander s fokusem před vylepšení přístupnosti](media/expander-before.png)

    <span data-ttu-id="9738b-155">Po:</span><span class="sxs-lookup"><span data-stu-id="9738b-155">After:</span></span> 

    ![Ovládací prvek Expander fokus po vylepšení přístupnosti](media/expander-after.png)

- <span data-ttu-id="9738b-157"><xref:System.Windows.Controls.CheckBox>a <xref:System.Windows.Controls.RadioButton> ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="9738b-157"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="9738b-158">Text v <xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.RadioButton> ovládací prvky je nyní snazší uvidí, když je vybraný v vysoký kontrast motivů.</span><span class="sxs-lookup"><span data-stu-id="9738b-158">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="9738b-159">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9738b-159">For example:</span></span>

    <span data-ttu-id="9738b-160">Před:</span><span class="sxs-lookup"><span data-stu-id="9738b-160">Before:</span></span> 

    ![Vysoký kontrast přepínač s fokusem před vylepšení přístupnosti](media/radio-button-before.png)
    
    <span data-ttu-id="9738b-162">Po:</span><span class="sxs-lookup"><span data-stu-id="9738b-162">After:</span></span> 

    ![Vysoký kontrast přepínač s fokusem po vylepšení přístupnosti](media/radio-button-after.png)

- <span data-ttu-id="9738b-164"><xref:System.Windows.Controls.ComboBox>ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="9738b-164"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="9738b-165">Od verze rozhraní .NET Framework 4.7.1, ohraničení zakázáno <xref:System.Windows.Controls.ComboBox> ovládací prvek se stejnou barvu jako zakázaný text.</span><span class="sxs-lookup"><span data-stu-id="9738b-165">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="9738b-166">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9738b-166">For example:</span></span>
    
    <span data-ttu-id="9738b-167">Před:</span><span class="sxs-lookup"><span data-stu-id="9738b-167">Before:</span></span> 

     ![ComboBox – zakázáno ohraničení a text před vylepšení přístupnosti](media/combo-disabled-before.png)

    <span data-ttu-id="9738b-169">Po:</span><span class="sxs-lookup"><span data-stu-id="9738b-169">After:</span></span>   

     ![ComboBox – po vylepšení přístupnosti zakázán ohraničení a text.](media/combo-disabled-after.png)

    <span data-ttu-id="9738b-171">Kromě toho zakázané a zaměřují se tlačítka použít barvu motivu správné.</span><span class="sxs-lookup"><span data-stu-id="9738b-171">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="9738b-172">Před:</span><span class="sxs-lookup"><span data-stu-id="9738b-172">Before:</span></span>

    ![Tlačítko barev motivů před vylepšení přístupnosti](media/button-themes-before.png) 
    
    <span data-ttu-id="9738b-174">Po:</span><span class="sxs-lookup"><span data-stu-id="9738b-174">After:</span></span> 

    ![Tlačítko barev motivů po vylepšení přístupnosti](media/button-themes-after.png) 

    <span data-ttu-id="9738b-176">Nakonec v rozhraní .NET Framework 4.7 a dřívějších verzích, nastavení <xref:System.Windows.Controls.ComboBox> styl ovládacího prvku, který se `Toolbar.ComboBoxStyleKey` způsobila na šipku rozevíracího seznamu byla neviditelná.</span><span class="sxs-lookup"><span data-stu-id="9738b-176">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="9738b-177">Tento problém vyřešen, od verze rozhraní .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="9738b-177">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="9738b-178">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9738b-178">For example:</span></span>

    <span data-ttu-id="9738b-179">Před:</span><span class="sxs-lookup"><span data-stu-id="9738b-179">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey před vylepšení přístupnosti](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="9738b-181">Po:</span><span class="sxs-lookup"><span data-stu-id="9738b-181">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey po vylepšení přístupnosti](media/comboboxstylekey-after.png) 

- <span data-ttu-id="9738b-183"><xref:System.Windows.Controls.DataGrid>ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="9738b-183"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="9738b-184">Od verze rozhraní .NET Framework 4.7.1, šipku řazení indikátoru v <xref:System.Windows.Controls.DataGrid> řídí teď používá opravte barev motivů.</span><span class="sxs-lookup"><span data-stu-id="9738b-184">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="9738b-185">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9738b-185">For example:</span></span>

    <span data-ttu-id="9738b-186">Před:</span><span class="sxs-lookup"><span data-stu-id="9738b-186">Before:</span></span> 

    ![Řazení šipku indikátoru před vylepšení přístupnosti](media/sort-indicator-before.png) 
    
    <span data-ttu-id="9738b-188">Po:</span><span class="sxs-lookup"><span data-stu-id="9738b-188">After:</span></span>   
 
    ![Řazení indikátor šipku po vylepšení přístupnosti](media/sort-indicator-after.png) 
    
    <span data-ttu-id="9738b-190">Kromě toho v rozhraní .NET Framework 4.7 a dřívějších verzí, výchozí styl odkaz změnit na nesprávné barva na myši v režimu vysokého kontrastu.</span><span class="sxs-lookup"><span data-stu-id="9738b-190">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="9738b-191">Tento problém vyřešen od verze rozhraní .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="9738b-191">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="9738b-192">Podobně <xref:System.Windows.Controls.DataGrid> políčko sloupce používá pro zpětnou vazbu fokus klávesnice od verze rozhraní .NET Framework 4.7.1 očekávané barvy.</span><span class="sxs-lookup"><span data-stu-id="9738b-192">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="9738b-193">Před:</span><span class="sxs-lookup"><span data-stu-id="9738b-193">Before:</span></span> 

    ![DataGrid – výchozí odkaz styl před vylepšení přístupnosti](media/default-link-style-before.png) 
 
    <span data-ttu-id="9738b-195">Po:</span><span class="sxs-lookup"><span data-stu-id="9738b-195">After:</span></span>    
  
    ![DataGrid – výchozí odkaz styl po vylepšení přístupnosti](media/default-link-style-after.png)  

<span data-ttu-id="9738b-197">Další informace o vylepšení přístupnosti grafického subsystému WPF v rozhraní .NET Framework 4.7.1 najdete v tématu [vylepšení přístupnosti v grafickém subsystému WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="9738b-197">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="9738b-198">Vylepšení přístupnosti Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9738b-198">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="9738b-199">Windows Forms (WinForms) v rozhraní .NET Framework 4.7.1 zahrnuje změny usnadnění v následujících oblastech.</span><span class="sxs-lookup"><span data-stu-id="9738b-199">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="9738b-200">**Vylepšené zobrazení v režimu vysokého kontrastu**</span><span class="sxs-lookup"><span data-stu-id="9738b-200">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="9738b-201">Od verze rozhraní .NET Framework 4.7.1, nabízejí různé ovládací prvky WinForms vylepšené vykreslování v funkce Vysoký kontrast režimech k dispozici v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="9738b-201">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="9738b-202">Windows 10 došlo ke změně hodnoty pro některé barvy systému vysoký kontrast a Windows Forms je založena na rozhraní Windows 10 Win32.</span><span class="sxs-lookup"><span data-stu-id="9738b-202">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="9738b-203">Pro dosažení co nejlepších výsledků spusťte na nejnovější verzi systému Windows a vyjádřit výslovný souhlas na nejnovější změny operačního systému tak, že přidáte soubor app.manifest v testovací aplikaci a zrušení komentář Windows 10 nepodporuje řádku operačního systému, aby vypadal jako následující:</span><span class="sxs-lookup"><span data-stu-id="9738b-203">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="9738b-204">Některé příklady vysoký kontrast změny patří:</span><span class="sxs-lookup"><span data-stu-id="9738b-204">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="9738b-205">Značky zaškrtnutí v <xref:System.Windows.Forms.MenuStrip> položky se snadněji zobrazení.</span><span class="sxs-lookup"><span data-stu-id="9738b-205">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="9738b-206">Pokud vybraná, zakázané <xref:System.Windows.Forms.MenuStrip> položky se snadněji zobrazení.</span><span class="sxs-lookup"><span data-stu-id="9738b-206">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="9738b-207">Text ve vybrané <xref:System.Windows.Forms.Button> řízení totéž co barva výběru.</span><span class="sxs-lookup"><span data-stu-id="9738b-207">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="9738b-208">Zakázaný text je snadnější čtení.</span><span class="sxs-lookup"><span data-stu-id="9738b-208">Disabled text is easier to read.</span></span> <span data-ttu-id="9738b-209">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9738b-209">For example:</span></span>

    <span data-ttu-id="9738b-210">Před:</span><span class="sxs-lookup"><span data-stu-id="9738b-210">Before:</span></span>

    ![Zakázaný text před vylepšení přístupnosti](media/wf-disabled-before.png) 

    <span data-ttu-id="9738b-212">Po:</span><span class="sxs-lookup"><span data-stu-id="9738b-212">After:</span></span>

    ![Zakázaný text po vylepšení přístupnosti](media/wf-disabled-after.png) 

- <span data-ttu-id="9738b-214">Vysoký kontrast vylepšení v dialogovém okně výjimka přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="9738b-214">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="9738b-215">**Vylepšená podpora Předčítání**</span><span class="sxs-lookup"><span data-stu-id="9738b-215">**Improved Narrator support**</span></span>

<span data-ttu-id="9738b-216">Windows Forms v rozhraní .NET Framework 4.7.1 obsahuje následující vylepšení přístupnosti pro předčítání:</span><span class="sxs-lookup"><span data-stu-id="9738b-216">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="9738b-217"><xref:System.Windows.Forms.MonthCalendar> Ovládací prvek je přístupná Předčítání, a také v jiných nástrojích automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9738b-217">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="9738b-218"><xref:System.Windows.Forms.CheckedListBox> Řízení upozorní Předčítání při změně stavu zkontrolujte položky tak, že se uživateli upozornění, že jste změněna hodnota položky seznamu.</span><span class="sxs-lookup"><span data-stu-id="9738b-218">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="9738b-219"><xref:System.Windows.Forms.DataGridViewCell> Řízení sestavy Předčítání správný stav jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="9738b-219">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="9738b-220">Program Předčítání může načíst zakázáno <xref:System.Windows.Forms.ToolStripMenuItem> text, zatímco dříve by přeskočit položky nabídky zakázané.</span><span class="sxs-lookup"><span data-stu-id="9738b-220">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="9738b-221">**Vylepšená podpora pro usnadnění vzory vlastnosti UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="9738b-221">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="9738b-222">Od verze rozhraní .NET Framework 4.7.1, vývojáři nástrojů technologie usnadnění, můžou využít běžných vzorů usnadnění rozhraní API a vlastností pro ovládací prvky několik WinForms.</span><span class="sxs-lookup"><span data-stu-id="9738b-222">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="9738b-223">Usnadnění vylepšení patří:</span><span class="sxs-lookup"><span data-stu-id="9738b-223">These accessibility improvements include:</span></span>

- <span data-ttu-id="9738b-224"><xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ToolStripSplitButton> teď podporují [rozbalit nebo sbalit vzor](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="9738b-224">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="9738b-225"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> Teď podporuje [přepnutí vzor](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="9738b-225">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="9738b-226"><xref:System.Windows.Forms.ToolStripItem> Podporuje ovládací prvek <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> vlastnost a [rozbalit nebo sbalit vzor](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="9738b-226">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="9738b-227"><xref:System.Windows.Forms.NumericUpDown> a <xref:System.Windows.Forms.DomainUpDown> podporu ovládací prvky <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9738b-227">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="9738b-228">**Práce s prohlížečem vylepšené vlastnost**</span><span class="sxs-lookup"><span data-stu-id="9738b-228">**Improved property browser experience**</span></span>

<span data-ttu-id="9738b-229">Od verze rozhraní .NET Framework 4.7.1, Windows Forms zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="9738b-229">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="9738b-230">Lepší navigační klávesnice prostřednictvím různých windows rozevíracího seznamu výběru.</span><span class="sxs-lookup"><span data-stu-id="9738b-230">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="9738b-231">Snížení nepotřebné zarážek tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="9738b-231">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="9738b-232">Typy ovládacích prvků hlášení lépe.</span><span class="sxs-lookup"><span data-stu-id="9738b-232">Better reporting of control types.</span></span>
- <span data-ttu-id="9738b-233">Vylepšené Předčítání chování.</span><span class="sxs-lookup"><span data-stu-id="9738b-233">Improved narrator behavior.</span></span>
 
## <a name="see-also"></a><span data-ttu-id="9738b-234">Viz také</span><span class="sxs-lookup"><span data-stu-id="9738b-234">See Also</span></span>
[<span data-ttu-id="9738b-235">Co je nového v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9738b-235">What's new in the .NET Framework</span></span>](whats-new.md)   
 