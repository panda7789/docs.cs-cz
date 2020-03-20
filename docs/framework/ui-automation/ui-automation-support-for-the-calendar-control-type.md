---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku kalendář
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Calendar control type
- Calendar control type
- control types, Calendar
ms.assetid: e91a7393-a7f9-4838-a1a6-857438b24bc9
ms.openlocfilehash: b9b7e999c20c97acd1da4d6afedbac9177996ebe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179834"
---
# <a name="ui-automation-support-for-the-calendar-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku kalendář
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahuje informace o podpoře pro typ ovládacího prvku Kalendář. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programu je typ ovládacího prvku sada podmínek, které <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> musí ovládací prvek splňovat, aby bylo možné použít vlastnost. Podmínky zahrnují konkrétní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, hodnoty [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastností, vzory ovládacího prvku a události.  
  
 Ovládací prvky kalendáře umožňují uživateli snadno určit datum a vybrat další data.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzorky ovládacího prvku a události pro typ ovládacího prvku Kalendář. Požadavky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] platí pro všechny ovládací [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]prvky kalendáře, ať už , Win32 nebo Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Požadovaná struktura stromu automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a zobrazení obsahu stromu, který se týkající se ovládacích prvků kalendáře, a popisuje, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu naleznete v [tématu Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|Kalendář<br /><br /> <ul><li>DataGrid<br /><br /> <ul><li>Záhlaví (0 nebo 1)</li><li>HeaderItem (0 nebo 7; množství závisí na tom, kolik dní se zobrazí ve sloupcích)</li><li>ListItem (množství závisí na tom, kolik dní se zobrazí)</li><li>Tlačítko (0 nebo 2; pro zobrazení stránkovacího kalendáře)</li></ul></li></ul>|Kalendář<br /><br /> - ListItem (množství závisí na tom, kolik dní se zobrazí)|  
  
 Ovládací prvky kalendáře mohou být reprezentovány v mnoha různých formách v rámci uživatelského rozhraní. Jediné zaručené ovládací prvky, které [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mají být v ovládacím zobrazení stromu, jsou ovládací prvky mřížky dat, záhlaví, položky záhlaví a položky seznamu.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vlastnosti, jejichž hodnota nebo definice jsou zvláště důležité pro ovládací prvky kalendáře. Další informace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o vlastnostech naleznete v [tématu Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečný napříč všechny ovládací prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Nejvzdálenější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Podporováno, pokud je ohraničující obdélník. Pokud není možné kliknout na každý bod v ohraničovacím obdélníku a provedete specializované testování přístupů, přepište a poskytněte bod, na který lze kliknout.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Kalendář|Tato hodnota je stejná pro všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Ovládací prvek kalendáře je vždy součástí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zobrazení obsahu stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Ovládací prvek kalendáře je vždy součástí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacího zobrazení stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Popisek ovládacího prvku dokumentu. Obvykle se používá název dokumentu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"kalendář"|Lokalizovaný řetězec odpovídající typu ovládacího prvku Kalendář.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Ovládací prvek kalendáře obvykle získá jeho název od data aktuálního dne.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory řízení automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vzory ovládacích prvků, které musí být podporovány všemi ovládacími prvky kalendáře. Další informace o vzorcích ovládacího prvku naleznete v [tématu Přehled řídicích vzorů automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vlastnost Vzorek/vzorek ovládacího prvku|Podpora|Poznámky|  
|---------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Ano|Ovládací prvek kalendáře vždy podporuje Grid vzor, protože dny v rámci měsíce jsou položky, které lze navigovat prostorově.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Závisí|Většina ovládacích prvků kalendáře podporuje převrácení zobrazení po stránce. Vzorek posouvání se doporučuje pro podporu stránkování navigace.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Závisí|Většina ovládacích prvků kalendáře zachovat konkrétní den, měsíc nebo rok jako výběr dílčího prvku. Některé kalendáře lze vybrat více a jiné pouze s jedním výběrem.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Ano|Ovládací prvek kalendáře má vždy záhlaví v rámci podstromu pro dny v týdnu, takže vzor tabulka musí být podporovány.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Ne|Vzor ovládacího prvku hodnota není nutné pro ovládací prvky kalendáře, protože nelze nastavit hodnotu přímo na ovládacíprvek. Pokud je k ovládacímu prvku přidruženo určité datum, měly by být informace poskytnuty pomocí vzoru ovládacího prvku Výběr.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny události, které musí být podporovány všemi ovládacími prvky kalendáře. Další informace o událostech naleznete v [tématu Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událost|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změněná vlastnostmi.|Závisí|Pokud ovládací prvek podporuje vzorek ovládacího prvku Scroll, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>událost změněná vlastnostmi.|Závisí|Pokud ovládací prvek podporuje vzorek ovládacího prvku Scroll, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>událost změněná vlastnostmi.|Závisí|Pokud ovládací prvek podporuje vzorek ovládacího prvku Scroll, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>událost změněná vlastnostmi.|Závisí|Pokud ovládací prvek podporuje vzorek ovládacího prvku Scroll, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>událost změněná vlastnostmi.|Závisí|Pokud ovládací prvek podporuje vzorek ovládacího prvku Scroll, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>událost změněná vlastnostmi.|Závisí|Pokud ovládací prvek podporuje vzorek ovládacího prvku Scroll, musí podporovat tuto událost.|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Požaduje se|Žádný|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.Calendar>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
