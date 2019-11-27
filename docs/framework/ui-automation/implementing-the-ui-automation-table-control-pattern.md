---
title: Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 8e929f181255f6738261533fa3261187ebe3c6ff
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447093"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="7cfa5-102">Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7cfa5-102">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="7cfa5-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="7cfa5-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="7cfa5-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="7cfa5-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="7cfa5-105">Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ITableProvider>, včetně informací o vlastnostech, metodách a událostech.</span><span class="sxs-lookup"><span data-stu-id="7cfa5-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="7cfa5-106">Odkazy na další odkazy jsou uvedeny na konci přehledu.</span><span class="sxs-lookup"><span data-stu-id="7cfa5-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="7cfa5-107">Vzor ovládacího prvku <xref:System.Windows.Automation.TablePattern> slouží k podpoře ovládacích prvků, které fungují jako kontejnery pro kolekci podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="7cfa5-107">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="7cfa5-108">Podřízené objekty tohoto elementu musí implementovat <xref:System.Windows.Automation.Provider.ITableItemProvider> a být uspořádány do dvojrozměrného systému logických souřadnic, který lze procházet podle řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="7cfa5-108">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="7cfa5-109">Tento vzor ovládacích prvků je podobný <xref:System.Windows.Automation.Provider.IGridProvider>, s rozlišením, že jakýkoli ovládací prvek implementující <xref:System.Windows.Automation.Provider.ITableProvider> musí také zveřejnit vztah záhlaví sloupce nebo řádku pro každý podřízený element.</span><span class="sxs-lookup"><span data-stu-id="7cfa5-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="7cfa5-110">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="7cfa5-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="7cfa5-111">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="7cfa5-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="7cfa5-112">Při implementaci vzoru ovládacího prvku tabulka si všimněte následujících pokynů a konvencí:</span><span class="sxs-lookup"><span data-stu-id="7cfa5-112">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="7cfa5-113">Přístup k obsahu jednotlivých buněk provádí dvourozměrný logický souřadnicový systém nebo pole poskytované požadovanou souběžnou implementací <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="7cfa5-113">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
- <span data-ttu-id="7cfa5-114">Záhlaví sloupce nebo řádku může být obsaženo v objektu tabulky nebo se jedná o samostatný objekt záhlaví, který je spojen s objektem tabulky.</span><span class="sxs-lookup"><span data-stu-id="7cfa5-114">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
- <span data-ttu-id="7cfa5-115">Záhlaví sloupců a řádků můžou zahrnovat primární hlavičku i všechny podpůrné hlavičky.</span><span class="sxs-lookup"><span data-stu-id="7cfa5-115">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7cfa5-116">Tento koncept bude zřejmý v tabulce aplikace Microsoft Excel, kde uživatel definoval sloupec "first name" (křestní jméno).</span><span class="sxs-lookup"><span data-stu-id="7cfa5-116">This concept becomes evident in a Microsoft Excel spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="7cfa5-117">Tento sloupec má teď dvě hlavičky – záhlaví "křestní jméno" definované uživatelem a alfanumerické označení pro daný sloupec přiřazenou aplikací.</span><span class="sxs-lookup"><span data-stu-id="7cfa5-117">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
- <span data-ttu-id="7cfa5-118">V tématu [implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-grid-control-pattern.md) pro související funkce mřížky.</span><span class="sxs-lookup"><span data-stu-id="7cfa5-118">See [Implementing the UI Automation Grid Control Pattern](implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="7cfa5-119">![Tabulka se složitými položkami záhlaví](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="7cfa5-119">![Table with complex header items.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="7cfa5-120">Příklad tabulky se složitými záhlavími sloupců</span><span class="sxs-lookup"><span data-stu-id="7cfa5-120">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="7cfa5-121">![Tabulka s nejednoznačnou vlastností RowOrColumnMajor](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="7cfa5-121">![Table with ambiguous RowOrColumnMajor property.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="7cfa5-122">Příklad tabulky s nejednoznačnou vlastností RowOrColumnMajor</span><span class="sxs-lookup"><span data-stu-id="7cfa5-122">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="7cfa5-123">Vyžadovaná členové pro ITableProvider</span><span class="sxs-lookup"><span data-stu-id="7cfa5-123">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="7cfa5-124">Pro rozhraní ITableProvider jsou vyžadovány následující vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="7cfa5-124">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="7cfa5-125">Vyžadovaná členové</span><span class="sxs-lookup"><span data-stu-id="7cfa5-125">Required members</span></span>|<span data-ttu-id="7cfa5-126">Typ člena</span><span class="sxs-lookup"><span data-stu-id="7cfa5-126">Member type</span></span>|<span data-ttu-id="7cfa5-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7cfa5-127">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="7cfa5-128">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="7cfa5-128">Property</span></span>|<span data-ttu-id="7cfa5-129">Žádné</span><span class="sxs-lookup"><span data-stu-id="7cfa5-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="7cfa5-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="7cfa5-130">Method</span></span>|<span data-ttu-id="7cfa5-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="7cfa5-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="7cfa5-132">Metoda</span><span class="sxs-lookup"><span data-stu-id="7cfa5-132">Method</span></span>|<span data-ttu-id="7cfa5-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="7cfa5-133">None</span></span>|  
  
 <span data-ttu-id="7cfa5-134">Tento vzor ovládacího prvku nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="7cfa5-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="7cfa5-135">Výjimky</span><span class="sxs-lookup"><span data-stu-id="7cfa5-135">Exceptions</span></span>  
 <span data-ttu-id="7cfa5-136">Tento vzor ovládacího prvku nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="7cfa5-136">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cfa5-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7cfa5-137">See also</span></span>

- [<span data-ttu-id="7cfa5-138">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7cfa5-138">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="7cfa5-139">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7cfa5-139">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="7cfa5-140">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="7cfa5-140">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="7cfa5-141">Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7cfa5-141">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="7cfa5-142">Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7cfa5-142">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="7cfa5-143">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7cfa5-143">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="7cfa5-144">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="7cfa5-144">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
