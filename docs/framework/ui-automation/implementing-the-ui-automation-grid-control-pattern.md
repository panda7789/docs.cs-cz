---
title: Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: f4b5f1763b655026b20f37605d4649606af7fea6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435370"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IGridProvider>, včetně informací o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 Vzor ovládacího prvku <xref:System.Windows.Automation.GridPattern> slouží k podpoře ovládacích prvků, které fungují jako kontejnery pro kolekci podřízených prvků. Podřízené objekty tohoto elementu musí implementovat <xref:System.Windows.Automation.Provider.IGridItemProvider> a být uspořádány do dvojrozměrného systému logických souřadnic, který lze procházet podle řádků a sloupců. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzorového ovládacího prvku mřížky si všimněte následujících pokynů a konvencí:  
  
- Souřadnice mřížky jsou založené na nule s horní levou (nebo pravou horní buňkou v závislosti na národním prostředí), která má souřadnice (0, 0).  
  
- Je-li buňka prázdná, musí být objekt automatizace uživatelského rozhraní nadále vrácen, aby podporoval vlastnost <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> pro tuto buňku. To je možné v případě, že rozložení podřízených prvků v mřížce je podobné nezarovnanému poli (viz příklad níže).  
  
 ![Zobrazení Průzkumníka Windows zobrazující nerovnoměrné rozložení](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Příklad ovládacího prvku mřížky s prázdnými souřadnicemi  
  
- K implementaci <xref:System.Windows.Automation.Provider.IGridProvider>, je-li logicky považována za mřížku, se stále vyžaduje mřížka s jednou položkou. Počet podřízených položek v mřížce je nemateriálný.  
  
- Skryté řádky a sloupce, v závislosti na implementaci poskytovatele, mohou být načteny do stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a proto se projeví ve vlastnostech <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> a <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A>. Pokud skryté řádky a sloupce ještě nebyly načteny, neměly by se počítat.  
  
- <xref:System.Windows.Automation.Provider.IGridProvider> nepovoluje aktivní manipulaci s mřížkou. aby bylo možné tuto funkci povolit, musí být implementována <xref:System.Windows.Automation.Provider.ITransformProvider>.  
  
- Použijte <xref:System.Windows.Automation.StructureChangedEventHandler> k naslouchání strukturálním nebo rozmístění změn v mřížce, například buněk, které byly přidány, odebrány nebo sloučeny.  
  
- Pomocí <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> můžete sledovat procházení položek nebo buněk v mřížce.  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a>Vyžadovaná členové pro IGridProvider  
 Pro implementaci rozhraní IGridProvider jsou vyžadovány následující vlastnosti a metody.  
  
|Vyžadovaná členové|Typ|Poznámky|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Metoda|Žádné|  
  
 Tento vzor ovládacího prvku nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> – Pokud je požadovaná souřadnice řádku větší než <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>, nebo je souřadnice sloupce větší než <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> – Pokud je jedna z požadovaných souřadnic řádku nebo sloupce menší než nula.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-griditem-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
