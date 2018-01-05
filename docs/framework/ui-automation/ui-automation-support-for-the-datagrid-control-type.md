---
title: "Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
caps.latest.revision: "32"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 3eb60004f4ffad0b62b10cf1e3ff5f28a3bf3fef
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataGrid
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku DataGrid. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je sadu podmínek, které ovládacího prvku musí splnit, aby bylo možné používat `ControlType` vlastnost. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků.  
  
 Typ ovládacího prvku DataGrid umožní uživateli snadno pracovat s položky, které obsahují metadata reprezentované ve sloupcích. Ovládací prvky mřížky dat mají řádky položky a sloupce informace o těchto položkách. Ovládacího prvku zobrazení seznamu v aplikaci Microsoft Vista Explorer je příklad, který podporuje typ ovládacího prvku DataGrid.  
  
 Následující části zadejte požadované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku DataGrid. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechna data ovládací prvky mřížky, jestli [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura stromu automatizace požadované uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, která se vztahují k mřížce dat řídí a popisuje, co může být obsažený v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení ovládacího prvku|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Záhlaví (0, 1 nebo 2)<br /><br /> <ul><li>HeaderItem (počet sloupců a řádků)</li></ul></li><li>Datová položka (0 nebo více; může být strukturován hierarchie)</li></ul>|DataGrid<br /><br /> -DataItem (0 nebo více; může být strukturován hierarchie)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí vlastnosti, jehož hodnota nebo definice je obzvláště důležité pro ovládací prvky mřížky data. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v části vlastnosti, [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Vlastnost|Hodnota|Poznámky|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélníku, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Podporováno, pokud je ohraničující obdélník. Není-li každého bodu v rámci ohraničující obdélník je můžete kliknout a provést specializované přístupů testování, přepsání a nabízí bod můžete kliknout.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Tato hodnota je stejný pro všechny rozhraní uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Hodnota této vlastnosti musí být vždy hodnotu True. To znamená, že ovládacího prvku mřížky dat musí být vždy v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Hodnota této vlastnosti musí být vždy hodnotu True. To znamená, že ovládacího prvku mřížky dat musí být vždy v zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|V části poznámky.|Pokud je statický text popisku této vlastnosti musí vystavit odkaz u daného ovládacího prvku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"datová mřížka"|Lokalizovaný řetězec odpovídající typ ovládacího prvku DataGrid.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Ovládací prvek mřížky dat obvykle získá hodnotu pro jeho `Name` vlastnost ze statického textu popisku. Pokud není k dispozici statický text popisku musí vývojář aplikace přidělíte hodnotu pro `Name` vlastnost. Hodnota `Name` vlastnost musí být nikdy textový obsah ovládacích prvků pro úpravy.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní požadované  
 Následující tabulka uvádí vzory ovládacích prvků, který je potřeba podporovat všechny ovládací prvky mřížky data. Další informace o vzory ovládacích prvků najdete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Vzor ovládacích prvků|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Ano|Ovládací prvek mřížky dat, samotné vždy podporuje vzoru ovládacích prvků mřížka, protože položky to obsahuje metadata, která je nastíněny v mřížce.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Závisí|Schopnost posuňte mřížky dat závisí na obsah a zda jsou k dispozici posuvníky.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Závisí|Umožňuje vybrat datová mřížka závisí na obsahu.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Ano|Ovládacího prvku mřížky data vždy má hlavičku v rámci jeho podstrom, takže vzoru ovládacích prvků tabulka musí být podporována.|  
  
 Datové položky v rámci kontejnerů mřížky dat bude podporovat minimálně:  
  
-   Výběr položky – vzor ovládacích prvků (Pokud datová mřížka je volitelný)  
  
-   Posuňte položka vzor ovládacích prvků (Pokud je datové mřížce posouvatelného)  
  
-   Položka vzor ovládacích prvků mřížky  
  
-   Položka tabulky – vzor ovládacích prvků  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] potřeba podporovat všechny ovládací prvky mřížky data události. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změny vlastnosti.|Závisí|Pokud ovládací prvek podporuje Scroll vzor, musí podporovat této události.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>událost změny vlastnosti.|Závisí|Pokud ovládací prvek podporuje Scroll vzor, musí podporovat této události.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>událost změny vlastnosti.|Závisí|Pokud ovládací prvek podporuje Scroll vzor, musí podporovat této události.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>událost změny vlastnosti.|Závisí|Pokud ovládací prvek podporuje Scroll vzor, musí podporovat této události.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>událost změny vlastnosti.|Závisí|Pokud ovládací prvek podporuje Scroll vzor, musí podporovat této události.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>událost změny vlastnosti.|Závisí|Pokud ovládací prvek podporuje Scroll vzor, musí podporovat této události.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Požadováno|Žádné|  
  
<a name="List_View_Control_Example"></a>   
## <a name="date-grid-control-type-example"></a>Příklad typ ovládacího prvku mřížky datum  
 Následující obrázek ukazuje ovládacího prvku zobrazení seznamu, který implementuje typ ovládacího prvku DataGrid.  
  
 ![Grafické ovládacího prvku zobrazení seznamu s dvěma datovými položkami](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, která se vztahují na ovládacího prvku zobrazení seznamu se zobrazí níže. Vzory ovládacích prvků pro jednotlivé elementy automatizace se zobrazí v závorkách.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení ovládacího prvku|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid – (Výběr tabulky, mřížky)</li><li>Záhlaví<br /><br /> <ul><li>HeaderItem "Name" (vyvolání)</li><li>HeaderItem "Datum změny" (vyvolání)</li><li>HeaderItem "Velikost" (vyvolání)</li></ul></li><li>Skupina "Contoso" (TableItem, GridItem, SelectionItem, tabulka *, mřížky\*)<br /><br /> <ul><li>Datová položka "účty Receivable.doc" (SelectionItem, vyvolání TableItem\*, GridItem\*)</li><li>Datová položka "účty Payable.doc" (SelectionItem, vyvolání TableItem\*, GridItem\*)</li></ul></li></ul>|<ul><li>DataGrid – (Výběr tabulky, mřížky)</li><li>Skupina "Contoso" (TableItem, GridItem, SelectionItem, tabulka *, mřížky\*)<br /><br /> <ul><li>Datová položka "účty Receivable.doc" (SelectionItem, vyvolání TableItem\*, GridItem\*)</li><li>Datová položka "účty Payable.doc" (SelectionItem, vyvolání TableItem\*, GridItem\*)</li></ul></li></ul>|  
  
 * V předchozím příkladu zobrazuje DataGrid, který obsahuje více úrovní ovládacích prvků. Ovládací prvek skupiny ("Contoso") obsahuje dvou ovládacích prvků DataItem ("Účty Receivable.doc" a "Payable.doc účtů"). Pár DataGrid/GridItem je nezávislé na pár na jiné úrovni. Ovládací prvky DataItem ve skupině mohou být zpřístupněny také jako typ ovládacího prvku ListItem, tím jim umožníte předkládané jasně vybrat více objektů, nikoli jako jednoduché datové prvky. Tento příklad nezahrnuje dílčí prvky seskupené datové položky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.DataGrid>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
