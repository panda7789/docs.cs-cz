---
title: Přehled rozšíření značek pro jazyk XAML
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: 0d1d3530bfd8bc85d6ae2d6741cbe6d48b381f69
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570015"
---
# <a name="markup-extensions-for-xaml-overview"></a>Přehled rozšíření značek pro jazyk XAML
Rozšíření značek jsou technika XAML pro získání hodnotu, která není na primitivní ani určitého typu XAML. Pro použití atributu rozšíření značek používat známé znak sekvence otevírající složenou závorku `{` k zadání oboru rozšíření značek a uzavírací složenou závorku `}` ukončíte. Při použití rozhraní .NET Framework XAML Services, můžete použít některé z předdefinovaných rozšíření značek jazyka XAML v oboru názvů System.Xaml sestavení. Můžete také jsou podtřídami tříd <xref:System.Windows.Markup.MarkupExtension> třídy definované v oboru názvů System.Xaml a definovat vlastní rozšíření značek. Nebo můžete použít rozšíření značek, které jsou definována v určité rozhraní, pokud se už odkazuje na dané rozhraní.  
  
 Při přístupu k použití rozšíření značky XAML objektu zapisovače mohou poskytovat služby k vlastní <xref:System.Windows.Markup.MarkupExtension> třídu v rámci připojení služby k časovému okamžiku <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> přepsat. Služby lze získat kontextové informace o využití, specifické možnosti objektu zapisovače, kontext schématu XAML a tak dále.  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>Rozšíření značek XAML definovaný  
 Několik rozšíření značek jsou implementované rozhraní .NET Framework XAML Services pro podporu jazyka XAML. Tyto přípony označení odpovídají částí specifikace XAML jako jazyk. Toto jsou obvykle poznáte ho podle `x:` předponu v syntaxi, jak je vidět v běžných použití. Implementace rozhraní .NET Framework XAML Services pro tyto prvky jazyka XAML všechny odvozovat <xref:System.Windows.Markup.MarkupExtension> základní třídy.  
  
> [!NOTE]
>  `x:` Předpona se používá pro typické oboru názvů XAML mapování oboru názvů jazyka XAML, v kořenový prvek XAML produkční. Například šablony sady Visual Studio projekt a stránky pro různé architektury, konkrétní inicializovat pomocí tohoto souboru XAML `x:` mapování. Můžete se rozhodnout token jinou předponu ve vlastním XAML mapování oboru názvů, ale tato dokumentace se předpokládá výchozí `x:` mapování jako způsob určení těchto entit, které jsou definované součástí oboru názvů XAML jazyka XAML, nikoli obor názvů XAML výchozí konkrétní framework nebo jiných libovolného nebo kód XML, CLR oborech názvů.  
  
### <a name="xtype"></a>x:Type  
 `x:Type` dodává <xref:System.Type> objekt s názvem typu. Tato funkce se nejčastěji používá v odložení mechanismy, které používají základní typ CLR a typ odvození jako zástupný název seskupení nebo identifikátor. WPF styly a šablony a jejich využití `TargetType` vlastnosti, jsou konkrétní příklad. Další informace najdete v tématu [x: Type – rozšíření značek](../../../docs/framework/xaml-services/x-type-markup-extension.md).  
  
### <a name="xstatic"></a>x: Static  
 `x:Static` vytváří statické hodnoty z entity kód typ hodnoty, které nejsou přímo typ hodnoty vlastnosti, ale může být vyhodnocen jako typu. To je užitečné pro zadání hodnoty, které již existují jako dobře známé konstanty v definici typu. Další informace najdete v tématu [x: Static – rozšíření značek](../../../docs/framework/xaml-services/x-static-markup-extension.md).  
  
