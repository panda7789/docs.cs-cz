---
title: Postup serializace a deserializace JSON pomocí C#-.NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 6324fe28b23e4df74bcf3fd1dbb7e0c14d5e3d1b
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135799"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>Jak serializovat a deserializovat (zařazování a zrušit zařazení) JSON v .NET

Tento článek ukazuje, jak použít <xref:System.Text.Json> obor názvů k serializaci a deserializaci do a z JavaScript Object Notation (JSON). Pokud přenášíte existující kód z `Newtonsoft.Json`nástroje, přečtěte si téma [Jak `System.Text.Json`migrovat na ](system-text-json-migrate-from-newtonsoft-how-to.md).

Pokyny a vzorový kód používají knihovnu přímo, nikoli prostřednictvím rozhraní, jako je například [ASP.NET Core](/aspnet/core/).

Většina ukázkových kódů serializace se <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> nastaví `true` na "poměrně tištěné" formát JSON (s odsazením a prázdným znakem pro lidskou čitelnost). V případě produkčního použití byste obvykle přijímají výchozí hodnotu `false` pro toto nastavení.

Příklady kódu odkazují na následující třídu a varianty:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a>Jmenné prostory

<xref:System.Text.Json> Obor názvů obsahuje všechny vstupní body a hlavní typy. <xref:System.Text.Json.Serialization> Obor názvů obsahuje atributy a rozhraní API pro pokročilé scénáře a přizpůsobení specifické pro serializaci a deserializaci. Příklady kódu, které jsou uvedeny v tomto `using` článku, vyžadují direktivy pro jeden nebo oba tyto obory názvů:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

Atributy z oboru <xref:System.Runtime.Serialization> názvů se v `System.Text.Json`současné době nepodporují.

## <a name="how-to-write-net-objects-to-json-serialize"></a>Zápis objektů .NET do formátu JSON (serializace)

Chcete-li zapsat JSON do řetězce nebo do souboru, zavolejte <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> metodu.

Následující příklad vytvoří JSON jako řetězec:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

Následující příklad používá synchronní kód k vytvoření souboru JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

Následující příklad používá asynchronní kód k vytvoření souboru JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

Předchozí příklady používají odvození typu pro typ, který je serializován. Přetížení `Serialize()` přebírá parametr obecného typu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a>Příklad serializace

Tady je ukázková třída, která obsahuje kolekce a vnořenou třídu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

Výstup JSON z serializace instance předchozího typu vypadá jako v následujícím příkladu. Výstup JSON je ve výchozím nastavení minifikovaného:

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

