---
title: Automatizace uživatelského rozhraní a technologie Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: 9a84c344ffabdaaa9d0aed68b05b7a4449776789
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179984"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>Automatizace uživatelského rozhraní a technologie Microsoft Active Accessibility
> [!NOTE]
> Tato dokumentace je určena pro vývojáře rozhraní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] .NET Framework, kteří chtějí používat spravované třídy definované v oboru <xref:System.Windows.Automation> názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]rozhraní [WINDOWS Automation API: Automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).  
  
 Microsoft Active Accessibility bylo dřívější řešení pro zpřístupnění aplikací. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]je nový model usnadnění pro systém Microsoft Windows a je určen k řešení potřeb produktů asistenčních technologií a automatizovaných testovacích nástrojů. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nabízí mnoho vylepšení oproti aktivní přístupnosti.  
  
 Toto téma obsahuje [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] hlavní rysy a vysvětluje, jak se tyto funkce liší od funkce Active Accessibility.  
  
<a name="Programming_Languages_compare"></a>
## <a name="programming-languages"></a>Programovací jazyky  
<Active Accessibility je založen na modelu COM (Com) s podporou duálních rozhraní, a je proto programovatelný v jazycích C/C++, Microsoft Visual Basic 6.0 a skriptování. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)](včetně knihovny zprostředkovatelů na straně klienta pro standardní ovládací prvky) je zapsán ve spravovaném kódu a klientské aplikace Automatizace uživatelského rozhraní jsou nejsnadněji naprogramovány pomocí jazyka C# nebo Visual Basic .NET. Zprostředkovatelé automatizace uživatelského rozhraní, což jsou implementace rozhraní, mohou být zapsáni ve spravovaném kódu nebo v jazyce C/C++.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>
## <a name="support-in-windows-presentation-foundation"></a>Podpora v nadaci Windows Presentation Foundation  
 Windows Presentation Foundation (WPF) je nový model pro vytváření uživatelských rozhraní. WPF prvky neobsahují nativní podporu pro aktivní usnadnění přístupu; podporují však [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], což zahrnuje překlenovací podporu pro klienty Active Accessibility. Pouze klienti napsaní speciálně pro [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mohou plně využívat funkce usnadnění WPF, jako je například bohatá podpora textu.  
  
<a name="Servers_and_Clients_compare"></a>
## <a name="servers-and-clients"></a>Servery a klienti  
 V aplikaci Active Accessibility komunikují servery a `IAccessible`klienti přímo, převážně prostřednictvím implementace aplikace .  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], základní služba leží mezi serverem (nazývá zprostředkovatel) a klientem. Základní služba provádí volání rozhraní implementovaných zprostředkovateli a poskytuje další služby, jako je generování jedinečných identifikátorů modulu runtime pro prvky. Klientské aplikace používají funkce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] knihovny k volání služby.  
  
 Poskytovatelé automatizace uživatelského rozhraní mohou poskytovat informace klientům Active Accessibility a servery Active Accessibility mohou poskytovat informace klientským aplikacím Automatizace uživatelského rozhraní. Protože však funkce Active Accessibility nezveřejňuje tolik informací jako [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], nejsou oba modely plně kompatibilní.  
  
<a name="UI_Elements_compare"></a>
## <a name="ui-elements"></a>Prvky uživatelského rozhraní  
 Aktivní usnadnění [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] představuje prvky jako `IAccessible` rozhraní nebo jako podřízený identifikátor. Je obtížné porovnat `IAccessible` dva ukazatele k určení, pokud odkazují na stejný prvek.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]aplikaci je každý <xref:System.Windows.Automation.AutomationElement> prvek reprezentován jako objekt. Porovnání se provádí pomocí operátoru <xref:System.Windows.Automation.AutomationElement.Equals%2A> rovnosti nebo metody, které porovnávají jedinečné identifikátory runtime prvků.  
  
