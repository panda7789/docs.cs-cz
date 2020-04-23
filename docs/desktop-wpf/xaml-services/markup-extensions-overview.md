---
title: Přehled rozšíření značek pro jazyk XAML
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: c0ca8e7d0d68d4730173385540cbcec66c7bf03a
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071715"
---
# <a name="overview-of-markup-extensions-for-xaml"></a>Přehled rozšíření značek pro XAML

Rozšíření značek jsou xaml technika pro získání hodnoty, která není primitivní nebo konkrétní typ XAML. Pro použití atributů rozšíření značek použít známé posloupnosti `{` znaků otevření složené závorky pro zadání `}` oboru rozšíření značky a uzavření složených složených složených znaků k ukončení. Při použití služby .NET XAML services můžete použít některá předdefinovaná rozšíření značek jazyka XAML ze sestavení System.Xaml. Můžete také podtřídy <xref:System.Windows.Markup.MarkupExtension> z třídy, definované v System.Xaml a definovat vlastní rozšíření značky. Nebo můžete použít rozšíření značek definované konkrétní rámec, pokud již odkazujete na tento rámec.

Při použití rozšíření značky je přístupná, zapisovač objektů <xref:System.Windows.Markup.MarkupExtension> XAML může poskytovat <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> služby vlastní třídy prostřednictvím spojovacího bodu služby v přepsání. Služby lze získat kontext o využití, konkrétní možnosti zapisovačobjektu, kontext schématu XAML a tak dále.

## <a name="xaml-defined-markup-extensions"></a>Rozšíření značek definovaná XAML

Několik rozšíření značek implementuje služba .NET XAML Services pro jazykovou podporu XAML. Tato rozšíření značek odpovídají části specifikace XAML jako jazyk. Ty jsou obvykle identifikovatelné `x:` podle předpony v syntaxi, jak je vidět v běžném použití. Implementace služby .NET XAML services pro tyto elementy jazyka XAML jsou odvozeny <xref:System.Windows.Markup.MarkupExtension> ze základní třídy.

> [!NOTE]
> Předpona se `x:` používá pro typické mapování oboru názvů XAML v oboru názvů jazyka XAML v kořenovém prvku produkce XAML. Například projekt visual studio a šablony stránek pro různé specifické architektury iniciovat soubor XAML pomocí tohoto `x:` mapování. Ve vlastním mapování oboru názvů XAML můžete zvolit jiný token předpony, `x:` ale tato dokumentace bude předpokládat výchozí mapování jako prostředek k identifikaci těch entit, které jsou definovanou součástí oboru názvů XAML jazyka XAML, na rozdíl od výchozího oboru názvů XAML konkrétního rozhraní nebo jiných libovolných oborů názvů CLR nebo XML.

### <a name="xtype"></a>x:Text

`x:Type`dodává <xref:System.Type> objekt pro pojmenovaný typ. Tato funkce se používá nejčastěji v mechanismech odkladu, které používají základní typ CLR a odvození typu clr jako zástupný název nebo identifikátor seskupení. WPF styly a šablony a `TargetType` jejich použití vlastností, jsou konkrétním příkladem. Další informace naleznete v tématu [x:Type Markup Extension](xtype-markup-extension.md).

### <a name="xstatic"></a>x:statické

`x:Static`vytváří statické hodnoty z entit kódu typu hodnoty, které nejsou přímo typem hodnoty vlastnosti, ale mohou být vyhodnoceny pro tento typ. To je užitečné pro určení hodnot, které již existují jako dobře známé konstanty v definici typu. Další informace naleznete v tématu [x:Static Markup Extension](xstatic-markup-extension.md).

### <a name="xnull"></a>x:Null

`x:Null`určuje `null` jako hodnotu pro člen XAML. V závislosti na návrhu konkrétní typy nebo `null` na větší framework koncepty není vždy výchozí hodnota pro vlastnost nebo implicitní hodnota atributu prázdný řetězec. Další informace naleznete v tématu [x:Null Markup Extension](xnull-markup-extension.md).

### <a name="xarray"></a>x:Pole

