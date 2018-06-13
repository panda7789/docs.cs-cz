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
manager: markl
ms.openlocfilehash: be7711fdbe9b2cb45d618e685a6f1ae2a941aa29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399159"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>Automatizace uživatelského rozhraní a technologie Microsoft Active Accessibility
> [!NOTE]
>  Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).  
  
 [!INCLUDE[TLA#tla_aa](../../../includes/tlasharptla-aa-md.md)] byl dřívější řešení pro zpřístupnění aplikací. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] je nový model usnadnění pro [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] a je určený k vyřešení požadovaných produktů využívajících technologie usnadnění a automatizované testování nástroje. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nabízí mnoho vylepšení než [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
 Toto téma obsahuje hlavní funkce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] a vysvětluje, jak tyto funkce liší od [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)].  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>Programovací jazyky  
<[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] je založena na [!INCLUDE[TLA#tla_com](../../../includes/tlasharptla-com-md.md)] s podporou pro duální rozhraní a je proto programovatelný v jazyce C/C++ [!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)]a skriptovací jazyky. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (včetně knihovně zprostředkovatele na straně klienta pro standardní ovládací prvky) je zapsané ve spravovaném kódu a automatizace uživatelského rozhraní klientské aplikace jsou snadno naprogramovaný tak pomocí jazyka C# nebo Visual Basic .NET. Zprostředkovatelé automatizace uživatelského rozhraní, které jsou implementace rozhraní, může být napsán ve spravovaném kódu nebo v jazyce C/C++.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Podpora v systému Windows Presentation Foundation  
 Windows Presentation Foundation (WPF) je nový model pro vytvoření uživatelského rozhraní. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)] prvky neobsahují nativní podpora pro [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]; ale podporují [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], což zahrnuje podporu pro přemostění [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klientů. Pouze klienti, které jsou napsané konkrétně pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] můžete využít všech výhod funkce pro usnadnění přístupu [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)], jako například bohaté podporu pro text.  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>Servery a klienty  
 V [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], servery a klienti komunikují přímo, z velké části prostřednictvím implementace serveru `IAccessible`.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], základní služby je mezi serverem (nazývané zprostředkovatele) a klientem. Základní služby provádí volání na rozhraní implementované poskytovatelů a poskytuje další služby, například generování runtime jedinečné identifikátory pro elementy. Klientské aplikace využít k volání funkce knihovny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] služby.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní můžete poskytují informace, které [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] klienty, a [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] servery mohou poskytovat informace pro automatizaci uživatelského rozhraní klientské aplikace. Ale protože [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] nevystavuje co nejvíce informací [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], dva modely nejsou plně kompatibilní.  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>Prvky uživatelského rozhraní  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] uvede [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementy buď jako `IAccessible` rozhraní nebo jako podřízené identifikátor. Je obtížné porovnat `IAccessible` ukazatele k určení, pokud se použijí pro referenci stejného elementu.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], každý element je reprezentován jako <xref:System.Windows.Automation.AutomationElement> objektu. Porovnání se provádí pomocí operátoru rovnosti nebo <xref:System.Windows.Automation.AutomationElement.Equals%2A> metody, které obě porovnat runtime jedinečné identifikátory elementů.  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>Zobrazení stromu a navigace  
 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] Elementů na obrazovce můžete zobrazit ve stromové struktuře s plochou jako kořenové, aplikace windows jako přímé podřízené objekty a prvky v aplikacích jako další následníky.  
  
 V [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], mnoho elementy automatizace, které jsou důležité pro koncové uživatele jsou viditelné ve stromové struktuře. Klientských aplikací mít podívat se na všechny elementy k určení, které mají význam.  
  
 Automatizace uživatelského rozhraní klienta aplikace najdete [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prostřednictvím filtrované zobrazení. Zobrazení obsahuje pouze elementy, které vás zajímají: ty, které poskytují informace o uživateli nebo Povolit interakci. Předdefinovaná zobrazení pouze ovládací prvky a pouze obsahu elementy jsou k dispozici. Kromě toho aplikace můžete definovat vlastní zobrazení. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zjednodušuje popisující [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] na uživatele a pomáhá uživatelům interakci s aplikací.  
  
 Navigace mezi elementy, v [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], je buď prostorových (například přesun do elementu, který je na levé straně na obrazovce), logické (například přesun na další položku nabídky nebo na další položku v pořadí v rámci dialogového okna) nebo hierarchické (pro například přesun prvním podřízeným objektem v kontejneru nebo z podřízených ke své nadřazené úloze). Hierarchická navigační ztěžuje fakt, že podřízené elementy nejsou vždy objekty, které implementují `IAccessible`.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], všechny [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvky jsou <xref:System.Windows.Automation.AutomationElement> objekty, které podporují stejné základní funkce. (Z hlediska poskytovatele, jsou objekty, které implementují rozhraní zděděno z <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>.) Navigace není především hierarchické: z nadřazené položky podřízených objektů a jeden na stejné úrovni jako na další. (Přecházení mezi členy na stejné úrovni má logický prvek, jak ho může podle pořadí.) Můžete přejít z jakékoli výchozího bodu, pomocí všechny filtrované zobrazení stromu s použitím <xref:System.Windows.Automation.TreeWalker> třídy. Můžete také přejít na konkrétní podřízené objekty nebo následníky pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> a <xref:System.Windows.Automation.AutomationElement.FindAll%2A>, například je velmi snadné načíst všechny elementy v dialogové okno, které podporují vzor zadaný ovládacích prvků.  
  
 Navigace ve [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] více konzistentní než v [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Některé prvky, jako jsou například rozevíracího seznamu a automaticky otevíraná okna zobrazí dvakrát v [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] stromu a navigace z nich může mít neočekávané výsledky. Ve skutečnosti nelze správně implementovat [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] ovládacího prvku matrice. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Umožňuje reparenting a přemístění, aby element můžete umístit kdekoli v stromu navzdory hierarchii způsobené vlastnictví systému windows.  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>Role a typy ovládacích prvků  
 [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] používá `accRole` vlastnost (`IAccessible::get_actRole`) k získání popisu elementu role v [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)], jako jsou například ROLE_SYSTEM_SLIDER nebo ROLE_SYSTEM_MENUITEM. Roli elementu je hlavní potvrzením do svých funkcí, k dispozici. Interakce s ovládacím prvkem je dosaženo pomocí pevné metody `IAccessible::accSelect` a `IAccessible::accDoDefaultAction`. Interakce mezi klientská aplikace a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] je omezený na co lze provést prostřednictvím `IAccessible`.  
  
 Naproti tomu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] z velké části oddělí typ elementu ovládacího prvku (popsaného <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> vlastnost) ze svých funkcí, očekávané. Funkce je určen podle vzorů ovládacích prvků, které podporované poskytovatelem prostřednictvím jeho implementace specializované rozhraní. Vzory ovládacích prvků mohou být kombinovány k popisu úplnou sadu funkcí podporovaných konkrétní [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] elementu. Někteří poskytovatelé jsou potřebné k podpoře určitého ovládacího prvku vzor; Zprostředkovatel pro zaškrtávací políčko například musí podporovat vzoru ovládacích prvků přepínání. Jiní poskytovatelé jsou potřebné k podpoře jeden nebo více sadu vzorů ovládacích prvků; například tlačítko musí podporovat přepnutí nebo Invoke. Ještě jiné podporují žádné vzory ovládacích prvků, vůbec; například podokno, které se nedá přesunout, po změně velikosti nebo ukotven nemá žádné vzory ovládacích prvků.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporuje vlastní ovládací prvky, které jsou určeny <xref:System.Windows.Automation.ControlType.Custom> vlastnost a mohou být popsány <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> vlastnost.  
  
 V následující tabulce jsou uvedeny mapování [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] role [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] řídit typy.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] Role|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] – Typ ovládacího prvku|  
