---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuItem
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Menu Item
- Menu Item control type
- UI Automation, Menu Item control type
ms.assetid: 54bce311-3d23-40b9-ba90-1bdbdaf8fbba
ms.openlocfilehash: 236f4ff5bfd709426975c7a8c1d828eb8b3fe89b
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57680175"
---
# <a name="ui-automation-support-for-the-menuitem-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuItem

> [!NOTE]
> Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).

Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku MenuItem. Popisuje ovládacího prvku [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] stromové struktury a poskytuje vlastnosti a vzorů ovládacích prvků, které jsou požadovány pro typ ovládacího prvku MenuItem.

Ovládací prvek nabídky umožňuje hierarchická uspořádání elementů spojených s příkazy a obslužnými rutinami událostí. V typické [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] aplikace, panel nabídek obsahuje několik položek nabídky (například **souboru**, **upravit**, a **okno**), a každá položka nabídky zobrazí nabídku. Nabídka obsahuje kolekci položek nabídky (například **nový**, **otevřít**, a **Zavřít**), které je možné rozšířit zobrazit další položky nabídky nebo provedení určité akce při kliknutí na. Položka nabídky je možné hostovat v nabídce, panel nabídky nebo panelu nástrojů.

Následující části definují požadovaný [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzorů ovládacích prvků a události pro typ ovládacího prvku MenuItem. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechny ovládací prvky seznamu, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].

<a name="Required_UI_Automation_Tree_Structure"></a>

## <a name="required-ui-automation-tree-structure"></a>Požadované uživatelské rozhraní automatizace stromová struktura

Následující tabulka popisuje ovládací prvek zobrazení a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom, který se vztahuje k položce nabídky ovládací prvky a popisuje, co mohou být obsaženy v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, přečtěte si téma [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).

|Ovládací prvek zobrazení|Zobrazení obsahu|
|------------------|------------------|
|Položku nabídky "Help"<br /><br /> <ul><li>Nabídka (dílčí položky nabídky nápovědy)<br /><br /> <ul><li>Položku nabídky "Nápovědu"</li><li>Položku nabídky "O Poznámkový blok"</li></ul></li></ul>|Položku nabídky "Help"<br /><br /> -MenuItem "nápovědu"<br />-MenuItem "O Poznámkový blok"|

Obsahuje ovládací prvek zobrazení ovládacího prvku položky nabídky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura uvedené výše. Všimněte si, že **pomáhají** položka nabídky je zahrnuta, abychom vám lépe předvedli struktury v typické nabídky do podnabídky hierarchie.

Pro zobrazení obsahu nabídky chybí z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, protože neznamená důležité informace pro koncového uživatele.

<a name="Required_UI_Automation_Properties"></a>

## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace uživatelského rozhraní vyžaduje

Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacích prvků položek na vlastnosti, jejichž hodnota nebo definice je obzvláště důležité pro nabídky. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, viz [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).

|Vlastnost|Hodnota|Popis|
|--------------|-----------|-----------------|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélník, který obsahuje celý ovládací prvek.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Nepodporuje. Pokud ohraničující obdélník. Pokud ne každý bod v rámci ohraničující obdélník je po kliknutí a provést specializované přístupů testování přepsat a zadat bod umožňující kliknutí.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může získat fokus klávesnice, musí podporovat tuto vlastnost.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Ovládací prvek položky nabídky je zahrnuta v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu a vlastní popisek s názvem.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Žádný popisek.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Položku nabídky|Tato hodnota je stejný pro všechny architektury uživatelského rozhraní.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"nabídka"|Lokalizovaný řetězec odpovídající typ ovládacího prvku MenuItem.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Pravda|Zobrazení obsahu nikdy součástí ovládací prvek položky nabídky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Pravda|Ovládací prvek položky nabídky musí vždy obsahovat zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|

<a name="Required_UI_Automation_Control_Patterns"></a>

## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní vyžaduje

Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit vzory vyžaduje to, že ovládací prvky položek nabídky. Další informace o vzorů ovládacích prvků naleznete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).

|Vlastnosti ovládacího prvku modelu|Podpora|Poznámky|
|------------------------------|-------------|-----------|
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Závisí|Pokud ovládacího prvku můžete rozbalit nebo sbalit, implementovat <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.|
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Závisí|Pokud ovládací prvek provede jednu akci nebo příkaz, implementovat <xref:System.Windows.Automation.Provider.IInvokeProvider>.|
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Závisí|Pokud ovládací prvek představuje možnost, která můžete zapnout nebo vypnout, implementovat <xref:System.Windows.Automation.Provider.IToggleProvider>.|
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Závisí|Pokud ovládací prvek se používá pro výběr ze seznamu možností mezi položek nabídky, implementovat <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.|

<a name="UI_Automation_Events_for_Menu_Item"></a>

## <a name="ui-automation-events-for-menu-item"></a>Události automatizace uživatelského rozhraní pro položku nabídky

Následující tabulce jsou uvedeny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] událostí spojených s ovládacím prvkem položky nabídky.

|Událost|Podpora|Vysvětlení|
|-----------|-------------|-----------------|
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závisí|Musí být vyvolány, když ovládací prvek podporuje Invoke – vzor ovládacích prvků.|
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> události změny vlastnosti.|Závisí|Musí být vyvolány, když ovládací prvek podporuje přepínání – vzor ovládacích prvků.|
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> události změny vlastnosti.|Závisí|Musí být vyvolány, když ovládací prvek podporuje Rozbalit sbalit – vzor ovládacích prvků.|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Závisí|Žádné|

<a name="Required_UI_Automation_Events"></a>

## <a name="required-ui-automation-events"></a>Události automatizace uživatelského rozhraní vyžaduje

Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřebné to, že všechny ovládací prvky položek nabídky. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).

|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Události|Podpora/hodnota|Poznámky|
|---------------------------------------------------------------------------------|--------------------|-----------|
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závisí|Žádná|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Závisí|Žádná|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Závisí|Žádná|
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Závisí|Žádná|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> události změny vlastnosti.|Požadováno|Žádná|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> události změny vlastnosti.|Požadováno|Žádná|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> události změny vlastnosti.|Požadováno|Žádná|
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> události změny vlastnosti.|Závisí|Žádná|
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> události změny vlastnosti.|Závisí|Žádná|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádná|
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádná|

<a name="Legacy_Issues"></a>

## <a name="legacy-issues"></a>Starší verze problémy

Přepnout model bude pouze podporovaná, až [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] položka nabídky je zaškrtnuto a můžete programově určit potřebných k podpoře vzoru přepínání. Vzhledem k tomu, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] nevystavuje položku nabídky, zda má schopnost kontrolovat, vyvolat vzor bude podporovat, není-li zaškrtnuta položka nabídky. Vždy vyvolat vzor podporovat i pro položky nabídky, které by měly podporovat pouze vzoru přepínání bude proveden výjimku. Jedná se proto, že klienti nebudou zaměňovat, že element, který byl podporující vzor vyvolání (Pokud položku nabídky zrušila) už podporuje vzor, jakmile bude zaškrtnuté políčko.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.ControlType.MenuItem>
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