`x:Array`podporuje vytváření obecných polí v syntaxi XAML v případech, kdy podpora kolekce, která je poskytována základními prvky a modely ovládacích prvků, se záměrně nepoužívá. Další informace naleznete v tématu [x:Array Markup Extension](xarray-markup-extension.md). V XAML 2009 konkrétně pole jsou přístupné jako jazyk primitivy namísto jako rozšíření. Další informace naleznete v tématu [XAML 2009 Language Features](xaml-2009-language-features.md).

### <a name="xreference"></a>x:Odkaz

`x:Reference`je součástí XAML 2009, rozšíření původní (2006) jazykové sady. `x:Reference`představuje odkaz na jiný existující objekt v grafu objektu. Tento objekt je `x:Name`identifikován jeho . Další informace naleznete v tématu [x:Reference Markup Extension](xreference-markup-extension.md).

### <a name="other-x-constructs"></a>Ostatní x: Konstrukce

Existují `x:` další konstrukce pro podporu funkcí jazyka XAML, ale nejsou implementovány jako rozšíření značek. Další informace naleznete v [tématu XAML Namespace (x:) Funkce jazyka](namespace-language-features.md).

## <a name="the-markupextension-base-class"></a>Základní třída MarkupExtension

Chcete-li definovat vlastní rozšíření značek, které lze interagovat s výchozí implementace čteček XAML a zapisovačů XAML v System.Xaml, odvodit třídu z abstraktní <xref:System.Windows.Markup.MarkupExtension> třídy. Tato třída má jednu metodu <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>přepsat, což je . Může být také nutné definovat další konstruktory pro podporu argumentů pro použití rozšíření značek a odpovídající nastavené vlastnosti.

Prostřednictvím <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>vlastní značky rozšíření má přístup k kontextu služby, která hlásí prostředí, kde je vyvolána rozšíření značky procesorem XAML. V cestě zatížení se obvykle <xref:System.Xaml.XamlObjectWriter>jedná o . V cestě pro uložení se <xref:System.Xaml.XamlXmlWriter>obvykle jedná o . Každý sestavu kontextu služby jako interní xaml třídy kontextu poskytovatele služeb, který implementuje vzor poskytovatele služeb. Další informace o dostupných službách a jejich verzi naleznete v [tématu Převaděče typů a rozšíření značek pro xaml](type-converters-and-markup-extensions.md).

Vaše třída rozšíření značek musí používat úroveň veřejného přístupu; XAML procesory musí být vždy schopen vytvořit instanci třídy podpory rozšíření značek, aby bylo možné používat jeho služby.

## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Definování typu podpory pro vlastní rozšíření o značky

Při použití služby .NET XAML Services nebo architektury, které jsou postaveny na .NET XAML Services, máte dvě možnosti, jak pojmenovat typ podpory rozšíření značky. Název typu je relevantní pro způsob, jakým se autoři objektů XAML pokoušejí získat přístup k typu podpory rozšíření značek a vyvolat je, když narazí na použití rozšíření značek v XAML. Použijte jednu z následujících strategií pojmenování:

- Název typu má být přesnou shodou tokenu použití značky XAML. Chcete-li například `{Collate ...}` podporovat použití rozšíření, `Collate`pojmenujte typ podpory .
- Název typu má být tokenem řetězce použití `Extension`plus příponou . Chcete-li například `{Collate ...}` podporovat použití rozšíření, `CollateExtension`pojmenujte typ podpory .

Pořadí vyhledávání je vyhledat `Extension`-suffixed název třídy první a potom vyhledejte `Extension` název třídy bez přípony.

Z hlediska použití značek, `Extension` včetně přípony jako součást použití je platný. To se však chová, jako by `Extension` skutečně součástí názvu třídy a zapisovače objektů XAML by se nepodařilo `Extension` vyřešit třídu podpory rozšíření značek pro toto použití, pokud třída podpory neměla příponu.

### <a name="the-parameterless-constructor"></a>Konstruktor bez parametrů

