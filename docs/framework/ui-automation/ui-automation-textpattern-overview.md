---
title: Přehled prvku TextPattern automatizace uživatelského rozhraní
description: Přečtěte si přehled vzoru ovládacího prvku TextPattern v automatizaci uživatelského rozhraní. Tento řídicí vzor zpřístupňuje textový obsah ovládacího prvku, včetně formátů a stylu.
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
ms.openlocfilehash: 986b601bbd212582c09c559a9bb22983ba59fa17
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924666"
---
# <a name="ui-automation-textpattern-overview"></a>Přehled prvku TextPattern automatizace uživatelského rozhraní

> [!NOTE]
> Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).

Tento přehled popisuje, jak použít [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] k vystavení textového obsahu, včetně atributů formátu a stylu pro textové ovládací prvky v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] podporovaných platformách. Tyto ovládací prvky zahrnují, ale nejsou omezeny na, .NET Framework <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox> také na jejich ekvivalenty Win32.

Vystavení textového obsahu ovládacího prvku je provedeno pomocí <xref:System.Windows.Automation.TextPattern> vzoru ovládacího prvku, který představuje obsah kontejneru textu jako textový Stream. Zase vyžaduje, aby <xref:System.Windows.Automation.TextPattern> Podpora <xref:System.Windows.Automation.Text.TextPatternRange> třídy zveřejnila atributy formátu a stylu. <xref:System.Windows.Automation.Text.TextPatternRange>podporuje <xref:System.Windows.Automation.TextPattern> zastupuje souvislý nebo vícenásobný nesouvislý text v kontejneru textu s kolekcí <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> a <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> koncovými body. <xref:System.Windows.Automation.Text.TextPatternRange>podporuje funkce, jako je výběr, porovnání, načítání a procházení.

