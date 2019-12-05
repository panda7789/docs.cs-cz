---
title: Přehled prvku TextPattern automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
ms.openlocfilehash: b7e378d79109d33859a38ea398cffd2193044abd
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800195"
---
# <a name="ui-automation-textpattern-overview"></a>Přehled prvku TextPattern automatizace uživatelského rozhraní

> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).

Tento přehled popisuje, jak použít [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k vystavení textového obsahu, včetně formátů a atributů stylu, textových ovládacích prvků v platformách podporovaných [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Mezi tyto ovládací prvky patří, ale nejsou omezeny na .NET Framework <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox> od společnosti Microsoft, jakož i jejich ekvivalenty [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)].

Vystavení textového obsahu ovládacího prvku je provedeno pomocí vzoru ovládacího prvku <xref:System.Windows.Automation.TextPattern>, který představuje obsah kontejneru textu jako textový Stream. <xref:System.Windows.Automation.TextPattern> vyžaduje podporu třídy <xref:System.Windows.Automation.Text.TextPatternRange> k vystavení formátu a atributů stylu. <xref:System.Windows.Automation.Text.TextPatternRange> podporuje <xref:System.Windows.Automation.TextPattern> tím, že představuje souvislý nebo vícenásobný nesouvislý text v kontejneru textu s kolekcí <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> a <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> koncových bodů. <xref:System.Windows.Automation.Text.TextPatternRange> podporuje funkce, jako je výběr, porovnání, načítání a procházení.

> [!NOTE]
> Třídy <xref:System.Windows.Automation.TextPattern> neposkytují prostředky pro vložení nebo úpravu textu. V závislosti na ovládacím prvku však lze to provést [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> nebo přímým vstupem klávesnice. Příklad naleznete v [ukázce TextPattern INSERT text](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText) .

Funkce popsané v tomto přehledu jsou důležité pro dodavatele s asistenčními technologiemi a jejich koncové uživatele. Technologie pro usnadnění můžou použít [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ke shromažďování úplných informací o formátování textu pro uživatele a poskytování programové navigace a výběru textu pomocí <xref:System.Windows.Automation.Text.TextUnit> (znak, Word, řádek nebo odstavec).

<a name="UI_Automation_TextPattern_vs__Cicero"></a>

## <a name="ui-automation-textpattern-vs-text-services-framework"></a>ROZHRANÍ .NET Automation TextPattern vs. Text Services Framework

Rozhraní TSF (text Services Framework) je jednoduché a škálovatelné systémové rozhraní, které umožňuje využívat služby přirozeného jazyka a pokročilý Textový vstup na ploše a v aplikacích. Kromě poskytování rozhraní pro aplikace k zveřejnění jejich textového úložiště podporuje také metadata pro toto úložiště textu.

TSF však byl navržen pro aplikace, které vyžadují vložení vstupu do kontextových scénářů, zatímco <xref:System.Windows.Automation.TextPattern> je řešení jen pro čtení (s výše uvedeným omezením), které má poskytovat optimalizovaný přístup k úložišti textu pro čtečky obrazovky a zařízení Braillova písma.

V krátkých a přístupných technologiích, které vyžadují přístup k úložišti textu jen pro čtení, může použít <xref:System.Windows.Automation.TextPattern>, ale budou potřebovat složitější funkce TSF pro kontextově náročné vstupy.

<a name="Control_Types"></a>

## <a name="control-types"></a>Typy ovládacích prvků

### <a name="text"></a>Text

Textový ovládací prvek je základní prvek reprezentující text na obrazovce.

Samostatný ovládací prvek textu lze použít jako popisek nebo statický text na formuláři. Ovládací prvky textu mohou být také obsaženy v rámci struktury <xref:System.Windows.Automation.ControlType.ListItem>, <xref:System.Windows.Automation.ControlType.TreeItem> nebo <xref:System.Windows.Automation.ControlType.DataItem>.

> [!NOTE]
> Textové ovládací prvky se nemusí zobrazit v zobrazení obsahu stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] (viz [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)). Je to proto, že textové ovládací prvky se často zobrazují prostřednictvím vlastnosti název jiného ovládacího prvku. Například text, který se používá k označení ovládacího prvku pro úpravy, je přístupný prostřednictvím vlastnosti Name ovládacího prvku pro úpravy. Vzhledem k tomu, že je ovládací prvek pro úpravy v zobrazení obsahu stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], není nutné, aby byl prvek textu v tomto zobrazení stromu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]. Jediný text, který se zobrazí v zobrazení obsahu, je text, který není redundantní informace. To umožňuje všem asistenčním technologiím rychle filtrovat pouze ty informace, které jejich uživatelé potřebují.

### <a name="edit"></a>Upravit

Ovládací prvky pro úpravy umožňují uživateli zobrazit a upravit jeden řádek textu.

> [!NOTE]
> Jeden řádek textu může v některých scénářích rozložení obtékat.

### <a name="document"></a>Dokument

Ovládací prvky dokumentu umožňují uživateli přejít na více stránek textu a získat z nich informace.

<a name="TextPattern_Client_API_s"></a>

