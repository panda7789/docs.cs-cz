---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 88ef124176642137e363a36563a236d6c6029398
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48030716"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataGrid
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku DataGrid. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je představují sadu podmínek, které ovládací prvek musí splnit, aby bylo možné používat `ControlType` vlastnost. Podmínky zahrnují konkrétní pokyny ke [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzorů ovládacích prvků.  
  
 Typ ovládacího prvku DataGrid umožní uživateli snadno pracovat s položkami, které obsahují metadata ve sloupcích. Ovládací prvky mřížky dat mají řádky položek a sloupce s informacemi o těchto položek. Ovládací prvek zobrazení seznamu v aplikaci Microsoft Vista Explorer je příklad, který podporuje typ ovládacího prvku DataGrid.  
  
 Následující části definují požadovaný [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzorů ovládacích prvků a události pro typ ovládacího prvku DataGrid. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechna data ovládací prvky mřížky, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Požadované uživatelské rozhraní automatizace stromová struktura  
 Následující tabulka popisuje ovládací prvek zobrazení a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, které se vztahují k mřížce dat řídí a popisuje, co mohou být obsaženy v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, přečtěte si téma [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom – ovládací prvek zobrazení|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Záhlaví (0, 1 nebo 2)<br /><br /> <ul><li>HeaderItem (počet sloupců nebo řádků)</li></ul></li><li>Datové položky (0 nebo více; může být strukturovaná v hierarchii)</li></ul>|DataGrid<br /><br /> -Datové položky (0 nebo více; může být strukturovaná v hierarchii)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace uživatelského rozhraní vyžaduje  
 V následující tabulce jsou uvedeny vlastnosti, jejichž hodnota nebo definice je obzvláště důležité pro ovládací prvky dat mřížky. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, viz [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Vlastnost|Hodnota|Poznámky|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Nepodporuje. Pokud ohraničující obdélník. Pokud ne každý bod v rámci ohraničující obdélník je po kliknutí a provést specializované přístupů testování přepsat a zadat bod umožňující kliknutí.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Tato hodnota je stejný pro všechny architektury uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Hodnota této vlastnosti musí být vždy hodnotu True. To znamená, že ovládací prvek mřížky dat musí být vždy v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Hodnota této vlastnosti musí být vždy hodnotu True. To znamená, že ovládací prvek mřížky dat musí být vždy v zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může získat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|V části poznámky.|Pokud je statický text popisku této vlastnosti musí vystavit odkaz na tento ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"mřížky dat."|Lokalizovaný řetězec odpovídající typ ovládacího prvku DataGrid.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Ovládací prvek mřížky dat obvykle získá hodnotu pro jeho `Name` vlastnost z statický text popisku. Pokud není statický text popisku musí vývojář aplikace přiřadit hodnotu pro `Name` vlastnost. Hodnota `Name` vlastnost nesmí být nikdy textový obsah ovládacího prvku pro úpravy.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní vyžaduje  
 V následující tabulce jsou uvedeny vzorů ovládacích prvků vyžaduje to, že všechny ovládací prvky dat mřížky. Další informace o vzorů ovládacích prvků naleznete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|– Vzor ovládacích prvků|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Ano|Ovládací prvek mřížky dat, samotný vždy podporuje vzoru ovládacích prvků mřížka, protože položky, že obsahuje metadata, která se zobrazuje ve mřížky.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Závisí|Posun mřížky dat možnost závisí na obsah a zda jsou k dispozici posuvníky.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Závisí|Vyberte mřížky dat možnost závisí na obsahu.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Ano|Ovládací prvek mřížky dat má vždy záhlaví v jeho podstromu, musí se podporovat vzoru ovládacích prvků tabulka.|  
  
 Datové položky v datové mřížce kontejnery bude podporovat minimálně:  
  
-   Výběr položky – vzor ovládacích prvků (Pokud mřížky dat je volitelný)  
  
-   Posunout položku – vzor ovládacích prvků (Pokud je datové mřížce posuvný)  
  
-   – Vzor ovládacích prvků položky mřížky  
  
-   Položka tabulky – vzor ovládacích prvků  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vyžaduje to, že všechny ovládací prvky mřížky dat událostí. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> události změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> události změny vlastnosti.|Závisí|Podporuje-li ovládací prvek posuvníku vzor, musí podporovat této události.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> události změny vlastnosti.|Závisí|Podporuje-li ovládací prvek posuvníku vzor, musí podporovat této události.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> události změny vlastnosti.|Závisí|Podporuje-li ovládací prvek posuvníku vzor, musí podporovat této události.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> události změny vlastnosti.|Závisí|Podporuje-li ovládací prvek posuvníku vzor, musí podporovat této události.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> události změny vlastnosti.|Závisí|Podporuje-li ovládací prvek posuvníku vzor, musí podporovat této události.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> události změny vlastnosti.|Závisí|Podporuje-li ovládací prvek posuvníku vzor, musí podporovat této události.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Požadováno|Žádné|  
  
<a name="List_View_Control_Example"></a>   
## <a name="date-grid-control-type-example"></a>Ovládací prvek datum Grid – příklad typu  
 Následující obrázek ukazuje ovládací prvek zobrazení seznamu, který implementuje typ ovládacího prvku DataGrid.  
  
 ![Grafického ovládacího prvku zobrazení seznamu s dvěma datovými položkami](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Ovládací prvek zobrazení a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, které se vztahují na ovládací prvek zobrazení seznamu se zobrazí níže. Vzory ovládacích prvků pro každý prvek automation jsou uvedeny v závorkách.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom – ovládací prvek zobrazení|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid – (Výběr tabulky, mřížky)</li><li>Záhlaví<br /><br /> <ul><li>HeaderItem "Name" (vyvolání)</li><li>HeaderItem "Datum změny" (vyvolání)</li><li>HeaderItem "Size" (vyvolání)</li></ul></li><li>Skupina "Contoso" (TableItem, Položka GridItem, prvků SelectionItem, tabulka *, mřížky\*)<br /><br /> <ul><li>Datová položka Receivable.doc "účty" (prvků SelectionItem, vyvolat TableItem\*, Položka GridItem\*)</li><li>Datová položka Payable.doc "účty" (prvků SelectionItem, vyvolat TableItem\*, Položka GridItem\*)</li></ul></li></ul>|<ul><li>DataGrid – (Výběr tabulky, mřížky)</li><li>Skupina "Contoso" (TableItem, Položka GridItem, prvků SelectionItem, tabulka *, mřížky\*)<br /><br /> <ul><li>Datová položka Receivable.doc "účty" (prvků SelectionItem, vyvolat TableItem\*, Položka GridItem\*)</li><li>Datová položka Payable.doc "účty" (prvků SelectionItem, vyvolat TableItem\*, Položka GridItem\*)</li></ul></li></ul>|  
  
 * Předchozí příklad ukazuje prvek DataGrid, který obsahuje více úrovní ovládacích prvků. Ovládací prvek skupiny ("Contoso") obsahuje dva ovládací prvky datové položky ("Účty Receivable.doc" a "Payable.doc účtů"). Pár DataGrid/prvků GridItem je nezávislé na pár na jiné úrovni. Datová položka ovládací prvky v rámci skupiny můžete také zobrazuje jako typ ovládacího prvku ListItem, povolení je zobrazovat jasně vybrat více objektů, nikoli jako jednoduché datové prvky. V tomto příkladu neobsahuje dílčí prvky seskupených datové položky.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.DataGrid>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
