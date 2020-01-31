---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku kalendář
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Calendar control type
- Calendar control type
- control types, Calendar
ms.assetid: e91a7393-a7f9-4838-a1a6-857438b24bc9
ms.openlocfilehash: 81f08fdfbf48eb3b9b8b9ce6c865bc923772b871
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789580"
---
# <a name="ui-automation-support-for-the-calendar-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku kalendář
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma poskytuje informace o podpoře [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pro typ ovládacího prvku Kalendář. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]je typ ovládacího prvku sada podmínek, které musí ovládací prvek splňovat, aby bylo možné použít vlastnost <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností, vzory ovládacích prvků a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události.  
  
 Ovládací prvky kalendáře umožňují uživateli snadno určit datum a vybrat jiná data.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku Kalendář. Požadavky na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] platí pro všechny ovládací prvky kalendáře, ať už [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 nebo model Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Požadovaná stromová struktura automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], které se vztahují k ovládacím prvkům kalendáře, a popisuje, co může být v každém zobrazení obsaženo. Další informace o stromové struktuře [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacích prvků|Zobrazení obsahu|  
|------------------|------------------|  
|Kalendář<br /><br /> <ul><li>DataGrid<br /><br /> <ul><li>Záhlaví (0 nebo 1)</li><li>HeaderItem (0 nebo 7; množství závisí na počtu dní zobrazených ve sloupcích)</li><li>ListItem (množství závisí na počtu zobrazených dní)</li><li>Tlačítko (0 nebo 2; pro zobrazení stránkovacího kalendáře)</li></ul></li></ul>|Kalendář<br /><br /> -ListItem (množství závisí na počtu zobrazených dní)|  
  
 Ovládací prvky kalendáře lze znázornit v mnoha různých formulářích v rámci uživatelského rozhraní. Jedinými zaručenými ovládacími prvky, které jsou v zobrazení ovládacích prvků stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], jsou ovládací prvky datové mřížky, záhlaví, záhlaví a položky seznamu.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny vlastnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], jejichž hodnota nebo definice jsou obzvláště relevantní pro ovládací prvky kalendáře. Další informace o vlastnostech [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] – vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečná napříč všemi ovládacími prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Vnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Podporováno, pokud je ohraničen obdélník. Pokud není k dispozici žádný bod v ohraničujícím obdélníku a provádíte specializované testování přístupů, přepíšete a získáte bod, který je k dispozici.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Kalendář|Tato hodnota je stejná pro všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Pravda|Ovládací prvek Kalendář je vždy součástí zobrazení obsahu stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Pravda|Ovládací prvek Kalendář je vždy součástí zobrazení ovládacího prvku stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může obdržet fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Popisek ovládacího prvku dokumentu Obvykle se používá název dokumentu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|Kalendář|Lokalizovaný řetězec odpovídající typu ovládacího prvku Calendar.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Ovládací prvek kalendáře obvykle získá své jméno z aktuálního dne.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory ovládacího prvku automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny vzory ovládacích prvků [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], které musí být podporovány všemi ovládacími prvky kalendáře. Další informace o vzorech ovládacích prvků naleznete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Řídicí vzorek/vlastnost vzoru|Podpora|Poznámky|  
|---------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Ano|Ovládací prvek kalendáře vždycky podporuje model mřížky, protože dny v měsíci jsou položky, které se dají procházet prostorově.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Závislosti|Většina ovládacích prvků Calendar podporuje překlopení zobrazení na stránce. Pro podporu navigace stránkování je doporučený vzor posuvníku.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Závislosti|Většina ovládacích prvků kalendáře uchovává určitý den, měsíc nebo rok jako výběr dílčího prvku. Některé kalendáře jsou vícenásobně vybratelné a jiné jenom v jednom výběru.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Ano|Ovládací prvek Calendar má vždy hlavičku v rámci svého podstromu pro dny v týdnu, takže je nutné použít vzor tabulky.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Ne|Vzor ovládacího prvku hodnoty není pro ovládací prvky kalendáře nutný, protože hodnotu nelze nastavit přímo na ovládacím prvku. Pokud je k ovládacímu prvku přidruženo určité datum, informace by měly být poskytnuty vzorem ovládacího prvku výběru.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, které musí být podporovány všemi ovládacími prvky kalendáře. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|Událost [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> událost změněné vlastností.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> událost změněné vlastností.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> událost změněné vlastností.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> událost změněné vlastností.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> událost změněné vlastností.|Závislosti|Pokud ovládací prvek podporuje vzor ovládacího prvku posuvník, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> událost změněné vlastností.|Závislosti|Pokud ovládací prvek podporuje vzor ovládacího prvku posuvník, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> událost změněné vlastností.|Závislosti|Pokud ovládací prvek podporuje vzor ovládacího prvku posuvník, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> událost změněné vlastností.|Závislosti|Pokud ovládací prvek podporuje vzor ovládacího prvku posuvník, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> událost změněné vlastností.|Závislosti|Pokud ovládací prvek podporuje vzor ovládacího prvku posuvník, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> událost změněné vlastností.|Závislosti|Pokud ovládací prvek podporuje vzor ovládacího prvku posuvník, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Požadováno|Žádné|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.ControlType.Calendar>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
