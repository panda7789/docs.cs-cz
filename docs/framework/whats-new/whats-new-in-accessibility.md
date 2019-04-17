---
title: Co je nového v usnadnění přístupu v rozhraní .NET Framework
ms.custom: updateeachrelease
ms.date: 04/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59fe1a5492b34d2aef88e81b86307498e3a5dc2c
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612287"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="9e9cd-102">Co je nového v usnadnění přístupu v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9e9cd-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="9e9cd-103">Rozhraní .NET Framework, zaměřuje na zpřístupnění aplikace více uživatelům.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="9e9cd-104">Funkce usnadnění umožnit aplikaci pro zajištění odpovídající prostředí pro uživatele technologie pro usnadnění.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="9e9cd-105">Od verze rozhraní .NET Framework 4.7.1, rozhraní .NET Framework obsahuje velké množství vylepšení přístupnosti, které umožňují vývojářům vytvářet aplikace přístupné.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-105">Starting with the .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="9e9cd-106">Usnadnění přepínače</span><span class="sxs-lookup"><span data-stu-id="9e9cd-106">Accessibility switches</span></span>

<span data-ttu-id="9e9cd-107">Můžete nakonfigurovat aplikaci tak, aby přihlašují funkce pro usnadnění přístupu, pokud cílí na rozhraní .NET Framework 4.7 nebo starší verzi, ale běží na rozhraní .NET Framework 4.7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-107">You can configure your app to opt into accessibility features if it targets the .NET Framework 4.7 or an earlier version but is running on the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="9e9cd-108">Můžete také konfigurovat aplikace pro použití funkce starší verze (a ne Využijte výhod funkce pro usnadnění přístupu), pokud je zaměřena rozhraní .NET Framework 4.7.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="9e9cd-109">Každá verze rozhraní .NET Framework, která zahrnuje funkce pro usnadnění přístupu má specifické pro verzi usnadnění přepínač, který přidáte do [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) oddílu konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="9e9cd-110">Tady jsou podporované přepínače:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-110">The following are the supported switches:</span></span>

|<span data-ttu-id="9e9cd-111">Version</span><span class="sxs-lookup"><span data-stu-id="9e9cd-111">Version</span></span>|<span data-ttu-id="9e9cd-112">Přepínač</span><span class="sxs-lookup"><span data-stu-id="9e9cd-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="9e9cd-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="9e9cd-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="9e9cd-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="9e9cd-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="9e9cd-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="9e9cd-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="9e9cd-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="9e9cd-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="9e9cd-117">Využití výhod vylepšení přístupnosti</span><span class="sxs-lookup"><span data-stu-id="9e9cd-117">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="9e9cd-118">Nové funkce pro usnadnění přístupu se ve výchozím nastavení pro aplikace, které jsou cíleny rozhraní .NET Framework 4.7.1 povolená nebo novější.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-118">The new accessibility features are enabled by default for applications that target the .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="9e9cd-119">Kromě toho aplikace, které cílí na starší verzi rozhraní .NET Framework, ale jsou spuštěny v rozhraní .NET Framework 4.7.1 nebo později se můžou rozhodnout ze starší verze usnadnění chování (a tím využít výhod vylepšení přístupnosti) přidáním přepínače [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) oddílu konfiguračního souboru aplikace a nastavení jejich hodnoty na `false`.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-119">In addition, applications that target an earlier version of the .NET Framework but are running on the .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="9e9cd-120">Následující ukazuje, jak můžete vyjádřit výslovný souhlas vylepšení přístupnosti představena v rozhraní .NET Framework 4.7.1:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-120">The following shows how to opt in to accessibility enhancements introduced in the .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="9e9cd-121">Pokud budete chtít povolit funkce usnadnění v novější verzi rozhraní .NET Framework, musíte také explicitně připojíte k funkcím z předchozích verzí rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-121">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="9e9cd-122">Konfigurace aplikace využít k vylepšení přístupnosti v obou rozhraní .NET Framework 4.7.1 a 4.7.2 vyžaduje následující [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-122">Configuring your app to take advantage of accessibility improvements in both the .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="9e9cd-123">Obnovit starší chování</span><span class="sxs-lookup"><span data-stu-id="9e9cd-123">Restoring legacy behavior</span></span>

