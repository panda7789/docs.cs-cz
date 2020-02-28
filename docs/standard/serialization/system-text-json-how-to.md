---
title: Postup serializace a deserializace JSON C# pomocí-.NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 8025f84f2425f5b91e08b28ddb24d105d8c4d1a3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159582"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>Jak serializovat a deserializovat (zařazování a zrušit zařazení) JSON v .NET

Tento článek ukazuje, jak použít obor názvů <xref:System.Text.Json> k serializaci a deserializaci do a z JavaScript Object Notation (JSON).

Pokyny a vzorový kód používají knihovnu přímo, nikoli prostřednictvím rozhraní, jako je například [ASP.NET Core](/aspnet/core/).

Většina vzorových ukázkových kódů v serializaci <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` na "poměrně tištěné" formátu JSON (s odsazením a prázdným znakem pro lidské čitelnost). Při použití v produkčním prostředí byste obvykle přijali výchozí hodnotu `false` pro toto nastavení.

## <a name="namespaces"></a>Obory názvů

Obor názvů <xref:System.Text.Json> obsahuje všechny vstupní body a hlavní typy. Obor názvů <xref:System.Text.Json.Serialization> obsahuje atributy a rozhraní API pro pokročilé scénáře a přizpůsobení specifické pro serializaci a deserializaci. Příklady kódu, které jsou uvedené v tomto článku, vyžadují direktivy `using` pro jeden nebo oba tyto obory názvů:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

Atributy z oboru názvů <xref:System.Runtime.Serialization> se v `System.Text.Json`aktuálně nepodporují.

## <a name="how-to-write-net-objects-to-json-serialize"></a>Zápis objektů .NET do formátu JSON (serializace)

Chcete-li zapsat JSON do řetězce nebo do souboru, zavolejte metodu <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.

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

Chcete-li serializovat do UTF-8, zavolejte metodu <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

K dispozici je také přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A>, které přijímá <xref:System.Text.Json.Utf8JsonWriter>.

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
* `Dictionary<string,TValue>`, kde `TValue` je `object`, `JsonElement`nebo POCO.
* Kolekce z následujících oborů názvů.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

[Vlastní převaděče můžete implementovat](system-text-json-converters-how-to.md) pro zpracování dalších typů nebo pro poskytování funkcí, které integrované převaděče nepodporují.

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Postup čtení formátu JSON do objektů .NET (deserializace)

Chcete-li provést deserializaci z řetězce nebo souboru, zavolejte metodu <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.

Následující příklad přečte JSON z řetězce a vytvoří instanci `WeatherForecast` třídy uvedené dříve pro [příklad serializace](#serialization-example):

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

Chcete-li provést deserializaci ze souboru pomocí synchronního kódu, přečtěte si soubor do řetězce, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

Chcete-li provést deserializaci ze souboru pomocí asynchronního kódu, zavolejte metodu <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>Deserializace ze znakové sady UTF-8

Chcete-li provést deserializaci ze znakové sady UTF-8, zavolejte <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> přetížení, které přebírá `Utf8JsonReader` nebo `ReadOnlySpan<byte>`, jak je znázorněno v následujících příkladech. V příkladech se předpokládá, že je JSON v bajtovém poli s názvem jsonUtf8Bytes.

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

Chcete-li vytvořit poměrně tisk výstupu JSON, nastavte <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> na `true`:

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

Pokud chcete u všech názvů vlastností JSON použít ve stylu CamelCase, nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na `JsonNamingPolicy.CamelCase`, jak je znázorněno v následujícím příkladu:

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
* Je přepsán `[JsonPropertyName]` atributy. To je důvod, proč název vlastnosti JSON `Wind` v příkladu není ve stylu CamelCase Case.

### <a name="use-a-custom-json-property-naming-policy"></a>Použít vlastní zásady pojmenování vlastností JSON

Chcete-li použít vlastní zásadu pojmenovávání vlastností JSON, vytvořte třídu, která je odvozena z <xref:System.Text.Json.JsonNamingPolicy> a přepište metodu <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

Pak nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na instanci třídy zásad pojmenování:

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
* Je přepsán `[JsonPropertyName]` atributy. Důvodem je, že název vlastnosti JSON `Wind` v příkladu není velká písmena.

### <a name="camel-case-dictionary-keys"></a>Klíče slovníku případů ve stylu CamelCase

Pokud je vlastnost objektu, která má být serializována, typu `Dictionary<string,TValue>`, `string` klíče lze převést na ve stylu CamelCase případ. Provedete to tak, že nastavíte <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> na `JsonNamingPolicy.CamelCase`, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

Serializace objektu se slovníkem s názvem `TemperatureRanges`, který má páry klíč-hodnota `"ColdMinTemp", 20` a `"HotMinTemp", 40` by vedlo jako výstup JSON jako v následujícím příkladu:

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

Zásady pro pojmenovávání ve stylu CamelCase pro klíče slovníku se vztahují pouze na serializaci. Pokud deserializaci slovníku, klíče budou odpovídat souboru JSON, i když zadáte `JsonNamingPolicy.CamelCase` pro `DictionaryKeyPolicy`.

### <a name="enums-as-strings"></a>Výčty jako řetězce

Ve výchozím nastavení jsou výčty serializovány jako čísla. Chcete-li serializovat názvy výčtu jako řetězce, použijte <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.

Předpokládejme například, že potřebujete serializovat následující třídu, která má výčet:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

Pokud je souhrn `Hot`, ve výchozím nastavení má serializovaný formát JSON číselnou hodnotu 3:

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

Vlastnost je jen pro čtení, pokud obsahuje veřejnou metodu getter, ale ne veřejnou metodu setter. Chcete-li vyloučit všechny vlastnosti jen pro čtení, nastavte <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> na `true`, jak je znázorněno v následujícím příkladu:

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

Chcete-li vyloučit všechny vlastnosti hodnoty null, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> na hodnotu `true`, jak je znázorněno v následujícím příkladu:

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

Ve výchozím nastavení serializátor řídí všechny znaky jiné než ASCII.  To znamená, že je nahradí je `\uxxxx`, kde `xxxx` je kód Unicode znaku.  Například pokud je vlastnost `Summary` nastavena na жаркоa v cyrilici, `WeatherForecast` objekt je serializován, jak je znázorněno v následujícím příkladu:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Serializovat znakové sady jazyků

Chcete-li serializovat znakové sady jednoho nebo více jazyků bez uvozovacího znaku, určete [rozsahy Unicode](xref:System.Text.Unicode.UnicodeRanges) při vytváření instance <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

Tento kód neřídí cyrilici ani řecké znaky. Pokud je vlastnost `Summary` nastavena na жаркоa v cyrilici, `WeatherForecast` objekt je serializován, jak je znázorněno v následujícím příkladu:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

Chcete-li serializovat všechny jazykové sady bez uvozovacího uvozovacího, použijte <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.

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

Chcete-li minimalizovat uvozovací znaky, můžete použít <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> V porovnání s výchozím kodérem je `UnsafeRelaxedJsonEscaping` kodér více opravňující, aby bylo možné předávat znaky bez řídicích znaků:
>
> * Neřídí znaky citlivé na HTML, například `<`, `>`, `&`a `'`.
> * Nenabízí žádné další ochrany proti důkladné ochraně před útoky XSS nebo informací, jako jsou ty, které by mohly vzniknout ze strany klienta a *serveru na znakovou sadu.*
>
> Nezabezpečený kodér používejte pouze v případě, že je známo, že klient bude interpretovat výslednou datovou část jako JSON kódovaný v kódování UTF-8. Můžete ji například použít, pokud server odesílá hlavičku odpovědi `Content-Type: application/json; charset=utf-8`. Nikdy nepovolujte výstup nezpracovaného `UnsafeRelaxedJsonEscaping` do stránky HTML nebo elementu `<script>`.

