---
title: Přehled rozšíření značek pro jazyk XAML
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: 68c03589294bcc8b58f1142331d4a889f0f18a3b
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736497"
---
# <a name="markup-extensions-for-xaml-overview"></a>Přehled rozšíření značek pro jazyk XAML

Rozšíření značek představují techniku XAML pro získání hodnoty, která není primitivní ani konkrétního typu XAML. Pro použití atributů rozšíření značek používají sekvenci známého znaku levé složené závorky `{` k zadání rozsahu rozšíření značek a uzavírací složená závorka `}` pro ukončení. Při použití .NET Framework služby XAML můžete použít některé z předdefinovaných rozšíření značek jazyka XAML ze sestavení System. XAML. Můžete také podtřídou z třídy <xref:System.Windows.Markup.MarkupExtension> definované v souboru System. XAML a definovat vlastní rozšíření značek. Nebo můžete použít rozšíření značek definované konkrétní architekturou, pokud již odkazujete na tuto architekturu.

Když je k použití rozšíření značek přistupované, modul pro zápis objektů XAML může poskytovat služby pro vlastní třídu <xref:System.Windows.Markup.MarkupExtension> prostřednictvím spojovacího bodu služby v přepsání <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType>. Služby lze použít k získání kontextu použití, specifických možností modulu pro zápis objektů, kontextu schématu XAML a tak dále.

<a name="XAML_Defined_Markup_Extensions"></a>
## <a name="xaml-defined-markup-extensions"></a>Rozšíření značek definovaná v jazyce XAML

Několik rozšíření značek je implementováno pomocí .NET Framework služby XAML pro podporu jazyka XAML. Tato rozšíření značek odpovídají částem specifikace XAML jako jazyka. Ty jsou obvykle identifikovatelné pomocí předpony `x:` v syntaxi, jak je vidět v tématu běžné použití. Implementace .NET Framework XAML Services pro tyto prvky jazyka XAML jsou odvozeny od základní třídy <xref:System.Windows.Markup.MarkupExtension>.

> [!NOTE]
> Předpona `x:` se používá pro typické mapování oboru názvů jazyka XAML jazyka XAML v kořenovém elementu v produkci XAML. Například projekt sady Visual Studio a šablony stránky pro různá konkrétní rozhraní iniciují soubor XAML pomocí tohoto mapování `x:`. Můžete zvolit jiný token předpony ve vlastním mapování oboru názvů XAML, ale tato dokumentace bude předpokládat výchozí mapování `x:` jako způsob identifikace těchto entit, které jsou definovanou součástí oboru názvů XAML jazyka XAML, na rozdíl od konkrétního výchozí obor názvů XAML rozhraní nebo jiné obory názvů CLR nebo XML.

### <a name="xtype"></a>x:Type

`x:Type` poskytne objekt <xref:System.Type> pro pojmenovaný typ. Tato funkce se používá nejčastěji v mechanizmu odložení, který používá základní typ CLR a odvození typu jako moniker seskupení nebo identifikátor. Konkrétní příklad jsou styly a šablony WPF a jejich použití vlastností `TargetType`. Další informace najdete v tématu [rozšíření značek x:Type](x-type-markup-extension.md).

### <a name="xstatic"></a>x:Static

`x:Static` vytvoří statické hodnoty z entit kódu typu hodnoty, které nejsou přímo typu hodnoty vlastnosti, ale lze je vyhodnotit na tento typ. To je užitečné při zadávání hodnot, které již existují jako známé konstanty v definici typu. Další informace najdete v tématu [rozšíření značek x:static](x-static-markup-extension.md).

### <a name="xnull"></a>x:Null

`x:Null` určuje `null` jako hodnotu pro člena XAML. V závislosti na návrhu konkrétního typu nebo na větších konceptech rozhraní `null` není vždy výchozí hodnota pro vlastnost nebo předpokládaná hodnota prázdného řetězcového atributu. Další informace najdete v tématu [rozšíření značek x:null](x-null-markup-extension.md).

### <a name="xarray"></a>x:Array

