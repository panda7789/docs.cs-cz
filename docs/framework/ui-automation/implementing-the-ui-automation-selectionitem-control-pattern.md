---
title: Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 410fe76fe6e3ddba143622c1bc4d0270d906d854
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423146"
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.ISelectionItemProvider>, včetně informací o vlastnosti, metody a události. Odkazy na další odkazy jsou uvedeny na konci přehledu.  
  
 <xref:System.Windows.Automation.SelectionItemPattern> – Vzor ovládacích prvků slouží k podpoře ovládací prvky, které fungují jako jednotlivé, vybrat podřízené položky kontejneru ovládacích prvků, které implementují <xref:System.Windows.Automation.Provider.ISelectionProvider>. Příklady ovládacích prvků, které implementace vzoru ovládacích prvků SelectionItem najdete v tématu [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny pro implementaci a konvence  
 Pokud implementace vzoru ovládacích prvků výběru položek, mějte na paměti následující pokyny a konvence:  
  
-   Jeden výběr ovládacích prvků, které spravují podřízených ovládacích prvků, které implementují <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, například **rozlišení obrazovky** posuvník v **vlastnosti zobrazení** dialogové okno, by měly implementovat <xref:System.Windows.Automation.Provider.ISelectionProvider>a jejich podřízené položky by měly implementovat obě <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> a <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>Požadované členy pro ISelectionItemProvider  
 Následující vlastnosti, metody a události, které jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Událost|Vyvoláno při výběru v kontejneru významně změnil a vyžaduje odeslání více <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> a <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> událostí, než <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> povoluje – konstanta.|  
  
-   Pokud výsledek <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>, <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>, nebo <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> je vybrané položce <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> by měla být zvýšena; jinak odešlete <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> podle potřeby.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Poskytovatelé musí vyvolání následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Když některý z následujících nedochází k pokusům o:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> je volána v kontejneru jedním výběrem kde <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` a prvek je už vybraná.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A> je volána v kontejneru více výběrů kde <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` a vybrali pouze jeden element.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A> je volána v kontejneru jedním výběrem kde <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` a jiný element je už vybraná.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-selection-control-pattern.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Ukázka fragmentu poskytovatele](https://msdn.microsoft.com/library/778ef1bc-8610-4bc9-886e-aeff94a8a13e)