<a name="Tree_Views_and_Navigation_compare"></a>
## <a name="tree-views-and-navigation"></a>Stromová zobrazení a navigace  
 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] Prvky na obrazovce lze zobrazit jako stromovou strukturu s plochou jako kořen, okna aplikace jako okamžité podřízené a prvky v rámci aplikací jako další potomci.  
  
 V aktivní usnadnění jsou ve stromu vystaveny mnoho prvků automatizace, které jsou pro koncové uživatele irelevantní. Klientské aplikace musí podívat na všechny prvky k určení, které jsou smysluplné.  
  
 Klientské aplikace automatizace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] uživatelského rozhraní vidí prostřednictvím filtrované zobrazení. Zobrazení obsahuje pouze prvky zájmu: ty, které poskytují informace uživateli nebo umožňují interakci. Předdefinované zobrazení pouze ovládacíprvky a pouze prvky obsahu jsou k dispozici; kromě toho mohou aplikace definovat vlastní zobrazení. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zjednodušuje úlohu popisu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] uživatele a pomáhá uživateli komunikovat s aplikací.  
  
 Navigace mezi prvky v aktivní přístupnosti je buď prostorová (například přesunutí na prvek, který leží vlevo na obrazovce), logická (například přesunutí na další položku nabídky nebo další položka v pořadí polí v dialogovém okně) nebo hierarchická ( například přesunutí prvního podřízeného dítěte v kontejneru nebo z podřízeného dítěte do nadřazeného dítěte). Hierarchické navigace je komplikována skutečností, že `IAccessible`podřízené prvky nejsou vždy objekty, které implementují .  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]aplikace [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] jsou <xref:System.Windows.Automation.AutomationElement> všechny prvky objekty, které podporují stejné základní funkce. (Z hlediska zprostředkovatele jsou objekty, které implementují <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>rozhraní zděděné z .) Navigace je převážně hierarchická: od rodičů k dětem a od jednoho sourozence k druhému. (Navigace mezi sourozenci má logický prvek, protože může následovat pořadí polí.) Pomocí třídy můžete přejít z libovolného počátečního bodu pomocí <xref:System.Windows.Automation.TreeWalker> libovolného filtrovaného zobrazení stromu. Můžete také přejít na konkrétní podřízené nebo potomky pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> a <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; například je velmi snadné načíst všechny prvky v dialogovém okně, které podporují zadaný vzor ovládacího prvku.  
  
 Navigace [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v programu je konzistentnější než v programu Aktivní přístupnost. Některé prvky, například rozevírací seznamy a automaticky otevíraná okna, se ve stromu Aktivní usnadnění zobrazí dvakrát a navigace z nich může mít neočekávané výsledky. Je ve skutečnosti nemožné správně implementovat aktivní usnadnění pro ovládací prvek výztuže. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umožňuje reparenting a přemístění, tak, aby prvek může být umístěn kdekoli ve stromu i přes hierarchii vynucenou vlastnictví majekcí.  
  
<a name="Roles_and_Control_Types"></a>
## <a name="roles-and-control-types"></a>Role a typy ovládacích prvku  
 Aktivní přístupnost `accRole` používá`IAccessible::get_actRole`vlastnost ( ) k načtení popisu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]role prvku v oblasti , například ROLE_SYSTEM_SLIDER nebo ROLE_SYSTEM_MENUITEM. Role prvku je hlavní vodítko k jeho dostupné funkce. Interakce s ovládacím prvkem je dosaženo `IAccessible::accSelect` `IAccessible::accDoDefaultAction`pomocí pevných metod, jako jsou například a . Interakce mezi klientskou aplikací [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] a klientskou aplikací `IAccessible`je omezena na to, co lze provést prostřednictvím aplikace .  
  
 Naproti tomu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] do značné míry odděluje typ ovládacího <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> prvku (popsaný vlastností) od jeho očekávané funkce. Funkce je určena vzory ovládacích prostředků, které jsou podporovány zprostředkovatelem prostřednictvím jeho implementace specializovaných rozhraní. Vzory ovládacího prvku lze kombinovat k popisu úplné sady [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] funkcí podporovaných určitým prvkem. Někteří zprostředkovatelé jsou povinni podporovat konkrétní vzor ovládacího prvku; Například zprostředkovatel pro zaškrtávací políčko musí podporovat přepínací ovládací prvek. Ostatní zprostředkovatelé jsou povinni podporovat jeden nebo více sadu vzorů ovládacího prvku; například tlačítko musí podporovat buď Přepnout nebo Vyvolat. Ještě jiní podporují žádné kontrolní vzory vůbec; například podokno, které nelze přesunout, velikost nebo ukotvení, nemá žádné vzorky ovládacího prvku.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]podporuje vlastní ovládací prvky, <xref:System.Windows.Automation.ControlType.Custom> které jsou identifikovány <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> vlastností a mohou být popsány vlastností.  
  
 V následující tabulce je zobrazeno [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] mapování rolí aktivní usnadnění na typy ovládacích prvku.  
  