<span data-ttu-id="9e9cd-124">Aplikací s cílovou verzí rozhraní .NET Framework 4.7.1 počínaje může zakázat funkce pro usnadnění přístupu přidáním přepínače [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) prvek [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) část konfigurační soubor aplikace a nastavení jejich hodnoty na `true`.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-124">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="9e9cd-125">Například následující konfigurace výslovný představena v rozhraní .NET Framework 4.7.2 funkce pro usnadnění přístupu:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-125">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-472"></a><span data-ttu-id="9e9cd-126">Co je nového v usnadnění přístupu v rozhraní .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="9e9cd-126">What's new in accessibility in the .NET Framework 4.7.2</span></span>

<span data-ttu-id="9e9cd-127">Rozhraní .NET Framework 4.7.2 obsahuje nové funkce pro usnadnění přístupu v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-127">The .NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="9e9cd-128">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e9cd-128">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="9e9cd-129">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="9e9cd-129">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="9e9cd-130">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e9cd-130">Windows Forms</span></span>

<span data-ttu-id="9e9cd-131">**Operační systém definovaných barev v Vysokokontrastních motivech**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-131">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="9e9cd-132">Počínaje rozhraním .NET Framework 4.7.2, Windows Forms používá barvám definovaným v Vysokokontrastních motivech v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-132">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="9e9cd-133">Tato akce ovlivní následující ovládací prvky:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-133">This affects the following controls:</span></span>

- <span data-ttu-id="9e9cd-134">Na šipku rozevíracího seznamu <xref:System.Windows.Forms.ToolStripDropDownButton> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-134">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="9e9cd-135"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> a <xref:System.Windows.Forms.CheckBox> ovládací prvky s <xref:System.Windows.Forms.ButtonBase.FlatStyle> nastavena na <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> nebo <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-135">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9e9cd-136">Dříve vybrané barvy textu a pozadí nebyly kontrastní a bylo obtížné číst.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-136">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="9e9cd-137">Ovládací prvky obsažené v rámci <xref:System.Windows.Forms.GroupBox> , který má jeho <xref:System.Windows.Forms.Control.Enabled> nastavenou na `false`.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-137">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="9e9cd-138"><xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, A <xref:System.Windows.Forms.ToolStripDropDownButton> ovládací prvky, které mají zvýšené světelnost kontrastní poměr v režimu s vysokým kontrastem.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-138">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="9e9cd-139"><xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> Vlastnost <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-139">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="9e9cd-140">**Vylepšení programu Předčítání**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-140">**Narrator improvements**</span></span>

<span data-ttu-id="9e9cd-141">Počínaje rozhraním .NET Framework 4.7.2, je program Předčítání podpory rozšířeného následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-141">Starting with the .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="9e9cd-142">Představuje hodnotu <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> při uvedení text <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-142">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="9e9cd-143">Označuje, kdy <xref:System.Windows.Forms.ToolStripMenuItem> má jeho <xref:System.Windows.Forms.Control.Enabled> nastavenou na `false`.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-143">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="9e9cd-144">Poskytuje zpětnou vazbu týkající se stavu zaškrtávacího políčka při <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> je nastavena na `true`.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-144">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="9e9cd-145">Program Předčítání na režim kontroly fokus pořadí je konzistentní s visual pořadí ovládacích prvků v dialogovém okně stahování ClickOnce.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-145">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="9e9cd-146">**Vylepšení ovládacího prvku DataGridView**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-146">**DataGridView improvements**</span></span>

<span data-ttu-id="9e9cd-147">Počínaje rozhraním .NET Framework 4.7.2, <xref:System.Windows.Forms.DataGridView> ovládací prvek přináší následující vylepšení přístupnosti:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-147">Starting with the .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="9e9cd-148">Lze seřadit řádky pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-148">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="9e9cd-149">Uživatele můžete použít klávesy F3 k řazení podle aktuální sloupce.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-149">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="9e9cd-150">Když <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> je nastavena na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, záhlaví sloupce se změní barvu označující aktuální sloupec jako karty uživatele mezi buňkami v aktuálním řádku.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-150">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="9e9cd-151"><xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> Vlastnost <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> vrátí správné nadřazený ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-151">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="9e9cd-152">**Vylepšené vizuální prvky**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-152">**Improved visual cues**</span></span>

