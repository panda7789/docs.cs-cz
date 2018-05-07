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
ms.openlocfilehash: 0038202fb7c7f1a6e0b4f21592d7a1056c4dfa2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-the-ui-automation-grid-control-pattern"></a>Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IGridProvider>, včetně informací o události, vlastnosti a metody. Na konci tohoto přehledu jsou uvedeny odkazy na další odkazy.  
  
 <xref:System.Windows.Automation.GridPattern> – Vzor ovládacích prvků se používá pro podporu ovládacích prvků, které fungují jako kontejnery pro kolekci podřízených elementů. Podřízené objekty tohoto elementu musí implementovat <xref:System.Windows.Automation.Provider.IGridItemProvider> a být uspořádány do dvourozměrná logické systém souřadnic, který lze procházet podle řádků a sloupců. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Postup implementace a konvence  
 Když implementace vzoru ovládacích prvků mřížka, poznamenejte si následující pokyny a konvence:  
  
-   Souřadnice mřížky jsou od nuly s horní levý (nebo horní pravé buňky v závislosti na národní prostředí) s souřadnice (0, 0).  
  
-   Pokud buňku je prázdná, prvku automatizace uživatelského rozhraní musí být vrácen stále za účelem podpory <xref:System.Windows.Automation.Provider.IGridItemProvider.ContainingGrid%2A> vlastnost pro dané buňky. To je možné, pokud je podobná nepravidelné pole rozložení podřízených elementů v mřížce (viz následující příklad).  
  
 ![Průzkumník Windows zobrazení zobrazující nepravidelné rozložení. ] (../../../docs/framework/ui-automation/media/uia-gridpattern-ragged-array.PNG "UIA_GridPattern_Ragged_Array")  
Příklad ovládacího prvku mřížky s prázdnou souřadnice  
  
-   Mřížka s jednou položkou je stále vyžadují k implementaci <xref:System.Windows.Automation.Provider.IGridProvider> Pokud logicky se považuje za mřížka. Počet podřízené položky v mřížce je důležité.  
  
-   Skryté řádky a sloupce, v závislosti na implementaci zprostředkovatele, mohou být načteny v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu a proto budou promítnuta <xref:System.Windows.Automation.GridPattern.GridPatternInformation.RowCount%2A> a <xref:System.Windows.Automation.GridPattern.GridPatternInformation.ColumnCount%2A> vlastnosti. Pokud dosud nebyly byl načteny skryté řádky a sloupce, by neměly být započítány.  
  
-   <xref:System.Windows.Automation.Provider.IGridProvider> neumožňuje active zpracování mřížka; <xref:System.Windows.Automation.Provider.ITransformProvider> Pokud chcete tuto funkci povolit, musí být implementována.  
  
-   Použití <xref:System.Windows.Automation.StructureChangedEventHandler> naslouchat strukturálních nebo rozložení mřížky například buněk, které jste přidali, odebrat nebo sloučit změny.  
  
-   Použití <xref:System.Windows.Automation.AutomationFocusChangedEventHandler> sledovat traversal prostřednictvím položky nebo buněk mřížka.  
  
<a name="Required_Members_for_IGridProvider"></a>   
## <a name="required-members-for-igridprovider"></a>Požadované členy pro IGridProvider  
 Následující vlastnosti a metody jsou požadovány pro implementaci rozhraní IGridProvider.  
  
|Požadované členy|Typ|Poznámky|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A>|Metoda|Žádné|  
  
 Tento vzor ovládacích prvků nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí throw následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> – Pokud souřadnice požadovaný řádek je větší než <xref:System.Windows.Automation.Provider.IGridProvider.RowCount%2A> nebo souřadnici sloupec je větší než <xref:System.Windows.Automation.Provider.IGridProvider.ColumnCount%2A>.|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.Windows.Automation.Provider.IGridProvider.GetItem%2A><br /><br /> – Pokud některý z požadovaný řádek nebo sloupec souřadnice je menší než nula.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementace vzoru ovládacích prvků GridItem pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-griditem-control-pattern.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
