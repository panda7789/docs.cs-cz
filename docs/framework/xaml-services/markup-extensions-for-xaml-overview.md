---
title: Přehled rozšíření značek pro jazyk XAML
ms.date: 03/30/2017
helpviewer_keywords:
- markup extensions [XAML Services], custom
- XAML [XAML Services], markup extensions
ms.assetid: 261b2b11-2dc0-462f-8c66-55b8c9c6e436
ms.openlocfilehash: 6b7c13355fe46d4b768699555bbaf522e3b49c73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566571"
---
# <a name="markup-extensions-for-xaml-overview"></a>Přehled rozšíření značek pro jazyk XAML
Rozšíření značek jsou techniku XAML pro získání hodnotu, která není primitivní ani konkrétní typ jazyka XAML. Pro použití atributu, použít rozšíření značek pořadí známé znak otevření složené závorky `{` k zadání oboru rozšíření značek a složené závorky ukončovací `}` ukončíte. Pokud používáte rozhraní .NET Framework XAML Services, můžete některé z předdefinovaných rozšíření značek jazyka XAML z System.Xaml sestavení. Můžete také podtřídou z <xref:System.Windows.Markup.MarkupExtension> třídy definované v System.Xaml a definovat vlastní rozšíření značek. Nebo můžete použít rozšíření značek definované určité rozhraní, pokud jsou již odkazující na dané platformy.  
  
 Při přístupu k použití rozšíření značek zapisovače objektu XAML poskytuje služby pro vlastní <xref:System.Windows.Markup.MarkupExtension> prostřednictvím připojení ke službě bod v <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A?displayProperty=nameWithType> přepsat. Služby lze použít k získání kontextu o využití, specifické možnosti zapisovače objektu, kontext schématu XAML a tak dále.  
  
<a name="XAML_Defined_Markup_Extensions"></a>   
## <a name="xaml-defined-markup-extensions"></a>Rozšíření značek definovaný XAML  
 Několik rozšíření značek jsou implementovány pomocí rozhraní .NET Framework XAML Services pro podporu jazyka XAML. Tato rozšíření značek odpovídají částí jako jazyk specifikace jazyka XAML. Toto jsou obvykle poznáte ho podle `x:` předpony v syntaxi, jak je vidět v běžných využití. Implementace rozhraní .NET Framework XAML Services pro tyto elementy jazyka XAML dědí ze <xref:System.Windows.Markup.MarkupExtension> základní třídy.  
  
> [!NOTE]
>  `x:` Předpona se používá pro typické mapování oboru názvů jazyka XAML oboru názvů jazyka XAML, v kořenovém elementu provozní XAML. Například šablony sady Visual Studio projekt a stránku pro různé konkrétní rozhraní zahájit soubor XAML pomocí této `x:` mapování. Může zvolit jinou předponu token v vlastní mapování oboru názvů jazyka XAML, ale tato dokumentace bude předpokládat výchozí `x:` mapování jako prostředek identifikace tyto entity, které jsou definované součástí oboru názvů jazyka XAML jazyka XAML naproti tomu konkrétní framework oboru názvů jazyka XAML výchozí nebo jiných libovolný CLR nebo XML oborech názvů.  
  
### <a name="xtype"></a>x: Type  
 `x:Type` poskytuje <xref:System.Type> objektu pro typ s názvem. Tato funkce se nejčastěji používá v odložení mechanismy, které používají základní typ CLR a zadejte odvození jako přezdívku seskupení nebo identifikátor. WPF styly a šablony a jejich využití `TargetType` vlastnosti, jsou konkrétní příklad. Další informace najdete v tématu [x: Type – rozšíření značek](../../../docs/framework/xaml-services/x-type-markup-extension.md).  
  
### <a name="xstatic"></a>x: Static  
 `x:Static` Vytvoří statické hodnoty z entit kód typ hodnoty, které nejsou přímo typ vlastnosti na hodnotu, ale lze vyhodnotit na typu. To je užitečné pro zadání hodnoty, které už existují jako dobře známé konstanty v definici typu. Další informace najdete v tématu [x: Static – rozšíření značek](../../../docs/framework/xaml-services/x-static-markup-extension.md).  
  
### <a name="xnull"></a>x: Null  
 `x:Null` Určuje `null` jako hodnotu pro člena XAML. V závislosti na konkrétní typy nebo na větší framework koncepty návrhu `null` není vždy výchozí hodnotu pro vlastnost nebo předpokládané hodnotu atributu prázdný řetězec. Další informace najdete v tématu [x: Null – rozšíření značek](../../../docs/framework/xaml-services/x-null-markup-extension.md).  
  
