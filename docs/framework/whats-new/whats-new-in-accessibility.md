---
title: Co je nového v usnadnění v rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fe7e15e482028b9988d7e560b98be19b6c07427
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509213"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="2eccc-102">Co je nového v usnadnění v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2eccc-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="2eccc-103">Rozhraní .NET Framework se zaměřuje na zpřístupnění aplikace více pro vaše uživatele.</span><span class="sxs-lookup"><span data-stu-id="2eccc-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="2eccc-104">Funkce usnadnění povolit aplikace a poskytuje příslušné prostředí pro uživatele technologie usnadnění.</span><span class="sxs-lookup"><span data-stu-id="2eccc-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="2eccc-105">Od verze rozhraní .NET Framework 4.7.1, rozhraní .NET Framework obsahuje velké množství vylepšení přístupnosti, které umožňují vývojářům vytvářet aplikace přístupná.</span><span class="sxs-lookup"><span data-stu-id="2eccc-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span> 

## <a name="accessibility-switches"></a><span data-ttu-id="2eccc-106">Usnadnění přepínače</span><span class="sxs-lookup"><span data-stu-id="2eccc-106">Accessibility switches</span></span>

<span data-ttu-id="2eccc-107">Můžete nakonfigurovat aplikace, který se přidá do funkce pro usnadnění přístupu, pokud se používá starší verze nebo 4.7 rozhraní .NET Framework, ale běží na rozhraní .NET Framework 4.7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="2eccc-107">You can configure your app to opt into accessibility features if it targets the .NET Framework 4.7 or an earlier version but is running on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="2eccc-108">Můžete také nakonfigurovat v aplikaci použijte starší verze funkce (a ne využívají funkce pro usnadnění přístupu), pokud je cílem rozhraní .NET Framework 4.7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="2eccc-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="2eccc-109">Každá verze rozhraní .NET Framework, která zahrnuje funkce pro usnadnění přístupu má specifické pro verzi usnadnění přepínač, který přidáte do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element v [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) části konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="2eccc-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="2eccc-110">Tady jsou podporované přepínače:</span><span class="sxs-lookup"><span data-stu-id="2eccc-110">The following are the supported switches:</span></span>

