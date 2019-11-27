---
title: Přehled vlastností automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 2f96f3c7261882af58cd10038d729c4e723d6fa0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447952"
---
# <a name="ui-automation-properties-overview"></a><span data-ttu-id="a9aa4-102">Přehled vlastností automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9aa4-102">UI Automation Properties Overview</span></span>
> [!NOTE]
> <span data-ttu-id="a9aa4-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="a9aa4-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="a9aa4-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="a9aa4-105">Zprostředkovatelé automatizace uživatelského rozhraní zveřejňují vlastnosti pro prvky [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a9aa4-105">UI Automation providers expose properties on [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements.</span></span> <span data-ttu-id="a9aa4-106">Tyto vlastnosti umožňují klientským aplikacím automatizace uživatelského rozhraní zjišťovat informace o částech [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], zejména ovládací prvky, včetně statických i dynamických dat.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-106">These properties enable UI Automation client applications to discover information about pieces of the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], especially controls, including both static and dynamic data.</span></span>  
  
 <span data-ttu-id="a9aa4-107">V této části najdete obsáhlý přehled [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]ch vlastností.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-107">This section gives a broad overview of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] properties.</span></span> <span data-ttu-id="a9aa4-108">Konkrétnější informace jsou uvedeny v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="a9aa4-108">More specific information is given in the following topics:</span></span>  
  
- [<span data-ttu-id="a9aa4-109">Vlastnosti automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="a9aa4-109">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)  
  
- [<span data-ttu-id="a9aa4-110">Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru</span><span class="sxs-lookup"><span data-stu-id="a9aa4-110">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>   
## <a name="property-identifiers"></a><span data-ttu-id="a9aa4-111">Identifikátory vlastností</span><span class="sxs-lookup"><span data-stu-id="a9aa4-111">Property Identifiers</span></span>  
 <span data-ttu-id="a9aa4-112">Každá vlastnost je identifikována číslem a názvem.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-112">Every property is identified by a number and a name.</span></span> <span data-ttu-id="a9aa4-113">Názvy vlastností jsou používány pouze pro ladění a diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-113">The names of properties are used only for debugging and diagnosis.</span></span> <span data-ttu-id="a9aa4-114">Poskytovatelé používají číselná ID k identifikaci příchozích požadavků na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-114">Providers use the numeric IDs to identify incoming property requests.</span></span> <span data-ttu-id="a9aa4-115">Klientské aplikace však používají pouze <xref:System.Windows.Automation.AutomationProperty>, které zapouzdřují číslo a název pro identifikaci vlastností, které chtějí načíst.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-115">Client applications, however, only use <xref:System.Windows.Automation.AutomationProperty>, which encapsulates the number and name, to identify properties they wish to retrieve.</span></span>  
  
 <span data-ttu-id="a9aa4-116">objekty <xref:System.Windows.Automation.AutomationProperty> reprezentující konkrétní vlastnosti jsou k dispozici jako pole v různých třídách.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-116"><xref:System.Windows.Automation.AutomationProperty> objects representing particular properties are available as fields in various classes.</span></span> <span data-ttu-id="a9aa4-117">Z bezpečnostních důvodů poskytovatelé automatizace uživatelského rozhraní získávají tyto objekty ze samostatné sady tříd, které jsou obsaženy v knihovně UIAutomationTypes. dll.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-117">For security reasons, UI Automation providers obtain these objects from a separate set of classes that are contained in Uiautomationtypes.dll.</span></span>  
  
 <span data-ttu-id="a9aa4-118">V následující tabulce jsou vlastnosti třídy, které obsahují ID <xref:System.Windows.Automation.AutomationProperty>.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-118">The following table categorizes properties by the classes that contain the <xref:System.Windows.Automation.AutomationProperty>IDs.</span></span>  
  
|<span data-ttu-id="a9aa4-119">Typy vlastností</span><span class="sxs-lookup"><span data-stu-id="a9aa4-119">Kinds of properties</span></span>|<span data-ttu-id="a9aa4-120">Klienti získávají ID z</span><span class="sxs-lookup"><span data-stu-id="a9aa4-120">Clients get IDs from</span></span>|<span data-ttu-id="a9aa4-121">Poskytovatelé získají ID z</span><span class="sxs-lookup"><span data-stu-id="a9aa4-121">Providers get IDs from</span></span>|  
|-------------------------|--------------------------|----------------------------|  
|<span data-ttu-id="a9aa4-122">Vlastnosti společné pro všechny elementy (viz následující tabulky)</span><span class="sxs-lookup"><span data-stu-id="a9aa4-122">Properties common to all elements (see following tables)</span></span>|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|<span data-ttu-id="a9aa4-123">Pozice ukotveného okna</span><span class="sxs-lookup"><span data-stu-id="a9aa4-123">Position of a docking window</span></span>|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|<span data-ttu-id="a9aa4-124">Stav prvku, který lze rozbalit a sbalit</span><span class="sxs-lookup"><span data-stu-id="a9aa4-124">State of an element that can expand and collapse</span></span>|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|<span data-ttu-id="a9aa4-125">Vlastnosti položky v mřížce</span><span class="sxs-lookup"><span data-stu-id="a9aa4-125">Properties of an item in a grid</span></span>|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|<span data-ttu-id="a9aa4-126">Vlastnosti mřížky</span><span class="sxs-lookup"><span data-stu-id="a9aa4-126">Properties of a grid</span></span>|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|<span data-ttu-id="a9aa4-127">Aktuální a podporované zobrazení prvku, který má více zobrazení</span><span class="sxs-lookup"><span data-stu-id="a9aa4-127">Current and supported view of an element that has multiple views</span></span>|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|<span data-ttu-id="a9aa4-128">Vlastnosti prvku, který se přesouvá nad určitou škálou hodnot, jako je například posuvník</span><span class="sxs-lookup"><span data-stu-id="a9aa4-128">Properties of an element that moves over a range of values, such as a slider</span></span>|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|<span data-ttu-id="a9aa4-129">Vlastnosti okna posouvání</span><span class="sxs-lookup"><span data-stu-id="a9aa4-129">Properties of a scrolling window</span></span>|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|<span data-ttu-id="a9aa4-130">Stav a kontejner položky, kterou lze vybrat, jako v seznamu</span><span class="sxs-lookup"><span data-stu-id="a9aa4-130">Status and container of an item that can be selected, as in a list</span></span>|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|<span data-ttu-id="a9aa4-131">Vlastnosti ovládacího prvku, který obsahuje položky výběru</span><span class="sxs-lookup"><span data-stu-id="a9aa4-131">Properties of a control that contains selection items</span></span>|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|<span data-ttu-id="a9aa4-132">Záhlaví sloupců a řádků položky v tabulce</span><span class="sxs-lookup"><span data-stu-id="a9aa4-132">Column and row headers of an item in a table</span></span>|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|<span data-ttu-id="a9aa4-133">Záhlaví sloupců a řádků a orientace tabulky</span><span class="sxs-lookup"><span data-stu-id="a9aa4-133">Column and row headers, and orientation, of a table</span></span>|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|<span data-ttu-id="a9aa4-134">Stav ovládacího prvku přepínací tlačítko</span><span class="sxs-lookup"><span data-stu-id="a9aa4-134">State of a toggle control</span></span>|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|<span data-ttu-id="a9aa4-135">Schopnosti prvku, který lze přesunout, otočit nebo změnit jeho velikost</span><span class="sxs-lookup"><span data-stu-id="a9aa4-135">Capabilities of an element that can be moved, rotated, or resized</span></span>|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|<span data-ttu-id="a9aa4-136">Hodnoty a možnosti čtení a zápisu prvku, který má hodnotu</span><span class="sxs-lookup"><span data-stu-id="a9aa4-136">Value and read/write capabilities of an element that has a value</span></span>|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|<span data-ttu-id="a9aa4-137">Možnosti a stav okna</span><span class="sxs-lookup"><span data-stu-id="a9aa4-137">Capabilities and state of a window</span></span>|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>   
## <a name="properties-by-category"></a><span data-ttu-id="a9aa4-138">Vlastnosti podle kategorie</span><span class="sxs-lookup"><span data-stu-id="a9aa4-138">Properties by Category</span></span>  
 <span data-ttu-id="a9aa4-139">Následující tabulky kategorizují vlastnosti, jejichž ID se nacházejí v <xref:System.Windows.Automation.AutomationElement> a <xref:System.Windows.Automation.AutomationElementIdentifiers>.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-139">The following tables categorize the properties whose IDs are found in <xref:System.Windows.Automation.AutomationElement> and <xref:System.Windows.Automation.AutomationElementIdentifiers>.</span></span> <span data-ttu-id="a9aa4-140">Tyto vlastnosti jsou společné pro všechny ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-140">These properties are common to all controls.</span></span> <span data-ttu-id="a9aa4-141">U všech, ale u některých z nich je pravděpodobně statický po celou dobu životnosti aplikace poskytovatele; Většina dynamických vlastností je přidružená k vzorům ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-141">All but a few of them are likely to be static over the lifetime of the provider application; most dynamic properties are associated with control patterns.</span></span>  
  
 <span data-ttu-id="a9aa4-142">Sloupec **přístup k vlastnosti** obsahuje kromě <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> a <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>všechny další přistupující objekty pro každou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-142">The **Property Access** column lists any other accessors for each property, in addition to <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> and <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span></span> <span data-ttu-id="a9aa4-143">Další informace o získání vlastností v klientské aplikaci najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).</span><span class="sxs-lookup"><span data-stu-id="a9aa4-143">For more information on getting properties in a client application, see [UI Automation Properties for Clients](ui-automation-properties-for-clients.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9aa4-144">Konkrétní informace o jednotlivých vlastnostech získáte pomocí odkazu ve sloupci **přístup k vlastnostem** .</span><span class="sxs-lookup"><span data-stu-id="a9aa4-144">For specific information about each property, follow the link in the **Property Access** column.</span></span>  
  
### <a name="display-characteristics"></a><span data-ttu-id="a9aa4-145">Vlastnosti zobrazení</span><span class="sxs-lookup"><span data-stu-id="a9aa4-145">Display Characteristics</span></span>  
  
|<span data-ttu-id="a9aa4-146">Identifikátor vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9aa4-146">Property identifier</span></span>|<span data-ttu-id="a9aa4-147">Přístup k vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9aa4-147">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|<span data-ttu-id="a9aa4-148">neuvedeno</span><span class="sxs-lookup"><span data-stu-id="a9aa4-148">n/a</span></span>|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a><span data-ttu-id="a9aa4-149">Element Type</span><span class="sxs-lookup"><span data-stu-id="a9aa4-149">Element Type</span></span>  
  
|<span data-ttu-id="a9aa4-150">Identifikátor vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9aa4-150">Property identifier</span></span>|<span data-ttu-id="a9aa4-151">Přístup k vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9aa4-151">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a><span data-ttu-id="a9aa4-152">Identifikace</span><span class="sxs-lookup"><span data-stu-id="a9aa4-152">Identification</span></span>  
  
|<span data-ttu-id="a9aa4-153">Identifikátor vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9aa4-153">Property identifier</span></span>|<span data-ttu-id="a9aa4-154">Přístup k vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9aa4-154">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a><span data-ttu-id="a9aa4-155">Interakce</span><span class="sxs-lookup"><span data-stu-id="a9aa4-155">Interaction</span></span>  
  
|<span data-ttu-id="a9aa4-156">Identifikátor vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9aa4-156">Property identifier</span></span>|<span data-ttu-id="a9aa4-157">Přístup k vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9aa4-157">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a><span data-ttu-id="a9aa4-158">Podpora vzorů</span><span class="sxs-lookup"><span data-stu-id="a9aa4-158">Support for Patterns</span></span>  
  
|<span data-ttu-id="a9aa4-159">Identifikátor vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9aa4-159">Property identifier</span></span>|<span data-ttu-id="a9aa4-160">Přístup k vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9aa4-160">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsDockPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsExpandCollapsePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsGridPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsInvokePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsMultipleViewPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsRangeValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsScrollPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsSelectionPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTableItemPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTablePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTextPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTogglePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsTransformPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsValuePatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsWindowPatternAvailableProperty>|<xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>|  
  
### <a name="miscellaneous"></a><span data-ttu-id="a9aa4-161">Různé</span><span class="sxs-lookup"><span data-stu-id="a9aa4-161">Miscellaneous</span></span>  
  
|<span data-ttu-id="a9aa4-162">Identifikátor vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9aa4-162">Property identifier</span></span>|<span data-ttu-id="a9aa4-163">Přístup k vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a9aa4-163">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>   
## <a name="localization"></a><span data-ttu-id="a9aa4-164">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="a9aa4-164">Localization</span></span>  
 <span data-ttu-id="a9aa4-165">poskytovatelé [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] by měli v jazyce operačního systému prezentovat následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a9aa4-165">[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] providers should present the following properties in the language of the operating system:</span></span>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>   
## <a name="properties-and-events"></a><span data-ttu-id="a9aa4-166">Vlastnosti a události</span><span class="sxs-lookup"><span data-stu-id="a9aa4-166">Properties and Events</span></span>  
 <span data-ttu-id="a9aa4-167">Úzce se na základě vlastností v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pojem události změněné vlastností.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-167">Closely tied in with the properties in [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is the concept of property-changed events.</span></span> <span data-ttu-id="a9aa4-168">U dynamických vlastností klientská aplikace potřebuje způsob, jak zjistit, že došlo ke změně hodnoty vlastnosti, aby mohla aktualizovat svou mezipaměť informací nebo reagovat na nové informace jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-168">For dynamic properties, the client application needs a way to know that a property value has changed, so that it can update its cache of information or react to the new information in some other way.</span></span>  
  
 <span data-ttu-id="a9aa4-169">Poskytovatelé vyvolávají události, když se něco v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] mění.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-169">Providers raise events when something in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] changes.</span></span> <span data-ttu-id="a9aa4-170">Například pokud je zaškrtávací políčko zaškrtnuto nebo vymazáno, událost změněné vlastností je vyvolána implementací vzoru přepínání poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-170">For example, if a check box is selected or cleared, a property-changed event is raised by the provider's implementation of the Toggle pattern.</span></span> <span data-ttu-id="a9aa4-171">Poskytovatelé můžou události vyvolávat selektivně, v závislosti na tom, jestli některý z klientů naslouchá událostem nebo naslouchá konkrétním událostem.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-171">Providers can raise events selectively, depending on whether any clients are listening for events, or listening for specific events.</span></span>  
  
 <span data-ttu-id="a9aa4-172">Ne všechny změny vlastností vyvolávají události; To je zcela až do implementace zprostředkovatele automatizace uživatelského rozhraní pro element.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-172">Not all property changes raise events; that is entirely up to the implementation of the UI Automation provider for the element.</span></span> <span data-ttu-id="a9aa4-173">Například standardní poskytovatelé proxy serverů pro seznamy nevyvolávají událost při změně <xref:System.Windows.Automation.SelectionPattern.SelectionProperty>.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-173">For example, the standard proxy providers for list boxes do not raise an event when the <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> changes.</span></span> <span data-ttu-id="a9aa4-174">V takovém případě musí aplikace naslouchat <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-174">In this case, the application instead must listen for an <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span></span>  
  
 <span data-ttu-id="a9aa4-175">Klienti naslouchají událostem tím, že se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-175">Clients listen for events by subscribing to them.</span></span> <span data-ttu-id="a9aa4-176">Přihlášení k odběru událostí znamená vytvoření metod delegáta, které mohou zpracovávat události, a následné předání metod [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] společně s konkrétními událostmi, které budou řešeny v těchto metodách.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-176">Subscribing to events means creating delegate methods that can handle the events, and then passing the methods to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] along with the specific events that will be dealt with in those methods.</span></span> <span data-ttu-id="a9aa4-177">Pro události změněné vlastností musí klienti implementovat <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="a9aa4-177">For property-changed events in particular, clients must implement <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9aa4-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9aa4-178">See also</span></span>

- [<span data-ttu-id="a9aa4-179">Práce s mezipamětí u klientů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9aa4-179">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
- [<span data-ttu-id="a9aa4-180">Vlastnosti automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="a9aa4-180">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="a9aa4-181">Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru</span><span class="sxs-lookup"><span data-stu-id="a9aa4-181">Server-Side UI Automation Provider Implementation</span></span>](server-side-ui-automation-provider-implementation.md)
- [<span data-ttu-id="a9aa4-182">Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost</span><span class="sxs-lookup"><span data-stu-id="a9aa4-182">Find a UI Automation Element Based on a Property Condition</span></span>](find-a-ui-automation-element-based-on-a-property-condition.md)
- [<span data-ttu-id="a9aa4-183">Vrácení vlastností ze zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9aa4-183">Return Properties from a UI Automation Provider</span></span>](return-properties-from-a-ui-automation-provider.md)
- [<span data-ttu-id="a9aa4-184">Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9aa4-184">Raise Events from a UI Automation Provider</span></span>](raise-events-from-a-ui-automation-provider.md)
