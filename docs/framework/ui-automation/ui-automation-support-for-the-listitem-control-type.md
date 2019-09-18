---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ListItem
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List Item control type
- UI Automation, List Item control type
ms.assetid: 34f533bf-fc14-4e78-8fee-fb7107345fab
ms.openlocfilehash: 18dcec2be6d9496c14dcc12c1d21b60967732db8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041462"
---
# <a name="ui-automation-support-for-the-listitem-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ListItem
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma poskytuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podpoře <xref:System.Windows.Automation.ControlType.ListItem> pro typ ovládacího prvku. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nástroji je typ ovládacího prvku sada podmínek, které musí ovládací prvek splňovat, aby bylo možné <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost použít. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků.  
  
 Ovládací prvky seznamu položek jsou příkladem ovládacích prvků, které implementují typ ovládacího prvku ListItem.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku ListItem. Požadavky platí pro všechny ovládací prvky seznamu bez ohledu [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]na to, [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]zda, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]nebo. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Požadovaná stromová struktura automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahu stromové struktury, které se vztahují k ovládacím prvkům položky seznamu, a popisuje, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacích prvků|Zobrazení obsahu|  
|------------------|------------------|  
|Collection<br /><br /> -Image (0 nebo více)<br />-Text (0 nebo více)<br />-Edit (0 nebo více)|Collection|  
  
 Podřízené položky ovládacího prvku položky seznamu v rámci zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahu stromu musí být vždy "0". Pokud je struktura ovládacího prvku taková, že další položky jsou obsaženy pod položkou seznamu, pak by měly splňovat požadavky na [podporu automatizace uživatelského rozhraní pro](ui-automation-support-for-the-treeitem-control-type.md) typ ovládacího prvku typu ovládacího prvku TreeItem.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice je obzvláště relevantní pro ovládací prvky položky seznamu. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostech najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Majetek|Value|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečná napříč všemi ovládacími prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Tato hodnota této vlastnosti by měla obsahovat oblast obrázku a textu položky seznamu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Závislosti|Pokud má ovládací prvek seznam možnost výběru (bod, na který se dá kliknout, aby se seznam aktivoval), musí být tento bod vystavený prostřednictvím této vlastnosti. Pokud je ovládací prvek seznam zcela pokryt položkami seznamu následníků, vyvolá <xref:System.Windows.Automation.NoClickablePointException> , aby označoval, že klient musí požádat o položku v ovládacím prvku seznam pro položku, která je k dismístě.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Hodnota vlastnosti název ovládacího prvku položka seznamu pochází z textového obsahu položky.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Pokud je popisek statický text, musí tato vlastnost vystavit odkaz na tento ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Collection|Tato hodnota je stejná pro všechny architektury uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"položka seznamu"|Lokalizovaný řetězec odpovídající typu ovládacího prvku ListItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Pravda|V zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahu stromu je vždy zahrnut ovládací prvek seznam.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Pravda|Ovládací prvek seznam je vždy součástí zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacího prvku stromové struktury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Pravda|Pokud kontejner může přijmout vstup z klávesnice, hodnota této vlastnosti by měla být true.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|""|Text nápovědy pro ovládací prvky seznam by měl vysvětlit, proč se uživateli požaduje, aby si vyžádal volbu ze seznamu možností, což je obvykle stejný typ informací prezentovaný pomocí popisu tlačítka. Například "vyberte položku pro nastavení rozlišení obrazovky pro monitor."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Závislosti|Tato vlastnost by měla být vystavena ovládacím prvkům položky seznamu, které představují základní objekt. Tyto ovládací prvky seznamu položek mají obvykle ikonu přidruženou k ovládacímu prvku, který uživatelé přiřadí k základnímu objektu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Závislosti|Tato vlastnost musí vracet hodnotu, pokud je položka seznamu aktuálně posunuta do zobrazení v nadřazeném kontejneru, který implementuje vzor ovládacího prvku posun.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory ovládacího prvku automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vzory ovládacích prvků, které musí být podporovány ovládacími prvky položky seznamu. Další informace o vzorech ovládacích prvků naleznete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vzor ovládacího prvku|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Ano|Ovládací prvek položky seznamu musí implementovat tento vzor ovládacího prvku. To umožňuje ovládacím prvkům položky seznamu sdělit, kdy jsou vybrány.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Závislosti|Pokud je položka seznamu obsažena v kontejneru, který lze procházet, je nutné tento vzor ovládacího prvku implementovat.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Závislosti|Pokud je položka seznamu rezervovaná a akce neprovede změnu stavu výběru, musí být tento vzor řízení implementován.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Závislosti|Pokud je možné položku manipulovat s zobrazením nebo skrytím informací, musí být tento vzor ovládacího prvku implementován.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závislosti|Pokud je možné položku upravovat, je nutné tento vzor ovládacího prvku implementovat. Změny ovládacího prvku položka seznamu způsobí změny v hodnotách <xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>, a. <xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Závislosti|Pokud je položka pro prostorovou navigaci v kontejneru seznamu podporována a kontejner je uspořádán do řádků a sloupců, je nutné implementovat vzor ovládacího prvku položky mřížky.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Závislosti|Pokud má položka příkaz, který může být proveden, oddělený od výběru, musí být tento vzor implementován. Obvykle se jedná o akci spojenou s dvojitým kliknutím na ovládací prvek položky seznamu. Příklady by vyžadovaly spuštění dokumentu z [!INCLUDE[TLA#tla_winexpl](../../../includes/tlasharptla-winexpl-md.md)]nebo přehrávání hudebního souboru v. [!INCLUDE[TLA#tla_wmp](../../../includes/tlasharptla-wmp-md.md)]|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, které musí být podporovány všemi ovládacími prvky položky seznamu. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událostí|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závislosti|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>událost změny vlastnosti.|Závislosti|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.ControlType.ListItem>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
