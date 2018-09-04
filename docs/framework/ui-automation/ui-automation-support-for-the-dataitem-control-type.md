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
ms.openlocfilehash: e3008b710a6fcaba476fd8c425beaa8eb11f9e52
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43527550"
---
# <a name="ui-automation-support-for-the-dataitem-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku DataItem
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku DataItem. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] typ ovládacího prvku je představují sadu podmínek, které ovládací prvek musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny ke [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzorů ovládacích prvků.  
  
 Položky v seznamu kontaktů je příkladem ovládacího prvku položek. Ovládací prvek položky dat obsahuje informace, které jsou zajímavé pro koncového uživatele. To je složitější než jednoduchý seznam položek, protože obsahuje podrobnější informace.  
  
 Následující části definují požadovaný [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzorů ovládacích prvků a události pro typ ovládacího prvku DataItem. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechna data ovládací prvky položek, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Požadované uživatelské rozhraní automatizace stromová struktura  
 Následující tabulka popisuje ovládací prvek zobrazení a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom, který se týká datovou položku Ovládací prvky a popisuje, co mohou být obsaženy v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, přečtěte si téma [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom – ovládací prvek zobrazení|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|Datové položky<br /><br /> -Se liší (0 nebo více; může být strukturovaná v hierarchii)|Datové položky<br /><br /> -Se liší (0 nebo více; může být strukturovaná v hierarchii)|  
  
 Datový prvek položky v datové mřížce můžete hostovat různé objekty, včetně další vrstvu datové položky, nebo konkrétní mřížky prvky, jako jsou text, obrázky, nebo ovládacích prvcích pro úpravy. Pokud má element dat položky roli konkrétního objektu, element by měly být vystaveny jako určitý ovládací prvek typu; například ListItem typu ovládacího prvku pro volitelné datové položky v mřížce.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace uživatelského rozhraní vyžaduje  
 V následující tabulce jsou uvedeny vlastnosti, jejichž hodnota nebo definice je obzvláště důležité pro ovládací prvky dat položky. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, viz [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Vlastnost|Hodnota|Poznámky|  
|--------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Nepodporuje. Pokud ohraničující obdélník. Pokud ne každý bod v rámci ohraničující obdélník je po kliknutí a provést specializované přístupů testování přepsat a zadat bod umožňující kliknutí.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Datové položky|Tato hodnota je stejný pro všechny architektury uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Ovládací prvek položky dat musí být vždy obsahu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Ovládací prvek položky dat musí být vždy ovládacího prvku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může získat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|V části poznámky.|Pokud ovládací prvek obsahuje stav, který je aktualizován dynamicky musí tato vlastnost podporována, tak, aby technologie pro usnadnění můžete dostávat aktualizace, když se změní stav elementu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|V části poznámky.|To je řetězcovou hodnotu, která přenáší koncovému uživateli základní objekt, který představuje položku. Příklady jsou "Mediálního souboru" nebo "Obraťte se na".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Ovládací prvky položek dat nemají popisek statický text.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"datová položka"|Lokalizovaný řetězec odpovídající typ ovládacího prvku DataItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Ovládací prvek položky dat vždy obsahuje element primární text, který má vztah k co uživatel přidružit jako největší sémantické identifikátor pro položku.|  
  
<a name="_Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] řídit vzory vyžaduje to, že všechny ovládací prvky dat položky. Další informace o vzorů ovládacích prvků naleznete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|– Vzor ovládacích prvků|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Závisí|Pokud datová položka můžete rozbalit nebo sbalit zobrazení a skrytí informace, musí se podporovat vzor Rozbalit sbalit.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Závisí|Datové položky bude podporovat vzor položky mřížky, pokud je kolekce položek dat k dispozici v rámci kontejneru, který může být prostorově přejde položku k položce.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Závisí|Všechny datové položky podporují možnost být přesunut do oblasti zobrazení se vzorem posouvání položek při jejich datový kontejner obsahuje více položek, než se vejde na obrazovce.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Ano|Všechny datové položky musí podporovat vzor výběru položky k označení při výběru položky.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Závisí|Pokud datová položka je obsažena v datové mřížce typ ovládacího prvku se bude podporovat tento model.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Závisí|Pokud datová položka obsahuje stavu, ve kterém můžete cyklicky.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závisí|Pokud primární text položky dat je možné upravovat, musí se podporovat vzor hodnota.|  
  
<a name="Working_with_Data_Items_in_Large_Lists"></a>   
## <a name="working-with-data-items-in-large-lists"></a>Práce s datovými položkami v rozsáhlých seznamů  
 Dlouhé seznamy jsou často virtualizované v rámci dat [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] platformy, které pomáhají při výkonu. Z toho důvodu nelze použít klientů automatizace uživatelského rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] funkce dotazu k scrape obsah stromu úplné stejným způsobem, který lze uložit do jiných kontejnerů prvku. Klient by měl přejděte na položku do zobrazení (nebo rozbalit ovládací prvek zobrazíte všechny možnosti cenné) před přístupem kompletní informace z datové položky.  
  
 Při volání metody `SetFocus` na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] – element pro položky dat [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)] vrátí úspěšně a způsobit, že se na nastavení pro úpravy v rámci podstrom položky dat případ.  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vyžaduje to, že všechny položky ovládacích prvcích dat události. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> události změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> události změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> události změny vlastnosti.|Závisí|Žádné|  
  
<a name="Data_Item_Control_Type_Example"></a>   
## <a name="dataitem-control-type-example"></a>Příklad typu ovládacího prvku DataItem  
 Následující obrázek ukazuje typ ovládacího prvku DataItem v ovládacím prvku zobrazení seznamu s podporou pro široké škály informací pro sloupce.  
  
 ![Grafického ovládacího prvku zobrazení seznamu s dvěma datovými položkami](../../../docs/framework/ui-automation/media/uiauto-data-grid-detailed.GIF "uiauto_data_grid_detailed")  
  
 Ovládací prvek zobrazení a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, které se vztahují na ovládací prvek položky dat se zobrazí níže. Vzory ovládacích prvků pro každý prvek automation jsou uvedeny v závorkách. Skupina "Contoso" je také součástí gridu hostitelský ovládací prvek mřížky dat.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom – ovládací prvek zobrazení|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|-Skupiny "Contoso" (tabulky, mřížky)<br />-DataItem Receivable.doc "účty" (TableItem, Položka GridItem, prvků SelectionItem, vyvolat)<br />-Image "Účty Receivable.doc"<br />-Upravte "Name" (TableItem prvků GridItem, hodnota "Receivable.doc účtů")<br />-Upravit "Datum změny" (TableItem prvků GridItem, hodnota "8/25/2006 3:29 PM")<br />-Upravte "Velikost" (Položka GridItem TableItem, hodnota "11.0 KB)<br />-DataItem Payable.doc "účty" (TableItem, Položka GridItem, prvků SelectionItem, vyvolat)<br />-   ...|-Skupiny "Contoso" (tabulky, mřížky)<br />-DataItem Receivable.doc "účty" (TableItem, Položka GridItem, prvků SelectionItem, vyvolat)<br />-Image "Účty Receivable.doc"<br />-Upravte "Name" (TableItem prvků GridItem, hodnota "Receivable.doc účtů")<br />-Upravit "Datum změny" (TableItem prvků GridItem, hodnota "8/25/2006 3:29 PM")<br />-Upravte "Velikost" (Položka GridItem TableItem, hodnota "11.0 KB)<br />-DataItem Payable.doc "účty" (TableItem, Položka GridItem, prvků SelectionItem, vyvolat)<br />-   …|  
  
 Pokud mřížky představuje seznam volitelných položek, může být typem ovládacího prvku ListItem místo typu ovládacího prvku DataItem vystavena odpovídající prvky uživatelského rozhraní. V předchozím příkladu prvky datové položky ("Účty Receivable.doc" a "Payable.doc účtů") ve skupině ("Contoso") lze vylepšit vystavení jako typy ovládacích prvků ListItem, protože tento typ už podporuje vzoru ovládacích prvků SelectionItem.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.DataItem>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
