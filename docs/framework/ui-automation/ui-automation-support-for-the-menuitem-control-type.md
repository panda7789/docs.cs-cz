---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuItem
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu Item
- Menu Item control type
- UI Automation, Menu Item control type
ms.assetid: 54bce311-3d23-40b9-ba90-1bdbdaf8fbba
ms.openlocfilehash: a1dba653a308bc4fa865e8ee362893cbd15d68da
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041293"
---
# <a name="ui-automation-support-for-the-menuitem-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuItem

> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.

Toto téma poskytuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podpoře pro typ ovládacího prvku MenuItem. Popisuje [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] stromovou strukturu ovládacího prvku a poskytuje vlastnosti a vzory ovládacích prvků, které jsou požadovány pro typ ovládacího prvku MenuItem.

Ovládací prvek nabídky umožňuje hierarchická organizaci prvků spojených s příkazy a obslužnými rutinami událostí. V [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] typické aplikaci panel nabídek obsahuje několik položek nabídky (například **soubor**, **Úpravy**a **okno**) a každá položka nabídky zobrazuje nabídku. Nabídka obsahuje kolekci položek nabídky (například **Nový**, **otevřít**a **Zavřít**), která se dá rozšířit tak, aby se zobrazily další položky nabídky, nebo když se klikne na tlačítko, provede se konkrétní akce. Položka nabídky může být hostována v nabídce, panelu nabídek nebo panelu nástrojů.

Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku MenuItem. Požadavky platí pro všechny ovládací prvky seznamu bez ohledu [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]na to, [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]zda, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]nebo. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Požadovaná stromová struktura automatizace uživatelského rozhraní

Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahu stromové struktury, které se vztahují k ovládacím prvkům položky nabídky, a popisuje, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).

|Zobrazení ovládacích prvků|Zobrazení obsahu|
|------------------|------------------|
|MenuItem – Help<br /><br /> <ul><li>Nabídka (podnabídka položky nabídky Help)<br /><br /> <ul><li>MenuItem – témata nápovědy</li><li>MenuItem "o programu Poznámkový blok"</li></ul></li></ul>|MenuItem – Help<br /><br /> -MenuItem témata nápovědy<br />-MenuItem "o programu Poznámkový blok"|

Zobrazení ovládacího prvku položky nabídky má [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu zobrazenou výše. Všimněte si, že položka nabídky **help** je zahrnutá k lepší ilustraci struktury v typické nabídce v hierarchii podnabídky.

V zobrazení obsahu se ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře nevyskytuje nabídka, protože nedává koncovému uživateli smysluplné informace.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní

V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice je obzvláště relevantní pro ovládací prvky položek nabídky. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostech najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).

|Vlastnost|Value|Popis|
|--------------|-----------|-----------------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečná napříč všemi ovládacími prvky v aplikaci.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Vnější obdélník, který obsahuje celý ovládací prvek.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Podporováno, pokud je ohraničen obdélník. Pokud není k dispozici žádný bod v ohraničujícím obdélníku a provádíte specializované testování přístupů, přepíšete a získáte bod, který je k dispozici.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může obdržet fokus klávesnice, musí podporovat tuto vlastnost.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Ovládací prvek položka nabídky je součástí zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahu stromu a je označen jako označený jako název.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Bez popisku|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|MenuItem|Tato hodnota je stejná pro všechny architektury uživatelského rozhraní.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"položka nabídky"|Lokalizovaný řetězec odpovídající typu ovládacího prvku MenuItem.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Pravda|Ovládací prvek položka nabídky není nikdy zahrnutý v zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahu stromu.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Pravda|Ovládací prvek položky nabídky musí být vždy součástí zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacího prvku stromové struktury.|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns"></a>Požadované vzory ovládacího prvku automatizace uživatelského rozhraní

V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vzory ovládacích prvků, které jsou požadovány pro podporu ovládacích prvků položky nabídky. Další informace o vzorech ovládacích prvků naleznete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).

|Vlastnost vzoru ovládacího prvku|Podpora|Poznámky|
|------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Závislosti|Pokud ovládací prvek lze rozšířit nebo sbalit, implementovat <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.|
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Závislosti|Pokud ovládací prvek provede jednu akci nebo příkaz, implementujte <xref:System.Windows.Automation.Provider.IInvokeProvider>.|
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Závislosti|Pokud ovládací prvek představuje možnost, kterou lze zapnout nebo vypnout, implementovat <xref:System.Windows.Automation.Provider.IToggleProvider>.|
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Závislosti|Pokud ovládací prvek slouží k výběru ze seznamu možností mezi položkami nabídky, implementujte <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.|

<a name="UI_Automation_Events_for_Menu_Item"></a>

## <a name="ui-automation-events-for-menu-item"></a>Události automatizace uživatelského rozhraní pro položku nabídky

V následující tabulce jsou uvedeny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] události přidružené k ovládacímu prvku položky nabídky.

|Událost|Podpora|Vysvětlení|
|-----------|-------------|-----------------|
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závislosti|Musí být vyvolána, pokud ovládací prvek podporuje model ovládacího prvku Invoke.|
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>událost změny vlastnosti.|Závislosti|Musí být vyvolána, pokud ovládací prvek podporuje vzor ovládacího prvku přepínací tlačítko.|
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>událost změny vlastnosti.|Závislosti|Musí být vyvolána, pokud ovládací prvek podporuje rozbalení řídicího vzoru pro sbalení.|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Závislosti|Žádné|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní

V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, které musí být podporovány všemi ovládacími prvky položek nabídky. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událostí|Podpora/hodnota|Poznámky|
|---------------------------------------------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závislosti|Žádné|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Závislosti|Žádné|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Závislosti|Žádné|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Závislosti|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Požadováno|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Požadováno|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Požadováno|Žádné|
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>událost změny vlastnosti.|Závislosti|Žádné|
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>událost změny vlastnosti.|Závislosti|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|

<a name="Legacy_Issues"></a>

## <a name="legacy-issues"></a>Starší problémy

Přepínač Pattern bude podporován pouze v případě, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] že je položka nabídky zaškrtnuta a lze ji programově určit, aby podporovala přepínací vzorek. Vzhledem k tomu, že položka nabídkynevystavuje,zdamábýtmožnostkontrolována,jepodporovánvzorvolání,pokudpoložkanabídkynenízaškrtnuta.[!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] Bude provedena výjimka, která bude vždy podporovat vzor volání, i pro položky nabídky, které by měly podporovat pouze přepínací vzorek. To je proto, že klienti nebudou zaměňováni, že prvek, který podporoval volání metody Invoke (Pokud položka nabídky byla nezaškrtnuta), již není po zaškrtnutí tohoto vzoru nadále podporován.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.ControlType.MenuItem>
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
