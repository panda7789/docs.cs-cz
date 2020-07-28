---
title: Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní
description: Přečtěte si pokyny a konvence pro implementaci vzoru ovládacího prvku tabulka v automatizaci uživatelského rozhraní. Znáte požadované členy pro rozhraní ITableProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: e88ddee04ba887daf1929d855526cd0d062f78d5
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168242"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="bf730-104">Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf730-104">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="bf730-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bf730-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bf730-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="bf730-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="bf730-107">Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ITableProvider> , včetně informací o vlastnostech, metodách a událostech.</span><span class="sxs-lookup"><span data-stu-id="bf730-107">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="bf730-108">Odkazy na další odkazy jsou uvedeny na konci přehledu.</span><span class="sxs-lookup"><span data-stu-id="bf730-108">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="bf730-109"><xref:System.Windows.Automation.TablePattern>Vzor ovládacího prvku slouží k podpoře ovládacích prvků, které fungují jako kontejnery pro kolekci podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="bf730-109">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="bf730-110">Podřízené objekty tohoto elementu musí být implementovány <xref:System.Windows.Automation.Provider.ITableItemProvider> a uspořádány do dvojrozměrného logického systému souřadnic, který lze procházet podle řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="bf730-110">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="bf730-111">Tento vzor řízení je podobný <xref:System.Windows.Automation.Provider.IGridProvider> , s rozlišením, že jakékoli implementující ovládací prvky <xref:System.Windows.Automation.Provider.ITableProvider> musí také zveřejnit vztah záhlaví sloupce nebo řádku pro každý podřízený element.</span><span class="sxs-lookup"><span data-stu-id="bf730-111">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="bf730-112">Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="bf730-112">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="bf730-113">Pokyny a konvence implementace</span><span class="sxs-lookup"><span data-stu-id="bf730-113">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="bf730-114">Při implementaci vzoru ovládacího prvku tabulka si všimněte následujících pokynů a konvencí:</span><span class="sxs-lookup"><span data-stu-id="bf730-114">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="bf730-115">Přístup k obsahu jednotlivých buněk provádí dvourozměrný logický souřadnicový systém nebo pole poskytované požadovanou souběžnou implementací <xref:System.Windows.Automation.Provider.IGridProvider> .</span><span class="sxs-lookup"><span data-stu-id="bf730-115">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
- <span data-ttu-id="bf730-116">Záhlaví sloupce nebo řádku může být obsaženo v objektu tabulky nebo se jedná o samostatný objekt záhlaví, který je spojen s objektem tabulky.</span><span class="sxs-lookup"><span data-stu-id="bf730-116">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
- <span data-ttu-id="bf730-117">Záhlaví sloupců a řádků můžou zahrnovat primární hlavičku i všechny podpůrné hlavičky.</span><span class="sxs-lookup"><span data-stu-id="bf730-117">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bf730-118">Tento koncept bude zřejmý v tabulce aplikace Microsoft Excel, kde uživatel definoval sloupec "first name" (křestní jméno).</span><span class="sxs-lookup"><span data-stu-id="bf730-118">This concept becomes evident in a Microsoft Excel spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="bf730-119">Tento sloupec má teď dvě hlavičky – záhlaví "křestní jméno" definované uživatelem a alfanumerické označení pro daný sloupec přiřazenou aplikací.</span><span class="sxs-lookup"><span data-stu-id="bf730-119">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
- <span data-ttu-id="bf730-120">V tématu [implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-grid-control-pattern.md) pro související funkce mřížky.</span><span class="sxs-lookup"><span data-stu-id="bf730-120">See [Implementing the UI Automation Grid Control Pattern](implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="bf730-121">![Tabulka se složitými položkami záhlaví](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="bf730-121">![Table with complex header items.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="bf730-122">Příklad tabulky se složitými záhlavími sloupců</span><span class="sxs-lookup"><span data-stu-id="bf730-122">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="bf730-123">![Tabulka s nejednoznačnou vlastností RowOrColumnMajor](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="bf730-123">![Table with ambiguous RowOrColumnMajor property.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="bf730-124">Příklad tabulky s nejednoznačnou vlastností RowOrColumnMajor</span><span class="sxs-lookup"><span data-stu-id="bf730-124">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="bf730-125">Vyžadovaná členové pro ITableProvider</span><span class="sxs-lookup"><span data-stu-id="bf730-125">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="bf730-126">Pro rozhraní ITableProvider jsou vyžadovány následující vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="bf730-126">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="bf730-127">Vyžadovaná členové</span><span class="sxs-lookup"><span data-stu-id="bf730-127">Required members</span></span>|<span data-ttu-id="bf730-128">Typ člena</span><span class="sxs-lookup"><span data-stu-id="bf730-128">Member type</span></span>|<span data-ttu-id="bf730-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf730-129">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="bf730-130">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="bf730-130">Property</span></span>|<span data-ttu-id="bf730-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="bf730-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="bf730-132">Metoda</span><span class="sxs-lookup"><span data-stu-id="bf730-132">Method</span></span>|<span data-ttu-id="bf730-133">Žádné</span><span class="sxs-lookup"><span data-stu-id="bf730-133">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="bf730-134">Metoda</span><span class="sxs-lookup"><span data-stu-id="bf730-134">Method</span></span>|<span data-ttu-id="bf730-135">Žádné</span><span class="sxs-lookup"><span data-stu-id="bf730-135">None</span></span>|  
  
 <span data-ttu-id="bf730-136">Tento vzor ovládacího prvku nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="bf730-136">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="bf730-137">Výjimky</span><span class="sxs-lookup"><span data-stu-id="bf730-137">Exceptions</span></span>  
 <span data-ttu-id="bf730-138">Tento vzor ovládacího prvku nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="bf730-138">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf730-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf730-139">See also</span></span>

- [<span data-ttu-id="bf730-140">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf730-140">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="bf730-141">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf730-141">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="bf730-142">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="bf730-142">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="bf730-143">Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf730-143">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="bf730-144">Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf730-144">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="bf730-145">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf730-145">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="bf730-146">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf730-146">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