## <a name="serialize-properties-of-derived-classes"></a>Serializovat vlastnosti odvozených tříd

Serializace hierarchie polymorfního typu není podporována. Například pokud je vlastnost definována jako rozhraní nebo abstraktní třída, jsou serializovány pouze vlastnosti definované v rozhraní nebo abstraktní třídě, a to i v případě, že typ modulu runtime má další vlastnosti. Výjimky z tohoto chování jsou vysvětleny v této části.

Předpokládejme například, že máte třídu `WeatherForecast` a odvozenou třídu `WeatherForecastDerived`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

A Předpokládejme, že argument typu metody `Serialize` v době kompilace je `WeatherForecast`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

V tomto scénáři není vlastnost `WindSpeed` serializována i v případě, že je objekt `weatherForecast` ve skutečnosti objekt `WeatherForecastDerived`. Serializovat se budou jenom vlastnosti základní třídy:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Toto chování je určeno k tomu, aby se zabránilo náhodnému úniku dat v odvozeném typu vytvořeném modulem runtime.

Chcete-li serializovat vlastnosti odvozeného typu v předchozím příkladu, použijte jeden z následujících přístupů:

* Zavolejte přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A>, které umožňuje určit typ za běhu:

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* Deklarujte objekt, který se má serializovat jako `object`.

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