`x:Array` podporuje vytváření obecných polí v syntaxi jazyka XAML v případech, kdy podpora kolekce, která je poskytována základními prvky a modely ovládacích prvků, není záměrně použita. Další informace najdete v tématu [rozšíření značek x:Array](x-array-markup-extension.md). V jazyce XAML 2009 konkrétně jsou pole k dispozici jako jazykové primitiva namísto jako rozšíření. Další informace naleznete v tématu [funkce jazyka XAML 2009](xaml-2009-language-features.md).

### <a name="xreference"></a>x:Reference

`x:Reference` je součástí XAML 2009, přípony původní (2006) sady jazyků. `x:Reference` představuje odkaz na jiný existující objekt v grafu objektů. Tento objekt je identifikován jeho `x:Name`. Další informace najdete v tématu [rozšíření značek x:Reference](x-reference-markup-extension.md).

### <a name="other-x-constructs"></a>Jiné x: konstrukce

Další konstrukce `x:` pro podporu funkcí jazyka XAML existují, ale nejsou implementovány jako rozšíření značek. Další informace naleznete v tématu [obor názvů XAML (x:). Jazykové funkce](xaml-namespace-x-language-features.md).

<a name="the_markupextension_base_class"></a>

## <a name="the-markupextension-base-class"></a>Základní třída MarkupExtension

Chcete-li definovat vlastní rozšíření značek, které může komunikovat s výchozími implementacemi čteček XAML a zapisovači XAML v System. XAML, odvozujete třídu od abstraktní třídy <xref:System.Windows.Markup.MarkupExtension>. Tato třída má jednu metodu, která má být přepsána, což je <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Může být také nutné definovat další konstruktory pro podporu argumentů použití rozšíření značek a přizpůsobení vlastností, které lze nastavit.

Prostřednictvím <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A> má rozšíření pro vlastní označení přístup k kontextu služby, který oznamuje prostředí, ve kterém je rozšíření značek skutečně vyvoláno procesorem XAML. V cestě načtení se jedná obvykle o <xref:System.Xaml.XamlObjectWriter>. V poli Uložit cestu je to obvykle <xref:System.Xaml.XamlXmlWriter>. Každou sestavu kontextu služby jako interní třídu kontextu poskytovatele služby XAML, která implementuje model poskytovatele služby. Další informace o dostupných službách a o tom, co představují, najdete v tématu [převaděče typů a rozšíření značek pro jazyk XAML](type-converters-and-markup-extensions-for-xaml.md).

Třída rozšíření značek musí používat úroveň veřejného přístupu; Procesory XAML musí být vždy schopny vytvořit instanci třídy podpory rozšíření značek, aby bylo možné používat jeho služby.

<a name="naming_the_support_type"></a>
## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Definování typu podpory pro vlastní rozšíření značek

Pokud používáte .NET Framework služby XAML nebo architektury, které se sestavují v .NET Framework služby XAML, máte dvě možnosti, jak pojmenovat typ podpory rozšíření značek. Název typu je relevantní, jak se autoři objektů XAML pokusí získat přístup a vyvolat typ podpory rozšíření značek, když narazí na použití rozšíření značek v jazyce XAML. Použijte jednu z následujících strategií vytváření názvů:

- Název typu, který bude mít přesnou shodu s tokenem použití kódu XAML. Pokud například chcete podporovat použití rozšíření `{Collate ...}`, zadejte název podpory `Collate`.
- Název typu, který má být tokenem řetězce využití, a příponou `Extension`. Pokud například chcete podporovat použití rozšíření `{Collate ...}`, zadejte název podpory `CollateExtension`.

Pořadí vyhledávání je nejprve vyhledat @no__t název třídy s příponou -0 a pak vyhledat název třídy bez přípony `Extension`.
  
Z perspektivy použití značek, včetně přípony `Extension` jako součást použití, je platný. To se ale chová, jako by `Extension` je skutečně součástí názvu třídy a zapisovače objektů XAML by nemohly přeložit třídu podpory rozšíření značek pro toto použití, pokud třída podpory nemá příponu `Extension`.

### <a name="the-parameterless-constructor"></a>Konstruktor bez parametrů

