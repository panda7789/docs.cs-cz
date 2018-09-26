---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku HeaderItem
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Header Item control type
- Header Item control type
- control types, Header Item
ms.assetid: 09ce1310-ee31-493c-a71e-010bafc42fcf
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: cfbf554bb3b8cdd05338879af5be1abcc0a17de1
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47172677"
---
# <a name="ui-automation-support-for-the-headeritem-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku HeaderItem
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku HeaderItem. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je představují sadu podmínek, které ovládací prvek musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny ke [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzorů ovládacích prvků.  
  
 Typ ovládacího prvku HeaderItem poskytuje vizuální popisek pro řádek nebo sloupec informací.  
  
 Ovládací prvky záhlaví položek jsou příklady ovládacích prvků, které implementují typ ovládacího prvku HeaderItem. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky v následující části platí pro všechny ovládací prvky záhlaví, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Požadované uživatelské rozhraní automatizace stromová struktura  
 Následující tabulka popisuje ovládací prvek zobrazení a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom, který se týká položky záhlaví ovládací prvky a popisuje, co mohou být obsaženy v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, přečtěte si téma [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Ovládací prvek zobrazení|Zobrazení obsahu|  
|------------------|------------------|  
|HeaderItem|Žádné|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacích prvků položek na vlastnosti, jejichž hodnota nebo definice je obzvláště důležité pro záhlaví. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, viz [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Nepodporuje. Pokud ohraničující obdélník. Pokud ne každý bod v rámci ohraničující obdélník je po kliknutí a provést specializované přístupů testování přepsat a zadat bod umožňující kliknutí.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může získat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Vždy je držitelem popisky položek ovládacího prvku záhlaví.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`.|Ovládací prvky záhlaví položek nemají statický popisek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|HeaderItem|Tato hodnota je stejný pro všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"položky záhlaví"|Lokalizovaný řetězec pro typ ovládacího prvku HeaderItem|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Položky ovládacího prvku záhlaví není součástí zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Položky ovládacího prvku záhlaví je vždy součástí zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|V části poznámky.|Tato vlastnost obsahuje informace o pořadí řazení podle položky záhlaví.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit vzory vyžaduje to, že všechny položky ovládacích prvků záhlaví. Další informace o vzorů ovládacích prvků naleznete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|– Vzor ovládacích prvků|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|Závisí|Tento ovládací prvek model implementujte, pokud můžete změnit velikost položky ovládacího prvku záhlaví.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Závisí|Implementujte tento – vzor ovládacích prvků, pokud ovládací prvek položky hlavičky dá kliknout, aby data seřadit.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřebné to, že všechny položky ovládacích prvků záhlaví. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.HeaderItem>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
