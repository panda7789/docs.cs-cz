---
title: "Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ComboBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, Combo Box
- UI Automation, Combo Box control type
- ComboBox controls
ms.assetid: bb321126-4770-41da-983a-67b7b89d45dd
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4b27f0feda959ccfe868ed741122fe2bb7e162f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ui-automation-support-for-the-combobox-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ComboBox
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku pole se seznamem. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je sadu podmínek, které ovládacího prvku musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností, vzory ovládacích prvků a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události.  
  
 Pole se seznamem je pole se seznamem v kombinaci s statické ovládací prvek nebo textové pole, které se zobrazí aktuálně vybrané položky v seznamu části pole se seznamem. Seznam části ovládacího prvku se zobrazí po celou dobu nebo pouze se zobrazí, když uživatel vybere (což je tlačítko) šipku rozevíracího seznamu vedle ovládacího prvku. Pokud je datové pole výběru ovládacího prvku úprav, může uživatel vložit informace, které se nenachází v seznamu; jinak hodnota uživatel může vybrat pouze položky v seznamu.  
  
 Následující části zadejte požadované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku pole se seznamem. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechny ovládací prvky pole se seznamem, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura stromu automatizace požadované uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, která se vztahují na pole se seznamem ovládací prvky a popisuje, co může být obsažený v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|ComboBox<br /><br /> -Upravit (0 nebo 1)<br />-List (1)<br />-Seznam položek (podřízená položka seznamu; 0 k mnoha)<br />-Tlačítko (1)|ComboBox<br /><br /> -List Item (0 k mnoha)|  
  
 Ovládací prvek upravit v zobrazení ovládacího prvku pole se seznamem je nutné pouze v případě, že pole se seznamem lze upravit žádný vstup, stejně jako v případě pole se seznamem v dialogového okna spustit.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacích prvků pole vlastnosti, jehož hodnota nebo definice je obzvláště důležité pro pole se seznamem. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v části vlastnosti, [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélníku, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Podporováno, pokud je ohraničující obdélník. Není-li každého bodu v rámci ohraničující obdélník je můžete kliknout a provést specializované přístupů testování, přepsání a nabízí bod můžete kliknout.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ComboBox|Tato hodnota je stejný pro všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|V části poznámky.|Text nápovědy pro ovládací prvky pole se seznamem musí vysvětlit, proč je požadováno uživatele vyberte volbu z pole se seznamem. Text je podobná informace uvedené prostřednictvím popisek. Například "vyberte položku, kterou chcete nastavit zobrazení rozlišení monitoru".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Pole se seznamem jsou vždy zahrnuty v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Pole se seznamem jsou vždy zahrnuty v zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Hodnota TRUE|Pole se seznamem vystavit sadu položek z kontejneru výběr. Ovládacího prvku pole se seznamem může přijímat fokus klávesnice, přestože při automatizace uživatelského rozhraní klienta nastaví fokus na pole se seznamem, všechny položky v podstrom pole se seznamem může být vybrán.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|V části poznámky.|Pole se seznamem obvykle mají statický text popisku, který odkazuje na tato vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"– pole se seznamem"|Lokalizovaný řetězec odpovídající typ ovládacího prvku pole se seznamem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Její název ovládacího prvku pole se seznamem obvykle získá z ovládacího prvku statický text.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní požadované  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řízení vzory potřeba podporovat všechny ovládací prvky pole se seznamem. Další informace o vzory ovládacích prvků, najdete v části [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Vzor ovládacích prvků|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Ano|Ovládacího prvku pole se seznamem vždycky musí obsahovat rozevírací tlačítko aby byla pole se seznamem.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Ano|Zobrazí aktuální výběr v seznamu. Tato podpora se deleguje na pole se seznamem pod polem se seznamem.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závisí|Pokud pole se seznamem má schopnost pořizovat libovolný textové hodnoty, musí být hodnota vzor podporována. Tento vzor poskytuje možnost nastavit prostřednictvím kódu programu řetězec obsah pole se seznamem. Pokud vzor hodnota není podporován, znamená to, že uživatel musí proveďte výběr z položky seznamu v rámci podstrom pole se seznamem.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Nikdy|Vzor posuňte se na poli se seznamem nikdy podporuje přímo. Pokud může pole se seznamem obsažené v rámci pole se seznamem posunete je podporována. Může je podporována pouze v případě pole se seznamem je viditelný na obrazovce.|  
  
<a name="Required_Events"></a>   
## <a name="required-events"></a>Požadované události  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřeba podporovat všechny ovládací prvky pole se seznamem. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>událost změny vlastnosti.|Závisí|Pokud ovládací prvek podporuje vzoru hodnota, musí podporovat této události.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.ComboBox>  
 [Přehled typů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
