---
title: Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 39baadbad4bf5aff1cc2cd7877489f43581e0fa0
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458157"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje pokyny a konvence pro implementaci <xref:System.Windows.Automation.Provider.ISelectionProvider>, včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor ovládacího prvku <xref:System.Windows.Automation.SelectionPattern> slouží k podpoře ovládacích prvků, které fungují jako kontejnery pro kolekci volitelných podřízených položek. Podřízené objekty tohoto elementu musí implementovat <xref:System.Windows.Automation.Provider.ISelectionItemProvider>. Příklady ovládacích prvků, které implementují tento vzor ovládacích prvků, naleznete v tématu [mapování vzoru ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a>Pokyny a konvence implementace  
 Při implementaci vzoru ovládacího prvku Výběr si všimněte následujících pokynů a konvencí:  
  
- Ovládací prvky, které implementují <xref:System.Windows.Automation.Provider.ISelectionProvider> umožňují vybrat jednu nebo více podřízených položek. Například seznam, zobrazení seznamu a stromové zobrazení podporují více výběrů, zatímco pole se seznamem, posuvník a skupiny přepínačů podporují jeden výběr.  
  
- Ovládací prvky, které mají minimální, maximální a souvislý rozsah, jako je například ovládací prvek posuvníku **hlasitosti** , by měly implementovat <xref:System.Windows.Automation.Provider.IRangeValueProvider> místo <xref:System.Windows.Automation.Provider.ISelectionProvider>.  
  
- Ovládací prvky pro jedno výběr, které spravují podřízené ovládací prvky, které implementují <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>, jako je posuvník **rozlišení obrazovky** v dialogovém okně **zobrazení vlastností** nebo výběr **barvy** v aplikaci Microsoft Word (znázorněné níže ), by měly implementovat <xref:System.Windows.Automation.Provider.ISelectionProvider>; jejich podřízené objekty by měly implementovat jak <xref:System.Windows.Automation.Provider.IRawElementProviderFragment>, tak <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.  
  
 ![Výběr barvy se žlutým zvýrazněním](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Příklad mapování řetězců vzorníku barev  
  
- Nabídky <xref:System.Windows.Automation.SelectionPattern>nepodporují. Pokud pracujete s položkami nabídky, které zahrnují grafiku a text (například položky v **podokně náhledu** v nabídce **zobrazení** v aplikaci Microsoft Outlook) a je třeba předat stav, měli byste implementovat <xref:System.Windows.Automation.Provider.IToggleProvider>.  
  
<a name="Required_Members_for_ISelectionProvider"></a>   
## <a name="required-members-for-iselectionprovider"></a>Vyžadovaná členové pro ISelectionProvider  
 Pro rozhraní <xref:System.Windows.Automation.Provider.ISelectionProvider> jsou vyžadovány následující vlastnosti, metody a události.  
  
|Vyžadovaná členové|Typ|Poznámky|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Vlastnost|Měla by podporovat události změněné vlastnosti pomocí <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> a <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Vlastnost|Měla by podporovat události změněné vlastnosti pomocí <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> a <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Žádné|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Událost|Vyvolá se v případě, že se výběr v kontejneru významně změnil a vyžaduje odeslání dalších událostí sčítání a odinstalování, než povoluje <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> konstanta.|  
  
 Vlastnosti <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> a <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> mohou být dynamické. Například počáteční stav ovládacího prvku nemusí mít ve výchozím nastavení vybrané žádné položky, což značí, že <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> `false`. Po výběru položky však musí mít ovládací prvek vždy alespoň jednu položku, která je vybrána. Podobně ve výjimečných případech může ovládací prvek při inicializaci vybrat více položek, ale následně umožní provedení pouze jednoho výběru.  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Pokud ovládací prvek není povolený.|  
|<xref:System.InvalidOperationException>|Pokud je ovládací prvek skrytý.|  
  
## <a name="see-also"></a>Viz také:

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-selectionitem-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
