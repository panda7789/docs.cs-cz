---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku úprav
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Edit
- Edit control type
- UI Automation, Edit control type
ms.assetid: 6db9d231-c0a0-4e17-910e-ac80357f774f
ms.openlocfilehash: 5cce634e2ba80b496b808a4ec66c4c06118b5989
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041709"
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku úprav

> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.

Toto téma poskytuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podpoře pro typ ovládacího prvku pro úpravy. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nástroji je typ ovládacího prvku sada podmínek, které musí ovládací prvek splňovat, aby bylo možné <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost použít. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků.

Ovládací prvky pro úpravy umožňují uživateli zobrazit a upravit jednoduchý řádek textu bez podpory formátovaného formátu.

Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku pro úpravy. Požadavky platí pro všechny ovládací prvky pro úpravy bez [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]ohledu na to [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)], zda, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]nebo. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Požadovaná stromová struktura automatizace uživatelského rozhraní

Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahu stromové struktury, které se vztahují k ovládacím prvkům pro úpravy, a popisuje, co může být v každém zobrazení obsaženo. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).

|Zobrazení ovládacích prvků|Zobrazení obsahu|
|------------------|------------------|
|Upravit|Upravit|

Ovládací prvky, které implementují typ ovládacího prvku pro úpravy, budou mít vždy nulové posuvníky v zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacího prvku stromu, protože se jedná o ovládací prvek s jedním řádkem. Jeden řádek textu se může v některých scénářích rozložení zalamovat. Typ ovládacího prvku pro úpravy je nejvhodnější pro uchovávání malých objemů upravitelných a volitelných textů.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní

V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice jsou obzvláště důležité pro úpravy ovládacích prvků. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostech najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Majetek|Value|Poznámky|
|------------------------------------------------------------------------------------|-----------|-----------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečná napříč všemi ovládacími prvky v aplikaci.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Vnější obdélník, který obsahuje celý ovládací prvek.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Ovládací prvek pro úpravy musí mít upravitelný bod, který umožňuje vstup fokusu na část úpravy ovládacího prvku, když uživatel klikne myší na tlačítko.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může obdržet fokus klávesnice, musí podporovat tuto vlastnost.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Název ovládacího prvku pro úpravy je obvykle generován z popisku statického textu. Pokud není k dispozici žádný statický textový popisek, hodnota `Name` vlastnosti musí být přiřazena vývojářem aplikace. `Name` Vlastnost by nikdy neměla obsahovat textový obsah ovládacího prvku pro úpravy.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Pokud je k ovládacímu prvku přidružen statický textový popisek, musí tato vlastnost vystavit odkaz na tento ovládací prvek. Pokud je ovládací prvek text dílčí součástí jiného ovládacího prvku, nebude mít `LabeledBy` sadu vlastností.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Upravit|Tato hodnota je stejná pro všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektury.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|úpravě|Lokalizovaný řetězec odpovídající typu ovládacího prvku pro úpravy.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Pravda|Textové pole je vždy součástí zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahu stromu.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Pravda|Textové pole je vždy součástí zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacího prvku stromové struktury.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|Viz poznámky.|Musí být nastaven na hodnotu true u ovládacích prvků pro úpravy, které obsahují hesla. Pokud ovládací prvek pro úpravy obsahuje obsah hesla, lze tuto vlastnost použít čtečkou obrazovky k určení, zda mají být stisknuty klávesy pro čtení, jak je uživatel zadá.|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns-and-properties"></a>Požadované vzory a vlastnosti ovládacího prvku automatizace uživatelského rozhraní

V následující tabulce jsou uvedeny vzory ovládacích prvků, které musí být podporovány všemi ovládacími prvky pro úpravy. Další informace o vzorech ovládacích prvků naleznete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).

|Řídicí vzorek/vlastnost vzoru ovládacího prvku|Podpora/hodnota|Poznámky|
|-----------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.Provider.ITextProvider>|Závislosti|Ovládací prvky pro úpravy by měly podporovat vzor ovládacího prvku text, protože podrobné informace o textu by měly být vždy k dispozici pro klienty.|
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závislosti|Všechny ovládací prvky pro úpravy, které přijímají řetězec, musí vystavit vzor hodnoty.|
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|Viz poznámky.|Tato vlastnost musí být nastavena tak, aby označovala, zda ovládací prvek může mít hodnotu nastavenou programově nebo může uživatel upravovat.|
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|Viz poznámky.|Tato vlastnost vrátí textový obsah ovládacího prvku pro úpravy. Pokud je parametr nastaven na `true`hodnotu, musí `InvalidOperationException` Tato vlastnost po vyžádání vyvolat. `IsPasswordProperty`|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Závislosti|Všechny ovládací prvky pro úpravy, které přijímají číselný rozsah, musí vystavovat vzor ovládacího prvku hodnota rozsahu.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|Viz poznámky.|Tato vlastnost musí být nejmenší hodnota, na kterou může být obsah ovládacího prvku pro úpravy nastaven.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|Viz poznámky.|Tato vlastnost musí být největší hodnota, na kterou může být obsah ovládacího prvku pro úpravy nastaven.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|Viz poznámky.|Tato vlastnost musí určovat počet desetinných míst, na která lze hodnotu nastavit. Pokud úpravy převezmou pouze celá čísla, `SmallChangeProperty` musí být 1. Pokud úpravy přebírají rozsah od 1,0 do 2,0, `SmallChangeProperty` musí být 0,1. Pokud ovládací prvek pro úpravy přebírá rozsah od 1,00 do 2,00 `SmallChangeProperty` , musí být 0,001.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Tato vlastnost nemusí být vystavena na ovládacím prvku pro úpravy.|
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|Viz poznámky.|Tato vlastnost označí číselný obsah ovládacího prvku pro úpravy. Když [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klient nastaví přesnější hodnotu v rámci rozsahů určených `Minimum` ve vlastnostech a `Maximum` , vlastnost hodnota se automaticky zaokrouhlí na nejbližší přijatou hodnotu.|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní

V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, které musí být podporovány všemi ovládacími prvky pro úpravy. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událostí|Podpora|Poznámky|
|---------------------------------------------------------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Požadováno|Žádné|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Požadováno|Žádné|
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Požadováno|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Požadováno|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Požadováno|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Požadováno|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>událost změny vlastnosti.|Požadováno|Žádné|
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>událost změny vlastnosti.|Závislosti|Žádné|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změny vlastnosti.|Nikdy|Žádné|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>událost změny vlastnosti.|Nikdy|Žádné|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>událost změny vlastnosti.|Nikdy|Žádné|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>událost změny vlastnosti.|Nikdy|Žádné|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>událost změny vlastnosti.|Nikdy|Žádné|
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>událost změny vlastnosti.|Nikdy|Žádné|
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>událost změny vlastnosti.|Závislosti|Pokud ovládací prvek podporuje vzor ovládacího prvku hodnota rozsahu, musí podporovat tuto událost.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.ControlType.Edit>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
