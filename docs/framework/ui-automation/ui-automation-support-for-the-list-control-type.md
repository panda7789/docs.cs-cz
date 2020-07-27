---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku seznam
description: Získejte informace o podpoře automatizace uživatelského rozhraní pro typ ovládacího prvku seznam. Seznamte se s požadovanou stromovou strukturou, vlastnostmi, vzory ovládacích prvků a událostmi.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
ms.openlocfilehash: 01827250ac216dbcb57a8a139637e7c48d59566d
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166078"
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku seznam
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma poskytuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podpoře pro typ ovládacího prvku seznam. V nástroji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] je typ ovládacího prvku sada podmínek, které musí ovládací prvek splňovat, aby bylo možné vlastnost použít <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků.  
  
 Typ ovládacího prvku seznam poskytuje způsob, jak uspořádat plochou skupinu nebo skupiny položek a umožní uživateli vybrat jednu nebo více těchto položek. Typ ovládacího prvku seznam má volné omezení pro typy podřízených elementů, které může obsahovat. To umožňuje zprostředkovatelům automatizace uživatelského rozhraní podporovat známý element pro kontejnery výběru.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Požadavky v následujících částech platí pro všechny ovládací prvky, které implementují typ ovládacího prvku seznam, bez ohledu na to [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] , zda je typu Win32 nebo model Windows Forms. Seznam ovládacích prvků kontejneru je příkladem ovládacích prvků, které implementují typ ovládacího prvku seznam.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Požadovaná stromová struktura automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje dvě zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, která se vztahují k ovládacím prvkům seznamu, a popisuje, co může být v každém zobrazení obsaženo. Zobrazení ovládacího prvku obsahuje pouze prvky, které jsou ovládacími prvky, a zobrazení obsahu odebere nadbytečné informace ze stromu. Například textový ovládací prvek, který se používá k označení pole se seznamem, bude vystaven jako `ComboBox NameProperty` . Vzhledem k tomu, že ovládací prvek text je již vystaven tímto způsobem prostřednictvím zobrazení ovládacího prvku, není nutné jej vystavit dvakrát; Proto je odebrán ze zobrazení obsahu. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacích prvků|Zobrazení obsahu|  
|------------------|------------------|  
|Obsahuje prvky, které odpovídají ovládacím prvkům.|Odstraní redundantní informace ze stromu, takže technologie pro usnadnění práce s nejmenší sadou smysluplných informací pro koncového uživatele.|  
|Seznam<br /><br /> -DataItem (0 nebo více)<br />-ListItem (0 nebo více)<br />-Group (0 nebo více)<br />-ScrollBar (0, 1 nebo 2)|Seznam<br /><br /> -DataItem (0 nebo více)<br />-ListItem (0 nebo více)<br />-Group (0 nebo více)|  
  
 Zobrazení ovládacího prvku pro ovládací prvek, který implementuje typ ovládacího prvku seznam (například ovládací prvek seznam), se skládá z těchto prvků:  
  
- Nula nebo více položek v rámci ovládacího prvku seznam (položky mohou být založené na typu položky seznamu nebo ovládacího prvku položky dat).
  
- Nula nebo více ovládacích prvků skupiny v rámci ovládacího prvku seznam.
  
- Nula, jeden nebo dva ovládací prvky posuvníku.
  
Zobrazení obsahu ovládacího prvku, který implementuje typ ovládacího prvku seznam (například ovládací prvek seznam), se skládá z těchto prvků:  
  
- Nula nebo více položek v rámci ovládacího prvku seznam (položky mohou být založené na typu položky seznamu nebo ovládacího prvku položky dat).
  
- V rámci ovládacího prvku seznamu není nula nebo více skupin.