|----------------------------------------------------------------------|----------------------------------------------------------------------------------------|  
|ROLE_SYSTEM_PUSHBUTTON|Tlačítko|  
|ROLE_SYSTEM_CLIENT|Kalendář|  
|ROLE_SYSTEM_CHECKBUTTON|Zaškrtávací políčko|  
|ROLE_SYSTEM_COMBOBOX|Pole se seznamem|  
|ROLE_SYSTEM_CLIENT|Vlastní|  
|ROLE_SYSTEM_LIST|Datové mřížky|  
|ROLE_SYSTEM_LISTITEM|Datová položka|  
|ROLE_SYSTEM_DOCUMENT|Dokument|  
|ROLE_SYSTEM_TEXT|Upravit|  
|ROLE_SYSTEM_GROUPING|Skupina|  
|ROLE_SYSTEM_LIST|Záhlaví|  
|ROLE_SYSTEM_COLUMNHEADER|Položky hlavičky|  
|ROLE_SYSTEM_LINK|Hypertextový odkaz|  
|ROLE_SYSTEM_GRAPHIC|Image|  
|ROLE_SYSTEM_LIST|Seznam|  
|ROLE_SYSTEM_LISTITEM|položky seznamu|  
|ROLE_SYSTEM_MENUPOPUP|Nabídka|  
|ROLE_SYSTEM_MENUBAR|Panel nabídek|  
|ROLE_SYSTEM_MENUITEM|Položky nabídky|  
|ROLE_SYSTEM_PANE|Podokno|  
|ROLE_SYSTEM_PROGRESSBAR|Indikátor průběhu|  
|ROLE_SYSTEM_RADIOBUTTON|Přepínač|  
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
  
 Další informace o typech různých řízení, najdete v části [typy ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>   
## <a name="states-and-properties"></a>Stavy a vlastnosti  
 V [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], elementy podporují společnou sadu vlastností a některé vlastnosti (například `accState`) musí popisovat, velmi různých věcí, v závislosti na roli elementu. Servery musí implementovat všechny metody `IAccessible` , které vracejí vlastnost, i ty, které nejsou relevantní pro element.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Definuje mnohem více vlastností, z nichž některé odpovídají stavů v [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Některé jsou společné pro všechny elementy, ale jiné jsou specifické pro typy ovládacích prvků a vzory ovládacích prvků. Vlastnosti jsou rozlišené jedinečné identifikátory a většinu vlastností můžete načíst pomocí jedné metody <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> nebo <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Mnoho vlastností se taky dá snadno načíst, z <xref:System.Windows.Automation.AutomationElement.Current%2A> a <xref:System.Windows.Automation.AutomationElement.Cached%2A> přístupové objekty vlastnosti.  
  
 Zprostředkovatel automatizace uživatelského rozhraní není nutné implementovat důležité vlastnosti, ale můžete jednoduše vrátit `null` hodnotu pro všechny vlastnosti nejsou podporovány. Navíc [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] základní služby můžete získat od výchozího zprostředkovatele okno některé vlastnosti, a ty se spojit s vlastnosti explicitně implementované zprostředkovatelem.  
  
 Podporuje mnoho další vlastnosti, [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] zdroje vyšší výkon tím, že více vlastností, které mají být načteny pomocí volání napříč jedním procesem.  
  
 V následující tabulce jsou uvedeny propojeni vlastnosti v obou modelů.  
  
|[!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] přistupující objekt vlastnosti|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Vlastnost ID|Poznámky|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> Nebo <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty` Pokud jsou obě přítomny, má přednost před.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Najdete v předchozí tabulce pro mapování rolí na typy ovládacích prvků.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Tato možnost je platná pouze pro typy ovládacích prvků, které podporují ValuePattern nebo RangeValuePattern. RangeValue hodnoty jsou normalizovány na 0-100, aby byla konzistentní se MSAA chování. Hodnota položky pomocí řetězce.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Není podporována v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription` neměl vymazat specifikace v rámci MSAA, čímž vznikl ve zprostředkovatelích umístění různých údaje v této vlastnosti.|  
|`get_accHelpTopic`|Není podporována v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
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
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> A <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern> je podporováno|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|A|  
  
 Následující stavy buď nebyly implementované většinu [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] řízení serverů nebo nemají žádný ekvivalent v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
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
  
 Úplný seznam [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] najdete v části identifikátory. vlastnost [přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>Události  
 Mechanismus událostí v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], na rozdíl od, že v [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)], není závislý na systému Windows událost směrování (která úzce souvisí se pomocí okna obslužné rutiny) a nevyžaduje klientská aplikace nastavit háky. Odběry událostí můžete upřesnění, ne jenom na konkrétní události, ale na konkrétní části stromu. Zprostředkovatelé můžete i upřesnit jejich vyvolávání událostí udržovat přehled o událostech, které jsou právě naslouchali pro.  
  
 Je také usnadňuje klientům načítat prvky, které vyvolávání událostí, jako jsou tyto předaný přímo na událost zpětného volání. Pokud se žádost o mezipaměti byl aktivní, pokud se klient odběru události jsou automaticky prefetched vlastnosti elementu.  
  
 V následující tabulce jsou uvedeny soulad [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)] WinEvents a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] události.  
  