Následující příklad ukazuje stejný formát JSON (to znamená, že je poměrně vytištěn s prázdným znakem a odsazením):

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": 20,
      "Low": -10
    },
    "Hot": {
      "High": 60,
      "Low": 20
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

### <a name="serialize-to-utf-8"></a>Serializovat do UTF-8

Pro serializaci do UTF-8 volejte <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> metodu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

K <xref:System.Text.Json.JsonSerializer.Serialize%2A> dispozici je také <xref:System.Text.Json.Utf8JsonWriter> přetížení, které přijímá objekt.

Serializace do UTF-8 je přibližně 5-10% rychlejší než použití metod založených na řetězci. Rozdíl je z důvodu, že bajty (jako UTF-8) není nutné převést na řetězce (UTF-16).

## <a name="serialization-behavior"></a>Chování serializace

* Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti. Můžete [určit vlastnosti, které se mají vyloučit](#exclude-properties-from-serialization).
* [Výchozí kodér](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) řídí znaky jiné než ASCII, znaky citlivé na jazyk HTML v rozsahu ASCII a znaky, které musí být uvozeny podle [specifikace JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).
* Ve výchozím nastavení je JSON minifikovaného. [Kód JSON můžete v podstatě vytisknout](#serialize-to-formatted-json).
* Ve výchozím nastavení jsou malá a velká písmena názvů JSON shodná s názvy .NET. Můžete [přizpůsobit název a velikost písmen JSON](#customize-json-names-and-values).
* Byly zjištěny cyklické odkazy a byly vyvolány výjimky.
* V současné době jsou pole vyloučena.

Mezi podporované typy patří:

* Primitivní prvky .NET, které se mapují na primitivní prvky JavaScriptu, jako jsou číselné typy, řetězce a logická hodnota.
* Uživatelsky definované [prosté staré objekty CLR (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).
* Jednorozměrné a vícenásobná pole (`ArrayName[][]`).
* `Dictionary<string,TValue>`Where `TValue` je `object`, `JsonElement`nebo POCO.
* Kolekce z následujících oborů názvů.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

[Vlastní převaděče můžete implementovat](system-text-json-converters-how-to.md) pro zpracování dalších typů nebo pro poskytování funkcí, které integrované převaděče nepodporují.

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Postup čtení formátu JSON do objektů .NET (deserializace)

Chcete-li provést deserializaci z řetězce nebo souboru, <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> zavolejte metodu.

Následující příklad přečte JSON z řetězce a vytvoří instanci `WeatherForecast` třídy uvedené dříve pro [příklad serializace](#serialization-example):

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

Chcete-li provést deserializaci ze souboru pomocí synchronního kódu, přečtěte si soubor do řetězce, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

Chcete-li provést deserializaci ze souboru pomocí asynchronního kódu <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> , zavolejte metodu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>Deserializace ze znakové sady UTF-8

Chcete-li deserializovat ze znakové sady UTF- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 8, zavolejte přetížení `Utf8JsonReader` , které `ReadOnlySpan<byte>`přijímá nebo, jak je znázorněno v následujících příkladech. V příkladech se předpokládá, že je JSON v bajtovém poli s názvem jsonUtf8Bytes.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a>Chování deserializace

* Ve výchozím nastavení se při porovnávání názvů vlastností rozlišují velká a malá písmena. Můžete [zadat nerozlišování velkých a malých písmen](#case-insensitive-property-matching).
* Pokud JSON obsahuje hodnotu vlastnosti jen pro čtení, hodnota je ignorována a není vyvolána žádná výjimka.
* Deserializace na odkazové typy bez bezparametrového konstruktoru není podporována.
* Deserializace u neměnných objektů nebo vlastností jen pro čtení není podporována.
* Ve výchozím nastavení jsou výčty podporovány jako čísla. [Názvy výčtů můžete serializovat jako řetězce](#enums-as-strings).
* Pole nejsou podporována.
* Ve výchozím nastavení komentáře nebo koncové čárky ve formátu JSON vyvolají výjimky. Můžete [povolovat komentáře a koncové čárky](#allow-comments-and-trailing-commas).
* [Výchozí maximální hloubka](xref:System.Text.Json.JsonReaderOptions.MaxDepth) je 64.

[Vlastní převaděče můžete implementovat](system-text-json-converters-how-to.md) pro poskytování funkcí, které nejsou podporované integrovanými převaděči.

## <a name="serialize-to-formatted-json"></a>Serializovat do formátovaného formátu JSON

Pro poměrně vytisknutí výstupu JSON nastavte <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> na: `true`

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

Tady je příklad typu pro serializaci a poměrně tištěné výstup JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a>Přizpůsobení názvů a hodnot JSON

Ve výchozím nastavení se názvy vlastností a klíče slovníku ve výstupu JSON nezměnily, včetně případu. Hodnoty výčtu jsou reprezentovány jako čísla. V této části se dozvíte, jak:

* [Přizpůsobení jednotlivých názvů vlastností](#customize-individual-property-names)
* [Převést názvy všech vlastností na velikost ve stylu CamelCase](#use-camel-case-for-all-json-property-names)
* [Implementace vlastní zásady pro pojmenovávání vlastností](#use-a-custom-json-property-naming-policy)
* [Převede klíče slovníku na ve stylu CamelCase případ.](#camel-case-dictionary-keys)
* [Převod výčtů na řetězce a ve stylu CamelCase velikost písmen](#enums-as-strings)

Pro jiné scénáře, které vyžadují speciální zpracování názvů a hodnot vlastností JSON, můžete [implementovat vlastní převaděče](system-text-json-converters-how-to.md).

### <a name="customize-individual-property-names"></a>Přizpůsobení jednotlivých názvů vlastností

Chcete-li nastavit název jednotlivých vlastností, použijte atribut [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .

Tady je příklad typu k serializaci a výslednému formátu JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

Název vlastnosti nastavený tímto atributem:

* Platí v obou směrech pro serializaci a deserializaci.
* Má přednost před zásadami pro pojmenovávání vlastností.

### <a name="use-camel-case-for-all-json-property-names"></a>Pro všechny názvy vlastností JSON použijte ve stylu CamelCase Case

Pro použití ve stylu CamelCase pro všechny názvy vlastností JSON nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na `JsonNamingPolicy.CamelCase`, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

Tady je příklad třídy pro serializaci a výstup JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

Zásada pro pojmenování vlastností případu ve stylu CamelCase:

* Platí pro serializaci a deserializaci.
* Je potlačen `[JsonPropertyName]` atributy. To je důvod, proč název `Wind` vlastnosti JSON v příkladu není ve stylu CamelCase Case.

### <a name="use-a-custom-json-property-naming-policy"></a>Použít vlastní zásady pojmenování vlastností JSON

Chcete-li použít vlastní zásadu pojmenovávání vlastností JSON, vytvořte třídu, která <xref:System.Text.Json.JsonNamingPolicy> je odvozena <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> z třídy, a přepište metodu, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

Pak nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> vlastnost na instanci třídy zásad pojmenování:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

Tady je příklad třídy pro serializaci a výstup JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

Zásady pojmenování vlastností JSON:

* Platí pro serializaci a deserializaci.
* Je potlačen `[JsonPropertyName]` atributy. To je důvod, proč název `Wind` vlastnosti JSON v příkladu není velká písmena.

### <a name="camel-case-dictionary-keys"></a>Klíče slovníku případů ve stylu CamelCase

Pokud je vlastnost objektu, který má být serializován, typu `Dictionary<string,TValue>`, lze `string` klíče převést na ve stylu CamelCase případ. To provedete tak <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> , `JsonNamingPolicy.CamelCase`že nastavíte na, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

Serializace objektu se slovníkem s názvem `TemperatureRanges` , který má páry `"ColdMinTemp", 20` klíč-hodnota `"HotMinTemp", 40` a výsledkem by byl výstup JSON jako v následujícím příkladu:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

Zásady pro pojmenovávání ve stylu CamelCase pro klíče slovníku se vztahují pouze na serializaci. Při deserializaci slovníku budou klíče odpovídat souboru JSON, i když zadáte `JsonNamingPolicy.CamelCase` pro. `DictionaryKeyPolicy`

### <a name="enums-as-strings"></a>Výčty jako řetězce

Ve výchozím nastavení jsou výčty serializovány jako čísla. Chcete-li serializovat názvy výčtu jako řetězce, <xref:System.Text.Json.Serialization.JsonStringEnumConverter>použijte.

Předpokládejme například, že potřebujete serializovat následující třídu, která má výčet:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

Pokud je `Hot`souhrn, ve výchozím nastavení má serializovaný formát JSON číselnou hodnotu 3:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

Následující vzorový kód místo číselných hodnot serializace názvy výčtu a převede názvy na ve stylu CamelCase případ:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

Výsledný kód JSON vypadá jako v následujícím příkladu:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

Názvy řetězců výčtu lze deserializovat také, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a>Vyloučit vlastnosti ze serializace

Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti. Pokud nechcete, aby se některé z nich zobrazovaly ve výstupu JSON, máte několik možností. V této části se dozvíte, jak vyloučit:

* [Jednotlivé vlastnosti](#exclude-individual-properties)
* [Všechny vlastnosti jen pro čtení](#exclude-all-read-only-properties)
* [Všechny vlastnosti s hodnotou null](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a>Vyloučení individuálních vlastností

Chcete-li ignorovat jednotlivé vlastnosti, použijte atribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .

Tady je příklad typu pro serializaci a výstup JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a>Vyloučit všechny vlastnosti jen pro čtení

Vlastnost je jen pro čtení, pokud obsahuje veřejnou metodu getter, ale ne veřejnou metodu setter. Chcete-li vyloučit všechny vlastnosti jen pro čtení, <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> nastavte `true`na, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

Tady je příklad typu pro serializaci a výstup JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Tato možnost se vztahuje pouze na serializaci. Během deserializace jsou vlastnosti jen pro čtení ve výchozím nastavení ignorovány.

### <a name="exclude-all-null-value-properties"></a>Vyloučit všechny vlastnosti hodnoty null

Chcete-li vyloučit všechny vlastnosti hodnoty null, <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> nastavte vlastnost `true`na hodnotu, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

Zde je příklad objektu pro serializaci a výstup JSON:

|Vlastnost |Hodnota  |
|---------|---------|
| Datum    | 8/1/2019 12:00:00 DOP. 07:00|
| TemperatureCelsius| 25 |
| Souhrn| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

Toto nastavení platí pro serializaci a deserializaci. Informace o jeho vlivu na deserializaci naleznete v tématu [Ignore null Při deserializaci](#ignore-null-when-deserializing).

## <a name="customize-character-encoding"></a>Přizpůsobení kódování znaků

Ve výchozím nastavení serializátor řídí všechny znaky jiné než ASCII.  To znamená, že je nahradí `\uxxxx` znakem `xxxx` , kde je kód Unicode znaku.  Například pokud je `Summary` vlastnost nastavena na жаркоa v cyrilici, `WeatherForecast` objekt je serializován, jak je znázorněno v následujícím příkladu:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Serializovat znakové sady jazyků

Chcete-li serializovat znakové sady jednoho nebo více jazyků bez uvozovacího znaku, určete [Rozsah znaků Unicode](xref:System.Text.Unicode.UnicodeRanges) při vytváření instance <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

Tento kód neřídí cyrilici ani řecké znaky. Pokud je `Summary` vlastnost nastavena na жаркоa v cyrilici, `WeatherForecast` objekt je serializován, jak je znázorněno v následujícím příkladu:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

Chcete-li serializovat všechny jazykové sady bez použití uvozovacího, použijte <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.

### <a name="serialize-specific-characters"></a>Serializovat konkrétní znaky

Alternativou je zadání jednotlivých znaků, které chcete použít, bez nutnosti řídicích znaků. Následující příklad serializace pouze prvních dvou znaků жарко:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

Zde je příklad kódu JSON vytvořeného předchozím kódem:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>Serializovat všechny znaky

K minimalizaci řídicích znaků, <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>které můžete použít, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> V `UnsafeRelaxedJsonEscaping` porovnání s výchozím kodérem je kodér více opravňujícím, aby bylo možné předávat znaky bez řídicích znaků:
>
> * `<`Neřídí znaky citlivé na HTML, například, `>`, `&`a. `'`
> * Nenabízí žádné další ochrany proti důkladné ochraně před útoky XSS nebo informací, jako jsou ty, které by mohly vzniknout ze strany klienta a *serveru na znakovou sadu.*
>
> Nezabezpečený kodér používejte pouze v případě, že je známo, že klient bude interpretovat výslednou datovou část jako JSON kódovaný v kódování UTF-8. Můžete ho například použít, pokud server posílá hlavičku `Content-Type: application/json; charset=utf-8`odpovědi. Nikdy nepovolujte `UnsafeRelaxedJsonEscaping` , aby se nezpracovaný výstup vygeneroval do stránky HTML `<script>` nebo elementu.

## <a name="serialize-properties-of-derived-classes"></a>Serializovat vlastnosti odvozených tříd

Serializace hierarchie polymorfního typu není podporována. Například pokud je vlastnost definována jako rozhraní nebo abstraktní třída, jsou serializovány pouze vlastnosti definované v rozhraní nebo abstraktní třídě, a to i v případě, že typ modulu runtime má další vlastnosti. Výjimky z tohoto chování jsou vysvětleny v této části.

Předpokládejme například, že máte `WeatherForecast` třídu a odvozenou třídu: `WeatherForecastDerived`

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

A Předpokládejme, že argument typu `Serialize` metody v době kompilace je: `WeatherForecast`

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

V tomto scénáři není `WindSpeed` Vlastnost serializována i v případě, že `weatherForecast` objekt je ve skutečnosti `WeatherForecastDerived` objekt. Serializovat se budou jenom vlastnosti základní třídy:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Toto chování je určeno k tomu, aby se zabránilo náhodnému úniku dat v odvozeném typu vytvořeném modulem runtime.

Chcete-li serializovat vlastnosti odvozeného typu v předchozím příkladu, použijte jeden z následujících přístupů:

* Zavolejte přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A> , které umožňuje určit typ za běhu:

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* Deklarujte objekt, který se má `object`serializovat jako.

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

V předchozím ukázkovém scénáři oba přístupy způsobí, že `WindSpeed` vlastnost bude obsažena ve výstupu JSON:

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> Tyto přístupy poskytují polymorfní serializaci pouze pro kořenový objekt, který má být serializován, nikoli pro vlastnosti daného kořenového objektu.

Můžete získat polymorfní serializaci pro objekty nižší úrovně, pokud je definujete jako typ `object`. Předpokládejme například, že vaše `WeatherForecast` třída má vlastnost s názvem `PreviousForecast` , která může být definována jako `WeatherForecast` typ `object`nebo:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

Pokud `PreviousForecast` vlastnost obsahuje instanci `WeatherForecastDerived`:

* Výstup JSON ze serializace `WeatherForecastWithPrevious` **neobsahuje** `WindSpeed`.
* Výstup JSON ze serializace `WeatherForecastWithPreviousAsObject` **obsahuje** `WindSpeed`.

Pro serializaci `WeatherForecastWithPreviousAsObject`není nutné volat `Serialize<object>` nebo `GetType` , protože kořenový objekt není ten, který může být odvozeného typu. Následující příklad kódu nevolá `Serialize<object>` nebo: `GetType`

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

Předchozí kód správně serializace `WeatherForecastWithPreviousAsObject`:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

Stejný přístup k definování vlastností jako `object` funguje s rozhraními. Předpokládejme, že máte následující rozhraní a implementaci a chcete serializovat třídu s vlastnostmi, které obsahují instance implementace:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

Při `Forecasts`serializaci instance je zobrazena pouze `Tuesday` `WindSpeed` vlastnost, protože `Tuesday` je definována jako: `object`

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

Následující příklad ukazuje kód JSON, který je výsledkem předchozího kódu:

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

Další informace o polymorfní **serializaci**a informace o **deserializaci**naleznete v tématu [How to migruje from Newtonsoft. JSON to System. text. JSON](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).

## <a name="allow-comments-and-trailing-commas"></a>Povolí komentáře a koncové čárky.

Ve výchozím nastavení se komentáře a koncové čárky ve formátu JSON nepovolují. Chcete-li ve formátu JSON dovolit komentáře, <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> nastavte vlastnost `JsonCommentHandling.Skip`na hodnotu.
A chcete-li použít koncové čárky, nastavte <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> vlastnost na `true`hodnotu. Následující příklad ukazuje, jak je možné:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

Tady je příklad JSON s komentáři a koncovou čárkou:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>Porovnávání vlastností bez rozlišení velkých a malých písmen

Ve výchozím nastavení deserializace hledá název vlastnosti rozlišující velká a malá písmena mezi vlastnostmi JSON a cílovým objektem. Chcete-li toto chování změnit <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> , `true`nastavte na:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

Tady je příklad JSON s názvy vlastností Case ve stylu CamelCase. Lze deserializovat do následujícího typu, který má názvy vlastností Case typu Pascal.

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a>Přetečení JSON popisovače

Při deserializaci můžete přijímat data ve formátu JSON, která nejsou reprezentovaná vlastnostmi cílového typu. Předpokládejme například, že váš cílový typ je:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

A JSON, který se má deserializovat, je:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

Pokud deserializaci kódu JSON zobrazeného na zobrazeném typu, `DatesAvailable` vlastnosti `SummaryWords` a se nikde k přechodu a jsou ztraceny. Chcete-li zachytit další data, jako jsou tyto vlastnosti, použijte atribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) na vlastnost typu `Dictionary<string,object>` nebo `Dictionary<string,JsonElement>`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

Při deserializaci formátu JSON zobrazeného dříve do tohoto ukázkového typu se data dalších dat stávají páry klíč-hodnota `ExtensionData` vlastnosti:

|Vlastnost |Hodnota  |Poznámky  |
|---------|---------|---------|
| Datum    | 8/1/2019 12:00:00 DOP. 07:00||
| TemperatureCelsius| 0 | Neshoda malých a velkých`temperatureCelsius` písmen (ve formátu JSON), takže vlastnost není nastavena. |
| Souhrn | Hot ||
| ExtensionData – | temperatureCelsius: 25 |Vzhledem k tomu, že se neshoduje velká a malá písmena, je tato vlastnost JSON extra a ve slovníku se stala dvojicí klíč-hodnota.|
|| DatesAvailable:<br>  8/1/2019 12:00:00 DOP. 07:00<br>8/2/2019 12:00:00 DOP. 07:00 |Vlastnost extra z formátu JSON se stávají dvojicí klíč-hodnota s polem jako objektem hodnoty.|
| |SummaryWords:<br>Cool<br>Vítr<br>Humid |Vlastnost extra z formátu JSON se stávají dvojicí klíč-hodnota s polem jako objektem hodnoty.|

Při serializaci cílového objektu se dvojice hodnoty klíče dat rozšíření stanou vlastnostmi JSON stejně, jako kdyby byly ve vstupním formátu JSON:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

Všimněte si, `ExtensionData` že název vlastnosti se ve formátu JSON nezobrazuje. Díky tomuto chování může JSON vytvořit zpáteční cestu, aniž by došlo ke ztrátě dalších dat, která by jinak nebyla deserializována.

## <a name="ignore-null-when-deserializing"></a>Při deserializaci ignorovat hodnotu null

Ve výchozím nastavení platí, že pokud je vlastnost ve formátu JSON null, odpovídající vlastnost v cílovém objektu je nastavena na hodnotu null. V některých scénářích může cílová vlastnost mít výchozí hodnotu a nechcete, aby hodnota null přepsala výchozí hodnotu.

Předpokládejme například, že následující kód představuje cílový objekt:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

A Předpokládejme, že následující kód JSON je deserializovaný:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Po deserializaci má `Summary` vlastnost `WeatherForecastWithDefault` objektu hodnotu null.

Chcete-li toto chování změnit <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> , `true`nastavte na hodnotu, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

S touto možností je `Summary` vlastnost `WeatherForecastWithDefault` objektu výchozí hodnotou "No Summary" po deserializaci.

Hodnoty null ve formátu JSON jsou ignorovány pouze v případě, že jsou platné. Hodnoty null pro typy hodnot, které neumožňují hodnotu null, způsobují výjimky.

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter a JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>je vysoce výkonné, nízké přidělení, jen pro čtení pro text JSON s kódováním UTF-8, načtené z `ReadOnlySpan<byte>` nebo. `ReadOnlySequence<byte>` `Utf8JsonReader` Je typ nižší úrovně, který lze použít k vytvoření vlastních analyzátorů a deserializace. <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> Metoda používá `Utf8JsonReader` v rámci pokrývání.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>je vysoce výkonný způsob, jak psát text JSON kódovaný v kódování UTF-8 ze běžných typů .NET `String`, `Int32`jako jsou `DateTime`, a. Zapisovač je typ nižší úrovně, který lze použít k vytvoření vlastních serializátorů. <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> Metoda používá `Utf8JsonWriter` v rámci pokrývání.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>poskytuje možnost sestavit model DOM (Document Object Model) (DOM) jen pro čtení pomocí `Utf8JsonReader`. Model DOM poskytuje náhodný přístup k datům v datové části JSON. K prvkům JSON, které tvoří datovou část, lze <xref:System.Text.Json.JsonElement> přistupovat prostřednictvím typu. `JsonElement` Typ poskytuje enumerátory polí a objektů spolu s rozhraními API pro převod textu JSON na běžné typy .NET. `JsonDocument`zpřístupňuje <xref:System.Text.Json.JsonDocument.RootElement> vlastnost.

Následující části ukazují, jak používat tyto nástroje pro čtení a zápis JSON.

## <a name="use-jsondocument-for-access-to-data"></a>Použití JsonDocument pro přístup k datům

Následující příklad ukazuje, jak použít <xref:System.Text.Json.JsonDocument> třídu pro náhodný přístup k datům v řetězci JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

Předcházející kód:

* Předpokládá, že se JSON, který se má analyzovat `jsonString`, nachází v řetězci s názvem.
* Vypočítá průměrnou třídu pro objekty v `Students` poli, které mají `Grade` vlastnost.
* Přiřadí výchozí stupeň 70 pro studenty, kteří nemají třídu.
* Spočítá studenty zvýšením `count` proměnné s každou iterací. Alternativou je volání <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, jak je znázorněno v následujícím příkladu:

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

Zde je příklad kódu JSON, který tento kód zpracovává:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>Zápis JSON pomocí JsonDocument

Následující příklad ukazuje, jak zapsat JSON z <xref:System.Text.Json.JsonDocument>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

Předcházející kód:

* Přečte soubor JSON, načte data do `JsonDocument`a zapisuje do souboru formát JSON s formátováním (poměrně vytištěného).
* Používá <xref:System.Text.Json.JsonDocumentOptions> se k určení, že komentáře ve vstupním JSON jsou povolené, ale ignorují se.
* Po dokončení volání <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> do zapisovače. Alternativou je umožnit zapisovači AutoFlush při jeho uvolnění.

Tady je příklad vstupu JSON, který se má zpracovat v příkladu kódu:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

Výsledkem je následující poměrně tištěný výstup JSON:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>Použití Utf8JsonWriter

Následující příklad ukazuje, jak použít <xref:System.Text.Json.Utf8JsonWriter> třídu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>Použití Utf8JsonReader

Následující příklad ukazuje, jak použít <xref:System.Text.Json.Utf8JsonReader> třídu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

Předchozí kód předpokládá, že `jsonUtf8` proměnná je bajtové pole, které obsahuje platný kód JSON KÓDOVANÝ jako UTF-8.

### <a name="filter-data-using-utf8jsonreader"></a>Filtrování dat pomocí Utf8JsonReader

Následující příklad ukazuje, jak číst soubor synchronně a vyhledat hodnotu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

Předcházející kód:

* Předpokládá, že JSON obsahuje pole objektů a každý objekt může obsahovat vlastnost Name typu String.
* Spočítá hodnoty vlastností Objects a Name, které končí na "University".
* Předpokládá, že soubor je kódovaný jako UTF-16 a překóduje ho do UTF-8. Soubor kódovaný jako UTF-8 lze číst přímo do a `ReadOnlySpan<byte>`pomocí následujícího kódu:

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  Pokud soubor obsahuje znak pořadí bajtů UTF-8 (BOM), odeberte ho před předáním bajtů do `Utf8JsonReader`, protože čtecí modul očekává text. V opačném případě se kusovník považuje za neplatný kód JSON a čtenář vyvolá výjimku.

Zde je ukázka JSON, kterou může předchozí kód přečíst. Výsledná Souhrnná zpráva je "2 z čtvrtého" má názvy, které končí na "University" ":

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a>Další materiály a zdroje informací

* [System.Text.JsonPřehled](system-text-json-overview.md)
* [Postup zápisu vlastních převaděčů](system-text-json-converters-how-to.md)
* [Postup migrace zNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Podpora DateTime a DateTimeOffset vSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.JsonReference k rozhraní API](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
