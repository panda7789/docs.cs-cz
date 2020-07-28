---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataGrid
description: Získejte informace o podpoře automatizace uživatelského rozhraní pro typ ovládacího prvku DataGrid. Seznamte se s požadovanou stromovou strukturou, vlastnostmi, vzory ovládacích prvků a událostmi.
ms.date: 03/30/2017
helpviewer_keywords:
- Data Grid control type
- control types, Data Grid
- UI Automation, Data Grid control type
ms.assetid: a3db4a3f-feb5-4e5f-9b42-aae7fa816e8a
ms.openlocfilehash: 13f265e414383e646f3e138feb890661fa01e2de
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167996"
---
# <a name="ui-automation-support-for-the-datagrid-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataGrid
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma poskytuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podpoře pro typ ovládacího prvku DataGrid. V nástroji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] je typ ovládacího prvku sada podmínek, které musí ovládací prvek splňovat, aby bylo možné vlastnost použít `ControlType` . Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků.  
  
 Typ ovládacího prvku DataGrid umožňuje uživateli snadno pracovat s položkami, které obsahují metadata reprezentovaná ve sloupcích. Ovládací prvky mřížky dat obsahují řádky položek a sloupců s informacemi o těchto položkách. Ovládací prvek zobrazení seznamu v Průzkumníkovi Microsoft Vista je příkladem, který podporuje typ ovládacího prvku DataGrid.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku DataGrid. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Požadavky platí pro všechny ovládací prvky datové mřížky, ať už [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] , Win32 nebo model Windows Forms.  
  
## <a name="required-ui-automation-tree-structure"></a>Požadovaná stromová struktura automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, které se vztahují k ovládacím prvkům pro datovou mřížku, a popisuje, co může být v každém zobrazení obsaženo. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zobrazení stromového řízení|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|DataGrid<br /><br /> <ul><li>Záhlaví (0, 1 nebo 2)<br /><br /> <ul><li>HeaderItem (počet sloupců nebo řádků)</li></ul></li><li>Datová položka (0 nebo více; může být strukturovaná v hierarchii)</li></ul>|DataGrid<br /><br /> -DataItem (0 nebo více; může být strukturovaný v hierarchii)|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny vlastnosti, jejichž hodnota nebo definice jsou obzvláště důležité pro ovládací prvky datové mřížky. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostech najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|Vlastnost|Hodnota|Poznámky|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečná napříč všemi ovládacími prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Vnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Podporováno, pokud je ohraničen obdélník. Pokud není k dispozici žádný bod v ohraničujícím obdélníku a provádíte specializované testování přístupů, přepíšete a získáte bod, který je k dispozici.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|DataGrid|Tato hodnota je stejná pro všechny architektury uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Ano|Hodnota této vlastnosti musí být vždy true. To znamená, že ovládací prvek data Grid musí být vždy v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Ano|Hodnota této vlastnosti musí být vždy true. To znamená, že ovládací prvek datové mřížky musí být vždy v zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může obdržet fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Pokud je popisek statický text, musí tato vlastnost vystavit odkaz na tento ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"data grid"|Lokalizovaný řetězec odpovídající typu ovládacího prvku DataGrid|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Ovládací prvek datové mřížky obvykle získává hodnotu `Name` vlastnosti z popisku statického textu. Pokud není k dispozici žádný statický textový popisek, musí vývojář aplikace přiřadit hodnotu pro `Name` vlastnost. Hodnota `Name` vlastnosti nikdy nesmí být textový obsah ovládacího prvku pro úpravy.|  
  
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory ovládacího prvku automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny vzory ovládacích prvků, které musí být podporovány všemi ovládacími prvky datové mřížky. Další informace o vzorech ovládacích prvků naleznete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vzor ovládacího prvku|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Ano|Ovládací prvek datová mřížka sám o sobě vždycky podporuje vzor ovládacích prvků mřížky, protože obsahuje položky, které obsahuje metadata, která jsou obsažena v mřížce.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Závislosti|Možnost posouvání datové mřížky závisí na obsahu a na tom, zda jsou posuvníky k dispozici.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Závislosti|Možnost výběru datové mřížky závisí na obsahu.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Ano|Ovládací prvek tabulka dat vždy obsahuje hlavičku v rámci jeho podstromu, takže musí být podporován vzor ovládacího prvku tabulka.|  
  
 Datové položky v kontejnerech datové mřížky budou podporovat minimálně:  
  