V předchozím ukázkovém scénáři obě přístupy způsobí, že vlastnost `WindSpeed` bude zahrnutá ve výstupu JSON:

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

Můžete získat polymorfní serializaci pro objekty nižší úrovně, pokud je definujete jako typ `object`. Předpokládejme například, že vaše třída `WeatherForecast` má vlastnost s názvem `PreviousForecast`, kterou lze definovat jako typ `WeatherForecast` nebo `object`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

Pokud vlastnost `PreviousForecast` obsahuje instanci `WeatherForecastDerived`:

* Výstup JSON pro serializaci `WeatherForecastWithPrevious` **nezahrnuje** `WindSpeed`.
* Výstup JSON pro serializaci `WeatherForecastWithPreviousAsObject` **zahrnuje** `WindSpeed`.

Pro serializaci `WeatherForecastWithPreviousAsObject`není nutné volat `Serialize<object>` nebo `GetType`, protože kořenový objekt není ten, který může být odvozeného typu. Následující příklad kódu nevolá `Serialize<object>` nebo `GetType`:

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

Stejný přístup k definování vlastností jako `object` pracuje s rozhraními. Předpokládejme, že máte následující rozhraní a implementaci a chcete serializovat třídu s vlastnostmi, které obsahují instance implementace:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

Při serializaci instance `Forecasts`pouze `Tuesday` zobrazí vlastnost `WindSpeed`, protože `Tuesday` je definován jako `object`:

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

Ve výchozím nastavení se komentáře a koncové čárky ve formátu JSON nepovolují. Chcete-li ve formátu JSON dovolit komentáře, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> na hodnotu `JsonCommentHandling.Skip`.
A pokud chcete koncovým čárkám povolený, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> na `true`. Následující příklad ukazuje, jak je možné:

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

Ve výchozím nastavení deserializace hledá název vlastnosti rozlišující velká a malá písmena mezi vlastnostmi JSON a cílovým objektem. Chcete-li toto chování změnit, nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> na `true`:

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

Pokud deserializaci kódu JSON zobrazeného na zobrazeném typu, `DatesAvailable` a `SummaryWords` vlastnosti mají nikde a budou ztraceny. Chcete-li zachytit další data, jako jsou tyto vlastnosti, použijte atribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) na vlastnost typu `Dictionary<string,object>` nebo `Dictionary<string,JsonElement>`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

Při deserializaci formátu JSON zobrazeného dříve do tohoto ukázkového typu se data dalších dat stávají páry klíč-hodnota vlastnosti `ExtensionData`:

|Vlastnost |Hodnota  |Poznámky:  |
|---------|---------|---------|
| Datum    | 8/1/2019 12:00:00 DOP. 07:00||
| TemperatureCelsius| 0 | Neshoda malých a velkých písmen (`temperatureCelsius` ve formátu JSON), takže vlastnost není nastavená. |
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

Všimněte si, že název vlastnosti `ExtensionData` se ve formátu JSON nezobrazuje. Díky tomuto chování může JSON vytvořit zpáteční cestu, aniž by došlo ke ztrátě dalších dat, která by jinak nebyla deserializována.

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

Po deserializaci má vlastnost `Summary` objektu `WeatherForecastWithDefault` hodnotu null.

Chcete-li toto chování změnit, nastavte <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> na `true`, jak je znázorněno v následujícím příkladu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

Při této možnosti je vlastnost `Summary` objektu `WeatherForecastWithDefault` výchozí hodnotou "No Summary" po deserializaci.

