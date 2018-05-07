---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku úprav
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Edit
- Edit control type
- UI Automation, Edit control type
ms.assetid: 6db9d231-c0a0-4e17-910e-ac80357f774f
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 0cd1744702448836e6b4e1eb04d14725a1baba39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku úprav
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku úprav. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je sadu podmínek, které ovládacího prvku musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků.  
  
 Ovládacích prvcích pro úpravy povolit uživatelům zobrazení a úpravy jednoduché řádku textu bez bohaté formátování podpory.  
  
 Následující části zadejte požadované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastností, vzory ovládacích prvků a události pro typ ovládacího prvku úprav. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechny ovládacích prvcích pro úpravy, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Struktura stromu automatizace požadované uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, která se vztahují na ovládacích prvcích pro úpravy a popisuje, co může být obsažený v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|Upravit|Upravit|  
  
 Ovládací prvky, které implementují typ ovládacího prvku úprav bude mít vždy nulové posuvníky v zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, protože je ovládacího prvku jeden řádek. V některých scénářích rozložení může obtékat jednoho řádku textu. Typ ovládacího prvku úprav je nejvhodnější pro uložení malé množství text upravovat nebo které lze vybírat.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jehož hodnota nebo definice je obzvláště důležité pro ovládacích prvcích pro úpravy. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v části vlastnosti, [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélníku, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Textové pole musí mít bod můžete kliknout, který poskytuje zaměření pro vstup pro úpravy část ovládacího prvku, po kliknutí myší existuje.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Název ovládacích prvků pro úpravy se obvykle generují z statický text popisku. Pokud není statický text popisku, hodnota vlastnosti `Name` musí být přiřadila vývojáře aplikace. `Name` Vlastnost by měla obsahovat nikdy textový obsah ovládacích prvků pro úpravy.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|V části poznámky.|Pokud je statický text popisku, přidružený k ovládacímu prvku, tato vlastnost musí vystavit odkaz u daného ovládacího prvku. Pokud ovládací prvek text je dílčí nevyberou, nebudou mít `LabeledBy` sadu vlastností.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Upravit|Tato hodnota je stejný pro všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"upravit"|Lokalizovaný řetězec odpovídající typ ovládacího prvku úprav.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Textové pole je vždy součástí obsahu zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Textové pole je vždy součástí zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|V části poznámky.|Musí být nastavena na hodnotu true v ovládacích prvcích pro úpravy obsahující hesla. Pokud ovládací prvek upravit neobsahuje heslo obsah pak tato vlastnost slouží čtecí zařízení k určení, zda stisknutí kláves byste si měli přečíst jako typy uživatelů je.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Požadované vlastnosti a vzory ovládacích prvků automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny požadované vzory ovládacích prvků mají být podporovány všechny ovládací prvky úprav. Další informace o vzory ovládacích prvků najdete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Vlastnost vzor vzor a ovládání ovládací prvek|Podpora – hodnota|Poznámky|  
|-----------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|Závisí|Ovládacích prvcích pro úpravy by měly podporovat vzor Text ovládacích prvků, protože informace by měl být vždy k dispozici pro klienty.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závisí|Všechny ovládací prvky úprav, které provést řetězec musí vystavit vzoru hodnotu.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|V části poznámky.|Tato vlastnost musí být nastavena zda ovládací prvek může mít hodnotu nastavit programově, nebo můžete upravovat uživatele.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|V části poznámky.|Tato vlastnost vrátí textový obsah ovládacích prvků pro úpravy. Pokud `IsPasswordProperty` je nastaven na `true`, musíte zvýšit tuto vlastnost `InvalidOpertaionException` vyžádání.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Závisí|Všechny ovládací prvky úprav, které provést číselný rozsah musí vystavit hodnotu rozsahu – vzor ovládacích prvků.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|V části poznámky.|Tato vlastnost musí být nejmenší hodnotu, která ovládací prvek upravit obsah může být nastaven na.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|V části poznámky.|Tato vlastnost musí být největší hodnotu, která ovládací prvek upravit obsah může být nastaven na.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|V části poznámky.|Tato vlastnost musí označovat počet desetinných míst, která hodnotu můžete nastavit na. Pokud úpravy trvat jenom celá čísla, `SmallChangeProperty` musí být 1. Pokud úpravy trvá rozmezí 1.0 a 2.0, pak se `SmallChangeProperty` musí být 0,1. Pokud ovládací prvek upravit trvá rozsah od 1.00 do 2.00 potom `SmallChangeProperty` musí být 0,001.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Tato vlastnost nemusí být odhalen na ovládací prvek upravit.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|V části poznámky.|Tato vlastnost bude znamenat číselné obsah ovládacích prvků pro úpravy. Když přesnější hodnota je nastavena [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klienta v rámci rozsahů určených v `Minimum` a `Maximum` vlastnosti, hodnota vlastnosti automaticky zaokrouhlen na nejbližší hodnotu přijala.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace požadované uživatelského rozhraní  
 Následující tabulka uvádí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události muset být podporována všemi ovládacích prvcích pro úpravy. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> událost změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> událost změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> událost změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> událost změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> událost změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> událost změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> událost změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> událost změny vlastnosti.|Závisí|Pokud ovládací prvek podporuje rozsah vzoru ovládacích prvků hodnota, musí podporovat této události.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.Edit>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
