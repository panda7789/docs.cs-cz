---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku podokno
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Pane control type
- Pane control type
- control types, Pane
ms.assetid: 79761191-4449-4630-899c-9cbdb8867d3f
ms.openlocfilehash: ab888c2ecfd516ae4e7ce5dab0dca3fde1a7b98e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179663"
---
# <a name="ui-automation-support-for-the-pane-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku podokno
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahuje informace o podpoře typu ovládacího prvku Podokno. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programu je typ ovládacího prvku sada podmínek, které <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> musí ovládací prvek splňovat, aby bylo možné použít vlastnost. Podmínky zahrnují zvláštní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, hodnoty vlastností a vzory ovládacích prvku.  
  
 Typ ovládacího prvku Podokno se používá k reprezentaci objektu v okně rámce nebo dokumentu. Uživatelé mohou přecházet mezi ovládacími prvky podokna a v rámci obsahu aktuálního podokna, ale nemohou přecházet mezi položkami v různých podoknech. Ovládací prvky podokna tedy představují úroveň seskupení nižší než okna nebo dokumenty, ale nad jednotlivé ovládací prvky. Uživatel přejde mezi podokny stisknutím kláves TAB, F6 nebo CTRL+TAB, v závislosti na kontextu. Typ ovládacího prvku Podokno nevyžaduje žádnou konkrétní navigaci pomocí klávesnice.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzorky ovládacího prvku a události pro typ ovládacího prvku podokna. Požadavky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] platí pro všechny ovládací [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]prvky seznamu, ať už , Win32 nebo Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Požadovaná struktura stromu automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a zobrazení obsahu stromu, který se týkající se ovládacích prvků podokna, a popisuje, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu naleznete v [tématu Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|Podokno|Podokno|  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vlastnosti, jejichž hodnota nebo definice jsou obzvláště důležité pro ovládací prvky podokna. Další informace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o vlastnostech naleznete v [tématu Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečný napříč všechny ovládací prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Nejvzdálenější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Hodnota pro tuto vlastnost musí být vždy jasný, výstižný a smysluplný název.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Tato vlastnost zpřístupňuje bod, na který lze kliknout v ovládacím prvku podokna, který způsobí, že se podokno při klepnutí zaměří.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Ovládací prvky podokna obvykle nemají statický popisek. Pokud je statický textový popisek, by měl být vystaven prostřednictvím této vlastnosti.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Podokno|Tato hodnota je stejná pro všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"podokno"|Lokalizovaný řetězec odpovídající typu ovládacího prvku Podokno.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Ovládací prvky podokna jsou vždy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zahrnuty v zobrazení obsahu stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Ovládací prvky podokna jsou vždy [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zahrnuty v ovládacím zobrazení stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Text nápovědy pro ovládací prvky podokna by měl vysvětlit, proč je účel rámečku a jak souvisí s jinými rámečky. Popis je nezbytný, pokud účel a vztah rámců není `NameProperty`jasný z hodnoty . "|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AccessKeyProperty>|Viz poznámky.|Pokud konkrétní kombinace kláves poskytuje fokus podokna pak tyto informace by měly být vystaveny prostřednictvím této vlastnosti.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory řízení automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vzory ovládacích prvků, které musí být podporovány všemi ovládacími prvky podokna. Další informace o vzorcích ovládacího prvku naleznete v [tématu Přehled řídicích vzorů automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vzorek ovládacího prvku|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITransformProvider>|Závisí|Tento vzor ovládacího prvku implementujte, pokud lze ovládací prvek podokna přesunout, změnit jejich velikost nebo otočit na obrazovce.|  
|<xref:System.Windows.Automation.Provider.IWindowProvider>|Never (Nikdy)|Pokud potřebujete implementovat tento vzor ovládacího prvku, <xref:System.Windows.Automation.ControlType.Window> ovládací prvek by měl být založen na typu ovládacího prvku.|  
|<xref:System.Windows.Automation.Provider.IDockProvider>|Závisí|Implementujte tento vzor ovládacího prvku, pokud lze ovládací prvek podokna ukotvit.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Závisí|Implementujte tento vzor ovládacího prvku, pokud lze posouvat ovládací prvek podokna.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny události, které musí být podporovány všemi ovládacími prvky podokna. Další informace o událostech naleznete v [tématu Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událost|Podpora/hodnota|Poznámky|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowClosedEvent>|Never (Nikdy)|Žádný|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowOpenedEvent>|Never (Nikdy)|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AsyncContentLoadedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.WindowPatternIdentifiers.WindowVisualStateProperty>událost změněná vlastnostmi.|Never (Nikdy)|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požaduje se|Žádný|  
  
<a name="Pane_Control_Type_Example"></a>
## <a name="pane-control-type-example"></a>Příklad typu ovládacího prvku podokna  
 Následující obrázek znázorňuje ovládací prvek, který implementuje typ ovládacího prvku podokno.  
  
 ![Snímek obrazovky okna apletu se dvěma podokny](./media/uiauto-pane.GIF "uiauto_pane")  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení ovládacího prvku|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>Podokno</li><li>Strom (vzorek posouvání)<br /><br /> <ul><li>Treeitem</li><li>Podokno</li><li>Upravit (vzorek posouvání</li></ul></li></ul>|- Podokno<br />- Strom (rolovací vzor)<br />- Stromová položka<br />- ... Podokně<br />- Upravit<br />- (Rolovací vzor)|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.Pane>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
