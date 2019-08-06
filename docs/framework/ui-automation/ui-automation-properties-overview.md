---
title: Přehled vlastností automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, properties
- properties, UI Automation
ms.assetid: a6c31d7b-b33e-49b3-b5c1-31a345f9b7c8
ms.openlocfilehash: 0468a2f47b9f270e37ad800b83d70c475cbed2c6
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796623"
---
# <a name="ui-automation-properties-overview"></a><span data-ttu-id="9a9bb-102">Přehled vlastností automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a9bb-102">UI Automation Properties Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="9a9bb-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9a9bb-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="9a9bb-105">Zprostředkovatelé automatizace uživatelského rozhraní zveřejňují vlastnosti u [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elementů.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-105">UI Automation providers expose properties on [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] elements.</span></span> <span data-ttu-id="9a9bb-106">Tyto vlastnosti umožňují klientským aplikacím automatizace uživatelského rozhraní zjišťovat informace o částech [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], zejména o ovládacích prvcích, včetně statických i dynamických dat.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-106">These properties enable UI Automation client applications to discover information about pieces of the [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)], especially controls, including both static and dynamic data.</span></span>  
  
 <span data-ttu-id="9a9bb-107">V této části najdete obsáhlý přehled [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] vlastností.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-107">This section gives a broad overview of [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] properties.</span></span> <span data-ttu-id="9a9bb-108">Konkrétnější informace jsou uvedeny v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="9a9bb-108">More specific information is given in the following topics:</span></span>  
  