- Vzor ovládacího prvku položky výběru (Pokud je vybraná datová mřížka)  
  
- Posunutí vzoru ovládacího prvku položky (Pokud je datová mřížka posunutá)  
  
- Vzor ovládacího prvku položka mřížky  
  
- Položka tabulky – vzor ovládacích prvků  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, které musí být podporovány všemi ovládacími prvky pro datovou mřížku. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událostí|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Závislosti|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Povinné|Žádné|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změny vlastnosti.|Závislosti|Pokud ovládací prvek podporuje vzor posuvníku, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>událost změny vlastnosti.|Závislosti|Pokud ovládací prvek podporuje vzor posuvníku, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>událost změny vlastnosti.|Závislosti|Pokud ovládací prvek podporuje vzor posuvníku, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>událost změny vlastnosti.|Závislosti|Pokud ovládací prvek podporuje vzor posuvníku, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>událost změny vlastnosti.|Závislosti|Pokud ovládací prvek podporuje vzor posuvníku, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>událost změny vlastnosti.|Závislosti|Pokud ovládací prvek podporuje vzor posuvníku, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Povinné|Žádné|  
  
## <a name="date-grid-control-type-example"></a>Příklad typu ovládacího prvku mřížky dat  
 Následující obrázek znázorňuje ovládací prvek zobrazení seznamu, který implementuje typ ovládacího prvku DataGrid.  
  
 ![Obrázek ovládacího prvku zobrazení seznamu se dvěma datovými položkami](./media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, které se vztahují k ovládacímu prvku zobrazení seznamu, se zobrazuje níže. Vzory ovládacích prvků pro každý element automatizace jsou uvedeny v závorkách.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zobrazení stromového řízení|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>DataGrid (tabulka, mřížka, výběr)</li><li>Hlavička<br /><br /> <ul><li>HeaderItem "Name" (Invoke)</li><li>HeaderItem "datum změny" (vyvolání)</li><li>HeaderItem "velikost" (vyvolání)</li></ul></li><li>Skupina "contoso" (TableItem, GridItem, ovládacích SelectionItem, tabulka *, mřížka \* )<br /><br /> <ul><li>DataItem "Accounts Receivable.doc" (ovládacích SelectionItem, Invoke, TableItem \* , GridItem \* )</li><li>DataItem "Accounts Payable.doc" (ovládacích SelectionItem, Invoke, TableItem \* , GridItem \* )</li></ul></li></ul>|<ul><li>DataGrid (tabulka, mřížka, výběr)</li><li>Skupina "contoso" (TableItem, GridItem, ovládacích SelectionItem, tabulka *, mřížka \* )<br /><br /> <ul><li>DataItem "Accounts Receivable.doc" (ovládacích SelectionItem, Invoke, TableItem \* , GridItem \* )</li><li>DataItem "Accounts Payable.doc" (ovládacích SelectionItem, Invoke, TableItem \* , GridItem \* )</li></ul></li></ul>|  
  
 \*Předchozí příklad ukazuje prvek DataGrid, který obsahuje více úrovní ovládacích prvků. Ovládací prvek Group ("contoso") obsahuje dva ovládací prvky DataItem (účty Receivable.doc a Accounts Payable.doc). Pár DataGrid/GridItem je nezávislý na páru na jiné úrovni. Ovládací prvky DataItem v rámci skupiny lze také zveřejnit jako typ ovládacího prvku ListItem, což umožňuje jejich prezentování přehlednější jako objekty s možností výběru, nikoli jako jednoduché datové prvky. Tento příklad nezahrnuje dílčí prvky seskupených datových položek.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.DataGrid>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
