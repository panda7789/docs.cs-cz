---
title: Přehled prvku TextPattern automatizace uživatelského rozhraní
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, TextPattern class
- TextPattern class
- classes, TextPattern
ms.assetid: 41787927-df1f-4f4a-aba3-641662854fc4
author: Xansky
ms.author: mhopkins
ms.openlocfilehash: 884bf82c81f30c51dec8a70131e7bfb0a392e809
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352822"
---
# <a name="ui-automation-textpattern-overview"></a>Přehled prvku TextPattern automatizace uživatelského rozhraní

> [!NOTE]
> Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů. Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).

Tento přehled popisuje způsob použití [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] vystavit textový obsah, včetně atributů formátu a styl textových ovládacích prvků v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]– podporované platformy. Tyto ovládací prvky patří, ale nejsou omezené na rozhraní Microsoft .NET Framework <xref:System.Windows.Controls.TextBox> a <xref:System.Windows.Controls.RichTextBox> stejně jako jejich [!INCLUDE[TLA2#tla_win32](../../../includes/tla2sharptla-win32-md.md)] ekvivalenty.

Vystavení textový obsah ovládacího prvku se provádí prostřednictvím <xref:System.Windows.Automation.TextPattern> vzor ovládacích prvků, které představuje obsah zásobník textu jako textového datového proudu. Pak <xref:System.Windows.Automation.TextPattern> vyžaduje podporu <xref:System.Windows.Automation.Text.TextPatternRange> třídy k vystavení atributů formátu a stylu. <xref:System.Windows.Automation.Text.TextPatternRange> podporuje <xref:System.Windows.Automation.TextPattern> představující souvislý nebo více nesouvislé rozpětí textu v kontejneru text se do kolekce <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> a <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> koncových bodů. <xref:System.Windows.Automation.Text.TextPatternRange> podporuje funkce, jako je například výběr, porovnání, načítání a procházení.

> [!NOTE]
> <xref:System.Windows.Automation.TextPattern> Třídy neposkytují prostředky vložit nebo upravit text. Nicméně, v závislosti na ovládací prvek, to může udělat [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] <xref:System.Windows.Automation.ValuePattern> nebo prostřednictvím vstup z klávesnice s přímým přístupem. Zobrazit [ukázka vložení textu TextPattern](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/InsertText) příklad.

Popsané v tomto přehledu funkce je potřeba technologie pro usnadnění dodavateli a koncovým uživatelům. Můžete použít technologie pro usnadnění [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] shromažďování úplné informace pro uživatele pro formátování textu a poskytují programově řízená navigace a výběr textu pomocí <xref:System.Windows.Automation.Text.TextUnit> (znak, word, řádku nebo odstavce).

<a name="UI_Automation_TextPattern_vs__Cicero"></a>

## <a name="ui-automation-textpattern-vs-text-services-framework"></a>Vs prvku TextPattern automatizace uživatelského rozhraní. Text Services Framework

[!INCLUDE[TLA#tla_tsf](../../../includes/tlasharptla-tsf-md.md)] je snadné a škálovatelné systému architektura, která umožňuje služby přirozeného jazyka a pokročilé textového zadání na ploše a v rámci aplikace. Kromě toho, že rozhraní pro aplikace k vystavení jejich text úložiště podporuje také metadat pro toto úložiště text.

Ale [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] je navržená pro aplikace, které potřebují vložit vstup do scénáře s ohledem na kontextu, vzhledem k tomu <xref:System.Windows.Automation.TextPattern> je řešení jen pro čtení (s omezenou řešení, jak je uvedeno nahoře) určená k poskytování optimalizované přístup k úložišti text pro čtečky obrazovky a zařízení Braillovo písmo.

Stručně řečeno, můžete použít dostupné technologie, které vyžadují přístup jen pro čtení do úložiště text <xref:System.Windows.Automation.TextPattern>, ale bude složitější funkce [!INCLUDE[TLA2#tla_tsf](../../../includes/tla2sharptla-tsf-md.md)] pro vstup s ohledem na kontextu.

<a name="Control_Types"></a>

## <a name="control-types"></a>Typy ovládacích prvků

#### <a name="text"></a>Text

Ovládací prvek textu je základní prvek představující část textu na obrazovce.

Ovládací prvek textového samostatné může sloužit jako popisek nebo statický text ve formuláři. Textových ovládacích prvků mohou být také umístěny ve struktuře <xref:System.Windows.Automation.ControlType.ListItem>, <xref:System.Windows.Automation.ControlType.TreeItem> nebo <xref:System.Windows.Automation.ControlType.DataItem>.

> [!NOTE]
> Textových ovládacích prvků se nemusí zobrazit v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu (viz [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)). Je to proto textových ovládacích prvků se často zobrazují jiného ovládacího prvku pomocí vlastnosti Name. Například text, který se používá k označení ovládacího prvku pro úpravy je přístupný prostřednictvím vlastnosti název ovládacích prvků pro úpravy. Vzhledem k tomu, že je ovládací prvek pro úpravy v zobrazení obsahu [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu, není nutné pro text elementu samotného v tomto zobrazení [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu. Pouze text, který se zobrazí v zobrazení obsahu je text, který není nadbytečné informace. Díky všechny technologie pro usnadnění rychle vyfiltrovat pouze na řadu informací jejich uživatelé potřebují.

#### <a name="edit"></a>Upravit

Upravte ovládací prvky povolit uživatelům zobrazení a úprava jeden řádek textu.

> [!NOTE]
> Jeden řádek textu může obtékat v některých scénářích rozložení.

#### <a name="document"></a>Dokument

Ovládacích prvků dokumentu může uživatel procházet a získávání informací z více stránek textu.

<a name="TextPattern_Client_API_s"></a>

## <a name="textpattern-client-apis"></a>TextPattern klientských rozhraní API

|||
|-|-|
|`System.Windows.Automation.TextPattern Class`|Vstupní bod pro [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] textový model.<br /><br /> Tato třída také obsahuje dva <xref:System.Windows.Automation.TextPattern> naslouchacích procesů událostí <xref:System.Windows.Automation.TextPattern.TextSelectionChangedEvent> a <xref:System.Windows.Automation.TextPattern.TextChangedEvent>.|
|`System.Windows.Automation.Text.TextPatternRange Class`|Reprezentace rozpětí textu v rámci zásobník textu, který podporuje <xref:System.Windows.Automation.TextPattern>.<br /><br /> Klienti automatizace uživatelského rozhraní by měl být opatrní při aktuální platnosti rozsah textu vytvořené pomocí <xref:System.Windows.Automation.Text.TextPatternRange>. Pokud původní text v ovládacím prvku text je zcela nahrazena novým textem, aktuální rozsah textu se stanou neplatnými. Ale rozsah textu mohou mít i nadále některé odříznutí Pokud pouze část původní text se změní a základní ovládací prvek textu spravuje jeho textu "ukazatel" s ukotvení (nebo na koncové body), nikoli s umístěním absolutní znak.<br /><br /> Klienti může naslouchat <xref:System.Windows.Automation.TextPattern.TextChangedEvent> pro oznámení o všech změnách textový obsah pracují s.|
|`System.Windows.Automation.AutomationTextAttribute Class`|Používá k identifikaci formátování atributy rozsah textu.|

<a name="TextPattern_Provider_API_s"></a>

## <a name="textpattern-provider-apis"></a>Rozhraní API poskytovatele vlastnosti TextPattern

Prvky uživatelského rozhraní nebo ovládací prvky, které podporují <xref:System.Windows.Automation.TextPattern> implementací <xref:System.Windows.Automation.Provider.ITextProvider> a <xref:System.Windows.Automation.Provider.ITextRangeProvider> rozhraní, buď nativně nebo prostřednictvím [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] proxy servery, dokáží zveřejnění informací o podrobné atributu pro jakýkoli text, který obsahují v Přidání robustního navigační zajišťuje.

A <xref:System.Windows.Automation.TextPattern> poskytovatele nemusí podporovat všechny atributy textu, pokud ovládací prvek nemá podporu pro všemi konkrétní atributy.

A <xref:System.Windows.Automation.TextPattern> musí podporovat zprostředkovatele <xref:System.Windows.Automation.TextPattern.GetSelection%2A> a <xref:System.Windows.Automation.Text.TextPatternRange.Select%2A> funkcí, pokud ovládací prvek podporuje výběr textu nebo umístění kurzoru text (nebo stříšku system) v rámci části textu. Pokud ovládací prvek nepodporuje tuto funkci následně nemusí podporovat některé z těchto metod. Ale ovládací prvek musí vystavit typu podporuje implementací výběr textu <xref:System.Windows.Automation.Provider.ITextProvider.SupportedTextSelection%2A> vlastnost.

A <xref:System.Windows.Automation.TextPattern> zprostředkovatele musí podporovat vždy <xref:System.Windows.Automation.Text.TextUnit> konstanty <xref:System.Windows.Automation.Text.TextUnit.Character> a <xref:System.Windows.Automation.Text.TextUnit.Document> stejně jako jakýkoli jiný <xref:System.Windows.Automation.Text.TextUnit> konstanty je schopný zajistit podporu.

> [!NOTE]
> Poskytovatel může přeskočit podporu pro konkrétní <xref:System.Windows.Automation.Text.TextUnit> odložením na další největší <xref:System.Windows.Automation.Text.TextUnit> podporované v následujícím pořadí: <xref:System.Windows.Automation.Text.TextUnit.Character>, <xref:System.Windows.Automation.Text.TextUnit.Format>, <xref:System.Windows.Automation.Text.TextUnit.Word>, <xref:System.Windows.Automation.Text.TextUnit.Line>, <xref:System.Windows.Automation.Text.TextUnit.Paragraph>, <xref:System.Windows.Automation.Text.TextUnit.Page>, a <xref:System.Windows.Automation.Text.TextUnit.Document> .

|||
|-|-|
|`ITextProvider Interface`|Poskytuje metody, vlastnosti a atributy, které podporují <xref:System.Windows.Automation.TextPattern> v klientských aplikacích (viz <xref:System.Windows.Automation.Provider.ITextProvider>).|
|`ITextRangeProvider Interface`|Reprezentuje rozpětí textu ve zprostředkovateli text (viz <xref:System.Windows.Automation.Provider.ITextRangeProvider>).|
|`System.Windows.Automation.TextPatternIdentifiers Class`|Obsahuje hodnoty, které jsou použity jako identifikátory pro poskytovatele textu (viz <xref:System.Windows.Automation.TextPatternIdentifiers>).|

<a name="Security"></a>
## <a name="security"></a>Zabezpečení
 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] Architektura je navržená s ohledem na bezpečnost (viz [Přehled zabezpečení automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-security-overview.md)). TextPattern třídy je popsáno v tomto přehledu ale vyžadovat některé specifické aspekty zabezpečení.

- [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] poskytovatelé text zadat jen pro čtení rozhraní a neposkytuje možnost měnit existující text v ovládacím prvku.

- Klienti automatizace uživatelského rozhraní lze použít pouze [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] případě, že jsou plně "důvěryhodné". Příklad tohoto by chráněné přihlašování, kde lze spustit pouze známé a důvěryhodné aplikace.

- Vývojáři zprostředkovatelů automatizace uživatelského rozhraní byste si být vědomi, že všechny informace se rozhodnete vystavit v jeho ovládání pomocí [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] je v podstatě veřejné a plně přístupná jiným kódem. [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] nevyvine žádnou akci k určení, že důvěryhodnost jakékoliv klienty automatizace uživatelského rozhraní a proto zprostředkovatele automatizace uživatelského rozhraní by neměly zveřejňovat chráněného obsahu nebo citlivých textové informace (například pole s heslem).

- Jeden z nejvýznamnějších změn v zabezpečení pro [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] je široce označovány jako "Zabezpečené Input" zahrnující technologie, jako je nejnižší úrovní oprávnění (nebo omezené) uživatelské účty (LUA) a uživatelského rozhraní oprávnění úroveň izolace (UIPI).

    - UIPI brání jeden program od řízení nebo monitorování druhého další "privilegovaných" program, prevence útoků zprávy okna procesy, které falšují vstup uživatele.

    - LUA nastavuje omezení oprávnění aplikací spuštěných uživatelů ve skupině Administrators. Aplikace nemusí mít oprávnění správce, ale místo toho spustí s nejmenší možná oprávnění. V důsledku toho může být určitá omezení prosazuje LUA scénáře. Zkrácení (včetně TextPattern řetězce), kde může být potřeba omezit velikost řetězce načítají z aplikací na úrovni správce, nejsou vynucené přidělení paměti pro bod zakázání aplikace zejména řetězce.

<a name="Performance"></a>

## <a name="performance"></a>Výkon

Protože TextPattern závisí na mezi procesní volání pro většinu jeho funkcí, neposkytuje mechanismus ukládání do mezipaměti ke zlepšení výkonu při zpracování obsahu. Jde na rozdíl od jiných vzorů ovládacích prvků v [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] , které lze přistupovat pomocí <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> metody.

Jeden taktika pro zlepšení výkonu je zajistit, klienti automatizace uživatelského rozhraní se pokoušejí o načtení středně velikých bloky textu s využitím <xref:System.Windows.Automation.Text.TextPatternRange.GetText%2A>. Například GetText(1) volání bude mít za následek přístupy mezi procesy pro každý znak že GetText(-1) volání bude mít za následek jeden položek mezi procesy, ale může mít vysokou latenci v závislosti na velikosti poskytovatele textu.

<a name="Glossary"></a>

## <a name="textpattern-terminology"></a>TextPattern terminologie

**Atribut** formátování charakteristiku rozsah textu (například <xref:System.Windows.Automation.TextPattern.IsItalicAttribute> nebo <xref:System.Windows.Automation.TextPattern.FontNameAttribute>).

**Rozsah degenerovanou dimenzi** degenerovanou rozsah je rozsah textu znaku nula nebo prázdná. Pro účely TextPattern vzoru ovládacích prvků považuje textový kurzor (nebo stříšku systému) degenerovanou rozsahu. Pokud není vybraný žádný text, <xref:System.Windows.Automation.TextPattern.GetSelection%2A> vracel degenerovanou rozsahu na pozici kurzoru text a <xref:System.Windows.Automation.TextPattern.RangeFromPoint%2A> vracel degenerovanou rozsahu jako svůj výchozí koncový bod. <xref:System.Windows.Automation.TextPattern.RangeFromChild%2A> a <xref:System.Windows.Automation.TextPattern.GetVisibleRanges%2A> může vracet degenerovanou rozsahy poskytovatele textu nelze nalézt žádné oblasti textu, které odpovídají dané podmínce. Tento rozsah degenerovanou může sloužit jako výchozí koncový bod v rámci poskytovatele textu. <xref:System.Windows.Automation.Text.TextPatternRange.FindText%2A> a <xref:System.Windows.Automation.Text.TextPatternRange.FindAttribute%2A> vrácen nulový odkaz (`Nothing` v aplikaci Microsoft Visual Basic .NET) aby nedocházelo k záměnám s celou zjištěných oproti degenerovanou rozsahu.

**Vložený objekt** existují dva typy vložené objekty v [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] textový model. Skládají se z textového obsahu prvky, jako jsou hypertextové odkazy nebo tabulky a ovládací prvky jako obrázky a tlačítka. Další informace najdete v tématu [přístup vložené objekty pomocí automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/access-embedded-objects-using-ui-automation.md).

**Koncový bod** absolutní <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.Start> nebo <xref:System.Windows.Automation.Text.TextPatternRangeEndpoint.End> bod rozsah textu v rámci zásobník textu.

![Výčty TextPatternRangeEndpoint &#40;počáteční a koncové&#41;. ](../../../docs/framework/ui-automation/media/uia-textpattern-endpoints.PNG "UIA_TextPattern_Endpoints") následující obrázek znázorňuje sadu počátečního a koncového bodu.

**TextRange** reprezentace rozpětí textu, počáteční a koncový bod v zásobník textu, včetně všech přidružených atributů a funkce.

<xref:System.Windows.Automation.Text.TextUnit> Předdefinované jednotka text (znak, word, řádku nebo odstavce) použitý pro navigaci v logických segmentů rozsah textu.

## <a name="see-also"></a>Viz také:

- [Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
- [Přehled vzorů ovládacích prvků pro automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)
- [Přehled stromu automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)
- [Použití mezipaměti při automatizaci uživatelského rozhraní](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [Podpora vzorů ovládacích prvků u zprostředkovatele automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)
- [Mapování vzorů ovládacích prvků pro klienty automatizace uživatelského rozhraní](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md)
- [Text Services Framework](/windows/desktop/api/_tsf/)