### <a name="xnull"></a>x: Null  
 `x:Null` Určuje `null` jako hodnotu pro člena XAML. V závislosti na návrhu konkrétní typy nebo na větší framework koncepty `null` není vždy výchozí hodnotu pro vlastnost nebo implicitní hodnota atributu prázdný řetězec. Další informace najdete v tématu [x: Null – rozšíření značek](../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
### <a name="xarray"></a>x: Array  
 `x:Array` podporuje vytváření obecné polí v syntaxe XAML v případech, kdy je záměrně není použita podporu kolekce, které poskytuje základní elementy a modely ovládacího prvku. Další informace najdete v tématu [x: Array – rozšíření značek](../../../docs/framework/xaml-services/x-array-markup-extension.md). V XAML 2009 konkrétně pole jsou dostupné jako primitivní místo jako rozšíření. Další informace najdete v tématu [funkce jazyka XAML 2009](../../../docs/framework/xaml-services/xaml-2009-language-features.md).  
  
### <a name="xreference"></a>x: Reference  
 `x:Reference` je součástí XAML 2009, rozšíření z původní sady language (2006). `x:Reference` představuje odkaz na jiný existující objekt v grafu objektů. Tento objekt je identifikován jeho `x:Name`. Další informace najdete v tématu [x: Reference – rozšíření značek](../../../docs/framework/xaml-services/x-reference-markup-extension.md).  
  
### <a name="other-x-constructs"></a>Další x: Konstrukce  
 Další `x:` existují konstrukty, které podporují funkce jazyka XAML, ale ty nejsou implementované jako rozšíření značek. Další informace najdete v tématu [Namespace XAML (x:) Funkce jazyka](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).  
  
<a name="the_markupextension_base_class"></a>   
## <a name="the-markupextension-base-class"></a>MarkupExtension základní třída  
 Chcete-li definovat rozšíření vlastního kódu, které mohou komunikovat s výchozí implementace XAML čtečky a zapisovače XAML v oboru názvů System.Xaml odvodit třídu z abstraktní <xref:System.Windows.Markup.MarkupExtension> třídy. Že třída má jedna metoda přepsání, která je <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Budete také muset definovat další konstruktory pro podporu argumenty pro použití rozšíření značky a odpovídající nastavitelné vlastnosti.  
  
 Prostřednictvím <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, rozšíření vlastního kódu má přístup do kontextu služby, který bude hlásit prostředí, kde rozšíření značek ve skutečnosti vyvolávat procesoru XAML. V cestě zatížení obvykle se jedná <xref:System.Xaml.XamlObjectWriter>. V Uložit cestu obvykle se jedná <xref:System.Xaml.XamlXmlWriter>. Každá sestava kontext služby jako interní XAML služby zprostředkovatele kontextu třída, která implementuje vzor poskytovatele služeb. Další informace o dostupných službách a co představují, najdete v části [převaděče typů a rozšíření značek pro XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 Vaše třída rozšíření značek musí používat úroveň veřejného přístupu; XAML procesory musí být vždy umožňuje vytvořit instanci pomocná třída rozšíření značek, aby bylo možné používat jeho služeb.  
  
<a name="naming_the_support_type"></a>   
## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Definování typu podporu pro rozšíření vlastního kódu  
 Při použití rozhraní .NET Framework XAML Services nebo rozhraní, které staví na rozhraní .NET Framework XAML Services, máte dvě možnosti, jak zadat název typu podporu rozšíření značek. Název typu je relevantní pro jak XAML objekt zapisovače pokus o přístup k a má být vyvolán jako typ podpory rozšíření značek při použití rozšíření značky v XAML narazí. Použijte jednu z následujících strategií pojmenování:  
  
-   Název typu být přesnou shodou token využití značek XAML. Například pro podporu `{Collate ...}` použití rozšíření, název typu podporu `Collate`.  
  
-   Název typu jako řetězec s tokenem využití a přípona `Extension`. Například pro podporu `{Collate ...}` použití rozšíření, název typu podporu `CollateExtension`.  
  
 Pořadí vyhledávání je vás pod rouškou `Extension`-příponami třídy pojmenujte první a potom vyhledejte název třídy bez `Extension` příponu.  
  
 Z hlediska využití značek včetně `Extension` přípony jako součást využití je platný. Ale to se chová jako kdyby `Extension` je skutečně část názvu třídy a XAML objekt zapisovače selže vyřešíte pomocná třída rozšíření značek tohle využívání pomocná třída nemá `Extension` příponu.  
  
### <a name="the-default-constructor"></a>Výchozí konstruktor  
 Všechna rozšíření značek podporují typy, by měly vystavit veřejný výchozí konstruktor. Výchozí konstruktor je vyžadován pro případ, kdy zapisovače objektu XAML vytváří instanci rozšíření značek z použití elementu objektu. Podpora použití elementu objektu je veletrh očekávání ohledně rozšíření značek, zejména pro serializaci. Pokud chcete podporovat použití atributu rozšíření značek, je však implementovat rozšíření značek bez veřejného konstruktoru.  
  
 Pokud vaše použití rozšíření značky nemá žádné argumenty, je potřeba podporovat použití výchozího konstruktoru.  
  
<a name="constructor_patterns_and_positional_arguments_for_a_custom_markup_extension"></a>   
## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Zabezpečené vzory konstruktoru a poziční argumenty pro rozšíření vlastního kódu  
 Pro rozšíření značek s využitím odpovídající argument veřejné konstruktory musí odpovídat režimy zamýšlené použití. Jinými slovy Pokud vaše – rozšíření značek je navržen tak, aby vyžadovala jedna poziční argument jako platný využití, by měl podporovat veřejný konstruktor s jeden vstupní parametr, který přijímá poziční argument.  
  
 Předpokládejme například, že `Collate` – rozšíření značek je určené pro podporu pouze režim stanoveno, je-li jeden poziční argument, který představuje jeho režimu, `CollationMode` konstanta výčtu. V takovém případě by měl být konstruktor s následující tvar:  
  
```  
public Collate(CollationMode collationMode) {...}  
```  
  
 Na základní úrovni argumenty předané do rozšíření značek jsou řetězce, protože jsou předávány z hodnot atributů kódu. Můžete provést všechny vaše argumenty řetězce a pracovat se vstupem na této úrovni. Ale máte přístup k určité zpracování, který nastal dřív, než jsou předány argumenty přípony označení pomocná třída.  
  
 Zpracování se koncepčně funguje jakoby rozšíření značek je objekt, který se má vytvořit, a nastavte hodnoty jeho členů. Každá zadaná vlastnost pro nastavení je vyhodnocen podobný jak zadaného člena lze nastavit pro objekt vytvořený při XAML je analyzován. Existují dva důležité rozdíly:  
  
-   Jak bylo uvedeno dříve, není potřeba mít výchozí konstruktor, aby bylo možné vytvořit instanci v XAML jako typ podpory rozšíření značek. Konstrukce objektu je odloženo, dokud jeho možné argumenty v textu syntaxe jsou tokenizovaného a vyhodnotí jako poziční nebo pojmenované argumenty a odpovídajícího konstruktoru je volána v daném čase.  
  
-   Použití rozšíření značky mohou být vnořené. Rozšíření pro vnitřní kód je vyhodnocen jako první. Proto můžete předpokládat takové použití a deklarujte jeden z parametrů konstrukce na typ, který vyžaduje převaděč hodnoty (jako je například rozšíření značek) k vytvoření.  
  
 Závislost na toto zpracování se zobrazilo v předchozím příkladu. Objekt zapisovače rozhraní .NET Framework XAML Services XAML procesu výčtu konstant názvy do výčtové hodnoty na nativní úroveň.  
  
 Zpracování textová syntaxe značek pozičních parametrů rozšíření můžete také využívají konvertor typu, který je přidružen typ, který je v argumentu konstrukce.  
  
 Argumenty jsou nazývány poziční argumenty, protože odpovídá pořadí, ve kterém dochází tokeny ve využití pořadí poziční parametr konstruktoru, ke kterému jsou přiřazeny. Představte si třeba následující podpis konstruktoru:  
  
```  
public Collate(CollationMode collationMode, object collateThis) {...}  
```  
  
 Procesor XAML očekává, že dva poziční argumenty tohoto rozšíření značek. Pokud se využití `{Collate AlphaUp,{x:Reference circularFile}}`, `AlphaUp` token se odesílají do první parametr a vyhodnotí jako `CollationMode` výčtu s názvem – konstanta. Výsledek vnitřního `x:Reference` se odesílají na druhý parametr a vyhodnotit jako objekt.  
  
 XAML je zadaná pravidla pro rozšíření syntaxe značek a zpracování, čárky oddělovač mezi argumenty, jestli tyto argumenty jsou poziční argumenty nebo pojmenované argumenty.  
  
### <a name="duplicate-arity-of-positional-arguments"></a>Duplicitní Arita pro instanci poziční argumenty  
 Pokud se použití rozšíření značky s poziční argumenty, zaznamená zapisovače objektu XAML a existuje více argumentů konstruktoru, které tohoto čísla argumenty (duplicitní Arita), který není nutně chybu. Chování závisí na přizpůsobitelné XAML schématu nastavení kontextu, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>. Pokud <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> je `true`, zapisovače objektu XAML by neměla vyvolávat výjimka pouze z důvodů duplicitní Arita. Chování za daným bodem není striktně definované. Předpoklad základním návrhu je, že kontextu schématu je k dispozici pro parametry pro konkrétní informace o typu a může pokus o explicitní přetypování, které odpovídají duplicitní kandidáty zobrazíte podpis, který může být nejlepší shodu. Pokud žádné podpisy projdou testy, které jsou uložené tento konkrétní schématu kontext, který běží na zapisovače objektu XAML, může být stále vyvolána výjimka.  
  
 Ve výchozím nastavení <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> je `false` v CLR-based <xref:System.Xaml.XamlSchemaContext> pro rozhraní .NET Framework XAML Services. Proto výchozí <xref:System.Xaml.XamlObjectWriter> vyvolá výjimky, pokud se setká s použití rozšíření značky ve kterých je duplicitní Arita v konstruktory základního typu.  
  
<a name="named_arguments_for_a_custom_markup_extension"></a>   
## <a name="named-arguments-for-a-custom-markup-extension"></a>Pojmenované argumenty pro rozšíření vlastního kódu  
 Rozšíření značek XAML určený můžete také formuláře pojmenované argumenty pro využití. Na první úrovni Tokenizace textová syntaxe se dělí argumenty. Přítomnost znak rovná se (=) v rámci některý argument určuje argument jako pojmenovaný argument. Takové argument je také tokenizovaného do dvojici název/hodnota. Jména v tomto případě veřejné nastavitelnou vlastnost typu podporu rozšíření značek. Pokud máte v úmyslu podporují použití pojmenovaných argumentů, je vhodné zadat tyto veřejné nastavitelné vlastnosti. Vlastnosti může být zděděné vlastnosti, tak dlouho, dokud zůstává zachována možnost jejich veřejné.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Přístup k kontext zprostředkovatele služby z implementace rozšíření značek  
 Dostupné služby jsou stejné pro všechny převaděč hodnoty. Rozdíl je v jak každý převaděč hodnoty obdrží kontext služby. Přístup k službám a službám, které jsou k dispozici jsou popsány v tématu [převaděče typů a rozšíření značek pro XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="property_element_usage_of_a_markup_extension"></a>   
## <a name="property-element-usage-of-a-markup-extension"></a>Použití elementu vlastnosti rozšíření značek  
 Scénáře pro použití rozšíření značky jsou často navržené s ohledem pomocí rozšíření značek v použití atributu. Je však také potenciálně možné základní třídy pro podporu použití elementu vlastnosti.  
  
 Chcete-li podporovat použití elementu vlastnosti vašeho rozšíření značek, definujte veřejný výchozí konstruktor. To by měl být konstruktor instance není statický konstruktor. Se totiž procesoru XAML musí obecně vyvolání výchozího konstruktoru u libovolného elementu objektu, který zpracovává ze značek, a to zahrnuje třídy rozšíření značek jako elementů objektu. Pro pokročilé scénáře můžete definovat cesty k jiné než výchozí konstrukci pro třídy. (Další informace najdete v tématu [x: FactoryMethod – direktiva](../../../docs/framework/xaml-services/x-factorymethod-directive.md).) Tato schémata však neměli byste používat pro účely rozšíření značek, protože díky tomu zjišťování vzor používání mnohem obtížnější, pro profesionální návrháře využívající i pro uživatele nezpracovaný kód.  
  
<a name="attributing_for_a_custom_markup_extension"></a>   
## <a name="attributing-for-a-custom-markup-extension"></a>Přidělování pro rozšíření vlastního kódu  
 Pro podporu vybavená vývojová prostředí a určitých scénářů objekt zapisovače XAML, by měl atribut jako typ podpory rozšíření značek s několika atributy CLR. Tyto atributy zasílání zpráv o využití rozšíření odpovídající značky.  
  
 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute> sestavy <xref:System.Type> zadejte informace o objektu, který <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> vrátí. Čistě podpisem <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> vrátí <xref:System.Object>. Ale různé uživatele může být vhodné přesnější informace návratovým typem. Sem patří:  
  
-   Návrháři a Integrovaná vývojová prostředí, který může být schopný poskytnout s ohledem na typ podporu pro použití rozšíření značky.  
  
-   Implementace rozšířené `SetMarkupExtension` obslužné rutiny na cílové třídy, které může závisí na reflexi k určení návratového typu rozšíření značek namísto větvení na konkrétní známé <xref:System.Windows.Markup.MarkupExtension> implementace podle názvu.  
  
<a name="serialization_of_markup_extension_usages"></a>   
## <a name="serialization-of-markup-extension-usages"></a>Serializace použití rozšíření značek  
 Při zápisu objektu XAML zpracovává použití rozšíření značky a volání <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, kontext pro něj předtím se použití rozšíření značky přetrvává v datovém proudu uzlu XAML, ale ne v grafu objektů. V grafu objektů je zachována pouze hodnotu. Pokud máte scénáře návrhu nebo jiných důvodů, proč trvalé původní použití rozšíření značky na serializovaná výstupu, je třeba navrhnout vlastní infrastrukturu pro sledování využití rozšíření značek v datovém proudu uzlu XAML cesta zatížení. Můžete implementovat chování, abyste mohli znovu vytvořit prvky datový proud uzlu z cesty zatížení a jejich přehrávání pro autory XAML pro serializaci v Uložit cestu, nahraďte hodnoty v příslušné pozici datovém proudu uzlu.  
  
<a name="markup_extensions_in_the_xaml_node_stream"></a>   
## <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozšíření značek v Stream uzlu XAML  
 Pokud pracujete s datový proud uzlu XAML v cestě zatížení, zobrazí se použití rozšíření značky v datovém proudu uzlu jako objekt.  
  
 Pokud se použití rozšíření značky používá poziční argumenty, je datum vyjádřeno jako počáteční objekt s hodnotou inicializace. Jako hrubý textové vyjádření datovém proudu uzlu vypadá přibližně takto:  
  
 `StartObject` (<xref:System.Xaml.XamlType> je typ definice rozšíření značek, její návratový typ)  
  
 `StartMember` (název <xref:System.Xaml.XamlMember> je `_InitializationText`)  
  
 `Value` (hodnota je poziční argumenty jako řetězec, včetně použité oddělovače)  
  
 `EndMember`  
  
 `EndObject`  
  
 Použití rozšíření značky s pojmenovanými argumenty je reprezentována jako objekt s členy od příslušného názvu každého nastavení s textovými řetězci hodnotami.  
  
 Ve skutečnosti volání `ProvideValue` provádění rozšíření značek vyžaduje kontext schématu XAML, protože, která vyžaduje mapování typu a vytvoření instance typu podporu rozšíření značek. Toto je jedním z důvodů, proč použití rozšíření značky jsou zachovány tímto způsobem v datové proudy rozhraní .NET Framework XAML Services uzlu výchozí – čtečky část cesty zatížení, který je často nemá potřebné XAML schématu kontextu k dispozici.  
  
 Pokud pracujete s datový proud uzlu XAML Uložit cestu, obvykle není k dispozici v reprezentaci grafu objektů, který informuje, že objekt určený k serializaci byla původně poskytované použití rozšíření značky a `ProvideValue` výsledek. Scénáře, které je potřeba zachovat použití rozšíření značky u verzemi, zatímco také zaznamenání další změny v grafu objektů musí navrhnout svoje vlastní techniky pro zachování informací o použití rozšíření značky z původní vstup XAML. Například chcete-li obnovit použití rozšíření značky, budete muset pracovat s datovém proudu uzlu na Uložit cestu, aby bylo možné obnovit použití rozšíření značky nebo provádí nějaký typ sloučení mezi původní XAML a XAML odbavovaná. Některé implementace XAML architektury, jako jsou WPF reprezentují případy, kdy použití rozšíření značky zadané hodnoty pomocí vnitřní typy (výrazy).  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Markup.MarkupExtension>
- [Převaděče typů a rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)
- [Rozšíření značek a WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
