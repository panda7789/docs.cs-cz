---
title: Přehled převaděčů typů pro jazyk XAML
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [XAML Services], type converters
- XAML [XAML Services], TypeConverter
- type conversion for XAML [XAML Services]
ms.assetid: 51a65860-efcb-4fe0-95a0-1c679cde66b7
ms.openlocfilehash: c3c69aebacd140a14e74545d601c0207cb8de681
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/27/2020
ms.locfileid: "82071631"
---
# <a name="overview-of-type-converters-for-xaml"></a>Přehled typových převodníků pro XAML

Převaděče typů poskytují logiku pro zapisovač objektů, který se převádí z řetězce v označení XAML na určité objekty v grafu objektu. Ve službě .NET XAML Services musí být převaděč typu třídou, která je odvozena od . <xref:System.ComponentModel.TypeConverter> Některé převaděče také podporují cestu pro uložení XAML a lze jej použít k serializaci objektu do řetězcového formuláře v značkách serializace. Toto téma popisuje, jak a kdy jsou vyvolány převaděče typu v <xref:System.ComponentModel.TypeConverter>XAML a poskytuje poradenství implementace pro přepsání metody .

## <a name="type-conversion-concepts"></a>Koncepty převodu typů

V následujících částech jsou vysvětleny základní pojmy o tom, jak XAML používá řetězce a jak autoři objektů ve službě .NET XAML services používají převaděče typů ke zpracování některých hodnot řetězce, které se vyskytují ve zdroji XAML.

### <a name="xaml-and-string-values"></a>Hodnoty XAML a řetězce

Pokud nastavíte hodnotu atributu v souboru XAML, počáteční typ této hodnoty je řetězec v obecném smyslu a hodnota atributu řetězce ve smyslu XML. Dokonce i další <xref:System.Double> primitiva, jako jsou zpočátku řetězce procesoru XAML.

Ve většině případů procesor XAML potřebuje ke zpracování hodnoty atributu dva informace. První informace je typ hodnoty vlastnosti, která je nastavena. Libovolný řetězec, který definuje hodnotu atributu a který je zpracován v XAML, musí být nakonec převeden nebo vyřešen na hodnotu tohoto typu. Pokud je hodnota primitivní, který je chápán analyzátorem XAML (například číselnou hodnotou), dojde k přímému převodu řetězce. Pokud hodnota atributu odkazuje na výčet, zadaný řetězec je zkontrolován na shodu názvu s pojmenovanou konstantou v tomto výčtu. Pokud hodnota není parser pochopil primitivní nebo konstantní název z výčtu, příslušný typ musí být schopen poskytnout hodnotu nebo odkaz, který je založen na převedený řetězec.

> [!NOTE]
> Direktivy jazyka XAML nepoužívají převaděče typů.

### <a name="type-converters-and-markup-extensions"></a>Převaděče typů a rozšíření o značky

Použití rozšíření značek musí být zpracovány procesorem XAML před tím, než zkontroluje typ vlastnosti a další aspekty. Například pokud vlastnost nastavena jako atribut má obvykle převod typu, ale v konkrétním případě je nastavena použití rozšíření značky, pak chování rozšíření značky procesy jako první. Jedna běžná situace, kdy je nutné rozšíření značky je odkaz na objekt, který již existuje. V tomto scénáři převaděč bezstavového typu může generovat pouze novou instanci, která nemusí být žádoucí. Další informace o rozšířeních značek naleznete v [tématu Markup Extensions for XAML Overview](markup-extensions-overview.md).

### <a name="native-type-converters"></a>Převaděče nativního typu

