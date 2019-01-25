---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku obrázek
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, Image control type
- control types, Image
- Image control type
ms.assetid: 4e0eeefb-e09b-46d2-b83b-0a7e35543ab8
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: cfd5057ee95c5a569d85a29a25afe9a32240e801
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707788"
---
# <a name="ui-automation-support-for-the-image-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku obrázek
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podpora pro typ ovládacího prvku obrázek. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je představují sadu podmínek, které ovládací prvek musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny ke [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzorů ovládacích prvků.  
  
 Typ ovládacího prvku obrázek bude podporovat Image prvky používané jako ikony, informační grafika a grafy. Ovládací prvky používat jako pozadí nebo vodoznak Image nebude podporovat typ ovládacího prvku obrázek.  
  
 Následující části definují požadovaný [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzorů ovládacích prvků a události pro typ ovládacího prvku obrázek. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechny ovládací prvky obrázků, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Požadované uživatelské rozhraní automatizace stromová struktura  
 Následující tabulka popisuje ovládací prvek zobrazení a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, které se vztahují na ovládacích prvcích obrázků a popisuje, co mohou být obsaženy v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, přečtěte si téma [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Ovládací prvek zobrazení|Zobrazení obsahu|  
|------------------|------------------|  
|Image|Bitové kopie (závisí, zda bitová kopie obsahuje informace (na základě hodnoty z `IsContentElement` vlastnosti))|  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit typ vlastnosti, jejichž hodnota nebo definice je obzvláště důležité pro bitovou kopii. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, viz [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Bod umožňující kliknutí na tento ovládací prvek obrázku musí být bod ovládacím prvkem obrázku v rámci ohraničující obdélník.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|V části poznámky.|Pokud ovládací prvek může získat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Vlastnost Name musí být vystaveny pro všechny ovládací prvky obrázků, které obsahují informace. Programový přístup k těmto informacím vyžaduje, aby textový ekvivalent obrázek poskytnuta. Pokud tento ovládací prvek obrázku je čistě dekorativní, se musí pouze zobrazí v ovládacím zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu a není nutné mít název. Architektury uživatelského rozhraní musí podporovat ALT nebo alternativní text vlastnosti bitové kopie, které můžete nastavit od jejich rámci. Tato vlastnost bude poté budou mapovány [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnost Name.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|V části poznámky.|Pokud je statický text popisku této vlastnosti musí vystavit odkaz na tento ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Image|Tato hodnota je stejný pro všechny architektury uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"image"|Lokalizovaný řetězec odpovídající typ ovládacího prvku obrázek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|V části poznámky.|Tento ovládací prvek obrázku musí být součástí obsahu zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, pokud obsahuje důležité informace, které ještě není vystavený pro koncového uživatele.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Pravda|Tento ovládací prvek obrázku je vždy součástí zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|V části poznámky.|Vlastnost HelpText zpřístupňuje lokalizovaný řetězec, který popisuje skutečné vzhled ovládacího prvku (například červený čtvereček obsahující bílý znak "X") nebo jiné informace popisu tlačítka, které jsou spojené s imagí.<br /><br /> Tato vlastnost musí být podporováni, když dlouhý popis, je potřeba sdělit Další informace o ovládacím prvku obrázek. Například na složité graf nebo diagram. Tato vlastnost mapuje na značku HTML LongDesc a značky Desc grafiky SVG (Scalable Vector). Vývojáři pracující s ovládacími prvky obrázků musí podporovat vlastnost umožňující visual popis, který má být nastavena na ovládacím prvku. Tato vlastnost musí být mapována na vlastnost VisualDescription automatizace uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>|V části poznámky.|Pokud tento ovládací prvek obrázku představuje informace o konkrétní položku na obrazovce stavu, ovládací prvek by měly být obsaženy v rámci položky. Pokud je na obrázku je obsažen v položku položky musí podporovat vlastnost stavu a vyvolat příslušné oznámení, kdy se stav změní.<br /><br /> Pokud bitovou kopii je samostatný ovládací prvek a je takzvané stavu musí tato vlastnost podporována.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit vzory vyžaduje to, že všechny ovládací prvky obrázků. Další informace o vzorů ovládacích prvků naleznete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|– Vzor ovládacích prvků|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IGridItemProvider>|Závisí|Tento ovládací prvek obrázku podporuje položky mřížky vzor, pokud je ovládací prvek v rámci kontejneru mřížky.|  
|<xref:System.Windows.Automation.Provider.ITableItemProvider>|Závisí|Tento ovládací prvek obrázku podporuje vzor položka tabulky, pokud je ovládací prvek do kontejneru, který obsahuje ovládací prvky záhlaví.|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Nikdy|Pokud tento ovládací prvek obrázku obsahuje bitovou kopii lze kliknout, by měl ovládací prvek podporovat typ ovládacího prvku, který podporuje Invoke vzor, jako je například typ ovládacího prvku tlačítko.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Nikdy|Ovládací prvky obrázků by neměl podporují vzor výběru položky.|  
  
<a name="Required_UI_Automation_Events"></a>   
## <a name="required-ui-automation-events"></a>Události automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřebné to, že všechny ovládací prvky obrázků. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Nikdy|Žádná|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Nikdy|Žádná|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Nikdy|Žádná|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Nikdy|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> události změny vlastnosti.|Požadováno|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> události změny vlastnosti.|Požadováno|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> události změny vlastnosti.|Požadováno|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty> události změny vlastnosti.|Požadováno|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádná|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádná|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Automation.ControlType.Image>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
