---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ListItem
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
ms.openlocfilehash: 245f9030897d54a2f1c95d5ce6369b67d23cb319
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179704"
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ListItem
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahuje informace <xref:System.Windows.Automation.ControlType.ListItem> o podpoře pro typ ovládacího prvku. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programu je typ ovládacího prvku sada podmínek, které <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> musí ovládací prvek splňovat, aby bylo možné použít vlastnost. Podmínky zahrnují zvláštní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, hodnoty vlastností a vzory ovládacích prvku.  
  
 Seznam položek ovládací prvky jsou příkladem ovládacích prvků, které implementují ListItem typ ovládacího prvku.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzorky ovládacího prvku a události pro typ ovládacího prvku ListItem. Požadavky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] platí pro všechny ovládací [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]prvky seznamu, ať už , Win32 nebo Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Požadovaná struktura stromu automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a zobrazení obsahu stromu, který se týkající se ovládacích prvků položek seznamu, a popisuje, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu naleznete v [tématu Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|Listitem<br /><br /> - Obrázek (0 nebo více)<br />- Text (0 nebo více)<br />- Upravit (0 nebo více)|Listitem|  
  
 Podřízené položky seznamu v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu musí být vždy "0". Pokud struktura ovládacího prvku je taková, že ostatní položky jsou obsaženy pod položku seznamu pak by měl dodržovat požadavky na [podporu automatizace uživatelského rozhraní pro typ ovládacího prvku TreeItem.](ui-automation-support-for-the-treeitem-control-type.md)  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vlastnosti, jejichž hodnota nebo definice jsou zvláště důležité pro ovládací prvky položky seznamu. Další informace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o vlastnostech naleznete v [tématu Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečný napříč všechny ovládací prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Tato hodnota této vlastnosti by měla zahrnovat oblast obrázku a textový obsah položky seznamu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Závisí|Pokud má ovládací prvek seznamu bod, na který lze kliknout (bod, na který lze klepnout, aby se seznam zaměřil), musí být tento bod vystaven prostřednictvím této vlastnosti. Pokud je ovládací prvek seznamu zcela pokryt položkami seznamu potomků, vyvolá <xref:System.Windows.Automation.NoClickablePointException> a označuje, že klient musí požádat položku uvnitř ovládacího prvku seznamu o bod, na který lze kliknout.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Hodnota vlastnosti názvu ovládacího prvku položky seznamu pochází z textového obsahu položky.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Pokud je statický textový popisek pak tato vlastnost musí vystavit odkaz na tento ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Listitem|Tato hodnota je stejná pro všechny architektury ui.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"položka seznamu"|Lokalizovaný řetězec odpovídající typu ovládacího prvku ListItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Ovládací prvek seznamu je vždy součástí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zobrazení obsahu stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Ovládací prvek seznamu je vždy součástí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacího zobrazení stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Pokud kontejner může přijímat vstup z klávesnice, měla by být tato hodnota vlastnosti pravdivá.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Text nápovědy pro ovládací prvky seznamu by měl vysvětlit, proč je uživatel vyzván k výběru ze seznamu možností, což je obvykle stejný typ informací prezentovaných prostřednictvím popisku. Například "Vyberte položku, která nastaví rozlišení zobrazení monitoru."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Závisí|Tato vlastnost by měla být vystavena pro ovládací prvky položky seznamu, které představují základní objekt. Tyto ovládací prvky položky seznamu mají obvykle ikonu přidruženou k ovládacímu prvku, který uživatelé přidruží k podkladovému objektu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Závisí|Tato vlastnost musí vrátit hodnotu pro zda je položka seznamu aktuálně posunuta do zobrazení v rámci nadřazeného kontejneru, který implementuje vzorek ovládacího prvku Scroll.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory řízení automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vzory ovládacích prvků, které musí být podporovány ovládacími prvky položek seznamu. Další informace o vzorcích ovládacího prvku naleznete v [tématu Přehled řídicích vzorů automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vzorek ovládacího prvku|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Ano|Ovládací prvek položky seznamu musí implementovat tento vzor ovládacího prvku. To umožňuje ovládací prvky seznamu položek sdělit, když jsou vybrány.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Závisí|Pokud je položka seznamu obsažena v kontejneru, který je posuvný, pak tento vzor ovládacího prvku musí být implementována.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Závisí|Pokud je položka seznamu kontrolovatelná a akce neprovede změnu stavu výběru, musí být tento vzor ovládacího prvku implementován.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Závisí|Pokud lze s položkou manipulovat, aby se zobrazily nebo skryly informace, musí být tento vzor ovládacího prvku implementován.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závisí|Pokud lze položku upravit, musí být implementován tento vzor ovládacího prvku. Změny ovládacího prvku položky seznamu způsobí <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>změny <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>hodnot . a .|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Závisí|Pokud je prostorová navigace položky k položce podporována v kontejneru seznamu a kontejner je uspořádán do řádků a sloupců, musí být implementován vzor ovládacího prvku Položka mřížky.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Závisí|Pokud položka má příkaz, který lze provést na něm, odděleně od výběru, pak tento vzor musí být implementována. Obvykle se jedná o akci přidruženou k poklepání na ovládací prvek položky seznamu. Příkladem může být spuštění dokumentu z průzkumníka Microsoft Windows nebo přehrávání hudebního souboru v programu Microsoft Windows Media Player.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny události, které musí být podporovány všemi ovládacími prvky položek seznamu. Další informace o událostech naleznete v [tématu Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událost|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závisí|Žádný|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požaduje se|Žádný|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.ListItem>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
