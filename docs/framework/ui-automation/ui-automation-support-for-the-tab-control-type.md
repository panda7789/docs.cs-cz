---
title: "Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku karta"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TabControl type
- UI Automation, Tab control type
- control types, Tab
ms.assetid: f8be2732-836d-4e4d-85e2-73aa39479bf4
caps.latest.revision: "20"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: bf1164b1f3496359a2013253fb275b08acdffc71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-the-tab-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku karta
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku karta. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je sadu podmínek, které ovládacího prvku musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. vzory ovládacích prvků.  
  
 Ovládacího prvku karta je obdobou rozdělení v poznámkovém bloku nebo popisky v souboru CAB. Pomocí ovládacího prvku Karta aplikace můžete definovat více stránek pro stejné oblasti okno nebo dialogové okno.  
  
 Následující části zadejte požadované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastností, vzory ovládacích prvků a události pro typ ovládacího prvku karta. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechny ovládací prvky karet, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura stromu automatizace požadované uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, která se vztahují na ovládací prvky karet a popisuje, co může být obsažený v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|Tabulátor<br /><br /> <ul><li>TabItem (1 nebo více)</li><li>ScrollBar (0 nebo 1)<br /><br /> <ul><li>Tlačítko (0 nebo 2)</li></ul></li></ul>|Tabulátor<br /><br /> -TabItem (1 nebo více)|  
  
 Ovládací prvky karet mít podřízené [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvky založené na typ ovládacího prvku Karta položky. Pokud budou seskupeny položky karta (například jako aplikace Microsoft Office 2007) můžete typ ovládacího prvku karta hostovat skupiny typy ovládacích prvků pro seskupené kartě položky, jak ukazuje následující stromové struktury.  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|Tabulátor<br /><br /> <ul><li>TabItem (1 nebo více)</li><li>Skupina (0 nebo více)<br /><br /> <ul><li>TabItem (0 nebo více)</li></ul></li><li>ScrollBar (0 nebo více)<br /><br /> <ul><li>Tlačítko (0 nebo 2)</li></ul></li></ul>|Tabulátor<br /><br /> <ul><li>TabItem (1 nebo více)</li><li>Skupina (0 nebo více)<br /><br /> <ul><li>TabItem (0 nebo více)</li></ul></li></ul>|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jehož hodnota nebo definice je obzvláště důležité, na kartu řízení typu. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v části vlastnosti, [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélníku, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Ovládacího prvku karta zřídka vyžaduje vlastnost názvu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Ne|Ovládacího prvku karta nemá bod můžete kliknout.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|V části poznámky.|Ovládací prvky karet obvykle mají statický text popisku, který je zveřejněný prostřednictvím této vlastnosti.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Tabulátor|Tato hodnota je stejný pro všechny rozhraní uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"kartu"|Lokalizovaný řetězec odpovídající typ ovládacího prvku karta.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Hodnota TRUE|Typ ovládacího prvku karta musí být schopný přijímat fokus klávesnice. Obvykle [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klienta volání funkce SetFocus na ovládacím prvkem karta a jeden z jeho položky předá fokus klávesnice do ovládacího prvku karta. Je možné pro některé kartě kontejnery přepínat bez nastavení fokusu na jednu z jeho položky.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Ovládacího prvku karta je vždy součástí obsahu zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Ovládacího prvku karta je vždy součástí zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|V části poznámky.|Ovládacího prvku karta musí vždy označuje, zda je umístěný vodorovně nebo svisle.|  
  
<a name="Required_UI_Automation_Control_Patterns_and_Properties"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Požadované vlastnosti a vzory ovládacích prvků automatizace uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řízení vzory potřeba podporovat všechny ovládací prvky karet. Další informace o vzory ovládacích prvků, najdete v části [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Vlastnost vzor nebo vzor ovládacího prvku|Podpora – hodnota|Poznámky|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Ano|Všechny ovládací prvky karet musí podporovat vzoru výběr.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Hodnota TRUE|Ovládací prvky karet vždy vyžadovat, aby byly provedeny výběr.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|False|Ovládací prvky karet jsou vždy jedním výběrem kontejnery.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Závisí|Posouvání, které musí být v ovládacího prvku karta podporovaný vzor má pomůcky, které umožňují pro sadu položek karta posouvat prostřednictvím.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřeba podporovat všechny ovládací prvky karet. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.Tab>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
