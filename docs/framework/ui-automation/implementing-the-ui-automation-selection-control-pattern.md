---
title: Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 6b5e0e4e0a14410c23833db6cc90d23e7959ad22
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087715"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma popisuje pravidla a zásady pro implementaci <xref:System.Windows.Automation.Provider.ISelectionProvider>, včetně informací o události a vlastnosti. Odkazy na další odkazy jsou uvedeny na konci tohoto tématu.  
  
 <xref:System.Windows.Automation.SelectionPattern> – Vzor ovládacích prvků slouží k podpoře ovládací prvky, které fungují jako kontejnery pro kolekci volitelných podřízených položek. Podřízené objekty tohoto elementu musí implementovat <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. Příklady ovládacích prvků, které tento ovládací prvek model implementovat, najdete v článku [ovládací prvek vzor mapování pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny pro implementaci a konvence  
 Pokud implementace vzoru ovládacích prvků výběru, mějte na paměti následující pokyny a konvence:  
  
-   Ovládací prvky, které implementují <xref:System.Windows.Automation.Provider.ISelectionProvider> povolit jeden nebo více podřízených položek má být vybrán. Pole se seznamem, zobrazením seznamu a stromovým zobrazením podporují více výběrů, že pole se seznamem, posuvník a skupina přepínacích tlačítek podporují jeden výběr.  
  
-   Ovládací prvky, které mají minimální, maximální a průběžné rozsahu, například **svazku** ovládací prvek posuvník, by měly implementovat <xref:System.Windows.Automation.Provider.IRangeValueProvider> místo <xref:System.Windows.Automation.Provider.ISelectionProvider>.  
  
-   Jeden výběr ovládacích prvků, které spravují podřízených ovládacích prvků, které implementují <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, například **rozlišení obrazovky** posuvník v **vlastnosti zobrazení** dialogové okno nebo **barva Výběr** ovládacího prvku pro výběr z [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] (zobrazený dole), by měly implementovat <xref:System.Windows.Automation.Provider.ISelectionProvider>; jejich podřízené položky by měly implementovat obě <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> a <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
 ![Výběr barvy s zvýrazněn žlutou barvou. ](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Příklad mapování řetězec vzorníku barev  
  
-   Nabídky nepodporují <xref:System.Windows.Automation.SelectionPattern>. Pokud pracujete s položkami nabídky, které zahrnují grafiku a text (například **podokno náhledu** položky v **zobrazení** v nabídce [!INCLUDE[TLA#tla_outlook](../../../includes/tlasharptla-outlook-md.md)]) a potřeba zprostředkovat stavu, měli byste implementovat <xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>Požadované členy pro ISelectionProvider  
 Jsou požadovány pro následující vlastnosti, metody a události <xref:System.Windows.Automation.Provider.ISelectionProvider> rozhraní.  
  
|Požadované členy|Type|Poznámky|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Vlastnost|By měl podporovat události změněné vlastnosti pomocí <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> a <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Vlastnost|By měl podporovat události změněné vlastnosti pomocí <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> a <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Událost|Vyvoláno při výběru v kontejneru významně změnil a vyžaduje odeslání více událostí, přidávání a odebírání než <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> povoluje – konstanta.|  
  
 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> a <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> vlastnosti mohou být dynamické. Počáteční stav ovládacího prvku nemusí mít například položky vybrané ve výchozím nastavení, což indikuje, že <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> je `false`. Ale po výběru položky ovládacího prvku musí mít vždy alespoň jeden zvolené položky. Podobně ve výjimečných případech může být ovládací prvek povolit více položek vybraných na inicializaci, ale později povolit pouze jeden výběr má být provedeno.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Poskytovatelé musí vyvolání následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Pokud je ovládací prvek není povoleno.|  
|<xref:System.InvalidOperationException>|Když je skrytý ovládací prvek.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-selectionitem-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