Pro všechny typy podpory rozšíření značek byste měli vystavit veřejný konstruktor bez parametrů. Konstruktor bez parametrů je vyžadován pro případ, kdy zapisovač objektů XAML vytvoří instanci rozšíření značek z použití prvku objektu. Podpora použití elementu objektu je korektní očekávání pro rozšíření značek, zejména pro serializaci. Můžete však implementovat rozšíření značek bez veřejného konstruktoru, pokud chcete pouze podporovat použití atributů rozšíření značek.  

Pokud vaše použití rozšíření značek nemá žádné argumenty, konstruktor bez parametrů je vyžadován k podpoře využití.

<a name="constructor_patterns_and_positional_arguments_for_a_custom_markup_extension"></a>
## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Vzory a poziční argumenty konstruktoru pro vlastní rozšíření značek

Pro rozšíření značek se zamýšleným použitím argumentů musí veřejné konstruktory odpovídat režimům zamýšleného použití. Jinými slovy, pokud je vaše rozšíření značek navrženo tak, aby vyžadovalo jeden poziční argument jako platné použití, měli byste podporovat veřejný konstruktor s jedním vstupním parametrem, který přebírá poziční argument.

Předpokládejme například, že rozšíření značek `Collate` je určeno pro podporu pouze režimu, kde existuje jeden poziční argument, který představuje jeho režim, který je určen jako konstanta výčtu `CollationMode`. V takovém případě by měl být konstruktor s následujícím formulářem:

```csharp
public Collate(CollationMode collationMode) {...}
```

Na úrovni Basic jsou argumenty předané příponě kódu řetězce, protože jsou předávány z hodnot atributů značek. Můžete provést všechny řetězce argumentů a pracovat se vstupem na této úrovni. Nicméně máte přístup k určitému zpracování, ke kterému dochází před předáním argumentů rozšíření značek do třídy podpory.

Zpracování funguje koncepčně, jako je přípona označení objektu, který má být vytvořen, a poté jsou nastaveny hodnoty členů. Každá zadaná vlastnost, která má být nastavena, je vyhodnocena podobným způsobem, jakým je možné nastavit konkrétního člena při analýze XAML. Existují dva důležité rozdíly:
  
- Jak bylo uvedeno dříve, typ podpory rozšíření značek nemusí mít konstruktor bez parametrů, aby mohl být vytvořen v jazyce XAML. Konstrukce objektu je odložena, dokud jeho možné argumenty v syntaxi textu nejsou vyhodnoceny jako poziční nebo pojmenované argumenty a příslušný konstruktor je v daném okamžiku volán.
- Používání rozšíření značek lze vnořovat. Nejprve se vyhodnocuje přípona nejvnitřnějšího označení. Proto můžete předpokládat takové použití a deklarovat jeden z parametrů konstrukce jako typ, který vyžaduje konvertor hodnoty (například rozšíření značek) k vytvoření.

V předchozím příkladu se zobrazila závislost na takovém zpracování. Modul pro zápis objektů XAML .NET Framework XAML Services zpracovává výčtové hodnoty do výčtových hodnot na nativní úrovni.

Syntaxe textu pozičního parametru rozšíření značek se může také spoléhat na konvertor typu, který je přidružený k typu, který je v argumentu konstrukce.

Argumenty jsou označovány jako poziční argumenty, protože pořadí, ve kterém jsou zjištěny tokeny v použití, odpovídají umístění parametru konstruktoru, ke kterému jsou přiřazeny. Zvažte například následující signatura konstruktoru:

```csharp
public Collate(CollationMode collationMode, object collateThis) {...}
```

Procesor XAML očekává dva Poziční argumenty pro tuto příponu označení. Pokud došlo k použití `{Collate AlphaUp,{x:Reference circularFile}}`, token `AlphaUp` se pošle na první parametr a vyhodnotí se jako výčet `CollationMode` s názvem konstantou. Výsledek vnitřní `x:Reference` se pošle druhému parametru a vyhodnotí se jako objekt.

V zadaném pravidle XAML pro syntaxi a zpracování rozšíření značek je čárka oddělovač mezi argumenty, zda jsou tyto argumenty poziční argumenty nebo pojmenované argumenty.

### <a name="duplicate-arity-of-positional-arguments"></a>Duplicitní Arita pozičních argumentů

