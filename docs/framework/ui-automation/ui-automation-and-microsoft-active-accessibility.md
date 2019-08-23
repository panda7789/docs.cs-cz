---
title: Automatizace uživatelského rozhraní a technologie Microsoft Active Accessibility
ms.date: 03/30/2017
helpviewer_keywords:
- Active Accessibility
- UI Automation, Active Accessibility compared to
- UI Automation, Microsoft Active Accessibility
- Active Accessibility, UI Automation compared to
ms.assetid: 87bee662-0a3e-4232-a421-20e7a5968321
ms.openlocfilehash: 8aadcc213e92fd53490f639f37dc8d8f62762c2c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946485"
---
# <a name="ui-automation-and-microsoft-active-accessibility"></a>Automatizace uživatelského rozhraní a technologie Microsoft Active Accessibility
> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.  
  
 Microsoft Active Accessibility je dřívější řešení pro zpřístupnění aplikací. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]je nový model přístupnosti [!INCLUDE[TLA#tla_win](../../../includes/tlasharptla-win-md.md)] pro nástroj a má řešit potřeby produktů pro usnadnění a automatizované testování. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nabízí mnoho vylepšení služby Active Accessibility.  
  
 Toto téma obsahuje hlavní funkce [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nástroje a vysvětluje, jak se tyto funkce liší od aktivního přístupu.  
  
<a name="Programming_Languages_compare"></a>   
## <a name="programming-languages"></a>Programovací jazyky  
< aktivní přístupnost je založena na modelu COM (Component Object Model) s podporou duálních rozhraní a je proto programovatelné v jazycích C/C++, [!INCLUDE[TLA#tla_vb6](../../../includes/tlasharptla-vb6-md.md)]a skriptovacích jazycích. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)](včetně knihovny zprostředkovatele na straně klienta pro standardní ovládací prvky) je zapsán ve spravovaném kódu a klientské aplikace automatizace uživatelského rozhraní jsou nejčastěji programové pomocí C# nebo Visual Basic .NET. Zprostředkovatelé automatizace uživatelského rozhraní, což jsou implementace rozhraní, mohou být napsány ve spravovanémC++kódu nebo v C/.  
  
<a name="Support_in_Windows_Presentation_Foundation_"></a>   
## <a name="support-in-windows-presentation-foundation"></a>Podpora v Windows Presentation Foundation  
 Windows Presentation Foundation (WPF) je nový model pro vytváření uživatelských rozhraní. [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]prvky neobsahují nativní podporu pro aktivní přístupnost; podporují [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ale podporu přemostění pro aktivní klienty usnadnění. Jenom klienti napsané speciálně [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] pro můžou plně využít výhod [!INCLUDE[TLA2#tla_wpf](../../../includes/tla2sharptla-wpf-md.md)]funkcí pro usnadnění přístupu, jako je bohatá podpora pro text.  
  
<a name="Servers_and_Clients_compare"></a>   
## <a name="servers-and-clients"></a>Servery a klienti  
 V aktivním usnadnění komunikuje servery a klienti přímo do značné míry prostřednictvím implementace `IAccessible`serveru.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]nástroji se mezi serverem (nazývaným zprostředkovatel) a klientem nachází základní služba. Základní služba volá rozhraní implementovaná poskytovateli a poskytuje další služby, jako je například generování jedinečných identifikátorů modulu runtime pro prvky. Klientské aplikace používají funkce knihovny pro volání [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] služby.  
  
 Zprostředkovatelé automatizace uživatelského rozhraní můžou poskytovat informace pro aktivní klienty usnadnění a aktivní servery pro usnadnění můžou poskytovat informace klientským aplikacím automatizace uživatelského rozhraní. Protože ale aktivní přístupnost nezveřejňuje tolik informací [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], že tyto dva modely nejsou plně kompatibilní.  
  
<a name="UI_Elements_compare"></a>   
## <a name="ui-elements"></a>Prvky uživatelského rozhraní  
 Aktivní přístupnost prezentuje [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvky buď `IAccessible` jako rozhraní, nebo jako identifikátor podřízeného objektu. Je obtížné porovnat dva `IAccessible` ukazatele, aby bylo možné určit, zda odkazují na stejný prvek.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]je každý prvek reprezentován <xref:System.Windows.Automation.AutomationElement> jako objekt. Porovnání je provedeno pomocí operátoru rovnosti nebo <xref:System.Windows.Automation.AutomationElement.Equals%2A> metody, obou z nich porovnává jedinečné běhové identifikátory prvků.  
  
<a name="Tree_Views_and_Navigation_compare"></a>   
## <a name="tree-views-and-navigation"></a>Stromová zobrazení a navigace  
 [!INCLUDE[TLA#tla_ui](../../../includes/tlasharptla-ui-md.md)] Prvky na obrazovce lze zobrazit jako stromovou strukturu s plochou jako kořenovým adresářem, aplikacemi jako bezprostředními podřízenými a prvky v aplikacích jako další následníky.  
  
 V aktivním usnadnění jsou ve stromové struktuře dostupné mnoho prvků automatizace, které jsou pro koncové uživatele nepodstatné. Klientské aplikace musí pohlížet na všechny prvky a určit, které jsou smysluplné.  
  
 Klientské aplikace automatizace uživatelského rozhraní se [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] zobrazí ve filtrovaném zobrazení. Zobrazení obsahuje pouze zajímavé prvky: ty, které uživateli poskytují informace nebo umožňují interakci. Předdefinovaná zobrazení pouze ovládacích prvků a jsou k dispozici pouze prvky obsahu; Kromě toho můžou aplikace definovat vlastní zobrazení. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]zjednodušuje úkol popisu [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] uživatele a pomáhá uživatelům pracovat s aplikací.  
  
 Navigace mezi prvky v aktivním usnadnění je buď prostorová (například přechod na prvek, který je na obrazovce vlevo), logický (například přesunutí na další položku nabídky nebo další položka v pořadí prvků v dialogovém okně) nebo hierarchická ( například přesunutí prvního podřízeného objektu do kontejneru nebo z podřízeného na jeho nadřazený objekt. Hierarchická navigace je složitá faktem, že podřízené elementy nejsou vždy objekty, `IAccessible`které implementují.  
  
 V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]platí, [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] že všechny <xref:System.Windows.Automation.AutomationElement> prvky jsou objekty, které podporují stejné základní funkce. (Z hlediska poskytovatele jsou objekty, které implementují rozhraní zděděné z <xref:System.Windows.Automation.Provider.IRawElementProviderSimple>.) Navigace je hlavně hierarchicky: od rodičů po podřízené a z jednoho na stejné úrovni jako další. (Navigace mezi sourozenci má logický element, jak může následovat po pořadí ovládacích prvků.) Můžete přejít z libovolného počátečního bodu pomocí libovolného filtrovaného zobrazení stromu <xref:System.Windows.Automation.TreeWalker> pomocí třídy. Můžete také přejít na konkrétní podřízené položky nebo následníky pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> a <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; například je velmi snadné načíst všechny prvky v dialogovém okně, které podporují určený vzor ovládacího prvku.  
  
 Navigace v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] nástroji je spolehlivější než v aktivních přístupnosti. Některé prvky, jako jsou rozevírací seznamy a automaticky otevíraná okna, se v aktivním stromu přístupnosti zobrazují dvakrát a navigace z nich může mít neočekávané výsledky. Ve skutečnosti není možné správně implementovat aktivní přístupnost pro ovládací prvek matrice. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]umožňuje přemísťovat nadřazené a přemístění, aby se element mohl umístit kamkoli do stromu navzdory hierarchii, kterou ukládá vlastnictví Windows.  
  
<a name="Roles_and_Control_Types"></a>   
## <a name="roles-and-control-types"></a>Role a typy ovládacích prvků  
 Aktivní přístupnost používá `accRole` vlastnost (`IAccessible::get_actRole`) k načtení popisu role [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)]elementu v, jako je například ROLE_SYSTEM_SLIDER nebo ROLE_SYSTEM_MENUITEM. Role elementu je hlavním prvkem přístupnosti k dostupným funkcím. Interakce s ovládacím prvkem se dosahuje pomocí pevných metod, jako `IAccessible::accSelect` jsou `IAccessible::accDoDefaultAction`a. Interakce mezi klientskou aplikací a [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] je omezená na to, co se dá dělat prostřednictvím. `IAccessible`  
  
 Naproti tomu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] převážně odděluje typ ovládacího prvku prvku (popsaný <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.ControlType%2A> vlastností) z očekávané funkce. Funkčnost je určena vzory ovládacích prvků, které jsou podporovány poskytovatelem prostřednictvím jeho implementace specializovaných rozhraní. Vzory ovládacích prvků lze kombinovat a popsat tak úplnou sadu funkcí podporovaných určitým [!INCLUDE[TLA2#tla_ui](../../../includes/tla2sharptla-ui-md.md)] prvkem. Někteří poskytovatelé jsou vyžadováni pro podporu určitého vzoru ovládacího prvku. například poskytovatel pro zaškrtávací políčko musí podporovat vzor ovládacího prvku přepínací tlačítko. Jiní poskytovatelé jsou vyžadováni k podpoře jednoho nebo více sad řídicích vzorů; například tlačítko musí podporovat buď přepínač, nebo vyvolání. Pořád ještě nepodporují žádné řídicí vzory. například podokno, které nelze přesunout, změnit jeho velikost nebo ukotvení, nemá žádné vzory ovládacích prvků.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]podporuje vlastní ovládací prvky, které jsou označeny <xref:System.Windows.Automation.ControlType.Custom> vlastností a mohou být popsány <xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> vlastností.  
  
 Následující tabulka ukazuje mapování aktivních rolí přístupnosti na [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] typy ovládacích prvků.  
  
|Role aktivního přístupnosti|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]typ ovládacího prvku|  
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
|ROLE_SYSTEM_COLUMNHEADER|Položka záhlaví|  
|ROLE_SYSTEM_LINK|Hypertextový odkaz|  
|ROLE_SYSTEM_GRAPHIC|Image|  
|ROLE_SYSTEM_LIST|Seznam|  
|ROLE_SYSTEM_LISTITEM|Položka seznamu|  
|ROLE_SYSTEM_MENUPOPUP|Nabídka|  
|ROLE_SYSTEM_MENUBAR|Panel nabídek|  
|ROLE_SYSTEM_MENUITEM|Položka nabídky|  
|ROLE_SYSTEM_PANE|Podokno|  
|ROLE_SYSTEM_PROGRESSBAR|Indikátor průběhu|  
|ROLE_SYSTEM_RADIOBUTTON|Přepínač|  
|ROLE_SYSTEM_SCROLLBAR|Posuvník|  
|ROLE_SYSTEM_SEPARATOR|Oddělovač|  
|ROLE_SYSTEM_SLIDER|Posuvník|  
|ROLE_SYSTEM_SPINBUTTON|Číselník|  
|ROLE_SYSTEM_SPLITBUTTON|Tlačítko rozdělení|  
|ROLE_SYSTEM_STATUSBAR|Stavový řádek|  
|ROLE_SYSTEM_PAGETABLIST|Karta|  
|ROLE_SYSTEM_PAGETAB|Položka karty|  
|ROLE_SYSTEM_TABLE|Tabulka|  
|ROLE_SYSTEM_STATICTEXT|Text|  
|ROLE_SYSTEM_INDICATOR|Jezdec|  
|ROLE_SYSTEM_TITLEBAR|Záhlaví|  
|ROLE_SYSTEM_TOOLBAR|Panel nástrojů|  
|ROLE_SYSTEM_TOOLTIP|Popisy tlačítek|  
|ROLE_SYSTEM_OUTLINE|Strom|  
|ROLE_SYSTEM_OUTLINEITEM|Položka stromu|  
|ROLE_SYSTEM_WINDOW|Okno|  
  
 Další informace o různých typech ovládacích prvků naleznete v tématu [typy ovládacích prvků automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-types.md).  
  
<a name="States_and_Properties"></a>   
## <a name="states-and-properties"></a>Stavy a vlastnosti  
 V aktivních přístupnostech prvky podporují společnou sadu vlastností a některé vlastnosti (například `accState`) musí v závislosti na roli elementu popsány velmi odlišně. Servery musí implementovat všechny metody `IAccessible` , které vracejí vlastnost, i ty, které nejsou relevantní pro element.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]definuje mnoho dalších vlastností, z nichž některé odpovídají státům v aktivním usnadnění. Některé jsou společné pro všechny prvky, ale jiné jsou specifické pro typy ovládacích prvků a vzory ovládacích prvků. Vlastnosti jsou odlišeny pomocí jedinečných identifikátorů a většinu vlastností lze načíst pomocí jediné metody <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> nebo. <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> Mnoho vlastností je také možné snadno získat z <xref:System.Windows.Automation.AutomationElement.Current%2A> přístupových objektů a <xref:System.Windows.Automation.AutomationElement.Cached%2A> vlastností.  
  
 Zprostředkovatel automatizace uživatelského rozhraní nevyžaduje implementaci nepodstatných vlastností, ale může jednoduše vrátit `null` hodnotu pro jakékoli vlastnosti, které nepodporuje. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Základní služba taky může získat některé vlastnosti z výchozího poskytovatele Windows a ty jsou dají s vlastnostmi, které jsou explicitně implementované zprostředkovatelem.  
  
 Stejně jako podpora mnoha dalších vlastností poskytuje lepší [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] výkon tím, že umožňuje načíst více vlastností s jedním voláním mezi procesy.  
  
 Následující tabulka znázorňuje korespondenci mezi vlastnostmi ve dvou modelech.  
  
|Přístup k vlastnosti aktivního přístupnosti|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ID vlastnosti|Poznámky|  
|-----------------------------------------------------------------------------------|---------------------------------------------------------------------------------------|-------------|  
|`get_accKeyboardShortcut`|<xref:System.Windows.Automation.AutomationElement.AccessKeyProperty> Nebo <xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>|`AccessKeyProperty`má přednost, pokud jsou oba přítomné.|  
|`get_accName`|<xref:System.Windows.Automation.AutomationElement.NameProperty>||  
|`get_accRole`|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty>|Viz předchozí tabulka pro mapování rolí na typy ovládacích prvků.|  
|`get_accValue`|<xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType><br /><br /> <xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>|Platné pouze pro typy ovládacích prvků, které podporují ValuePattern nebo RangeValuePattern. Hodnoty ovládacích RangeValue jsou normalizovány na 0-100, aby byly konzistentní s chováním MSAA. Položky hodnot používají řetězec.|  
|`get_accHelp`|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>||  
|`accLocation`|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>||  
|`get_accDescription`|Nepodporováno v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|`accDescription`v rámci rozhraní MSAA neexistovala žádná specifikace, což vedlo k tomu, že poskytovatelé z této vlastnosti umísťují různé informace.|  
|`get_accHelpTopic`|Nepodporováno v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]||  
  
 V následující tabulce jsou uvedeny [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] vlastnosti, které odpovídají aktivním konstantám stavu přístupnosti.  
  
|Stav aktivního přístupnosti|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]majetek|Aktivuje se změna stavu?|  
|-----------------------------------------------------------------------|------------------------------------------------------------------------------------|----------------------------|  
|STATE_SYSTEM_CHECKED|Pro zaškrtávací políčko<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty><br /><br /> Pro přepínač<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|Ano|  
|STATE_SYSTEM_COLLAPSED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Collapsed>|Ano|  
|STATE_SYSTEM_EXPANDED|<xref:System.Windows.Automation.ExpandCollapsePattern.ExpandCollapsePatternInformation.ExpandCollapseState%2A> = <xref:System.Windows.Automation.ExpandCollapseState.Expanded>ani<xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>|Ano|  
|STATE_SYSTEM_FOCUSABLE|<xref:System.Windows.Automation.AutomationElement.IsKeyboardFocusableProperty>|N|  
|STATE_SYSTEM_FOCUSED|<xref:System.Windows.Automation.AutomationElement.HasKeyboardFocusProperty>|N|  
|STATE_SYSTEM_HASPOPUP|<xref:System.Windows.Automation.ExpandCollapsePattern>pro položky nabídky|N|  
|STATE_SYSTEM_INVISIBLE|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= True a <xref:System.Windows.Automation.AutomationElement.GetClickablePoint%2A> příčiny<xref:System.Windows.Automation.NoClickablePointException>|N|  
|STATE_SYSTEM_LINKED|<xref:System.Windows.Automation.AutomationElement.ControlTypeProperty> =<br /><br /> <xref:System.Windows.Automation.ControlType.Hyperlink>|N|  
|STATE_SYSTEM_MIXED|<xref:System.Windows.Automation.TogglePattern.TogglePatternInformation.ToggleState%2A> = <xref:System.Windows.Automation.ToggleState.Indeterminate>|N|  
|STATE_SYSTEM_MOVEABLE|<xref:System.Windows.Automation.TransformPattern.CanMoveProperty>|N|  
|STATE_SYSTEM_MUTLISELECTABLE|<xref:System.Windows.Automation.SelectionPattern.CanSelectMultipleProperty>|N|  
|STATE_SYSTEM_OFFSCREEN|<xref:System.Windows.Automation.AutomationElement.IsOffscreenProperty>= True|N|  
|STATE_SYSTEM_PROTECTED|<xref:System.Windows.Automation.AutomationElement.IsPasswordProperty>|N|  
|STATE_SYSTEM_READONLY|<xref:System.Windows.Automation.RangeValuePattern.IsReadOnlyProperty?displayProperty=nameWithType> a <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty?displayProperty=nameWithType>|N|  
|STATE_SYSTEM_SELECTABLE|<xref:System.Windows.Automation.SelectionItemPattern>je podporováno|N|  
|STATE_SYSTEM_SELECTED|<xref:System.Windows.Automation.SelectionItemPattern.IsSelectedProperty>|N|  
|STATE_SYSTEM_SIZEABLE|<xref:System.Windows.Automation.TransformPattern.TransformPatternInformation.CanResize%2A>|N|  
|STATE_SYSTEM_UNAVAILABLE|<xref:System.Windows.Automation.AutomationElement.IsEnabledProperty>|Ano|  
  
 Následující stavy buď nebyly implementovány většinou aktivních serverů řízení dostupnosti, nebo nemají žádný ekvivalent [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)].  
  
|Stav aktivního přístupnosti|Poznámky|  
|-----------------------------------------------------------------------|-------------|  
|STATE_SYSTEM_BUSY|Není k dispozici v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_DEFAULT|Není k dispozici v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ANIMATED|Není k dispozici v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_EXTSELECTABLE|Aktivní servery pro usnadnění nejsou široce implementovány.|  
|STATE_SYSTEM_MARQUEED|Aktivní servery pro usnadnění nejsou široce implementovány.|  
|STATE_SYSTEM_SELFVOICING|Aktivní servery pro usnadnění nejsou široce implementovány.|  
|STATE_SYSTEM_TRAVERSED|Není k dispozici v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_ALERT_HIGH|Aktivní servery pro usnadnění nejsou široce implementovány.|  
|STATE_SYSTEM_ALERT_MEDIUM|Aktivní servery pro usnadnění nejsou široce implementovány.|  
|STATE_SYSTEM_ALERT_LOW|Aktivní servery pro usnadnění nejsou široce implementovány.|  
|STATE_SYSTEM_FLOATING|Aktivní servery pro usnadnění nejsou široce implementovány.|  
|STATE_SYSTEM_HOTTRACKED|Není k dispozici v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
|STATE_SYSTEM_PRESSED|Není k dispozici v[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]|  
  
 Úplný seznam [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] identifikátorů vlastností najdete v tématu [Přehled vlastností automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-properties-overview.md).  
  
<a name="uiautomation_events_compare"></a>   
## <a name="events"></a>Události  
 Mechanismus událostí v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], na rozdíl od toho, že v aktivním usnadnění, nespoléhá na směrování událostí systému Windows (což je úzce svázáno s popisovači oken) a nevyžaduje klientskou aplikaci, aby nastavila zavěšení. Odběry událostí mohou být jemně vyladěny nejen na konkrétní události, ale pouze na konkrétní části stromu. Poskytovatelé mohou také doladit své vyvolání událostí tím, že udržují přehled o událostech, které jsou pro ně naslouchají.  
  
 Pro klienty je také snazší načíst prvky, které vyvolávají události, protože jsou předány přímo do zpětného volání události. Vlastnosti prvku jsou automaticky načteny, pokud byla žádost o mezipaměť aktivní, když se klient přihlásil k odběru události.  
  
 Následující tabulka uvádí korespondenci aktivních WinEvents a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] událostí přístupnosti.  
  
