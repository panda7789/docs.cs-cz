---
title: Migrace ze Newtonsoft. JSON na System. text. JSON – .NET
author: tdykstra
ms.author: tdykstra
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 01f94bcfce97da8c71b1b709baa34c2b7509a5e5
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116686"
---
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a>Postup migrace z Newtonsoft. JSON na System. text. JSON

Tento článek ukazuje, jak migrovat z [Newtonsoft. JSON](https://www.newtonsoft.com/json) na <xref:System.Text.Json>.

 `System.Text.Json` se soustředí hlavně na dodržování předpisů pro výkon, zabezpečení a standardy. Obsahuje některé klíčové rozdíly ve výchozím chování a nebrání tomu, aby se `Newtonsoft.Json`. V některých scénářích `System.Text.Json` nemá žádnou vestavěnou funkci, ale existují doporučená řešení. Pro jiné scénáře jsou alternativní řešení nepraktická. Pokud vaše aplikace závisí na chybějící funkci, zvažte možnost nahlásit [problém](https://github.com/dotnet/runtime/issues/new) , abyste zjistili, jestli je možné přidat podporu pro váš scénář.

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

Většinou tohoto článku se dozvíte, jak používat rozhraní <xref:System.Text.Json.JsonSerializer> API, ale obsahuje také pokyny k použití <xref:System.Text.Json.JsonDocument> (který představuje model DOM (Document Object Model) nebo DOM), <xref:System.Text.Json.Utf8JsonReader>a <xref:System.Text.Json.Utf8JsonWriter> typů. Článek je uspořádán do sekcí v následujícím pořadí:

* [Rozdíly ve **výchozím** chování JsonSerializer ve srovnání s Newtonsoft. JSON](#differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson)
* [Scénáře využívající JsonSerializer, které vyžadují alternativní řešení](#scenarios-using-jsonserializer-that-require-workarounds)
* [Scénáře, které JsonSerializer aktuálně nepodporuje](#scenarios-that-jsonserializer-currently-doesnt-support)
* [JsonDocument a JsonElement v porovnání s JToken (jako JObject, JArray)](#jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray)
* [Utf8JsonReader ve srovnání s JsonTextReader](#utf8jsonreader-compared-to-jsontextreader)
* [Utf8JsonWriter ve srovnání s JsonTextWriter](#utf8jsonwriter-compared-to-jsontextwriter)

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a>Rozdíly ve výchozím chování JsonSerializer ve srovnání s Newtonsoft. JSON

ve výchozím nastavení je <xref:System.Text.Json> striktní a vyhnout se případnému odhadu nebo výkladu jménem volajícího a zdůraznění deterministického chování. Knihovna je záměrně navržena tak, aby způsobila výkon a zabezpečení. ve výchozím nastavení je `Newtonsoft.Json` flexibilní. Tento základní rozdíl v návrhu je za mnoho z následujících specifických rozdílů ve výchozím chování.

### <a name="case-insensitive-deserialization"></a>Deserializace bez rozlišování velkých a malých písmen 

Při deserializaci `Newtonsoft.Json` ve výchozím nastavení rozlišovat velikost písmen bez rozlišení velkých a malých písmen. Ve výchozím nastavení <xref:System.Text.Json> rozlišuje velká a malá písmena, což dává lepší výkon, protože se jedná o přesnou shodu. Informace o tom, jak rozlišovat velká a malá písmena, naleznete v tématu [porovnávání vlastností](system-text-json-how-to.md#case-insensitive-property-matching)bez rozlišování velkých a malých písmen.

Pokud používáte `System.Text.Json` nepřímo pomocí ASP.NET Core, nemusíte nic dělat, abyste získali chování jako `Newtonsoft.Json`. ASP.NET Core určuje nastavení [názvů vlastností ve stylu CamelCase-střev](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) a porovnávání bez rozlišení velkých a malých písmen při použití `System.Text.Json`.

### <a name="comments"></a>Komentáře

Při deserializaci `Newtonsoft.Json` ve výchozím nastavení ignorovat komentáře ve formátu JSON. <xref:System.Text.Json> výchozím nastavení je vyvolat výjimky pro komentáře, protože specifikace [RFC 8259](https://tools.ietf.org/html/rfc8259) je neobsahuje. Informace o povolení komentářů najdete v tématu [Povolení komentářů a koncových čárek](system-text-json-how-to.md#allow-comments-and-trailing-commas).

### <a name="trailing-commas"></a>Čárky na konci

Při deserializaci `Newtonsoft.Json` ve výchozím nastavení ignorovat koncové čárky. Ignoruje také více koncových čárek (například `[{"Color":"Red"},{"Color":"Green"},,]`). <xref:System.Text.Json> výchozím nastavení je vyvolat výjimky pro koncové čárky, protože specifikace [RFC 8259](https://tools.ietf.org/html/rfc8259) je nepovoluje. Informace o tom, jak `System.Text.Json` přijmout, najdete v tématu [Povolení komentářů a koncových čárek](system-text-json-how-to.md#allow-comments-and-trailing-commas). Neexistuje žádný způsob, jak povoluje více koncových čárek.

### <a name="json-strings-property-names-and-string-values"></a>Řetězce JSON (názvy vlastností a řetězcové hodnoty)

Při deserializaci `Newtonsoft.Json` akceptuje názvy vlastností, které jsou obklopeny dvojitými uvozovkami, jednoduchými uvozovkami nebo bez uvozovek. Přijímá řetězcové hodnoty obklopené dvojitými uvozovkami nebo jednoduchými uvozovkami. `Newtonsoft.Json` například akceptuje následující kód JSON:

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json` do dvojitých uvozovek akceptují pouze názvy vlastností a řetězcové hodnoty, protože tento formát je vyžadován specifikací [RFC 8259](https://tools.ietf.org/html/rfc8259) a je jediným formátem, který se považuje za platný kód JSON.

Hodnota uzavřená v jednoduchých uvozovkách má za následek [JsonException](xref:System.Text.Json.JsonException) s následující zprávou:

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>Hodnoty nepatřící do řetězce pro vlastnosti řetězce

`Newtonsoft.Json` přijímá hodnoty, které nejsou řetězcem, jako je číslo nebo literály `true` a `false`pro deserializaci vlastností typu String. Tady je příklad JSON, který `Newtonsoft.Json` úspěšně deserializovat do následující třídy:

```json
{
  "String1": 1,
  "String2": true,
  "String3": false
}
```

```csharp
public class ExampleClass
{
    public string String1 { get; set; }
    public string String2 { get; set; }
    public string String3 { get; set; }
}
```

`System.Text.Json` neprovádí deserializaci hodnot, které nejsou řetězcové, do vlastností řetězce. Neřetězcová hodnota přijatá pro pole typu String má za následek [JsonException](xref:System.Text.Json.JsonException) s následující zprávou:

```
The JSON value could not be converted to System.String.
```

### <a name="converter-registration-precedence"></a>Priorita registrace převaděče

`Newtonsoft.Json` priorita registrace pro vlastní převaděče je následující:

* Atribut u vlastnosti
* Atribut u typu
* Kolekce [převaděčů](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm)

Toto pořadí znamená, že vlastní převaděč v kolekci `Converters` je přepsán převaděčem, který je zaregistrován použitím atributu na úrovni typu. Oba tyto registrace jsou přepsány atributem na úrovni vlastnosti.

<xref:System.Text.Json> priorita registrace pro vlastní převaděče se liší:

* Atribut u vlastnosti
* kolekce <xref:System.Text.Json.JsonSerializerOptions.Converters>
* Atribut u typu

Rozdíl je v tom, že vlastní převaděč v kolekci `Converters` Přepisuje atribut na úrovni typu. Záměrem na základě tohoto pořadí priorit je provést změny v době návrhu v době běhu. Neexistuje žádný způsob, jak změnit prioritu.

Další informace o registraci vlastního převaděče najdete v tématu [registrace vlastního převaděče](system-text-json-converters-how-to.md#register-a-custom-converter).

### <a name="character-escaping"></a>Znakové uvozovací znaky

Během serializace je `Newtonsoft.Json` relativně opravňující k tomu, aby bylo umožněno použití znaků bez uvozovacích znaků. To znamená, že je nenahrazuje pomocí `\uxxxx`, kde `xxxx` je znakový bod znaku. Tam, kde je řídí, vygeneruje `\` před znakem (například `"` se bude `\"`). ve výchozím nastavení <xref:System.Text.Json> sekvence více znaků, aby bylo zajištěno důkladné ochrany proti skriptování mezi weby (XSS) nebo útokům prostřednictvím odhalení informací a k tomu využívá sekvenci šesti znaků. `System.Text.Json` ve výchozím nastavení zařídí všechny znaky jiné než ASCII, takže nemusíte nic dělat, pokud používáte `StringEscapeHandling.EscapeNonAscii` v `Newtonsoft.Json`. ve výchozím nastavení `System.Text.Json` také řídí znaky citlivé na kód HTML. Informace o tom, jak přepsat výchozí chování `System.Text.Json`, naleznete v tématu [přizpůsobení kódování znaků](system-text-json-how-to.md#customize-character-encoding).

### <a name="deserialization-of-object-properties"></a>Deserializace vlastností objektu

Když `Newtonsoft.Json` deserializace pro `object` vlastnosti v POCOs nebo ve slovnících typu `Dictionary<string, object>`, je:

* Odvodí typ primitivních hodnot v datové části JSON (jiné než `null`) a vrátí uložené `string`, `long`, `double`, `boolean`nebo `DateTime` jako zabalený objekt. *Primitivní hodnoty* jsou jednoduché hodnoty JSON, jako je číslo JSON, řetězec, `true`, `false`nebo `null`.
* Vrátí `JObject` nebo `JArray` pro komplexní hodnoty v datové části JSON. *Komplexní hodnoty* jsou kolekce párů klíč-hodnota JSON v rámci složených závorek (`{}`) nebo seznamů hodnot v závorkách (`[]`). Vlastnosti a hodnoty v závorkách nebo závorkách mohou mít další vlastnosti nebo hodnoty.
* Vrátí odkaz s hodnotou null, pokud má datová část literál `null` JSON.

<xref:System.Text.Json> ukládá zabalenou `JsonElement` pro primitivní i komplexní hodnoty v rámci vlastnosti `System.Object` nebo hodnoty slovníku. Zpracovává se ale `null` stejné jako `Newtonsoft.Json` a vrátí odkaz s hodnotou null, pokud je v datové části obsažený `null` literál JSON.

Chcete-li implementovat odvození typu pro vlastnosti `object`, vytvořte pomocí převaděče jako příklad [psaní vlastních převaděčů](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties).

### <a name="maximum-depth"></a>Maximální hloubka

ve výchozím nastavení nemá `Newtonsoft.Json` maximální hloubkový limit. Pro <xref:System.Text.Json> existuje výchozí limit 64 a je možné ho nakonfigurovat nastavením <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>.

### <a name="omit-null-value-properties"></a>Vynechat vlastnosti hodnoty null

`Newtonsoft.Json` má globální nastavení, které způsobuje vyloučení vlastností hodnoty null z serializace: [NullValueHandling. Ignore](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_NullValueHandling.htm). Odpovídající možnost v <xref:System.Text.Json> je <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues%2A>.

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a>Scénáře využívající JsonSerializer, které vyžadují alternativní řešení

Následující scénáře nejsou podporovány integrovanými funkcemi, ale pro alternativní řešení je k dispozici vzorový kód. Většina alternativních řešení vyžaduje, abyste implementovali [vlastní převaděče](system-text-json-converters-how-to.md).

### <a name="specify-date-format"></a>Zadat formát data

`Newtonsoft.Json` poskytuje několik způsobů, jak řídit, jak vlastnosti `DateTime` a `DateTimeOffset` typy jsou serializovány a deserializovány:

* Nastavení `DateTimeZoneHandling` lze použít k serializaci všech `DateTime`ch hodnot jako data UTC.
* Nastavení `DateFormatString` a převaděče `DateTime` lze použít k přizpůsobení formátu řetězce data.

V <xref:System.Text.Json>je jediným formátem, který má integrovanou podporu, ISO 8601-1:2019, protože je široce přijatý, jednoznačně nejednoznačný a způsobuje přesné zpoždění. Pokud chcete použít jiný formát, vytvořte vlastní převaděč. Další informace najdete v tématu [Podpora DateTime a DateTimeOffset v System. text. JSON](../datetime/system-text-json-support.md).

### <a name="quoted-numbers"></a>Čísla v uvozovkách

`Newtonsoft.Json` mohou serializovat nebo deserializovat čísla reprezentovaná řetězci JSON (obklopenými uvozovkami). Například může přijmout: `{"DegreesCelsius":"23"}` místo `{"DegreesCelsius":23}`. Chcete-li toto chování povolit v <xref:System.Text.Json>, implementujte vlastní převaděč podobný následujícímu příkladu. Převaděč zpracovává vlastnosti definované jako `long`:

* Jejich serializace jako řetězce JSON. 
* Při deserializaci přijímá čísla a čísla JSON v rámci uvozovek.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

Tento vlastní převaděč Zaregistrujte [pomocí atributu](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) u jednotlivých vlastností `long` nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekce <xref:System.Text.Json.JsonSerializerOptions.Converters>.

### <a name="dictionary-with-non-string-key"></a>Slovník s jiným než řetězcovým klíčem

`Newtonsoft.Json` podporuje kolekce typu `Dictionary<TKey, TValue>`. Integrovaná podpora kolekcí slovníků v <xref:System.Text.Json> je omezená na `Dictionary<string, TValue>`. To znamená, že klíč musí být řetězec.

Pro podporu slovníku s celým číslem nebo jiným typem jako klíč vytvořte konvertor jako příklad v tématu [jak psát vlastní převaděče](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key).

### <a name="polymorphic-serialization"></a>Polymorfní serializace

`Newtonsoft.Json` automaticky provede polymorfní serializaci. Informace o možnostech omezeného polymorfní serializace <xref:System.Text.Json>najdete v tématu [serializace properties of Derived Classes](system-text-json-how-to.md#serialize-properties-of-derived-classes).

Alternativní řešení je popsáno pro definování vlastností, které mohou obsahovat odvozené třídy jako typ `object`. Pokud to není možné, je další možností vytvoření převaděče s `Write` metodou pro celou hierarchii typu dědičnosti, jako je například příklad [psaní vlastních převaděčů](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

### <a name="polymorphic-deserialization"></a>Polymorfní deserializace

`Newtonsoft.Json` má `TypeNameHandling` nastavení, které při serializaci přidá do formátu JSON metadata typu Type. Používá metadata při deserializaci k provedení polymorfního deserializace. <xref:System.Text.Json> může provádět omezený rozsah [polymorfní serializace](system-text-json-how-to.md#serialize-properties-of-derived-classes) , ale ne polymorfní deserializace.

Pro podporu polymorfního deserializace vytvořte jako příklad v [postupu psaní vlastních převaděčů](system-text-json-converters-how-to.md#support-polymorphic-deserialization)převaděč.

### <a name="required-properties"></a>Požadované vlastnosti

Při deserializaci <xref:System.Text.Json> nevyvolá výjimku, pokud není ve formátu JSON přijata žádná hodnota pro jednu z vlastností cílového typu. Například pokud máte třídu `WeatherForecast`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

Následující kód JSON je deserializovaný bez chyby:

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

Chcete-li, aby deserializace selhala v případě, že ve formátu JSON není žádná vlastnost `Date`, implementujte vlastní převaděč. Následující ukázkový kód převaděče vyvolá výjimku, pokud vlastnost `Date` není nastavena po dokončení deserializace:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

Zaregistrujte tento vlastní převaděč [pomocí atributu ve třídě POCO](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekce <xref:System.Text.Json.JsonSerializerOptions.Converters>.

Pokud budete postupovat podle tohoto vzoru, nepředávejte objekt Options při rekurzivním volání <xref:System.Text.Json.JsonSerializer.Serialize%2A> nebo <xref:System.Text.Json.JsonSerializer.Deserialize%2A>. Objekt Options obsahuje kolekci <xref:System.Text.Json.JsonSerializerOptions.Converters%2A>. Pokud ho předáte do `Serialize` nebo `Deserialize`, vlastní převaděč zavolá sám sebe a vytvoří nekonečnou smyčku, která způsobí výjimku přetečení zásobníku. Pokud výchozí možnosti nejsou proveditelné, vytvořte novou instanci možností s nastavením, které potřebujete. Tento přístup bude pomalý, protože každá nová instance mezipamětí nezávisle.

Předchozí kód převaděče je zjednodušený příklad. Pokud potřebujete zpracovat atributy (například [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) nebo jiné možnosti (například vlastní kodéry), bude nutné další logiku. Kromě toho ukázkový kód nezpracovává vlastnosti, pro které je v konstruktoru nastavena výchozí hodnota. A tento přístup nerozlišuje mezi následujícími scénáři:

* Ve formátu JSON chybí vlastnost.
* Vlastnost pro typ, který nepovoluje hodnotu null, je přítomna ve formátu JSON, ale hodnota je výchozím typem pro typ, například nula pro `int`.
* Vlastnost pro typ s povolenou hodnotou null je k dispozici ve formátu JSON, ale hodnota je null.

### <a name="deserialize-null-to-non-nullable-type"></a>Deserializovat hodnotu null na typ, který není možnou hodnotou null 

`Newtonsoft.Json` nevyvolá výjimku v následujícím scénáři:

* `NullValueHandling` je nastavené na `Ignore`a
* Při deserializaci obsahuje JSON hodnotu null pro typ, který nemůže mít hodnotu null.

Ve stejném scénáři <xref:System.Text.Json> vyvolá výjimku. (Odpovídající nastavení zpracování hodnoty null je <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>.)

Pokud vlastníte cílový typ, nejlepším řešením je učinit vlastnost dotazovat se na hodnotu null (například změnit `int` na `int?`).

Dalším řešením je vytvořit převaděč pro typ, například následující příklad, který zpracovává hodnoty null pro `DateTimeOffset` typy:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

Tento vlastní převaděč Zaregistrujte [pomocí atributu u vlastnosti](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekce <xref:System.Text.Json.JsonSerializerOptions.Converters>.

**Poznámka:** Předchozí převaděč **zpracovává hodnoty null jinak** než `Newtonsoft.Json` pro POCOs, které určují výchozí hodnoty. Předpokládejme například, že následující kód představuje cílový objekt:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

A Předpokládejme, že následující JSON je deserializovat pomocí předchozího převaděče:

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Po deserializaci má vlastnost `Date` hodnotu 1/1/0001 (`default(DateTimeOffset)`), což znamená, že hodnota nastavená v konstruktoru je přepsána. Pro stejné POCO a JSON `Newtonsoft.Json` deserializace ponechá 1/1/2001 ve vlastnosti `Date`.

### <a name="deserialize-to-immutable-classes-and-structs"></a>Deserializace pro neměnné třídy a struktury

`Newtonsoft.Json` může deserializovat pro neměnné třídy a struktury, protože může používat konstruktory s parametry. <xref:System.Text.Json> podporuje pouze veřejné konstruktory bez parametrů. Jako alternativní řešení můžete volat konstruktor s parametry ve vlastním převaděči.

Tady je neproměnlivá struktura s více parametry konstruktoru:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

A zde je převaděč, který serializace a deserializace této struktury:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

Zaregistrujte tento vlastní převaděč [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekce <xref:System.Text.Json.JsonSerializerOptions.Converters>.

Příklad podobného převaděče, který zpracovává otevřené generické vlastnosti, naleznete v [integrovaném převaděči pro páry klíč-hodnota](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs).

### <a name="specify-constructor-to-use"></a>Zadejte konstruktor, který se má použít.

Atribut `Newtonsoft.Json` `[JsonConstructor]` umožňuje určit, který konstruktor se má volat při deserializaci do POCO. <xref:System.Text.Json> podporuje pouze konstruktory bez parametrů. Jako alternativní řešení můžete zavolat libovolný konstruktor, který potřebujete, ve vlastním převaděči. Podívejte se na příklad pro [deserializaci pro neměnné třídy a struktury](#deserialize-to-immutable-classes-and-structs).

### <a name="conditionally-ignore-a-property"></a>Podmíněně ignorovat vlastnost

`Newtonsoft.Json` má několik způsobů, jak podmíněně ignorovat vlastnost při serializaci nebo deserializaci:

* `DefaultContractResolver` umožňuje vybrat vlastnosti, které se mají zahrnout nebo vyloučit, na základě libovolného kritéria. 
* Nastavení `NullValueHandling` a `DefaultValueHandling` na `JsonSerializerSettings` umožňují určit, že všechny vlastnosti null-Value nebo Default-value by měly být ignorovány.
* Nastavení `NullValueHandling` a `DefaultValueHandling` na atributu `[JsonProperty]` umožňují zadat jednotlivé vlastnosti, které by měly být ignorovány, pokud je nastavena hodnota null nebo výchozí hodnota.

<xref:System.Text.Json> poskytuje následující způsoby, jak vynechat vlastnosti při serializaci:

* Atribut [[JsonIgnore]](system-text-json-how-to.md#exclude-individual-properties) u vlastnosti způsobí, že vlastnost bude při serializaci vynechána ve formátu JSON.
* Globální možnost [IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) umožňuje vyloučit všechny vlastnosti s hodnotou null.
* Globální možnost [IgnoreReadOnlyProperties](system-text-json-how-to.md#exclude-all-read-only-properties) umožňuje vyloučit všechny vlastnosti jen pro čtení.

Tyto možnosti **vám** neumožňují:

* Ignorovat všechny vlastnosti, které mají výchozí hodnotu pro typ.
* Ignoruje vybrané vlastnosti, které mají výchozí hodnotu pro daný typ.
* Ignoruje vybrané vlastnosti, pokud jejich hodnota je null.
* Ignorovat vybrané vlastnosti na základě libovolných kritérií vyhodnocených v době běhu. 

Pro tuto funkci můžete napsat vlastní převaděč. Tady je ukázkový POCO a vlastní převaděč, který ilustruje tento přístup:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

Převaděč způsobí, že vlastnost `Summary` bude vynechána z serializace, je-li její hodnota null, prázdný řetězec nebo "N/A". 

Zaregistrujte tento vlastní převaděč [pomocí atributu ve třídě](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekce <xref:System.Text.Json.JsonSerializerOptions.Converters>.

Tento přístup vyžaduje další logiku v těchto případech:

* POCO obsahuje komplexní vlastnosti.
* Je nutné zpracovat atributy, jako například `[JsonIgnore]` nebo možnosti, jako jsou například vlastní kodéry.

### <a name="callbacks"></a>Zpětná volání

`Newtonsoft.Json` umožňuje spustit vlastní kód v několika bodech v procesu serializace nebo deserializace:

* OnDeserializing (při zahájení deserializace objektu)
* OnDeserialized (po dokončení deserializace objektu)
* Probíhá serializace (při zahájení serializace objektu)
* V-deserializovat (po dokončení serializace objektu)

V <xref:System.Text.Json>můžete volání simulovat pomocí vlastního převaděče. Následující příklad ukazuje vlastní převaděč pro POCO. Převaděč obsahuje kód, který zobrazí zprávu v každém bodě, který odpovídá zpětnému volání `Newtonsoft.Json`.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

Zaregistrujte tento vlastní převaděč [pomocí atributu ve třídě](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) nebo [přidáním převaděče](system-text-json-converters-how-to.md#registration-sample---converters-collection) do kolekce <xref:System.Text.Json.JsonSerializerOptions.Converters>.

Pokud používáte vlastní převaděč, který odpovídá předchozí ukázce:

* Kód `OnDeserializing` nemá přístup k nové instanci POCO. Chcete-li pracovat s novou instancí POCO na začátku deserializace, vložte tento kód do konstruktoru POCO.
* Nepředávejte v objektu Options při rekurzivním volání `Serialize` nebo `Deserialize`. Objekt Options obsahuje kolekci `Converters`. Pokud jej předáte do `Serialize` nebo `Deserialize`, bude použit konvertor, což vede k nekonečnou smyčku, která způsobí výjimku přetečení zásobníku.

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a>Scénáře, které JsonSerializer aktuálně nepodporuje

Alternativní řešení jsou možná pro následující scénáře, ale některé z nich by bylo poměrně obtížné implementovat. Tento článek neposkytuje ukázky kódu pro alternativní řešení těchto scénářů.

Nejedná se o vyčerpávající seznam funkcí `Newtonsoft.Json`, které nemají v `System.Text.Json`žádné ekvivalenty. Seznam obsahuje mnoho scénářů, které byly vyžádány v rámci [problémů GitHubu](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) nebo [StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json) příspěvky.

Pokud implementujete alternativní řešení pro jeden z těchto scénářů a můžete ho sdílet, vyberte v dolní části stránky tlačítko "**Tato stránka**". Tím se vytvoří problém GitHubu a přidá se k problémům, které jsou uvedeny v dolní části stránky.

### <a name="types-without-built-in-support"></a>Typy bez integrované podpory

<xref:System.Text.Json> nenabízí integrovanou podporu pro následující typy:

* <xref:System.Data.DataTable> a související typy
* F#typy, například [rozlišené sjednocení](../../fsharp/language-reference/discriminated-unions.md), [typy záznamů](../../fsharp/language-reference/records.md)a [anonymní typy záznamů](../../fsharp/language-reference/anonymous-records.md).
* Typy kolekce v oboru názvů <xref:System.Collections.Specialized>
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple> a přidružené obecné typy

Vlastní převaděče lze implementovat pro typy, které nemají vestavěnou podporu.

### <a name="public-and-non-public-fields"></a>Veřejná a neveřejná pole

`Newtonsoft.Json` mohou serializovat a deserializovat pole a také vlastnosti. <xref:System.Text.Json> funguje pouze s veřejnými vlastnostmi. Tato funkce může poskytnout vlastní převaděče.

### <a name="internal-and-private-property-setters-and-getters"></a>Interní a privátní vlastnosti setter a getter

`Newtonsoft.Json` může použít nastavení privátních a vnitřních vlastností a getter prostřednictvím atributu `JsonProperty`. <xref:System.Text.Json> podporuje pouze veřejné metody setter. Tato funkce může poskytnout vlastní převaděče.

### <a name="preserve-object-references-and-handle-loops"></a>Zachovat odkazy na objekty a zpracovávat smyčky

Ve výchozím nastavení `Newtonsoft.Json` serializovat podle hodnoty. Například pokud objekt obsahuje dvě vlastnosti, které obsahují odkaz na stejný objekt `Person`, hodnoty vlastností objektu `Person` jsou duplikovány ve formátu JSON.

`Newtonsoft.Json` má `PreserveReferencesHandling` nastavení na `JsonSerializerSettings`, které umožňuje serializaci podle odkazu:

* Metadata identifikátoru jsou přidána do formátu JSON vytvořeného pro první objekt `Person`.
* KÓD JSON, který je vytvořen pro druhý objekt `Person` obsahuje odkaz na tento identifikátor namísto hodnot vlastností.

`Newtonsoft.Json` má také nastavení `ReferenceLoopHandling`, které umožňuje ignorovat cyklické odkazy namísto vyvolání výjimky.

<xref:System.Text.Json> podporuje pouze serializaci podle hodnoty a vyvolá výjimku pro cyklické odkazy.

### <a name="systemruntimeserialization-attributes"></a>Atributy System. Runtime. Serialization

<xref:System.Text.Json> nepodporuje atributy z oboru názvů `System.Runtime.Serialization`, jako je například `DataMemberAttribute` a `IgnoreDataMemberAttribute`.

### <a name="octal-numbers"></a>Osmičková čísla

`Newtonsoft.Json` zachází s čísly s úvodní nulou jako osmičková čísla. <xref:System.Text.Json> nepovoluje úvodní nuly, protože specifikace [RFC 8259](https://tools.ietf.org/html/rfc8259) je nepovoluje.

### <a name="populate-existing-objects"></a>Naplnit existující objekty

Metoda `JsonConvert.PopulateObject` v `Newtonsoft.Json` deserializace dokumentu JSON na existující instanci třídy místo vytvoření nové instance. <xref:System.Text.Json> vždy vytvoří novou instanci cílového typu pomocí výchozího veřejného konstruktoru bez parametrů. Vlastní převaděče mohou být deserializovány na existující instanci.

### <a name="reuse-rather-than-replace-properties"></a>Znovu použít místo nahrazení vlastností

Nastavení `ObjectCreationHandling` `Newtonsoft.Json` umožňuje určit, že se mají při deserializaci znovu použít objekty ve vlastnostech, a ne nahradit. <xref:System.Text.Json> vždy nahrazuje objekty ve vlastnostech.  Tato funkce může poskytnout vlastní převaděče.

### <a name="add-to-collections-without-setters"></a>Přidat do kolekcí bez setter

Při deserializaci `Newtonsoft.Json` přidává objekty do kolekce i v případě, že vlastnost nemá metodu setter. <xref:System.Text.Json> ignoruje vlastnosti, které nemají setter. Tato funkce může poskytnout vlastní převaděče.

### <a name="missingmemberhandling"></a>MissingMemberHandling

`Newtonsoft.Json` lze nakonfigurovat tak, aby vyvolal výjimky během deserializace, pokud JSON obsahuje vlastnosti, které chybí v cílovém typu. <xref:System.Text.Json> ignoruje další vlastnosti ve formátu JSON, s výjimkou použití [atributu [JsonExtensionData]](system-text-json-how-to.md#handle-overflow-json). Pro chybějící funkci člena není k dispozici žádné alternativní řešení.

### <a name="tracewriter"></a>TraceWriter

`Newtonsoft.Json` umožňuje ladění pomocí `TraceWriter` k zobrazení protokolů, které jsou generovány pomocí serializace nebo deserializace. <xref:System.Text.Json> neprovádí protokolování.

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>JsonDocument a JsonElement v porovnání s JToken (jako JObject, JArray)

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> poskytuje možnost analyzovat a sestavit model DOM (Document Object Model) modelu DOM (jen **pro čtení** ) z existujících datových částí JSON. Model DOM poskytuje náhodný přístup k datům v datové části JSON. K elementům JSON, které tvoří datovou část, lze přistupovat prostřednictvím <xref:System.Text.Json.JsonElement>ho typu. Typ `JsonElement` poskytuje rozhraní API pro převod textu JSON na běžné typy .NET. `JsonDocument` zpřístupňuje vlastnost <xref:System.Text.Json.JsonDocument.RootElement>.

### <a name="jsondocument-is-idisposable"></a>JsonDocument je IDisposable

`JsonDocument` vytvoří zobrazení dat v paměti do fondu vyrovnávací paměti. Proto na rozdíl od `JObject` nebo `JArray` z `Newtonsoft.Json`, typ `JsonDocument` implementuje `IDisposable` a musí být použit uvnitř bloku using. 

Jenom `JsonDocument` z rozhraní API, pokud chcete přenést vlastnictví životnosti a zařadit odpovědnost volajícímu. Ve většině scénářů to není nutné. Pokud volající potřebuje pracovat s celým dokumentem JSON, vraťte <xref:System.Text.Json.JsonElement.Clone%2A> <xref:System.Text.Json.JsonDocument.RootElement%2A>, což je <xref:System.Text.Json.JsonElement>. Pokud volající potřebuje pracovat s konkrétním prvkem v dokumentu JSON, vraťte <xref:System.Text.Json.JsonElement.Clone%2A> tohoto <xref:System.Text.Json.JsonElement>. Pokud vrátíte `RootElement` nebo dílčí prvek přímo bez provedení `Clone`, volající nebude moci získat přístup k vráceným `JsonElement` po `JsonDocument`, který je vlastníkem, je uvolněn.

Tady je příklad, který vyžaduje, abyste provedli `Clone`:

```csharp
public JsonElement LookAndLoad(JsonElement source)
{
    string json = File.ReadAllText(source.GetProperty("fileName").GetString());
   
    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        return doc.RootElement.Clone();
    }
}
```

Předchozí kód očekává `JsonElement`, který obsahuje vlastnost `fileName`. Otevře soubor JSON a vytvoří `JsonDocument`. Metoda předpokládá, že volající chce pracovat s celým dokumentem, a vrátí `Clone` `RootElement`. 

Pokud obdržíte `JsonElement` a vrátíte dílčí prvek, není nutné vracet `Clone` dílčího prvku. Volající je zodpovědný za udržování naživu `JsonDocument`, do kterého patří předaný `JsonElement`. Příklad:

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument je jen pro čtení.

<xref:System.Text.Json> DOM nemůže přidávat, odebírat ani upravovat elementy JSON. Je navržený tak, aby se snížil výkon a omezila se alokace při analýze běžných velikostí datových částí JSON (tj. < 1 MB). Pokud váš scénář aktuálně používá upravitelný model DOM, může být možné provést jedno z následujících řešení:

* Chcete-li vytvořit `JsonDocument` od začátku (to znamená, že bez předání existující datové části JSON do metody `Parse`), zapište text JSON pomocí `Utf8JsonWriter` a analyzujte výstup z tohoto objektu a vytvořte nový `JsonDocument`.
* Chcete-li upravit existující `JsonDocument`, použijte ji k zápisu textu JSON, provádění změn při psaní a analýzou výstupu z něj vytvořte nový `JsonDocument`.
* K sloučení existujících dokumentů JSON, které jsou ekvivalentní `JObject.Merge` nebo `JContainer.Merge` rozhraní API z `Newtonsoft.Json`, se podívejte na [Tento problém GitHubu](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853).

### <a name="jsonelement-is-a-union-struct"></a>JsonElement je struktura sjednocení.

`JsonDocument` zpřístupňuje `RootElement` jako vlastnost typu <xref:System.Text.Json.JsonElement>, což je sjednocení, typ struktury, který zahrnuje jakýkoli element JSON. `Newtonsoft.Json` používá vyhrazené hierarchické typy jako `JObject`,`JArray`, `JToken`a tak dále. `JsonElement` je to, co můžete hledat a vyčíslit a můžete použít `JsonElement` k vyhodnotit prvků JSON do typů .NET.

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>Jak vyhledávat JsonDocument a JsonElement pro dílčí prvky

Vyhledává tokeny JSON pomocí `JObject` nebo `JArray` z `Newtonsoft.Json` je obvykle relativně rychlá, protože jsou vyhledávání v některém slovníku. Na základě porovnání vyhledává `JsonElement` vyžadují sekvenční hledání vlastností, a proto je poměrně pomalé (například při použití `TryGetProperty`). <xref:System.Text.Json> je navržena tak, aby minimalizovala čas počáteční analýzy, nikoli čas vyhledávání. Proto pomocí následujících přístupů Optimalizujte výkon při hledání prostřednictvím objektu `JsonDocument`:

* Místo vlastního indexování nebo smyček použijte předdefinované enumerátory (<xref:System.Text.Json.JsonElement.EnumerateArray%2A> a <xref:System.Text.Json.JsonElement.EnumerateObject%2A>).
* Neprovádějte sekvenční hledání celého `JsonDocument` přes každou vlastnost pomocí `RootElement`. Místo toho hledejte ve vnořených objektech JSON na základě známé struktury dat JSON. Například pokud hledáte vlastnost `Grade` v objektech `Student`, procházejte smyčkou objektů `Student` a získejte hodnotu `Grade` pro každou místo hledání `JsonElement`ch objektů, které hledají `Grade` vlastnosti. V takovém případě by to vedlo k zbytečnému průchodu se stejnými daty.

Příklad kódu naleznete v tématu [použití JsonDocument pro přístup k datům](system-text-json-how-to.md#use-jsondocument-for-access-to-data).

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader ve srovnání s JsonTextReader

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> je pro text JSON s kódováním UTF-8 s vysokým výkonem vysokého výkonu, který je určený jen pro čtení, načtený z [ReadOnlySpan\<bajtů >](xref:System.ReadOnlySpan%601) nebo [ReadOnlySequence\<bajtů >](xref:System.Buffers.ReadOnlySequence%601). `Utf8JsonReader` je typ nízké úrovně, který lze použít k vytvoření vlastních analyzátorů a deserializace.

Následující části vysvětlují Doporučené programovací vzory pro použití `Utf8JsonReader`.

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JsonReader je struktura ref.

Vzhledem k tomu, že `Utf8JsonReader` typ je *Struktura ref*, má [určitá omezení](../../csharp/language-reference/keywords/ref.md#ref-struct-types). Například nemůže být uložen jako pole ve třídě nebo struktuře jiné než struktura ref. Aby se dosáhlo vysokého výkonu, musí být tento typ `ref struct`, protože musí ukládat do mezipaměti vstupní [\<bajtů](xref:System.ReadOnlySpan%601), která je sama strukturou ref. Tento typ je navíc proměnlivý, protože obsahuje stav. Proto **jej předejte pomocí ref** , nikoli podle hodnoty. Předání podle hodnoty by vedlo k kopírování struktury a změny stavu by pro volajícího neměly být viditelné. To se liší od `Newtonsoft.Json`, protože `Newtonsoft.Json` `JsonTextReader` je třída. Další informace o použití struktur ref, najdete v tématu [Zápis bezpečného a efektivního C# kódu](../../csharp/write-safe-efficient-code.md).

### <a name="read-utf-8-text"></a>Číst text v kódování UTF-8

Abyste dosáhli nejlepšího možného výkonu při použití `Utf8JsonReader`, číst datové části JSON, které jsou už kódované jako text UTF-8, a ne jako řetězce UTF-16. Příklad kódu naleznete v tématu [Filter data using Utf8JsonReader](system-text-json-how-to.md#filter-data-using-utf8jsonreader).

### <a name="read-with-a-stream-or-pipereader"></a>Čtení s datovým proudem nebo PipeReader

`Utf8JsonReader` podporuje čtení z [ReadOnlySpan\<bajtů](xref:System.ReadOnlySpan%601) kódovaných v kódování UTF-8 > nebo [ReadOnlySequence\<bajtů](xref:System.Buffers.ReadOnlySequence%601) (což je výsledek čtení z >).

Pro synchronní čtení můžete načíst datovou část JSON až do konce datového proudu do pole bajtů a předat je do čtecího zařízení. Pro čtení z řetězce (který je kódován jako UTF-16) volejte <xref:System.Text.Encoding.UTF8>.<xref:System.Text.Encoding.GetBytes%2A> pro první překódování řetězce do kódovaného bajtového pole UTF-8. Pak předejte tuto `Utf8JsonReader`. 

Vzhledem k tomu, že `Utf8JsonReader` považuje vstup za text JSON, znamená to, že znak pořadí bajtů UTF-8 (BOM) se považuje za neplatný JSON. Volající musí tuto funkci před předáním dat do čtecího modulu filtrovat.

Příklady kódu naleznete v tématu [Use Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader).

### <a name="read-with-multi-segment-readonlysequence"></a>Čtení s více segmenty ReadOnlySequence

Pokud je váš vstup ve formátu JSON [ReadOnlySpan\<](xref:System.ReadOnlySpan%601), ke každému elementu JSON se dá získat přístup z vlastnosti `ValueSpan` ve čtečce při procházení smyčky pro čtení. Pokud je však vstup [ReadOnlySequence\<bajt >](xref:System.Buffers.ReadOnlySequence%601) (což je výsledek čtení z <xref:System.IO.Pipelines.PipeReader>), mohou některé elementy JSON přetažný více segmentů objektu `ReadOnlySequence<byte>`. Tyto prvky nebudou přístupné z <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> v souvislém bloku paměti. Místo toho, když máte jako vstup více segmentů `ReadOnlySequence<byte>`, Dotazujte vlastnost <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> na čtečce, abyste zjistili, jak získat přístup k aktuálnímu elementu JSON. Tady je doporučený vzor:

```csharp
while (reader.Read())
{
    switch (reader.TokenType)
    {
        // ...
        ReadOnlySpan<byte> jsonElement = reader.HasValueSequence ?
            reader.ValueSequence.ToArray() :
            reader.ValueSpan;
        // ...
    }
}
```

### <a name="use-valuetextequals-for-property-name-lookups"></a>Pro vyhledávání názvů vlastností použijte ValueTextEquals

Nepoužívejte <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> k provádění porovnávání po bajtech voláním <xref:System.MemoryExtensions.SequenceEqual%2A> pro vyhledávání názvů vlastností. Místo toho zavolejte <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A>, protože tato metoda odřídí všechny znaky, které jsou ve formátu JSON uvozené řídicím znakem. Tady je příklad, který ukazuje, jak vyhledat vlastnost s názvem "Name":

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>Čtení hodnot null na typy hodnot s možnou hodnotou null

`Newtonsoft.Json` poskytuje rozhraní API, která vracejí <xref:System.Nullable%601>, jako je například `ReadAsBoolean`, která zpracovává `Null` `TokenType` za vás vrácením `bool?`. Vestavěná `System.Text.Json` rozhraní API vracejí pouze nehodnotové typy, které neumožňují hodnotu null. Například <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> vrátí `bool`. Vyvolá výjimku, pokud nalezne `Null` ve formátu JSON. Následující příklady znázorňují dva způsoby, jak zpracovat hodnoty null, jednu vrácením typu hodnoty s možnou hodnotou null a jedním vrácením výchozí hodnoty:

```csharp
public bool? ReadAsNullableBoolean()
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return null;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

```csharp
public bool ReadAsBoolean(bool defaultValue)
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return defaultValue;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

### <a name="multi-targeting"></a>Cílení na více platforem

Pokud potřebujete nadále používat `Newtonsoft.Json` pro určité cílové architektury, můžete mít více cílů a mít dvě implementace. To ale není triviální a vyžaduje `#ifdefs` a duplikování zdroje. Jedním ze způsobů, jak sdílet co nejvíc kódů, je vytvořit `ref struct` Obálka kolem `Utf8JsonReader` a `Newtonsoft.Json` `JsonTextReader`. Tato obálka sjednotí oblast veřejného povrchu a současně izoluje rozdíly v chování. To vám umožní izolovat změny hlavně pro konstrukci typu, spolu s předáním nového typu kolem odkazu. Toto je vzor, který následuje knihovna [Microsoft. Extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) :

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter ve srovnání s JsonTextWriter

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> je vysoce výkonný způsob, jak psát text JSON kódovaný v kódování UTF-8 ze běžných typů .NET, jako jsou `String`, `Int32`a `DateTime`. Zapisovač je typ nižší úrovně, který lze použít k vytvoření vlastních serializátorů.

Následující části vysvětlují Doporučené programovací vzory pro použití `Utf8JsonWriter`.

### <a name="write-with-utf-8-text"></a>Zápis s textem v kódování UTF-8

Abyste dosáhli nejlepšího možného výkonu při použití `Utf8JsonWriter`, pište datové části JSON, které jsou už kódované jako text UTF-8, a ne jako řetězce UTF-16. Použijte <xref:System.Text.Json.JsonEncodedText> k ukládání a předkódování známých názvů vlastností řetězce a hodnot jako statických a předejte je do zapisovače namísto použití řetězcových literálů UTF-16. Je to rychlejší než ukládání do mezipaměti a používání bajtových polí UTF-8.

Tento přístup funguje také v případě, že potřebujete vlastní uvozovací znaky. `System.Text.Json` neumožňuje zakázat uvozovací znaky při zápisu řetězce. Můžete však předat vlastní <xref:System.Text.Encodings.Web.JavaScriptEncoder> jako možnost zapisovače nebo vytvořit vlastní `JsonEncodedText`, který používá vaši `JavascriptEncoder` k tomu, aby provedl uvozovací znaky, a pak zapsat `JsonEncodedText` namísto řetězce. Další informace najdete v tématu [přizpůsobení kódování znaků](system-text-json-how-to.md#customize-character-encoding).

### <a name="write-raw-values"></a>Zapsat nezpracované hodnoty

Metoda `Newtonsoft.Json` `WriteRawValue` zapisuje nezpracovaný kód JSON, kde je očekávána hodnota. <xref:System.Text.Json> nemá žádný přímý ekvivalent, ale tady je alternativní řešení, které zajistí, že se zapíše jenom platný kód JSON:

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>Přizpůsobení znakové uvozovací znaky

Nastavení [StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) `JsonTextWriter` nabízí možnosti pro únik všech znaků, které nejsou ASCII, **nebo** znaků HTML. Ve výchozím nastavení `Utf8JsonWriter` řídí všechny znaky jiné než ASCII **a** HTML. Tyto uvozovací znaky se provádějí z důvodů zabezpečení s důkladnou ochranou. Pokud chcete zadat jinou zásadu uvozovacích uvozovacích znaků, vytvořte <xref:System.Text.Encodings.Web.JavaScriptEncoder> a nastavte <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>. Další informace najdete v tématu [přizpůsobení kódování znaků](system-text-json-how-to.md#customize-character-encoding).

### <a name="customize-json-format"></a>Přizpůsobení formátu JSON

`JsonTextWriter` obsahuje následující nastavení, u kterých `Utf8JsonWriter` nemá žádný ekvivalent:

* [Odsazení](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) – určuje, kolik znaků se má odsadit. `Utf8JsonWriter` vždy provádí odsazení 2 znaky.
* [IndentChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) – určuje znak, který se má použít pro odsazení.  `Utf8JsonWriter` vždy používá prázdné znaky.
* [QuoteChar současně](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) – určuje znak, který se má použít k obložení řetězcových hodnot.  `Utf8JsonWriter` vždy používá dvojité uvozovky.
* [Quote](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) – určuje, jestli se mají kolem názvů vlastností dokončit uvozovky.  `Utf8JsonWriter` jsou vždy obklopeny uvozovkami.

Neexistují žádná alternativní řešení, která by vám mohla umožnit přizpůsobení formátu JSON vytvořeného `Utf8JsonWriter` tímto způsobem.

### <a name="write-null-values"></a>Zapsat hodnoty null

Chcete-li zapsat hodnoty null pomocí `Utf8JsonWriter`, zavolejte:

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A> napsat pár klíč-hodnota s hodnotou null jako hodnotu.
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A> k zápisu hodnoty null jako prvku pole JSON.

V případě řetězcové vlastnosti, pokud je řetězec null, <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> a <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> jsou ekvivalentní `WriteNull` a `WriteNullValue`.

### <a name="write-timespan-uri-or-char-values"></a>Zápis hodnot TimeSpan, URI nebo char

`JsonTextWriter` poskytuje `WriteValue` metody pro hodnoty [TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm), [URI](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)a [char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) . `Utf8JsonWriter` nemá ekvivalentní metody. Místo toho naformátujte tyto hodnoty jako řetězce (například voláním `ToString()`) a volání <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>.

### <a name="multi-targeting"></a>Cílení na více platforem

Pokud potřebujete nadále používat `Newtonsoft.Json` pro určité cílové architektury, můžete mít více cílů a mít dvě implementace. To ale není triviální a vyžaduje `#ifdefs` a duplikování zdroje. Jedním ze způsobů, jak sdílet co nejvíc kódů, je vytvořit obálku kolem `Utf8JsonWriter` a `Newtonsoft` `JsonTextWriter`. Tato obálka sjednotí oblast veřejného povrchu a současně izoluje rozdíly v chování. To umožňuje izolovat změny hlavně pro konstrukci typu. Následující knihovna [Microsoft. Extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) :

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>Další materiály a zdroje informací

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [Přehled System. text. JSON](system-text-json-overview.md)
* [Jak používat System. text. JSON](system-text-json-how-to.md)
* [Zápis vlastních převaděčů](system-text-json-converters-how-to.md)
* [Podpora DateTime a DateTimeOffset v System. text. JSON](../datetime/system-text-json-support.md)
* [Reference k rozhraní API System. text. JSON](xref:System.Text.Json)
* [Reference k rozhraní API System. text. JSON. Serialization](xref:System.Text.Json.Serialization)