|Role aktivní přístupnosti|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]typ ovládacího prvku|  
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
|ROLE_SYSTEM_LIST|Hlavička|  
|ROLE_SYSTEM_COLUMNHEADER|Položka záhlaví|  
|ROLE_SYSTEM_LINK|Hypertextový odkaz|  
|ROLE_SYSTEM_GRAPHIC|Image|  
|ROLE_SYSTEM_LIST|Seznam|  
|ROLE_SYSTEM_LISTITEM|Položka seznamu|  
|ROLE_SYSTEM_MENUPOPUP|Nabídka|  
|ROLE_SYSTEM_MENUBAR|Nabídek|  
|ROLE_SYSTEM_MENUITEM|Položka nabídky|  
|ROLE_SYSTEM_PANE|Podokno|  
|ROLE_SYSTEM_PROGRESSBAR|Indikátor průběhu|  
|ROLE_SYSTEM_RADIOBUTTON|Přepínač|  
|ROLE_SYSTEM_SCROLLBAR|Posuvník|  
|ROLE_SYSTEM_SEPARATOR|Oddělovač|  
|ROLE_SYSTEM_SLIDER|Posuvník|  
|ROLE_SYSTEM_SPINBUTTON|Číselník|  
|ROLE_SYSTEM_SPLITBUTTON|Tlačítko Rozdělit|  
|ROLE_SYSTEM_STATUSBAR|Stavovém|  
|ROLE_SYSTEM_PAGETABLIST|Karta|  
|ROLE_SYSTEM_PAGETAB|Položka tabulátoru|  
|ROLE_SYSTEM_TABLE|Table|  
|ROLE_SYSTEM_STATICTEXT|Text|  
|ROLE_SYSTEM_INDICATOR|Jezdec|  
|ROLE_SYSTEM_TITLEBAR|Záhlaví|  
|ROLE_SYSTEM_TOOLBAR|Panel nástrojů|  
|ROLE_SYSTEM_TOOLTIP|Popisy tlačítek|  
|ROLE_SYSTEM_OUTLINE|Strom|  
|ROLE_SYSTEM_OUTLINEITEM|Položka stromu|  
|ROLE_SYSTEM_WINDOW|Okno|  
  
 Další informace o různých typech ovládacích prvku naleznete v [tématu Typy řízení automatizace uživatelského rozhraní](ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>
## <a name="states-and-properties"></a>Stavy a vlastnosti  
 V active accessibility elementy podporují společnou sadu vlastností `accState`a některé vlastnosti (například) musí popisovat velmi odlišné věci v závislosti na roli prvku. Servery musí implementovat všechny `IAccessible` metody, které vrátí vlastnost, i ty, které nejsou relevantní pro prvek.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]definuje mnoho dalších vlastností, z nichž některé odpovídají stavům v aktivní přístupnosti. Některé jsou společné pro všechny prvky, ale jiné jsou specifické pro typy ovládacích prvků a vzory ovládacích prvků. Vlastnosti jsou rozlišeny jedinečnými identifikátory a většinu vlastností lze načíst pomocí jediné metody <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> nebo <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>. Mnoho vlastností jsou také <xref:System.Windows.Automation.AutomationElement.Current%2A> snadno <xref:System.Windows.Automation.AutomationElement.Cached%2A> načíst z přístupových objektů a vlastností.  
  
 Zprostředkovatel automatizace uživatelského rozhraní nemusí implementovat irelevantní `null` vlastnosti, ale může jednoduše vrátit hodnotu pro všechny vlastnosti, které nepodporuje. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Základní služba může také získat některé vlastnosti od výchozího zprostředkovatele okna a ty jsou sloučeny s vlastnostmi explicitně implementovanými zprostředkovatelem.  
  
 Kromě podpory mnoha dalších [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastností poskytuje lepší výkon tím, že umožňuje načtení více vlastností pomocí jednoho volání mezi procesy.  
  
 V následující tabulce je uvedena shoda mezi vlastnostmi v obou modelech.  
  
|Přistupující objekt vlastnosti Active Accessibility|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ID vlastnosti|Poznámky|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> nebo <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty`má přednost, pokud jsou přítomny obě.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Mapování rolí na typy ovládacích prvku naleznete v předchozí tabulce.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Platí pouze pro typy ovládacích prvku, které podporují ValuePattern nebo RangeValuePattern. RangeValue hodnoty jsou normalizovány na 0-100, aby byly konzistentní s chováním MSAA. Hodnoty položky používají řetězec.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Není podporováno v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription`neměl jasnou specifikaci v rámci MSAA, což vedlo k tomu, že poskytovatelé umístili různé informace do této vlastnosti.|  
|`get_accHelpTopic`|Není podporováno v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 V následující tabulce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] jsou uvedeny vlastnosti, které odpovídají konstantám stavu aktivní přístupnosti.  
  
