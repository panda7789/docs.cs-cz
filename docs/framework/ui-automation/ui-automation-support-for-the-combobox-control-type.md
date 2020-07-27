---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ComboBox
description: Získejte informace o podpoře automatizace uživatelského rozhraní pro typ ovládacího prvku ComboBox. Seznamte se s požadovanou stromovou strukturou, vlastnostmi, vzory ovládacích prvků a událostmi.
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Combo Box
- UI Automation, Combo Box control type
- ComboBox controls
ms.assetid: bb321126-4770-41da-983a-67b7b89d45dd
ms.openlocfilehash: c708de791056969e281ad1bc223e2a2233fa170b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166089"
---
# <a name="ui-automation-support-for-the-combobox-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ComboBox
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma poskytuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podpoře pro typ ovládacího prvku ComboBox. V nástroji [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] je typ ovládacího prvku sada podmínek, které musí ovládací prvek splňovat, aby bylo možné vlastnost použít <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> . Podmínky zahrnují konkrétní pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností, vzory ovládacích prvků a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události.  
  
 Pole se seznamem je pole se seznamem kombinované se statickým ovládacím prvkem nebo ovládacím prvkem pro úpravy, který zobrazuje aktuálně vybranou položku v části seznamu pole se seznamem. Část seznamu ovládacího prvku se zobrazí ve všech časech, nebo se zobrazí pouze v případě, že uživatel vybere šipku rozevíracího seznamu (což je tlačítko push) vedle ovládacího prvku. Pokud je pole výběru ovládacím prvkem pro úpravy, může uživatel zadat informace, které nejsou v seznamu. v opačném případě může uživatel vybrat pouze položky v seznamu.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzory ovládacích prvků a události pro typ ovládacího prvku ComboBox. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Požadavky platí pro všechny ovládací prvky pole se seznamem bez ohledu na to [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)] , zda, Win32 nebo model Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Požadovaná stromová struktura automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, které se vztahují k ovládacím prvkům pole se seznamem, a popisuje, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktuře najdete v tématu [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacích prvků|Zobrazení obsahu|  
|------------------|------------------|  
|ComboBox<br /><br /> -Upravit (0 nebo 1)<br />-List (1)<br />– Položka seznamu (podřízená položka seznamu; 0 až mnoho)<br />-Tlačítko (1)|ComboBox<br /><br /> – Položka seznamu (0 až n)|  
  
 Ovládací prvek pro úpravy v zobrazení ovládacích prvků pole se seznamem je nutný pouze v případě, že pole se seznamem lze upravit tak, aby převzalo jakékoli zadání, jako je případ pole se seznamem v dialogovém okně Spustit.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice je obzvláště relevantní pro ovládací prvky pole se seznamem. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnostech najdete v tématu [Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Majetek|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečná napříč všemi ovládacími prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Vnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Podporováno, pokud je ohraničen obdélník. Pokud není k dispozici žádný bod v ohraničujícím obdélníku a provádíte specializované testování přístupů, přepíšete a získáte bod, který je k dispozici.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ComboBox|Tato hodnota je stejná pro všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Viz poznámky.|Text helpu pro ovládací prvky pole se seznamem by měl vysvětlit, proč se uživateli zobrazí výzva k výběru možnosti z pole se seznamem. Text je podobný informacím prezentovaným pomocí popisu tlačítka. Například "vybrat položku pro nastavení rozlišení displeje".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Ano|Ovládací prvky pole se seznamem jsou vždy zahrnuty v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Ano|Ovládací prvky pole se seznamem jsou vždy zahrnuty v zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Ano|Ovládací prvky pole se seznamem zpřístupňují sadu položek z kontejneru výběru. Ovládací prvek pole se seznamem může obdržet fokus klávesnice, i když klient automatizace uživatelského rozhraní nastaví fokus na pole se seznamem, může se stát, že se všechny položky v podstromu pole se seznamem dostanou fokusem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Ovládací prvky pole se seznamem obvykle mají statický textový popisek, na který odkazuje tato vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"pole se seznamem"|Lokalizovaný řetězec odpovídající typu ovládacího prvku ComboBox.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Ovládací prvek pole se seznamem obvykle získá svůj název z ovládacího prvku statický text.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory ovládacího prvku automatizace uživatelského rozhraní  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vzory ovládacích prvků, které musí být podporovány všemi ovládacími prvky pole se seznamem. Další informace o vzorech ovládacích prvků naleznete v tématu [Přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vzor ovládacího prvku|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Ano|Ovládací prvek pole se seznamem musí vždy obsahovat tlačítko rozevíracího seznamu, aby bylo pole se seznamem.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Ano|Zobrazí aktuální výběr v poli se seznamem. Tato podpora je delegována do pole seznamu pod polem se seznamem.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závislosti|Pokud pole se seznamem umožňuje přebírat libovolné textové hodnoty, musí být podporován vzorec hodnoty. Tento model poskytuje možnost programově nastavit obsah řetězce pole se seznamem. Pokud není vzor hodnoty podporován, znamená to, že uživatel musí provést výběr z položek seznamu v rámci podstromu pole se seznamem.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Nikdy|V poli se seznamem není nikdy podporován vzor posuvníku. Podporuje se v případě, že se může posunout pole seznamu obsažené v poli se seznamem. Může být podporován pouze v případě, že je pole seznamu viditelné na obrazovce.|  
  
<a name="Required_Events"></a>
## <a name="required-events"></a>Požadované události  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události, které musí být podporovány všemi ovládacími prvky pole se seznamem. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událostí|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Povinné|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>událost změny vlastnosti.|Povinné|Žádné|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>událost změny vlastnosti.|Závislosti|Pokud ovládací prvek podporuje vzorec hodnoty, musí podporovat tuto událost.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.ComboBox>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