Pro všechny typy podpory rozšíření značek byste měli vystavit veřejný konstruktor bez parametrů. Konstruktor bez parametrů je vyžadován pro každý případ, kdy zapisovač objektu XAML inkasuje rozšíření značek z použití prvku objektu. Použití podpůrného prvku objektu je spravedlivé očekávání pro rozšíření značek, zejména pro serializaci. Rozšíření značek však můžete implementovat bez veřejného konstruktoru, pokud máte v úmyslu podporovat pouze použití atributů rozšíření značek.

Pokud vaše použití rozšíření značek nemá žádné argumenty, konstruktor bez parametrů je vyžadován pro podporu využití.

## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Vzory konstruktoru a poziční argumenty pro vlastní rozšíření značek

Pro rozšíření značek s zamýšlené použití argumentu veřejné konstruktory musí odpovídat režimy zamýšlené použití. Jinými slovy, pokud je vaše rozšíření značek navrženo tak, aby vyžadovalo jeden poziční argument jako platné použití, měli byste podporovat veřejný konstruktor s jedním vstupním parametrem, který přebírá poziční argument.

Předpokládejme například, že rozšíření `Collate` značek je určena pro podporu pouze režimu, kde existuje `CollationMode` jeden poziční argument, který představuje jeho režim, zadaný jako konstanta výčtu. V tomto případě by měl být konstruktor s následujícím formulářem:

```csharp
public Collate(CollationMode collationMode) {...}
```

Na základní úrovni argumenty předané rozšíření značky jsou řetězec, protože jsou předávány z hodnot atributů značky. Můžete vytvořit všechny řetězce argumentů a pracovat se vstupem na této úrovni. Máte však přístup k určité zpracování, ke kterému dochází před argumenty rozšíření značky jsou předány do třídy podpory.

Zpracování funguje koncepčně, jako kdyby rozšíření značek je objekt, který má být vytvořen a pak jsou nastaveny jeho členské hodnoty. Každá zadaná vlastnost, která má být nastavena, je vyhodnocena podobně jako zadaný člen lze nastavit na vytvořeném objektu při analýzě xaml. Existují dva důležité rozdíly:

- Jak již bylo uvedeno dříve, typ podpory rozšíření značek nemusí mít konstruktor bez parametrů, aby mohl být vytvořen v XAML. Jeho konstrukce objektu je odložena, dokud jeho možné argumenty v syntaxi textu jsou tokenizovány a vyhodnoceny jako poziční nebo pojmenované argumenty a příslušný konstruktor je volána v té době.
- Použití rozšíření značek lze vnořit. Nejprve je vyhodnoceno nejvnitřnější rozšíření značky. Proto můžete předpokládat takové využití a deklarovat jeden z parametrů konstrukce být typ, který vyžaduje převaděč hodnot (například rozšíření značek) k výrobě.

V předchozím příkladu bylo uvedeno spoléhání se na takové zpracování. Zapisovač objektů XAML služby .NET XAML zpracuje konstantní názvy výčtu do výčtových hodnot na nativní úrovni.

Zpracování syntaxe textu pozičního parametru rozšíření značek se může také spolehnout na převaděč typu, který je přidružen k typu, který je v argumentu konstrukce.

Argumenty se nazývají poziční argumenty, protože pořadí, ve kterém je zjištěna tokeny v použití odpovídá poziční pořadí parametrkonstruktoru, ke kterému jsou přiřazeny. Zvažte například následující podpis konstruktoru:

```csharp
public Collate(CollationMode collationMode, object collateThis) {...}
```

Procesor XAML očekává dva poziční argumenty pro toto rozšíření značek. Pokud došlo k `{Collate AlphaUp,{x:Reference circularFile}}`použití `AlphaUp` , token je odeslán a `CollationMode` vyhodnocen jako výčet s názvem konstanta. Výsledek vnitřní `x:Reference` je odeslán do druhého parametru a vyhodnocen jako objekt.

V xaml zadaných pravidel pro syntaxi rozšíření značek a zpracování čárka je oddělovač mezi argumenty, zda tyto argumenty jsou poziční argumenty nebo pojmenované argumenty.

