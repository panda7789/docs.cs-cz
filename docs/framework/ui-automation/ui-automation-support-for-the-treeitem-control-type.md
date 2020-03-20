---
title: Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TreeItem
ms.date: 03/30/2017
helpviewer_keywords:
- control types, Tree Item
- Tree Item control type
- UI Automation, Tree Item control type
ms.assetid: 229f341a-477f-434e-b877-4db9973068eb
ms.openlocfilehash: 4dc55b4baaf42d22f0c7db1301a78672e739e757
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179424"
---
# <a name="ui-automation-support-for-the-treeitem-control-type"></a>Podpora automatizace uživatelského rozhraní pro typ ovládacího prvku TreeItem
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Toto téma [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] obsahuje informace o podpoře pro typ ovládacího prvku TreeItem. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]programu je typ ovládacího prvku sada podmínek, které <xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> musí ovládací prvek splňovat, aby bylo možné použít vlastnost. Podmínky zahrnují zvláštní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pokyny pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, hodnoty vlastností a vzory ovládacích prvku.  
  
 Typ ovládacího prvku TreeItem představuje uzel v kontejneru stromu. Každý uzel může obsahovat další uzly, nazývané podřízené uzly. Nadřazené uzly nebo uzly, které obsahují podřízené uzly, lze zobrazit jako rozbalené nebo sbalené.  
  
 Následující části definují požadovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromovou strukturu, vlastnosti, vzorky ovládacího prvku a události pro typ ovládacího prvku TreeItem. Požadavky [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] platí pro všechny ovládací [!INCLUDE[TLA#tla_winclient](../../../includes/tlasharptla-winclient-md.md)]prvky položky stromu, ať už , Win32 nebo Windows Forms.  
  
<a name="Required_UI_Automation_Tree_Structure"></a>
## <a name="required-ui-automation-tree-structure"></a>Požadovaná struktura stromu automatizace uživatelského rozhraní  
 Následující tabulka znázorňuje zobrazení ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a zobrazení obsahu stromu, který se týkající se ovládacích prvků položky stromu, a popisuje, co může být obsaženo v každém zobrazení. Další informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu naleznete v [tématu Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md).  
  
|Zobrazení ovládacího prvku|Zobrazení obsahu|  
|------------------|------------------|  
|Treeitem<br /><br /> - CheckBox (0 nebo 1)<br />- Obrázek (0 nebo 1)<br />- Tlačítko (0 nebo 1)<br />- TreeItem (0 nebo více)|Treeitem<br /><br /> - TreeItem (0 nebo více)|  
  
 Ovládací prvky položky stromu mohou mít v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zobrazení obsahu stromu nulové nebo více podřízených položek stromu. Pokud ovládací prvek položky stromu má funkce nad rámec co je vystaveno v ovládacích vzorcích uvedených níže, pak ovládací prvek by měl být založen na typu ovládacího prvku položky dat.  
  
 Sbalené položky stromu se v ovládacím zobrazení nebo zobrazení obsahu nezobrazí, dokud nebudou rozbaleny a viditelné (nebo mohou být posunuty do zobrazení).  
  
 Zobrazení ovládacího prvku může obsahovat další podrobnosti ovládacího prvku, včetně přidruženého obrázku nebo tlačítka. Položka v zobrazení osnovy může například obsahovat obrázek a také tlačítko pro rozbalení nebo sbalení osnovy. Tyto objekty podrobností se v zobrazení obsahu nezobrazí, protože informace jsou již reprezentovány nadřazenou položkou stromu. Stromové položky, které jsou posunuty mimo obrazovku, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] se zobrazí v <xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> zobrazení ovládacího prvku i obsahu stromu a měly by mít nastavenou hodnotu true.  
  
<a name="Required_UI_Automation_Properties"></a>
## <a name="required-ui-automation-properties"></a>Požadované vlastnosti automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vlastnosti, jejichž hodnota nebo definice jsou obzvláště důležité pro ovládací prvky seznamu. Další informace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] o vlastnostech naleznete v [tématu Vlastnosti automatizace uživatelského rozhraní pro klienty](ui-automation-properties-for-clients.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Hodnota|Poznámky|  
|------------------------------------------------------------------------------------|-----------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationIdProperty>|Viz poznámky.|Hodnota této vlastnosti musí být jedinečný napříč všechny ovládací prvky v aplikaci.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>|Viz poznámky.|Nejvzdálenější obdélník, který obsahuje celý ovládací prvek.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ClickablePointProperty>|Viz poznámky.|Tato vlastnost musí vrátit umístění položky, která způsobí, že položka změnit stav výběru nebo se zaměřit.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ControlTypeProperty>|Treeitem|Tato hodnota je stejná pro všechny architektury ui.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsContentElementProperty>|True|Ovládací prvek seznamu je vždy součástí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zobrazení obsahu stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsControlElementProperty>|True|Ovládací prvek seznamu je vždy součástí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ovládacího zobrazení stromu.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>|Viz poznámky.|Tato vlastnost je nastavena tak, aby označovala, kdy je ovládací prvek položky stromu posunut mimo obrazovku.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsKeyboardFocusableProperty>|Viz poznámky.|Pokud ovládací prvek může přijímat fokus klávesnice, musí podporovat tuto vlastnost.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemTypeProperty>|Viz poznámky.|Pokud ovládací prvek položky stromu používá vizuální ikonu k označení, že se jedná o určitý typ objektu, musí být tato vlastnost podporována a označovat, co je objekt.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LabeledByProperty>|`Null`|Ovládací prvky položky stromu jsou samoozytní.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.LocalizedControlTypeProperty>|"položka stromu"|Lokalizovaný řetězec odpovídající typu ovládacího prvku TreeItem.|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>|Viz poznámky.|Tato vlastnost zpřístupňuje text zobrazený pro každý ovládací prvek položky stromu.|  
  
<a name="Required_UI_Automation_Control_Patterns"></a>
## <a name="required-ui-automation-control-patterns"></a>Požadované vzory řízení automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vzory ovládacích prvků, které musí být podporovány ovládacími prvky seznamu. Další informace o vzorcích ovládacího prvku naleznete v [tématu Přehled řídicích vzorů automatizace uživatelského rozhraní](ui-automation-control-patterns-overview.md).  
  
|Vlastnost Vzorek/vzorek ovládacího prvku|Podpora/hodnota|Poznámky|  
|---------------------------------------|--------------------|-----------|  
|<xref:System.Windows.Automation.Provider.IInvokeProvider>|Závisí|Implementujte tento vzor ovládacího prvku, pokud položka stromu má samostatný příkaz, který lze žalovat.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider>|Ano|Všechny položky stromu lze rozbalit nebo sbalit.|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|Rozbalené, sbalené nebo listové uzla|Stromové položky budou listové uzly, pokud nejsou rozbaleny nebo sbaleny.|  
|<xref:System.Windows.Automation.Provider.IScrollItemProvider>|Závisí|Implementujte tento vzor ovládacího prvku, pokud kontejner stromu podporuje vzorek ovládacího prvku Posouvání.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider>|Závisí|Implementujte tento vzor ovládacího prvku, pokud je možné mít aktivní výběr, který je udržován, když se uživatel vrátí do kontejneru stromu.|  
|<xref:System.Windows.Automation.Provider.ISelectionItemProvider.SelectionContainer%2A>|Ano|Tato vlastnost bude vystavit stejný kontejner pro všechny položky v rámci kontejneru.|  
|<xref:System.Windows.Automation.Provider.IToggleProvider>|Závisí|Tento vzor ovládacího prvku implementujte, pokud má položka stromu přidružené zaškrtávací políčko.|  
  
<a name="Required_UI_Automation_Events"></a>
## <a name="required-ui-automation-events"></a>Požadované události automatizace uživatelského rozhraní  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny události, které musí být podporovány všemi ovládacími prvky položky stromu. Další informace o událostech naleznete v [tématu Přehled událostí automatizace uživatelského rozhraní](ui-automation-events-overview.md).  
  
|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Událost|Podpora|Poznámky|  
|---------------------------------------------------------------------------------|-------------|-----------|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.AutomationFocusChangedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.BoundingRectangleProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsEnabledProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.IsOffscreenProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.ItemStatusProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.NameProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.AutomationElementIdentifiers.StructureChangedEvent>|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.ExpandCollapsePatternIdentifiers.ExpandCollapseStateProperty>událost změněná vlastnostmi.|Požaduje se|Žádný|  
|<xref:System.Windows.Automation.InvokePatternIdentifiers.InvokedEvent>|Závisí|Žádný|  
|<xref:System.Windows.Automation.MultipleViewPatternIdentifiers.CurrentViewProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementAddedToSelectionEvent>|Závisí|Žádný|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementRemovedFromSelectionEvent>|Závisí|Žádný|  
|<xref:System.Windows.Automation.SelectionItemPatternIdentifiers.ElementSelectedEvent>|Závisí|Žádný|  
|<xref:System.Windows.Automation.TogglePatternIdentifiers.ToggleStateProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
|<xref:System.Windows.Automation.ValuePatternIdentifiers.ValueProperty>událost změněná vlastnostmi.|Závisí|Žádný|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Automation.ControlType.TreeItem>
- [Přehled typů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-types-overview.md)
- [Přehled automatizace uživatelského rozhraní](ui-automation-overview.md)