- <span data-ttu-id="9e9cd-153"><xref:System.Windows.Forms.RadioButton> a <xref:System.Windows.Forms.CheckBox> ovládací prvky s prázdnou <xref:System.Windows.Forms.ButtonBase.Text> vlastnost zobrazit indikátor fokus, když obdrží fokus.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-153">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="9e9cd-154">**Podpora vylepšené vlastnost mřížky**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-154">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="9e9cd-155"><xref:System.Windows.Forms.PropertyGrid> Ovládací prvek nyní návratový podřízené prvky `true` pro <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> vlastnost, jenom když je povolený prvku PropertyGrid.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-155">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="9e9cd-156"><xref:System.Windows.Forms.PropertyGrid> Ovládacích prvků podřízené návratový `false` pro <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> vlastnost pouze v případě, že uživatel může změnit prvku PropertyGrid.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-156">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="9e9cd-157">**Navigace pomocí kláves vylepšené**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-157">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="9e9cd-158"><xref:System.Windows.Forms.ToolStripButton> Ovládací prvek umožňuje fokus, pokud je obsažen v <xref:System.Windows.Forms.ToolStripPanel> , který má <xref:System.Windows.Forms.ToolStripPanel.TabStop> vlastnost nastavena na hodnotu `true`</span><span class="sxs-lookup"><span data-stu-id="9e9cd-158">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="9e9cd-159">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="9e9cd-159">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="9e9cd-160">**Změny ovládacích prvků CheckBox a ovládacího prvku RadioButton**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-160">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="9e9cd-161">V rozhraní .NET Framework 4.7.1 a předchozími verzemi, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> a <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> ovládací prvky mají nekonzistentní a v modelu Classic a Vysoký kontrast motivy, nesprávné fokus vizuály.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-161">In the .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="9e9cd-162">Těmto problémům dochází v případech, ve kterém ovládací prvky nemají žádné sadu obsahu.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-162">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="9e9cd-163">Přechod mezi motivy matoucí a vizuál se fokus může být špatně vidět.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-163">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="9e9cd-164">V rozhraní .NET Framework 4.7.2 tyto vizuály jsou teď víc konzistentní v rámci celého motivy a snadněji viditelné v modelu Classic a Vysoký kontrast – motivy.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-164">In the .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="9e9cd-165">**Ovládacích prvků WinForms hostované v aplikaci WPF**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-165">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="9e9cd-166">Pro ovládací prvek WinForms je hostován v aplikaci WPF v rozhraní .NET Framework 4.7.1 a dřívějších verzích, uživatelé nelze kartu z vrstvy WinForms Pokud je první nebo poslední ovládací prvek v této vrstvě WPF <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-166">For WinForms control hosted in a WPF application in the .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="9e9cd-167">V rozhraní .NET Framework 4.7.2 uživatelé mohou nyní na kartě mimo vrstvě WinForms.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-167">In the .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="9e9cd-168">Automatizované aplikace, které spoléhají na fokus nikdy uvození WinForms vrstvy, ale už nemusí fungovat podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-168">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a><span data-ttu-id="9e9cd-169">Co je nového v usnadnění přístupu v rozhraní .NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="9e9cd-169">What's new in accessibility in the .NET Framework 4.7.1</span></span>

<span data-ttu-id="9e9cd-170">Rozhraní .NET Framework 4.7.1 obsahuje nové funkce pro usnadnění přístupu v následujících oblastech:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-170">The .NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="9e9cd-171">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="9e9cd-171">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="9e9cd-172">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e9cd-172">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="9e9cd-173">Webové ovládací prvky ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9e9cd-173">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="9e9cd-174">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="9e9cd-174">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="9e9cd-175">Windows Workflow Foundation (WF), návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="9e9cd-175">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="9e9cd-176">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="9e9cd-176">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="9e9cd-177">**Vylepšení čtečky obrazovky**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-177">**Screen reader improvements**</span></span>

<span data-ttu-id="9e9cd-178">Pokud jsou povolené vylepšení přístupnosti, rozhraní .NET Framework 4.7.1 zahrnuje následující vylepšení, které ovlivňují čtečky obrazovky:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-178">If accessibility improvements are enabled, the .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="9e9cd-179">V rozhraní .NET Framework 4.7 a předchozími verzemi <xref:System.Windows.Controls.Expander> ovládací prvky byly oznamovaný čtečkami obrazovky jako tlačítka.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-179">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="9e9cd-180">Od verze rozhraní .NET Framework 4.7.1, jejich správně oznámení jako rozšíření/sbalitelné skupiny.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-180">Starting with the .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="9e9cd-181">V rozhraní .NET Framework 4.7 a předchozími verzemi <xref:System.Windows.Controls.DataGridCell> ovládací prvky byly oznamovaný čtečkami obrazovky jako "vlastní".</span><span class="sxs-lookup"><span data-stu-id="9e9cd-181">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="9e9cd-182">Od verze rozhraní .NET Framework 4.7.1, jejich nyní správně oznámení jako buňka datové mřížky (lokalizované).</span><span class="sxs-lookup"><span data-stu-id="9e9cd-182">Starting with the .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="9e9cd-183">Od verze rozhraní .NET Framework 4.7.1, čtečky obrazovky oznamujeme název upravitelné <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-183">Starting with the .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="9e9cd-184">V rozhraní .NET Framework 4.7 a předchozími verzemi <xref:System.Windows.Controls.PasswordBox> ovládací prvky byly uvolněné jako "žádné položky v zobrazení" nebo měl jinak nesprávné chování.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-184">In the .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="9e9cd-185">Tento problém vyřešen, od verze rozhraní .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-185">This issue is fixed starting with the .NET Framework 4.7.1.</span></span>