V implementacích služby WPF (Windows Presentation Foundation) a .NET XAML existují určité typy CLR, které mají nativní zpracování převodu typu. Tyto typy CLR však nejsou konvenčně považovány za primitiva. Příkladem takového typu je <xref:System.DateTime>. Jedním z důvodů je způsob, jakým architektura <xref:System.DateTime> rozhraní .NET Framework funguje: typ je definován v mscorlib, nejzákladnější knihovně v rozhraní .NET. <xref:System.DateTime>není povoleno připsat atribut, který pochází z jiného sestavení, které<xref:System.ComponentModel.TypeConverterAttribute> zavádí závislost (je ze systému). Proto obvyklý typ převaděč zjišťování mechanismus přiřazením nelze podporovat. Místo toho analyzátor XAML má seznam typů, které potřebují nativní zpracování a zpracovává tyto typy podobné způsobu zpracování true primitiv. V případě <xref:System.DateTime>, toto zpracování <xref:System.DateTime.Parse%2A>zahrnuje volání .

## <a name="implementing-a-type-converter"></a>Implementace převaděče typů

Následující části popisují rozhraní <xref:System.ComponentModel.TypeConverter> API třídy.

### <a name="typeconverter"></a>TypeConverter

V části .NET XAML Services jsou všechny převaděče typu, které se <xref:System.ComponentModel.TypeConverter>používají pro účely XAML, třídy, které jsou odvozeny ze základní třídy . Třída <xref:System.ComponentModel.TypeConverter> existovala ve verzích rozhraní .NET Framework před existencí xaml; jedním z <xref:System.ComponentModel.TypeConverter> původních scénářů bylo poskytnout převod řetězců pro editory vlastností v vizuálních návrhářů.

Pro XAML je <xref:System.ComponentModel.TypeConverter> rozšířena role. Pro účely XAML <xref:System.ComponentModel.TypeConverter> je základní třída pro poskytování podpory pro některé převody na řetězec a z řetězce. From-string umožňuje analýzu hodnoty atributu řetězce z XAML. To-string může povolit zpracování hodnoty run-time určité vlastnosti objektu zpět do atributu v XAML pro serializaci.

<xref:System.ComponentModel.TypeConverter>definuje čtyři členy, které jsou relevantní pro převod na řetězec a z řetězce pro účely zpracování XAML:

- <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>

- <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>

- <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>

- <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>

Z těchto členů je <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A>nejdůležitější metodou , která převede vstupní řetězec na požadovaný typ objektu. Metoda <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> může být implementována převést širší rozsah typů do zamýšleného cílového typu převaděče. Proto může sloužit účelům, které přesahují XAML, jako je například podpora převodů za běhu. Pro použití XAML je však důležité pouze <xref:System.String> cesta kódu, který může zpracovat vstup.

Druhou nejdůležitější metodou je <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>. Pokud je aplikace převedena na reprezentaci značek (například pokud je uložena <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> do XAML jako soubor), je zapojen do většíscénář zapisovače textu XAML k vytvoření reprezentace značek. V tomto případě je důležitá cesta kódu pro XAML, když volající předá `destinationType` . <xref:System.String>

<xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>a <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> jsou podpůrné metody, které se používají, <xref:System.ComponentModel.TypeConverter> když služba dotazuje možnosti implementace. Je nutné implementovat `true` tyto metody vrátit pro případy specifické pro typ, které ekvivalentní metody převodu podporují převaděč. Pro účely XAML to <xref:System.String> obecně znamená typ.

### <a name="culture-information-and-type-converters-for-xaml"></a>Informace o jazykové verzi a převaděče typů pro XAML

Každá <xref:System.ComponentModel.TypeConverter> implementace může jednoznačně interpretovat, co je platný řetězec pro převod a může také použít nebo ignorovat popis typu, který je předán jako parametry. Důležitým aspektem pro jazykovou verzi a převod typu XAML je následující: i když použití lokalizovatelných řetězců jako hodnot atributů je podporováno XAML, nelze použít tyto lokalizovatelné řetězce jako vstup převaděče typu s požadavky na konkrétní jazykovou verzi. Toto omezení je, protože převaděče typů pro hodnoty atributů XAML `en-US` zahrnují nutně chování zpracování XAML v pevném jazyce, které používá jazykovou verzi. Další informace o důvodech návrhu tohoto omezení naleznete v jazykové specifikaci XAML ([\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10))) nebo [Přehled globalizace a lokalizace WPF](../../framework/wpf/advanced/wpf-globalization-and-localization-overview.md).

