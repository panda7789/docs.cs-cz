---
title: "Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
caps.latest.revision: "33"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: cb8b47b147e3a7a3c615418e2c0987e4d6a20f4c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma představuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ISelectionProvider>, včetně informací o události a vlastnosti. Na konci tohoto tématu jsou uvedeny odkazy na další odkazy.  
  
 <xref:System.Windows.Automation.SelectionPattern> – Vzor ovládacích prvků se používá pro podporu ovládacích prvků, které fungují jako kontejnery pro kolekci volitelný podřízené položky. Podřízené objekty tohoto elementu musí implementovat <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků najdete v tématu [řízení vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Postup implementace a konvence  
 Při implementace vzoru ovládacích prvků výběr, poznamenejte si následující pokyny a konvence:  
  
-   Určuje, které implementují <xref:System.Windows.Automation.Provider.ISelectionProvider> povolit jednoho nebo několika podřízenými vybrat položky. Pole se seznamem, zobrazení seznamu a stromové zobrazení podporovat více výběrů, že pole se seznamem, posuvník a skupina přepínacích tlačítek podpory jednoho výběru.  
  
-   Ovládací prvky, které mají minimální, maximální a průběžné rozsah, například **svazku** posuvník, by měla implementovat <xref:System.Windows.Automation.Provider.IRangeValueProvider> místo <xref:System.Windows.Automation.Provider.ISelectionProvider>.  
  
-   Jedním výběrem ovládacích prvků, které spravují podřízených ovládacích prvků, které implementují <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, například **rozlišení obrazovky** jezdec v **vlastností zobrazení** dialogové okno nebo **barev Výběr** ovládacího prvku pro výběr z [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (zobrazený dole), by měla implementovat <xref:System.Windows.Automation.Provider.ISelectionProvider>; jejich podřízené by měla implementovat obě <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> a <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
 ![Výběr barvy s žlutý zvýrazněná. ] (../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Příklad mapování řetězec vzorníku barev  
  
-   Nabídky nepodporují <xref:System.Windows.Automation.SelectionPattern>. Pokud pracujete s položky nabídky, které zahrnují grafika a text (například **podokno náhledu** položky v **zobrazení** nabídky v [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)]) a muset nesou stavu, měli byste implementovat <xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>Požadované členy pro ISelectionProvider  
 Následující vlastnosti, metod a události jsou vyžadovány pro <xref:System.Windows.Automation.Provider.ISelectionProvider> rozhraní.  
  
|Požadované členy|Typ|Poznámky|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Vlastnost|Musí podporovat události změněné vlastnosti pomocí <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> a <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Vlastnost|Musí podporovat události změněné vlastnosti pomocí <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> a <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Událost|Vyvolá, když výběr v kontejneru došlo ke změně výrazně a vyžaduje odesílání další přidávání a odebírání událostí, než <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> umožňuje konstanta.|  
  
 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> a <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> vlastnosti mohou být dynamické. Počáteční stav ovládacího prvku nemusí mít například všechny položky vybrané ve výchozím nastavení, která znamená, že <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> je `false`. Ale po výběru položky se ovládací prvek musí mít vždy alespoň jedna položka vybrána. Podobně ve výjimečných případech může povolit ovládacího prvku více položek v inicializace zaškrtnuta, ale následně povolit pouze jeden výběr má být provedeno.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí throw následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Pokud ovládací prvek není povolena.|  
|<xref:System.InvalidOperationException>|Pokud je skrytý ovládací prvek.|  
  
## <a name="see-also"></a>Viz také  
 [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [Vzory ovládacího prvku automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [Implementace vzoru SelectionItem ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-selectionitem-control-pattern.md)  
 [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