<span data-ttu-id="9e9cd-186">**Vlastnosti UIAutomation LiveRegion podpory**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-186">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="9e9cd-187">Čtečky obrazovky, jako jsou například lidé pomoc programu Předčítání číst obsah uživatelského rozhraní aplikace, obvykle převod textu na řeč výstupní obsah uživatelského rozhraní, který má fokus.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-187">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="9e9cd-188">Pokud ale prvku uživatelského rozhraní se změní a nemá fokus, uživatel nemusí být upozorněni a přijít o důležité informace.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-188">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="9e9cd-189">Živé oblastech zaměřené na řešení tohoto problému.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-189">Live regions aim at solving this problem.</span></span> <span data-ttu-id="9e9cd-190">Vývojář můžete využít k informování čtečky obrazovky nebo jakéhokoli klienta vlastnosti UIAutomation, který byl proveden důležité změny prvku uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-190">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="9e9cd-191">Čtečka obrazovky se můžete rozhodnout používat jak a kdy informovat uživatele o této změně.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-191">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="9e9cd-192">Pro podporu živé oblastí, jsme přidali následující rozhraní API k použití WPF:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-192">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="9e9cd-193"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> pole, které identifikovat **LiveSetting** vlastnost a **LiveRegionChanged** událostí.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-193">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="9e9cd-194">Můžete třeba nastavit pomocí XAML.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-194">They can be set by using XAML.</span></span>

- <span data-ttu-id="9e9cd-195">**AutomationProperties.LiveSetting** přidružená vlastnost, která informuje o čtečka obrazovky významné změny uživatelského rozhraní pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-195">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="9e9cd-196"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Vlastnost, která identifikuje **AutomationProperties.LiveSetting** přidružená vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-196">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="9e9cd-197"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Metodu, která může být potlačena za účelem poskytují **LiveSetting** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-197">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="9e9cd-198"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> a <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> metody, které get a set **LiveSetting** hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-198">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="9e9cd-199"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Výčet, který definuje následující možné **LiveSetting** hodnoty:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-199">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

   - <span data-ttu-id="9e9cd-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-200"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9e9cd-201">Element neodešle oznámení, pokud došlo ke změně obsahu aktivní oblast.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-201">The element does not send notifications if the content of the live region has changed.</span></span>
   - <span data-ttu-id="9e9cd-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-202"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9e9cd-203">Element odešle-interruptive oznámení, pokud došlo ke změně obsahu aktivní oblast.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-203">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

   - <span data-ttu-id="9e9cd-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-204"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9e9cd-205">Element odešle interruptive oznámení, pokud došlo ke změně obsahu aktivní oblast.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-205">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="9e9cd-206">Můžete vytvořit LiveRegion nastavením **AutomationProperties.LiveSetting** vlastnosti prvku, která vás zajímá, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-206">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="9e9cd-207">Při změně dat v živé oblasti a je potřeba informovat čtečky obrazovky, můžete explicitně vyvolat událost, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-207">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="9e9cd-208">**Vysoký kontrast**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-208">**High contrast**</span></span>

<span data-ttu-id="9e9cd-209">Od verze rozhraní .NET Framework 4.7.1, vylepšení ve vysokém kontrastu byly provedeny na různé ovládací prvky WPF.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-209">Starting with the .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="9e9cd-210">Jsou nyní viditelné při <xref:System.Windows.SystemParameters.HighContrast%2A> je nastavený.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-210">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="9e9cd-211">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-211">These include:</span></span>

- <span data-ttu-id="9e9cd-212"><xref:System.Windows.Controls.Expander> Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="9e9cd-212"><xref:System.Windows.Controls.Expander> control</span></span>

    <span data-ttu-id="9e9cd-213">Visual pro zaměření <xref:System.Windows.Controls.Expander> je nyní ovládací prvek viditelný.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-213">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="9e9cd-214">Vizuály klávesnice pro <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, a <xref:System.Windows.Controls.RadioButton> ovládací prvky jsou také viditelné.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-214">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="9e9cd-215">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-215">For example:</span></span>

    <span data-ttu-id="9e9cd-216">Před:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-216">Before:</span></span> 

    ![Rozšíření – ovládací prvek s fokusem před vylepšení přístupnosti](media/expander-before.png)

    <span data-ttu-id="9e9cd-218">Po:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-218">After:</span></span> 

    ![Rozšíření – ovládací prvek s fokusem po vylepšení přístupnosti](media/expander-after.png)