### <a name="duplicate-arity-of-positional-arguments"></a>Duplikát arita pozičních argumentů

Pokud zapisovač objektu XAML narazí na použití rozšíření značek s pozičními argumenty a existuje více argumentů konstruktoru, které berou tento počet argumentů (duplicitní arity), to nemusí být nutně chyba. Chování závisí na přizpůsobitelném nastavení kontextu schématu XAML <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>. Pokud <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> `true`je , zapisovač objektu XAML by neměl vyvolat výjimku pouze z důvodů duplicitní aritaty. Chování za tímto bodem není přesně definováno. Základní předpoklad návrhu je, že kontext schématu obsahuje informace o typu, které jsou k dispozici pro konkrétní parametry a může se pokusit explicitní přetypování, které odpovídají duplicitní kandidáty zjistit, který podpis může být nejlepší shoda. Výjimka může být stále vyvolána, pokud žádné podpisy mohou projít testy, které jsou vynuceny tímto kontextem konkrétního schématu, který je spuštěn na zapisovači objektu XAML.

Ve výchozím <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> `false` nastavení je ve <xref:System.Xaml.XamlSchemaContext> službě CLR pro služby .NET XAML Services. Výchozí tedy <xref:System.Xaml.XamlObjectWriter> vyvolá výjimky, pokud narazí na použití rozšíření značek, kde je duplicitní arity v konstruktory typu zálohování.

## <a name="named-arguments-for-a-custom-markup-extension"></a>Pojmenované argumenty pro vlastní rozšíření značek

Značkovací rozšíření určená xaml můžete také použít formulář pojmenované argumenty pro použití. Na první úrovni tokenizace je syntaxe textu rozdělena na argumenty. Přítomnost znaménko rovná se (=) v rámci libovolného argumentu identifikuje argument jako pojmenovaný argument. Takový argument je také tokenizován do dvojice název/hodnota. Název v tomto případě pojmenuje veřejnou settable vlastnost typu podpory rozšíření značek. Pokud máte v úmyslu podporovat použití pojmenované argument, měli byste zadat tyto veřejné settable vlastnosti. Vlastnosti mohou být zděděné vlastnosti tak dlouho, dokud zůstanou veřejné.

## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Přístup k kontextu poskytovatele služeb z implementace rozšíření značek

Dostupné služby jsou stejné pro libovolný převaděč hodnot. Rozdíl je v tom, jak každý převaděč hodnoty obdrží kontext služby. Přístup ke službám a dostupným službám je popsán v tématu [Typ převaděče a Rozšíření značek pro XAML](type-converters-and-markup-extensions.md).

## <a name="property-element-usage-of-a-markup-extension"></a>Použití prvku vlastnosti rozšíření značek

Scénáře pro použití rozšíření značek jsou často navrženy kolem pomocí rozšíření značek v použití atributu. Je však také potenciálně možné definovat třídu zálohování pro podporu použití prvku vlastnosti.

Chcete-li podporovat použití prvku vlastnosti rozšíření značek, definujte veřejný konstruktor bez parametrů. To by mělo být konstruktor instance není statický konstruktor. To je nutné, protože procesor XAML musí obecně vyvolat konstruktor bez parametrů na libovolný prvek objektu, který zpracovává ze značek, a to zahrnuje třídy rozšíření značek jako prvky objektu. Pro pokročilé scénáře můžete definovat jiné než výchozí cesty konstrukce pro třídy. (Další informace naleznete v tématu [x:FactoryMethod Směrnice](xfactorymethod-directive.md).) Tyto vzory byste však neměli používat pro účely rozšíření značek, protože to ztěžuje zjišťování vzoru použití, a to jak pro návrháře, tak pro uživatele nezpracovaných značek.

## <a name="attributing-for-a-custom-markup-extension"></a>Přiřazení pro vlastní rozšíření značek

Chcete-li podporovat návrhová prostředí i určité scénáře zápisu objektů XAML, měli byste přiřadit typ podpory rozšíření značek s několika atributy CLR. Tyto atributy hlásí zamýšlené použití rozšíření značek.

 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute>hlásí <xref:System.Type> informace pro typ <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> objektu, který se vrací. Svým čistým <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> podpisem se vrací <xref:System.Object>. Různí spotřebitelé však mohou chtít přesnější informace o typu vrácení. To zahrnuje:

