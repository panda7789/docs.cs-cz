---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataItem
description: Získejte informace o podpoře automatizace uživatelského rozhraní pro typ ovládacího prvku DataItem. Seznamte se s požadovanou stromovou strukturou, vlastnostmi, vzory ovládacích prvků a událostmi.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
ms.openlocfilehash: c1b149e1033303e98bd150e62c6344b60eec1f93
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167976"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataItem
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma poskytuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podpoře pro typ ovládacího prvku DataItem. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] typu ovládacího prvku je sada podmínek, které musí ovládací prvek splňovat, aby bylo možné vlastnost použít <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků.  
  
 Položka v seznamu kontaktů je příkladem ovládacího prvku datová položka. Ovládací prvek datová položka obsahuje informace, které mají zájem o koncového uživatele. Je složitější než jednoduchá položka seznamu, protože obsahuje bohatší informace.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku DataItem. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Požadavky platí pro všechny ovládací prvky datových položek, ať už [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] , Win32 nebo model Windows Forms.  
  
## <a name="required-ui-automation-tree-structure"></a>Požadovaná stromová struktura automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, které se vztahují k ovládacím prvkům datových položek, a popisuje, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zobrazení stromového řízení|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataItem<br /><br /> – Liší se (0 nebo více; může být strukturované v hierarchii).|DataItem<br /><br /> – Liší se (0 nebo více; může být strukturované v hierarchii).|  
  
 Prvek datové položky v datové mřížce může hostovat různé objekty, včetně jiné vrstvy datových položek nebo určitých prvků mřížky, jako jsou text, obrázky nebo textové ovládací prvky. Pokud prvek datové položky má konkrétní roli objektu, měl by být element vystaven jako konkrétní typ ovládacího prvku; například typ ovládacího prvku ListItem pro selektivní datovou položku v mřížce.  
  
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny vlastnosti, jejichž hodnota nebo definice jsou obzvláště důležité pro ovládací prvky datových položek. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostech najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|Vlastnost|Hodnota|Poznámky|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečná napříč všemi ovládacími prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Vnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Podporováno, pokud je ohraničen obdélník. Pokud není k dispozici žádný bod v ohraničujícím obdélníku a provádíte specializované testování přístupů, přepíšete a získáte bod, který je k dispozici.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataItem|Tato hodnota je stejná pro všechny architektury uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Ano|Ovládací prvek datové položky musí být vždy obsah.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Ano|Ovládací prvek datové položky musí být vždy ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může obdržet fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Viz poznámky.|Pokud ovládací prvek obsahuje stav, který se dynamicky aktualizuje, musí být tato vlastnost podporovaná, aby technologie pro usnadnění mohli dostávat aktualizace, když se změní stav prvku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Viz poznámky.|Toto je řetězcová hodnota, která odpovídá koncovému uživateli základnímu objektu, který položka představuje. Příklady jsou "mediální soubor" nebo "kontakt".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Ovládací prvky datové položky neobsahují statický textový popisek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"datová položka"|Lokalizovaný řetězec odpovídající typu ovládacího prvku DataItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Ovládací prvek datová položka obsahuje vždy primární textový prvek, který souvisí s tím, co by uživatel přidružil jako nejvíc sémantický identifikátor položky.|  
  
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory ovládacího prvku automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] vzory ovládacích prvků, které musí být podporovány všemi ovládacími prvky datových položek. Další informace o vzorech ovládacích prvků naleznete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vzor ovládacího prvku|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Závislosti|Pokud lze datovou položku Rozbalit nebo sbalit pro zobrazení a skrytí informací, je nutné použít vzor rozbalit sbalení.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Závislosti|Datové položky budou podporovat model položky mřížky, je-li kolekce datových položek k dispozici v rámci kontejneru, který může být prostorově převedený na položku.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Závislosti|Všechny položky dat podporují možnost posouvání v zobrazení pomocí vzoru posouvaných položek, když jejich kontejner dat obsahuje více položek, než lze na obrazovku vejít.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Ano|Všechny položky dat musí podporovat vzor výběrové položky, který určuje, kdy je položka vybrána.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Závislosti|Je-li datová položka obsažena v rámci typu ovládacího prvku datové mřížky, bude tento model podporovat.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Závislosti|Pokud datová položka obsahuje stav, který může být cyklicky vytvořen.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závislosti|Pokud je primární text položky dat upravitelný, musí být podporován vzorec hodnoty.|  
  