- <span data-ttu-id="9e9cd-220"><xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.RadioButton> ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="9e9cd-220"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

    <span data-ttu-id="9e9cd-221">Text <xref:System.Windows.Controls.CheckBox> a <xref:System.Windows.Controls.RadioButton> ovládacích prvků je teď snazší zjistit při výběru v vysokokontrastních motivech.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-221">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="9e9cd-222">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-222">For example:</span></span>

    <span data-ttu-id="9e9cd-223">Před:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-223">Before:</span></span> 

    ![Vysoký kontrast – přepínač s fokusem před vylepšení přístupnosti](media/radio-button-before.png)

    <span data-ttu-id="9e9cd-225">Po:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-225">After:</span></span> 

    ![Vysoký kontrast – přepínač s fokusem po vylepšení přístupnosti](media/radio-button-after.png)

- <span data-ttu-id="9e9cd-227"><xref:System.Windows.Controls.ComboBox> Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="9e9cd-227"><xref:System.Windows.Controls.ComboBox> control</span></span>

    <span data-ttu-id="9e9cd-228">Od verze rozhraní .NET Framework 4.7.1, ohraničení zakázané <xref:System.Windows.Controls.ComboBox> ovládací prvek se stejnou barvu jako neaktivního textu.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-228">Starting with the .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="9e9cd-229">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-229">For example:</span></span>

    <span data-ttu-id="9e9cd-230">Před:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-230">Before:</span></span> 

     ![Pole se seznamem zakázané ohraničení a text před vylepšení přístupnosti](media/combo-disabled-before.png)

    <span data-ttu-id="9e9cd-232">Po:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-232">After:</span></span>   

     ![Pole se seznamem zakázané ohraničení a text po vylepšení přístupnosti](media/combo-disabled-after.png)

    <span data-ttu-id="9e9cd-234">Kromě toho tlačítka zakázáno a zaměřují se používají Barva motivu správné.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-234">In addition, disabled and focused buttons use the correct theme color.</span></span>

    <span data-ttu-id="9e9cd-235">Před:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-235">Before:</span></span>

    ![Tlačítko barvy motivu před vylepšení přístupnosti](media/button-themes-before.png) 

    <span data-ttu-id="9e9cd-237">Po:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-237">After:</span></span> 

    ![Tlačítko barvy motivu po vylepšení přístupnosti](media/button-themes-after.png) 

    <span data-ttu-id="9e9cd-239">Nakonec v rozhraní .NET Framework 4.7 a předchozími verzemi, nastavení <xref:System.Windows.Controls.ComboBox> stylu ovládacího prvku na `Toolbar.ComboBoxStyleKey` způsobila na šipku rozevíracího seznamu byla neviditelná.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-239">Finally, in the .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="9e9cd-240">Tento problém vyřešen, od verze rozhraní .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-240">This issue is fixed starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="9e9cd-241">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-241">For example:</span></span>

    <span data-ttu-id="9e9cd-242">Před:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-242">Before:</span></span> 

    ![Toolbar.ComboBoxStyleKey před vylepšení přístupnosti](media/comboboxstylekey-before.png) 

    <span data-ttu-id="9e9cd-244">Po:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-244">After:</span></span> 

    ![Toolbar.ComboBoxStyleKey po vylepšení přístupnosti](media/comboboxstylekey-after.png) 

