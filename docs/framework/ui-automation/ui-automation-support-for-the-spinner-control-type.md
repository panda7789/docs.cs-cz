---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku číselník
description: Získejte informace o podpoře automatizace uživatelského rozhraní pro typ ovládacího prvku číselník. Seznamte se s požadovanou stromovou strukturou, vlastnostmi, vzory ovládacích prvků a událostmi.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Spinner control type
- Spinner control type
- control types, Spinner
ms.assetid: 3a29d185-65d8-42e3-bcc3-7f43e96f40c5
ms.openlocfilehash: 7d2955758a8d1da40d7ed18da1103b5d99849d03
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166970"
---
# <a name="ui-automation-support-for-the-spinner-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku číselník
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma poskytuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podpoře pro typ ovládacího prvku číselník. V nástroji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] je typ ovládacího prvku sada podmínek, které musí ovládací prvek splňovat, aby bylo možné vlastnost použít <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků.  
  
 Ovládací prvky číselníku se používají k výběru z domény položek nebo rozsahu čísel.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku číselník. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Požadavky se vztahují na všechny ovládací prvky číselníku, ať už [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] typu Win32, nebo model Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Požadovaná stromová struktura automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, které se vztahují na číselníky, když podporují vzorce rozsahu, hodnoty a výběry a popisují, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
 **Hodnota rozsahu nebo vzor ovládacího prvku hodnoty**  
  
|Zobrazení ovládacích prvků|Zobrazení obsahu|  
|------------------|------------------|  
|Číselník<br /><br /> -Upravit (0 nebo 1)<br />-Tlačítko (2)|Číselník|  
  
 **Vzor ovládacího prvku Výběr**  
  
|Zobrazení ovládacích prvků|Zobrazení obsahu|  
|------------------|------------------|  
|Číselník<br /><br /> -Upravit (0 nebo 1)<br />-Tlačítko (2)<br />– Položka seznamu (0 nebo více)|Číselník<br /><br /> -ListItem (0 nebo více)|  
  
 Chcete-li zajistit, že dvě tlačítka v podstromu zobrazení ovládacích prvků lze odlišit pomocí automatizovaných testovacích nástrojů, přiřaďte `SmallIncrement` nebo `SmallDecrement` `AutomationId` podle potřeby. U některých implementací může být přidružený ovládací prvek pro úpravy rovnocenným ovládacím prvkem číselníku.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice je obzvláště relevantní pro číselníkové ovládací prvky. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostech najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Majetek|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečná napříč všemi ovládacími prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Vnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Upravitelný bod ovládacího prvku číselník má fokus na část úpravy ovládacího prvku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může obdržet fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Číselník obvykle získá svůj název ze statického textového popisku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Ovládací prvky číselníku mají statický textový popisek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Číselník|Tato hodnota je stejná pro všechny architektury uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|zprav|Lokalizovaný řetězec odpovídající typu ovládacího prvku číselník|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Ano|Ovládací prvek číselníku musí být vždy obsah.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Ano|Číselník musí být vždy ovládací prvek.|  
  
<a name="Required_UI_Automation_Control_Patterns_and_Properties"></a>
## <a name="required-ui-automation-control-patterns-and-properties"></a>Požadované vzory a vlastnosti ovládacího prvku automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vzory ovládacích prvků, které jsou požadovány pro podporu číselníků. Další informace o vzorech ovládacích prvků naleznete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Řídicí vzorek/vlastnost vzoru|Podpora/hodnota|Poznámky|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Závislosti|Tento model musí podporovat ovládací prvky číselníku, které mají vybrat seznam položek, které mají být vybrány.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Ne|Číselníkové ovládací prvky jsou vždy kontejnery s jedním výběrem.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Závislosti|Ovládací prvky číselníku, které mají rozsah číselných rozsahů, mohou tento model podporovat.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závislosti|Tento model mohou podporovat ovládací prvky číselníku, které jsou rozloženy diskrétní sadou možností nebo čísel.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, které musí být podporovány všemi ovládacími prvky číselníku. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událostí|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Závislosti|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Povinné|Žádné|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.Spinner>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
