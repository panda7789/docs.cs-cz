---
title: Automatizace uživatelského rozhraní a technologie Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 1b7dbc8dffb15485ec035049d2da7aac6915eb58
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47071193"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>Automatizace uživatelského rozhraní a technologie Microsoft Active Accessibility
> [!NOTE]
>  Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] byl starší řešení pro zpřístupnění aplikace. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] je nový model usnadnění pro [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] má sloužit k řešení potřeb produktů využívajících technologie usnadnění a automatizované testovací nástroje. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nabízí mnoho vylepšení [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
 Toto téma obsahuje hlavní funkce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a vysvětluje, jak tyto funkce se liší od [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>Programovací jazyky  
<[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] je založen na [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] s podporou pro duální rozhraní a proto je programovatelná v jazyce C/C++ [!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)]a skriptovací jazyky. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (včetně knihovnu zprostředkovatele na straně klienta pro standardní ovládací prvky) je zapsána ve spravovaném kódu a automatizace uživatelského rozhraní klientské aplikace jsou nejsnadněji naprogramovat pomocí jazyka C# nebo Visual Basic .NET. Zprostředkovatelé automatizace uživatelského rozhraní, které jsou implementace rozhraní, může být napsán ve spravovaném kódu nebo v jazyce C/C++.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Podpora ve Windows Presentation Foundation  
 Windows Presentation Foundation (WPF) je nový model pro vytváření uživatelského rozhraní. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] prvky neobsahují nativní podporu pro [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], nicméně podporují [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], což zahrnuje podporu pro přemostění [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klientů. Pouze klienti aplikace napsané konkrétně pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] můžete plně využít funkce pro usnadnění přístupu [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], jako Rozsáhlá podpora pro text.  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>Servery a klienty  
 V [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], servery a klienti komunikují přímo, do značné míry prostřednictvím implementace serveru `IAccessible`.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], základní služby je mezi serverem (označované jako zprostředkovatele) a klientem. Základní služba provede volání do rozhraní implementovaná pomocí poskytovatele a poskytuje další služby, jako je například generuje runtime jedinečné identifikátory pro elementy. Klientské aplikace použít k volání funkce knihovny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] služby.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní může poskytnout informace, které [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klienty, a [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servery mohou poskytovat informace pro automatizaci uživatelského rozhraní klientské aplikace. Ale protože [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] nevystavuje co nejvíce informací [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], dva modely nejsou plně kompatibilní.  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>Prvky uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] uvede počet [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvky buď jako `IAccessible` rozhraní nebo jako identifikátor podřízené. Je obtížné pro porovnání dvou `IAccessible` ukazatele k určení, pokud se odkazují na stejný prvek.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], každý prvek je vyjádřena jako <xref:System.Windows.Automation.AutomationElement> objektu. Porovnání se provádí pomocí operátoru rovnosti nebo <xref:System.Windows.Automation.AutomationElement.Equals%2A> metody, které porovnání identifikátory jedinečný runtime prvků.  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>Stromová zobrazení a navigaci  
 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] Prvky na obrazovce uvidíte ve stromové struktuře s plochou jako kořenové, aplikace pro windows jako přímé podřízené objekty a elementů v rámci aplikace jako další následníky.  
  
 V [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], mnoho pohyb mezi elementy automatizace, které se koncovým uživatelům se zveřejňují ve stromové struktuře. Podívat se na všechny prvky k určení, které mají smysl mít klientské aplikace.  
  
 Automatizace uživatelského rozhraní klientských aplikací, najdete v článku [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prostřednictvím filtrované zobrazení. Zobrazení obsahuje pouze elementy, které vás zajímají: ty, které poskytují informace o uživateli nebo povolení interakce. Předdefinovaná zobrazení pouze ovládací prvky a pouze elementy obsahu jsou k dispozici. aplikace můžete navíc definovat vlastní zobrazení. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zjednodušuje popisující [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] na uživatele a pomáhá uživatelům interakci s aplikací.  
  
 Navigace mezi elementy, v [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], je buď spatial (například přechodu na element, který je na levé straně na obrazovce), logický (například přechod na další položku nabídky nebo na další položku v pořadí v rámci dialogového okna), nebo hierarchické (pro například přesun prvním podřízeným objektem kontejneru, nebo z podřízené k nadřazené úloze). Hierarchická navigace je složité fakt, že podřízené prvky nejsou vždy objekty, které implementují `IAccessible`.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvky jsou <xref:System.Windows.Automation.AutomationElement> objekty, které podporují stejné základní funkce. (Z hlediska zprostředkovatele, jsou objekty, které implementují rozhraní zděděná z <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>.) Je především hierarchická navigace: z nadřazené položky na podřízené položky a z jednoho na stejné úrovni na další. (Navigaci mezi na stejné úrovni má logický prvek, jak se dá provést pomocí následujícího pořadí.) Můžete přejít z jakékoli východisko, jakékoli filtrované zobrazení ve stromu, pomocí <xref:System.Windows.Automation.TreeWalker> třídy. Můžete také přejít na konkrétní podřízené prvky nebo potomky pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> a <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; například je velmi snadné k načtení všech elementů v rámci dialogového okna, které podporují vzoru pro zadaný ovládací prvek.  
  
 Navigace v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] odpovídá více než v [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Některé prvky, jako jsou rozevírací seznamy a automaticky otevíraná okna se zobrazí dvakrát v [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] stromu a navigace z nich může mít neočekávané výsledky. Je skutečně možné správně implementovat [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] pro ovládací prvek matrice. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] umožňuje, aby změna nadřazení a přemístění, tak, aby element může být umístěna kdekoli ve stromové struktuře bez ohledu na hierarchii stanovené vlastnictví systému windows.  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>Role a typy ovládacích prvků  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] používá `accRole` vlastnosti (`IAccessible::get_actRole`) k získání popisu prvku role v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], jako je například ROLE_SYSTEM_SLIDER nebo ROLE_SYSTEM_MENUITEM. Role elementu je hlavní vodítko k jeho dostupné funkce. Interakce s ovládacím prvkem je dosaženo pomocí pevné metody `IAccessible::accSelect` a `IAccessible::accDoDefaultAction`. Interakce mezi klientskou aplikací a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] je omezená na co se dá dělat pomocí `IAccessible`.  
  
 Naproti tomu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do značné míry odděluje typ ovládacího prvku (popsaného <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> vlastnost) z jeho očekávaný funkce. Funkce se určuje podle vzorů ovládacích prvků, které podporuje zprostředkovatel prostřednictvím implementace rozhraní specializované. Vzory ovládacích prvků mohou být kombinovány pro úplnou sadu funkcí podporovaných jazykem konkrétní popsat [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementu. Někteří poskytovatelé jsou vyžadovány pro podporu vzoru pro konkrétní ovládací prvek; například zprostředkovatele pro zaškrtávací políčko musí podporovat vzoru ovládacích prvků přepínání. Ostatní zprostředkovatelé jsou vyžadovány pro podporu jeden nebo více sadu vzorů ovládacích prvků; například tlačítko musí podporovat přepínací tlačítko nebo Invoke. Stále jiné podporují žádné vzorů ovládacích prvků, vůbec; například podokno, které nelze přesunout, velikost nebo ukotven nemá žádné vzorů ovládacích prvků.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporuje vlastní ovládací prvky, které jsou určeny <xref:System.Windows.Automation.ControlType.Custom> vlastnost a mohou být popsány <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> vlastnost.  
  
 V následující tabulce jsou uvedeny mapování [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] role [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit typy.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] Role|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Typ ovládacího prvku|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|Tlačítko|  
|ROLE_SYSTEM_CLIENT|Kalendář|  
|ROLE_SYSTEM_CHECKBUTTON|Zaškrtávací políčko|  
|ROLE_SYSTEM_COMBOBOX|Pole se seznamem|  
|ROLE_SYSTEM_CLIENT|Vlastní|  
|ROLE_SYSTEM_LIST|Datová mřížka|  
|ROLE_SYSTEM_LISTITEM|Datová položka|  
|ROLE_SYSTEM_DOCUMENT|Dokument|  
|ROLE_SYSTEM_TEXT|Upravit|  
|ROLE_SYSTEM_GROUPING|Skupina|  
|ROLE_SYSTEM_LIST|Záhlaví|  
|ROLE_SYSTEM_COLUMNHEADER|Položky záhlaví|  
|ROLE_SYSTEM_LINK|Hypertextový odkaz|  
|ROLE_SYSTEM_GRAPHIC|Image|  
|ROLE_SYSTEM_LIST|Seznam|  
|ROLE_SYSTEM_LISTITEM|Položka seznamu|  
|ROLE_SYSTEM_MENUPOPUP|Nabídka|  
|ROLE_SYSTEM_MENUBAR|Panel nabídek|  
|ROLE_SYSTEM_MENUITEM|Položka nabídky|  
|ROLE_SYSTEM_PANE|Podokno|  
|ROLE_SYSTEM_PROGRESSBAR|Indikátor průběhu|  
|ROLE_SYSTEM_RADIOBUTTON|Přepínací tlačítko|  
|ROLE_SYSTEM_SCROLLBAR|Posuvník|  
|ROLE_SYSTEM_SEPARATOR|Oddělovač|  
|ROLE_SYSTEM_SLIDER|Posuvník|  
|ROLE_SYSTEM_SPINBUTTON|Číselník|  
|ROLE_SYSTEM_SPLITBUTTON|Tlačítko rozdělení|  
|ROLE_SYSTEM_STATUSBAR|Stavový řádek|  
|ROLE_SYSTEM_PAGETABLIST|Tabulátor|  
|ROLE_SYSTEM_PAGETAB|Položka tabulátoru|  
|ROLE_SYSTEM_TABLE|Tabulka|  
|ROLE_SYSTEM_STATICTEXT|Text|  
|ROLE_SYSTEM_INDICATOR|Jezdec|  
|ROLE_SYSTEM_TITLEBAR|Záhlaví|  
|ROLE_SYSTEM_TOOLBAR|Panel nástrojů|  
|ROLE_SYSTEM_TOOLTIP|Popisy tlačítek|  
|ROLE_SYSTEM_OUTLINE|Strom|  
|ROLE_SYSTEM_OUTLINEITEM|Položka stromu|  
|ROLE_SYSTEM_WINDOW|Okno|  
  
 Další informace o typech jiného ovládacího prvku, naleznete v tématu [typy ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>   
## <a name="states-and-properties"></a>Stavy a vlastnosti  
 V [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], společnou sadu vlastností a některé vlastnosti podporují prvky (například `accState`) musí popisovat velmi různé věci, v závislosti na roli elementu. Servery musí implementovat všechny metody `IAccessible` , který vrátí vlastnosti, včetně těch, které nejsou relevantní pro element.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] definuje mnoho dalších vlastností, z nichž některé odpovídají stavům v [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Některé jsou společné pro všechny prvky, ale ostatní jsou specifické pro typy ovládacích prvků a vzorů ovládacích prvků. Vlastnosti se rozlišují výhradně podle jedinečné identifikátory a většinu vlastností lze načíst s použitím jedné metody <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> nebo <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Mnoho vlastností jsou také snadno získat z <xref:System.Windows.Automation.AutomationElement.Current%2A> a <xref:System.Windows.Automation.AutomationElement.Cached%2A> přistupující objekty vlastnosti.  
  
 Není nutné implementovat irelevantní vlastnosti zprostředkovatele automatizace uživatelského rozhraní, ale může jednoduše provést vrácení `null` hodnotu pro všechny vlastnosti nepodporuje. Také [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] core service můžete získat některé vlastnosti z okna výchozího zprostředkovatele, a ty se spojit s vlastnostmi explicitně implementované zprostředkovatelem.  
  
 Podporuje mnoho dalších vlastností, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nabízí vyšší výkon tím, že více vlastností, které se mají načíst s jedním mezi procesní volání.  
  
 Následující tabulka ukazuje souvztažnost mezi vlastnostmi v obou modelů.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] přistupující objekt vlastnosti|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ID vlastnosti|Poznámky|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> Nebo <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty` Pokud jsou obě přítomny, má přednost.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Najdete v předchozí tabulce mapování role, které typy ovládacích prvků.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Platí jenom pro typy ovládacích prvků, které podporují ValuePattern nebo RangeValuePattern. Hodnoty prvků RangeValue jsou normalizovány na 0 – 100, aby byla konzistentní s MSAA chování. Hodnota položky pomocí řetězce.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Není podporován v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription` neměl vymazat specifikace v rámci MSAA, což vedlo poskytovatelé uvedení různé druhy údajů v této vlastnosti.|  
|`get_accHelpTopic`|Není podporován v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 Následující tabulka uvádí, které [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti odpovídají [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] stavu konstanty.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] Stav|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnost|Změna stavu aktivace?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Pro zaškrtávací políčko <xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Pro přepínací tlačítko <xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|A|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|A|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded> Nebo <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|A|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern> pro položky nabídky|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True a <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> způsobí, že <xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty> = True|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> a <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern> je podporováno|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|A|  
  
 Následující stavy buď nebyly prováděny většinu [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] řídit servery nebo nemají žádný ekvivalent v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] Stav|Poznámky|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Není k dispozici v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Není k dispozici v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Není k dispozici v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Není široce implementované [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servery|  
|STATE_SYSTEM_MARQUEED|Není široce implementované [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servery|  
|STATE_SYSTEM_SELFVOICING|Není široce implementované [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servery|  
|STATE_SYSTEM_TRAVERSED|Není k dispozici v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Není široce implementované [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servery|  
|STATE_SYSTEM_ALERT_MEDIUM|Není široce implementované [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servery|  
|STATE_SYSTEM_ALERT_LOW|Není široce implementované [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servery|  
|STATE_SYSTEM_FLOATING|Není široce implementované [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servery|  
|STATE_SYSTEM_HOTTRACKED|Není k dispozici v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Není k dispozici v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Úplný seznam [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] viz vlastnost identifikátory [přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>Události  
 Mechanismus události v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], na rozdíl od [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], nevyžaduje Windows směrování událostí (která je úzce vázané pomocí okna úchyty) a nevyžaduje, aby klientská aplikace nastavit zavěšení. Odběry událostí můžete doladíte, ne jenom na konkrétní události, ale konkrétní části stromu. Poskytovatelé lze optimalizovat také při jejich vyvolávání událostí udržovat přehled o jaké události se sleduje pro.  
  
 Je také jednodušší pro klienty načíst prvky, které vyvolávají události, protože ty jsou předány přímo pro událost zpětného volání. Pokud žádost o mezipaměti byl aktivní, pokud se klient odběru události jsou automaticky předem načteného vlastnosti elementu.  
  
 V následující tabulce jsou uvedeny soulad [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] WinEvents a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události.  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] identifikátor události|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty> Změna vlastnosti|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> nebo <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> při změně vlastnosti přidružené posuvníky|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Žádný ekvivalent|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Žádné naprosto stejný; možná <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> nebo <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> Změna vlastnosti|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty> Změna|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> Změna vlastnosti|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty> Změna vlastnosti|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Nepoužito konzistentně v [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Žádné přímo odpovídající událost je definována v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Žádný ekvivalent|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Různé události změny vlastnosti|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType> a <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> změnit|  
|EVENT_SYSTEM_ALERT|Žádný ekvivalent|  
|EVENT_SYSTEM_CAPTUREEND|Žádný ekvivalent|  
|EVENT_SYSTEM_CAPTURESTART|Žádný ekvivalent|  
|EVENT_SYSTEM_CONTEXTHELPEND|Žádný ekvivalent|  
|EVENT_SYSTEM_CONTEXTHELPSTART|Žádný ekvivalent|  
|EVENT_SYSTEM_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT_SYSTEM_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT_SYSTEM_DRAGDROPEND|Žádný ekvivalent|  
|EVENT_SYSTEM_DRAGDROPSTART|Žádný ekvivalent|  
|EVENT_SYSTEM_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_SYSTEM_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> Změna vlastnosti|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> Změna vlastnosti|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> Změna vlastnosti|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> Změna vlastnosti|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> nebo <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> Změna vlastnosti|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> nebo <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> Změna vlastnosti|  
|EVENT_SYSTEM_SOUND|Žádný ekvivalent|  
|EVENT_SYSTEM_SWITCHEND|Žádný ekvivalent ale <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> události signalizuje, že nová aplikace získala fokus|  
|EVENT_SYSTEM_SWITCHSTART|Žádný ekvivalent|  
|Žádný ekvivalent|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty> Změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty> Změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty> Změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> Změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> Změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty> Změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty> Změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty> Změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty> Změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent> Události|  
|Žádný ekvivalent|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## <a name="security"></a>Zabezpečení  
 Některé `IAccessible` přizpůsobení nevyžadují zabalení základní `IAccessible` a prostřednictvím volání do něj. Tato akce nemá vliv na zabezpečení, protože částečně důvěryhodné komponenty by neměl být zprostředkovatele v kódové cestě.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Modelu eliminuje potřebu poskytovatelé volání prostřednictvím jiného poskytovatele kódu. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Základní služba nemá potřebné agregace.  
  
## <a name="see-also"></a>Viz také  
 [Principy automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/index.md)