|WinEvent|[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]identifikátor události|  
|--------------|--------------------------------------------------------------------------------------------|  
|EVENT_OBJECT_ACCELERATORCHANGE|<xref:System.Windows.Automation.AutomationElement.AcceleratorKeyProperty>Změna vlastnosti|  
|EVENT_OBJECT_CONTENTSCROLLED|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>nebo <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> Změna vlastnosti na přidružených posuvníkech|  
|EVENT_OBJECT_CREATE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_DEFACTIONCHANGE|Bez ekvivalentu|  
|EVENT_OBJECT_DESCRIPTIONCHANGE|Bez přesného ekvivalentu; Možná <xref:System.Windows.Automation.AutomationElement.HelpTextProperty> nebo<xref:System.Windows.Automation.AutomationElement.LocalizedControlTypeProperty> Změna vlastnosti|  
|EVENT_OBJECT_DESTROY|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_FOCUS|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_OBJECT_HELPCHANGE|<xref:System.Windows.Automation.AutomationElement.HelpTextProperty>mění|  
|EVENT_OBJECT_HIDE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_LOCATIONCHANGE|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>Změna vlastnosti|  
|EVENT_OBJECT_NAMECHANGE|<xref:System.Windows.Automation.AutomationElement.NameProperty>Změna vlastnosti|  
|EVENT_OBJECT_PARENTCHANGE|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_REORDER|Nepoužívá se konzistentně v aktivním usnadnění. V [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]není definována žádná přímo odpovídající událost.|  
|EVENT_OBJECT_SELECTION|<xref:System.Windows.Automation.SelectionItemPattern.ElementSelectedEvent>|  
|EVENT_OBJECT_SELECTIONADD|<xref:System.Windows.Automation.SelectionItemPattern.ElementAddedToSelectionEvent>|  
|EVENT_OBJECT_SELECTIONREMOVE|<xref:System.Windows.Automation.SelectionItemPattern.ElementRemovedFromSelectionEvent>|  
|EVENT_OBJECT_SELECTIONWITHIN|Bez ekvivalentu|  
|EVENT_OBJECT_SHOW|<xref:System.Windows.Automation.AutomationElement.StructureChangedEvent>|  
|EVENT_OBJECT_STATECHANGE|Různé události změněné vlastností|  
|EVENT_OBJECT_VALUECHANGE|<xref:System.Windows.Automation.RangeValuePattern.ValueProperty?displayProperty=nameWithType>a <xref:System.Windows.Automation.ValuePattern.ValueProperty?displayProperty=nameWithType> změněno|  
|EVENT_SYSTEM_ALERT|Bez ekvivalentu|  
|EVENT_SYSTEM_CAPTUREEND|Bez ekvivalentu|  
|EVENT_SYSTEM_CAPTURESTART|Bez ekvivalentu|  
|EVENT_SYSTEM_CONTEXTHELPEND|Bez ekvivalentu|  
|EVENT_SYSTEM_CONTEXTHELPSTART|Bez ekvivalentu|  
|EVENT_SYSTEM_DIALOGEND|<xref:System.Windows.Automation.WindowPattern.WindowClosedEvent>|  
|EVENT_SYSTEM_DIALOGSTART|<xref:System.Windows.Automation.WindowPattern.WindowOpenedEvent>|  
|EVENT_SYSTEM_DRAGDROPEND|Bez ekvivalentu|  
|EVENT_SYSTEM_DRAGDROPSTART|Bez ekvivalentu|  
|EVENT_SYSTEM_FOREGROUND|<xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent>|  
|EVENT_SYSTEM_MENUEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPEND|<xref:System.Windows.Automation.AutomationElement.MenuClosedEvent>|  
|EVENT_SYSTEM_MENUPOPUPSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MENUSTART|<xref:System.Windows.Automation.AutomationElement.MenuOpenedEvent>|  
|EVENT_SYSTEM_MINIMIZEEND|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>Změna vlastnosti|  
|EVENT_SYSTEM_MINIMIZESTART|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>Změna vlastnosti|  
|EVENT_SYSTEM_MOVESIZEEND|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>Změna vlastnosti|  
|EVENT_SYSTEM_MOVESIZESTART|<xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty>Změna vlastnosti|  
|EVENT_SYSTEM_SCROLLINGEND|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>nebo <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> Změna vlastnosti|  
|EVENT_SYSTEM_SCROLLINGSTART|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>nebo <xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty> Změna vlastnosti|  
|EVENT_SYSTEM_SOUND|Bez ekvivalentu|  
|EVENT_SYSTEM_SWITCHEND|Bez ekvivalentu, ale <xref:System.Windows.Automation.AutomationElement.AutomationFocusChangedEvent> událost signalizuje, že nová aplikace obdržela fokus.|  
|EVENT_SYSTEM_SWITCHSTART|Bez ekvivalentu|  
|Bez ekvivalentu|<xref:System.Windows.Automation.MultipleViewPattern.CurrentViewProperty>Změna vlastnosti|  
|Bez ekvivalentu|<xref:System.Windows.Automation.ScrollPattern.HorizontallyScrollableProperty>Změna vlastnosti|  
|Bez ekvivalentu|<xref:System.Windows.Automation.ScrollPattern.VerticallyScrollableProperty>Změna vlastnosti|  
|Bez ekvivalentu|<xref:System.Windows.Automation.ScrollPattern.HorizontalScrollPercentProperty>Změna vlastnosti|  
|Bez ekvivalentu|<xref:System.Windows.Automation.ScrollPattern.VerticalScrollPercentProperty>Změna vlastnosti|  
|Bez ekvivalentu|<xref:System.Windows.Automation.ScrollPattern.HorizontalViewSizeProperty>Změna vlastnosti|  
|Bez ekvivalentu|<xref:System.Windows.Automation.ScrollPattern.VerticalViewSizeProperty>Změna vlastnosti|  
|Bez ekvivalentu|<xref:System.Windows.Automation.TogglePattern.ToggleStateProperty>Změna vlastnosti|  
|Bez ekvivalentu|<xref:System.Windows.Automation.WindowPattern.WindowVisualStateProperty>Změna vlastnosti|  
|Bez ekvivalentu|<xref:System.Windows.Automation.AutomationElement.AsyncContentLoadedEvent>událostí|  
|Bez ekvivalentu|<xref:System.Windows.Automation.AutomationElement.ToolTipOpenedEvent>|  
  
<a name="Security_compare"></a>   
## <a name="security"></a>Zabezpečení  
 Některé `IAccessible` scénáře přizpůsobení vyžadují zalomení základní `IAccessible` třídy a volání do ní. To má vliv na zabezpečení, protože částečně důvěryhodná komponenta by neměla být zprostředkující v cestě kódu.  
  
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Model odebere nutnost volání zprostředkovatelů do jiného kódu poskytovatele. [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Základní služba provádí veškerou nezbytnou agregaci.  
  
## <a name="see-also"></a>Viz také:

- [Principy automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/index.md)
