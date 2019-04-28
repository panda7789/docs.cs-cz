---
title: Implementace vzoru ovládacích prvků ExpandCollapse pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
ms.openlocfilehash: ff07f5264ccb3ec699e3676a2e9ba64443b2875f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61610007"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>Implementace vzoru ovládacích prvků ExpandCollapse pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>, včetně informací o vlastnosti, metody a události. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 <xref:System.Windows.Automation.ExpandCollapsePattern> – Vzor ovládacích prvků slouží k podpoře ovládací prvky, které vizuálně rozbalte zobrazíte další obsah a sbalení pro skrytí obsahu. Příklady ovládacích prvků, které tento ovládací prvek model implementovat, najdete v článku [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny pro implementaci a konvence  
 Pokud implementace vzoru ovládacích prvků ExpandCollapse, mějte na paměti následující pokyny a konvence:  
  
- Agregovat ovládací prvky – vytvořených pomocí podřízených objektů, které poskytují rozhraní s funkcí Rozbalit/sbalit – musí podporovat <xref:System.Windows.Automation.ExpandCollapsePattern> řídit vzor, že jejich podřízené prvky tomu tak není. Například ovládací prvek pole se seznamem se vytvořil s kombinací pole se seznamem, tlačítka a textová pole, ale je pouze nadřazené pole se seznamem, který musí podporovat <xref:System.Windows.Automation.ExpandCollapsePattern>.  
  
    > [!NOTE]
    >  Výjimkou je ovládací prvek nabídky, který je agregací jednotlivé objekty MenuItem. Podporuje objekty MenuItem <xref:System.Windows.Automation.ExpandCollapsePattern> – vzor ovládacích prvků, ale nadřazený nabídky ovládací prvek nelze. Podobné výjimky platí pro ovládací prvky stromu a položka stromu.  
  
- Když <xref:System.Windows.Automation.ExpandCollapseState> ovládacího prvku nastavená na <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, všechny <xref:System.Windows.Automation.ExpandCollapsePattern> funkce je aktuálně neaktivní ovládacího prvku a je jen informace, které lze získat pomocí tohoto – vzor ovládacích prvků <xref:System.Windows.Automation.ExpandCollapseState>. Pokud později přidané všechny podřízené objekty, <xref:System.Windows.Automation.ExpandCollapseState> změny a <xref:System.Windows.Automation.ExpandCollapsePattern> je aktivovaná funkce.  
  
- <xref:System.Windows.Automation.ExpandCollapseState> Označuje, zda se bezprostředně podřízených objektů neodkazuje na viditelnost všechny odvozené objekty.  
  
- Rozbalit a sbalit funkce jsou specifické pro ovládací prvek. Následují příklady tohoto chování.  
  
    - Osobní nabídky Office může být MenuItem tri stav (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>, <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> a <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) určuje, kde ovládacího prvku stavu na přijetí, kdy <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> nebo <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> je volána.  
  
    - Volání <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> na TreeItem může zobrazit všechny následníky nebo pouze přímé podřízené objekty.  
  
    - Pokud volání <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> nebo <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> na ovládací prvek udržuje svůj stav z jejich potomků pak událost změny viditelnost mají být odeslány, nikoli události změny stavu pokud nadřazený ovládací prvek nespravuje stavu z jejich potomků pak při sbalení, mohou ovládací prvek Zničte všechny následníky, které již nejsou viditelné a vyvolat událost zničení; nebo může změnit <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> pro každou následník a zvýší viditelnost události změny.  
  
- Pokud chcete zajistit navigace, je žádoucí, aby objekt v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu (s odpovídající viditelnost) bez ohledu na jeho rodičů <xref:System.Windows.Automation.ExpandCollapseState>. Pokud následníky jsou generovány na vyžádání, se může vyskytovat jenom [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu po zobrazení první čas nebo pouze, pokud nejsou viditelná.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iexpandcollapseprovider"></a>Požadované členy pro IExpandCollapseProvider  
 Následující vlastnosti a metody, které jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Událost|Tento ovládací prvek nemá žádné přidružené události; Použijte tento obecný delegát.|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Poskytovatelé musí vyvolání následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Buď <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> nebo <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> je volána, když <xref:System.Windows.Automation.ExpandCollapseState>  =  <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Pohyb mezi elementy automatizace uživatelského rozhraní pomocí třídy TreeWalker](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
