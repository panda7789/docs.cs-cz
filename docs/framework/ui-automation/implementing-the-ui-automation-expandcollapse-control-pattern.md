---
title: "Implementace vzoru ovládacích prvků ExpandCollapse pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
caps.latest.revision: "25"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 8e956008c6b80e0b2184adcf0a45b70efa21d752
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>Implementace vzoru ovládacích prvků ExpandCollapse pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>, včetně informací o události, vlastnosti a metody. Na konci tohoto přehledu jsou uvedeny odkazy na další odkazy.  
  
 <xref:System.Windows.Automation.ExpandCollapsePattern> – Vzor ovládacích prvků se používá pro podporu ovládacích prvků, které vizuálně rozbalte zobrazíte další obsah a sbalit ke skrytí obsahu. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Postup implementace a konvence  
 Při implementaci ExpandCollapse – vzor ovládacích prvků, poznamenejte si následující pokyny a konvence:  
  
-   Agregace ovládací prvky – vytvořené s nástroji podřízené objekty, které poskytují rozhraní s funkcemi rozbalit nebo sbalit – musí podporovat <xref:System.Windows.Automation.ExpandCollapsePattern> řízení vzor, zatímco jejich podřízené elementy nepodporují. Například ovládací prvek pole se seznamem je vytvořené s kombinací pole se seznamem, tlačítka a ovládacích prvcích pro úpravy, ale je pouze nadřazené pole se seznamem, musí podporovat <xref:System.Windows.Automation.ExpandCollapsePattern>.  
  
    > [!NOTE]
    >  Výjimkou je ovládací prvek nabídky, který je agregace jednotlivé objekty MenuItem. Objekty MenuItem může podporovat <xref:System.Windows.Automation.ExpandCollapsePattern> – vzor ovládacích prvků, ale nadřazeného ovládacího prvku nelze nabídky. Podobně jako výjimka platí pro ovládací prvky stromů a položka stromu.  
  
-   Když <xref:System.Windows.Automation.ExpandCollapseState> ovládacího prvku je nastaven na <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, jakékoliv <xref:System.Windows.Automation.ExpandCollapsePattern> funkce je aktuálně neaktivní pro ovládací prvek a pouze informace, které lze získat pomocí tohoto – vzor ovládacích prvků <xref:System.Windows.Automation.ExpandCollapseState>. Pokud později přidané žádné podřízené objekty, <xref:System.Windows.Automation.ExpandCollapseState> změny a <xref:System.Windows.Automation.ExpandCollapsePattern> funkce se aktivuje.  
  
-   <xref:System.Windows.Automation.ExpandCollapseState>odkazuje na viditelnost pouze; bezprostředně podřízené objekty neodkazuje na viditelnost všechny následné objekty.  
  
-   Rozbalte a sbalit funkce je specifický pro ovládací prvek. Následují příklady toto chování.  
  
    -   Osobní nabídky Office může být tři stavu MenuItem (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>, <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> a <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) kde ovládacího prvku určuje stav přijmout, kdy <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> nebo <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> je volána.  
  
    -   Volání metody <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> na TreeItem se může zobrazovat všechny následníky nebo přímé podřízené objekty.  
  
    -   Pokud volání <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> nebo <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> v ovládacím prvku Udržovat stav z jejich potomků událost změny zda mají být odeslány, není událost změny stavu Pokud nadřazeného ovládacího prvku nespravuje stav jeho následníky při sbalení, může ovládacího prvku zrušení všech potomků, které již nejsou viditelné a vyvolání zničení událostí; nebo může změnit <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> pro každou následník a vygenerovat viditelnost události změny.  
  
-   Pokud chcete zajistit navigace, je žádoucí, aby objekt v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu (s odpovídající viditelnost stav) bez ohledu na jeho nadřazené položky <xref:System.Windows.Automation.ExpandCollapseState>. Pokud na vyžádání jsou generovány následníky, se může vyskytovat pouze v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu po se zobrazuje pro první čas nebo pouze v době, kdy jsou viditelné.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iexpandcollapseprovider"></a>Požadované členy pro IExpandCollapseProvider  
 Následující vlastnosti a metody jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Událost|Tento ovládací prvek nemá žádné přidružené události; Použijte tento obecný delegát.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí throw následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Buď <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> nebo <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> je volána, když <xref:System.Windows.Automation.ExpandCollapseState>  =  <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Pohyb mezi elementy automatizace uživatelského rozhraní pomocí třídy TreeWalker](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