- Návrháři a INEŽ, kteří mohou být schopni poskytnout podporu podle typu pro použití rozšíření značek.
- Rozšířené implementace `SetMarkupExtension` obslužné rutiny na cílové třídy, které mohou spoléhat na reflexi <xref:System.Windows.Markup.MarkupExtension> k určení typu návratu rozšíření značky namísto větvení na konkrétní známé implementace podle názvu.

## <a name="serialization-of-markup-extension-usages"></a>Serializace použití rozšíření značek

Když zapisovač objektu XAML zpracuje použití rozšíření značek a zavolá <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, kontext pro jeho dříve použití rozšíření značek přetrvává v datovém proudu uzlu XAML, ale ne v grafu objektu. V grafu objektu je zachována pouze hodnota. Pokud máte scénáře návrhu nebo jiné důvody pro zachování původní ho využití rozšíření značek do serializovaného výstupu, musíte navrhnout vlastní infrastrukturu pro sledování použití rozšíření značek z datového proudu uzlu XAML načíst cestu zatížení. Můžete implementovat chování znovu prvky datového proudu uzlu z cesty zatížení a přehrát je zpět do Zapisovače XAML pro serializaci v cestě uložit, nahrazení hodnoty v příslušné pozici datového proudu uzlu.

## <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozšíření značek v datovém proudu uzlu XAML

Pokud pracujete s datovým proudem uzlu XAML na cestě zatížení, využití rozšíření značek se zobrazí v datovém proudu uzlu jako objekt.

Pokud použití rozšíření značek používá poziční argumenty, je reprezentováno jako počáteční objekt s inicializační hodnotou. Jako hrubá reprezentace textu se datový proud uzlu podobá následujícímu:

`StartObject`(<xref:System.Xaml.XamlType> je typ definice rozšíření značky, nikoli jeho návratový typ)

`StartMember`(název <xref:System.Xaml.XamlMember> je `_InitializationText`)

`Value`(hodnota je poziční argumenty jako řetězec včetně zasahujících oddělovačů)

`EndMember`

`EndObject`

Použití rozšíření značek s pojmenovanými argumenty je reprezentováno jako objekt s členy příslušných názvů, z nichž každá je nastavena s hodnotami textového řetězce.

Ve skutečnosti vyvolání `ProvideValue` implementace rozšíření značek vyžaduje kontext schématu XAML, protože to vyžaduje mapování typů a vytvoření instance typu podpory rozšíření značek. To je jeden z důvodů, proč jsou použití rozšíření značek zachována tímto způsobem ve výchozím datovém proudu uzlu .NET XAML Services - čtenářská část cesty zatížení často nemá k dispozici potřebný kontext schématu XAML.

Pokud pracujete s datovým proudem uzlu XAML na cestě pro uložení, obecně není nic v reprezentaci grafu objektu, které vás může `ProvideValue` informovat, že objekt serializovat byl původně poskytnut použitím rozšíření značek a výsledkem. Scénáře, které je třeba zachovat použití rozšíření značek pro round-tripping a zároveň zachytit další změny v grafu objektu musí navrhnout své vlastní techniky pro zachování znalosti použití rozšíření značky z původního vstupu XAML. Chcete-li například obnovit použití rozšíření značek, budete muset pracovat s datovým proudem uzlů na cestě pro uložení, abyste obnovili použití rozšíření značek nebo provedli nějaký typ sloučení mezi původním XAML a round-tripped XAML. Některé rozhraní implementující XAML, jako je wpf, používají zprostředkující typy (výrazy), které pomáhají reprezentovat případy, kdy použití rozšíření značek poskytlo hodnoty.

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Markup.MarkupExtension>
- [Převaděče typů a rozšíření značek pro jazyk XAML](type-converters-and-markup-extensions.md)
- [Rozšíření značek a WPF XAML](../../framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