## <a name="textpattern-client-apis"></a>Klientská rozhraní API pro TextPattern

|||
|-|-|
|`System.Windows.Automation.TextPattern Class`|Vstupní bod pro [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] textový model.<br /><br /> Tato třída také obsahuje dva naslouchací procesy <xref:System.Windows.Automation.TextPattern> události <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> a <xref:System.Windows.Automation.TextPattern.TextChangedEvent>.|
|`System.Windows.Automation.Text.TextPatternRange Class`|Reprezentace rozsahu textu v rámci kontejneru textu, který podporuje <xref:System.Windows.Automation.TextPattern>.<br /><br /> Klienti automatizace uživatelského rozhraní by měli mít pozor na aktuální platnosti rozsahu textu vytvořeného pomocí <xref:System.Windows.Automation.Text.TextPatternRange>. Pokud je původní text v ovládacím prvku text úplně nahrazen novým textem, aktuální rozsah textu se změní na neplatný. Rozsah textu ale může mít i určitou životaschopnost, pokud se změní jenom část původního textu a podkladový ovládací prvek textu spravuje svůj text "ukazatel" s kotvami (nebo koncovými body) místo s absolutním umístěním znaků.<br /><br /> Klienti mohou naslouchat <xref:System.Windows.Automation.TextPattern.TextChangedEvent> a oznámení o změnách v textovém obsahu, se kterými pracují.|
|`System.Windows.Automation.AutomationTextAttribute Class`|Slouží k identifikaci formátovacích atributů oblasti textu.|

<a name="TextPattern_Provider_API_s"></a>

## <a name="textpattern-provider-apis"></a>Rozhraní API pro poskytovatele TextPattern

Prvky uživatelského rozhraní nebo ovládací prvky, které podporují <xref:System.Windows.Automation.TextPattern> implementací rozhraní <xref:System.Windows.Automation.Provider.ITextProvider> a <xref:System.Windows.Automation.Provider.ITextRangeProvider>, a to buď nativně, nebo [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] prostřednictvím proxy serverů, jsou schopné vystavit podrobné informace o atributu pro libovolný text, který obsahuje kromě poskytování robustních navigačních možností.

Poskytovatel <xref:System.Windows.Automation.TextPattern> nemusí podporovat všechny atributy textu, pokud ovládací prvek nemá podporu pro všechny konkrétní atributy.

Poskytovatel <xref:System.Windows.Automation.TextPattern> musí podporovat funkce <xref:System.Windows.Automation.TextPattern.GetSelection%2A> a <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A>, pokud ovládací prvek podporuje výběr textu nebo umístění textového kurzoru (nebo systémového kurzoru) v oblasti textu. Pokud ovládací prvek tuto funkci nepodporuje, nemusí podporovat žádnou z těchto metod. Ovládací prvek však musí vystavit typ výběru textu, který podporuje implementací vlastnosti <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A>.

Poskytovatel <xref:System.Windows.Automation.TextPattern> musí vždycky podporovat <xref:System.Windows.Automation.Text.TextUnit> konstanty <xref:System.Windows.Automation.Text.TextUnit.Character> a <xref:System.Windows.Automation.Text.TextUnit.Document> a také všechny další <xref:System.Windows.Automation.Text.TextUnit> konstanty, které podporuje.

> [!NOTE]
> Poskytovatel může přeskočit podporu konkrétního <xref:System.Windows.Automation.Text.TextUnit> tím, že odvozuje k nejbližšímu největšímu <xref:System.Windows.Automation.Text.TextUnit> podporovanému v následujícím pořadí: <xref:System.Windows.Automation.Text.TextUnit.Character>, <xref:System.Windows.Automation.Text.TextUnit.Format>, <xref:System.Windows.Automation.Text.TextUnit.Word>, <xref:System.Windows.Automation.Text.TextUnit.Line>, <xref:System.Windows.Automation.Text.TextUnit.Paragraph>, <xref:System.Windows.Automation.Text.TextUnit.Page>a <xref:System.Windows.Automation.Text.TextUnit.Document>.

|||
|-|-|
|`ITextProvider Interface`|Zpřístupňuje metody, vlastnosti a atributy, které podporují <xref:System.Windows.Automation.TextPattern> v klientských aplikacích (viz <xref:System.Windows.Automation.Provider.ITextProvider>).|
|`ITextRangeProvider Interface`|Představuje rozsah textu v poskytovateli textu (viz <xref:System.Windows.Automation.Provider.ITextRangeProvider>).|
|`System.Windows.Automation.TextPatternIdentifiers Class`|Obsahuje hodnoty, které se používají jako identifikátory pro poskytovatele textu (viz <xref:System.Windows.Automation.TextPatternIdentifiers>).|

<a name="Security"></a>

## <a name="security"></a>Zabezpečení –

Architektura [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] byla navržena s ohledem na zabezpečení (viz [Přehled zabezpečení automatizace uživatelského rozhraní](ui-automation-security-overview.md)). Třídy TextPattern popsané v tomto přehledu ale vyžadují určité konkrétní požadavky na zabezpečení.

