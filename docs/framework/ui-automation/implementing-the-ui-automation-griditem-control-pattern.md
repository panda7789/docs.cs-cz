---
title: Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní
description: Pokyny a konvence pro implementaci vzoru ovládacích prvků GridItemPattern pro položky mřížky v automatizaci uživatelského rozhraní. Viz povinné členy pro IGridItemProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, GridItem
- UI Automation GridItem control pattern
- GridItem control pattern
ms.assetid: bffbae08-fe2a-42fd-ab84-f37187518916
ms.openlocfilehash: e0a0c616f3f0cf9bc091e4fbb496d71ab8550bd3
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165818"
---
# <a name="implementing-the-ui-automation-griditem-control-pattern"></a>Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IGridItemProvider> , včetně informací o vlastnostech. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 <xref:System.Windows.Automation.GridItemPattern>Vzor ovládacího prvku se používá pro podporu jednotlivých podřízených ovládacích prvků kontejnerů, které implementují <xref:System.Windows.Automation.Provider.IGridProvider> . Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci nástroje <xref:System.Windows.Automation.Provider.IGridProvider> si všimněte následujících pokynů a konvencí:  
  
- Souřadnice mřížky jsou vypočítány od nuly s horní levou buňkou, která má souřadnice (0, 0).  
  
- Sloučené buňky budou nahlásit <xref:System.Windows.Automation.Provider.IGridItemProvider.Row%2A> své <xref:System.Windows.Automation.Provider.IGridItemProvider.Column%2A> vlastnosti a vlastnostmi na základě jejich podkladové buňky ukotvení, jak jsou definovány zprostředkovatelem automatizace uživatelského rozhraní. Obvykle se jedná o horní a levý řádek nebo sloupec.  
  
- <xref:System.Windows.Automation.Provider.IGridItemProvider>neposkytuje aktivní manipulaci s mřížkou, jako je například sloučení nebo rozdělení buněk.  
  
- Ovládací prvky, které implementují, <xref:System.Windows.Automation.Provider.IGridItemProvider> je obvykle možné procházet (to znamená, že se klient automatizace uživatelského rozhraní může přesunout na sousedící ovládací prvky) pomocí klávesnice.  
  
<a name="Required_Members_for_IGridItemProvider"></a>
## <a name="required-members-for-igriditemprovider"></a>Vyžadovaná členové pro IGridItemProvider  
 Pro implementaci jsou vyžadovány následující vlastnosti a metody <xref:System.Windows.Automation.Provider.IGridItemProvider> .  
  
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
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-grid-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
