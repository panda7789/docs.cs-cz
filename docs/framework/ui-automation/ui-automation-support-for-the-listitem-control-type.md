---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ListItem
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 95e0e44584a25543577628d1ff8a8b3dae87d34e
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47193681"
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ListItem
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu <xref:System.Windows.Automation.ControlType.ListItem> ovládací prvek typu. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je představují sadu podmínek, které ovládací prvek musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny ke [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzorů ovládacích prvků.  
  
 Ovládací prvky položky seznamu představují ovládací prvky, které implementují typ ovládacího prvku ListItem.  
  
 Následující části definují požadovaný [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzorů ovládacích prvků a události pro typ ovládacího prvku ListItem. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechny ovládací prvky seznamu, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Požadované uživatelské rozhraní automatizace stromová struktura  
 Následující tabulka popisuje ovládací prvek zobrazení a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom, který se vztahuje k položce seznamu ovládací prvky a popisuje, co mohou být obsaženy v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, přečtěte si téma [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Ovládací prvek zobrazení|Zobrazení obsahu|  
|------------------|------------------|  
|ListItem<br /><br /> – Image (0 nebo více)<br />-Text (0 nebo více)<br />-Upravit (0 nebo více)|ListItem|  
  
 Podřízené položky ovládacího prvku seznamu zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu musí být vždy "0". Pokud struktura ovládací prvek je tak, aby ostatní položky jsou obsaženy pod položky seznamu a měla by odpovídat požadavky [podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TreeItem](../../../docs/framework/ui-automation/ui-automation-support-for-the-treeitem-control-type.md) ovládací prvek typu.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice je obzvláště důležité pro ovládací prvky položek seznamu. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, viz [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Tato hodnota této vlastnosti by měly zahrnovat oblasti obsah obrázků a textu položky seznamu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Závisí|Pokud je ovládací prvek seznamu bod pro kliknutí (bodu, který se dá kliknout, aby se seznam přepínat) tohoto bodu musí být vystavené prostřednictvím této vlastnosti. Pokud ovládací prvek seznamu je zcela pokryta potomků seznam položek se vyvolat <xref:System.Windows.Automation.NoClickablePointException> k označení, že klient musí požádat položky uvnitř ovládacího prvku seznam pro bod umožňující kliknutí.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Hodnota vlastnosti název ovládacího prvku seznamu položky pochází z obsah textu položky.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|V části poznámky.|Pokud je statický text popisku této vlastnosti musí vystavit odkaz na tento ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ListItem|Tato hodnota je stejný pro všechny architektury uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"položka"|Lokalizovaný řetězec odpovídající typ ovládacího prvku ListItem|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Ovládací prvek seznamu je vždy součástí obsahu zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Ovládací prvek seznamu je vždy součástí zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Hodnota TRUE|Kontejner můžete přijmout vstup z klávesnice tato hodnota vlastnosti musí být true.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Text nápovědy pro ovládací prvky seznamu by měl vysvětlit, proč je požadováno uživateli umožní výběr ze seznamu možností, které je obvykle stejný typ informací prezentovaná prostřednictvím popisek. Například "vyberte položku, kterou chcete nastavit rozlišení zobrazení monitoru".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Závisí|Tato vlastnost by měly být vystaveny pro ovládací prvky seznamu položek, které představují základní objekt. Tyto ovládací prvky seznamu položky mají obvykle ikonu přidružený k ovládacímu prvku, který uživatelé přidružit k základní objekt.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Závisí|Tato vlastnost musí vrátit hodnotu Určuje, zda položka seznamu je aktuálně přešla do oblasti zobrazení v rámci nadřazeného kontejneru, který implementuje vzoru ovládacích prvků posuv.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit vzory vyžaduje to, že ovládací prvky položek seznamu. Další informace o vzorů ovládacích prvků naleznete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|– Vzor ovládacích prvků|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Ano|Ovládací prvek položky seznamu musí implementovat toto – vzor ovládacích prvků. To umožňuje seznamu ovládacích prvků položek k předání, pokud jsou vybrány.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Závisí|Pokud položka seznamu je obsažena v kontejneru, který je posuvný musí být implementované tento – vzor ovládacích prvků.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Závisí|Pokud je položka seznamu kontrolovatelné a akci neprovede změně stavu výběru, musí být implementované tento – vzor ovládacích prvků.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Závisí|Pokud chcete zobrazit nebo skrýt informace lze ovládat položky musí být implementované tento – vzor ovládacích prvků.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závisí|Pokud položka se dá upravit musí implementovat toto – vzor ovládacích prvků. Změny v ovládacím prvku položky seznamu způsobí, že změny hodnot <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>, a <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>.|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Závisí|Pokud prostorových navigační položka k položce se podporuje v seznamu kontejnerů a kontejner je uspořádán do řádků a sloupců musí být implementované vzoru ovládacích prvků položky mřížky.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Závisí|Pokud položka neobsahuje příkaz, který pro ni být prováděny, nezávisle na výběr, pak tento model musí být implementované. Obvykle se jedná o akci přidruženou poklepáním na ovládací prvek položky seznamu. Příklady by otevírání dokumentu z [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)], nebo přehrávání hudby [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)].|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřebné to, že všechny ovládací prvky položek seznamu. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty> události změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> události změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> události změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty> události změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.ListItem>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
