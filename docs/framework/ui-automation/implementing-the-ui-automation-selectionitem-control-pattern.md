---
title: Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
ms.openlocfilehash: 02505224e4673592f1e169c40af1cfb098e5d9bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180105"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.ISelectionItemProvider>konvence pro implementaci , včetně informací o vlastnostech, metodách a událostech. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 Vzor <xref:System.Windows.Automation.SelectionItemPattern> ovládacího prvku se používá k podpoře ovládacích prvků, které <xref:System.Windows.Automation.Provider.ISelectionProvider>fungují jako jednotlivé, volitelné podřízené položky ovládacíprvky kontejneru, které implementují . Příklady ovládacích prvků, které implementují vzor ovládacího prvku SelectionItem, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Prováděcí pokyny a úmluvy  
 Při implementaci vzor ovládacího prvku Položka výběru, poznamenejte si následující pokyny a konvence:  
  
- Ovládací prvky s jedním výběrem, které spravují podřízené ovládací <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>prvky, které implementují , například posuvník Rozlišení **obrazovky** v dialogovém okně **Vlastnosti zobrazení,** by se měly implementovat <xref:System.Windows.Automation.Provider.ISelectionProvider> a jejich podřízené objekty by měly implementovat obě <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> a <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>
## <a name="required-members-for-iselectionitemprovider"></a>Požadované členy pro ISelectionItemProvider  
 Následující vlastnosti, metody a události jsou <xref:System.Windows.Automation.Provider.ISelectionItemProvider>vyžadovány pro implementaci .  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Vlastnost|Žádný|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Událost|Je aktivována, když výběr v kontejneru <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> výrazně změnila <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> a vyžaduje odesílání více a události, než konstantní povolení.|  
  
- Pokud je výsledkem <xref:System.Windows.Automation.SelectionItemPattern.Select%2A> <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>, , <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> nebo a je <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> jedna vybraná položka, by měla být zvýšena; jinak <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> odeslat podle potřeby.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Při pokusu o některou z následujících pokusů:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>je volána na kontejner <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` u jednoho výběru, kde a prvek je již vybrán.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>je volána v kontejneru <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` s více násobným výběrem, kde a je vybrán pouze jeden prvek.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A>je volána na kontejner <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` u jednoho výběru, kde a jiný prvek je již vybrán.|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-selection-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
- [Ukázka zprostředkovatele fragmentů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771502(v=vs.90))