|WinEvent.|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] identifikátor události|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty> Změna vlastnosti|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> nebo <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> změnu vlastnosti na přidružené posuvníky|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Žádný ekvivalent|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Ekvivalent přesný; možná <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> nebo <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> změnu vlastnosti|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty> změnit|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> Změna vlastnosti|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty> Změna vlastnosti|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Není konzistentní se používá v [!INCLUDE[TLA2#tla_aa](../../../includes/tla2sharptla-aa-md.md)]. Žádné přímo odpovídající událost je definována v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].|  
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
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> nebo <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> změnu vlastnosti|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty> nebo <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> změnu vlastnosti|  
|EVENT_SYSTEM_SOUND|Žádný ekvivalent|  
|EVENT_SYSTEM_SWITCHEND|Žádný ekvivalent, ale <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> událost signalizuje, že novou aplikaci přijal fokusu|  
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
 Některé `IAccessible` scénáře přizpůsobení vyžadují zabalení na základní `IAccessible` a prostřednictvím volání do ní. Tato akce nemá vliv na zabezpečení, protože částečně důvěryhodné součást by neměl být prostředník v cestě kódu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Model eliminuje potřebu poskytovatelům provolat ke jiný kód, zprostředkovatele. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Základní služby neobsahuje všechny potřebné agregace.  
  
## <a name="see-also"></a>Viz také  
 [Principy automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/index.md)
