---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ComboBox
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Combo Box
- UI Automation, Combo Box control type
- ComboBox controls
ms.assetid: bb321126-4770-41da-983a-67b7b89d45dd
ms.openlocfilehash: 2b1629adcc9e23294daa0512070089cc72ab5810
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179784"
---
# <a name="ui-automation-support-for-the-combobox-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku ComboBox
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahuje informace o podpoře pro typ ovládacího prvku ComboBox. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programu je typ ovládacího prvku sada podmínek, které <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> musí ovládací prvek splňovat, aby bylo možné použít vlastnost. Podmínky zahrnují konkrétní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, hodnoty [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastností, vzory ovládacího prvku a události.  
  
 Pole se seznamem je seznam kombinovaný se statickým ovládacím prvkem nebo ovládacím prvkem pro úpravy, který zobrazuje aktuálně vybranou položku v části seznamu pole se seznamem. Část seznamu ovládacího prvku se zobrazí vždy nebo se zobrazí pouze v případě, že uživatel vybere šipku rozevíracího seznamu (což je tlačítko) vedle ovládacího prvku. Pokud je výběrové pole ovládacíprvek úprav, může uživatel zadat informace, které nejsou v seznamu; v opačném případě může uživatel vybrat pouze položky v seznamu.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzorky ovládacího prvku a události pro typ ovládacího prvku ComboBox. Požadavky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] platí pro všechny ovládací prvky pole se seznamem, ať už [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)], Win32 nebo Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Požadovaná struktura stromu automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a zobrazení obsahu stromu, který se přilne k ovládacím prvkům pole se seznamem, a popisuje, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu naleznete v [tématu Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|ComboBox<br /><br /> - Upravit (0 nebo 1)<br />- Seznam (1)<br />- Položka seznamu (podřízená položka seznamu; 0 až mnoho)<br />- Tlačítko (1)|ComboBox<br /><br /> - Položka seznamu (0 až mnoho)|  
  
 Ovládací prvek úpravy v ovládacím zobrazení pole se seznamem je nutný pouze v případě, že pole se seznamem lze upravit tak, aby bylo možné převzít jakýkoli vstup, jako je tomu v případě pole se seznamem v dialogovém okně Spustit.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vlastnosti, jejichž hodnota nebo definice je zvláště důležité pro ovládací prvky pole se seznamem. Další informace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o vlastnostech naleznete v [tématu Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečný napříč všechny ovládací prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Nejvzdálenější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Podporováno, pokud je ohraničující obdélník. Pokud není možné kliknout na každý bod v ohraničovacím obdélníku a provedete specializované testování přístupů, přepište a poskytněte bod, na který lze kliknout.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|ComboBox|Tato hodnota je stejná pro všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] architektury.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.HelpTextProperty>|Viz poznámky.|Text nápovědy pro ovládací prvky pole se seznamem by měl vysvětlit, proč je uživatel vyzván k výběru možnosti z pole se seznamem. Text je podobný informacím prezentovaným prostřednictvím popisku. Například "Vyberte položku pro nastavení rozlišení zobrazení monitoru."|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Ovládací prvky pole se seznamem jsou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vždy zahrnuty v zobrazení obsahu stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Ovládací prvky pole se seznamem jsou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vždy zahrnuty v ovládacím zobrazení stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|True|Ovládací prvky pole se seznamem zveřejňují sadu položek z kontejneru výběru. Ovládací prvek pole se seznamem může přijímat fokus klávesnice, i když když klient automatizace uživatelského rozhraní nastaví fokus na pole se seznamem, všechny položky v podstromu se seznamem může získat fokus.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|Viz poznámky.|Ovládací prvky pole se seznamem mají obvykle statický textový popisek, na který tato vlastnost odkazuje.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"pole se seznamem"|Lokalizovaný řetězec odpovídající typu ovládacího prvku ComboBox.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Ovládací prvek pole se seznamem obvykle získá jeho název z ovládacího prvku statického textu.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory řízení automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vzory ovládacích prvků, které musí být podporovány všemi ovládacími prvky pole se seznamem. Další informace o vzorcích ovládacího prvku naleznete v [tématu Přehled řídicích vzorů automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vzorek ovládacího prvku|Podpora|Poznámky|  
|---------------------|-------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Ano|Ovládací prvek pole se seznamem musí vždy obsahovat rozbalovací tlačítko, aby byl pole se seznamem.|  
|<xref:System.Windows.Automation.Provider.ISelectionProvider>|Ano|Zobrazí aktuální výběr v poli se seznamem. Tato podpora je delegována do seznamu pod polem se seznamem.|  
|<xref:System.Windows.Automation.Provider.IValueProvider>|Závisí|Pokud pole se seznamem má schopnost přijmout libovolné textové hodnoty, musí být podporován vzor Hodnota. Tento vzor poskytuje možnost programově nastavit obsah řetězce pole se seznamem. Pokud value vzor není podporován, to znamená, že uživatel musí provést výběr ze seznamu položek v rámci podstromu pole se seznamem.|  
|<xref:System.Windows.Automation.Provider.IScrollProvider>|Never (Nikdy)|Scroll vzor není nikdy podporována na pole se seznamem přímo. Je podporována, pokud se může posouvat seznam obsažený v poli se seznamem. Může být podporovánpouze v případě, že je seznam viditelný na obrazovce.|  
  
<a name="Required_Events"></a>
## <a name="required-events"></a>Požadované události  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny události, které musí být podporovány všemi ovládacími prvky pole se seznamem. Další informace o událostech naleznete v [tématu Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událost|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>událost změněná vlastnostmi.|Závisí|Pokud ovládací prvek podporuje Value vzor, musí podporovat tuto událost.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.ComboBox>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