### <a name="xarray"></a>x: Array  
 `x:Array` podporuje vytváření obecné pole v syntaxi XAML v případech, kdy je podpora kolekce, které poskytuje základní prvky a modely ovládací prvek záměrně není použita. Další informace najdete v tématu [x: Array – rozšíření značek](../../../docs/framework/xaml-services/x-array-markup-extension.md). V jazyce XAML 2009 konkrétně pole jsou dostupné jako primitiva jazyka místo jako rozšíření. Další informace najdete v tématu [funkce jazyka XAML 2009](../../../docs/framework/xaml-services/xaml-2009-language-features.md).  
  
### <a name="xreference"></a>x: Reference  
 `x:Reference` je součástí XAML 2009, rozšíření původní (2006) jazykové sady. `x:Reference` představuje odkaz na jiný existující objekt v grafu objektu. Tento objekt je určený podle jeho `x:Name`. Další informace najdete v tématu [x: Reference – rozšíření značek](../../../docs/framework/xaml-services/x-reference-markup-extension.md).  
  
### <a name="other-x-constructs"></a>Další konstrukce x:  
 Další `x:` konstrukty, které podporují funkce jazyka XAML existují, avšak tyto nejsou implementované jako rozšíření značek. Další informace najdete v tématu [Namespace XAML (x:) Jazykové funkce](../../../docs/framework/xaml-services/xaml-namespace-x-language-features.md).  
  
