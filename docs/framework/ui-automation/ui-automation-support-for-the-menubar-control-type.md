---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuBar
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Menu Bar control type
- control types, Menu Bar
- Menu Bar control type
ms.assetid: c1202b21-c1f0-4560-853c-7b99bd73ad97
ms.openlocfilehash: c50c5abb450ae44fcc08507354ea73f3a780afdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179640"
---
# <a name="ui-automation-support-for-the-menubar-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuBar
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahuje informace <xref:System.Windows.Automation.ControlType.MenuBar> o podpoře pro typ ovládacího prvku. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programu je typ ovládacího prvku sada podmínek, které <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> musí ovládací prvek splňovat, aby bylo možné použít vlastnost. Podmínky zahrnují zvláštní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, hodnoty vlastností a vzory ovládacích prvku.  
  
 Ovládací prvky panelu nabídek jsou příkladem ovládacích prvků, které implementují typ ovládacího prvku MenuBar. Panely nabídek poskytují uživatelům prostředky k aktivaci příkazů a možností obsažených v aplikaci.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzorky ovládacího prvku a události pro typ ovládacího prvku MenuBar. Požadavky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] platí pro všechny ovládací [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]prvky seznamu, ať už , Win32 nebo Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Požadovaná struktura stromu automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a zobrazení obsahu stromu, který se nálsek a ovládací prvky panelu nabídek, a popisuje, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu naleznete v [tématu Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|Menu<br /><br /> - MenuItem (1 nebo více)<br />- Jiné ovládací prvky (0 nebo více)|Menu<br /><br /> - MenuItem (1 nebo více)<br />- Jiné ovládací prvky (0 nebo více)|  
  
 Ovládací prvky panelu nabídek mohou obsahovat další ovládací prvky, jako jsou ovládací prvky pro úpravy a pole se seznamem v rámci své struktury. Tyto další ovládací prvky odpovídají "další ovládací prvky" uvedené výše v ovládacích prvků a zobrazení obsahu.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vlastnosti, jejichž hodnota nebo definice jsou obzvláště důležité pro ovládací prvky panelu nabídek. Další informace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o vlastnostech naleznete v [tématu Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Hodnota vystavená touto vlastností musí obsahovat všechny ovládací prvky obsažené v ní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Ovládací prvek panelu nabídek nepotřebuje název, pokud aplikace nemá více než jeden řádek nabídek. Pokud je více než jeden řádek nabídek v aplikaci, pak tato vlastnost by měla být použita k vystavení rozlišovací názvy, jako je například "Formátování" nebo "Osnova."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Ovládací prvky panelu nabídek nikdy nemají popisek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Menu|Tato hodnota je stejná pro všechny architektury ui.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"panel nabídek"|Lokalizovaný řetězec odpovídající typu ovládacího prvku MenuBar.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Ovládací prvek panelu nabídek je vždy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] součástí zobrazení obsahu stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Ovládací prvek panelu nabídek je vždy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] součástí ovládacího zobrazení stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Viz poznámky.|Hodnota této vlastnosti závisí na tom, zda je ovládací prvek zobrazitelný na obrazovce.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.OrientationProperty>|Závisí|Tato vlastnost zpřístupňuje, zda je ovládací prvek panelu nabídek vodorovný nebo svislý.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Ovládací prvky panelu nabídek lze zaostřit pomocí klávesnice, protože ovládací prvky, které obsahují, mohou zaostřovat pomocí klávesnice.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Viz poznámky.|Žádné scénáře pro, kdy je pro ovládací prvek panelu nabídek vyžadován text nápovědy.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AcceleratorKeyProperty>|`Null`|Panely nabídek nikdy nemají klávesy akcelerátoru.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|"ALT"|Stisknutí klávesy ALT by mělo vždy přinést fokus na řádek nabídek v aplikaci.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory řízení automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vzory ovládacích prvků, které musí být podporovány ovládacími prvky panelu nabídek. Další informace o vzorcích ovládacího prvku naleznete v [tématu Přehled řídicích vzorů automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vzorek ovládacího prvku|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Závisí|Pokud lze ovládací prvek rozbalit <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>nebo sbalit, implementujte .|  
|<xref:System.Windows.Automation.Provider.IDockProvider>|Závisí|Pokud lze ovládací prvek ukotvit do různých <xref:System.Windows.Automation.Provider.IDockProvider>částí obrazovky, implementujte .|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|Závisí|Pokud lze změnit velikost ovládacího prvku, otočit <xref:System.Windows.Automation.Provider.ITransformProvider>nebo přesunout, musí být implementován .|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny události, které musí být podporovány všemi ovládacími prvky panelu nabídek. Další informace o událostech naleznete v [tématu Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událost|Podpora/hodnota|Poznámky|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požaduje se|Žádný|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.MenuBar>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
