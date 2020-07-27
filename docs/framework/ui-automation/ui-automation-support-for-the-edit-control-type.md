---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku úprav
description: Získejte informace o podpoře automatizace uživatelského rozhraní pro typ ovládacího prvku pro úpravy. Seznamte se s požadovanou stromovou strukturou, vlastnostmi, vzory ovládacích prvků a událostmi.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Edit
- Edit control type
- UI Automation, Edit control type
ms.assetid: 6db9d231-c0a0-4e17-910e-ac80357f774f
ms.openlocfilehash: 6c404786d58cfcb4cc7dabd982eea33694b7cd0b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167942"
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku úprav

> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).

Toto téma poskytuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podpoře pro typ ovládacího prvku pro úpravy. V nástroji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] je typ ovládacího prvku sada podmínek, které musí ovládací prvek splňovat, aby bylo možné vlastnost použít <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků.

Ovládací prvky pro úpravy umožňují uživateli zobrazit a upravit jednoduchý řádek textu bez podpory formátovaného formátu.

Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku pro úpravy. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Požadavky platí pro všechny ovládací prvky pro úpravy, ať už [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] , Win32 nebo model Windows Forms.

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Požadovaná stromová struktura automatizace uživatelského rozhraní

Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, které se vztahují k ovládacím prvkům pro úpravy, a popisuje, co může být v každém zobrazení obsaženo. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).

|Zobrazení ovládacích prvků|Zobrazení obsahu|
|------------------|------------------|
|Upravit|Upravit|

Ovládací prvky, které implementují typ ovládacího prvku pro úpravy, budou mít vždy nulové posuvníky v zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, protože se jedná o ovládací prvek s jedním řádkem. Jeden řádek textu se může v některých scénářích rozložení zalamovat. Typ ovládacího prvku pro úpravy je nejvhodnější pro uchovávání malých objemů upravitelných a volitelných textů.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní

V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice jsou obzvláště důležité pro úpravy ovládacích prvků. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostech najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Majetek|Hodnota|Poznámky|
|------------------------------------------------------------------------------------|-----------|-----------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečná napříč všemi ovládacími prvky v aplikaci.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Vnější obdélník, který obsahuje celý ovládací prvek.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Ovládací prvek pro úpravy musí mít upravitelný bod, který umožňuje vstup fokusu na část úpravy ovládacího prvku, když uživatel klikne myší na tlačítko.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může obdržet fokus klávesnice, musí podporovat tuto vlastnost.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Název ovládacího prvku pro úpravy je obvykle generován z popisku statického textu. Pokud není k dispozici žádný statický textový popisek, hodnota vlastnosti `Name` musí být přiřazena vývojářem aplikace. `Name`Vlastnost by nikdy neměla obsahovat textový obsah ovládacího prvku pro úpravy.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Pokud je k ovládacímu prvku přidružen statický textový popisek, musí tato vlastnost vystavit odkaz na tento ovládací prvek. Pokud je ovládací prvek text dílčí součástí jiného ovládacího prvku, nebude mít `LabeledBy` sadu vlastností.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Upravit|Tato hodnota je stejná pro všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektury.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|úpravě|Lokalizovaný řetězec odpovídající typu ovládacího prvku pro úpravy.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Ano|Textové pole je vždy součástí zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Ano|Textové pole je vždy součástí zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|Viz poznámky.|Musí být nastaven na hodnotu true u ovládacích prvků pro úpravy, které obsahují hesla. Pokud ovládací prvek pro úpravy obsahuje obsah hesla, lze tuto vlastnost použít čtečkou obrazovky k určení, zda mají být stisknuty klávesy pro čtení, jak je uživatel zadá.|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns-and-properties"></a>Požadované vzory a vlastnosti ovládacího prvku automatizace uživatelského rozhraní

V následující tabulce jsou uvedeny vzory ovládacích prvků, které musí být podporovány všemi ovládacími prvky pro úpravy. Další informace o vzorech ovládacích prvků naleznete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).

|Řídicí vzorek/vlastnost vzoru ovládacího prvku|Podpora/hodnota|Poznámky|
|-----------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.Provider.ITextProvider>|Závislosti|Ovládací prvky pro úpravy by měly podporovat vzor ovládacího prvku text, protože podrobné informace o textu by měly být vždy k dispozici pro klienty.|
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závislosti|Všechny ovládací prvky pro úpravy, které přijímají řetězec, musí vystavit vzor hodnoty.|
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Viz poznámky.|Tato vlastnost musí být nastavena tak, aby označovala, zda ovládací prvek může mít hodnotu nastavenou programově nebo může uživatel upravovat.|
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Viz poznámky.|Tato vlastnost vrátí textový obsah ovládacího prvku pro úpravy. Pokud `IsPasswordProperty` je parametr nastaven na hodnotu `true` , musí tato vlastnost `InvalidOperationException` po vyžádání vyvolat.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Závislosti|Všechny ovládací prvky pro úpravy, které přijímají číselný rozsah, musí vystavovat vzor ovládacího prvku hodnota rozsahu.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|Viz poznámky.|Tato vlastnost musí být nejmenší hodnota, na kterou může být obsah ovládacího prvku pro úpravy nastaven.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|Viz poznámky.|Tato vlastnost musí být největší hodnota, na kterou může být obsah ovládacího prvku pro úpravy nastaven.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|Viz poznámky.|Tato vlastnost musí určovat počet desetinných míst, na která lze hodnotu nastavit. Pokud úpravy převezmou pouze celá čísla, `SmallChangeProperty` musí být 1. Pokud úpravy přebírají rozsah od 1,0 do 2,0, `SmallChangeProperty` musí být 0,1. Pokud ovládací prvek pro úpravy přebírá rozsah od 1,00 do 2,00, `SmallChangeProperty` musí být 0,001.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Tato vlastnost nemusí být vystavena na ovládacím prvku pro úpravy.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|Viz poznámky.|Tato vlastnost označí číselný obsah ovládacího prvku pro úpravy. Když klient nastaví přesnější hodnotu v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] rámci rozsahů určených ve `Minimum` `Maximum` vlastnostech a, vlastnost hodnota se automaticky zaokrouhlí na nejbližší přijatou hodnotu.|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní

V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, které musí být podporovány všemi ovládacími prvky pro úpravy. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událostí|Podpora|Poznámky|
|---------------------------------------------------------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Povinné|Žádné|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Povinné|Žádné|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Povinné|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Povinné|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Povinné|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Povinné|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>událost změny vlastnosti.|Povinné|Žádné|
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>událost změny vlastnosti.|Závislosti|Žádné|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změny vlastnosti.|Nikdy|Žádné|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>událost změny vlastnosti.|Nikdy|Žádné|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>událost změny vlastnosti.|Nikdy|Žádné|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>událost změny vlastnosti.|Nikdy|Žádné|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>událost změny vlastnosti.|Nikdy|Žádné|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>událost změny vlastnosti.|Nikdy|Žádné|
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>událost změny vlastnosti.|Závislosti|Pokud ovládací prvek podporuje vzor ovládacího prvku hodnota rozsahu, musí podporovat tuto událost.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Povinné|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Povinné|Žádné|

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.Edit>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