## <a name="working-with-data-items-in-large-lists"></a>Práce s datovými položkami ve velkých seznamech  
 Rozsáhlé seznamy jsou často virtualizované data v rámci [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] platforem, což pomáhá při výkonu. Z tohoto důvodu nemůže klient automatizace uživatelského rozhraní použít [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] funkci dotazu k vyřazení obsahu úplného stromu stejným způsobem jako v kontejnerech dalších položek. Klient by měl položku posunout na zobrazení (nebo rozšířit ovládací prvek tak, aby zobrazoval všechny důležité možnosti) před přístupem k plné sadě informací z datové položky.  
  
 Při volání `SetFocus` na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvek pro datovou položku bude případ programu Microsoft Windows Explorer úspěšně vrácen a způsobí, že se fokus nastaví na hodnotu upravit v podstromu datové položky.  
  
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, které musí být podporovány všemi ovládacími prvky datových položek. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událostí|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Povinné|Žádné|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Povinné|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Povinné|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Povinné|Žádné|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>událost změny vlastnosti.|Závislosti|Žádné|  
  
## <a name="dataitem-control-type-example"></a>Příklad typu ovládacího prvku DataItem  
 Následující obrázek znázorňuje typ ovládacího prvku DataItem v ovládacím prvku zobrazení seznamu s podporou pro rozšířené informace pro sloupce.  
  
 ![Obrázek ovládacího prvku zobrazení seznamu se dvěma datovými položkami](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, které se vztahují k ovládacímu prvku datová položka, se zobrazuje níže. Vzory ovládacích prvků pro každý element automatizace jsou uvedeny v závorkách. Skupina "contoso" je také součástí mřížky ovládacího prvku hostitele datové mřížky.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zobrazení stromového řízení|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-Group "contoso" (tabulka, mřížka)<br />-DataItem "Accounts Receivable.doc" (TableItem, GridItem, ovládacích SelectionItem, Invoke)<br />-Image "Receivable.doc účtů"<br />-Upravit "název" (TableItem, GridItem, value "Accounts Receivable.doc)<br />-Edit "Date Modified" (TableItem; GridItem; value "8/25/2006 3:29 PM")<br />-Editing "size" (GridItem; TableItem; value "11,0 KB)<br />-DataItem "Accounts Payable.doc" (TableItem, GridItem, ovládacích SelectionItem, Invoke)<br />-   ...|-Group "contoso" (tabulka, mřížka)<br />-DataItem "Accounts Receivable.doc" (TableItem, GridItem, ovládacích SelectionItem, Invoke)<br />-Image "Receivable.doc účtů"<br />-Upravit "název" (TableItem, GridItem, value "Accounts Receivable.doc)<br />-Edit "Date Modified" (TableItem; GridItem; value "8/25/2006 3:29 PM")<br />-Editing "size" (GridItem; TableItem; value "11,0 KB)<br />-DataItem "Accounts Payable.doc" (TableItem, GridItem, ovládacích SelectionItem, Invoke)<br />-   …|  
  
 Pokud Mřížka představuje seznam volitelných položek, mohou být příslušné prvky uživatelského rozhraní zpřístupněny pomocí typu ovládacího prvku ListItem místo typu ovládacího prvku DataItem. V předchozím příkladu lze zlepšit prvky DataItem ("Accounts Receivable.doc" a "Accounts Payable.doc") pod Group ("contoso") tím, že je zveřejňujete jako typy ovládacích prvků ListItem, protože tento typ již podporuje vzor ovládacích prvků ovládacích SelectionItem.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.DataItem>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