<a name="the_markupextension_base_class"></a>   
## <a name="the-markupextension-base-class"></a>MarkupExtension základní třída  
 Můžete definovat rozšíření vlastních značek, které mohou komunikovat s výchozí implementace XAML čtení a zápis XAML v System.Xaml, odvození třídy z abstraktní <xref:System.Windows.Markup.MarkupExtension> třídy. Aby třída má jednu metodu přepsat, což je <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>. Je také třeba definovat další konstruktory pro podporu argumenty pro použití rozšíření značek a odpovídající nastavit vlastnosti.  
  
 Prostřednictvím <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, rozšíření vlastních značek má přístup ke kontextu služby, který hlásí prostředí, kde je ve skutečnosti vyvolat rozšíření značek procesorem XAML. V cestě zatížení to je obvykle <xref:System.Xaml.XamlObjectWriter>. V poli Uložit cestu, obvykle je to <xref:System.Xaml.XamlXmlWriter>. Všechny sestavy kontext služby jako interní XAML služby zprostředkovatele kontextu třídu, která implementuje vzor zprostředkovatele služby. Další informace o dostupných služeb a co představují, najdete v části [převaděče typů a rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
 Třídě rozšíření značek musí použít úroveň veřejný přístup; XAML procesory musí být vždy schopen vytvořit instanci třídy podporu rozšíření značek-li používat jeho služby.  
  
<a name="naming_the_support_type"></a>   
## <a name="defining-the-support-type-for-a-custom-markup-extension"></a>Definování typu podporu pro rozšíření vlastních značek  
 Pokud používáte rozhraní .NET Framework XAML Services nebo rozhraní, které sestavení v rozhraní .NET Framework XAML Services, máte dvě možnosti pro pojmenování typ podporu rozšíření značek. Název typu je relevantní pro jak XAML objekt zapisovače pokusí o přístup a vyvolání typu značek rozšíření podpory, když narazí na používání rozšíření značek v jazyce XAML. Použijte jednu z následujících strategií pojmenování:  
  
-   Název název typu, který se má přesnou shodou token využití kód XAML. Například pro podporu `{Collate ...}` rozšíření využití, název typu podporu `Collate`.  
  
-   Název název typu jako token řetězcového využití plus přípona `Extension`. Například pro podporu `{Collate ...}` rozšíření využití, název typu podporu `CollateExtension`.  
  
 Pořadí vyhledávání je hledání `Extension`-vyznačeno třída nejprve název a potom vyhledejte název třídy bez `Extension` příponu.  
  
 Z hlediska využití značek včetně `Extension` přípona jako součást využití je platný. To však chová jako kdyby `Extension` je skutečně součástí název třídy a XAML objekt zapisovače by nepodaří vyřešit třídu značek rozšíření podpory pro toto využití, pokud třída podporu neměl `Extension` příponu.  
  
### <a name="the-default-constructor"></a>Výchozí konstruktor.  
 Pro všechny – rozšíření značek podporují typy, by měl vystavit veřejný výchozí konstruktor. Výchozí konstruktor je vyžadována pro každý případ, kde zapisovač objekt XAML vytvoří rozšíření značek z použití elementu objektu. Podpora použití elementu objektu je správného očekávání pro rozšíření značek, zejména pro serializaci. Pokud chcete podporovat použití atributu rozšíření značek, ale můžete implementovat rozšíření značek bez veřejný konstruktor.  
  
 Pokud vaše využití rozšíření značek neobsahuje žádné argumenty, je potřeba podporovat použití výchozí konstruktor.  
  
<a name="constructor_patterns_and_positional_arguments_for_a_custom_markup_extension"></a>   
## <a name="constructor-patterns-and-positional-arguments-for-a-custom-markup-extension"></a>Konstruktor vzory a poziční argumenty pro rozšíření vlastních značek  
 Pro rozšíření značek s argument zamýšlené použití musí odpovídat veřejné konstruktory režimy zamýšlené použití. Jinými slovy Pokud vaše – rozšíření značek je navržený tak, aby vyžadovala jeden argument poziční jako platné použití, by měly podporovat veřejný konstruktor s jeden vstupní parametr, který přebírá poziční argument.  
  
 Předpokládejme například, že `Collate` – rozšíření značek je určená pro podporu pouze režim níž se nachází jeden poziční argument, který představuje jeho režim, zadaný jako `CollationMode` konstanta výčtu. V takovém případě by měl být konstruktor s následující tvar:  
  
```  
public Collate(CollationMode collationMode) {...}  
```  
  
 Na základní úrovni jsou argumenty předávané rozšíření značek řetězec, protože jsou předávány z hodnot atributů z kódu. Můžete nastavit všechny vaše argumenty řetězce a pracovat s vstup na této úrovni. Můžete ale mají přístup k určité zpracování, k níž dojde před argumenty rozšíření značek do třídy podpory.  
  
 Zpracování funguje koncepčně jako v případě, že rozšíření značek je objekt, který se má vytvořit, a nastavte svých členských hodnot. Každou zadanou vlastnost nastavit vyhodnotí podobná jak zadaného člena lze nastavit u objekt vytvořený při je analyzovat XAML. Existují dva důležité rozdíly:  
  
-   Jak je uvedeno dříve, není nutné mít výchozí konstruktor, aby bylo možné vytvořit instanci v jazyce XAML typu značek rozšíření podpory. Jeho vytváření objektů je odložení, dokud jeho možných argumentů v textových syntaxi jsou tokenizovaného a vyhodnotit jako poziční nebo pojmenované argumenty a vhodný konstruktor je volána v daném čase.  
  
-   Použití rozšíření značek mohou být použity. Rozšíření nejvnitřnější značek je první vyhodnocen. Proto můžete předpokládat takové použití a jeden z parametrů konstrukce jako typ, který vyžaduje převaděč hodnoty (například rozšíření značek) k vytvoření deklarovat.  
  
 Závislá na takové zpracování se zobrazí v předchozím příkladu. Objekt zapisovače rozhraní .NET Framework XAML Services XAML procesu výčtu konstantní názvy do výčtové hodnoty na nativní úroveň.  
  
 Zpracování textových syntaxi poziční parametru rozšíření značek můžete také závisí na převaděče typů, která souvisí s typem, který je v argumentu konstrukce.  
  
 Argumenty, které se nazývají poziční argumenty, protože odpovídá pořadí, ve kterém je došlo tokeny v použití poziční pořadí parametr konstruktoru, ke které jsou přiřazeni. Zvažte například následující konstruktor podpis:  
  
```  
public Collate(CollationMode collationMode, object collateThis) {...}  
```  
  
 Procesor XAML očekává dva argumenty poziční pro tuto příponu značek. Pokud se na používání `{Collate AlphaUp,{x:Reference circularFile}}`, `AlphaUp` se odesílají na první parametr a vyhodnotit jako token `CollationMode` s názvem konstanta výčtu. Výsledek vnitřního `x:Reference` se odesílají na druhý parametr a vyhodnotit jako objekt.  
  
 V XAML zadaný pravidla pro kód rozšíření syntaxe a zpracování, čárkou je odděleny argumenty, zda jsou tyto argumenty poziční argumentů nebo pojmenované argumenty.  
  
### <a name="duplicate-arity-of-positional-arguments"></a>Duplicitní aritu argumentů umístění.  
 Pokud objekt zapisovač XAML zaznamená použití značek rozšíření s poziční parametry a existuje více argumentů konstruktor vyžadující počet argumentů (duplicitní Arita), který není nutně k chybě. Chování závisí na přizpůsobitelné XAML schématu nastavení kontextu, <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A>. Pokud <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> je `true`, by neměla vyvolat výjimku pouze z důvodů duplicitní Arita, zapisovač objekt XAML. Chování za tímto bodem není definován výhradně. Základní návrhu předpokladem je, že kontext schématu má k dispozici pro konkrétní parametry informací o typu a může pokus o explicitní přetypování, které odpovídají duplicitní kandidáty zobrazíte podpisů může být nejlepší shodu. Pokud žádné podpisy můžete předat testy, které jsou způsobené tohoto kontextu konkrétní schématu, která běží na objekt zapisovač XAML, může být stále vyvolána výjimka.  
  
 Ve výchozím nastavení <xref:System.Xaml.XamlSchemaContextSettings.SupportMarkupExtensionsWithDuplicateArity%2A> je `false` CLR založený na <xref:System.Xaml.XamlSchemaContext> pro rozhraní .NET Framework XAML Services. Proto výchozí <xref:System.Xaml.XamlObjectWriter> vyvolá výjimek, pokud zjistí použití rozšíření značek kterých je duplicitní Arita v konstruktory základního typu.  
  
<a name="named_arguments_for_a_custom_markup_extension"></a>   
## <a name="named-arguments-for-a-custom-markup-extension"></a>Pojmenované argumenty pro rozšíření vlastních značek  
 Rozšíření značek podle specifikace XAML můžete také formuláře pojmenované argumenty pro použití. V první úroveň tokenizaci textových syntaxi rozdělen do argumenty. Přítomnost znak rovná se (=) v rámci některý argument identifikuje argument jako argumentem. Takové argument je také tokenizovaného do dvojici název/hodnota. Název v tomto případě názvy veřejných nastavit vlastnost typu podporu rozšíření značek. Pokud máte v úmyslu podporovat použití pojmenovaný argument, měl by poskytnout tyto veřejné nastavit vlastnosti. Vlastnosti může být zděděné vlastnosti, tak dlouho, dokud zůstanou veřejné.  
  
<a name="accessing_service_provider_context_from_a_markup_extension_implementation"></a>   
## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Přístup k kontext zprostředkovatele služby z implementaci rozšíření značek  
 Služby k dispozici jsou stejné pro všechny převaděč hodnoty. Rozdíl spočívá v tom, jak každý převaděč hodnoty obdrží kontext služby. Přístup k službám a službami, které jsou k dispozici jsou popsané v tématu [převaděče typů a rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).  
  
<a name="property_element_usage_of_a_markup_extension"></a>   
## <a name="property-element-usage-of-a-markup-extension"></a>Použití elementu vlastnosti rozšíření značek  
 Scénáře pro použití rozšíření značek jsou často uspořádaná kolem pomocí rozšíření značek v použití atributu. Je však také potenciálně možné definovat základní třídu pro podporu použití elementu vlastnosti.  
  
 Chcete-li podporovat použití elementu vlastnosti vašeho rozšíření značek, definujte výchozí veřejný konstruktor. To by měl být konstruktoru instance statického konstruktoru. Toto je nutné kvůli procesor XAML musí obecně vyvolat výchozí konstruktor u libovolného elementu objektu, který zpracovává z značek, a to zahrnuje značek rozšíření třídy jako elementy objektu. Pro pokročilé scénáře můžete definovat konstrukce jiné než výchozí cesty pro třídy. (Další informace najdete v tématu [x: factorymethod – direktiva](../../../docs/framework/xaml-services/x-factorymethod-directive.md).) Nicméně byste neměli používat tyto vzory pro účely rozšíření značek, protože díky zjišťování vzor používání mnohem obtížnější, pro návrháře i pro uživatele nezpracovaná značek.  
  
<a name="attributing_for_a_custom_markup_extension"></a>   
## <a name="attributing-for-a-custom-markup-extension"></a>Zapisujících pro rozšíření vlastních značek  
 Pro podporu prostředí návrhu a některých scénářích objekt zapisovače XAML, má atribut typu značek rozšíření podpory s několika atributy CLR. Tyto atributy sestavy využití rozšíření určený značek.  
  
 <xref:System.Windows.Markup.MarkupExtensionReturnTypeAttribute> sestavy <xref:System.Type> informace pro objekt typu <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> vrátí. Čistý podpisem <xref:System.Windows.Markup.ArrayExtension.ProvideValue%2A> vrátí <xref:System.Object>. Ale různé příjemci chtít přesnější informací o návratovém typu. Sem patří:  
  
-   Návrháři a integrovaného vývojového prostředí, který může být schopný poskytnout používající typ podporu pro použití rozšíření značek.  
  
-   Rozšířené implementace `SetMarkupExtension` obslužné rutiny na cílové třídy, které může závisí na reflexi určit návratový typ rozšíření značek místo vytvoření větve na konkrétní známé <xref:System.Windows.Markup.MarkupExtension> implementace podle názvu.  
  
<a name="serialization_of_markup_extension_usages"></a>   
## <a name="serialization-of-markup-extension-usages"></a>Serializace použití rozšíření značek  
 Pokud objekt zapisovač XAML zpracovává použití rozšíření značek a volání <xref:System.Windows.Markup.MarkupExtension.ProvideValue%2A>, kontext pro něj předtím se použití rozšíření značek potrvají datový proud uzlu XAML, avšak nejsou v grafu objektů. V grafu objektů se zachová pouze hodnotu. Pokud máte scénáře návrhu nebo z jiných důvodů pro zachování původní rozšíření použití značek do serializovaných výstup, je třeba navrhnout vlastní infrastrukturu pro sledování použití rozšíření značek z datový proud uzlu XAML cesta zatížení. Můžete implementovat chování znovu vytvářet prvky datový proud uzlu z cesty zatížení- and -play zpět do zapisovače XAML pro serializaci v uložení cestu, nahraďte hodnoty v příslušné pozici datový proud uzlu.  
  
<a name="markup_extensions_in_the_xaml_node_stream"></a>   
## <a name="markup-extensions-in-the-xaml-node-stream"></a>Rozšíření značek v datový proud uzlu XAML  
 Pokud pracujete s datový proud uzlu XAML v cestě zatížení, se zobrazí na používání rozšíření značek v datový proud uzlu jako objekt.  
  
 Pokud rozšíření použití značek používá poziční argumenty, je reprezentována jako objekt počáteční hodnotou inicializace. Datový proud uzlu jako hrubý textové reprezentace, vypadá třeba takto:  
  
 `StartObject` (<xref:System.Xaml.XamlType> je typ definice rozšíření značek, její návratový typ)  
  
 `StartMember` (název <xref:System.Xaml.XamlMember> je `_InitializationText`)  
  
 `Value` (hodnota je poziční argumenty jako řetězec včetně použité oddělovače)  
  
 `EndMember`  
  
 `EndObject`  
  
 Použití značek rozšíření s pojmenované argumenty je reprezentována jako objekt se členy příslušné názvy jednotlivých nastavit s hodnotami typu řetězec textu.  
  
 Ve skutečnosti vyvolání `ProvideValue` implementaci rozšíření značek vyžaduje kontext schématu XAML vzhledem k tomu, který vyžaduje typ mapování a vytvoření instance typu podporu rozšíření značek. Toto je jedním z důvodů, proč použití rozšíření značek se zachovají tímto způsobem v datové proudy uzlu rozhraní .NET Framework XAML Services výchozí – čtečky část cesty zatížení, který je často nemá potřebné XAML schématu kontext k dispozici.  
  
 Pokud pracujete s datový proud uzlu XAML na uložení cestu, obvykle není nic v grafu reprezentaci objektu, který informovat, že objekt k serializaci byl původně poskytované použití rozšíření značek a `ProvideValue` výsledek. Scénáře, které je potřeba zachovat použití rozšíření značek pro odezvy při zaznamenávání také další změny v grafu objektů musíte navrhnout vlastní techniky pro zachování informací o použití rozšíření značek z původní XAML zadejte. Například pokud chcete obnovit použití rozšíření značek, musíte pracovat s datový proud uzlu na uložení cestu, aby bylo možné obnovit použití rozšíření značek nebo provést nějaký typ sloučení mezi původní XAML a zpětné odbavení XAML. Některé XAML implementace architektury například WPF představují případech, kde značek rozšíření použití poskytuje hodnoty pomocí zprostředkující typy (výrazy).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Markup.MarkupExtension>  
 [Převaděče typů a rozšíření značek pro jazyk XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md)  
 [Rozšíření značek a WPF XAML](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)
