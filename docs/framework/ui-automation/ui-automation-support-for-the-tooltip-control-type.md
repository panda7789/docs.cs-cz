---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ToolTip
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, ToolTip control type
- ToolTip control type
- control types, ToolTip
ms.assetid: c3779d78-3164-43ae-8dae-bfaeafffdd65
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: ac16e99bbc65e2874ffbf1be3c78f12b7fd73df6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-support-for-the-tooltip-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ToolTip
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku popisek. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je sadu podmínek, které ovládacího prvku musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků.  
  
 Ovládací prvky popisek tlačítek jsou automaticky otevíraná okna, které obsahují text.  
  
 Následující části zadejte požadované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku popisek. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechny ovládací prvky popisek tlačítek, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura stromu automatizace požadované uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, která se vztahují na nástroj tip ovládací prvky a popisuje, co může být obsažený v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|Popisy tlačítek<br /><br /> -Text (0 nebo více)<br />-Image (0 nebo více)|Popisy tlačítek|  
  
 Ovládací prvky popisek tlačítek objeví jenom v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, pokud obdrží fokus klávesnice. Jinak, všechny informace tip nástroje má k dispozici `HelpTextProperty` na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element, který odkazuje popis tlačítka na.  
  
 Popisy tlačítek, měl by být pod ovládací prvek, který odkazuje na své informace. Klienti musí naslouchat `ToolTipOpenedEvent` zajistit, že konzistentně získat informace obsažené v popisy.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jehož hodnota nebo definice je obzvláště důležité pro ovládací prvky popisek tlačítek. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v části vlastnosti, [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélníku, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Můžete kliknout bodu musí být součástí tip nástroj, který bude zavření ovládací prvek. Některé popisy není tato možnost a nebudou mít k dispozici prokliknutelný bod.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Název ovládacím prvkem popis tlačítka je text, který se zobrazí v rámci popis tlačítka.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Ovládací prvky popisek tlačítek jsou vždy samoobslužné označeny jejich obsah.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Popisy tlačítek|Tato hodnota je stejný pro všechny rozhraní uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"Popis tlačítka"|Lokalizovaný řetězec odpovídající typ ovládacího prvku popisek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Závisí|Pokud ovládacím prvkem popis tlačítka mohou získat fokus klávesnice, musí být v zobrazení obsahu stromu. Pokud se jedná pouze text, je k dispozici jako HelpTextProperty z ovládacího prvku, která je vyvolána.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Ovládacím prvkem popis tlačítka musí být vždy ovládacího prvku.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní požadované  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řízení vzory potřeba podporovat ovládací prvky popisek tlačítek. Další informace o vzory ovládacích prvků, najdete v části [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Vzor ovládacích prvků|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|Závisí|Typy nástrojů, které je možné uzavřít kliknutím na položku uživatelského rozhraní musí podporovat WindowPattern tak, aby se automaticky uzavřeny.|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|Závisí|Pro lepší usnadnění prvkem popis tlačítka může podporovat vzor ovládacích prvků textu, i když není potřeba. Vzor ovládacích prvků textu je užitečné, když text má bohaté styl a atributy (například barvy, tučné písmo a italics).|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace požadované uživatelského rozhraní  
 Ovládací prvky popisek tlačítek musíte zvýšit `ToolTipOpenedEvent` Jakmile se zobrazí na obrazovce. Události bude obsahovat odkaz na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvek popis tlačítka, sám sebe.  
  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřeba podporovat všechny ovládací prvky popisek tlačítek. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipOpenedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ToolTipClosedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty> událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.ToolTip>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