Jako příklad, kde může být problém jazykové verze, některé jazykové verze používají čárku namísto tečky jako oddělovač desetinných bodů pro čísla v řetězcové podobě. Toto použití se srazí s chováním, které mají mnoho existujících převaděčů typu, což je použití čárky jako oddělovače. Předávání jazykové `xml:lang` verze v okolním XAML problém nevyřeší.

### <a name="implementing-convertfrom"></a>Implementace convertfrom

Chcete-li být <xref:System.ComponentModel.TypeConverter> použitelné jako implementace, která <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> podporuje XAML, metoda pro `value` tento převaděč musí přijmout řetězec jako parametr. Pokud je řetězec v platném formátu a <xref:System.ComponentModel.TypeConverter> může být převeden implementací, vrácený objekt musí podporovat přetypování na typ, který je očekáván vlastností. V opačném <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> případě `null`musí být implementace vrácena .

Každá <xref:System.ComponentModel.TypeConverter> implementace může jednoznačně interpretovat, co představuje platný řetězec pro převod a může také použít nebo ignorovat kontexty popisu typu nebo jazykové verze, které jsou předány jako parametry. Zpracování WPF XAML však nemusí předat hodnoty kontextu popisu typu ve všech případech `xml:lang`a také nemusí předat jazykovou verzi založenou na .

