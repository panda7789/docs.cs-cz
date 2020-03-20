---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku obrázek
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Image control type
- control types, Image
- Image control type
ms.assetid: 4e0eeefb-e09b-46d2-b83b-0a7e35543ab8
ms.openlocfilehash: b77174a573b027f44be6104cda3d9846d12924e0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179729"
---
# <a name="ui-automation-support-for-the-image-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku obrázek
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahuje informace o podpoře pro typ ovládacího prvku Obrázek. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programu je typ ovládacího prvku sada podmínek, které <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> musí ovládací prvek splňovat, aby bylo možné použít vlastnost. Podmínky zahrnují zvláštní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, hodnoty vlastností a vzory ovládacích prvku.  
  
 Ovládací prvky obrázků používané jako ikony, informační grafiky a grafy budou podporovat typ ovládacího prvku Obrázek. Ovládací prvky použité jako obrázky pozadí nebo vodoznaku nepodporují typ ovládacího prvku Obrázek.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzorky ovládacího prvku a události pro typ ovládacího prvku Obrázek. Požadavky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] platí pro všechny ovládací [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]prvky bitové kopie , ať už win32 nebo windows forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Požadovaná struktura stromu automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a zobrazení obsahu stromu, který se týkající se ovládacích prvků obrazu, a popisuje, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu naleznete v [tématu Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|Image|Obrázek (Závisí na tom, zda obrázek obsahuje informace (na základě hodnoty `IsContentElement` vlastnosti))|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vlastnosti, jejichž hodnota nebo definice jsou obzvláště důležité pro typ ovládacího prvku Obrázek. Další informace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o vlastnostech naleznete v [tématu Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečný napříč všechny ovládací prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Nejvzdálenější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Bod, na který lze kliknout, musí být bodem v ohraničovacím obdélníku ovládacího prvku obrázek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Vlastnost Name musí být vystavena pro všechny ovládací prvky obrazu, které obsahují informace. Programový přístup k těmto informacím vyžaduje, aby byl poskytnut textový ekvivalent grafiky. Pokud je ovládací prvek obrazu čistě dekorativní, musí se zobrazit [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pouze v ovládacím zobrazení stromu a nemusí mít název. Rozhraní ui musí podporovat alt nebo alternativní text vlastnost na obrázky, které lze nastavit z jejich rámci. Tato vlastnost pak bude [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mapovat name vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Pokud je statický textový popisek pak tato vlastnost musí vystavit odkaz na tento ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Image|Tato hodnota je stejná pro všechny architektury ui.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"obrázek"|Lokalizovaný řetězec odpovídající typu ovládacího prvku Obrázek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Viz poznámky.|Ovládací prvek image musí být zahrnuty [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do zobrazení obsahu stromu, pokud obsahuje smysluplné informace, které nejsou dosud vystaveny koncovému uživateli.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Ovládací prvek image je vždy součástí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacího zobrazení stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Viz poznámky.|Vlastnost HelpText zpřístupňuje lokalizovaný řetězec, který popisuje skutečný vizuální vzhled ovládacího prvku (například červený čtverec s bílým "X") nebo jiné informace popisku spojené s obrazem.<br /><br /> Tato vlastnost musí být podporována, pokud je potřeba dlouhý popis sdělit další informace o ovládacím prvku image. Například složitý graf nebo diagram. Tato vlastnost se mapuje na značku LONGDesc HTML a značku SVG (Scalable Vector Graphics) Desc. Vývojáři pracující s ovládacími prvky bitové kopie musí podporovat vlastnost, aby bylo možné nastavit vizuální popis ovládacího prvku. Tato vlastnost musí být mapována na vlastnost VisualDescription automatizace uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|Viz poznámky.|Pokud ovládací prvek obrázku představuje informace o stavu o určité položce na obrazovce, ovládací prvek by měl být obsažen v položce. Pokud je obrázek obsažen v položce, musí položka podporovat vlastnost status a vyvolávat příslušná oznámení při změně stavu.<br /><br /> Pokud je bitová kopie samostatný ovládací prvek a je přenos stavu tato vlastnost musí být podporovány.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory řízení automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vzorky ovládacích prvků, které musí být podporovány všemi ovládacími prvky obrazu. Další informace o vzorcích ovládacího prvku naleznete v [tématu Přehled řídicích vzorů automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vzorek ovládacího prvku|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Závisí|Ovládací prvek image podporuje vzorek Položky mřížky, pokud je ovládací prvek v kontejneru mřížky.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Závisí|Ovládací prvek image podporuje vzor Položky tabulky, pokud je ovládací prvek v kontejneru, který má ovládací prvky záhlaví.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Never (Nikdy)|Pokud ovládací prvek image obsahuje obrázek, na který lze kliknout, ovládací prvek by měl podporovat typ ovládacího prvku, který podporuje vzorek Invoke, například typ ovládacího prvku Button.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Never (Nikdy)|Ovládací prvky obrazu by neměly podporovat vzorek položky výběru.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny události, které musí být podporovány všemi ovládacími prvky bitové kopie. Další informace o událostech naleznete v [tématu Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událost|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Never (Nikdy)|Žádný|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Never (Nikdy)|Žádný|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Never (Nikdy)|Žádný|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Never (Nikdy)|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požaduje se|Žádný|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.Image>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