- [<span data-ttu-id="9a9bb-109">Vlastnosti automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="9a9bb-109">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
  
- [<span data-ttu-id="9a9bb-110">Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru</span><span class="sxs-lookup"><span data-stu-id="9a9bb-110">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)  
  
<a name="Property_Identifiers"></a>   
## <a name="property-identifiers"></a><span data-ttu-id="9a9bb-111">Identifikátory vlastností</span><span class="sxs-lookup"><span data-stu-id="9a9bb-111">Property Identifiers</span></span>  
 <span data-ttu-id="9a9bb-112">Každá vlastnost je identifikována číslem a názvem.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-112">Every property is identified by a number and a name.</span></span> <span data-ttu-id="9a9bb-113">Názvy vlastností jsou používány pouze pro ladění a diagnostiku.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-113">The names of properties are used only for debugging and diagnosis.</span></span> <span data-ttu-id="9a9bb-114">Poskytovatelé používají číselná ID k identifikaci příchozích požadavků na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-114">Providers use the numeric IDs to identify incoming property requests.</span></span> <span data-ttu-id="9a9bb-115">Klientské aplikace však používají <xref:System.Windows.Automation.AutomationProperty>pouze, které zapouzdřují číslo a název pro identifikaci vlastností, které chtějí načíst.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-115">Client applications, however, only use <xref:System.Windows.Automation.AutomationProperty>, which encapsulates the number and name, to identify properties they wish to retrieve.</span></span>  
  
 <span data-ttu-id="9a9bb-116"><xref:System.Windows.Automation.AutomationProperty>objekty reprezentující konkrétní vlastnosti jsou k dispozici jako pole v různých třídách.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-116"><xref:System.Windows.Automation.AutomationProperty> objects representing particular properties are available as fields in various classes.</span></span> <span data-ttu-id="9a9bb-117">Z bezpečnostních důvodů poskytovatelé automatizace uživatelského rozhraní získávají tyto objekty ze samostatné sady tříd, které jsou obsaženy v knihovně UIAutomationTypes. dll.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-117">For security reasons, UI Automation providers obtain these objects from a separate set of classes that are contained in Uiautomationtypes.dll.</span></span>  
  
 <span data-ttu-id="9a9bb-118">V následující tabulce jsou vlastnosti třídy, které obsahují <xref:System.Windows.Automation.AutomationProperty>ID.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-118">The following table categorizes properties by the classes that contain the <xref:System.Windows.Automation.AutomationProperty>IDs.</span></span>  
  
|<span data-ttu-id="9a9bb-119">Typy vlastností</span><span class="sxs-lookup"><span data-stu-id="9a9bb-119">Kinds of properties</span></span>|<span data-ttu-id="9a9bb-120">Klienti získávají ID z</span><span class="sxs-lookup"><span data-stu-id="9a9bb-120">Clients get IDs from</span></span>|<span data-ttu-id="9a9bb-121">Poskytovatelé získají ID z</span><span class="sxs-lookup"><span data-stu-id="9a9bb-121">Providers get IDs from</span></span>|  
|-------------------------|--------------------------|----------------------------|  
|<span data-ttu-id="9a9bb-122">Vlastnosti společné pro všechny elementy (viz následující tabulky)</span><span class="sxs-lookup"><span data-stu-id="9a9bb-122">Properties common to all elements (see following tables)</span></span>|<xref:System.Windows.Automation.AutomationElement>|<xref:System.Windows.Automation.AutomationElementIdentifiers>|  
|<span data-ttu-id="9a9bb-123">Pozice ukotveného okna</span><span class="sxs-lookup"><span data-stu-id="9a9bb-123">Position of a docking window</span></span>|<xref:System.Windows.Automation.DockPattern>|<xref:System.Windows.Automation.DockPatternIdentifiers>|  
|<span data-ttu-id="9a9bb-124">Stav prvku, který lze rozbalit a sbalit</span><span class="sxs-lookup"><span data-stu-id="9a9bb-124">State of an element that can expand and collapse</span></span>|<xref:System.Windows.Automation.ExpandCollapsePattern>|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers>|  
|<span data-ttu-id="9a9bb-125">Vlastnosti položky v mřížce</span><span class="sxs-lookup"><span data-stu-id="9a9bb-125">Properties of an item in a grid</span></span>|<xref:System.Windows.Automation.GridItemPattern>|<xref:System.Windows.Automation.GridItemPatternIdentifiers>|  
|<span data-ttu-id="9a9bb-126">Vlastnosti mřížky</span><span class="sxs-lookup"><span data-stu-id="9a9bb-126">Properties of a grid</span></span>|<xref:System.Windows.Automation.GridPattern>|<xref:System.Windows.Automation.GridPatternIdentifiers>|  
|<span data-ttu-id="9a9bb-127">Aktuální a podporované zobrazení prvku, který má více zobrazení</span><span class="sxs-lookup"><span data-stu-id="9a9bb-127">Current and supported view of an element that has multiple views</span></span>|<xref:System.Windows.Automation.MultipleViewPattern>|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers>|  
|<span data-ttu-id="9a9bb-128">Vlastnosti prvku, který se přesouvá nad určitou škálou hodnot, jako je například posuvník</span><span class="sxs-lookup"><span data-stu-id="9a9bb-128">Properties of an element that moves over a range of values, such as a slider</span></span>|<xref:System.Windows.Automation.RangeValuePattern>|<xref:System.Windows.Automation.RangeValuePatternIdentifiers>|  
|<span data-ttu-id="9a9bb-129">Vlastnosti okna posouvání</span><span class="sxs-lookup"><span data-stu-id="9a9bb-129">Properties of a scrolling window</span></span>|<xref:System.Windows.Automation.ScrollPattern>|<xref:System.Windows.Automation.ScrollPatternIdentifiers>|  
|<span data-ttu-id="9a9bb-130">Stav a kontejner položky, kterou lze vybrat, jako v seznamu</span><span class="sxs-lookup"><span data-stu-id="9a9bb-130">Status and container of an item that can be selected, as in a list</span></span>|<xref:System.Windows.Automation.SelectionItemPattern>|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers>|  
|<span data-ttu-id="9a9bb-131">Vlastnosti ovládacího prvku, který obsahuje položky výběru</span><span class="sxs-lookup"><span data-stu-id="9a9bb-131">Properties of a control that contains selection items</span></span>|<xref:System.Windows.Automation.SelectionPattern>|<xref:System.Windows.Automation.SelectionPatternIdentifiers>|  
|<span data-ttu-id="9a9bb-132">Záhlaví sloupců a řádků položky v tabulce</span><span class="sxs-lookup"><span data-stu-id="9a9bb-132">Column and row headers of an item in a table</span></span>|<xref:System.Windows.Automation.TableItemPattern>|<xref:System.Windows.Automation.TableItemPatternIdentifiers>|  
|<span data-ttu-id="9a9bb-133">Záhlaví sloupců a řádků a orientace tabulky</span><span class="sxs-lookup"><span data-stu-id="9a9bb-133">Column and row headers, and orientation, of a table</span></span>|<xref:System.Windows.Automation.TablePattern>|<xref:System.Windows.Automation.TablePatternIdentifiers>|  
|<span data-ttu-id="9a9bb-134">Stav ovládacího prvku přepínací tlačítko</span><span class="sxs-lookup"><span data-stu-id="9a9bb-134">State of a toggle control</span></span>|<xref:System.Windows.Automation.TogglePattern>|<xref:System.Windows.Automation.TogglePatternIdentifiers>|  
|<span data-ttu-id="9a9bb-135">Schopnosti prvku, který lze přesunout, otočit nebo změnit jeho velikost</span><span class="sxs-lookup"><span data-stu-id="9a9bb-135">Capabilities of an element that can be moved, rotated, or resized</span></span>|<xref:System.Windows.Automation.TransformPattern>|<xref:System.Windows.Automation.TransformPatternIdentifiers>|  
|<span data-ttu-id="9a9bb-136">Hodnoty a možnosti čtení a zápisu prvku, který má hodnotu</span><span class="sxs-lookup"><span data-stu-id="9a9bb-136">Value and read/write capabilities of an element that has a value</span></span>|<xref:System.Windows.Automation.ValuePattern>|<xref:System.Windows.Automation.ValuePatternIdentifiers>|  
|<span data-ttu-id="9a9bb-137">Možnosti a stav okna</span><span class="sxs-lookup"><span data-stu-id="9a9bb-137">Capabilities and state of a window</span></span>|<xref:System.Windows.Automation.WindowPattern>|<xref:System.Windows.Automation.WindowPatternIdentifiers>|  
  
<a name="Properties_by_Category"></a>   
## <a name="properties-by-category"></a><span data-ttu-id="9a9bb-138">Vlastnosti podle kategorie</span><span class="sxs-lookup"><span data-stu-id="9a9bb-138">Properties by Category</span></span>  
 <span data-ttu-id="9a9bb-139">Následující tabulky kategorizují vlastnosti, jejichž identifikátory se nacházejí v <xref:System.Windows.Automation.AutomationElement> a. <xref:System.Windows.Automation.AutomationElementIdentifiers></span><span class="sxs-lookup"><span data-stu-id="9a9bb-139">The following tables categorize the properties whose IDs are found in <xref:System.Windows.Automation.AutomationElement> and <xref:System.Windows.Automation.AutomationElementIdentifiers>.</span></span> <span data-ttu-id="9a9bb-140">Tyto vlastnosti jsou společné pro všechny ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-140">These properties are common to all controls.</span></span> <span data-ttu-id="9a9bb-141">U všech, ale u některých z nich je pravděpodobně statický po celou dobu životnosti aplikace poskytovatele; Většina dynamických vlastností je přidružená k vzorům ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-141">All but a few of them are likely to be static over the lifetime of the provider application; most dynamic properties are associated with control patterns.</span></span>  
  
 <span data-ttu-id="9a9bb-142">Sloupec pro **přístup k vlastnostem** uvádí všechny další přistupující objekty pro každou vlastnost, kromě <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> a <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-142">The **Property Access** column lists any other accessors for each property, in addition to <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> and <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>.</span></span> <span data-ttu-id="9a9bb-143">Další informace o získání vlastností v klientské aplikaci najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).</span><span class="sxs-lookup"><span data-stu-id="9a9bb-143">For more information on getting properties in a client application, see [UI Automation Properties for Clients](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9a9bb-144">Konkrétní informace o jednotlivých vlastnostech získáte pomocí odkazu ve sloupci **přístup k vlastnostem** .</span><span class="sxs-lookup"><span data-stu-id="9a9bb-144">For specific information about each property, follow the link in the **Property Access** column.</span></span>  
  
### <a name="display-characteristics"></a><span data-ttu-id="9a9bb-145">Vlastnosti zobrazení</span><span class="sxs-lookup"><span data-stu-id="9a9bb-145">Display Characteristics</span></span>  
  
|<span data-ttu-id="9a9bb-146">Identifikátor vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9a9bb-146">Property identifier</span></span>|<span data-ttu-id="9a9bb-147">Přístup k vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9a9bb-147">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.BoundingRectangle%2A>|  
|<xref:System.Windows.Automation.AutomationElement.CultureProperty>|<span data-ttu-id="9a9bb-148">není k dispozici</span><span class="sxs-lookup"><span data-stu-id="9a9bb-148">n/a</span></span>|  
|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HelpText%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsOffscreen%2A>|  
|<xref:System.Windows.Automation.AutomationElement.OrientationProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Orientation%2A>|  
  
### <a name="element-type"></a><span data-ttu-id="9a9bb-149">Element Type</span><span class="sxs-lookup"><span data-stu-id="9a9bb-149">Element Type</span></span>  
  
|<span data-ttu-id="9a9bb-150">Identifikátor vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9a9bb-150">Property identifier</span></span>|<span data-ttu-id="9a9bb-151">Přístup k vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9a9bb-151">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsContentElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsContentElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsControlElementProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsControlElement%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemType%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LocalizedControlType%2A>|  
  
### <a name="identification"></a><span data-ttu-id="9a9bb-152">Identifikace</span><span class="sxs-lookup"><span data-stu-id="9a9bb-152">Identification</span></span>  
  
|<span data-ttu-id="9a9bb-153">Identifikátor vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9a9bb-153">Property identifier</span></span>|<span data-ttu-id="9a9bb-154">Přístup k vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9a9bb-154">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AutomationIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AutomationId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClassNameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ClassName%2A>|  
|<xref:System.Windows.Automation.AutomationElement.FrameworkIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.FrameworkId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.LabeledByProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.LabeledBy%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NameProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ProcessIdProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ProcessId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.RuntimeIdProperty>|<xref:System.Windows.Automation.AutomationElement.GetRuntimeId%2A>|  
|<xref:System.Windows.Automation.AutomationElement.NativeWindowHandleProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.NativeWindowHandle%2A>|  
  
### <a name="interaction"></a><span data-ttu-id="9a9bb-155">Interakce</span><span class="sxs-lookup"><span data-stu-id="9a9bb-155">Interaction</span></span>  
  
|<span data-ttu-id="9a9bb-156">Identifikátor vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9a9bb-156">Property identifier</span></span>|<span data-ttu-id="9a9bb-157">Přístup k vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9a9bb-157">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AcceleratorKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.AccessKey%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ClickablePointProperty>|<xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A>|  
|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.HasKeyboardFocus%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsEnabled%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsKeyboardFocusable%2A>|  
  
### <a name="support-for-patterns"></a><span data-ttu-id="9a9bb-158">Podpora vzorů</span><span class="sxs-lookup"><span data-stu-id="9a9bb-158">Support for Patterns</span></span>  
  
|<span data-ttu-id="9a9bb-159">Identifikátor vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9a9bb-159">Property identifier</span></span>|<span data-ttu-id="9a9bb-160">Přístup k vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9a9bb-160">Property access</span></span>|  
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
  
### <a name="miscellaneous"></a><span data-ttu-id="9a9bb-161">Různé</span><span class="sxs-lookup"><span data-stu-id="9a9bb-161">Miscellaneous</span></span>  
  
|<span data-ttu-id="9a9bb-162">Identifikátor vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9a9bb-162">Property identifier</span></span>|<span data-ttu-id="9a9bb-163">Přístup k vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9a9bb-163">Property access</span></span>|  
|-------------------------|---------------------|  
|<xref:System.Windows.Automation.AutomationElement.IsRequiredForFormProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsRequiredForForm%2A>|  
|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.IsPassword%2A>|  
|<xref:System.Windows.Automation.AutomationElement.ItemStatusProperty>|<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ItemStatus%2A>|  
  
<a name="Localization"></a>   
## <a name="localization"></a><span data-ttu-id="9a9bb-164">Lokalizace</span><span class="sxs-lookup"><span data-stu-id="9a9bb-164">Localization</span></span>  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]<span data-ttu-id="9a9bb-165">Poskytovatelé by měli v jazyce operačního systému zobrazit následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="9a9bb-165">providers should present the following properties in the language of the operating system:</span></span>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>  
  
- <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>  
  
<a name="Properties_and_Events"></a>   
## <a name="properties-and-events"></a><span data-ttu-id="9a9bb-166">Vlastnosti a události</span><span class="sxs-lookup"><span data-stu-id="9a9bb-166">Properties and Events</span></span>  
 <span data-ttu-id="9a9bb-167">Úzce svázané v rámci s vlastnostmi v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nástroji je koncept událostí změněných vlastností.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-167">Closely tied in with the properties in [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] is the concept of property-changed events.</span></span> <span data-ttu-id="9a9bb-168">U dynamických vlastností klientská aplikace potřebuje způsob, jak zjistit, že došlo ke změně hodnoty vlastnosti, aby mohla aktualizovat svou mezipaměť informací nebo reagovat na nové informace jiným způsobem.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-168">For dynamic properties, the client application needs a way to know that a property value has changed, so that it can update its cache of information or react to the new information in some other way.</span></span>  
  
 <span data-ttu-id="9a9bb-169">Poskytovatelé vyvolávají události, když se [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] něco změní.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-169">Providers raise events when something in the [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] changes.</span></span> <span data-ttu-id="9a9bb-170">Například pokud je zaškrtávací políčko zaškrtnuto nebo vymazáno, událost změněné vlastností je vyvolána implementací vzoru přepínání poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-170">For example, if a check box is selected or cleared, a property-changed event is raised by the provider's implementation of the Toggle pattern.</span></span> <span data-ttu-id="9a9bb-171">Poskytovatelé můžou události vyvolávat selektivně, v závislosti na tom, jestli některý z klientů naslouchá událostem nebo naslouchá konkrétním událostem.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-171">Providers can raise events selectively, depending on whether any clients are listening for events, or listening for specific events.</span></span>  
  
 <span data-ttu-id="9a9bb-172">Ne všechny změny vlastností vyvolávají události; To je zcela až do implementace zprostředkovatele automatizace uživatelského rozhraní pro element.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-172">Not all property changes raise events; that is entirely up to the implementation of the UI Automation provider for the element.</span></span> <span data-ttu-id="9a9bb-173">Například standardní poskytovatelé proxy serverů pro seznamy nevyvolávají událost při <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> změnách.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-173">For example, the standard proxy providers for list boxes do not raise an event when the <xref:System.Windows.Automation.SelectionPattern.SelectionProperty> changes.</span></span> <span data-ttu-id="9a9bb-174">V takovém případě musí aplikace naslouchat pro <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-174">In this case, the application instead must listen for an <xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>.</span></span>  
  
 <span data-ttu-id="9a9bb-175">Klienti naslouchají událostem tím, že se přihlásí k odběru.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-175">Clients listen for events by subscribing to them.</span></span> <span data-ttu-id="9a9bb-176">Přihlášení k odběru událostí znamená vytvoření metod delegáta, které mohou zpracovávat události a následně předání metod do [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] spolu s konkrétními událostmi, které budou v těchto metodách řešeny.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-176">Subscribing to events means creating delegate methods that can handle the events, and then passing the methods to [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] along with the specific events that will be dealt with in those methods.</span></span> <span data-ttu-id="9a9bb-177">Pro události změněné vlastností musí být klienti implementované <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="9a9bb-177">For property-changed events in particular, clients must implement <xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a9bb-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a9bb-178">See also</span></span>

- [<span data-ttu-id="9a9bb-179">Práce s mezipamětí u klientů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a9bb-179">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
- [<span data-ttu-id="9a9bb-180">Vlastnosti automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="9a9bb-180">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [<span data-ttu-id="9a9bb-181">Implementace zprostředkovatele automatizace uživatelského rozhraní na straně serveru</span><span class="sxs-lookup"><span data-stu-id="9a9bb-181">Server-Side UI Automation Provider Implementation</span></span>](../../../docs/framework/ui-automation/server-side-ui-automation-provider-implementation.md)
- [<span data-ttu-id="9a9bb-182">Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost</span><span class="sxs-lookup"><span data-stu-id="9a9bb-182">Find a UI Automation Element Based on a Property Condition</span></span>](../../../docs/framework/ui-automation/find-a-ui-automation-element-based-on-a-property-condition.md)
- [<span data-ttu-id="9a9bb-183">Vrácení vlastností ze zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a9bb-183">Return Properties from a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/return-properties-from-a-ui-automation-provider.md)
- [<span data-ttu-id="9a9bb-184">Vyvolávání událostí ze zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a9bb-184">Raise Events from a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/raise-events-from-a-ui-automation-provider.md)
