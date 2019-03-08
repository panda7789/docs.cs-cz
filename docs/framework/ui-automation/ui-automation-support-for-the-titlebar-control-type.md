---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TitleBar
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Title Bar
- Title Bar control type
- UI Automation, Title Bar control type
ms.assetid: 3b7a4e13-0305-45d5-bc33-1f4133c50782
ms.openlocfilehash: 4e3b980aaa64dcfd53f533808be3ae5887cbfb61
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676847"
---
# <a name="ui-automation-support-for-the-titlebar-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TitleBar
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku TitleBar. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je představují sadu podmínek, které ovládací prvek musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny ke [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzorů ovládacích prvků.  
  
 Ovládací prvky stavového řádku název představují názvy nebo pruhy popisek v okně.  
  
 Následující části definují požadovaný [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzorů ovládacích prvků a události pro typ ovládacího prvku TitleBar. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechny ovládací prvky stavového řádku title, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Požadované uživatelské rozhraní automatizace stromová struktura  
 Následující tabulka popisuje ovládací prvek zobrazení a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, které se vztahují na záhlaví okna Ovládací prvky a popisuje, co mohou být obsaženy v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, přečtěte si téma [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Ovládací prvek zobrazení|Zobrazení obsahu|  
|------------------|------------------|  
|Záhlaví<br /><br /> -Nabídky (0 nebo 1)<br />-Tlačítko (0 nebo více)|Nelze použít. (ovládací prvek panel názvu nemá žádný obsah).|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice je obzvláště důležité pro ovládací prvky záhlaví. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, viz [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Ohraničující obdélník záhlaví musí zahrnovat všechny ovládací prvky, které jsou v něm obsaženy.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Nepodporuje. Pokud ohraničující obdélník. Pokud ne každý bod v rámci ohraničující obdélník je po kliknutí a provést specializované přístupů testování přepsat a zadat bod umožňující kliknutí.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|False|Záhlaví nikdy mít fokus klávesnice.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|""|Není záhlaví obsahu; jeho textové informace je vystaven na nadřazené okno.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|V části poznámky.|Ovládací prvek panel název obvykle nemá popisek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Záhlaví|Tato hodnota je stejný pro všechny architektury uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"záhlaví"|Lokalizovaný řetězec odpovídající typ ovládacího prvku TitleBar|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|False|Ovládací prvek panel název není nikdy obsahu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Pravda|Ovládací prvek panel název musí být vždy ovládacího prvku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Závisí|Tento ovládací prvek vrátí hodnotu v závislosti na tom, zda je viditelný na obrazovce záhlaví okna.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Není nutné vystavit text nápovědy.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|""|Záhlaví mít nikdy žádná přístupové klávesy.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|""|Ovládací prvek panel názvu nemá přístupový klíč.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní vyžaduje  
 Typ ovládacího prvku TitleBar není vyžadovaný jako podpora vzorů ovládacích prvků pro všechny. Jeho funkce jsou dostupné prostřednictvím vzoru ovládacích prvků okno na ovládací prvek okna.  
  
## <a name="required-ui-automation-events"></a>Události automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vyžaduje to, že všechny ovládací prvky stavového řádku název události. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> události změny vlastnosti.|Požadováno|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> události změny vlastnosti.|Požadováno|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> události změny vlastnosti.|Nikdy|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Nikdy|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádná|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Automation.ControlType.TitleBar>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
