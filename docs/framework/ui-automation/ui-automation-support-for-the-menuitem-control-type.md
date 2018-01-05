---
title: "Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuItem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, Menu Item
- Menu Item control type
- UI Automation, Menu Item control type
ms.assetid: 54bce311-3d23-40b9-ba90-1bdbdaf8fbba
caps.latest.revision: "23"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: fe4e46294f10d3b48dcf4162d64047ae2930d777
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-the-menuitem-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku MenuItem
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku MenuItem. Popisuje ovládacího prvku [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] stromové struktury a poskytuje vlastnosti a vzory ovládacích prvků, které jsou požadovány pro typ ovládacího prvku MenuItem.  
  
 Ovládacího prvku nabídka umožňuje hierarchická organizace elementy související s příkazy a obslužné rutiny událostí. V typické [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] aplikace, panel nabídek obsahuje několik položek nabídky (například **soubor**, **upravit**, a **okno**), a každou položku nabídky se zobrazí nabídka. Nabídky obsahuje kolekci položek nabídky (například **nový**, **otevřete**, a **Zavřít**), který lze rozšířit na zobrazení další položky nabídky nebo provádět určité akce při kliknutí na. Položky nabídky může být hostovaný v nabídce, nabídek nebo na panelu nástrojů.  
  
 Následující části zadejte požadované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku MenuItem. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechny ovládací prvky seznamu, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura stromu automatizace požadované uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, která se vztahují na položku nabídky ovládací prvky a popisuje, co může být obsažený v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|MenuItem "Nápověda"<br /><br /> <ul><li>Nabídky (dílčí nabídky položky nabídky Nápověda)<br /><br /> <ul><li>MenuItem "Témata nápovědy"</li><li>MenuItem "O Poznámkový blok"</li></ul></li></ul>|MenuItem "Nápověda"<br /><br /> -MenuItem "témata nápovědy"<br />-MenuItem "O Poznámkový blok"|  
  
 Obsahuje zobrazení ovládacího prvku ovládacího prvku položek nabídky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury uvedené výše. Všimněte si, že **pomoci** položky nabídky je inlcluded abychom vám lépe předvedli strukturu v typické nabídce dílčí hierarchie.  
  
 Pro zobrazení obsahu nabídky chybí z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, protože je špatně přenáší důležité informace pro koncového uživatele.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jehož hodnota nebo definice je obzvláště důležité pro nabídky položky ovládacích prvků. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v části vlastnosti, [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|Vlastnost|Hodnota|Popis|  
|--------------|-----------|-----------------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélníku, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Podporováno, pokud je ohraničující obdélník. Není-li každého bodu v rámci ohraničující obdélník je můžete kliknout a provést specializované přístupů testování, přepsání a nabízí bod můžete kliknout.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Ovládací prvek položky nabídky je součástí obsahu zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu a je sám sebou označené s názvem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Žádný štítek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Položka nabídky|Tato hodnota je stejný pro všechny rozhraní uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"položku nabídky"|Lokalizovaný řetězec odpovídající typ ovládacího prvku MenuItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Zobrazení obsahu z nikdy součástí ovládacího prvku položku nabídky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Ovládací prvek položky nabídky musí být vždy součástí zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní požadované  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řízení vzory muset být podporována ovládacích prvků položky nabídky. Další informace o vzory ovládacích prvků, najdete v části [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Vlastnost vzor ovládacího prvku|Podpora|Poznámky|  
|------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Závisí|Pokud ovládací prvek můžete rozbalit nebo sbalit, implementujte <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Závisí|Pokud se ovládací prvek provede jednu akci nebo příkazu, implementovat <xref:System.Windows.Automation.Provider.IInvokeProvider>.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Závisí|Pokud ovládací prvek představuje možnost, která můžete zapnout nebo vypnout, implementujte <xref:System.Windows.Automation.Provider.IToggleProvider>.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Závisí|Pokud ovládací prvek slouží k výběru ze seznamu možností mezi položky nabídky, implementujte <xref:System.Windows.Automation.Provider.ISelectionItemProvider>.|  
  
<a name="UI_Automation_Events_for_Menu_Item"></a>   
## <a name="ui-automation-events-for-menu-item"></a>Události automatizace uživatelského rozhraní pro položku nabídky  
 Následující tabulka uvádí [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] události související s ovládacím prvkem položku nabídky.  
  
|Událost|Podpora|Vysvětlení|  
|-----------|-------------|-----------------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závisí|Musí být vyvolány, pokud řízení podporuje Invoke – vzor ovládacích prvků.|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>událost změny vlastnosti.|Závisí|Musí být vyvolány, pokud řízení podporuje přepínání – vzor ovládacích prvků.|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>událost změny vlastnosti.|Závisí|Musí být vyvolána, pokud řízení podporuje Rozbalit sbalit – vzor ovládacích prvků.|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Závisí|Žádné|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřeba podporovat všechny ovládací prvky položku nabídky. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Události|Podpora – hodnota|Poznámky|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
  
<a name="Legacy_Issues"></a>   
## <a name="legacy-issues"></a>Starší verze problémy  
 Přepínání – vzor prvků bude pouze podporovaná, až [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] položky nabídky se kontroluje a můžete prostřednictvím kódu programu určit potřebných k podpoře přepnutí vzor. Protože [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)] položky nabídky nevystavuje, zda má schopnost kontrolovat, vyvolání vzor se podporuje, pokud není zaškrtnuto políčko položky nabídky. Vždy podporují vyvolání vzor i pro položky nabídky, které by měly podporovat pouze přepnutí vzor budou provedeny výjimku. Toto je, aby klienti nepřestali být zaměňovat, že element, který byl podporující vzor vyvolání (Pokud byla položka nabídky nezaškrtnuté) už podporuje vzor po stane zaškrtnutí.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.MenuItem>  
 [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