- <span data-ttu-id="9e9cd-246"><xref:System.Windows.Controls.DataGrid> Ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="9e9cd-246"><xref:System.Windows.Controls.DataGrid> control</span></span>

    <span data-ttu-id="9e9cd-247">Od verze rozhraní .NET Framework 4.7.1, šipku indikátor řazení v <xref:System.Windows.Controls.DataGrid> řídí teď používá opravte barvy motivu.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-247">Starting with the .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="9e9cd-248">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-248">For example:</span></span>

    <span data-ttu-id="9e9cd-249">Před:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-249">Before:</span></span> 

    ![Šipka řazení před vylepšení přístupnosti](media/sort-indicator-before.png) 

    <span data-ttu-id="9e9cd-251">Po:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-251">After:</span></span>   

    ![Řazení šipka po vylepšení přístupnosti](media/sort-indicator-after.png) 

    <span data-ttu-id="9e9cd-253">Kromě toho v rozhraní .NET Framework 4.7 a dřívějších verzích výchozí styl odkaz změnit k nesprávné barvě po pozastavení ukazatele myši v režimu vysokého kontrastu.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-253">In addition, in the .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="9e9cd-254">Tento problém nevyřeší, od verze rozhraní .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-254">This is resolved starting with the .NET Framework 4.7.1.</span></span> <span data-ttu-id="9e9cd-255">Obdobně <xref:System.Windows.Controls.DataGrid> sloupce zaškrtávací políčko používá očekávané barvy pro zpětnou vazbu fokus klávesnice, která je od verze rozhraní .NET Framework 4.7.1.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-255">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with the .NET Framework 4.7.1.</span></span>

    <span data-ttu-id="9e9cd-256">Před:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-256">Before:</span></span> 

    ![DataGrid – výchozí odkaz styl před vylepšení přístupnosti](media/default-link-style-before.png) 

    <span data-ttu-id="9e9cd-258">Po:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-258">After:</span></span>    

    ![DataGrid – výchozí odkaz styl po vylepšení přístupnosti](media/default-link-style-after.png) 