Hodnoty null ve formátu JSON jsou ignorovány pouze v případě, že jsou platné. Hodnoty null pro typy hodnot, které neumožňují hodnotu null, způsobují výjimky.

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter a JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> je pro text JSON s kódováním UTF-8 s vysokým výkonem vysoce výkonné, nízké přidělení a je čteno z `ReadOnlySpan<byte>` nebo `ReadOnlySequence<byte>`. `Utf8JsonReader` je typ nízké úrovně, který lze použít k vytvoření vlastních analyzátorů a deserializace. Metoda <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> používá `Utf8JsonReader` v rámci pokrývání.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> je vysoce výkonný způsob, jak psát text JSON kódovaný v kódování UTF-8 ze běžných typů .NET, jako jsou `String`, `Int32`a `DateTime`. Zapisovač je typ nižší úrovně, který lze použít k vytvoření vlastních serializátorů. Metoda <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> používá `Utf8JsonWriter` v rámci pokrývání.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> poskytuje možnost vytvářet model DOM (Document Object Model) DOM (jen pro čtení) pomocí `Utf8JsonReader`. Model DOM poskytuje náhodný přístup k datům v datové části JSON. K elementům JSON, které tvoří datovou část, lze přistupovat prostřednictvím <xref:System.Text.Json.JsonElement>ho typu. `JsonElement` typ poskytuje enumerátory Array a Object spolu s rozhraními API pro převod textu JSON na běžné typy .NET. `JsonDocument` zpřístupňuje vlastnost <xref:System.Text.Json.JsonDocument.RootElement>.

Následující části ukazují, jak používat tyto nástroje pro čtení a zápis JSON.

## <a name="use-jsondocument-for-access-to-data"></a>Použití JsonDocument pro přístup k datům

Následující příklad ukazuje, jak použít třídu <xref:System.Text.Json.JsonDocument> pro náhodný přístup k datům v řetězci JSON:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

Předchozí kód:

* Předpokládá, že se JSON, který se má analyzovat, nachází v řetězci s názvem `jsonString`.
* Vypočítá průměrnou třídu pro objekty v `Students` poli, které mají vlastnost `Grade`.
* Přiřadí výchozí stupeň 70 pro studenty, kteří nemají třídu.
* Počítá studenty zvýšením `count` proměnné s každou iterací. Alternativou je volání <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, jak je znázorněno v následujícím příkladu:

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

Zde je příklad kódu JSON, který tento kód zpracovává:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>Zápis JSON pomocí JsonDocument

Následující příklad ukazuje, jak zapsat JSON z <xref:System.Text.Json.JsonDocument>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

Předchozí kód:

* Přečte soubor JSON, načte data do `JsonDocument`a zapisuje do souboru formát JSON s formátováním (poměrně vytištěného).
* Používá <xref:System.Text.Json.JsonDocumentOptions> k určení, že komentáře ve vstupním JSON jsou povolené, ale ignorují se.
* Po dokončení volání zavolá <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> na zapisovači. Alternativou je umožnit zapisovači AutoFlush při jeho uvolnění.

Tady je příklad vstupu JSON, který se má zpracovat v příkladu kódu:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

Výsledkem je následující poměrně tištěný výstup JSON:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>Použití Utf8JsonWriter

Následující příklad ukazuje, jak použít třídu <xref:System.Text.Json.Utf8JsonWriter>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>Použití Utf8JsonReader

Následující příklad ukazuje, jak použít třídu <xref:System.Text.Json.Utf8JsonReader>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

Předchozí kód předpokládá, že proměnná `jsonUtf8` je bajtové pole, které obsahuje platný kód JSON kódovaný jako UTF-8.

### <a name="filter-data-using-utf8jsonreader"></a>Filtrování dat pomocí Utf8JsonReader

Následující příklad ukazuje, jak číst soubor synchronně a vyhledat hodnotu:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

Předchozí kód:

* Předpokládá, že JSON obsahuje pole objektů a každý objekt může obsahovat vlastnost Name typu String.
* Spočítá hodnoty vlastností Objects a Name, které končí na "University".
* Předpokládá, že soubor je kódovaný jako UTF-16 a překóduje ho do UTF-8. Soubor kódovaný jako UTF-8 lze číst přímo do `ReadOnlySpan<byte>`pomocí následujícího kódu:

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  Pokud soubor obsahuje znak pořadí bajtů UTF-8 (BOM), odeberte ho před předáním bajtů do `Utf8JsonReader`, protože čtecí modul očekává text. V opačném případě se kusovník považuje za neplatný kód JSON a čtenář vyvolá výjimku.

Zde je ukázka JSON, kterou může předchozí kód přečíst. Výsledná Souhrnná zpráva je "2 z čtvrtého" má názvy, které končí na "University" ":

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a>Další zdroje

* [Přehled System.Text.Json](system-text-json-overview.md)
* [Zápis vlastních převaděčů](system-text-json-converters-how-to.md)
* [Postup migrace z Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Podpora DateTime a DateTimeOffset v System.Text.Json](../datetime/system-text-json-support.md)
* [Reference k rozhraní API System.Text.Json](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