Pokud modul pro zápis objektů XAML narazí na použití rozšíření značek pomocí pozičních argumentů a existuje více argumentů konstruktoru, které přebírají tento počet argumentů (duplicitní Arita), což není nutně chyba. Chování závisí na přizpůsobitelné nastavení kontextu schématu XAML <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>. Pokud je <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> `true`, modul pro zápis objektů XAML by neměl vyvolat výjimku pouze z důvodu duplicitní aritou. Chování nad tímto bodem není definováno přesně. Základním předpokladem pro návrh je, že kontext schématu má k dispozici informace o typu pro konkrétní parametry a může se pokusit o explicitní přetypování, které odpovídají duplicitním kandidátům, aby bylo možné zjistit, který podpis může být nejlepší shodou. Výjimka může být stále vyvolána, pokud žádné signatury nemůžou předat testy, které jsou uloženy v rámci konkrétního kontextu schématu, který je spuštěn v modulu pro zápis objektů XAML.

Ve výchozím nastavení je <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> `false` v @no__t založeném na CLR-2 pro .NET Framework služby XAML. Proto výchozí <xref:System.Xaml.XamlObjectWriter> vyvolá výjimky, pokud dojde k použití rozšíření značek, kde je duplicitní Arita v konstruktorech back-Type.

<a name="named_arguments_for_a_custom_markup_extension"></a>   
## <a name="named-arguments-for-a-custom-markup-extension"></a>Pojmenované argumenty pro vlastní rozšíření značek

Rozšíření značek, jak je uvedeno v jazyce XAML, mohou také použít formulář pojmenovaných argumentů pro použití. Na první úrovni tokenizace je syntaxe textu rozdělena do argumentů. Přítomnost znaménka rovná se (=) v rámci libovolného argumentu identifikuje argument jako pojmenovaný argument. Takový argument je také přidaný do dvojice název/hodnota. Název v tomto případě pojmenovává veřejnou nastavitelnou vlastnost typu podpory rozšíření značek. Pokud máte v úmyslu podporovat použití pojmenovaného argumentu, měli byste poskytnout tyto veřejné vlastnosti. Vlastnosti mohou být děděny, pokud zůstanou veřejné.

<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Přístup k kontextu poskytovatele služby z implementace rozšíření značek

Dostupné služby jsou pro libovolný převaděč hodnot stejné. Rozdíl je v tom, jak každý konvertor hodnot přijímá kontext služby. Přístup ke službám a službám, které jsou k dispozici, jsou popsány v tématu [převaděče typů a rozšíření značek pro jazyk XAML](type-converters-and-markup-extensions-for-xaml.md).

<a name="property_element_usage_of_a_markup_extension"></a>
## <a name="property-element-usage-of-a-markup-extension"></a>Použití elementu vlastnosti rozšíření značek

Scénáře použití rozšíření značek jsou často navržené kolem použití rozšíření značek v použití atributu. Je však také možné definovat třídu zálohování pro podporu použití prvku vlastnosti.

Pro podporu použití elementu vlastností rozšíření značek definujte veřejný konstruktor bez parametrů. Toto by měl být konstruktor instance, který není statickým konstruktorem. To je nutné, protože procesor XAML musí obecně vyvolat konstruktor bez parametrů u libovolného objektu, který zpracovává ze značky, a obsahuje třídy rozšíření značek jako prvky objektů. V případě pokročilých scénářů můžete definovat jiné než výchozí cesty konstrukce pro třídy. (Další informace najdete v tématu [direktiva x:FactoryMethod –](x-factorymethod-directive.md).) Nepoužívejte však tyto vzory pro účely rozšíření značek, protože díky tomu je zjišťování vzoru použití mnohem obtížnější, jak pro návrháře, tak pro uživatele nezpracovaných značek.

<a name="attributing_for_a_custom_markup_extension"></a>
## <a name="attributing-for-a-custom-markup-extension"></a>Připisující se k vlastnímu rozšíření značek

Aby bylo možné podporovat návrhová prostředí i určité scénáře zapisovače objektů XAML, měli byste atribut typu podpora rozšíření značek zadat pomocí několika atributů CLR. Tyto atributy nahlásí zamýšlené použití rozšíření značek.

 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute> hlásí informace o <xref:System.Type> pro typ objektu, který <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> vrátí. Pomocí jeho čistého podpisu <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> vrátí <xref:System.Object>. Ale různí spotřebitelé můžou chtít přesnější informace o návratovém typu. To zahrnuje:

