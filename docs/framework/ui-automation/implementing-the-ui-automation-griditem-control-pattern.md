---
title: Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: fdaac3cad61f6047201587e48d4377fa61b868af
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043406"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.IGridItemProvider>implementaci, včetně informací o vlastnostech. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 Vzor ovládacího prvku se používá pro podporu jednotlivých podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.IGridProvider>. <xref:System.Windows.Automation.GridItemPattern> Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci <xref:System.Windows.Automation.Provider.IGridProvider>nástroje si všimněte následujících pokynů a konvencí:  
  
- Souřadnice mřížky jsou vypočítány od nuly s horní levou buňkou, která má souřadnice (0, 0).  
  
- Sloučené buňky budou nahlásit <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> své <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> vlastnosti a vlastnostmi na základě jejich podkladové buňky ukotvení, jak jsou definovány zprostředkovatelem automatizace uživatelského rozhraní. Obvykle se jedná o horní a levý řádek nebo sloupec.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider>neposkytuje aktivní manipulaci s mřížkou, jako je například sloučení nebo rozdělení buněk.  
  
- Ovládací prvky, <xref:System.Windows.Automation.Provider.IGridItemProvider> které implementují, je obvykle možné procházet (to znamená, že se klient automatizace uživatelského rozhraní může přesunout na sousedící ovládací prvky) pomocí klávesnice.  
  
<a name="Required_Members_for_IGridItemProvider"></a>   
## <a name="required-members-for-igriditemprovider"></a>Vyžadovaná členové pro IGridItemProvider  
 Pro implementaci <xref:System.Windows.Automation.Provider.IGridItemProvider>jsou vyžadovány následující vlastnosti a metody.  
  
|Vyžadovaná členové|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Vlastnost|Žádné|  
  
 Tento model řízení nemá žádné přidružené metody nebo události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Tento vzor ovládacího prvku nemá žádné přidružené výjimky.  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-grid-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
