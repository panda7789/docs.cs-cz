---
title: Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: 04f3ee1e01054df6a13ab2391e14a6a7f7274bb9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180218"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.IGridProvider>konvence pro implementaci , včetně informací o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 Vzor <xref:System.Windows.Automation.GridPattern> ovládacího prvku se používá k podpoře ovládacích prvků, které fungují jako kontejnery pro kolekci podřízených prvků. Podřízené položky tohoto <xref:System.Windows.Automation.Provider.IGridItemProvider> prvku musí implementovat a uspořádat do dvojrozměrného logického souřadnicového systému, který lze procházet řádek a sloupec. Příklady ovládacích prvků, které implementují tento vzor ovládacího prvku, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Prováděcí pokyny a úmluvy  
 Při implementaci gridový vzor ovládacího prvku, poznamenejte si následující pokyny a konvence:  
  
- Souřadnice mřížky jsou založeny na nule s levou horní (nebo v pravém horním rohu buňky v závislosti na národním prostředí) souřadnicemi (0, 0).  
  
- Pokud je buňka prázdná, musí být stále vrácen prvek <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> automatizace uživatelského rozhraní, aby byla pro tuto buňku podpořena vlastnost. To je možné, když rozložení podřízených prvků v mřížce je podobné nepravidelné pole (viz příklad níže).  
  
 ![Zobrazení Průzkumníka Windows zobrazující nepravidelné rozložení.](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Příklad gridového ovládacího prvku s prázdnými souřadnicemi  
  
- Mřížka s jednou položkou je <xref:System.Windows.Automation.Provider.IGridProvider> stále nutné implementovat, pokud je logicky považován za mřížku. Počet podřízených položek v mřížce je nepodstatný.  
  
- Skryté řádky a sloupce, v závislosti na implementaci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zprostředkovatele, mohou být <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> načteny ve stromu a proto se projeví ve vlastnostech a. <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> Pokud skryté řádky a sloupce ještě nebyly načteny, neměly by být počítány.  
  
- <xref:System.Windows.Automation.Provider.IGridProvider>neumožňuje aktivní manipulaci s mřížkou; <xref:System.Windows.Automation.Provider.ITransformProvider> musí být implementována, aby byla tato funkce povolena.  
  
- Slouží <xref:System.Windows.Automation.StructureChangedEventHandler> k naslouchání strukturálním změnám nebo změnám rozložení v mřížce, jako jsou buňky, které byly přidány, odebrány nebo sloučeny.  
  
- Slouží <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> ke sledování průchodu mezi položkami nebo buňkami mřížky.  
  
<a name="Required_Members_for_IGridProvider"></a>
## <a name="required-members-for-igridprovider"></a>Požadované členy pro iGridProvider  
 Následující vlastnosti a metody jsou vyžadovány pro implementaci rozhraní IGridProvider.  
  
|Požadované členy|Typ|Poznámky|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Metoda|Žádný|  
  
 Tento vzor ovládacího prvku nemá žádné přidružené události.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> - Pokud je souřadnice <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> požadovaného řádku větší <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>než souřadnice sloupce nebo je větší než .|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> - Pokud je některý z požadovaných souřadnic řádku nebo sloupce menší než nula.|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-griditem-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
