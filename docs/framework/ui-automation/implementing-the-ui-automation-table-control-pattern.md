---
title: Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
ms.openlocfilehash: 0b3d000112060550734890ad3c4063a26c320b04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180120"
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a><span data-ttu-id="9e6b0-102">Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e6b0-102">Implementing the UI Automation Table Control Pattern</span></span>
> [!NOTE]
> <span data-ttu-id="9e6b0-103">Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="9e6b0-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="9e6b0-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="9e6b0-105">Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.ITableProvider>konvence pro implementaci , včetně informací o vlastnostech, metodách a událostech.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.ITableProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="9e6b0-106">Odkazy na další odkazy jsou uvedeny na konci přehledu.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="9e6b0-107">Vzor <xref:System.Windows.Automation.TablePattern> ovládacího prvku se používá k podpoře ovládacích prvků, které fungují jako kontejnery pro kolekci podřízených prvků.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-107">The <xref:System.Windows.Automation.TablePattern> control pattern is used to support controls that act as containers for a collection of child elements.</span></span> <span data-ttu-id="9e6b0-108">Podřízené položky tohoto <xref:System.Windows.Automation.Provider.ITableItemProvider> prvku musí implementovat a uspořádat do dvojrozměrného logického souřadnicového systému, který lze procházet řádek a sloupec.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-108">The children of this element must implement <xref:System.Windows.Automation.Provider.ITableItemProvider> and be organized in a two-dimensional logical coordinate system that can be traversed by row and column.</span></span> <span data-ttu-id="9e6b0-109">Tento vzor ovládacího prvku <xref:System.Windows.Automation.Provider.IGridProvider>je obdobou , s <xref:System.Windows.Automation.Provider.ITableProvider> rozdílem, že všechny implementující ovládací prvek musí také vystavit sloupec nebo řádek záhlaví vztah pro každý podřízený prvek.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-109">This control pattern is analogous to <xref:System.Windows.Automation.Provider.IGridProvider>, with the distinction that any control implementing <xref:System.Windows.Automation.Provider.ITableProvider> must also expose a column and/or row header relationship for each child element.</span></span> <span data-ttu-id="9e6b0-110">Příklady ovládacích prvků, které implementují tento vzor ovládacího prvku, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="9e6b0-110">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="9e6b0-111">Prováděcí pokyny a úmluvy</span><span class="sxs-lookup"><span data-stu-id="9e6b0-111">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="9e6b0-112">Při implementaci vzor ovládacího prvku tabulka, poznamenejte si následující pokyny a konvence:</span><span class="sxs-lookup"><span data-stu-id="9e6b0-112">When implementing the Table control pattern, note the following guidelines and conventions:</span></span>  
  
- <span data-ttu-id="9e6b0-113">Přístup k obsahu jednotlivých buněk je prostřednictvím dvourozměrného logického souřadnicového systému nebo pole poskytovaného požadovanou souběžnou implementací <xref:System.Windows.Automation.Provider.IGridProvider>.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-113">Access to the content of individual cells is through a two-dimensional logical coordinate system or array provided by the required concurrent implementation of <xref:System.Windows.Automation.Provider.IGridProvider>.</span></span>  
  
- <span data-ttu-id="9e6b0-114">Záhlaví sloupce nebo řádku může být obsaženo v objektu tabulky nebo může být samostatným objektem záhlaví, který je přidružen k objektu tabulky.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-114">A column or row header can be contained within a table object or be a separate header object that is associated with a table object.</span></span>  
  
- <span data-ttu-id="9e6b0-115">Záhlaví sloupců a řádků mohou obsahovat primární záhlaví i podpůrná záhlaví.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-115">Column and row headers may include both a primary header as well as any supporting headers.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e6b0-116">Tento koncept se projeví v tabulce aplikace Microsoft Excel, kde uživatel definoval sloupec Křestní jméno.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-116">This concept becomes evident in a Microsoft Excel spreadsheet where a user has defined a "First name" column.</span></span> <span data-ttu-id="9e6b0-117">Tento sloupec má nyní dvě záhlaví – záhlaví "Jméno" definované uživatelem a alfanumerické označení pro tento sloupec přiřazené aplikací.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-117">This column now has two headers—the "First name" header defined by the user and the alphanumeric designation for that column assigned by the application.</span></span>  
  
