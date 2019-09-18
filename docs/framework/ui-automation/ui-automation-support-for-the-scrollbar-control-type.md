---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ScrollBar
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Scroll Bar control type
- control types, Scroll Bar
- Scroll Bar control type
ms.assetid: 329891d7-b609-49e6-920a-09ea8a627d07
ms.openlocfilehash: f983bd080d20a82d814445bfd90d145039d96b77
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041198"
---
# <a name="ui-automation-support-for-the-scrollbar-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ScrollBar
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma poskytuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podpoře pro typ ovládacího prvku ScrollBar. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nástroji je typ ovládacího prvku sada podmínek, které musí ovládací prvek splňovat, aby bylo možné <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost použít. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků.  
  
 Ovládací prvky posuvníku umožňují uživateli posouvání obsahu v rámci kontejneru okna nebo položky. Ovládací prvek se skládá ze sady tlačítek a ovládacího prvku posuvník.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku ScrollBar. Požadavky platí pro všechny ovládací prvky seznamu bez ohledu [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]na to, [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]zda, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]nebo. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Požadovaná stromová struktura automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahu stromové struktury, které se vztahují k ovládacím prvkům posuvníku, a popisuje, co může být v každém zobrazení obsaženo. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacích prvků|Zobrazení obsahu|  
|------------------|------------------|  
|ScrollBar<br /><br /> -Tlačítko (2 nebo 4)<br />-Palec (0 i:<0)|Není k dispozici. Ovládací prvek posuvníku neobsahuje obsah.|  
  
 Ovládací prvek posuvníku má vždy tři až pět podřízených objektů. Vzhledem k tomu, že podstrom obsahuje více než jeden ovládací prvek tlačítko, je <xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty> nutné nastavit konkrétní hodnotu pro každou položku, aby byla zjistitelná pro nástroje testů pro automatizaci.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice jsou obzvláště důležité pro ovládací prvky posuvníku. Všimněte si, že ovládací prvek posuvníku nemá obsah, který není k disřádku; jeho funkce je zpřístupněna prostřednictvím řídicího vzoru posuvníku, který je podporován na posouvaným kontejneru.  
  
 Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostech najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Majetek|Value|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečná napříč všemi ovládacími prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Vnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může obdržet fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|`Null`|Ovládací prvek posuvníku nemá prvky obsahu a `NameProperty` není nutné jej nastavit.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Nejedná se o číslo.|Ovládací prvek posuvníku neobsahuje body, které se na něj odkazují.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Posuvníky nemají popisky.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ScrollBar|Tato hodnota je stejná pro všechny architektury. Posuvníky, které fungují jako posuvníky, musí používat typ ovládacího prvku posuvník.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"posuvník"|Lokalizovaný řetězec, který odpovídá typu ovládacího prvku tlačítko.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Ovládací prvek posuvníku není nikdy prvkem obsahu. Pokud je posuvník samostatný ovládací prvek, je nutné, aby splňoval typ ovládacího prvku posuvník a vrátil `ControlType.Slider` `ControlType` vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Pravda|Posuvník musí být vždy ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|Pravda|Ovládací prvek posuvníku musí vždy vystavit jeho vodorovnou nebo svislou orientaci.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory ovládacího prvku automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vzory ovládacích prvků, které musí být podporovány ovládacími prvky posuvníku. Další informace o vzorech ovládacích prvků naleznete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md). Všimněte si, že když se posuvník používá jako ovládací prvek pouze pro manipulaci s myší, nepodporuje vzory ovládacích prvků. Pokud se používá jako ovládací prvek posuvníku v rámci aplikace, musí být daný typ ovládacího prvku posuvník.  
  
|Vzor ovládacího prvku|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Nikdy|Vzor ovládacího prvku posouvání není nikdy přímo podporován na posuvníku.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Závislosti|Tato funkce se vyžaduje, aby se podporovala pouze v případě, že není podporován vzor ovládacího prvku Scroll v kontejneru, který má posuvník.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, které musí být podporovány všemi ovládacími prvky posuvníku. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událostí|Podpora/hodnota|Poznámky|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>událost změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>událost změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>událost změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>událost změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>událost změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.ControlType.ScrollBar>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
