---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
ms.openlocfilehash: 69532c9836876c25e9f31395213b1a89e0307dcd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179806"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataGrid
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] obsahuje informace o podpoře typu ovládacího prvku DataGrid. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programu je typ ovládacího prvku sada podmínek, které `ControlType` musí ovládací prvek splňovat, aby bylo možné použít vlastnost. Podmínky zahrnují zvláštní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, hodnoty vlastností a vzory ovládacích prvku.  
  
 Typ ovládacího prvku DataGrid umožňuje uživateli snadno pracovat s položkami, které obsahují metadata reprezentovaná ve sloupcích. Ovládací prvky datové mřížky mají řádky položek a sloupce informací o těchto položkách. Ovládací prvek Zobrazení seznamu v aplikaci Microsoft Vista Explorer je příklad, který podporuje typ ovládacího prvku DataGrid.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzory ovládacích prvku a události pro typ ovládacího prvku DataGrid. Požadavky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] platí pro všechny ovládací [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]prvky datové mřížky, ať už , Win32 nebo Windows Forms.  
  
## <a name="required-ui-automation-tree-structure"></a>Požadovaná struktura stromu automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a zobrazení obsahu stromu, který se týkající se ovládacích prvků datové mřížky, a popisuje, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu naleznete v [tématu Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení ovládacího prvku|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Záhlaví (0, 1 nebo 2)<br /><br /> <ul><li>HeaderItem (počet sloupců nebo řádků)</li></ul></li><li>DataItem (0 nebo více; může být strukturována v hierarchii)</li></ul>|DataGrid<br /><br /> - DataItem (0 nebo více; může být strukturována v hierarchii)|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny vlastnosti, jejichž hodnota nebo definice jsou obzvláště důležité pro ovládací prvky datové mřížky. Další informace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o vlastnostech naleznete v [tématu Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|Vlastnost|Hodnota|Poznámky|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečný napříč všechny ovládací prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Nejvzdálenější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Podporováno, pokud je ohraničující obdélník. Pokud není možné kliknout na každý bod v ohraničovacím obdélníku a provedete specializované testování přístupů, přepište a poskytněte bod, na který lze kliknout.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Tato hodnota je stejná pro všechny architektury ui.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Hodnota této vlastnosti musí být vždy True. To znamená, že ovládací prvek mřížky dat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] musí být vždy v zobrazení obsahu stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Hodnota této vlastnosti musí být vždy True. To znamená, že ovládací prvek mřížky dat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] musí být vždy v ovládacím zobrazení stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Pokud je statický textový popisek pak tato vlastnost musí vystavit odkaz na tento ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"datová mřížka"|Lokalizovaný řetězec odpovídající typu ovládacího prvku DataGrid.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Ovládací prvek mřížky dat obvykle `Name` získá hodnotu pro svou vlastnost ze statického textového popisku. Pokud neexistuje statický textový popisek, musí vývojář aplikace `Name` přiřadit hodnotu pro vlastnost. Hodnota vlastnosti `Name` nesmí být nikdy textový obsah ovládacího prvku úprav.|  
  
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory řízení automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny vzory ovládacích prvků, které musí být podporovány všemi ovládacími prvky datové mřížky. Další informace o vzorcích ovládacího prvku naleznete v [tématu Přehled řídicích vzorů automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vzorek ovládacího prvku|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Ano|Samotný ovládací prvek datové mřížky vždy podporuje vzorek ovládacího prvku Grid, protože položky, které obsahuje metadata, která je rozložena v mřížce.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Závisí|Možnost posouvání datové mřížky závisí na obsahu a na tom, zda jsou k dispozici posuvníky.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Závisí|Možnost výběru datové mřížky závisí na obsahu.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Ano|Ovládací prvek mřížky dat má vždy záhlaví v rámci podstromu, takže musí být podporován vzor ovládacího prvku tabulka.|  
  
 Datové položky v kontejnerech datové mřížky budou podporovat minimálně:  
  
- Vzorek ovládacího prvku položky výběru (pokud je volitelná datová mřížka)  
  
- Vzorek ovládacího prvku Posouvání položky (pokud je datová mřížka posuvná)  
  
- Vzorek ovládacího prvku Položka mřížky  
  
- Položka tabulky – vzor ovládacích prvků  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny události, které musí být podporovány všemi ovládacími prvky datové mřížky. Další informace o událostech naleznete v [tématu Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událost|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Závisí|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změněná vlastnostmi.|Závisí|Pokud ovládací prvek podporuje Scroll vzor, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>událost změněná vlastnostmi.|Závisí|Pokud ovládací prvek podporuje Scroll vzor, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>událost změněná vlastnostmi.|Závisí|Pokud ovládací prvek podporuje Scroll vzor, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>událost změněná vlastnostmi.|Závisí|Pokud ovládací prvek podporuje Scroll vzor, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>událost změněná vlastnostmi.|Závisí|Pokud ovládací prvek podporuje Scroll vzor, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>událost změněná vlastnostmi.|Závisí|Pokud ovládací prvek podporuje Scroll vzor, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Požaduje se|Žádný|  
  
## <a name="date-grid-control-type-example"></a>Příklad typu ovládacího prvku mřížky kalendářních dat  
 Následující obrázek znázorňuje ovládací prvek Zobrazení seznamu, který implementuje typ ovládacího prvku DataGrid.  
  
 ![Obrázek ovládacího prvku Zobrazení seznamu se dvěma datovými položkami](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Zobrazení ovládacího prvku a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zobrazení obsahu stromu, který se nachází v ovládacím prvku Zobrazení seznamu, se zobrazí níže. Vzory ovládacího prvku pro každý prvek automatizace jsou zobrazeny v závorce.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení ovládacího prvku|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (tabulka, mřížka, výběr)</li><li>Hlavička<br /><br /> <ul><li>Hlavičková položka "Název" (Vyvolat)</li><li>Položka záhlaví "Datum změny" (vyvolání)</li><li>Hlavička "Velikost" (Vyvolat)</li></ul></li><li>Skupina "Contoso" (TableItem, GridItem, SelectionItem,\*Table*, Grid )<br /><br /> <ul><li>DataItem "Receivable.doc" (Položka výběru,\*vyvolání,\*položka tableitem , položka gridu )</li><li>DataItem "Accounts Payable.doc" (SelectionItem,\*Invoke,\*TableItem , GridItem )</li></ul></li></ul>|<ul><li>DataGrid (tabulka, mřížka, výběr)</li><li>Skupina "Contoso" (TableItem, GridItem, SelectionItem,\*Table*, Grid )<br /><br /> <ul><li>DataItem "Receivable.doc" (Položka výběru,\*vyvolání,\*položka tableitem , položka gridu )</li><li>DataItem "Accounts Payable.doc" (SelectionItem,\*Invoke,\*TableItem , GridItem )</li></ul></li></ul>|  
  
 \*Předchozí příklad ukazuje DataGrid, který obsahuje více úrovní ovládacích prvků. Ovládací prvek Group ("Contoso") obsahuje dva ovládací prvky DataItem ("Receivable.doc" a "Accounts Payable.doc"). Dvojice DataGrid/GridItem je nezávislá na páru na jiné úrovni. DataItem ovládací prvky v rámci skupiny mohou být také vystaveny jako typ ovládacího prvku ListItem, což umožňuje jejich jasněji jako volitelné objekty, spíše než jako jednoduché datové prvky. Tento příklad nezahrnuje dílčí prvky seskupených datových položek.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.DataGrid>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
