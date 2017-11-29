---
title: "Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Selection Item control pattern
- UI Automation, Selection Item control pattern
- control patterns, Selection Item
ms.assetid: 76b0949a-5b23-4cfc-84cc-154f713e2e12
caps.latest.revision: "22"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 28e28faee25dd89fa646bb6e82958746b6b5932e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-selectionitem-control-pattern"></a>Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ISelectionItemProvider>, včetně informací o události, vlastnosti a metody. Na konci tohoto přehledu jsou uvedeny odkazy na další odkazy.  
  
 <xref:System.Windows.Automation.SelectionItemPattern> – Vzor ovládacích prvků se používá pro podporu ovládací prvky, které se chovají jako jednotlivé, které lze vybírat podřízené položky kontejneru ovládacích prvků, které implementují <xref:System.Windows.Automation.Provider.ISelectionProvider>. Příklady ovládacích prvků, které implementují vzor SelectionItem ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Postup implementace a konvence  
 Při implementaci položka výběru – vzor ovládacích prvků, poznamenejte si následující pokyny a konvence:  
  
-   Jedním výběrem ovládacích prvků, které spravují podřízených ovládacích prvků, které implementují <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, například **rozlišení obrazovky** jezdec v **vlastností zobrazení** dialogové okno, by měla implementovat <xref:System.Windows.Automation.Provider.ISelectionProvider>a jejich podřízené položky, měly by implementovat obě <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> a <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iselectionitemprovider"></a>Požadované členy pro ISelectionItemProvider  
 Následující vlastnosti, metod a události jsou požadovány pro implementaci <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
|Požadované členy|Typ člena|Poznámky|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Vlastnost|Žádné|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Událost|Vyvolá, když výběr v kontejneru došlo ke změně výrazně a vyžaduje odesílání další <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> a <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> událostí, než <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> umožňuje konstanta.|  
  
-   Pokud výsledek <xref:System.Windows.Automation.SelectionItemPattern.Select%2A>, <xref:System.Windows.Automation.SelectionItemPattern.AddToSelection%2A>, nebo <xref:System.Windows.Automation.SelectionItemPattern.RemoveFromSelection%2A> je jeden vybranou položku <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent> by měla být zvýšena; v opačném případě poslat <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent> /  <xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent> podle potřeby.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí throw následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|Pokud některý z těchto pokus:<br /><br /> -   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>je volána v kontejneru jedním výběrem kde <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` a element je již vybrána.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.RemoveFromSelection%2A>je volána v kontejneru vícenásobného výběru kde <xref:System.Windows.Automation.SelectionPattern.IsSelectionRequiredProperty>  =  `true` a je vybrána pouze jeden element.<br />-   <xref:System.Windows.Automation.Provider.ISelectionItemProvider.AddToSelection%2A>je volána v kontejneru jedním výběrem kde <xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>  =  `false` a jiný element je již vybrána.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacího prvku automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementace vzoru ovládacích prvků uživatelského rozhraní automatizace výběr](../../../docs/framework/ui-automation/implementing-the-ui-automation-selection-control-pattern.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [Ukázka zprostředkovatele fragmentu](http://msdn.microsoft.com/en-us/778ef1bc-8610-4bc9-886e-aeff94a8a13e)
