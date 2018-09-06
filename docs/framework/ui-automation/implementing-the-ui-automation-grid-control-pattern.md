---
title: Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- control patterns, grid
- grid control pattern
- UI Automation, grid control pattern
ms.assetid: 234d11a0-7ce7-4309-8989-2f4720e02f78
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 036680ea908f2cbe58db398dc315fccd997c4148
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43879046"
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.IGridProvider>, včetně informací o vlastnosti, metody a události. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 <xref:System.Windows.Automation.GridPattern> – Vzor ovládacích prvků slouží k podpoře ovládací prvky, které fungují jako kontejnery pro kolekci podřízených elementů. Podřízené objekty tohoto elementu musí implementovat <xref:System.Windows.Automation.Provider.IGridItemProvider> a uspořádané v dvojrozměrné logické systém souřadnic, který můžete procházet podle řádků a sloupců. Příklady ovládacích prvků, které tento ovládací prvek model implementovat, najdete v článku [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny pro implementaci a konvence  
 Při implementaci vzoru ovládacích prvků mřížka, mějte na paměti následující pokyny a konvence:  
  
-   Souřadnice mřížky jsou počítány od nuly s vlevo nahoře (nebo horním pravém buňky v závislosti na národním prostředí) s souřadnice (0, 0).  
  
-   Pokud je prázdná buňka, prvku automatizace uživatelského rozhraní musí být vrácena stále za účelem podpory <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> vlastnosti pro tuto buňku. To je možné, pokud je podobný nepravidelné pole rozložení podřízených elementů mřížky (viz následující příklad).  
  
 ![Průzkumník Windows zobrazení zobrazuje nepravidelné rozložení. ](../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Příklad ovládací prvek mřížky s prázdnou souřadnice  
  
-   Mřížka s jednu položku se stále vyžadují k implementaci <xref:System.Windows.Automation.Provider.IGridProvider> Pokud logicky má se za to být mřížku. Počet podřízených položek v mřížce je důležité.  
  
-   Skryté řádků a sloupců, v závislosti na implementaci zprostředkovatele mohou být načteny v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu a proto se projeví ve <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> a <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> vlastnosti. Pokud skrytý řádků a sloupců ještě nebyly načteny, by neměly být započítány.  
  
-   <xref:System.Windows.Automation.Provider.IGridProvider> nepovolí aktivní zpracování mřížky; <xref:System.Windows.Automation.Provider.ITransformProvider> musí být implementován pro povolení této funkce.  
  
-   Použití <xref:System.Windows.Automation.StructureChangedEventHandler> pro naslouchání strukturální nebo rozložení mřížky, jako je například buňky, které byly přidány, odebrány nebo sloučit změny.  
  
-   Použití <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> ke sledování přechod zálohovaných položek nebo buňky mřížky.  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a>Požadované členy pro IGridProvider  
 Následující vlastnosti a metody jsou požadovány pro implementaci rozhraní IGridProvider.  
  
|Požadované členy|Typ|Poznámky|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Metoda|Žádné|  
  
 Tento model ovládací prvek nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Poskytovatelé musí vyvolání následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> – Pokud je větší než požadovaný řádek souřadnice <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> nebo souřadnice sloupec je větší než <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> – Pokud požadovaný řádek nebo sloupec souřadnice je menší než nula.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
