---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku posuvník
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Slider
- UI Automation, Slider control type
- Slider control type
ms.assetid: 045ea62f-7b50-46cf-a5a9-8eb97704355f
ms.openlocfilehash: e59b46b3e159ae95ae15835e9b000e7db71c4ad9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179612"
---
# <a name="ui-automation-support-for-the-slider-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku posuvník
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahuje informace o podpoře pro typ ovládacího prvku Slider. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programu je typ ovládacího prvku sada podmínek, které <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> musí ovládací prvek splňovat, aby bylo možné použít vlastnost. Podmínky zahrnují zvláštní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, hodnoty vlastností a typy ovládacích prvku.  
  
 Ovládací prvek Slider je složený ovládací prvek s tlačítky, které umožňují uživateli s myší nastavit číselný rozsah nebo vybrat ze sady položek.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzorky ovládacího prvku a události pro typ ovládacího prvku Slider. Požadavky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] platí pro všechny ovládací [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]prvky posuvníku, ať už , Win32 nebo Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Požadovaná struktura stromu automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacích prvků [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a zobrazení obsahu stromu, který se přilne k ovládacím prvkům jezdce, a popisuje, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu naleznete v [tématu Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|Posuvník<br /><br /> - Tlačítko (2 nebo 4)<br />- Palec (pouze 1)<br />- Položka seznamu (0 nebo více)|Posuvník<br /><br /> - Položka seznamu (0 nebo více)|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vlastnosti, jejichž hodnota nebo definice jsou obzvláště důležité pro typ ovládacího prvku Slider. Další informace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o vlastnostech naleznete v [tématu Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečný napříč všechny ovládací prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Nejvzdálenější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Zobrazit poznámky|Většina ovládacích prvků posuvníku musí zvýšit, <xref:System.Windows.Automation.NoClickablePointException> protože celý ohraničovací obdélník ovládacího prvku jezdce je obsazen podřízenými ovládacími prvky.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Název ovládacího prvku pro úpravy je obvykle generován ze statického textového popisku. Pokud není statický textový popisek, musí `Name` být hodnota vlastnosti pro přiřazena vývojářem aplikace. Vlastnost `Name` by nikdy neměla obsahovat textový obsah ovládacího prvku úprav.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Pokud je k ovládacímu prvku přidružen statický textový popisek, musí tato vlastnost vystavit odkaz na tento ovládací prvek. Pokud je textový ovládací prvek dílčí součástí jiného `LabeledBy` ovládacího prvku, nebude mít nastavenou vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Posuvník|Tato hodnota je stejná pro všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"jezdec"|Lokalizovaný řetězec odpovídající typu upravit ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Ovládací prvek úprav je vždy součástí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zobrazení obsahu stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Ovládací prvek úprav je vždy součástí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacího prvku stromu.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory řízení automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vzorky ovládacích prvků, které musí být podporovány všemi ovládacími prvky posuvníku. Další informace o vzorcích ovládacího prvku naleznete v [tématu Přehled řídicích vzorů automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vzorek ovládacího prvku|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Závisí|Jezdec by měl podporovat vzorek ovládacího prvku Výběr, pokud obsah představuje jednu hodnotu mezi samostatnou sadou možností. Pokud je podporován vzorek ovládacího prvku Výběr, musí být odpovídající výběr vystaven jako jedna nebo více podřízených položek seznamu jezdce.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Závisí|Posuvník by měl podporovat vzor ovládacího prvku RangeValue, pokud lze obsah nastavit na hodnotu v číselném rozsahu.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závisí|Posuvník by měl podporovat vzorek ovládacího prvku Hodnota, pokud obsah představuje jednu hodnotu mezi samostatnou sadou možností.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny události, které musí být podporovány všemi ovládacími prvky posuvníku.  
  
 Další informace o událostech naleznete v [tématu Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událost|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Závisí|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změněná vlastnostmi|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změněná vlastnostmi|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změněná vlastnostmi|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty>událost změněná vlastnostmi|Závisí|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požaduje se|Žádný|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.Slider>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
