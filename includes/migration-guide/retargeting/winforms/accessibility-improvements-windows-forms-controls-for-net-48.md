---
ms.openlocfilehash: e528a41748d9353c96d443f68e15e7a98ee7f4ae
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616241"
---
### <a name="accessibility-improvements-in-windows-forms-controls-for-net-48"></a><span data-ttu-id="8f34e-101">Vylepšení usnadnění v ovládacích prvcích model Windows Forms pro .NET 4,8</span><span class="sxs-lookup"><span data-stu-id="8f34e-101">Accessibility improvements in Windows Forms controls for .NET 4.8</span></span>

#### <a name="details"></a><span data-ttu-id="8f34e-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8f34e-102">Details</span></span>

<span data-ttu-id="8f34e-103">Rozhraní model Windows Forms Framework pokračuje v vylepšování toho, jak funguje s technologiemi usnadnění pro lepší podporu model Windows Formsch zákazníků.</span><span class="sxs-lookup"><span data-stu-id="8f34e-103">The Windows Forms Framework is continuing to improve how it works with accessibility technologies to better support Windows Forms customers.</span></span> <span data-ttu-id="8f34e-104">Mezi ně patří tyto změny:</span><span class="sxs-lookup"><span data-stu-id="8f34e-104">These include the following changes:</span></span>

- <span data-ttu-id="8f34e-105">Změny pro zlepšení zobrazení v režimu Vysoký kontrast.</span><span class="sxs-lookup"><span data-stu-id="8f34e-105">Changes to improve display during High Contrast mode.</span></span>
- <span data-ttu-id="8f34e-106">Změny interakce s programem Narrator.</span><span class="sxs-lookup"><span data-stu-id="8f34e-106">Changes to interaction with Narrator.</span></span>
- <span data-ttu-id="8f34e-107">Změny v přístupné hierarchii (Vylepšení navigace prostřednictvím stromu automatizace uživatelského rozhraní).</span><span class="sxs-lookup"><span data-stu-id="8f34e-107">Changes in the Accessible hierarchy (improving navigation through the UI Automation tree).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8f34e-108">Návrh</span><span class="sxs-lookup"><span data-stu-id="8f34e-108">Suggestion</span></span>

<span data-ttu-id="8f34e-109">**Jak vyjádřit nebo odhlásit tyto změny** Aby aplikace mohla tyto změny využívat, musí běžet na .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="8f34e-109">**How to opt in or out of these changes** In order for the application to benefit from these changes, it must run on the .NET Framework 4.8.</span></span> <span data-ttu-id="8f34e-110">Aplikace se může přihlásit k těmto změnám jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="8f34e-110">The application can opt in into these changes in either of the following ways:</span></span>

