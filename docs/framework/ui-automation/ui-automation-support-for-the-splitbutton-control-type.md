---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku SplitButton
ms.date: 03/30/2017
helpviewer_keywords:
- Split Button control type
- control types, Split Button
- UI Automation, Split Button control type
ms.assetid: 14b05ccf-bcd8-4045-9bae-f7679cd98711
ms.openlocfilehash: b3b8346ca77110b811ee0b226bfa2b4cbf2e18db
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71041100"
---
# <a name="ui-automation-support-for-the-splitbutton-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku SplitButton
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Toto téma poskytuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podpoře pro typ ovládacího prvku SplitButton. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nástroji je typ ovládacího prvku sada podmínek, které musí ovládací prvek splňovat, aby bylo možné <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost použít. Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností a vzory ovládacích prvků.  
  
 Ovládací prvek tlačítko rozdělení umožňuje provést akci s ovládacím prvkem a rozšířit ovládací prvek tak, aby se zobrazil seznam dalších možných akcí, které lze provést.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku SplitButton. Požadavky se vztahují na všechny ovládací prvky rozděleného tlačítka [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]bez ohledu na [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)]to, zda, [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)]nebo. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]  
  
## <a name="required-ui-automation-tree-structure"></a>Požadovaná stromová struktura automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahu stromové struktury, které se vztahují k ovládacím prvkům tlačítko rozdělení, a popisuje, co může být v každém zobrazení obsaženo. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacích prvků|Zobrazení obsahu|  
|------------------|------------------|  
|SplitButton<br /><br /> <ul><li>Obrázek (0 nebo 1)</li><li>Text (0 nebo 1)</li><li>Tlačítko (1 nebo 2)<br /><br /> <ul><li>Nabídka (0 nebo 1; se zobrazí jako podřízená položka, která podporuje vzor ovládacích prvků ExpandCollapse)</li><li>MenuItem (1 až mnoho)</li></ul></li></ul>|SplitButton<br /><br /> -MenuItem (1 až mnoho)|  
  
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice je obzvláště relevantní pro rozdělené ovládací prvky tlačítek. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostech najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Majetek|Value|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečná napříč všemi ovládacími prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Vnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Podporováno, pokud je ohraničen obdélník. Pokud není k dispozici žádný bod v ohraničujícím obdélníku a provádíte specializované testování přístupů, přepíšete a získáte bod, který je k dispozici.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může obdržet fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Návrat|Na tlačítku se zobrazí název ovládacího prvku tlačítko rozdělení.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Null|Ovládací prvky rozděleného tlačítka nemají statický textový popisek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|SplitButton|Tato hodnota je stejná pro všechny architektury uživatelského rozhraní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"tlačítko rozdělení"|Lokalizovaný řetězec odpovídající typu ovládacího prvku SplitButton|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Viz poznámky.|Text nápovědy může indikovat výsledek aktivace tlačítka rozdělení, což je obvykle stejný typ informací prezentovaný pomocí popisu tlačítka.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Pravda|Ovládací prvek tlačítko rozdělení obsahuje informace pro koncového uživatele.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Pravda|Ovládací prvek tlačítko rozdělení je viditelný pro koncového uživatele.|  
  
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory ovládacího prvku automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vzory ovládacích prvků, které musí být podporovány pomocí ovládacích prvků tlačítko rozdělení. Další informace o vzorech ovládacích prvků naleznete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vzor ovládacího prvku|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Požadováno|Pro rozdělená tlačítka jsou vždy k vyvolání přidružena výchozí akce.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Požadováno|Rozdělená tlačítka mají vždy možnost rozšířit seznam možností.|  
  
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, které musí být podporovány všemi ovládacími prvky tlačítka rozdělení. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událostí|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>událost změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
  
## <a name="splitbutton-control-example"></a>Příklad ovládacího prvku SplitButton  
 Následující obrázek znázorňuje typ ovládacího prvku SplitButton v ovládacím prvku datová mřížka.  
  
 ![Tlačítko rozdělení](./media/uiauto-splitbutton-detailed.gif "uiauto_splitbutton_detailed")  
  
 Zobrazení ovládacího prvku a zobrazení obsahu stromu automatizace uživatelského rozhraní, které se vztahuje k ovládacím prvkům datová mřížka a tlačítko rozdělení, jsou zobrazeny níže. Vzory ovládacích prvků pro každý element automatizace jsou uvedeny v závorkách.  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Zobrazení stromového řízení|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Strom – zobrazení obsahu|  
|------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------|  
|<ul><li>SplitButton "název" (Invoke, ovládacích prvků ExpandCollapse)</li><li>Tlačítko Další možnosti (vyvolat)<br /><br /> <ul><li>Nabídka</li><li>MenuItem</li><li>…</li></ul></li></ul>|<ul><li>SplitButton "název" (Invoke, ovládacích prvků ExpandCollapse)</li><li>Tlačítko Další možnosti (vyvolat)<br /><br /> <ul><li>Nabídka</li><li>MenuItem</li><li>…</li></ul></li></ul>|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Automation.ControlType.SplitButton>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