|Aktivní stav usnadnění|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Vlastnost|Spustí změnu stavu?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|U zaškrtávacího políčka<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> U přepínacího tlačítka<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|Ano|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|Ano|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded>Nebo<xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|Ano|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|Ne|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|Ne|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern>pro položky nabídky|Ne|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= Pravda <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> a příčiny<xref:System.Windows.Automation.NoClickablePointException>|Ne|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|Ne|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|Ne|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|Ne|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|Ne|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= Pravda|Ne|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|Ne|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> a <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|Ne|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern>je podporován|Ne|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|Ne|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|Ne|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|Ano|  
  
 Následující stavy buď nebyly implementovány většinou serverů řízení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]aktivní přístupnosti nebo nemají žádný ekvivalent v .  
  
|Aktivní stav usnadnění|Poznámky|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Není k dispozici v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Není k dispozici v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Není k dispozici v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Servery Active Accessibility nejsou široce implementovány|  
|STATE_SYSTEM_MARQUEED|Servery Active Accessibility nejsou široce implementovány|  
|STATE_SYSTEM_SELFVOICING|Servery Active Accessibility nejsou široce implementovány|  
|STATE_SYSTEM_TRAVERSED|Není k dispozici v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Servery Active Accessibility nejsou široce implementovány|  
|STATE_SYSTEM_ALERT_MEDIUM|Servery Active Accessibility nejsou široce implementovány|  
|STATE_SYSTEM_ALERT_LOW|Servery Active Accessibility nejsou široce implementovány|  
|STATE_SYSTEM_FLOATING|Servery Active Accessibility nejsou široce implementovány|  
|STATE_SYSTEM_HOTTRACKED|Není k dispozici v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Není k dispozici v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Úplný seznam identifikátorů vlastností [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] naleznete v [tématu Přehled vlastností automatizace uživatelského rozhraní](ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>
## <a name="events"></a>Akce  
 Mechanismus událostí [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]v aplikaci v aplikaci , na rozdíl od protokolu Active Accessibility, nespoléhá na směrování událostí systému Windows (které je úzce spojeno s popisovači oken) a nevyžaduje, aby klientská aplikace nastavila háčky. Odběry událostí lze doladit nejen na konkrétní události, ale na určité části stromu. Poskytovatelé mohou také doladit své zvyšování událostí tím, že sledují, jaké události jsou poslouchány.  
  
 Je také jednodušší pro klienty načíst prvky, které vyvolávají události, protože jsou předány přímo do zpětného volání události. Vlastnosti prvku jsou automaticky předběžně načteny, pokud byl požadavek mezipaměti aktivní, když se klient přihlásil k odběru události.  
  
 V následující tabulce je uvedena korespondence [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] winevents a událostí pro aktivní usnadnění přístupu.  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]identifikátor události|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>změna vlastnosti|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>nebo <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> změna vlastnosti na přidružených posuvnících|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Žádný ekvivalent|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Žádný přesný ekvivalent; možná <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> nebo změna majetku|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>Změnit|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>změna vlastnosti|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty>změna vlastnosti|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|V aktivní přístupnosti se nepoužívá konzistentně. V aplikaci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]není definována žádná přímo odpovídající událost.|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Žádný ekvivalent|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Různé události změněné vlastnostmi|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>a <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> změnil|  
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
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>změna vlastnosti|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>změna vlastnosti|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>změna vlastnosti|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>změna vlastnosti|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>nebo <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> změna vlastnosti|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>nebo <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> změna vlastnosti|  
|EVENT_SYSTEM_SOUND|Žádný ekvivalent|  
|EVENT_SYSTEM_SWITCHEND|Žádný ekvivalent, <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> ale událost signalizuje, že nová aplikace získala fokus|  
|EVENT_SYSTEM_SWITCHSTART|Žádný ekvivalent|  
|Žádný ekvivalent|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty>změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty>změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty>změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty>změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty>změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty>změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>změna vlastnosti|  
|Žádný ekvivalent|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent>Událost|  
|Žádný ekvivalent|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>
## <a name="security"></a>Zabezpečení  
 Některé `IAccessible` scénáře přizpůsobení vyžadují `IAccessible` obtékání základny a volání na něj. To má důsledky pro zabezpečení, protože částečně důvěryhodná součást by neměla být prostředníkem na cestě kódu.  
  
 Model [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] odebere potřebu zprostředkovatelů volat do jiného kódu zprostředkovatele. Základní [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] služba provádí všechny potřebné agregace.  
  
## <a name="see-also"></a>Viz také

- [Principy automatizace uživatelského rozhraní](index.md)
