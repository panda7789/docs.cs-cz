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
ms.openlocfilehash: 39804f7a525a45a4de37e7dded9ac4998280755f
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129611"
---
# <a name="ui-automation-support-for-the-edit-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku úprav
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podpora pro typ ovládacího prvku úprav. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je představují sadu podmínek, které ovládací prvek musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny ke [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzorů ovládacích prvků.  
  
 Ovládacích prvcích pro úpravy povolit uživatelům zobrazení a úpravám jednoduché řádek textu bez bohatého formátování podpory.  
  
 Následující části definují požadovaný [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzorů ovládacích prvků a události pro typ ovládacího prvku úprav. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechny ovládacích prvcích pro úpravy, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Požadované uživatelské rozhraní automatizace stromová struktura  
 Následující tabulka popisuje ovládací prvek zobrazení a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, které se vztahují na ovládacích prvcích pro úpravy a popisuje, co mohou být obsaženy v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, přečtěte si téma [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Ovládací prvek zobrazení|Zobrazení obsahu|  
|------------------|------------------|  
|Upravit|Upravit|  
  
 Ovládací prvky, které implementují typ ovládacího prvku úprav bude mít vždy nula posuvníků v ovládacím zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, protože je ovládací prvek jedním řádkem. Jeden řádek textu může obtékat v některých scénářích rozložení. Typ ovládacího prvku úprav je nejvhodnější pro malé množství upravovatelného nebo vybrat text uchování.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice je obzvláště důležité pro ovládacích prvcích pro úpravy. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, viz [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Ovládací prvek pro úpravy musí mít bod pro kliknutí, která poskytuje vstup k upravit části ovládacího prvku, když uživatel klikne myší existuje.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může získat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Název ovládacího prvku pro úpravy je obvykle vygenerován ze statického textu popisku. Pokud není statický text popisku, hodnota vlastnosti pro `Name` musíte být přiřazeni vývojářem aplikace. `Name` Vlastnost by měla obsahovat nikdy textový obsah ovládacího prvku pro úpravy.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|V části poznámky.|Pokud je popisek statický text přidružený k ovládacímu prvku, tato vlastnost musí vystavit odkaz na tento ovládací prvek. Pokud je ovládací prvek text %1.dílčí součást jiného ovládacího prvku, nebude mít `LabeledBy` sadu vlastností.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Upravit|Tato hodnota je stejný pro všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"edit"|Lokalizovaný řetězec odpovídající typ ovládacího prvku úprav.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Ovládací prvek pro úpravy je vždy součástí obsahu zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Ovládací prvek pro úpravy je vždy součástí zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsPasswordProperty>|V části poznámky.|Musí být nastavena na hodnotu true v ovládacích prvcích pro úpravy, které obsahují hesla. Pokud textové pole neobsahuje heslo obsah pak tato vlastnost slouží čtečka obrazovky k určení, zda stisknutí kláves byste si měli přečíst jako uživatel je.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní a vlastnosti  
 V následující tabulce jsou uvedeny vzorů ovládacích prvků vyžaduje to, že všechny ovládacích prvcích pro úpravy. Další informace o vzorů ovládacích prvků naleznete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Vlastnosti ovládacího prvku modelu a ovládání vzor|Podpora/hodnota|Poznámky|  
|-----------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ITextProvider>|Závisí|Ovládacích prvcích pro úpravy by měly podporovat vzoru ovládacích prvků textu, protože informace by měly mít vždycky k dispozici pro klienty.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závisí|Vzor hodnota musí vystavit všech ovládacích prvcích pro úpravy, které provést řetězec.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.IsReadOnly%2A>|V části poznámky.|Tato vlastnost musí být nastavena označující, zda ovládací prvek může mít hodnotu nastavení prostřednictvím kódu programu, nebo je možné upravovat uživatelem.|  
|<xref:System.Windows.Automation.Provider.IValueProvider.Value%2A>|V části poznámky.|Tato vlastnost vrátí textový obsah ovládacího prvku pro úpravy. Pokud `IsPasswordProperty` je nastavena na `true`, musí vyvolat tuto vlastnost `InvalidOpertaionException` na požádání.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider>|Závisí|Hodnota rozsahu – vzor ovládacích prvků musí vystavit všech ovládacích prvcích pro úpravy, které provést číselného rozsahu.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Minimum%2A>|V části poznámky.|Tato vlastnost musí mít nejmenší hodnota, obsah textové pole může být nastaven na.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Maximum%2A>|V části poznámky.|Tato vlastnost musí mít největší obsah v textovém poli může být nastaven na hodnotu.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.SmallChange%2A>|V části poznámky.|Tato vlastnost musí určit počet desetinných míst, které může být hodnota nastavena na. Pokud úpravy trvat jenom celá čísla, `SmallChangeProperty` musí být 1. Pokud úpravy trvá rozmezí 1.0 a 2.0, pak bude `SmallChangeProperty` musí být 0,1. Pokud má ovládací prvek pro úpravy rozsahu od 1,00 do 2.00 pak bude `SmallChangeProperty` musí být 0,001.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.LargeChange%2A>|`Null`|Tato vlastnost nemusí být odhalen na prvek pro úpravy.|  
|<xref:System.Windows.Automation.Provider.IRangeValueProvider.Value%2A>|V části poznámky.|Tato vlastnost bude tato informace uvedena číselné obsah ovládacího prvku pro úpravy. Když je nastavit přesnější hodnotu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klienta v rámci z rozsahů určených v `Minimum` a `Maximum` vlastnosti hodnotu vlastnosti automaticky se zaokrouhlí na nejbližší akceptovaná hodnota.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacích prvcích pro úpravy vyžaduje to, že všechny události. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextSelectionChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.TextPatternIdentifiers.TextChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> události změny vlastnosti.|Závisí|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> události změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> události změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> události změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> události změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> události změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> události změny vlastnosti.|Nikdy|Žádné|  
|<xref:System.Windows.Automation.RangeValuePatternIdentifiers.ValueProperty> události změny vlastnosti.|Závisí|Pokud ovládací prvek podporuje vzoru ovládacích prvků hodnota rozsahu, musí podporovat této události.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.Edit>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
