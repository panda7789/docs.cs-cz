---
title: "Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku posuvník"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, Slider
- UI Automation, Slider control type
- Slider control type
ms.assetid: 045ea62f-7b50-46cf-a5a9-8eb97704355f
caps.latest.revision: "18"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: d5edee3499c5d3e50c0ed359a5afdfbe1d37b376
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-the-slider-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku posuvník
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku posuvník. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je sadu podmínek, které ovládacího prvku musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a typy ovládacích prvků.  
  
 V ovládacím prvku posuvník je složeného ovládacího prvku pomocí tlačítka, které uživatelům myší nastavit číselný rozsah nebo vybrat ze sady položek.  
  
 Následující části zadejte požadované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastností, vzory ovládacích prvků a události pro typ ovládacího prvku posuvník. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechny ovládací prvky posuvníku, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura stromu automatizace požadované uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, která se vztahují na posuvníku ovládací prvky a popisuje, co může být obsažený v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|Posuvník<br /><br /> -Tlačítko (2 nebo 4)<br />-Jezdec (pouze 1)<br />-Položka list (0 nebo více)|Posuvník<br /><br /> -Položka list (0 nebo více)|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jehož hodnota nebo definice je obzvláště důležité pro posuvník řízení typu. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v části vlastnosti, [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélníku, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky|Většina ovládací prvky posuvníku musíte zvýšit <xref:System.Windows.Automation.NoClickablePointException> protože celý ohraničující obdélník ovládacího prvku posuvník je obsazena podřízených ovládacích prvků.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Název ovládacích prvků pro úpravy se obvykle generují z statický text popisku. Pokud není statický text popisku, hodnota vlastnosti `Name` musí být přiřadila vývojáře aplikace. `Name` Vlastnost by měla obsahovat nikdy textový obsah ovládacích prvků pro úpravy.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|V části poznámky.|Pokud je statický text popisku, přidružený k ovládacímu prvku, tato vlastnost musí vystavit odkaz u daného ovládacího prvku. Pokud ovládací prvek text je dílčí nevyberou, nebudou mít `LabeledBy` sadu vlastností.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Posuvník|Tato hodnota je stejný pro všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"posuvník"|Lokalizovaný řetězec odpovídající typ ovládacího prvku upravit.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Textové pole je vždy součástí obsahu zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Textové pole je vždy součástí zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní požadované  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řízení vzory potřeba podporovat všechny ovládací prvky posuvníku. Další informace o vzory ovládacích prvků, najdete v části [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Vzor ovládacích prvků|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Závisí|Pokud obsah představuje jednu hodnotu mezi diskrétní sadu možností, by měly podporovat jezdce vzoru ovládacích prvků výběr. Při vzoru ovládacích prvků výběr je podporováno, musí se zveřejnit odpovídající výběr jako jeden nebo více podřízených položek seznamu posuvníku.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Závisí|Jezdce by měly podporovat vzor RangeValue ovládacích prvků, pokud obsah můžete nastavit na hodnotu numerické rozsahu.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závisí|Jezdce by měly podporovat vzoru ovládacích prvků hodnota, pokud obsah představuje jednu hodnotu mezi diskrétní sada možností.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřeba podporovat všechny ovládací prvky posuvníku.  
  
 Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti|Požadováno|Žádné|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>událost změny vlastnosti|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.Slider>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
