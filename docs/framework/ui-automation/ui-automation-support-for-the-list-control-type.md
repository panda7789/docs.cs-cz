---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku seznam
ms.date: 03/30/2017
helpviewer_keywords:
- control types, List
- List control type
- UI Automation, List control type
ms.assetid: 0e959fcb-50f2-413b-948d-7167d279bc11
ms.openlocfilehash: 2926e06cfbe065ad8a5bccdb7ebaf16596721def
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179712"
---
# <a name="ui-automation-support-for-the-list-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku seznam
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahuje informace o podpoře pro typ ovládacího prvku Seznam. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programu je typ ovládacího prvku sada podmínek, které <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> musí ovládací prvek splňovat, aby bylo možné použít vlastnost. Podmínky zahrnují zvláštní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, hodnoty vlastností a vzory ovládacích prvku.  
  
 Typ ovládacího prvku Seznam poskytuje způsob uspořádání ploché skupiny nebo skupin položek a umožňuje uživateli vybrat jednu nebo více z těchto položek. List typ ovládacího prvku má volné omezení na jaké typy podřízených prvků může obsahovat. To umožňuje zprostředkovatelům automatizace uživatelského rozhraní podporovat známý prvek pro kontejnery výběru.  
  
 Požadavky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v následujících částech platí pro všechny ovládací prvky, které implementují typ ovládacího prvku List, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 nebo Windows Forms. Seznam ovládacíprvky kontejneru jsou příkladem ovládacích prvků, které implementují seznam typ ovládacího prvku.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Požadovaná struktura stromu automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje dvě [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zobrazení stromu, která se připojují k ovládacím prvkům seznamu, a popisuje, co lze v každém zobrazení ztvárnit. Zobrazení ovládacího prvku obsahuje pouze prvky, které jsou ovládací prvky a zobrazení obsahu odebere nadbytečné informace ze stromu. Například textový ovládací prvek použitý k označení pole se `ComboBox NameProperty`seznamem bude vystaven jako . Vzhledem k tomu, že ovládací prvek textu je již vystaventímto způsobem prostřednictvím zobrazení ovládacího prvku není nutné mít vystaveny dvakrát; proto je odebrán ze zobrazení obsahu. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu naleznete v [tématu Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|Obsahuje prvky, které odpovídají ovládací prvky.|Odebere redundantní informace ze stromu tak, aby asistenční technologie pracovat s nejmenší sadu smysluplné informace pro koncového uživatele.|  
|Seznam<br /><br /> - DataItem (0 nebo více)<br />- ListItem (0 nebo více)<br />- Skupina (0 nebo více)<br />- ScrollBar (0, 1 nebo 2)|Seznam<br /><br /> - DataItem (0 nebo více)<br />- ListItem (0 nebo více)<br />- Skupina (0 nebo více)|  
  
 Ovládací zobrazení pro ovládací prvek, který implementuje typ ovládacího prvku List (například ovládací prvek seznamu) se skládá z:  
  
- Nula nebo více položek v rámci ovládacího prvku seznamu (položky mohou být založeny na typech ovládacích údajů položky seznamu nebo položky dat).
  
- Nula nebo více skupinových ovládacích prvků v rámci ovládacího prvku seznamu.
  
- Nula, jeden nebo dva ovládací prvky posuvníku.
  
Zobrazení obsahu ovládacího prvku, který implementuje typ ovládacího prvku List (například ovládací prvek seznamu), se skládá z:  
  
- Nula nebo více položek v rámci ovládacího prvku seznamu (položky mohou být založeny na typech ovládacích údajů položky seznamu nebo položky dat).
  
- Nula nebo více skupin v rámci ovládacího prvku seznamu.

Ovládací prvek seznamu nesmí obsahovat položky, které mají jiný hierarchický vztah než seskupené. Pokud položky mají [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podřízené položky ve stromu, pak kontejner seznamu by měla být založena na stromu typ ovládacího prvku.  
  
 Volitelné položky v rámci ovládacího prvku seznamu budou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] k dispozici od potomků ve stromu ovládacího prvku seznamu. Všechny položky v ovládacím prvku seznamu musí patřit do stejné skupiny výběru. Volitelné položky v seznamu by měly být vystaveny jako Typy ovládacích prvku ListItem (namísto DataItem).  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vlastnosti, jejichž hodnota nebo definice jsou obzvláště důležité pro ovládací prvky seznamu. Další informace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o vlastnostech naleznete v [tématu Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečný napříč všechny ovládací prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Nejvzdálenější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Pokud má ovládací prvek seznamu bod, na který lze kliknout (bod, na který lze klepnout, aby se seznam zaměřil), musí být tento bod vystaven prostřednictvím této vlastnosti.<br /><br /> Pokud je hodnota `IsOffScreen` vlastnosti true, <xref:System.Windows.Automation.NoClickablePointException> pak bude zvýšena.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Hodnota vlastnosti Název ovládacího prvku seznamu by měla sdělit kategorii možností, ze kterých je uživatel vyzván k výběru. Tato vlastnost obvykle získá svůj název z statického textového popisku. Pokud není statický textový popisek, vývojář aplikace musí vystavit hodnotu vlastnosti Name.<br /><br /> Tato vlastnost není vyžadována pouze pro ovládací prvky seznamu je-li ovládací prvek používá v rámci podstromu jiného ovládacího prvku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Pokud je statický textový popisek pak tato vlastnost musí vystavit odkaz na tento ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Seznam|Tato hodnota je stejná pro všechny architektury ui.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"seznam"|Lokalizovaný řetězec odpovídající typu ovládacího prvku Seznam.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Ovládací prvek seznamu je vždy součástí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zobrazení obsahu stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Ovládací prvek seznamu je vždy součástí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacího zobrazení stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Pokud kontejner může přijímat vstup z klávesnice, měla by být tato hodnota vlastnosti pravdivá.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Viz poznámky.|Text nápovědy pro ovládací prvky seznamu by měl vysvětlit, proč je uživatel vyzván k výběru ze seznamu možností. Například "Výběr položky z tohoto seznamu nastaví rozlišení zobrazení monitoru."|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns-and-properties"></a>Požadované vzory a vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vzory ovládacích prvků, které musí být podporovány ovládacími prvky seznamu. Další informace o vzorcích ovládacího prvku naleznete v [tématu Přehled řídicích vzorů automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vlastnost Vzorek/vzorek ovládacího prvku|Podpora/hodnota|Poznámky|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Požaduje se|Všechny ovládací prvky, které `ISelectionProvider` podporují typ ovládacího prvku List musí implementovat při zachování stavu výběru mezi položkami obsaženými v ovládacím prvku. Pokud položky v kontejneru nejsou volitelné, musí být použit typ ovládacího prvku Skupiny.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.IsSelectionRequired%2A>|Závisí|Ovládací prvky seznamu ne vždy vyžadují, aby byla položka vybrána.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider.CanSelectMultiple%2A>|Závisí|Ovládací prvky seznamu mohou být kontejnery pro jeden nebo více výběrů.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Závisí|Implementujte tento vzor ovládacího prvku, pokud jsou položky v kontejneru posuvné.|  
|<xref:System.Windows.Automation.Provider.IGridProvider>|Závisí|Implementujte tento vzor, když navigace v mřížce musí být k dispozici pro položku podle položek.|  
|<xref:System.Windows.Automation.Provider.IMultipleViewProvider>|Závisí|Implementujte tento vzor ovládacího prvku, pokud ovládací prvek může podporovat více zobrazení položek v kontejneru.|  
|<xref:System.Windows.Automation.Provider.ITableProvider>|Never (Nikdy)|`ITableProvider`není nikdy podporován pro typ ovládacího prvku Seznam. Pokud ovládací prvek by měl podporovat tento vzor ovládacího prvku, pak ovládací prvek by měl být založen na typu ovládacího prvku datové mřížky.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny události, které musí být podporovány všemi ovládacími prvky seznamu. Další informace o událostech naleznete v [tématu Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událost|Podpora/hodnota|Poznámky|  
|---------------------------------------------------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.SelectionPatternIdentifiers.InvalidatedEvent>|Závisí|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LayoutInvalidatedEvent>|Závisí|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontallyScrollableProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalScrollPercentProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.HorizontalViewSizeProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalScrollPercentProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticallyScrollableProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ScrollPatternIdentifiers.VerticalViewSizeProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požaduje se|Žádný|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.List>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
