---
title: Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: d561587e6bb98ba857b27ba89b4c1a45ba964ffd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180186"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.IGridItemProvider>konvence pro implementaci , včetně informací o vlastnostech. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 Vzor <xref:System.Windows.Automation.GridItemPattern> ovládacího prvku se používá k podpoře <xref:System.Windows.Automation.Provider.IGridProvider>jednotlivých podřízených ovládacích prvků kontejnerů, které implementují . Příklady ovládacích prvků, které implementují tento vzor ovládacího prvku, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Prováděcí pokyny a úmluvy  
 Při provádění <xref:System.Windows.Automation.Provider.IGridProvider>si poznamenejte následující pokyny a konvence:  
  
- Souřadnice mřížky jsou založeny na nule, přičemž levá horní buňka má souřadnice (0, 0).  
  
- Sloučené buňky <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> budou vykazovat jejich a vlastnosti na základě jejich základní kotevní buňky definované zprostředkovatelem automatizace uživatelského rozhraní. Obvykle se bude jedná o nejvyšší a levý řádek nebo sloupec.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider>nezajišťuje aktivní manipulaci s mřížkou, jako je slučování nebo dělení buněk.  
  
- Ovládací prvky, které implementují <xref:System.Windows.Automation.Provider.IGridItemProvider> lze obvykle procházet (to znamená, že klient automatizace uživatelského rozhraní můžete přesunout do sousedních ovládacích prvků) pomocí klávesnice.  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a>Povinné členy pro IGridItemProvider  
 Následující vlastnosti a metody jsou <xref:System.Windows.Automation.Provider.IGridItemProvider>vyžadovány pro implementaci .  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.RowSpan%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ColumnSpan%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A>|Vlastnost|Žádný|  
  
 Tento vzor ovládacího prvku nemá žádné přidružené metody nebo události.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Tento vzor ovládacího prvku nemá žádné přidružené výjimky.  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-grid-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
