---
title: Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní
description: Pochopení pokynů a konvencí pro implementaci vzoru ovládacích prvků GridPattern Grid v automatizaci uživatelského rozhraní Naučte se implementovat rozhraní IGridProvider.
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
ms.openlocfilehash: c7aae8e8070c989c4b36e0581aa5f48f51416f97
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165877"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IGridProvider> , včetně informací o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 <xref:System.Windows.Automation.GridPattern>Vzor ovládacího prvku slouží k podpoře ovládacích prvků, které fungují jako kontejnery pro kolekci podřízených prvků. Podřízené objekty tohoto elementu musí být implementovány <xref:System.Windows.Automation.Provider.IGridItemProvider> a uspořádány do dvojrozměrného logického systému souřadnic, který lze procházet podle řádků a sloupců. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzorového ovládacího prvku mřížky si všimněte následujících pokynů a konvencí:  
  
- Souřadnice mřížky jsou založené na nule s horní levou (nebo pravou horní buňkou v závislosti na národním prostředí), která má souřadnice (0, 0).  
  
- Je-li buňka prázdná, musí být objekt automatizace uživatelského rozhraní nadále vrácen, aby podporoval <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> vlastnost pro tuto buňku. To je možné v případě, že rozložení podřízených prvků v mřížce je podobné nezarovnanému poli (viz příklad níže).  
  
 ![Zobrazení Průzkumníka Windows zobrazující nerovnoměrné rozložení](./media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Příklad ovládacího prvku mřížky s prázdnými souřadnicemi  
  
- K implementaci mřížky s jednou položkou je stále potřeba implementovat ji, <xref:System.Windows.Automation.Provider.IGridProvider> Pokud je logicky považována za mřížku. Počet podřízených položek v mřížce je nemateriálný.  
  
- Skryté řádky a sloupce, v závislosti na implementaci poskytovatele, mohou být načteny ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře, a proto se projeví <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> ve <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> vlastnostech a. Pokud skryté řádky a sloupce ještě nebyly načteny, neměly by se počítat.  
  
- <xref:System.Windows.Automation.Provider.IGridProvider>nepovoluje aktivní manipulaci s mřížkou. <xref:System.Windows.Automation.Provider.ITransformProvider>pro povolení této funkce je nutné implementovat implementaci.  
  
- Použijte <xref:System.Windows.Automation.StructureChangedEventHandler> k naslouchání strukturálním nebo rozmístění změn v mřížce, například buněk, které byly přidány, odebrány nebo sloučeny.  
  
- Použijte <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> ke sledování procházení položek nebo buněk v mřížce.  
  
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
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> – Pokud je požadovaná souřadnice řádku větší než <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> nebo souřadnice sloupce větší než <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A> .|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> – Pokud je jedna z požadovaných souřadnic řádku nebo sloupce menší než nula.|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-griditem-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