|<span data-ttu-id="2eccc-111">Version</span><span class="sxs-lookup"><span data-stu-id="2eccc-111">Version</span></span>|<span data-ttu-id="2eccc-112">přepínače</span><span class="sxs-lookup"><span data-stu-id="2eccc-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="2eccc-113">Rozhraní .NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="2eccc-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="2eccc-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="2eccc-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="2eccc-115">Rozhraní .NET framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="2eccc-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="2eccc-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="2eccc-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="2eccc-117">Využití výhod vylepšení přístupnosti</span><span class="sxs-lookup"><span data-stu-id="2eccc-117">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="2eccc-118">Nové funkce pro usnadnění přístupu jsou povolené ve výchozím nastavení pro aplikace, které cílí na rozhraní .NET Framework 4.7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="2eccc-118">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="2eccc-119">Kromě toho aplikace, které cílení na dřívější verzi rozhraní .NET Framework, ale běží na rozhraní .NET Framework 4.7.1 a později se můžete rozhodnout ze starší verze usnadnění chování (a tím využít výhod vylepšení přístupnosti) přidáním parametrů do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element v [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) oddíl konfiguračního souboru aplikace a nastavení jejich hodnoty `false`.</span><span class="sxs-lookup"><span data-stu-id="2eccc-119">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="2eccc-120">Následující ukazuje, jak se vyjádřit výslovný souhlas pro usnadnění vylepšení byla zavedená v rozhraní .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="2eccc-120">The following shows how to opt in to accessibility enhancements introduced in the .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="2eccc-121">Pokud zvolíte možnost vyjádřit výslovný souhlas pro funkce usnadnění v novější verzi rozhraní .NET Framework, můžete musí také výslovně vyjádřit výslovný souhlas k funkcím z dřívějších verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2eccc-121">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="2eccc-122">Konfigurace aplikace využívat výhod vylepšení přístupnosti v obou rozhraní .NET Framework 4.7.1 a 4.7.2 vyžaduje následující [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span><span class="sxs-lookup"><span data-stu-id="2eccc-122">Configuring your app to take advantage of accessibility improvements in both the .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="2eccc-123">Obnovení staršího chování</span><span class="sxs-lookup"><span data-stu-id="2eccc-123">Restoring legacy behavior</span></span>

<span data-ttu-id="2eccc-124">Aplikace, které cílové verze rozhraní .NET Framework, počínaje 4.7.1 můžete zakázat funkce usnadnění přidáním přepínače se mají [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element v [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) část konfigurační soubor aplikace a nastavení jejich hodnoty `true`.</span><span class="sxs-lookup"><span data-stu-id="2eccc-124">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="2eccc-125">Například následující konfigurace výslovný nesouhlas byla zavedená v rozhraní .NET Framework 4.7.2 funkce pro usnadnění přístupu:</span><span class="sxs-lookup"><span data-stu-id="2eccc-125">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>  

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-472"></a><span data-ttu-id="2eccc-126">Co je nového v usnadnění v rozhraní .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="2eccc-126">What's new in accessibility in the .NET Framework 4.7.2</span></span>

<span data-ttu-id="2eccc-127">Rozhraní .NET Framework 4.7.2 zahrnuje nové funkce usnadnění v těchto oblastech:</span><span class="sxs-lookup"><span data-stu-id="2eccc-127">The .NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="2eccc-128">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2eccc-128">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="2eccc-129">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="2eccc-129">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>
### <a name="windows-forms"></a><span data-ttu-id="2eccc-130">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2eccc-130">Windows Forms</span></span>

<span data-ttu-id="2eccc-131">**OS definovaných barev v motivy vysoký kontrast**</span><span class="sxs-lookup"><span data-stu-id="2eccc-131">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="2eccc-132">Od verze rozhraní .NET Framework 4.7.2, používá Windows Forms barev definovaných podle operačního systému v vysoký kontrast motivů.</span><span class="sxs-lookup"><span data-stu-id="2eccc-132">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="2eccc-133">Tato akce ovlivní následující prvky:</span><span class="sxs-lookup"><span data-stu-id="2eccc-133">This affects the following controls:</span></span>

- <span data-ttu-id="2eccc-134">Šipku rozevíracího seznamu <xref:System.Windows.Forms.ToolStripDropDownButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2eccc-134">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="2eccc-135"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> a <xref:System.Windows.Forms.CheckBox> ovládací prvky s <xref:System.Windows.Forms.ButtonBase.FlatStyle> nastavena na <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2eccc-135">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2eccc-136">Dříve vybrané barvy textu a pozadí nebyly – kontrast a byly těžko čitelný.</span><span class="sxs-lookup"><span data-stu-id="2eccc-136">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="2eccc-137">Ovládací prvky obsažené v <xref:System.Windows.Forms.GroupBox> s jeho <xref:System.Windows.Forms.Control.Enabled> vlastnost nastavena na hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="2eccc-137">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>
 
- <span data-ttu-id="2eccc-138"><xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, A <xref:System.Windows.Forms.ToolStripDropDownButton> ovládací prvky, které mají vyšší světlost kontrast poměr v režimu Vysoký kontrast.</span><span class="sxs-lookup"><span data-stu-id="2eccc-138">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="2eccc-139"><xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> Vlastnost <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="2eccc-139">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="2eccc-140">**Vylepšení Předčítání**</span><span class="sxs-lookup"><span data-stu-id="2eccc-140">**Narrator improvements**</span></span>

<span data-ttu-id="2eccc-141">Od verze rozhraní .NET Framework 4.7.2, je podpora Předčítání rozšířené následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="2eccc-141">Starting with the .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="2eccc-142">Vysílal informace o hodnotě <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> při uvedení text <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="2eccc-142">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span> 

- <span data-ttu-id="2eccc-143">Určuje, kdy <xref:System.Windows.Forms.ToolStripMenuItem> má jeho <xref:System.Windows.Forms.Control.Enabled> vlastnost nastavena na hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="2eccc-143">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="2eccc-144">Nabízí zpětnou vazbu týkající se stavu zaškrtávacího políčka při <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="2eccc-144">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="2eccc-145">Program Předčítání na kontrolovat režimu fokus pořadí je konzistentní s visual pořadí prvků v dialogovém okně stahování ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="2eccc-145">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="2eccc-146">**DataGridView – vylepšení**</span><span class="sxs-lookup"><span data-stu-id="2eccc-146">**DataGridView improvements**</span></span>

<span data-ttu-id="2eccc-147">Od verze rozhraní .NET Framework 4.7.2, <xref:System.Windows.Forms.DataGridView> ovládací prvek obsahuje zavedla následující vylepšení přístupnosti:</span><span class="sxs-lookup"><span data-stu-id="2eccc-147">Starting with the .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="2eccc-148">Řádky lze seřadit pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="2eccc-148">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="2eccc-149">Uživatele můžete použít klávesu F3 Chcete-li řadit podle aktuální sloupec.</span><span class="sxs-lookup"><span data-stu-id="2eccc-149">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="2eccc-150">Když <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> je nastaven na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, změní barvu, která označuje aktuální sloupec jako karty uživatele prostřednictvím buněk na aktuálním řádku na záhlaví sloupce.</span><span class="sxs-lookup"><span data-stu-id="2eccc-150">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="2eccc-151"><xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> Vlastnost <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> vrátí správné nadřazeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2eccc-151">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="2eccc-152">**Vylepšené vizuální upozornění**</span><span class="sxs-lookup"><span data-stu-id="2eccc-152">**Improved visual cues**</span></span>

- <span data-ttu-id="2eccc-153"><xref:System.Windows.Forms.RadioButton> a <xref:System.Windows.Forms.CheckBox> ovládací prvky s prázdnou <xref:System.Windows.Forms.ButtonBase.Text> vlastnost zobrazí indikátor fokus při přijetí fokus.</span><span class="sxs-lookup"><span data-stu-id="2eccc-153">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="2eccc-154">**Podpora vylepšené vlastnost mřížky**</span><span class="sxs-lookup"><span data-stu-id="2eccc-154">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="2eccc-155"><xref:System.Windows.Forms.PropertyGrid> Řízení nyní návratový podřízené elementy `true` pro <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> vlastnost pouze v případě, že je povolená PropertyGrid element.</span><span class="sxs-lookup"><span data-stu-id="2eccc-155">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="2eccc-156"><xref:System.Windows.Forms.PropertyGrid> Řízení podřízené elementy návratový `false` pro <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> vlastnost jenom v případě, že uživatel může změnit PropertyGrid elementu.</span><span class="sxs-lookup"><span data-stu-id="2eccc-156">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="2eccc-157">**Vylepšené klávesnice navigace**</span><span class="sxs-lookup"><span data-stu-id="2eccc-157">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="2eccc-158"><xref:System.Windows.Forms.ToolStripButton> Řízení umožňuje fokus při obsažené v <xref:System.Windows.Forms.ToolStripPanel> který má <xref:System.Windows.Forms.ToolStripPanel.TabStop> vlastnost nastavena na hodnotu `true`</span><span class="sxs-lookup"><span data-stu-id="2eccc-158">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>
### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="2eccc-159">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="2eccc-159">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="2eccc-160">**Změny ovládacích prvků CheckBox a RadioButton**</span><span class="sxs-lookup"><span data-stu-id="2eccc-160">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="2eccc-161">V rozhraní .NET Framework 4.7.1 a starší verze, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> a <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> ovládacích prvků mají nekonzistentní a v klasickém a Vysoký kontrast motivů, vizuály nesprávný fokus.</span><span class="sxs-lookup"><span data-stu-id="2eccc-161">In the .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="2eccc-162">Těmto problémům dochází v případech, kdy ovládací prvky nemají žádné sady obsahu.</span><span class="sxs-lookup"><span data-stu-id="2eccc-162">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="2eccc-163">Přechod mezi motivy matoucí a fokus visual může být obtížné najdete v článku.</span><span class="sxs-lookup"><span data-stu-id="2eccc-163">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="2eccc-164">V rozhraní .NET Framework 4.7.2 tyto vizuály jsou nyní víc konzistentní v rámci celého motivy a snadno viditelná v klasickém a vysokým kontrastem motivů.</span><span class="sxs-lookup"><span data-stu-id="2eccc-164">In the .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="2eccc-165">**Ovládací prvky WinForms hostované v aplikaci WPF**</span><span class="sxs-lookup"><span data-stu-id="2eccc-165">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="2eccc-166">Pro ovládací prvek WinForms hostované v aplikaci WPF v rozhraní .NET Framework 4.7.1 a starší verze, uživatelé nelze kartu mimo vrstvě WinForms Pokud je první nebo poslední ovládací prvek v této vrstvě WPF <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2eccc-166">For WinForms control hosted in a WPF application in the .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="2eccc-167">V rozhraní .NET Framework 4.7.2 mohou uživatelé nyní kartě mimo vrstvě WinForms.</span><span class="sxs-lookup"><span data-stu-id="2eccc-167">In the .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="2eccc-168">Automatizované aplikace, které závisí na fokus nikdy uvozovací znaky vrstvě WinForms může však přestane fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="2eccc-168">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="2eccc-169">Co je nového v usnadnění v rozhraní .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="2eccc-169">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="2eccc-170">Rozhraní .NET Framework 4.7.1 zahrnuje nové funkce usnadnění v těchto oblastech:</span><span class="sxs-lookup"><span data-stu-id="2eccc-170">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="2eccc-171">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="2eccc-171">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="2eccc-172">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2eccc-172">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="2eccc-173">Ovládací prvky ASP.NET web</span><span class="sxs-lookup"><span data-stu-id="2eccc-173">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="2eccc-174">.NET SDK – nástroje</span><span class="sxs-lookup"><span data-stu-id="2eccc-174">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="2eccc-175">Návrhář Windows Workflow Foundation (WF) pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="2eccc-175">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>
### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="2eccc-176">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="2eccc-176">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="2eccc-177">**Vylepšení čtečky obrazovky**</span><span class="sxs-lookup"><span data-stu-id="2eccc-177">**Screen reader improvements**</span></span>

<span data-ttu-id="2eccc-178">Pokud jsou povolené vylepšení přístupnosti, rozhraní .NET Framework 4.7.1 obsahuje následující vylepšení, které ovlivňují čtečky obrazovky:</span><span class="sxs-lookup"><span data-stu-id="2eccc-178">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="2eccc-179">V rozhraní .NET Framework 4.7 a dřívějších verzích <xref:System.Windows.Controls.Expander> ovládací prvky byly oznamují čtečky obrazovky jako tlačítka.</span><span class="sxs-lookup"><span data-stu-id="2eccc-179">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="2eccc-180">Od verze rozhraní .NET Framework 4.7.1, že jsou správně oznámila jako rozšíření, sbalitelné skupiny.</span><span class="sxs-lookup"><span data-stu-id="2eccc-180">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="2eccc-181">V rozhraní .NET Framework 4.7 a dřívějších verzích <xref:System.Windows.Controls.DataGridCell> ovládací prvky byly oznamují čtečky obrazovky jako "vlastní".</span><span class="sxs-lookup"><span data-stu-id="2eccc-181">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="2eccc-182">Od verze rozhraní .NET Framework 4.7.1, se nyní správně odesílány zpět jako buňky v mřížce dat (lokalizované).</span><span class="sxs-lookup"><span data-stu-id="2eccc-182">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>
 
- <span data-ttu-id="2eccc-183">Od verze rozhraní .NET Framework 4.7.1, čtečky obrazovky oznamujeme název upravitelné <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="2eccc-183">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="2eccc-184">V rozhraní .NET Framework 4.7 a dřívějších verzích <xref:System.Windows.Controls.PasswordBox> ovládací prvky byly oznámí jako "žádná položka v zobrazení", nebo byl jinak nesprávné chování.</span><span class="sxs-lookup"><span data-stu-id="2eccc-184">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="2eccc-185">Tento problém vyřešen, od verze rozhraní .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="2eccc-185">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>

<span data-ttu-id="2eccc-186">**Vlastnosti UIAutomation LiveRegion podpory**</span><span class="sxs-lookup"><span data-stu-id="2eccc-186">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="2eccc-187">Čtečky obrazovky například Předčítání pomoci ostatním uživatelům číst obsah uživatelského rozhraní aplikace, obvykle je výstup uživatelského rozhraní obsah, který je aktivní.</span><span class="sxs-lookup"><span data-stu-id="2eccc-187">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="2eccc-188">Ale pokud prvku uživatelského rozhraní se změní a nemá fokus, uživatel nemusí být upozorněni a může dojít důležité informace.</span><span class="sxs-lookup"><span data-stu-id="2eccc-188">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="2eccc-189">Za provozu oblasti cílem řešení tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="2eccc-189">Live regions aim at solving this problem.</span></span> <span data-ttu-id="2eccc-190">Vývojář může je použít k informování čtečky obrazovky nebo jakéhokoli klienta vlastnosti UIAutomation, který byl proveden důležité změně prvku uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2eccc-190">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="2eccc-191">Čtečky obrazovky můžete pak rozhodnout, jak a kdy k informování uživatelů této změny.</span><span class="sxs-lookup"><span data-stu-id="2eccc-191">The screen reader can then decide how and when to inform the user of this change.</span></span> 

<span data-ttu-id="2eccc-192">Pro podporu za provozu oblasti, byly přidány následující rozhraní API k použití WPF:</span><span class="sxs-lookup"><span data-stu-id="2eccc-192">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="2eccc-193"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> pole, které identifikovat **LiveSetting** vlastnost a **LiveRegionChanged** událostí.</span><span class="sxs-lookup"><span data-stu-id="2eccc-193">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="2eccc-194">Můžete být nastavit s použitím jazyka XAML.</span><span class="sxs-lookup"><span data-stu-id="2eccc-194">They can be set by using XAML.</span></span>

- <span data-ttu-id="2eccc-195">**AutomationProperties.LiveSetting** přidružená vlastnost, která informuje o čtečky obrazovky významné změny uživatelského rozhraní pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="2eccc-195">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="2eccc-196"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Vlastnost, která ji identifikuje **AutomationProperties.LiveSetting** přidružená vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2eccc-196">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>
 
- <span data-ttu-id="2eccc-197"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Metodu, která může být potlačena za účelem poskytování **LiveSetting** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2eccc-197">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="2eccc-198"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> metody, které získání a nastavení **LiveSetting** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2eccc-198">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>
 
- <span data-ttu-id="2eccc-199"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Výčtu, který definuje následující možné **LiveSetting** hodnoty:</span><span class="sxs-lookup"><span data-stu-id="2eccc-199">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="2eccc-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2eccc-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2eccc-201">Element neodešle oznámení, pokud došlo ke změně obsahu oblasti za provozu.</span><span class="sxs-lookup"><span data-stu-id="2eccc-201">The element does not send notifications if the content of the live region has changed.</span></span>   
   - <span data-ttu-id="2eccc-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2eccc-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2eccc-203">Element odešle-interruptive oznámení, pokud došlo ke změně obsahu oblasti za provozu.</span><span class="sxs-lookup"><span data-stu-id="2eccc-203">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>   

  - <span data-ttu-id="2eccc-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2eccc-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="2eccc-205">Element odešle interruptive oznámení, pokud došlo ke změně obsahu oblasti za provozu.</span><span class="sxs-lookup"><span data-stu-id="2eccc-205">The element sends interruptive notifications if the content of the live region has changed.</span></span>   

<span data-ttu-id="2eccc-206">Můžete vytvořit LiveRegion nastavením **AutomationProperties.LiveSetting** vlastnost v elementu zajímat, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2eccc-206">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="2eccc-207">Při změně dat v oblasti za provozu a je nutné informovat čtečky obrazovky, explicitně zvýšíte událost, jak znázorňuje následující ukázka.</span><span class="sxs-lookup"><span data-stu-id="2eccc-207">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="2eccc-208">**Vysoký kontrast**</span><span class="sxs-lookup"><span data-stu-id="2eccc-208">**High contrast**</span></span>

<span data-ttu-id="2eccc-209">Od verze rozhraní .NET Framework 4.7.1, vysoký kontrast vylepšily do různých ovládacích prvků WPF.</span><span class="sxs-lookup"><span data-stu-id="2eccc-209">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="2eccc-210">Jsou nyní viditelné při <xref:System.Windows.SystemParameters.HighContrast%2A> motiv nastavena.</span><span class="sxs-lookup"><span data-stu-id="2eccc-210">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="2eccc-211">Mezi ně patří:</span><span class="sxs-lookup"><span data-stu-id="2eccc-211">These include:</span></span>

- <span data-ttu-id="2eccc-212"><xref:System.Windows.Controls.Expander> Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="2eccc-212"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="2eccc-213">Visual pro zaměřuje <xref:System.Windows.Controls.Expander> ovládací prvek je nyní viditelné.</span><span class="sxs-lookup"><span data-stu-id="2eccc-213">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="2eccc-214">Vizuály klávesnice pro <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, a <xref:System.Windows.Controls.RadioButton> ovládací prvky jsou také viditelné.</span><span class="sxs-lookup"><span data-stu-id="2eccc-214">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="2eccc-215">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2eccc-215">For example:</span></span>

    <span data-ttu-id="2eccc-216">Před:</span><span class="sxs-lookup"><span data-stu-id="2eccc-216">Before:</span></span> 
    
    ![Ovládací prvek Expander s fokusem před vylepšení přístupnosti](media/expander-before.png)

    <span data-ttu-id="2eccc-218">Po:</span><span class="sxs-lookup"><span data-stu-id="2eccc-218">After:</span></span> 

    ![Ovládací prvek Expander fokus po vylepšení přístupnosti](media/expander-after.png)

- <span data-ttu-id="2eccc-220"><xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.RadioButton> ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="2eccc-220"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>
 
    <span data-ttu-id="2eccc-221">Text v <xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.RadioButton> ovládací prvky je nyní snazší uvidí, když je vybraný v vysoký kontrast motivů.</span><span class="sxs-lookup"><span data-stu-id="2eccc-221">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="2eccc-222">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2eccc-222">For example:</span></span>

    <span data-ttu-id="2eccc-223">Před:</span><span class="sxs-lookup"><span data-stu-id="2eccc-223">Before:</span></span> 

    ![Vysoký kontrast přepínač s fokusem před vylepšení přístupnosti](media/radio-button-before.png)
    
    <span data-ttu-id="2eccc-225">Po:</span><span class="sxs-lookup"><span data-stu-id="2eccc-225">After:</span></span> 

    ![Vysoký kontrast přepínač s fokusem po vylepšení přístupnosti](media/radio-button-after.png)

- <span data-ttu-id="2eccc-227"><xref:System.Windows.Controls.ComboBox> Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="2eccc-227"><xref:System.Windows.Controls.ComboBox> control</span></span>
 
    <span data-ttu-id="2eccc-228">Od verze rozhraní .NET Framework 4.7.1, ohraničení zakázáno <xref:System.Windows.Controls.ComboBox> ovládací prvek se stejnou barvu jako zakázaný text.</span><span class="sxs-lookup"><span data-stu-id="2eccc-228">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="2eccc-229">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2eccc-229">For example:</span></span>
    
    <span data-ttu-id="2eccc-230">Před:</span><span class="sxs-lookup"><span data-stu-id="2eccc-230">Before:</span></span> 

     ![ComboBox – zakázáno ohraničení a text před vylepšení přístupnosti](media/combo-disabled-before.png)

    <span data-ttu-id="2eccc-232">Po:</span><span class="sxs-lookup"><span data-stu-id="2eccc-232">After:</span></span>   

     ![ComboBox – po vylepšení přístupnosti zakázán ohraničení a text.](media/combo-disabled-after.png)

    <span data-ttu-id="2eccc-234">Kromě toho zakázané a zaměřují se tlačítka použít barvu motivu správné.</span><span class="sxs-lookup"><span data-stu-id="2eccc-234">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="2eccc-235">Před:</span><span class="sxs-lookup"><span data-stu-id="2eccc-235">Before:</span></span>

    ![Tlačítko barev motivů před vylepšení přístupnosti](media/button-themes-before.png) 
    
    <span data-ttu-id="2eccc-237">Po:</span><span class="sxs-lookup"><span data-stu-id="2eccc-237">After:</span></span> 

    ![Tlačítko barev motivů po vylepšení přístupnosti](media/button-themes-after.png) 

    <span data-ttu-id="2eccc-239">Nakonec v rozhraní .NET Framework 4.7 a dřívějších verzích, nastavení <xref:System.Windows.Controls.ComboBox> styl ovládacího prvku, který se `Toolbar.ComboBoxStyleKey` způsobila na šipku rozevíracího seznamu byla neviditelná.</span><span class="sxs-lookup"><span data-stu-id="2eccc-239">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="2eccc-240">Tento problém vyřešen, od verze rozhraní .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="2eccc-240">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="2eccc-241">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2eccc-241">For example:</span></span>

    <span data-ttu-id="2eccc-242">Před:</span><span class="sxs-lookup"><span data-stu-id="2eccc-242">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey před vylepšení přístupnosti](media/comboboxstylekey-before.png) 
    
    <span data-ttu-id="2eccc-244">Po:</span><span class="sxs-lookup"><span data-stu-id="2eccc-244">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey po vylepšení přístupnosti](media/comboboxstylekey-after.png) 