> [!NOTE]
> <xref:System.Windows.Automation.TextPattern>Třídy neposkytují prostředky pro vložení nebo úpravu textu. V závislosti na ovládacím prvku však může být k [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> diskrok přímo vstup klávesnice nebo. Příklad naleznete v [ukázce TextPattern INSERT text](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText) .

Funkce popsané v tomto přehledu jsou důležité pro dodavatele s asistenčními technologiemi a jejich koncové uživatele. Technologie usnadnění můžou využít [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] ke shromažďování úplných informací o formátování textu pro uživatele a poskytovat programovou navigaci a výběr textu podle <xref:System.Windows.Automation.Text.TextUnit> (znak, Word, řádek nebo odstavec).

<a name="UI_Automation_TextPattern_vs__Cicero"></a>

## <a name="ui-automation-textpattern-vs-text-services-framework"></a>ROZHRANÍ .NET Automation TextPattern vs. Text Services Framework

Rozhraní TSF (text Services Framework) je jednoduché a škálovatelné systémové rozhraní, které umožňuje využívat služby přirozeného jazyka a pokročilý Textový vstup na ploše a v aplikacích. Kromě poskytování rozhraní pro aplikace k zveřejnění jejich textového úložiště podporuje také metadata pro toto úložiště textu.

Služba TSF však byla navržena pro aplikace, které vyžadují vložení vstupu do kontextových scénářů, zatímco <xref:System.Windows.Automation.TextPattern> je řešení jen pro čtení (s výše uvedeným omezením) určeno k zajištění optimalizovaného přístupu k úložišti textu pro čtečky obrazovky a zařízení Braillova písma.

V krátkých, přístupných technologiích, které vyžadují přístup k úložišti textu jen pro čtení, může používat <xref:System.Windows.Automation.TextPattern> , ale budou potřebovat složitější funkce TSF pro kontext podporující kontext.

<a name="Control_Types"></a>

## <a name="control-types"></a>Typy ovládacích prvků

### <a name="text"></a>Text

Textový ovládací prvek je základní prvek reprezentující text na obrazovce.

Samostatný ovládací prvek textu lze použít jako popisek nebo statický text na formuláři. Textové ovládací prvky mohou být také obsaženy v rámci struktury <xref:System.Windows.Automation.ControlType.ListItem> <xref:System.Windows.Automation.ControlType.TreeItem> nebo <xref:System.Windows.Automation.ControlType.DataItem> .

> [!NOTE]
> Textové ovládací prvky se nemusí zobrazit v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu (viz [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)). Je to proto, že textové ovládací prvky se často zobrazují prostřednictvím vlastnosti název jiného ovládacího prvku. Například text, který se používá k označení ovládacího prvku pro úpravy, je přístupný prostřednictvím vlastnosti Name ovládacího prvku pro úpravy. Vzhledem k tomu, že je ovládací prvek pro úpravy v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, není nutné, aby byl prvek textu v tomto zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu. Jediný text, který se zobrazí v zobrazení obsahu, je text, který není redundantní informace. To umožňuje všem asistenčním technologiím rychle filtrovat pouze ty informace, které jejich uživatelé potřebují.

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
|`System.Windows.Automation.TextPattern Class`|Vstupní bod pro [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] textový model.<br /><br /> Tato třída také obsahuje dva <xref:System.Windows.Automation.TextPattern> naslouchací procesy pro události <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> a <xref:System.Windows.Automation.TextPattern.TextChangedEvent> .|
|`System.Windows.Automation.Text.TextPatternRange Class`|Reprezentace rozsahu textu v rámci kontejneru textu, který podporuje <xref:System.Windows.Automation.TextPattern> .<br /><br /> Klienti automatizace uživatelského rozhraní by měli mít pozor na aktuální platnosti rozsahu textu vytvořeného pomocí <xref:System.Windows.Automation.Text.TextPatternRange> . Pokud je původní text v ovládacím prvku text úplně nahrazen novým textem, aktuální rozsah textu se změní na neplatný. Rozsah textu ale může mít i určitou životaschopnost, pokud se změní jenom část původního textu a podkladový ovládací prvek textu spravuje svůj text "ukazatel" s kotvami (nebo koncovými body) místo s absolutním umístěním znaků.<br /><br /> Klienti mohou naslouchat <xref:System.Windows.Automation.TextPattern.TextChangedEvent> oznámením o změnách v textovém obsahu, se kterými pracují.|
|`System.Windows.Automation.AutomationTextAttribute Class`|Slouží k identifikaci formátovacích atributů oblasti textu.|

<a name="TextPattern_Provider_API_s"></a>

## <a name="textpattern-provider-apis"></a>Rozhraní API pro poskytovatele TextPattern

Prvky uživatelského rozhraní nebo ovládací prvky, které podporují <xref:System.Windows.Automation.TextPattern> implementaci <xref:System.Windows.Automation.Provider.ITextProvider> <xref:System.Windows.Automation.Provider.ITextRangeProvider> rozhraní a, a to buď nativně nebo prostřednictvím [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] proxy, jsou schopné vystavit podrobné informace o atributu pro libovolný text, který obsahuje kromě poskytování robustních navigačních možností.

<xref:System.Windows.Automation.TextPattern>Pokud ovládací prvek nemá podporu pro všechny konkrétní atributy, není nutné podporovat všechny atributy textu.

<xref:System.Windows.Automation.TextPattern>Zprostředkovatel musí podporovat <xref:System.Windows.Automation.TextPattern.GetSelection%2A> funkce a, <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> Pokud ovládací prvek podporuje výběr textu nebo umístění textového kurzoru (nebo systémového kurzoru) v oblasti textu. Pokud ovládací prvek tuto funkci nepodporuje, nemusí podporovat žádnou z těchto metod. Ovládací prvek však musí vystavit typ výběru textu, který podporuje implementací <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> Vlastnosti.

<xref:System.Windows.Automation.TextPattern>Poskytovatel musí vždy podporovat <xref:System.Windows.Automation.Text.TextUnit> konstanty <xref:System.Windows.Automation.Text.TextUnit.Character> a <xref:System.Windows.Automation.Text.TextUnit.Document> i jakékoli jiné <xref:System.Windows.Automation.Text.TextUnit> konstanty, které podporuje.

> [!NOTE]
> Poskytovatel může přeskočit podporu konkrétního typu <xref:System.Windows.Automation.Text.TextUnit> odložením na další největší <xref:System.Windows.Automation.Text.TextUnit> podporované v následujícím pořadí: <xref:System.Windows.Automation.Text.TextUnit.Character> , <xref:System.Windows.Automation.Text.TextUnit.Format> , <xref:System.Windows.Automation.Text.TextUnit.Word> , <xref:System.Windows.Automation.Text.TextUnit.Line> , <xref:System.Windows.Automation.Text.TextUnit.Paragraph> , <xref:System.Windows.Automation.Text.TextUnit.Page> a <xref:System.Windows.Automation.Text.TextUnit.Document> .

|||
|-|-|
|`ITextProvider Interface`|Zpřístupňuje metody, vlastnosti a atributy, které podporují <xref:System.Windows.Automation.TextPattern> klientské aplikace (viz <xref:System.Windows.Automation.Provider.ITextProvider> ).|
|`ITextRangeProvider Interface`|Představuje rozsah textu v poskytovateli textu (viz <xref:System.Windows.Automation.Provider.ITextRangeProvider> ).|
|`System.Windows.Automation.TextPatternIdentifiers Class`|Obsahuje hodnoty, které se používají jako identifikátory pro poskytovatele textu (viz <xref:System.Windows.Automation.TextPatternIdentifiers> ).|

<a name="Security"></a>

## <a name="security"></a>Zabezpečení

[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]Architektura byla navržena s ohledem na zabezpečení (viz [Přehled zabezpečení automatizace uživatelského rozhraní](ui-automation-security-overview.md)). Třídy TextPattern popsané v tomto přehledu ale vyžadují určité konkrétní požadavky na zabezpečení.

- [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]poskytovatelé textu poskytují rozhraní jen pro čtení a neposkytují možnost měnit stávající text v ovládacím prvku.

- Klienti automatizace uživatelského rozhraní můžou použít jenom v případě, že [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jsou plně důvěryhodní. Příkladem může být plocha chráněného přihlašování, kde se můžou spouštět jenom známé a důvěryhodné aplikace.

- Vývojáři zprostředkovatelů automatizace uživatelského rozhraní by si měli být vědomi, že všechny informace, které zvolí k zveřejnění ve svých ovládacích prvcích, [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] jsou v podstatě veřejné a plně přístupné pro jiný kód. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]nevyužívá žádné úsilí k určení věrohodnosti libovolného klienta automatizace uživatelského rozhraní a proto by zprostředkovatel automatizace uživatelského rozhraní neměl zveřejnit chráněný obsah nebo citlivé textové informace (například pole hesla).

- Jednou z nejvýznamnějších změn v zabezpečení pro systém Windows Vista je široce označovaná jako "zabezpečený vstup", který zahrnuje technologie, jako jsou například minimální privilegované (nebo omezené) uživatelské účty (LUA) a izolace úrovně oprávnění uživatelského rozhraní (UIPI).

  - UIPI zabrání jednomu programu v řízení a/nebo sledovat další "privilegovaný" program, který znemožňuje útokům prostřednictvím zpráv v okně mezi procesy, které jsou falešné na vstupu uživatele.

  - LUA nastaví omezení pro oprávnění aplikací, které používají uživatelé ve skupině Administrators. Aplikace nemusí nutně mít oprávnění správce, ale místo toho se spustí s nejmenšími potřebnými oprávněními. V důsledku toho můžou být v LUA scénářích vynutila určitá omezení. Nejpřesnější zkracování řetězců (včetně řetězců TextPattern), kde může být nutné omezit velikost řetězců načítaných z aplikací na úrovni správce, aby nemusely přidělovat paměť k bodu zakázání aplikace.

<a name="Performance"></a>

## <a name="performance"></a>Výkon

Vzhledem k tomu, že TextPattern spoléhá na většinu funkcí volání mezi procesy, neposkytuje mechanismus ukládání do mezipaměti za účelem zvýšení výkonu při zpracování obsahu. To se podobá jiným vzorům ovládacích prvků [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , které jsou k dispozici pomocí <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> metod nebo.

Jedním z cílem pro zlepšení výkonu je zajištění, že se klienti služby automatizace uživatelského rozhraní pokoušejí načíst středně velké bloky textu pomocí <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A> . Například volání GetText (1) bude mít za následek přístupy mezi procesy pro každý znak, zatímco jedno volání GetText (-1) bude mít za následek jeden z přístupů mezi procesy, ale může mít vysokou latenci v závislosti na velikosti poskytovatele textu.

<a name="Glossary"></a>

## <a name="textpattern-terminology"></a>Terminologie TextPattern

**Přidělen**\
Formátování charakteristické oblasti textu (například <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> nebo <xref:System.Windows.Automation.TextPattern.FontNameAttribute> ).

**Vygenerovat rozsah**\
Negenerovaný rozsah je prázdný text nebo textový rozsah s nulovým znakem. Pro účely vzoru ovládacího prvku TextPattern je textový kurzor (nebo systémový blikající kurzor) považován za negenerovaný rozsah. Pokud není vybraný žádný text, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> vrátí v místě vložení degenerovaný rozsah a <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> vrátí jako svůj počáteční koncový bod degenerovaný rozsah. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A>a <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> můžou vracet degenerované rozsahy, když poskytovatel textu nemůže najít žádné oblasti textu, které odpovídají dané podmínce. Tento degenerovaný rozsah lze použít jako počáteční koncový bod v rámci poskytovatele textu. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A>a <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> vrátit odkaz s hodnotou null ( `Nothing` v Microsoft Visual Basic .NET), aby nedocházelo k záměně se zjištěným rozsahem oproti negenerovanému rozsahu.

**Vložený objekt**\
V textovém modelu existují dva typy vložených objektů [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] . Jsou tvořeny textovými prvky obsahu, jako jsou hypertextové odkazy nebo tabulky, a ovládací prvky, jako jsou obrázky a tlačítka. Podrobnější informace najdete v tématu [přístup k vloženým objektům pomocí automatizace uživatelského rozhraní](access-embedded-objects-using-ui-automation.md).

**Služba**\
Absolutní <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> nebo <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> bodová oblast textu v rámci textového kontejneru.

![TextPatternRangeEndpoints &#40;Start a end&#41;.](./media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints")
Následující příklad ilustruje sadu počátečních a koncových bodů.

**TextRange**\
Reprezentace rozsahu textu s počátečním a koncovým bodem v kontejneru textu včetně všech přidružených atributů a funkcí.

<xref:System.Windows.Automation.Text.TextUnit>\
Předem definovaná jednotka textu (znak, Word, řádek nebo odstavec), která se používá k procházení logických segmentů textového rozsahu.

## <a name="see-also"></a>Viz také

- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](ui-automation-control-patterns-for-clients.md)
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](ui-automation-control-patterns-overview.md)
- [Přehled stromu automatizace uživatelského rozhraní](ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](use-caching-in-ui-automation.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](support-control-patterns-in-a-ui-automation-provider.md)
- [Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní](control-pattern-mapping-for-ui-automation-clients.md)
- [Rozhraní Text Services Framework](/windows/desktop/api/_tsf/)