Ovládací prvek seznamu nesmí obsahovat položky, které mají hierarchickou relaci jinou než dohromady seskupené. Pokud má položka podřízené položky ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře, měl by být kontejner seznamu založen na typu ovládacího prvku strom.  
  
 Položky, které lze vybrat v rámci ovládacího prvku seznam, budou k dispozici od následníků ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu ovládacího prvku seznam. Všechny položky v rámci ovládacího prvku seznam musí patřit do stejné skupiny výběru. Položky, které lze vybrat v seznamu, by měly být zveřejněny jako ListItem (namísto DataItem) typů ovládacích prvků.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice je obzvláště relevantní pro ovládací prvky seznamu. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostech najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Majetek|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečná napříč všemi ovládacími prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Vnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Pokud má ovládací prvek seznam možnost výběru (bod, na který se dá kliknout, aby se zavedl fokus seznamu), musí být tento bod vystavený prostřednictvím této vlastnosti.<br /><br /> Pokud má `IsOffScreen` vlastnost hodnotu true, <xref:System.Windows.Automation.NoClickablePointException> bude vyvolána.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může obdržet fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Hodnota vlastnosti název ovládacího prvku seznam by měla předávat kategorii možností, ze kterých je uživatel požádán o výběr. Tato vlastnost obvykle získá svůj název ze statického textového popisku. Pokud není k dispozici žádný statický textový popisek, vývojář aplikace musí vystavit hodnotu vlastnosti Name.<br /><br /> Pouze v případě, že tato vlastnost není vyžadována pro ovládací prvky seznamu, je v případě, že je ovládací prvek použit v rámci podstromu jiného ovládacího prvku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Pokud je popisek statický text, musí tato vlastnost vystavit odkaz na tento ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Seznam|Tato hodnota je stejná pro všechny architektury uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|seznamu|Lokalizovaný řetězec odpovídající typu ovládacího prvku seznam.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Ano|V zobrazení obsahu stromu je vždy zahrnut ovládací prvek seznam [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Ano|Ovládací prvek seznam je vždy součástí zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Ano|Pokud kontejner může přijmout vstup z klávesnice, hodnota této vlastnosti by měla být true.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Viz poznámky.|Text helpu pro ovládací prvky seznam by měl vysvětlit, proč se uživateli požaduje, aby si vyžádal volbu ze seznamu možností. Například "výběr položky z tohoto seznamu nastaví rozlišení zobrazení pro monitor."|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns-and-properties"></a>Požadované vzory a vlastnosti ovládacího prvku automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vzory ovládacích prvků, které musí být podporovány ovládacími prvky seznamu. Další informace o vzorech ovládacích prvků naleznete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Řídicí vzorek/vlastnost vzoru|Podpora/hodnota|Poznámky|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Povinné|Všechny ovládací prvky, které podporují typ ovládacího prvku seznam, musí implementovat, `ISelectionProvider` Pokud je stav výběru udržován mezi položkami obsaženými v ovládacím prvku. Pokud položky v kontejneru nelze vybrat, je nutné použít typ ovládacího prvku skupina.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Závislosti|Ovládací prvky seznamu nevyžadují vždy výběr položky.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Závislosti|Ovládací prvky seznamu mohou být kontejnery s jedním nebo více výběry.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Závislosti|Implementujte tento vzor ovládacích prvků, pokud se položky v kontejneru mají Procházet.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Závislosti|Tento model implementujte v případě, že je k dispozici navigace mřížky pro položku podle položky.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Závislosti|Implementujte tento model ovládacího prvku, pokud ovládací prvek může podporovat více zobrazení položek v kontejneru.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Nikdy|`ITableProvider`není nikdy podporován pro typ ovládacího prvku seznam. Pokud ovládací prvek by měl podporovat tento model ovládacího prvku, ovládací prvek by měl být založen na typu ovládacího prvku datová mřížka.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, které musí být podporovány všemi ovládacími prvky seznamu. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událostí|Podpora/hodnota|Poznámky|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Závislosti|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Závislosti|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Povinné|Žádné|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.List>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
