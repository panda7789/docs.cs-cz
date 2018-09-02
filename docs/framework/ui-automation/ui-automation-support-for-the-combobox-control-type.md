---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ComboBox
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Combo Box
- UI Automation, Combo Box control type
- ComboBox controls
ms.assetid: bb321126-4770-41da-983a-67b7b89d45dd
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 25d27faeac2c60a50801b817185aa1d5196e506d
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398557"
---
# <a name="ui-automation-support-for-the-combobox-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ComboBox
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 Toto téma obsahuje informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporu pro typ ovládacího prvku pole se seznamem. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], typ ovládacího prvku je představují sadu podmínek, které ovládací prvek musí splnit, aby bylo možné používat <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> vlastnost. Podmínky zahrnují konkrétní pokyny ke [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromová struktura, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hodnoty vlastností, vzorů ovládacích prvků a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události.  
  
 Pole se seznamem je pole se seznamem v kombinaci se statický ovládací prvek nebo prvek pro úpravy, který zobrazuje aktuálně vybrané položky v seznamu část pole se seznamem. Seznam části ovládacího prvku se zobrazí po celou dobu nebo jenom se zobrazí, když uživatel vybere (což je příkazové tlačítko) šipku rozevíracího seznamu vedle ovládacího prvku. Pokud je pole výběru ovládacího prvku pro úpravy, uživatel může zadat informace, které se nenachází v seznamu. v opačném případě uživatel může vybrat pouze položky v seznamu.  
  
 Následující části definují požadovaný [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, vlastnosti, vzorů ovládacích prvků a události pro typ ovládacího prvku pole se seznamem. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Požadavky platí pro všechny ovládací prvky pole se seznamem, zda [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], [!INCLUDE[TLA#tla_win32](../../../includes/tlasharptla-win32-md.md)], nebo [!INCLUDE[TLA#tla_winforms](../../../includes/tlasharptla-winforms-md.md)].  
  
<a name="Required_UI_Automation_Tree_Structure"></a>   
## <a name="required-ui-automation-tree-structure"></a>Požadované uživatelské rozhraní automatizace stromová struktura  
 Následující tabulka popisuje ovládací prvek zobrazení a zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] strom, který se týká – pole se seznamem ovládací prvky a popisuje, co mohou být obsaženy v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury, přečtěte si téma [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md).  
  
|Ovládací prvek zobrazení|Zobrazení obsahu|  
|------------------|------------------|  
|ComboBox<br /><br /> -Upravit (0 nebo 1)<br />-List (1)<br />-Položka seznamu (podřízený seznam; 0, n)<br />-Tlačítko (1)|ComboBox<br /><br /> -Položka list (0, n)|  
  
 Je nezbytné pouze v případě, že lze upravovat pole se seznamem umožní jakémukoli zadání, stejně jako v případě pole se seznamem v dialogového okna Spustit ovládacího prvku pro úpravy v zobrazení pro ovládací prvek pole se seznamem.  
  
<a name="Required_UI_Automation_Properties"></a>   
## <a name="required-ui-automation-properties"></a>Vlastnosti automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, jejichž hodnota nebo definice je obzvláště důležité pro pole se seznamem pole ovládacích prvků. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, viz [vlastnosti automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|V části poznámky.|Hodnota této vlastnosti musí být jedinečný v rámci všech ovládacích prvků v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|V části poznámky.|Nejkrajnější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|V části poznámky.|Nepodporuje. Pokud ohraničující obdélník. Pokud ne každý bod v rámci ohraničující obdélník je po kliknutí a provést specializované přístupů testování přepsat a zadat bod umožňující kliknutí.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ComboBox|Tato hodnota je stejný pro všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektur.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|V části poznámky.|Text nápovědy pro pole se seznamem by měl vysvětlit, proč je se uživateli zobrazí výzva k výběru možnosti v poli se seznamem. Text je podobné informace, které jsou nabízena prostřednictvím popisek. Například "vyberte položku, kterou chcete nastavit rozlišení monitoru".|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|Hodnota TRUE|Pole se seznamem jsou vždy součástí obsahu zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|Hodnota TRUE|Pole se seznamem jsou vždy součástí zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Hodnota TRUE|Pole se seznamem vystavení sady položek z výběru kontejneru. Ovládací prvek pole se seznamem může získat fokus klávesnice, i když při automatizaci uživatelského rozhraní klienta nastaví fokus na pole se seznamem, všechny položky v připojeném podstromu pole se seznamem může získat fokus.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|V části poznámky.|Pole se seznamem mají obvykle statický text popisku, který odkazuje na tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"– pole se seznamem"|Lokalizovaný řetězec odpovídající typ ovládacího prvku pole se seznamem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|V části poznámky.|Ovládací prvek pole se seznamem obvykle anglický název z ovládacího prvku statický text.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>   
## <a name="required-ui-automation-control-patterns"></a>Vzory ovládacích prvků automatizace uživatelského rozhraní vyžaduje  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit vzory vyžaduje to, že všechny ovládací prvky pole se seznamem. Další informace o vzorů ovládacích prvků naleznete v tématu [přehled vzorů ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md).  
  
|– Vzor ovládacích prvků|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Ano|Prvek pole se seznamem musí vždy obsahovat rozevírací tlačítko, aby byla pole se seznamem.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Ano|Zobrazí aktuální výběr v poli se seznamem. Tato podpora se deleguje na pole se seznamem pod pole se seznamem.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závisí|Pokud pole se seznamem má schopnost pořizovat libovolných textových hodnot, vzor hodnota musí být podporovány. Tento model umožňuje programově nastavit řetězec obsah pole se seznamem. Pokud není podporovaná hodnota vzoru, to znamená, že uživatel musí provést výběr ze seznamu položek v rámci podstrom pole se seznamem.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Nikdy|Vzor posuvníku se nikdy podporuje na pole se seznamem přímo. Je podporována, pokud můžete přejít pole se seznamem obsažené v rámci pole se seznamem. Může být pouze podporováni, když pole se seznamem je viditelný na obrazovce.|  
  
<a name="Required_Events"></a>   
## <a name="required-events"></a>Požadované události  
 Následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události potřebné to, že všechny ovládací prvky pole se seznamem. Další informace o událostech najdete v tématu [Přehled událostí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Události|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty> události změny vlastnosti.|Požadováno|Žádné|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty> události změny vlastnosti.|Závisí|Pokud ovládací prvek podporuje vzor hodnota, musí podporovat této události.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Automation.ControlType.ComboBox>  
 [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types-overview.md)  
 [Přehled automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-overview.md)
