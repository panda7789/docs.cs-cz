---
title: Implementace vzoru ovládacích prvků ExpandCollapse pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
ms.openlocfilehash: 232bceba8286c2566a7df03b9001a5c43b348b20
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71043461"
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a>Implementace vzoru ovládacích prvků ExpandCollapse pro automatizaci uživatelského rozhraní

> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.

Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>implementaci, včetně informací o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci přehledu.

Vzor <xref:System.Windows.Automation.ExpandCollapsePattern> ovládacího prvku slouží k podpoře ovládacích prvků, které se vizuálně rozbalí pro zobrazení více obsahu a sbalení pro skrytí obsahu. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).

<a name="Implementation_Guidelines_and_Conventions"></a>

## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace

Při implementaci vzoru ovládacího prvku ovládacích prvků ExpandCollapse si všimněte následujících pokynů a konvencí:

- Agregační ovládací prvky – sestavené s podřízenými objekty, které poskytují uživatelské rozhraní s funkcí rozbalit/sbalit <xref:System.Windows.Automation.ExpandCollapsePattern> – musí podporovat model ovládacího prvku, zatímco jejich podřízené prvky ne. Například ovládací prvek pole se seznamem je sestaven s kombinací ovládacích prvků seznam, tlačítko a úpravy, ale je to pouze nadřazené pole se seznamem, které musí podporovat <xref:System.Windows.Automation.ExpandCollapsePattern>.

  > [!NOTE]
  > Výjimkou je ovládací prvek nabídky, který je agregací jednotlivých objektů MenuItem. Objekty MenuItem mohou podporovat <xref:System.Windows.Automation.ExpandCollapsePattern> vzorek ovládacího prvku, ale nadřazený ovládací prvek nabídky nemůže. Podobná výjimka se vztahuje na ovládací prvky strom a strom položky stromu.

- Když je ovládací prvek nastaven na <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, všechny <xref:System.Windows.Automation.ExpandCollapsePattern> funkce jsou aktuálně neaktivní pro ovládací prvek a jediné informace, které lze získat pomocí tohoto vzoru ovládacího prvku, je <xref:System.Windows.Automation.ExpandCollapseState>. <xref:System.Windows.Automation.ExpandCollapseState> Pokud jsou následně přidány podřízené objekty, <xref:System.Windows.Automation.ExpandCollapseState> jsou aktivovány změny a <xref:System.Windows.Automation.ExpandCollapsePattern> funkce.

- <xref:System.Windows.Automation.ExpandCollapseState>odkazuje na viditelnost pouze bezprostředních podřízených objektů; neodkazuje na viditelnost všech potomků objektů.

- Funkce rozbalení a sbalení je specifická pro konkrétní ovládací prvek. Níže jsou uvedeny příklady tohoto chování.

  - Osobní nabídka Office může být třída MenuItem pro tři<xref:System.Windows.Automation.ExpandCollapseState.Expanded>země ( <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> a <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>), kde <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> ovládací prvek určuje stav, který se má přijmout při volání <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> nebo.

  - Volání <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> na TreeItem může zobrazit všechny následníky nebo pouze bezprostřední podřízené objekty.

  - Pokud volání <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> nebo <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> na ovládacím prvku udržuje stav jeho následníků, měla by být odeslána událost změny viditelnosti, nikoli událost změny stavu, pokud nadřazený ovládací prvek neudržuje stav potomků, pokud je sbalený, ovládací prvek může zničit všechny následníky, kteří již nejsou viditelní a vyvolávají událost zničení; nebo může změnit <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> pro každého následníka a vyvolat událost změny viditelnosti.

- Pro zajištění navigace je žádoucí, aby byl objekt ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu (s odpovídajícím stavem viditelnosti) bez ohledu na jeho rodiče. <xref:System.Windows.Automation.ExpandCollapseState> Pokud jsou následníky generovány na vyžádání, mohou se zobrazit pouze ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře po prvním zobrazení nebo pouze v případě, že jsou viditelné.

<a name="Required_Members_for_the_IValueProvider_Interface"></a>

## <a name="required-members-for-iexpandcollapseprovider"></a>Vyžadovaná členové pro IExpandCollapseProvider

Pro implementaci <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>jsou vyžadovány následující vlastnosti a metody.

|Vyžadovaná členové|Typ člena|Poznámky|
|----------------------|-----------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Vlastnost|Žádné|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|Metoda|Žádné|
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|Metoda|Žádné|
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|Událost|Tento ovládací prvek nemá žádné přidružené události; Použijte tohoto obecného delegáta.|

<a name="Exceptions"></a>

## <a name="exceptions"></a>Výjimky

Zprostředkovatelé musí vyvolat následující výjimky.

|Typ výjimky|Podmínka|
|--------------------|---------------|
|<xref:System.InvalidOperationException>|Buď <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> <xref:System.Windows.Automation.ExpandCollapseState>nebo jevolána = , když .<xref:System.Windows.Automation.ExpandCollapseState.LeafNode> <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|

## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Pohyb mezi elementy automatizace uživatelského rozhraní pomocí třídy TreeWalker](navigate-among-ui-automation-elements-with-treewalker.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
