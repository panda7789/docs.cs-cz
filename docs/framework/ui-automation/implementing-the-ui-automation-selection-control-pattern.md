---
title: Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 2297ea0a181fe0fd16aa32b85909acdad5f129ab
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545186"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní
> [!NOTE]
>  Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma obsahuje pokyny a konvence pro <xref:System.Windows.Automation.Provider.ISelectionProvider>implementaci, včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.SelectionPattern> ovládacího prvku slouží k podpoře ovládacích prvků, které fungují jako kontejnery pro kolekci volitelných podřízených položek. Podřízené objekty tohoto elementu musí implementovat <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacího prvku Výběr si všimněte následujících pokynů a konvencí:  
  
- Ovládací prvky, <xref:System.Windows.Automation.Provider.ISelectionProvider> které implementují, aby bylo možné vybrat jednu nebo více podřízených položek. Například seznam, zobrazení seznamu a stromové zobrazení podporují více výběrů, zatímco pole se seznamem, posuvník a skupiny přepínačů podporují jeden výběr.  
  
- Ovládací prvky, které mají minimální, maximální a souvislý rozsah, jako je například ovládací prvek posuvníku **hlasitosti** , <xref:System.Windows.Automation.Provider.IRangeValueProvider> by měly <xref:System.Windows.Automation.Provider.ISelectionProvider>implementovat místo.  
  
- Ovládací prvky pro jedno výběr, které spravují podřízené ovládací <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>prvky, které implementují, jako je posuvník **rozlišení obrazovky** v dialogovém okně **zobrazení vlastností** nebo výběr **barvy** v [!INCLUDE[TLA#tla_word](../../../includes/tlasharptla-word-md.md)] ovládacím prvku ( znázorněno níže), by <xref:System.Windows.Automation.Provider.ISelectionProvider>měly implementovat; jejich podřízené objekty <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> by <xref:System.Windows.Automation.Provider.ISelectionItemProvider>měly implementovat a.  
  
 ![Výběr barvy se žlutým zvýrazněním](../../../docs/framework/ui-automation/media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Příklad mapování řetězců vzorníku barev  
  
- Nabídky nepodporují <xref:System.Windows.Automation.SelectionPattern>. Pokud pracujete s položkami nabídky, které zahrnují grafiku a text (například položky v **podokně náhledu** v nabídce **zobrazení** v aplikaci Microsoft Outlook) a je třeba předat stav, měli byste implementovat <xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>Vyžadovaná členové pro ISelectionProvider  
 Pro <xref:System.Windows.Automation.Provider.ISelectionProvider> rozhraní jsou vyžadovány následující vlastnosti, metody a události.  
  
|Vyžadovaná členové|type|Poznámky|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Vlastnost|By měla podporovat události změněné vlastnosti <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> pomocí <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>a.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Vlastnost|By měla podporovat události změněné vlastnosti <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> pomocí <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>a.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Událost|Vyvolá se v případě, že se výběr v kontejneru významně změnil a vyžaduje odeslání dalších událostí přidání a odebrání <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> , než povoluje konstanta.|  
  
 Vlastnosti <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> a<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> mohou být dynamické. Například počáteční stav ovládacího prvku nemusí mít ve výchozím nastavení vybrané žádné položky, což znamená, že <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> je. `false` Po výběru položky však musí mít ovládací prvek vždy alespoň jednu položku, která je vybrána. Podobně ve výjimečných případech může ovládací prvek při inicializaci vybrat více položek, ale následně umožní provedení pouze jednoho výběru.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Pokud ovládací prvek není povolený.|  
|<xref:System.InvalidOperationException>|Pokud je ovládací prvek skrytý.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/implementing-the-ui-automation-selectionitem-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
