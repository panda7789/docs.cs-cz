---
title: "Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ToolBar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, Toolbar
- UI Automation, Toolbar control type
- ToolBar control type
ms.assetid: 85152efd-f4c5-430c-8878-3371cc598616
caps.latest.revision: "21"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 36f0d8ffef94a4c90303b9e38fdd27a25fc0a2bb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-the-toolbar-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ToolBar
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku panel nástrojů. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je sadu podmínek, které ovládacího prvku musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků. Ovládací prvky panelu nástrojů povolit koncovým uživatelům aktivovat příkazy a nástroje, které jsou obsaženy v rámci aplikace.  
  
 Následující části zadejte požadované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku panel nástrojů. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechny ovládací prvky panelu nástrojů, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura stromu automatizace požadované uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, která se vztahují na panelu nástrojů ovládací prvky a popisuje, co může být obsažený v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|ToolBar<br /><br /> -Různé ovládací prvky (0 nebo více)|ToolBar<br /><br /> -Různé ovládací prvky (0 nebo více)|  
  
 Ovládací prvek panelu nástrojů může obsahovat libovolný ovládací prvek v rámci jeho podstrom. Se nejčastěji používá obsahovat tlačítka, pole se seznamem a rozdělení tlačítka.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jehož hodnota nebo definice je obzvláště důležité pro ovládací prvky panelu nástrojů. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v části vlastnosti, [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélníku, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Podporováno, pokud je ohraničující obdélník. Není-li každého bodu v rámci ohraničující obdélník je můžete kliknout a provést specializované přístupů testování, přepsání a nabízí bod můžete kliknout.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Závisí|Ovládací prvek panelu nástrojů nemusí název, není-li více než jeden slouží v aplikaci. Pokud se nachází více než jeden, každý musí mít jedinečný název (například formátování nebo osnova).|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Ovládací prvky panelu nástrojů nikdy mít štítek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ToolBar|Tato hodnota je stejný pro všechny rozhraní uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"panelu nástrojů"|Lokalizovaný řetězec odpovídající typ ovládacího prvku panel nástrojů.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Ovládací prvek panelu nástrojů je vždy obsahu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Ovládací prvek panelu nástrojů musí být vždy ovládacího prvku.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní požadované  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řízení vzory potřeba podporovat ovládací prvky panelu nástrojů. Další informace o vzory ovládacích prvků, najdete v části [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Vzor ovládacích prvků|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.ExpandCollapsePattern>|Závisí|Pokud panelu nástrojů můžete rozšířit a sbalit, a zobrazit více položek, pak se tento vzor podporovat.|  
|<xref:System.Windows.Automation.DockPattern>|Závisí|Pokud panelu nástrojů můžete ukotvit různé části obrazovky, pak se tento vzor podporovat.|  
|<xref:System.Windows.Automation.TransformPattern>|Závisí|Pokud panelu nástrojů můžete po změně velikosti, otáčet nebo přesunout, musí tento vzor podporovat.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřeba podporovat všechny ovládací prvky panelu nástrojů. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.ToolBar>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
