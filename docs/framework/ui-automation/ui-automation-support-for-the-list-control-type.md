---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku seznam
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: b4223f479fa640cd528bff9ccf0d6b4b31cfb127
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54735698"
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku seznam
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku seznamu. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je představují sadu podmínek, které ovládací prvek musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny ke [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzorů ovládacích prvků.  
  
 Typ ovládacího prvku seznam poskytuje způsob, jak uspořádat bez stromové struktury skupin nebo skupin položek a umožňuje uživateli vybrat jednu nebo více z těchto položek. Typ ovládacího prvku seznam má volné omezení na typy podřízených elementů může obsahovat. To umožňuje zprostředkovatelů automatizace uživatelského rozhraní pro podporu dobře známý prvek pro výběr kontejnery.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky v následující části platí pro všechny ovládací prvky, které implementují typ ovládacího prvku seznam určuje, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]. Seznam kontejnerů ovládacích prvků jsou příkladem ovládací prvky, které implementují typ ovládacího prvku seznamu.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Požadované uživatelské rozhraní automatizace stromová struktura  
 Následující tabulka znázorňuje dvě zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom, který patří do seznamu ovládací prvky a popisuje, co mohou být obsaženy v každém zobrazení. Ovládací prvek zobrazení obsahuje pouze prvky, které jsou ovládací prvky a zobrazení obsahu Odebere nadbytečné informace ze stromu. Například ovládací prvek textu použitý k popisku pole se seznamem vystavena jako `ComboBox NameProperty`. Protože ovládací prvek textu je již vystavena tímto způsobem prostřednictvím zobrazení ovládacího prvku není nutné ji vystavený dvakrát; proto bude odebrán ze zobrazení obsahu. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, přečtěte si téma [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Ovládací prvek zobrazení|Zobrazení obsahu|  
|------------------|------------------|  
|Obsahuje elementy, které odpovídají ovládací prvky.|Odebere nadbytečné informace ze stromu technologie pro usnadnění práce s nejmenší sadu důležité informace pro koncového uživatele.|  
|Seznam<br /><br /> -Datové položky (0 nebo více)<br />-ListItem (0 nebo více)<br />-Group (0 nebo více)<br />-Posuvník (0, 1 nebo 2)|Seznam<br /><br /> -Datové položky (0 nebo více)<br />-ListItem (0 nebo více)<br />-Group (0 nebo více)|  
  
 Ovládací prvek zobrazení pro ovládací prvek, který implementuje typ ovládacího prvku seznam (jako je například ovládací prvek seznamu) zahrnuje:  
  
- Nula nebo více položek v rámci ovládacího prvku seznam (položky může být založen na typy ovládacích prvků datová položka nebo položky seznamu).
  
- Nula nebo více skupin ovládacích prvků v rámci ovládacího prvku seznamu.
  
- Nula, jeden nebo dva ovládací prvky posuvníku.
  
Zobrazení obsahu ovládacího prvku, který implementuje typ ovládacího prvku seznam (jako je například ovládací prvek seznamu) zahrnuje:  
  
- Nula nebo více položek v rámci ovládacího prvku seznam (položky může být založen na typy ovládacích prvků datová položka nebo položky seznamu).
  
- Nula nebo více skupin v rámci ovládacího prvku seznam.

Ovládací prvek seznamu nesmí obsahovat položky, které mají hierarchický vztah než byla seskupena dohromady. V případě položek obsahuje podřízené položky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom, pak kontejneru seznamu by měla vycházet z typ ovládacího prvku strom.  
  
 Volitelných položek v ovládacím prvku seznamu budou k dispozici následníků na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu ovládacího prvku seznamu. Všechny položky v rámci ovládacího prvku seznam musí patřit do stejné skupiny výběru. Volitelných položek v seznamu by měly být vystaveny jako typy ovládacího prvku ListItem (ne datové položky).  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice je obzvláště důležité pro ovládací prvky seznamu. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, viz [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Pokud je ovládací prvek seznamu bod pro kliknutí (bodu, který se dá kliknout, aby se seznam přepínat), tento bod musí být vystavené prostřednictvím této vlastnosti.<br /><br /> Pokud hodnota `IsOffScreen` vlastnost má hodnotu true, pak bude <xref:System.Windows.Automation.NoClickablePointException> , bude vyvolána.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může získat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Hodnota vlastnosti ovládacího prvku seznamu název by měl sdělit kategorie možností, které se je uživatel vyzván k výběru z. Tato vlastnost obvykle anglický název z statický text popisku. Pokud není statický text popisku musí vývojář aplikace vystavit hodnotu pro vlastnost Name.<br /><br /> Tato vlastnost není vyžadována pro ovládací prvky seznamu se pouze pokud ovládací prvek se používá v rámci podstrom jiný ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|V části poznámky.|Pokud je statický text popisku této vlastnosti musí vystavit odkaz na tento ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Seznam|Tato hodnota je stejný pro všechny architektury uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"seznam"|Lokalizovaný řetězec odpovídající typ ovládacího prvku seznamu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Pravda|Ovládací prvek seznamu je vždy součástí obsahu zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Pravda|Ovládací prvek seznamu je vždy součástí zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Pravda|Kontejner můžete přijmout vstup z klávesnice tato hodnota vlastnosti musí být true.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|V části poznámky.|Text nápovědy pro ovládací prvky seznamu by měl vysvětlit, proč je požadováno uživateli umožní výběr ze seznamu možností. Například "výběru položky z tohoto seznamu nastaví rozlišení zobrazení monitoru."|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns-and-properties"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní a vlastnosti  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit vzory vyžaduje to, že seznam ovládacích prvků. Další informace o vzorů ovládacích prvků naleznete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|Vlastnosti ovládacího prvku modelu nebo vzor|Podpora/hodnota|Poznámky|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Požadováno|Musí implementovat všechny ovládací prvky, které podporují typ ovládacího prvku seznam `ISelectionProvider` při výběru stavu je zachovat mezi položky obsažené v ovládacím prvku. Pokud se nedá vybrat položky v rámci kontejneru, musí použít typ ovládacího prvku skupina.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Závisí|Ovládací prvky seznamu není vždy třídou vyžadována vybrat položku.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Závisí|Ovládací prvky seznamu může být jeden nebo více výběrů kontejnerů.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Závisí|Implementujte toto – vzor ovládacích prvků, pokud jsou posuvný položky v kontejneru.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Závisí|Tento model implementujte, při navigaci mřížky musí být k dispozici na základě jednotlivých položkách.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Závisí|Tento ovládací prvek model implementujte, pokud ovládací prvek může podporovat více zobrazení položek v kontejneru.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Nikdy|`ITableProvider` Nikdy se podporuje pro typ ovládacího prvku seznamu. Jestli ovládací prvek podporovat tento – vzor ovládacích prvků, by měl ovládací prvek podle v datové mřížce typ ovládacího prvku.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřebné to, že všechny ovládací prvky seznamu. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Události|Podpora/hodnota|Poznámky|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Závisí|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Závisí|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> události změny vlastnosti.|Požadováno|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> události změny vlastnosti.|Požadováno|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> události změny vlastnosti.|Požadováno|Žádná|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty> události změny vlastnosti.|Závisí|Žádná|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty> události změny vlastnosti.|Závisí|Žádná|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty> události změny vlastnosti.|Závisí|Žádná|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty> události změny vlastnosti.|Závisí|Žádná|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty> události změny vlastnosti.|Závisí|Žádná|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty> události změny vlastnosti.|Závisí|Žádná|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty> události změny vlastnosti.|Závisí|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádná|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Automation.ControlType.List>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