- Návrháři a IDEs, kteří mohou poskytovat podporu typů pro použití rozšíření značek.
- Pokročilá implementace obslužných rutin `SetMarkupExtension` na cílových třídách, které se můžou spoléhat na reflexi pro určení návratového typu rozšíření značek místo větvení na konkrétní známá implementace <xref:System.Windows.Markup.MarkupExtension> podle názvu.

<a name="serialization_of_markup_extension_usages"></a>   
## <a name="serialization-of-markup-extension-usages"></a>Serializace používání rozšíření značek

Když modul pro zápis objektů XAML zpracuje použití rozšíření značek a volání <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, kontext pro něj předtím používá rozšíření značek v proudu uzlu XAML, ale ne v grafu objektů. V grafu objektů se zachová jenom hodnota. Máte-li scénáře návrhu nebo jiné důvody pro zachování původního využití rozšíření značek do serializovaného výstupu, je nutné navrhnout vlastní infrastrukturu pro sledování využití rozšíření značek z datového proudu uzlu XAML zatížení. Můžete implementovat chování pro opětovné vytvoření prvků datového proudu uzlu z cesty načtení a jejich přehrání zpět do zapisovačů XAML pro serializaci v cestě pro uložení, nahrazení hodnoty na příslušné pozici datového proudu uzlu.

<a name="markup_extensions_in_the_xaml_node_stream"></a>
## <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozšíření značek v datovém proudu uzlu XAML

Pokud pracujete s datovým proudem uzlu XAML v cestě zatížení, použití rozšíření značek se zobrazí v proudu uzlu jako objekt.

Pokud použití rozšíření značek používá poziční argumenty, je reprezentované jako počáteční objekt s hodnotou inicializace. Jako Přibližná reprezentace textu se datový proud uzlu podobá následujícímu:

 `StartObject` (<xref:System.Xaml.XamlType> je typ definice rozšíření značek, nikoli jeho návratový typ)

 `StartMember` (název <xref:System.Xaml.XamlMember> je `_InitializationText`)

 `Value` (hodnota je poziční argumenty jako řetězec, včetně používaných oddělovačů)

 `EndMember`

 `EndObject`

Použití rozšíření značek s pojmenovanými argumenty je reprezentováno jako objekt se členy příslušných názvů, každá sada má textové řetězce hodnoty.

Ve skutečnosti vyvolání implementace `ProvideValue` rozšíření pro označení vyžaduje kontext schématu XAML, protože to vyžaduje mapování typů a vytvoření instance typu podpora rozšíření značek. Toto je jeden z důvodů, proč se použití rozšíření značek zachová tímto způsobem ve výchozích .NET Framework datových proudů uzlu XAML Services – součást čtecího zařízení často nemá k dispozici potřebný kontext schématu XAML.

Pokud pracujete s datovým proudem uzlu XAML v cestě pro uložení, není obvykle přítomna žádná reprezentace v grafu objektů, která může informovat o tom, že objekt k serializaci byl původně poskytnut použitím rozšíření značek a výsledkem `ProvideValue`. Scénáře, které musí zachovat použití rozšíření značek pro příkaz Round-Trip a zároveň zachytit jiné změny v grafu objektů, musí navrhnout své vlastní techniky pro zachování znalostí rozšíření značek od původního vstupu XAML. Například pro obnovení použití rozšíření značek může být nutné pracovat s datovým proudem uzlu v cestě pro uložení, aby bylo možné obnovit použití rozšíření značek, nebo provést nějaký typ sloučení mezi původní XAML a kulatým Trip XAML. Některé architektury implementující XAML, jako je WPF, používají mezilehlé typy (výrazy) k vyjádření případů, kde využití rozšíření značek poskytlo hodnoty.

## <a name="see-also"></a>Další informace najdete v tématech

- <xref:System.Windows.Markup.MarkupExtension>
- [Převaděče typů a rozšíření značek pro jazyk XAML](type-converters-and-markup-extensions-for-xaml.md)
- [Rozšíření značek a WPF XAML](../wpf/advanced/markup-extensions-and-wpf-xaml.md)