- <span data-ttu-id="8f34e-111">Zkompiluje se znovu a zacílí na .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="8f34e-111">It is recompiled to target the .NET Framework 4.8.</span></span> <span data-ttu-id="8f34e-112">Tyto změny přístupnosti jsou ve výchozím nastavení povolené v aplikacích model Windows Forms, které cílí na .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="8f34e-112">These accessibility changes are enabled by default on Windows Forms applications that target the .NET Framework 4.8.</span></span>
- <span data-ttu-id="8f34e-113">Cílí na .NET Framework 4.7.2 nebo starší verze a výslovný ze staršího chování přístupnosti přidáním následujícího [přepínače AppContext](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) do `<runtime>` oddílu konfiguračního souboru aplikace a jeho nastavením na `false` , jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="8f34e-113">It targets the .NET Framework 4.7.2 or earlier version and opts out of the legacy accessibility behaviors by adding the following [AppContext switch](https://docs.microsoft.com/dotnet/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element) to the `<runtime>` section of the app config file and setting it to `false`, as the following example shows.</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <startup>
    <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
  </startup>
  <runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
  </runtime>
</configuration>
```

<span data-ttu-id="8f34e-114">Všimněte si, že pokud se chcete přihlásit k funkcím pro usnadnění přidaným v .NET Framework 4,8, musíte také vyjádřit souhlas s funkcemi přístupnosti .NET Framework 4.7.1 a 4.7.2.</span><span class="sxs-lookup"><span data-stu-id="8f34e-114">Note that to opt in to the accessibility features added in .NET Framework 4.8, you must also opt in to accessibility features of .NET Framework 4.7.1 and 4.7.2 as well.</span></span> <span data-ttu-id="8f34e-115">Aplikace, které cílí na .NET Framework 4,8 a chtějí zachovat starší možnosti přístupnosti, se můžou přihlásit k používání starších funkcí pro usnadnění přístupu, a to explicitně nastavením tohoto přepínače AppContext na `true` . Povolení podpory vyvolání popisku klávesnice vyžaduje přidání `Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false` řádku k hodnotě AppContextSwitchOverrides:</span><span class="sxs-lookup"><span data-stu-id="8f34e-115">Applications that target the .NET Framework 4.8 and want to preserve the legacy accessibility behavior can opt in to the use of legacy accessibility features by explicitly setting this AppContext switch to `true`.Enabling the keyboard ToolTip invocation support requires adding the `Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false` line to the AppContextSwitchOverrides value:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false" />
```

<span data-ttu-id="8f34e-116">Upozorňujeme, že povolení této funkce vyžaduje, abyste se při4.7.1I k výše uvedeným funkcím pro usnadnění přístupu .NET Framework 4,8.</span><span class="sxs-lookup"><span data-stu-id="8f34e-116">Note that enabling this feature requires opting in to the aforementioned accessibility features of .NET Framework 4.7.1 - 4.8.</span></span> <span data-ttu-id="8f34e-117">V případě, že se některé funkce přístupnosti nepovolují, ale v nástroji se zobrazí funkce zobrazení popisu, <xref:System.NotSupportedException> vyvolá se při prvním přístupu k těmto funkcím modul runtime.</span><span class="sxs-lookup"><span data-stu-id="8f34e-117">Also, if any of the accessibility features are not opted in but the tooltip display feature is opted in, a runtime <xref:System.NotSupportedException> will be thrown on the first access to these features.</span></span> <span data-ttu-id="8f34e-118">Zpráva o výjimce indikuje, že popisky klávesnice vyžadují, aby byla povolená vylepšení přístupnosti úrovně 3.</span><span class="sxs-lookup"><span data-stu-id="8f34e-118">The exception message indicates that keyboard ToolTips require accessibility improvements of level 3 to be enabled.</span></span>

<span data-ttu-id="8f34e-119">**Použití barev definovaných operačním systémem v motivech Vysoký kontrast**</span><span class="sxs-lookup"><span data-stu-id="8f34e-119">**Use of OS-defined colors in High Contrast themes**</span></span>

- <span data-ttu-id="8f34e-120">Vylepšené motivy s vysokým kontrastem.</span><span class="sxs-lookup"><span data-stu-id="8f34e-120">Improved high-contrast themes.</span></span>

<span data-ttu-id="8f34e-121">**Vylepšená podpora Narrator**</span><span class="sxs-lookup"><span data-stu-id="8f34e-121">**Improved Narrator support**</span></span>

- <span data-ttu-id="8f34e-122">Program Narrator nyní oznamuje směr řazení <xref:System.Windows.Forms.DataGridViewColumn> Při oznamování přístupového názvu a <xref:System.Windows.Forms.DataGridViewCell> .</span><span class="sxs-lookup"><span data-stu-id="8f34e-122">Narrator now announces the sort direction of the <xref:System.Windows.Forms.DataGridViewColumn> when announcing an accessible name of a <xref:System.Windows.Forms.DataGridViewCell>.</span></span>

<span data-ttu-id="8f34e-123">**Vylepšená podpora usnadnění CheckedListBox**</span><span class="sxs-lookup"><span data-stu-id="8f34e-123">**Improved CheckedListBox Accessibility support**</span></span>

- <span data-ttu-id="8f34e-124">Vylepšená podpora Narrator pro <xref:System.Windows.Forms.CheckedListBox> ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="8f34e-124">Improved Narrator support for the <xref:System.Windows.Forms.CheckedListBox> control.</span></span> <span data-ttu-id="8f34e-125">Při přechodu k <xref:System.Windows.Forms.CheckedListBox> ovládacímu prvku pomocí klávesnice se program Narrator zaměřuje na <xref:System.Windows.Forms.CheckedListBox> položku a oznamuje ji.</span><span class="sxs-lookup"><span data-stu-id="8f34e-125">When navigating to the <xref:System.Windows.Forms.CheckedListBox> control using the keyboard, Narrator focuses the <xref:System.Windows.Forms.CheckedListBox> item and announces it.</span></span>
- <span data-ttu-id="8f34e-126">Prázdný ovládací prvek CheckedListBox nyní obsahuje obdélník fokusu pro virtuální první položku, pokud se ovládací prvek změní na fokus.</span><span class="sxs-lookup"><span data-stu-id="8f34e-126">An empty CheckedListBox control now has a focus rectangle drawn for a virtual first item when the control becomes focused.</span></span>

<span data-ttu-id="8f34e-127">**Vylepšená podpora funkce ComboBox**</span><span class="sxs-lookup"><span data-stu-id="8f34e-127">**Improved ComboBox Accessibility support**</span></span>

- <span data-ttu-id="8f34e-128">Povolena Podpora automatizace uživatelského rozhraní pro <xref:System.Windows.Forms.ComboBox> ovládací prvek s možností používat oznámení o automatizaci uživatelského rozhraní a další funkce automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8f34e-128">Enabled UI Automation support for the <xref:System.Windows.Forms.ComboBox> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span>
<span data-ttu-id="8f34e-129">**Vylepšená podpora usnadnění přístupu DataGridView**</span><span class="sxs-lookup"><span data-stu-id="8f34e-129">**Improved DataGridView Accessibility support**</span></span>

- <span data-ttu-id="8f34e-130">Povolená Podpora automatizace uživatelského rozhraní pro <xref:System.Windows.Forms.DataGridView> řízení s možností používat oznámení automatizace uživatelského rozhraní a další funkce automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8f34e-130">Enabled UI Automation support for <xref:System.Windows.Forms.DataGridView> control with ability to use UI Automation notifications and other UI Automation features.</span></span>
- <span data-ttu-id="8f34e-131">Prvek automatizace uživatelského rozhraní, který odpovídá <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> nebo <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> je nyní podřízenosti odpovídající buňky pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="8f34e-131">The UI Automation element which corresponds to the <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl> or <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl> is now a child of corresponding editing cell.</span></span>

<span data-ttu-id="8f34e-132">**Vylepšená podpora usnadnění LinkLabel**</span><span class="sxs-lookup"><span data-stu-id="8f34e-132">**Improved LinkLabel Accessibility support**</span></span>

- <span data-ttu-id="8f34e-133">Vylepšené <xref:System.Windows.Forms.LinkLabel> přístupnost ovládacího prvku: Narrator oznamuje zakázaný stav odkazu, pokud je odpovídající <xref:System.Windows.Forms.LinkLabel> ovládací prvek zakázán.</span><span class="sxs-lookup"><span data-stu-id="8f34e-133">Improved <xref:System.Windows.Forms.LinkLabel> control accessibility: Narrator announces the disabled state for the link if the corresponding <xref:System.Windows.Forms.LinkLabel> control is disabled.</span></span>

<span data-ttu-id="8f34e-134">**Vylepšená podpora funkcí ProgressBar**</span><span class="sxs-lookup"><span data-stu-id="8f34e-134">**Improved ProgressBar Accessibility support**</span></span>

- <span data-ttu-id="8f34e-135">Povolena Podpora automatizace uživatelského rozhraní pro <xref:System.Windows.Forms.ProgressBar> ovládací prvek s možností používat oznámení o automatizaci uživatelského rozhraní a další funkce automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8f34e-135">Enabled UI Automation support for the <xref:System.Windows.Forms.ProgressBar> control with the ability to use UI Automation notifications and other UI Automation features.</span></span> <span data-ttu-id="8f34e-136">Vývojáři teď můžou používat upozornění na automatizaci uživatelského rozhraní, které může program Narrator oznámit, aby označoval průběh.</span><span class="sxs-lookup"><span data-stu-id="8f34e-136">Developers are now able to use UI Automation notifications which Narrator can announce to indicate progress.</span></span>
<span data-ttu-id="8f34e-137">Přehled událostí automatizace uživatelského rozhraní, včetně událostí oznámení automatizace uživatelského rozhraní, najdete v tématu [Přehled událostí automatizace](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-eventsoverview)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8f34e-137">For an overview of UI automation events overview, including UI automation notification events, see the [UI Automation Events Overview](https://docs.microsoft.com/windows/desktop/WinAuto/uiauto-eventsoverview).</span></span>

<span data-ttu-id="8f34e-138">**Vylepšená podpora funkcí PropertyGrid**</span><span class="sxs-lookup"><span data-stu-id="8f34e-138">**Improved PropertyGrid Accessibility support**</span></span>

- <span data-ttu-id="8f34e-139">Povolena Podpora automatizace uživatelského rozhraní pro <xref:System.Windows.Forms.PropertyGrid> ovládací prvek s možností používat oznámení o automatizaci uživatelského rozhraní a další funkce automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8f34e-139">Enabled UI Automation support for the <xref:System.Windows.Forms.PropertyGrid> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span>
- <span data-ttu-id="8f34e-140">Prvek automatizace uživatelského rozhraní, který odpovídá aktuálně upravované vlastnosti, je nyní podřízenou položkou příslušného elementu automatizace uživatelského rozhraní pro položku vlastností.</span><span class="sxs-lookup"><span data-stu-id="8f34e-140">The UI Automation element which corresponds to the currently edited property is now a child of the corresponding property item UI Automation element.</span></span>
- <span data-ttu-id="8f34e-141">Prvek položky vlastnosti automatizace uživatelského rozhraní je nyní podřízenou položkou odpovídajícího prvku kategorie, pokud <xref:System.Windows.Forms.PropertyGrid> je nadřazený ovládací prvek nastaven na zobrazení kategorií.</span><span class="sxs-lookup"><span data-stu-id="8f34e-141">The UI Automation property item element is now a child of the corresponding category element if the parent <xref:System.Windows.Forms.PropertyGrid> control is set to category view.</span></span>

<span data-ttu-id="8f34e-142">**Vylepšená podpora ovládacího prvku ToolStrip**</span><span class="sxs-lookup"><span data-stu-id="8f34e-142">**Improved ToolStrip support**</span></span>

- <span data-ttu-id="8f34e-143">Povolena Podpora automatizace uživatelského rozhraní pro <xref:System.Windows.Forms.ToolStrip> ovládací prvek s možností používat oznámení o automatizaci uživatelského rozhraní a další funkce automatizace uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8f34e-143">Enabled UI Automation support for the <xref:System.Windows.Forms.ToolStrip> control, with the ability to use UI Automation notifications and other UI Automation features.</span></span>
- <span data-ttu-id="8f34e-144">Vylepšená navigace prostřednictvím <xref:System.Windows.Forms.ToolStrip> položek</span><span class="sxs-lookup"><span data-stu-id="8f34e-144">Improved navigation through <xref:System.Windows.Forms.ToolStrip> items.</span></span>
- <span data-ttu-id="8f34e-145">V režimu položek nezmizí fokus Předčítání a nepřejde na skryté položky.</span><span class="sxs-lookup"><span data-stu-id="8f34e-145">In items mode, Narrator focus does not disappear and does not go to hidden items.</span></span>

<span data-ttu-id="8f34e-146">**Vylepšené vizuální pomůcky**</span><span class="sxs-lookup"><span data-stu-id="8f34e-146">**Improved Visual cues**</span></span>

- <span data-ttu-id="8f34e-147">Prázdný <xref:System.Windows.Forms.CheckedListBox> ovládací prvek nyní zobrazuje indikátor fokusu, když dostane fokus.</span><span class="sxs-lookup"><span data-stu-id="8f34e-147">An empty <xref:System.Windows.Forms.CheckedListBox> control now displays a focus indicator when it receives focus.</span></span>
<span data-ttu-id="8f34e-148">Poznámka: Podpora automatizace uživatelského rozhraní je povolená pro ovládací prvky v modulu runtime, ale nepoužívá se v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="8f34e-148">Note: UI automation support is enabled for controls in runtime but is not used in design time.</span></span> <span data-ttu-id="8f34e-149">Přehled automatizace uživatelského rozhraní najdete v tématu [Přehled automatizace uživatelského rozhraní](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).</span><span class="sxs-lookup"><span data-stu-id="8f34e-149">For an overview of UI automation, see the [UI Automation Overview](https://docs.microsoft.com/dotnet/framework/ui-automation/ui-automation-overview).</span></span>

<span data-ttu-id="8f34e-150">**Vyvolání popisů ovládacích prvků pomocí klávesnice**</span><span class="sxs-lookup"><span data-stu-id="8f34e-150">**Invoking controls' ToolTips with a keyboard**</span></span>

- <span data-ttu-id="8f34e-151">Popis ovládacího prvku se teď dá vyvolat tak, že se ovládací prvek vymění pomocí klávesnice.</span><span class="sxs-lookup"><span data-stu-id="8f34e-151">Control tooltip can now be invoked by focusing the control with keyboard.</span></span> <span data-ttu-id="8f34e-152">Tato funkce musí být pro aplikaci explicitně povolená (viz část \*\* &quot; jak tyto změny &quot; výslovně zapnout nebo\*\*vypnout).</span><span class="sxs-lookup"><span data-stu-id="8f34e-152">This feature needs to be enabled explicitly for the application (see section **&quot;How to opt in or out of these changes&quot;**)</span></span>

| <span data-ttu-id="8f34e-153">Name</span><span class="sxs-lookup"><span data-stu-id="8f34e-153">Name</span></span>    | <span data-ttu-id="8f34e-154">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8f34e-154">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8f34e-155">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8f34e-155">Scope</span></span>   | <span data-ttu-id="8f34e-156">Hlavní</span><span class="sxs-lookup"><span data-stu-id="8f34e-156">Major</span></span>       |
| <span data-ttu-id="8f34e-157">Verze</span><span class="sxs-lookup"><span data-stu-id="8f34e-157">Version</span></span> | <span data-ttu-id="8f34e-158">4,8</span><span class="sxs-lookup"><span data-stu-id="8f34e-158">4.8</span></span>         |
| <span data-ttu-id="8f34e-159">Typ</span><span class="sxs-lookup"><span data-stu-id="8f34e-159">Type</span></span>    | <span data-ttu-id="8f34e-160">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="8f34e-160">Retargeting</span></span> |
