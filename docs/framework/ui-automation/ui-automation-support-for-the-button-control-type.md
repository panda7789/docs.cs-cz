---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku tlačítko
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Button
- UI Automation, Button control type
- Button control type
ms.assetid: 057c983a-da83-4c50-86c7-26fe381076a6
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: c80a5df50e0d6161bf2ab251668991ff1b293283
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47082731"
---
# <a name="ui-automation-support-for-the-button-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku tlačítko
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podpora pro typ ovládacího prvku tlačítko. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je představují sadu podmínek, které ovládací prvek musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny ke [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností, vzorů ovládacích prvků a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události.  
  
 Objekt, který uživatel komunikuje s můžete provádět akce, jako je tlačítko **OK** a **zrušit** tlačítka v dialogovém okně. Ovládací prvek tlačítka je jednoduché ovládací prvek k vystavení, protože je namapován na jediný příkaz, který uživatel chce dokončení.  
  
 Následující části definují požadovaný [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzorů ovládacích prvků a události pro typ ovládacího prvku tlačítko. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechny ovládací prvky tlačítek, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Požadované uživatelské rozhraní automatizace stromová struktura  
 Následující tabulka popisuje ovládací prvek zobrazení a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, které se vztahují na ovládací prvky tlačítka a popisuje, co mohou být obsaženy v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, přečtěte si téma [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Ovládací prvek zobrazení|Zobrazení obsahu|  
|------------------|------------------|  
|Tlačítko<br /><br /> – Image (0 nebo více)<br />-Text (0 nebo více)|Tlačítko|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice je obzvláště důležité pro ovládací prvky, které implementují tlačítko ovládací prvek typu (například ovládací prvky tlačítka). Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, viz [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|V části poznámky.|Ovládací prvek tlačítko obvykle musí podporovat klíče akcelerátoru k povolit koncovým uživatelům provádět akce, kterou představuje rychle z klávesnice.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Nepodporuje. Pokud ohraničující obdélník. Pokud ne každý bod v rámci ohraničující obdélník je po kliknutí a provést specializované přístupů testování přepsat a zadat bod umožňující kliknutí.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Tlačítko|Tato hodnota je stejný pro všechny architektury uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|V části poznámky.|Text nápovědy můžete určit, co se bude aktivace tlačítka konečný výsledek. Toto je obvykle stejný typ informací prezentovaná prostřednictvím popisek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Ovládací prvek tlačítko musí být vždy obsahu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Ovládací prvek tlačítko musí být vždy ovládacího prvku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může získat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Ovládací prvky tlačítka jsou označeny svým jejich obsah.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"button"|Lokalizovaný řetězec odpovídající typ ovládacího prvku tlačítko.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Název ovládacího prvku tlačítko je text, který se používá k ho. Pokaždé, když se obrázek slouží k popisu tlačítka, je nutné zadat alternativní text pro vlastnost název tlačítka.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit vzory vyžaduje to, že všechny ovládací prvky tlačítek. Další informace o vzorů ovládacích prvků naleznete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|– Vzor ovládacích prvků|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|V části poznámky.|Vzor ovládacích prvků Invoke nebo vzoru ovládacích prvků přepínání by měly podporovat všechna tlačítka. Vyvolání je podporováno, pokud tlačítko provede příkaz na žádost uživatele. Tento příkaz se mapuje na jedné operace, jako je vyjmutí, kopírování, vložení nebo odstranění.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|V části poznámky.|Vzor ovládacích prvků Invoke nebo vzoru ovládacích prvků přepínání by měly podporovat všechna tlačítka. Přepínací tlačítko je podporována, je-li na tlačítko můžete cyklicky řadu až tři stavy. To je obvykle viděné jako konkrétní funkce přepínač zapnuto/vypnuto.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|V části poznámky.|Pokud tlačítko je hostovaný jako podřízený objekt tlačítko rozdělení, může podporovat tlačítko podřízené prvků ExpandCollapse vzor místo Invoke nebo přepínací tlačítko vzor. Vzor prvků ExpandCollapse lze použít pro otevírání nebo zavírání nabídky nebo jiných dílčí struktura přidružený k prvku tlačítko.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřebné to, že všechny ovládací prvky tlačítek. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závisí|Pokud ovládací prvek podporuje Invoke vzoru ovládacích prvků, musí podporovat této události.|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> události změny vlastnosti.|Závisí|Pokud ovládací prvek podporuje vzoru ovládacích prvků přepínání, musí podporovat této události.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.Button>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