- <span data-ttu-id="9e6b0-118">Informace o souvisejících funkcích mřížky naleznete [v tématu Implementace vzoru řízení mřížky automatizace](implementing-the-ui-automation-grid-control-pattern.md) uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-118">See [Implementing the UI Automation Grid Control Pattern](implementing-the-ui-automation-grid-control-pattern.md) for related grid functionality.</span></span>  
  
 <span data-ttu-id="9e6b0-119">![Tabulka se složitými položkami záhlaví.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span><span class="sxs-lookup"><span data-stu-id="9e6b0-119">![Table with complex header items.](./media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")</span></span>  
<span data-ttu-id="9e6b0-120">Příklad tabulky se složitými záhlavími sloupců</span><span class="sxs-lookup"><span data-stu-id="9e6b0-120">Example of a Table with Complex Column Headers</span></span>  
  
 <span data-ttu-id="9e6b0-121">![Tabulka s nejednoznačným vlastnostem RowOrColumnMajor.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span><span class="sxs-lookup"><span data-stu-id="9e6b0-121">![Table with ambiguous RowOrColumnMajor property.](./media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")</span></span>  
<span data-ttu-id="9e6b0-122">Příklad tabulky s nejednoznačnou vlastností RowOrColumnMajor</span><span class="sxs-lookup"><span data-stu-id="9e6b0-122">Example of a Table with Ambiguous RowOrColumnMajor Property</span></span>  
  
<a name="Required_Members_for_ITableProvider"></a>
## <a name="required-members-for-itableprovider"></a><span data-ttu-id="9e6b0-123">Požadované členy pro ITableProvider</span><span class="sxs-lookup"><span data-stu-id="9e6b0-123">Required Members for ITableProvider</span></span>  
 <span data-ttu-id="9e6b0-124">Pro rozhraní ITableProvider jsou vyžadovány následující vlastnosti a metody.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-124">The following properties and methods are required for the ITableProvider interface.</span></span>  
  
|<span data-ttu-id="9e6b0-125">Požadované členy</span><span class="sxs-lookup"><span data-stu-id="9e6b0-125">Required members</span></span>|<span data-ttu-id="9e6b0-126">Typ člena</span><span class="sxs-lookup"><span data-stu-id="9e6b0-126">Member type</span></span>|<span data-ttu-id="9e6b0-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e6b0-127">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|<span data-ttu-id="9e6b0-128">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="9e6b0-128">Property</span></span>|<span data-ttu-id="9e6b0-129">Žádný</span><span class="sxs-lookup"><span data-stu-id="9e6b0-129">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|<span data-ttu-id="9e6b0-130">Metoda</span><span class="sxs-lookup"><span data-stu-id="9e6b0-130">Method</span></span>|<span data-ttu-id="9e6b0-131">Žádný</span><span class="sxs-lookup"><span data-stu-id="9e6b0-131">None</span></span>|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|<span data-ttu-id="9e6b0-132">Metoda</span><span class="sxs-lookup"><span data-stu-id="9e6b0-132">Method</span></span>|<span data-ttu-id="9e6b0-133">Žádný</span><span class="sxs-lookup"><span data-stu-id="9e6b0-133">None</span></span>|  
  
 <span data-ttu-id="9e6b0-134">Tento vzor ovládacího prvku nemá žádné přidružené události.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-134">This control pattern has no associated events.</span></span>  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a><span data-ttu-id="9e6b0-135">Výjimky</span><span class="sxs-lookup"><span data-stu-id="9e6b0-135">Exceptions</span></span>  
 <span data-ttu-id="9e6b0-136">Tento vzor ovládacího prvku nemá žádné přidružené výjimky.</span><span class="sxs-lookup"><span data-stu-id="9e6b0-136">This control pattern has no associated exceptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e6b0-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e6b0-137">See also</span></span>

- [<span data-ttu-id="9e6b0-138">Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e6b0-138">UI Automation Control Patterns Overview</span></span>](ui-automation-control-patterns-overview.md)
- [<span data-ttu-id="9e6b0-139">Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e6b0-139">Support Control Patterns in a UI Automation Provider</span></span>](support-control-patterns-in-a-ui-automation-provider.md)
- [<span data-ttu-id="9e6b0-140">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="9e6b0-140">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
- [<span data-ttu-id="9e6b0-141">Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e6b0-141">Implementing the UI Automation TableItem Control Pattern</span></span>](implementing-the-ui-automation-tableitem-control-pattern.md)
- [<span data-ttu-id="9e6b0-142">Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e6b0-142">Implementing the UI Automation Grid Control Pattern</span></span>](implementing-the-ui-automation-grid-control-pattern.md)
- [<span data-ttu-id="9e6b0-143">Přehled stromu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e6b0-143">UI Automation Tree Overview</span></span>](ui-automation-tree-overview.md)
- [<span data-ttu-id="9e6b0-144">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e6b0-144">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