- <span data-ttu-id="2eccc-246"><xref:System.Windows.Controls.DataGrid> Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="2eccc-246"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="2eccc-247">Od verze rozhraní .NET Framework 4.7.1, šipku řazení indikátoru v <xref:System.Windows.Controls.DataGrid> řídí teď používá opravte barev motivů.</span><span class="sxs-lookup"><span data-stu-id="2eccc-247">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="2eccc-248">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2eccc-248">For example:</span></span>

    <span data-ttu-id="2eccc-249">Před:</span><span class="sxs-lookup"><span data-stu-id="2eccc-249">Before:</span></span> 

    ![Řazení šipku indikátoru před vylepšení přístupnosti](media/sort-indicator-before.png) 
    
    <span data-ttu-id="2eccc-251">Po:</span><span class="sxs-lookup"><span data-stu-id="2eccc-251">After:</span></span>   
 
    ![Řazení indikátor šipku po vylepšení přístupnosti](media/sort-indicator-after.png) 
    
    <span data-ttu-id="2eccc-253">Kromě toho v rozhraní .NET Framework 4.7 a dřívějších verzí, výchozí styl odkaz změnit na nesprávné barva na myši v režimu vysokého kontrastu.</span><span class="sxs-lookup"><span data-stu-id="2eccc-253">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="2eccc-254">Tento problém vyřešen od verze rozhraní .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="2eccc-254">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="2eccc-255">Podobně <xref:System.Windows.Controls.DataGrid> políčko sloupce používá pro zpětnou vazbu fokus klávesnice od verze rozhraní .NET Framework 4.7.1 očekávané barvy.</span><span class="sxs-lookup"><span data-stu-id="2eccc-255">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="2eccc-256">Před:</span><span class="sxs-lookup"><span data-stu-id="2eccc-256">Before:</span></span> 

    ![DataGrid – výchozí odkaz styl před vylepšení přístupnosti](media/default-link-style-before.png) 
 
    <span data-ttu-id="2eccc-258">Po:</span><span class="sxs-lookup"><span data-stu-id="2eccc-258">After:</span></span>    
  
    ![DataGrid – výchozí odkaz styl po vylepšení přístupnosti](media/default-link-style-after.png)  

