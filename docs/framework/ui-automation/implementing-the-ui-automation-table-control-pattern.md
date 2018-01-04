---
title: "Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, Table control pattern
- control patterns, Table
- TableControl pattern
ms.assetid: 880cd85c-aa8c-4fb5-9369-45491d34bb78
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 1e0b3c09948b53363888ae133cd0c4d9f9ae8f05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-table-control-pattern"></a>Implementace vzoru ovládacích prvků tabulka pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ITableProvider>, včetně informací o události, vlastnosti a metody. Na konci tohoto přehledu jsou uvedeny odkazy na další odkazy.  
  
 <xref:System.Windows.Automation.TablePattern> – Vzor ovládacích prvků se používá pro podporu ovládacích prvků, které fungují jako kontejnery pro kolekci podřízených elementů. Podřízené objekty tohoto elementu musí implementovat <xref:System.Windows.Automation.Provider.ITableItemProvider> a být uspořádány do dvourozměrná logické systém souřadnic, který lze procházet podle řádků a sloupců. Tento vzor ovládacích prvků je podobná <xref:System.Windows.Automation.Provider.IGridProvider>, s rozdíl, že všechny řídí, implementace <xref:System.Windows.Automation.Provider.ITableProvider> musí také vystavit vztahu sloupec nebo řádek záhlaví pro každý podřízený element. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Postup implementace a konvence  
 Když implementace vzoru ovládacích prvků tabulka, poznamenejte si následující pokyny a konvence:  
  
-   Přístup k obsahu jednotlivých buněk je prostřednictvím dvourozměrná logické souřadnicový systém nebo pole poskytované požadované souběžné provádění <xref:System.Windows.Automation.Provider.IGridProvider>.  
  
-   Záhlaví sloupce nebo řádku může být obsažený v rámci objektu tabulky nebo být samostatné záhlaví objekt, který je přidružený objekt tabulky.  
  
-   Záhlaví řádků a sloupců může zahrnovat jak primární záhlaví a také všechny podpůrné hlavičky.  
  
> [!NOTE]
>  Tento koncept se stane zřejmé ve [!INCLUDE[TLA#tla_xl](../../../includes/tlasharptla-xl-md.md)] tabulky, kde má uživatelem definovaný sloupec "Jméno". Tento sloupec má teď dvě hlavičky – hlavička "Jméno" definované uživatelem a alfanumerické označení pro tento sloupec přiřazeno aplikací.  
  
-   V tématu [implementace vzoru ovládacích prvků uživatelského rozhraní automatizace mřížka](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md) pro funkci související mřížky.  
  
 ![Tabulka s komplexními položkami záhlaví. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-complex-column-headers.PNG "UIA_TablePattern_Complex_Column_Headers")  
Příklad tabulky se záhlavími sloupců. komplexní  
  
 ![Tabulka s nejednoznačný RowOrColumnMajor vlastností. ] (../../../docs/framework/ui-automation/media/uia-tablepattern-roworcolumnmajorproperty.PNG "UIA_TablePattern_RowOrColumnMajorProperty")  
Příklad tabulky s vlastností nejednoznačný RowOrColumnMajor  
  
<a name="Required_Members_for_ITableProvider"></a>   
## <a name="required-members-for-itableprovider"></a>Požadované členy pro ITableProvider  
 Následující vlastnosti a metody jsou požadovány pro rozhraní ITableProvider.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITableProvider.RowOrColumnMajor%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetColumnHeaders%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.Provider.ITableProvider.GetRowHeaders%2A>|Metoda|Žádné|  
  
 Tento vzor ovládacích prvků nemá žádné přidružené události.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Tento vzor ovládacích prvků nemá žádné přidružené výjimky.  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementace vzoru ovládacích prvků TableItem pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-tableitem-control-pattern.md)  
 [Implementace vzoru ovládacích prvků mřížka pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-grid-control-pattern.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
