---
title: Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- Selection control pattern
- UI Automation, Selection control pattern
- control patterns, Selection
ms.assetid: 449c3068-a5d6-4f66-84c6-1bcc7dd4d209
ms.openlocfilehash: 083a4bb56fe76c1d65015ffabf741d7e1953d2ff
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180122"
---
# <a name="implementing-the-ui-automation-selection-control-pattern"></a>Implementace vzoru ovládacích prvků výběr pro automatizaci uživatelského rozhraní
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma představuje pokyny a <xref:System.Windows.Automation.Provider.ISelectionProvider>konvence pro implementaci , včetně informací o událostech a vlastnostech. Odkazy na další odkazy jsou uvedeny na konci tématu.  
  
 Vzor <xref:System.Windows.Automation.SelectionPattern> ovládacího prvku se používá k podpoře ovládacích prvků, které fungují jako kontejnery pro kolekci volitelných podřízených položek. Podřízené položky tohoto <xref:System.Windows.Automation.Provider.ISelectionItemProvider>prvku musí implementovat . Příklady ovládacích prvků, které implementují tento vzor ovládacího prvku, naleznete [v tématu Mapování vzorů ovládacího prvku pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md).  
  
<a name="Implementation_Guidelines_and_Conventions"></a>
## <a name="implementation-guidelines-and-conventions"></a>Prováděcí pokyny a úmluvy  
 Při implementaci vzor ovládacího prvku výběr, poznamenejte si následující pokyny a konvence:  
  
- Ovládací prvky, které implementují <xref:System.Windows.Automation.Provider.ISelectionProvider> umožňují vybrat jednu nebo více podřízených položek. Například seznam, zobrazení seznamu a stromové zobrazení podporují více výběrů, zatímco pole se seznamem, jezdec a skupina přepínacích tlačítek podporují jeden výběr.  
  
- Ovládací prvky, které mají minimální, maximální a nepřetržitý rozsah, <xref:System.Windows.Automation.Provider.IRangeValueProvider> například ovládací prvek posuvníku **Hlasitost,** by měly <xref:System.Windows.Automation.Provider.ISelectionProvider>být implementovány místo .  
  
- Ovládací prvky s jedním výběrem, které spravují podřízené ovládací prvky, které <xref:System.Windows.Automation.Provider.IRawElementProviderFragmentRoot>implementují , například jezdec Rozlišení **obrazovky** v dialogovém okně **Vlastnosti zobrazení** nebo ovládací prvek **výběru barvy** z aplikace Microsoft Word (znázorněno níže), by měly být implementovány <xref:System.Windows.Automation.Provider.ISelectionProvider>; jejich děti by <xref:System.Windows.Automation.Provider.IRawElementProviderFragment> <xref:System.Windows.Automation.Provider.ISelectionItemProvider>měly provádět jak a .  
  
 ![Výběr barvy se zvýrazněnou žlutou barvou](./media/uia-valuepattern-colorpicker.png "UIA_ValuePattern_ColorPicker")  
Příklad mapování řetězce políčka barev  
  
- Nabídky nepodporují <xref:System.Windows.Automation.SelectionPattern>. Pokud pracujete s položkami nabídky, které obsahují grafiku i text (například položky **podokna náhledu** <xref:System.Windows.Automation.Provider.IToggleProvider>v nabídce **Zobrazení** v aplikaci Microsoft Outlook) a potřebujete sdělit stav, měli byste implementovat .  
  
<a name="Required_Members_for_ISelectionProvider"></a>
## <a name="required-members-for-iselectionprovider"></a>Požadované členy pro ISelectionProvider  
 Pro rozhraní jsou vyžadovány následující vlastnosti, <xref:System.Windows.Automation.Provider.ISelectionProvider> metody a události.  
  
|Požadované členy|Typ|Poznámky|  
|----------------------|----------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Vlastnost|By podpora vlastnost <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> změněna události pomocí a <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Vlastnost|By podpora vlastnost <xref:System.Windows.Automation.Automation.AddAutomationPropertyChangedEventHandler%2A> změněna události pomocí a <xref:System.Windows.Automation.Automation.RemoveAutomationPropertyChangedEventHandler%2A>.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.GetSelection%2A>|Metoda|Žádný|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Událost|Je aktivována při výběru v kontejneru výrazně změněna <xref:System.Windows.Automation.Provider.AutomationInteropProvider.InvalidateLimit> a vyžaduje odesílání více sčítání a odebrání události než konstantní povolení.|  
  
 <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> Vlastnosti <xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A> a mohou být dynamické. Například počáteční stav ovládacího prvku nemusí mít ve výchozím nastavení <xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A> `false`vybrané žádné položky, což znamená, že je . Po výběru položky však musí mít ovládací prvek vždy vybrána alespoň jedna položka. Podobně ve výjimečných případech ovládací prvek může povolit více položek, které mají být vybrány při inicializaci, ale následně povolit pouze jeden výběr.  
  
<a name="Exceptions"></a>
## <a name="exceptions"></a>Výjimky  
 Zprostředkovatelé musí vyvolat následující výjimky.  
  
|Typ výjimky|Podmínka|  
|--------------------|---------------|  
|<xref:System.Windows.Automation.ElementNotEnabledException>|Pokud ovládací prvek není povolen.|  
|<xref:System.InvalidOperationException>|Pokud je ovládací prvek skrytý.|  
  
## <a name="see-also"></a>Viz také

- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Implementace vzoru ovládacích prvků SelectionItem pro automatizaci uživatelského rozhraní](implementing-the-ui-automation-selectionitem-control-pattern.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