<span data-ttu-id="2eccc-260">Další informace o vylepšení přístupnosti grafického subsystému WPF v rozhraní .NET Framework 4.7.1 najdete v tématu [vylepšení přístupnosti v grafickém subsystému WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="2eccc-260">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>
## <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="2eccc-261">Vylepšení přístupnosti Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2eccc-261">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="2eccc-262">Windows Forms (WinForms) v rozhraní .NET Framework 4.7.1 zahrnuje změny usnadnění v následujících oblastech.</span><span class="sxs-lookup"><span data-stu-id="2eccc-262">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="2eccc-263">**Vylepšené zobrazení v režimu vysokého kontrastu**</span><span class="sxs-lookup"><span data-stu-id="2eccc-263">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="2eccc-264">Od verze rozhraní .NET Framework 4.7.1, nabízejí různé ovládací prvky WinForms vylepšené vykreslování v funkce Vysoký kontrast režimech k dispozici v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="2eccc-264">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="2eccc-265">Windows 10 došlo ke změně hodnoty pro některé barvy systému vysoký kontrast a Windows Forms je založena na rozhraní Windows 10 Win32.</span><span class="sxs-lookup"><span data-stu-id="2eccc-265">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="2eccc-266">Pro dosažení co nejlepších výsledků spusťte na nejnovější verzi systému Windows a vyjádřit výslovný souhlas na nejnovější změny operačního systému tak, že přidáte soubor app.manifest v testovací aplikaci a zrušení komentář Windows 10 nepodporuje řádku operačního systému, aby vypadal jako následující:</span><span class="sxs-lookup"><span data-stu-id="2eccc-266">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
<span data-ttu-id="2eccc-267">Některé příklady vysoký kontrast změny patří:</span><span class="sxs-lookup"><span data-stu-id="2eccc-267">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="2eccc-268">Značky zaškrtnutí v <xref:System.Windows.Forms.MenuStrip> položky se snadněji zobrazení.</span><span class="sxs-lookup"><span data-stu-id="2eccc-268">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="2eccc-269">Pokud vybraná, zakázané <xref:System.Windows.Forms.MenuStrip> položky se snadněji zobrazení.</span><span class="sxs-lookup"><span data-stu-id="2eccc-269">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="2eccc-270">Text ve vybrané <xref:System.Windows.Forms.Button> řízení totéž co barva výběru.</span><span class="sxs-lookup"><span data-stu-id="2eccc-270">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="2eccc-271">Zakázaný text je snadnější čtení.</span><span class="sxs-lookup"><span data-stu-id="2eccc-271">Disabled text is easier to read.</span></span> <span data-ttu-id="2eccc-272">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2eccc-272">For example:</span></span>

    <span data-ttu-id="2eccc-273">Před:</span><span class="sxs-lookup"><span data-stu-id="2eccc-273">Before:</span></span>

    ![Zakázaný text před vylepšení přístupnosti](media/wf-disabled-before.png) 

    <span data-ttu-id="2eccc-275">Po:</span><span class="sxs-lookup"><span data-stu-id="2eccc-275">After:</span></span>

    ![Zakázaný text po vylepšení přístupnosti](media/wf-disabled-after.png) 

- <span data-ttu-id="2eccc-277">Vysoký kontrast vylepšení v dialogovém okně výjimka přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="2eccc-277">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="2eccc-278">**Vylepšená podpora Předčítání**</span><span class="sxs-lookup"><span data-stu-id="2eccc-278">**Improved Narrator support**</span></span>

<span data-ttu-id="2eccc-279">Windows Forms v rozhraní .NET Framework 4.7.1 obsahuje následující vylepšení přístupnosti pro předčítání:</span><span class="sxs-lookup"><span data-stu-id="2eccc-279">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="2eccc-280"><xref:System.Windows.Forms.MonthCalendar> Ovládací prvek je přístupná Předčítání, a také v jiných nástrojích automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2eccc-280">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="2eccc-281"><xref:System.Windows.Forms.CheckedListBox> Řízení upozorní Předčítání při změně stavu zkontrolujte položky tak, že se uživateli upozornění, že jste změněna hodnota položky seznamu.</span><span class="sxs-lookup"><span data-stu-id="2eccc-281">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>
 
- <span data-ttu-id="2eccc-282"><xref:System.Windows.Forms.DataGridViewCell> Řízení sestavy Předčítání správný stav jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="2eccc-282">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>
 
- <span data-ttu-id="2eccc-283">Program Předčítání může načíst zakázáno <xref:System.Windows.Forms.ToolStripMenuItem> text, zatímco dříve by přeskočit položky nabídky zakázané.</span><span class="sxs-lookup"><span data-stu-id="2eccc-283">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="2eccc-284">**Vylepšená podpora pro usnadnění vzory vlastnosti UIAutomation**</span><span class="sxs-lookup"><span data-stu-id="2eccc-284">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="2eccc-285">Od verze rozhraní .NET Framework 4.7.1, vývojáři nástrojů technologie usnadnění, můžou využít běžných vzorů usnadnění rozhraní API a vlastností pro ovládací prvky několik WinForms.</span><span class="sxs-lookup"><span data-stu-id="2eccc-285">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="2eccc-286">Usnadnění vylepšení patří:</span><span class="sxs-lookup"><span data-stu-id="2eccc-286">These accessibility improvements include:</span></span>

- <span data-ttu-id="2eccc-287"><xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ToolStripSplitButton> teď podporují [rozbalit nebo sbalit vzor](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2eccc-287">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>
 
- <span data-ttu-id="2eccc-288"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> Teď podporuje [přepnutí vzor](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2eccc-288">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>
 
- <span data-ttu-id="2eccc-289"><xref:System.Windows.Forms.ToolStripItem> Podporuje ovládací prvek <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> vlastnost a [rozbalit nebo sbalit vzor](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="2eccc-289">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="2eccc-290"><xref:System.Windows.Forms.NumericUpDown> a <xref:System.Windows.Forms.DomainUpDown> podporu ovládací prvky <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2eccc-290">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="2eccc-291">**Práce s prohlížečem vylepšené vlastnost**</span><span class="sxs-lookup"><span data-stu-id="2eccc-291">**Improved property browser experience**</span></span>

<span data-ttu-id="2eccc-292">Od verze rozhraní .NET Framework 4.7.1, Windows Forms zahrnuje:</span><span class="sxs-lookup"><span data-stu-id="2eccc-292">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="2eccc-293">Lepší navigační klávesnice prostřednictvím různých windows rozevíracího seznamu výběru.</span><span class="sxs-lookup"><span data-stu-id="2eccc-293">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="2eccc-294">Snížení nepotřebné zarážek tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="2eccc-294">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="2eccc-295">Typy ovládacích prvků hlášení lépe.</span><span class="sxs-lookup"><span data-stu-id="2eccc-295">Better reporting of control types.</span></span>
- <span data-ttu-id="2eccc-296">Vylepšené Předčítání chování.</span><span class="sxs-lookup"><span data-stu-id="2eccc-296">Improved narrator behavior.</span></span>
 
<a name="aspnet471"></a>
## <a name="aspnet-web-controls"></a><span data-ttu-id="2eccc-297">Ovládací prvky ASP.NET web</span><span class="sxs-lookup"><span data-stu-id="2eccc-297">ASP.NET web controls</span></span>

<span data-ttu-id="2eccc-298">Od verze rozhraní .NET Framework 4.7.1 a Visual Studio 2017 15.3, ASP.NET zvyšuje, jak fungují ovládacích prvků ASP.NET pomocí technologie usnadnění v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2eccc-298">Starting with the .NET Framework 4.7.1 and Visual Studio 2017 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="2eccc-299">Změny zahrnují následující:</span><span class="sxs-lookup"><span data-stu-id="2eccc-299">Changes include the following:</span></span>

- <span data-ttu-id="2eccc-300">Změny implementace chybějící vzorů usnadnění uživatelského rozhraní v ovládacích prvcích, jako je třeba **přidat pole** dialogové okno ve **zobrazení podrobností o** průvodce, nebo **Konfigurovat ListView** dialogovém **ListView** průvodce.</span><span class="sxs-lookup"><span data-stu-id="2eccc-300">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="2eccc-301">Změny ke zlepšení zobrazení v režimu vysokého kontrastu, jako je třeba **editoru služby Data Pager pole**.</span><span class="sxs-lookup"><span data-stu-id="2eccc-301">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="2eccc-302">Změny ke zlepšení navigační klávesnice vyskytne pro ovládací prvky, jako je třeba **pole** dialogové okno ve **upravit pole stránkování** Průvodce prvku DataPager **ObjectContext konfigurace**  dialogové okno, nebo **Konfigurovat výběr dat** dialogovém **konfigurace zdroje dat** průvodce.</span><span class="sxs-lookup"><span data-stu-id="2eccc-302">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>
## <a name="net-sdk-tools"></a><span data-ttu-id="2eccc-303">.NET SDK – nástroje</span><span class="sxs-lookup"><span data-stu-id="2eccc-303">.NET SDK Tools</span></span>

<span data-ttu-id="2eccc-304">[Nástroj Configuration Editor (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) a [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) došlo k vylepšení opravou rozmanitých problémy.</span><span class="sxs-lookup"><span data-stu-id="2eccc-304">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="2eccc-305">Většina z nich byly drobných záležitostí, jako je název není definované nebo určité vzorce automatizace uživatelského rozhraní není implementovaná správně.</span><span class="sxs-lookup"><span data-stu-id="2eccc-305">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="2eccc-306">Zatímco mnoho uživatelé nebudou vědět nesprávné hodnoty, zákazníkům, kteří používají technologie pro usnadnění jako čtečky obrazovky zjistí tyto sady SDK nástroje přístup.</span><span class="sxs-lookup"><span data-stu-id="2eccc-306">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span> 

<span data-ttu-id="2eccc-307">Tato vylepšení změnit některé předchozí chování, například pořadí fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="2eccc-307">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>
## <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="2eccc-308">Návrhář Windows Workflow Foundation (WF) pracovního postupu</span><span class="sxs-lookup"><span data-stu-id="2eccc-308">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="2eccc-309">Usnadnění změny v Návrháři pracovních postupů, patří:</span><span class="sxs-lookup"><span data-stu-id="2eccc-309">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="2eccc-310">Pořadí karet se změní na zleva doprava a shora dolů v některé ovládací prvky:</span><span class="sxs-lookup"><span data-stu-id="2eccc-310">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="2eccc-311">Okno inicializovat korelace pro nastavení korelace dat pro <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity.</span><span class="sxs-lookup"><span data-stu-id="2eccc-311">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="2eccc-312">Okno obsahu definice pro <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity.</span><span class="sxs-lookup"><span data-stu-id="2eccc-312">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="2eccc-313">Další funkce jsou dostupné prostřednictvím klávesnice:</span><span class="sxs-lookup"><span data-stu-id="2eccc-313">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="2eccc-314">Při úpravě vlastností aktivity, vlastnost skupiny lze sbalit pomocí klávesnice poprvé, které se zaměřuje.</span><span class="sxs-lookup"><span data-stu-id="2eccc-314">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="2eccc-315">Ikony upozornění jsou přístupné pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="2eccc-315">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="2eccc-316">**Více vlastnosti** v tlačítko **vlastnosti** okno je přístupná pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="2eccc-316">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="2eccc-317">Klávesnice mohou uživatelé položky hlavičky v **argumenty** a **proměnné** podokna Návrháře pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="2eccc-317">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="2eccc-318">Lepší viditelnost položek s fokusem, jako např. kdy:</span><span class="sxs-lookup"><span data-stu-id="2eccc-318">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="2eccc-319">Přidání řádků do datových mřížek používají návrháři návrháře pracovních postupů a aktivit.</span><span class="sxs-lookup"><span data-stu-id="2eccc-319">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="2eccc-320">Stisknutím klávesy tabulátor procházíte polí v <xref:System.ServiceModel.Activities.ReceiveReply> a <xref:System.ServiceModel.Activities.SendReply> aktivity.</span><span class="sxs-lookup"><span data-stu-id="2eccc-320">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="2eccc-321">Nastavení výchozí hodnoty pro proměnné nebo argumenty</span><span class="sxs-lookup"><span data-stu-id="2eccc-321">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="2eccc-322">Nyní můžete správné rozpoznání čtečky obrazovky:</span><span class="sxs-lookup"><span data-stu-id="2eccc-322">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="2eccc-323">Nastavte zarážky v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="2eccc-323">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="2eccc-324"><xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, A <xref:System.ServiceModel.Activities.CorrelationScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="2eccc-324">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="2eccc-325">Obsah <xref:System.ServiceModel.Activities.Receive> aktivity.</span><span class="sxs-lookup"><span data-stu-id="2eccc-325">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="2eccc-326">Cílový typ <xref:System.Activities.Statements.InvokeMethod> aktivity.</span><span class="sxs-lookup"><span data-stu-id="2eccc-326">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="2eccc-327">Pole se seznamem výjimky a nakonec v části <xref:System.Activities.Statements.TryCatch> aktivity.</span><span class="sxs-lookup"><span data-stu-id="2eccc-327">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="2eccc-328">Pole se seznamem typ zprávy, rozdělovače v okně Přidat inicializátory korelace, okno obsahu definice a definice CorrelatesOn okno v zasílání zpráv aktivity (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, a <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="2eccc-328">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="2eccc-329">Stav počítač přejde a přejde cíle.</span><span class="sxs-lookup"><span data-stu-id="2eccc-329">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="2eccc-330">Poznámky a konektory na <xref:System.Activities.Statements.FlowDecision> aktivity.</span><span class="sxs-lookup"><span data-stu-id="2eccc-330">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="2eccc-331">Kontextové (klikněte pravým tlačítkem) nabídky pro aktivity.</span><span class="sxs-lookup"><span data-stu-id="2eccc-331">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="2eccc-332">Editory hodnotu vlastnosti, na tlačítko Vymazat vyhledat, podle kategorie a abecedním řazení tlačítek a dialogové okno Editor výraz ve vlastnosti mřížky.</span><span class="sxs-lookup"><span data-stu-id="2eccc-332">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="2eccc-333">Procento přiblížení v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="2eccc-333">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="2eccc-334">Oddělovač v <xref:System.Activities.Statements.Parallel> a <xref:System.Activities.Statements.Pick> aktivity.</span><span class="sxs-lookup"><span data-stu-id="2eccc-334">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="2eccc-335"><xref:System.Activities.Statements.InvokeDelegate> Aktivity.</span><span class="sxs-lookup"><span data-stu-id="2eccc-335">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="2eccc-336">Vyberte typy okna pro slovník aktivity (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`atd.).</span><span class="sxs-lookup"><span data-stu-id="2eccc-336">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="2eccc-337">Okno Procházet a vyberte typ formátu .NET.</span><span class="sxs-lookup"><span data-stu-id="2eccc-337">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="2eccc-338">Popis cesty v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="2eccc-338">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="2eccc-339">Řady vylepšení v viditelnost návrháře pracovních postupů a jeho ovládacích prvků, jako je lepší kontrast poměr mezi elementy a použít pro prvky výběru výraznější výběr polí se zobrazí uživatelům, kteří se rozhodnou vysoký kontrast motivů.</span><span class="sxs-lookup"><span data-stu-id="2eccc-339">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="2eccc-340">Viz také</span><span class="sxs-lookup"><span data-stu-id="2eccc-340">See Also</span></span>

[<span data-ttu-id="2eccc-341">Co je nového v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2eccc-341">What's new in the .NET Framework</span></span>](whats-new.md)
 