<span data-ttu-id="9e9cd-260">Další informace o vylepšení přístupnosti WPF v rozhraní .NET Framework 4.7.1 najdete v tématu [vylepšení přístupnosti v subsystému WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="9e9cd-260">For more information on WPF accessibility improvements in the .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="9e9cd-261">Vylepšení přístupnosti Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9e9cd-261">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="9e9cd-262">V rozhraní .NET Framework 4.7.1 Windows Forms (WinForms) zahrnuje usnadnění změny v následujících oblastech.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-262">In the .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="9e9cd-263">**Vylepšené zobrazení v režim s vysokým kontrastem**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-263">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="9e9cd-264">Od verze rozhraní .NET Framework 4.7.1, různých ovládacích prvků WinForms nabízí vylepšené vykreslování v režimech funkce Vysoký kontrast v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-264">Starting with the .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="9e9cd-265">Windows 10 došlo ke změně hodnoty pro některé vysoký kontrast – barvy system a Windows Forms je založená na platformě Windows 10 Win32.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-265">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="9e9cd-266">Pro dosažení co nejlepších výsledků spusťte na nejnovější verzi Windows a vyjádřit výslovný souhlas s nejnovějšími změnami operačního systému tak, že přidáte soubor app.manifest v aplikaci test a zrušení comment Windows 10 nepodporují řádku operačního systému tak, aby následující:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-266">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

<span data-ttu-id="9e9cd-267">Mezi příklady vysoký kontrast – změny patří:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-267">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="9e9cd-268">Značek zaškrtnutí v <xref:System.Windows.Forms.MenuStrip> položky jsou usnadňuje zobrazení.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-268">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="9e9cd-269">Pokud je vybráno, zakázané <xref:System.Windows.Forms.MenuStrip> položky jsou usnadňuje zobrazení.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-269">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="9e9cd-270">Text ve vybrané <xref:System.Windows.Forms.Button> řídit liší od tradičnější barvu výběru.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-270">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="9e9cd-271">Neaktivní text je lépe čitelný.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-271">Disabled text is easier to read.</span></span> <span data-ttu-id="9e9cd-272">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-272">For example:</span></span>

    <span data-ttu-id="9e9cd-273">Před:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-273">Before:</span></span>

    ![Neaktivní text před vylepšení přístupnosti](media/wf-disabled-before.png) 

    <span data-ttu-id="9e9cd-275">Po:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-275">After:</span></span>

    ![Neaktivní text po vylepšení přístupnosti](media/wf-disabled-after.png) 

- <span data-ttu-id="9e9cd-277">Vysoký kontrast – vylepšení v dialogovém okně výjimky vlákna.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-277">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="9e9cd-278">**Vylepšená podpora Předčítání**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-278">**Improved Narrator support**</span></span>

<span data-ttu-id="9e9cd-279">Windows Forms v rozhraní .NET Framework 4.7.1 zahrnuje následující vylepšení přístupnosti Narrator:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-279">Windows Forms in the .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="9e9cd-280"><xref:System.Windows.Forms.MonthCalendar> Ovládací prvek je přístupný podle program Předčítání, a další nástroje pro automatizaci uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-280">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="9e9cd-281"><xref:System.Windows.Forms.CheckedListBox> Ovládací prvek upozorní Předčítání při změně stavu zaškrtnutí položky tak, že se uživatel dozví, že jste se změnil hodnotu ovládacího prvku položky seznamu.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-281">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="9e9cd-282"><xref:System.Windows.Forms.DataGridViewCell> Ovládací prvek sestavy Předčítání správný stav jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-282">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="9e9cd-283">Program Předčítání teď dokáže číst zakázáno <xref:System.Windows.Forms.ToolStripMenuItem> text, zatímco dříve by přeskočit prostřednictvím položky nabídky zakázané.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-283">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="9e9cd-284">**Vylepšená podpora pro vlastnosti UIAutomation usnadnění vzory**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-284">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="9e9cd-285">Od verze rozhraní .NET Framework 4.7.1, můžou využívat technologie usnadnění vývoje sofwaru bez běžných vzorů pro usnadnění rozhraní API a vlastnosti pro několik ovládacích prvků WinForms.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-285">Starting with the .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="9e9cd-286">Vylepšení usnadnění přístupu patří:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-286">These accessibility improvements include:</span></span>

- <span data-ttu-id="9e9cd-287"><xref:System.Windows.Forms.ComboBox> a <xref:System.Windows.Forms.ToolStripSplitButton> teď podporují [Rozbalit/sbalit vzor](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="9e9cd-287">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="9e9cd-288"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> Teď podporuje [vzoru přepínání](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="9e9cd-288">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="9e9cd-289"><xref:System.Windows.Forms.ToolStripItem> Podporuje ovládací prvek <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> vlastnost a [Rozbalit/sbalit vzor](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="9e9cd-289">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="9e9cd-290"><xref:System.Windows.Forms.NumericUpDown> a <xref:System.Windows.Forms.DomainUpDown> řídí podporu <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-290">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="9e9cd-291">**Vylepšené vlastnost prohlížeče prostředí**</span><span class="sxs-lookup"><span data-stu-id="9e9cd-291">**Improved property browser experience**</span></span>

<span data-ttu-id="9e9cd-292">Od verze rozhraní .NET Framework 4.7.1, Windows Forms obsahuje:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-292">Starting with the .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="9e9cd-293">Lepší navigaci pomocí klávesnice prostřednictvím různých windows rozevíracího seznamu výběru.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-293">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="9e9cd-294">Snížení zbytečné tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-294">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="9e9cd-295">Lepší vytváření sestav, typů ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-295">Better reporting of control types.</span></span>
- <span data-ttu-id="9e9cd-296">Vylepšené Předčítání chování.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-296">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="9e9cd-297">Webové ovládací prvky ASP.NET</span><span class="sxs-lookup"><span data-stu-id="9e9cd-297">ASP.NET web controls</span></span>

<span data-ttu-id="9e9cd-298">Od verze rozhraní .NET Framework 4.7.1 a Visual Studio 2017 15.3, ASP.NET zlepšuje, jak fungují ovládací prvky technologie ASP.NET webové technologie usnadnění v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-298">Starting with the .NET Framework 4.7.1 and Visual Studio 2017 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="9e9cd-299">Změny patří:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-299">Changes include the following:</span></span>

- <span data-ttu-id="9e9cd-300">Změny pro implementaci chybějící vzory usnadnění přístupu uživatelského rozhraní v ovládacích prvcích, jako je třeba **přidat pole** dialogového okna v **zobrazení podrobností o** průvodce, nebo **konfigurace ListView** dialogové okno **ListView** průvodce.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-300">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="9e9cd-301">Změny s cílem zobrazit v režimu vysokého kontrastu, jako je třeba **Editor pole stránkování dat**.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-301">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="9e9cd-302">Změny pro zlepšení navigace klávesnice, prostředí pro ovládací prvky, jako je třeba **pole** dialogového okna v **úpravy polí stránkování** průvodce ovládací prvek DataPager **Konfigurovat ObjectContext**  dialogového okna, nebo **Konfigurovat výběr dat** dialogové okno **konfigurace zdroje dat** průvodce.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-302">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="9e9cd-303">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="9e9cd-303">.NET SDK Tools</span></span>

<span data-ttu-id="9e9cd-304">[Nástroj Configuration Editor (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) a [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) byly vylepšeny opravou různých usnadnění.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-304">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="9e9cd-305">Většina z nich byly malé problémy, jako je název nedefinují nebo určité vzory pro automatizaci uživatelského rozhraní nebyl správně implementována.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-305">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="9e9cd-306">Přestože mnoho uživatelů nebude vědět o těchto nesprávné hodnoty, zákazníci, kteří používají podpůrnou technologií, jako je čtečky obrazovky najdete tyto sady SDK nástroje přístupnější.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-306">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="9e9cd-307">Tato vylepšení změnit některé předchozí chování, jako je například pořadí fokus klávesnice.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-307">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="9e9cd-308">Windows Workflow Foundation (WF), návrháře postupu provádění</span><span class="sxs-lookup"><span data-stu-id="9e9cd-308">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="9e9cd-309">Usnadnění změny v Návrháři postupu provádění, patří:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-309">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="9e9cd-310">Změní pořadí zleva doprava a shora dolů v některé ovládací prvky:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-310">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="9e9cd-311">Okno Inicializace korelace pro korelaci dat pro nastavení <xref:System.ServiceModel.Activities.InitializeCorrelation> aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-311">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="9e9cd-312">V okně Definice obsahu <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, a <xref:System.ServiceModel.Activities.ReceiveReply> aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-312">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="9e9cd-313">Další funkce jsou k dispozici prostřednictvím klávesnice:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-313">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="9e9cd-314">Při úpravě vlastností aktivity, skupiny vlastností můžete sbalit pomocí klávesnice, zaměřuje prvním.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-314">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="9e9cd-315">Varovné ikony jsou přístupné pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-315">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="9e9cd-316">**Více vlastností** tlačítko **vlastnosti** okno přístupný pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-316">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="9e9cd-317">Uživatelé klávesnice můžete přistupovat k položky hlavičky v **argumenty** a **proměnné** podoken návrháře postupu provádění.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-317">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="9e9cd-318">Vylepšená viditelnost položek s fokusem, jako např. kdy:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-318">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="9e9cd-319">Přidání řádků do datových mřížek používají návrháři návrháře pracovních postupů a aktivit.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-319">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="9e9cd-320">Procházíte polí <xref:System.ServiceModel.Activities.ReceiveReply> a <xref:System.ServiceModel.Activities.SendReply> aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-320">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="9e9cd-321">Nastavení výchozích hodnot proměnných nebo argumentů</span><span class="sxs-lookup"><span data-stu-id="9e9cd-321">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="9e9cd-322">Čtečky obrazovky nyní správně rozpozná:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-322">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="9e9cd-323">Zarážky nastavené v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-323">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="9e9cd-324"><xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, A <xref:System.ServiceModel.Activities.CorrelationScope> aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-324">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="9e9cd-325">Obsah <xref:System.ServiceModel.Activities.Receive> aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-325">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="9e9cd-326">Cílový typ pro <xref:System.Activities.Statements.InvokeMethod> aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-326">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="9e9cd-327">Pole se seznamem výjimek a nakonec v části <xref:System.Activities.Statements.TryCatch> aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-327">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="9e9cd-328">Pole se seznamem typ zprávy, rozdělovač v okně Přidat inicializátory korelace, okno Definice obsahu a okno definice vlastnosti CorrelatesOn v zasílání zpráv aktivity (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, a <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="9e9cd-328">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="9e9cd-329">Stavový stroj přechody a přechody cíle.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-329">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="9e9cd-330">Poznámky a konektory na <xref:System.Activities.Statements.FlowDecision> aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-330">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="9e9cd-331">(Klikněte pravým tlačítkem) kontextové nabídky pro aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-331">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="9e9cd-332">Do editorů hodnot vlastnost, tlačítko Vymazat hledání, podle kategorie a tlačítka abecední řazení a dialogové okno Editor výrazů v mřížce vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-332">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="9e9cd-333">Procento zvětšení v Návrháři pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-333">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="9e9cd-334">Oddělovač v <xref:System.Activities.Statements.Parallel> a <xref:System.Activities.Statements.Pick> aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-334">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="9e9cd-335"><xref:System.Activities.Statements.InvokeDelegate> Aktivity.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-335">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="9e9cd-336">V okně vyberte typy aktivit slovník (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`atd.).</span><span class="sxs-lookup"><span data-stu-id="9e9cd-336">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="9e9cd-337">Okno Procházet a vybrat typ .NET.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-337">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="9e9cd-338">V Návrháři pracovních postupů s popisem cesty.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-338">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="9e9cd-339">Uživatelé, kteří se rozhodnou vysoký kontrast – motivy uvidí řady vylepšení v zobrazení návrháře pracovních postupů a jeho ovládacích prvků, jako je lepší kontrastní poměr mezi elementy a snadněji postřehnutelné zaškrtávacími políčky použitých pro elementy fokus.</span><span class="sxs-lookup"><span data-stu-id="9e9cd-339">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e9cd-340">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e9cd-340">See also</span></span>

- [<span data-ttu-id="9e9cd-341">Co je nového v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9e9cd-341">What's new in the .NET Framework</span></span>](whats-new.md)