> [!NOTE]
> Nepoužívejte závorky{}( ), konkrétně otevírací závorku ({), jako prvek formátu řetězce. Tyto znaky jsou vyhrazeny jako položka a ukončení pro posloupnost rozšíření značek.

Je vhodné vyvolat výjimku, když převaděč typu musí mít přístup ke službě XAML <xref:System.IServiceProvider.GetService%2A> z zapisovače objektů služby .NET XAML Services, ale volání, které je provedeno proti kontextu, tuto službu nevrátí.

### <a name="implementing-convertto"></a>Implementace převodu

<xref:System.ComponentModel.TypeConverter.ConvertTo%2A>je potenciálně používán pro podporu serializace. Podpora serializace <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> prostřednictvím pro vlastní typ a jeho převaděč typu není absolutní požadavek. Pokud však implementujete ovládací prvek nebo používáte serializaci jako součást funkcí nebo <xref:System.ComponentModel.TypeConverter.ConvertTo%2A>návrhu vaší třídy, měli byste implementovat .

Chcete-li být <xref:System.ComponentModel.TypeConverter> použitelné jako implementace, která <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> podporuje XAML, metoda pro tento převaděč musí přijmout `value` instanci typu (nebo hodnotu), která je podporována jako parametr. Pokud `destinationType` je parametr <xref:System.String>typu , vrácený objekt musí <xref:System.String>být možné přetypovat jako . Vrácený řetězec musí představovat `value`serializovanou hodnotu . V ideálním případě by měl být formát serializace, který zvolíte, schopen <xref:System.ComponentModel.TypeConverter.ConvertFrom%2A> generovat stejnou hodnotu, jako kdyby byl tento řetězec předán implementaci stejného převaděče, bez významné ztráty informací.

Pokud hodnotu nelze serializovat nebo převaděč nepodporuje serializaci, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> implementace musí vrátit `null` a může vyvolat výjimku. Pokud však vyvoláte výjimky, měli byste nahlásit neschopnost použít <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> tento převod jako součást implementace, <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> aby byl podporován osvědčený postup kontroly s prvním, abyste se vyhnuli výjimkám.

Pokud `destinationType` parametr není typu <xref:System.String>, můžete si vybrat vlastní zpracování převaděče. Obvykle se vrátíte k základní zpracování implementace, <xref:System.ComponentModel.TypeConverter.ConvertTo%2A> která v základu vyvolá konkrétní výjimku.

Je vhodné vyvolat výjimku, když převaděč typu musí mít přístup ke službě XAML <xref:System.IServiceProvider.GetService%2A> z zapisovače objektů služby .NET XAML Services, ale volání, které je provedeno proti kontextu, tuto službu nevrátí.

### <a name="implementing-canconvertfrom"></a>Implementace CanConvertFrom

Implementace <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A> by `true` se `sourceType` měla <xref:System.String> vrátit pro typ a jinak, odložit na základní implementaci. Nevyvolávat výjimky z <xref:System.ComponentModel.TypeConverter.CanConvertFrom%2A>.

### <a name="implementing-canconvertto"></a>Implementace canconvertto

Implementace <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A> by `true` se `destinationType` měla <xref:System.String>vrátit pro typ a jinak odložit na základní implementaci. Nevyvolávat výjimky z <xref:System.ComponentModel.TypeConverter.CanConvertTo%2A>.

## <a name="applying-the-typeconverterattribute"></a>Použití atributu TypeConverterAttribute

Pro vlastní převaděč typu, který má být použit jako převaděč působícího typu <xref:System.ComponentModel.TypeConverterAttribute> pro vlastní třídu pomocí služby .NET XAML Services, je nutné použít definici třídy. Zadaný <xref:System.ComponentModel.TypeConverterAttribute.ConverterTypeName%2A> prostřednictvím atributu musí být název typu vlastního převaděče typu. Pokud použijete tento atribut, když procesor XAML zpracovává hodnoty, kde typ vlastnosti používá váš vlastní typ třídy, může zadávat řetězce a vrátit instance objektu.

Můžete také zadat převaděč typu na základě vlastnosti. <xref:System.ComponentModel.TypeConverterAttribute> Místo použití definice třídy ji použijte na definici vlastnosti (hlavní definice, `get` / `set` nikoli implementace v ní). Typ vlastnosti musí odpovídat typu, který je zpracován převaděčem vlastního typu. S tímto atributem použít, když procesor XAML zpracovává hodnoty této vlastnosti, může zpracovat vstupní řetězce a vrátit instance objektu. Technika převaděče typu vlastností je užitečná, pokud se rozhodnete použít typ vlastnosti z rozhraní Microsoft .NET <xref:System.ComponentModel.TypeConverterAttribute> Framework nebo z jiné knihovny, kde nelze řídit definici třídy a nelze použít tam.

Chcete-li zadat chování převodu typu pro <xref:System.ComponentModel.TypeConverterAttribute> vlastní `Get` připojený člen, použijte metodu přistupujícího objektu vzoru implementace pro připojený člen.

## <a name="accessing-service-provider-context-from-a-markup-extension-implementation"></a>Přístup k kontextu poskytovatele služeb z implementace rozšíření značek

Dostupné služby jsou stejné pro libovolný převaděč hodnot. Rozdíl je v tom, jak každý převaděč hodnoty obdrží kontext služby. Přístup ke službám a dostupným službám je popsán v tématu [Typ převaděče a Rozšíření značek pro XAML](type-converters-and-markup-extensions.md).

## <a name="type-converters-in-the-xaml-node-stream"></a>Převaděče typů v datovém proudu uzlů XAML

Pokud pracujete s datovým proudem uzlu XAML, akce nebo konečný výsledek převaděče typu ještě není proveden. V cestě zatížení řetězec atributu, který nakonec musí být převeden za typ, aby bylo možné načíst, zůstane jako textová hodnota v rámci počátečního a koncového člena. Převaděč typu, který je nakonec potřebné pro <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> tuto operaci lze určit pomocí vlastnosti. Získání platné hodnoty z <xref:System.Xaml.XamlMember.TypeConverter%2A?displayProperty=nameWithType> však závisí na tom, že máte kontext schématu XAML, který může získat přístup k těmto informacím prostřednictvím základního člena nebo typu hodnoty objektu, který člen používá. Vyvolání chování převodu typu také vyžaduje kontext schématu XAML, protože to vyžaduje mapování typů a vytvoření instance převaděče.

## <a name="see-also"></a>Viz také

- <xref:System.ComponentModel.TypeConverterAttribute>
- [Převaděče typů a rozšíření značek pro jazyk XAML](type-converters-and-markup-extensions.md)
- [Přehled XAML (WPF)](../fundamentals/xaml.md)