- poskytovatelé [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] textu poskytují rozhraní jen pro čtení a neposkytují možnost měnit stávající text v ovládacím prvku.

- Klienti automatizace uživatelského rozhraní můžou použít [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jenom v případě, že jsou plně důvěryhodní. Příkladem může být plocha chráněného přihlašování, kde se můžou spouštět jenom známé a důvěryhodné aplikace.

- Vývojáři zprostředkovatelů automatizace uživatelského rozhraní by si měli být vědomi, že všechny informace, které zvolí k vystavení v ovládacích prvcích prostřednictvím [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jsou v podstatě veřejné a plně přístupné pro jiný kód. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] neposkytuje žádné úsilí k určení věrohodnosti libovolného klienta automatizace uživatelského rozhraní, a proto by zprostředkovatel automatizace uživatelského rozhraní neměl zveřejnit chráněný obsah nebo citlivé textové informace (například pole hesla).

- Jednou z nejvýznamnějších změn v zabezpečení pro systém Windows Vista je široce označovaná jako "zabezpečený vstup", který zahrnuje technologie, jako jsou například minimální privilegované (nebo omezené) uživatelské účty (LUA) a izolace úrovně oprávnění uživatelského rozhraní (UIPI).

  - UIPI zabrání jednomu programu v řízení a/nebo sledovat další "privilegovaný" program, který znemožňuje útokům prostřednictvím zpráv v okně mezi procesy, které jsou falešné na vstupu uživatele.

  - LUA nastaví omezení pro oprávnění aplikací, které používají uživatelé ve skupině Administrators. Aplikace nemusí nutně mít oprávnění správce, ale místo toho se spustí s nejmenšími potřebnými oprávněními. V důsledku toho můžou být v LUA scénářích vynutila určitá omezení. Nejpřesnější zkracování řetězců (včetně řetězců TextPattern), kde může být nutné omezit velikost řetězců načítaných z aplikací na úrovni správce, aby nemusely přidělovat paměť k bodu zakázání aplikace.

<a name="Performance"></a>

## <a name="performance"></a>Výkon

Vzhledem k tomu, že TextPattern spoléhá na většinu funkcí volání mezi procesy, neposkytuje mechanismus ukládání do mezipaměti za účelem zvýšení výkonu při zpracování obsahu. To je na rozdíl od jiných vzorů ovládacích prvků v [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)], ke kterým lze přistupovat pomocí metod <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>.

Jedním z cílem pro zlepšení výkonu je zajištění, že se klienti automatizace uživatelského rozhraní snaží načíst střední bloky textu pomocí <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>. Například volání GetText (1) bude mít za následek přístupy mezi procesy pro každý znak, zatímco jedno volání GetText (-1) bude mít za následek jeden z přístupů mezi procesy, ale může mít vysokou latenci v závislosti na velikosti poskytovatele textu.

<a name="Glossary"></a>

## <a name="textpattern-terminology"></a>Terminologie TextPattern

\ **atributu**
Formátování charakteristické oblasti textu (například <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> nebo <xref:System.Windows.Automation.TextPattern.FontNameAttribute>).

**Degenerovat\ rozsahu**
Negenerovaný rozsah je prázdný text nebo textový rozsah s nulovým znakem. Pro účely vzoru ovládacího prvku TextPattern je textový kurzor (nebo systémový blikající kurzor) považován za negenerovaný rozsah. Pokud není vybraný žádný text, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> by vrátil v místě vložení degenerovaný rozsah a <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> by vrátil jako počáteční koncový bod degenerovaný rozsah. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> a <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> mohou vracet degenerované rozsahy, pokud poskytovatel textu nemůže najít žádné oblasti textu, které odpovídají dané podmínce. Tento degenerovaný rozsah lze použít jako počáteční koncový bod v rámci poskytovatele textu. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A> a <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> vrátí nulový odkaz (`Nothing` v Microsoft Visual Basic .NET), aby nedocházelo k záměně se zjištěným rozsahem oproti negenerovanému rozsahu.

\ **vloženého objektu**
V modelu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ho textu existují dva typy vložených objektů. Jsou tvořeny textovými prvky obsahu, jako jsou hypertextové odkazy nebo tabulky, a ovládací prvky, jako jsou obrázky a tlačítka. Podrobnější informace najdete v tématu [přístup k vloženým objektům pomocí automatizace uživatelského rozhraní](access-embedded-objects-using-ui-automation.md).

\ **koncového bodu**
Absolutní <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> nebo bod <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> oblasti textu v rámci textového kontejneru.

![TextPatternRangeEndpoints &#40;začátek a konec&#41;.](./media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints")
Následující příklad ilustruje sadu počátečních a koncových bodů.

**TextRange**\
Reprezentace rozsahu textu s počátečním a koncovým bodem v kontejneru textu včetně všech přidružených atributů a funkcí.

<xref:System.Windows.Automation.Text.TextUnit>\
Předem definovaná jednotka textu (znak, Word, řádek nebo odstavec), která se používá k procházení logických segmentů textového rozsahu.

## <a name="see-also"></a>Viz také:

- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md)
- [Text Services Framework](/windows/desktop/api/_tsf/)
