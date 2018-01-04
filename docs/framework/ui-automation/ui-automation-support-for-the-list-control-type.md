---
title: "Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku seznam"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
caps.latest.revision: "20"
author: Xansky
ms.author: mhopkins
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 6ff31bd7874af989332e83a05e644c816fc82108
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku seznam
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku seznam. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je sadu podmínek, které ovládacího prvku musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků.  
  
 Typ ovládacího prvku seznam poskytuje způsob, jak uspořádat ploché skupiny či skupin položek a umožňuje uživateli vybrat jednu nebo více z těchto položek. Typ ovládacího prvku seznam má přijít omezení na jaké typy podřízených elementů může obsahovat. To umožňuje zprostředkovateli automatizace uživatelského rozhraní pro podporu dobře známé prvku pro výběr kontejnery.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky v následující části platí pro všechny ovládací prvky, které implementují typ ovládacího prvku seznam, jestli [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]. Ovládací prvky kontejneru seznamu jsou příklady ovládacích prvků, které implementují typ ovládacího prvku seznam.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura stromu automatizace požadované uživatelského rozhraní  
 Následující tabulka znázorňuje dvě zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, která se vztahují k seznamu ovládací prvky a popisuje, co může být obsažený v každém zobrazení. Zobrazení ovládacího prvku obsahuje pouze elementy, které jsou ovládací prvky a zobrazení obsahu odebere redundantní informace ze stromu. Například se zveřejní ovládacího prvku typu textový slouží jako popisek pole se seznamem jako `ComboBox NameProperty`. Protože ovládací prvek text je již zveřejněný prostřednictvím zobrazení ovládacího prvku tímto způsobem není nutné jej zveřejněné dvakrát; Proto je odebrána ze zobrazení obsahu. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|Obsahuje prvky, které odpovídají ovládací prvky.|Odebere redundantní informace ze stromu tak, aby technologie pro usnadnění práce s nejmenší sadu důležité informace pro koncového uživatele.|  
|Seznam<br /><br /> -DataItem (0 nebo více)<br />-ListItem (0 nebo více)<br />-Group (0 nebo více)<br />-ScrollBar (0, 1 nebo 2)|Seznam<br /><br /> -DataItem (0 nebo více)<br />-ListItem (0 nebo více)<br />-Group (0 nebo více)|  
  
 Zobrazení ovládacího prvku ovládacího prvku, který implementuje typ ovládacího prvku seznam (například ovládací prvek seznamu) se skládá z:  
  
-   Nula nebo více položek v rámci ovládacího prvku seznam (položky může být založen na typy ovládacích prvků datová položka nebo položky seznamu)  
  
-   Nula nebo více seskupování ovládacích prvků v ovládacím prvku seznam  
  
-   Nula, jednu nebo dvě ovládací prvky posuvníku  
  
-  
  
 Zobrazení obsahu ovládacího prvku, který implementuje typ ovládacího prvku seznam (například ovládací prvek seznamu) se skládá z:  
  
-   Nula nebo více položek v rámci ovládacího prvku seznam (položky může být založen na typy ovládacích prvků datová položka nebo položky seznamu)  
  
-   Nula nebo více skupin v rámci ovládacího prvku seznam  
  
 Ovládací prvek seznamu nesmí mít položky, které mají hierarchický vztah, než se seskupeny dohromady. V případě položky obsahuje podřízené položky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, pak kontejneru seznamu by měla být založena na typ ovládacího prvku strom.  
  
 Vybrat položky v rámci ovládacího prvku seznam bude k dispozici z následníků na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu ovládacího prvku seznam. Všechny položky v rámci ovládacího prvku seznam musí patřit do stejné skupiny výběr. Vybrat položky v seznamu by měly být vystaveny jako typy ovládacích prvků ListItem (namísto datová položka).  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jehož hodnota nebo definice je obzvláště důležité pro ovládací prvky seznamu. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v části vlastnosti, [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélníku, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Pokud ovládací prvek seznamu má bod prokliknutelný (bod, který sloužící k způsobit seznamu přepínat), musí tento bod vystavenou přes tuto vlastnost.<br /><br /> Pokud hodnota `IsOffScreen` vlastnost je nastavena hodnota true, pak se <xref:System.Windows.Automation.NoClickablePointException> , bude vyvolána.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Hodnota vlastnosti název ovládacího prvku seznam by měl nesou kategorii možnosti, které se je uživatel vyzván k výběru. Tato vlastnost obvykle získá její název ze statického textu popisku. Pokud není k dispozici statický text popisku musí vývojář aplikace vystavit hodnotu pro vlastnost Name.<br /><br /> Tato vlastnost není vyžadována pro ovládací prvky seznamu je pouze pokud ovládací prvek se používá v rámci podstrom jiného ovládacího prvku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|V části poznámky.|Pokud je statický text popisku této vlastnosti musí vystavit odkaz u daného ovládacího prvku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Seznam|Tato hodnota je stejný pro všechny rozhraní uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"seznam|Lokalizovaný řetězec odpovídající typ ovládacího prvku seznam.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Ovládací prvek seznamu je vždy součástí obsahu zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Ovládací prvek seznamu je vždy součástí zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Hodnota TRUE|Kontejner může přijmout vstup z klávesnice tuto vlastnost hodnota musí být true.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|V části poznámky.|Text nápovědy pro ovládací prvky seznamu by měl vysvětlit, proč je uživatel požadováno umožní výběr ze seznamu možností. Například "výběru položky z tohoto seznamu bude nastavit rozlišení monitoru."|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Požadované vlastnosti a vzory ovládacích prvků automatizace uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řízení vzory potřeba podporovat ovládací prvky seznamu. Další informace o vzory ovládacích prvků, najdete v části [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Vlastnost vzor nebo vzor ovládacího prvku|Podpora – hodnota|Poznámky|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Požadováno|Musí implementovat všechny ovládací prvky, které podporují typ ovládacího prvku seznam `ISelectionProvider` při výběru stavu zachovaný mezi položkami obsažené v ovládacím prvku. Pokud položky v rámci kontejneru se nedá vybrat, musíte použít typ ovládacího prvku skupina.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Závisí|Ovládací prvky seznamu vždy nevyžadují, aby se vybere položka.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Závisí|Ovládací prvky seznamu může být jeden nebo více výběr kontejnerů.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Závisí|Tento vzor ovládacích prvků implementujte, pokud jsou posouvatelného položky v kontejneru.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Závisí|Tento vzor implementujte, pokud navigační mřížky musí být k dispozici na základě jednotlivých položek.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Závisí|Tento vzor ovládacích prvků implementujte, pokud ovládací prvek může podporovat více zobrazení položek v kontejneru.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Nikdy|`ITableProvider`nikdy je podporována pro typ ovládacího prvku seznam. Pokud ovládací prvek by měly podporovat tento vzor ovládacích prvků, by měla ovládacího prvku založena na typ ovládacího prvku mřížky Data.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřeba podporovat všechny ovládací prvky seznamu. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Události|Podpora – hodnota|Poznámky|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.List>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
