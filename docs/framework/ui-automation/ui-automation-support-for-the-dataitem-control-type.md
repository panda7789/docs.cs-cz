---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataItem
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Data Item control type
- Data Item control type
- control types, Data Item
ms.assetid: 181708fd-2595-4c43-9abd-75811627d64c
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: bef3393cda31e546afdb7b720cb08a2d45cb45bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409465"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataItem
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku DataItem. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] typu ovládacího prvku je sadu podmínek, které ovládacího prvku musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků.  
  
 Položku v seznamu kontaktů je příklad položky ovládacího prvku data. Ovládací prvek položky dat obsahuje informace, které je určen pro koncového uživatele. Ho je složitější než jednoduchý seznam položek, protože obsahuje rozsáhlejší informace.  
  
 Následující části zadejte požadované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku DataItem. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechna data ovládacích prvků položky, jestli [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura stromu automatizace požadované uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, která se vztahují na položku dat řídí a popisuje, co může být obsažený v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom – zobrazení ovládacího prvku|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|Datová položka<br /><br /> -Se liší (0 nebo více; může být strukturován hierarchie)|Datová položka<br /><br /> -Se liší (0 nebo více; může být strukturován hierarchie)|  
  
 Element položky dat v datové mřížce můžete hostovat různé objekty, včetně další vrstvu datových položek, nebo konkrétní mřížky prvky, jako jsou například text, obrázky, nebo ovládacích prvcích pro úpravy. Pokud datový prvek položka má určitý objekt role, by měly být vystaveny element jako určitý ovládací prvek typ; například ListItem typu ovládacího prvku pro volitelný datové položky v mřížce.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí vlastnosti, jehož hodnota nebo definice je obzvláště důležité pro ovládací prvky datových položek. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v části vlastnosti, [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Vlastnost|Hodnota|Poznámky|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélníku, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Podporováno, pokud je ohraničující obdélník. Není-li každého bodu v rámci ohraničující obdélník je můžete kliknout a provést specializované přístupů testování, přepsání a nabízí bod můžete kliknout.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Datová položka|Tato hodnota je stejný pro všechny rozhraní uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Ovládací prvek položky dat musí být vždy obsahu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Ovládací prvek položky dat musí být vždy ovládacího prvku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|V části poznámky.|Pokud ovládací prvek obsahuje stav, který se právě aktualizuje dynamicky, pak tato vlastnost musí být podporována tak, aby technologie usnadnění může přijímat aktualizace, když se změní stav daného elementu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|V části poznámky.|Toto je řetězcová hodnota, kterou přenese tak koncovým uživatelům základní objekt, který představuje položku. Příklady jsou "Soubor média" nebo "Kontaktovat".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Ovládací prvky datových položek nemají statický text popisku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"datová položka"|Lokalizovaný řetězec odpovídající typ ovládacího prvku DataItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Ovládací prvek položky dat vždy obsahuje primární textový element, který má vztah k co by uživatel přidružit jako nejvíce sémantického identifikátor pro položku.|  
  
<a name="_Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní požadované  
 Následující tabulka uvádí [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] řízení vzory potřeba podporovat všechny ovládací prvky datových položek. Další informace o vzory ovládacích prvků najdete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Vzor ovládacích prvků|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Závisí|Pokud položku dat můžete rozbalit nebo sbalit zobrazení a skrytí informace, musí být vzoru Rozbalit sbalit podporována.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Závisí|Datové položky budou podporovat vzoru položky v mřížce, pokud je kolekce položek dat k dispozici v rámci kontejneru, který může být jinými objekty navigaci položku k položce.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Závisí|Všechny datové položky podporují možnost být přesunut do oblasti zobrazení pomocí vzoru Scroll položky při jejich kontejner dat obsahuje více položek, než se vejde na obrazovce.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Ano|Položka výběru vzor označíte, pokud je vybrána položka musí podporovat všechny datové položky.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Závisí|Pokud příslušná položka dat je obsažena v typu ovládacího prvku mřížky Data pak bude podporovat tohoto vzoru.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Závisí|Pokud položku dat obsahuje stavu, který můžete cyklicky.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závisí|Pokud primární text položky dat upravovat musí podporovat vzoru hodnotu.|  
  
<a name="Working_with_Data_Items_in_Large_Lists"></a>   
## <a name="working-with-data-items-in-large-lists"></a>Práce s datovými položkami ve velkých seznamů  
 Velké seznamy jsou často data Virtualizovat v rámci [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] rozhraní, které vám pomohou v výkonu. Z toho důvodu nelze použít automatizace uživatelského rozhraní klienta [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] funkci dotaz tak, aby scrape obsah úplného stromu stejným způsobem, který ho můžete v kontejnerech další položky. Klient by měla položka přejděte do zobrazení (nebo rozbalte ovládacího prvku zobrazíte všechny možnosti cenné) před přístup k kompletní informace z datové položky.  
  
 Při volání metody `SetFocus` na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element položky dat [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] vrátí úspěšně a způsobit fokus být nastavena na úpravy v rámci podstrom položky dat případu.  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřeba podporovat všechny ovládací prvky datových položek. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> událost změny vlastnosti.|Závisí|Žádné|  
  
<a name="Data_Item_Control_Type_Example"></a>   
## <a name="dataitem-control-type-example"></a>Příklad pro typ ovládacího prvku DataItem  
 Následující obrázek ukazuje typu ovládacího prvku DataItem v ovládacím prvku zobrazení seznamu s podporou bohaté informace pro dané sloupce.  
  
 ![Grafické ovládacího prvku zobrazení seznamu s dvěma datovými položkami](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Zobrazení ovládacího prvku a zobrazení obsahu z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, která se vztahují na ovládací prvek položky dat se zobrazí níže. Vzory ovládacích prvků pro jednotlivé elementy automatizace se zobrazí v závorkách. Skupina "Contoso" je také součástí mřížky hostitelského ovládacího prvku mřížky Data.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom – zobrazení ovládacího prvku|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-Skupiny "Contoso" (tabulky, mřížky)<br />-DataItem "účty Receivable.doc" (TableItem, GridItem, SelectionItem, vyvolání)<br />-Image "Účty Receivable.doc"<br />-Upravte "Name" (TableItem GridItem, hodnota "Receivable.doc účtů")<br />-Upravit "Datum změny" (TableItem GridItem, hodnota "8/25/2006 15:29:00")<br />-Upravte "Velikost" (GridItem, TableItem, hodnota "11.0 KB)<br />-DataItem "účty Payable.doc" (TableItem, GridItem, SelectionItem, vyvolání)<br />-   ...|-Skupiny "Contoso" (tabulky, mřížky)<br />-DataItem "účty Receivable.doc" (TableItem, GridItem, SelectionItem, vyvolání)<br />-Image "Účty Receivable.doc"<br />-Upravte "Name" (TableItem GridItem, hodnota "Receivable.doc účtů")<br />-Upravit "Datum změny" (TableItem GridItem, hodnota "8/25/2006 15:29:00")<br />-Upravte "Velikost" (GridItem, TableItem, hodnota "11.0 KB)<br />-DataItem "účty Payable.doc" (TableItem, GridItem, SelectionItem, vyvolání)<br />-   …|  
  
 Pokud Mřížka představuje seznam položek, které lze vybírat, mohou být zpřístupněny odpovídající prvky uživatelského rozhraní s typ ovládacího prvku ListItem místo typ ovládacího prvku DataItem. V předchozím příkladu elementy DataItem ("Účty Receivable.doc" a "Payable.doc účtů") ve skupině ("Contoso") lze vylepšit vystavení jako typy ovládacích prvků ListItem, protože tento typ podporuje již vzor SelectionItem ovládacích prvků.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.DataItem>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
