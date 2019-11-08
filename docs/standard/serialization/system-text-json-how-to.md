---
title: Postup serializace a deserializace JSON C# pomocí-.NET
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: f0245feb710f33d5fcea2a7125b8753ba6064018
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740432"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a>Postup serializace a deserializace JSON v rozhraní .NET

> [!IMPORTANT]
> Dokumentace serializace JSON je vytvářena. Tento článek se nezabývá všemi scénáři. Další informace najdete v části [System. text. JSON – problémy](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) v úložišti dotnet/Corefx na GitHubu, zejména ty, které jsou označené jako [JSON-funkce-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).

Tento článek ukazuje, jak použít obor názvů <xref:System.Text.Json> k serializaci a deserializaci do a z JavaScript Object Notation (JSON). Pokyny a vzorový kód používají knihovnu přímo, nikoli prostřednictvím rozhraní, jako je například [ASP.NET Core](/aspnet/core/).

## <a name="namespaces"></a>Jmenné prostory

Obor názvů <xref:System.Text.Json> obsahuje všechny vstupní body a hlavní typy. Obor názvů <xref:System.Text.Json.Serialization> obsahuje atributy a rozhraní API pro pokročilé scénáře a přizpůsobení specifické pro serializaci a deserializaci. Příklady kódu, které jsou uvedené v tomto článku, vyžadují direktivy `using` pro jeden nebo oba tyto obory názvů:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

Atributy z oboru názvů <xref:System.Runtime.Serialization> nejsou v současné době podporovány v `System.Text.Json`.

## <a name="how-to-write-net-objects-to-json-serialize"></a>Zápis objektů .NET do formátu JSON (serializace)

Chcete-li zapsat JSON do řetězce nebo do souboru, zavolejte metodu <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.

Následující příklad vytvoří JSON jako řetězec:

```csharp
string json = JsonSerializer.Serialize(weatherForecast);
```

Následující příklad používá synchronní kód k vytvoření souboru JSON:

```csharp
File.WriteAllText(outputFileName, JsonSerializer.Serialize(weatherForecast));
```

Následující příklad používá asynchronní kód k vytvoření souboru JSON:

```csharp
using (FileStream fs = File.Create(outputFileName))
{
    await JsonSerializer.SerializeAsync(fs, weatherForecast);
}
```

Předchozí příklady používají odvození typu pro typ, který je serializován. Přetížení `Serialize()` přebírá parametr obecného typu:

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

### <a name="serialization-example"></a>Příklad serializace

Zde je příklad typu, který obsahuje kolekce a vnořené třídy:

```csharp
public class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public IList<DateTimeOffset> DatesAvailable { get; set;}
    public Dictionary<string, HighLowTemperatures> TemperatureRanges { get; set; }
    public string [] SummaryWords { get; set; }
}

public class HighLowTemperatures
{
    public Temperature High { get; set; }
    public Temperature Low { get; set; }
}

public class Temperature
{
    public int DegreesCelsius { get; set; }
}
```

Výstup JSON z serializace instance předchozího typu vypadá jako v následujícím příkladu. Výstup JSON je ve výchozím nastavení minifikovaného: 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

Následující příklad ukazuje stejný formát JSON (to znamená, že je poměrně vytištěn s prázdným znakem a odsazením):

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": {
        "DegreesCelsius": 20
      },
      "Low": {
        "DegreesCelsius": -10
      }
    },
    "Hot": {
      "High": {
        "DegreesCelsius": 60
      },
      "Low": {
        "DegreesCelsius": 20
      }
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

```csharp
byte[] jsonUtf8Bytes = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

K dispozici je také přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A>, které přijímá <xref:System.Text.Json.Utf8JsonWriter>.

Serializace do UTF-8 je přibližně 5-10% rychlejší než použití metod založených na řetězci. Rozdíl je z důvodu, že bajty (jako UTF-8) není nutné převést na řetězce (UTF-16).

## <a name="serialization-behavior"></a>Chování serializace

* Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti. Můžete [určit vlastnosti, které se mají vyloučit](#exclude-properties-from-serialization).
* [Výchozí kodér](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) řídí znaky jiné než ASCII, znaky citlivé na jazyk HTML v rozsahu ASCII a znaky, které musí být uvozeny podle [specifikace JSON](https://tools.ietf.org/html/rfc8259#section-7).
* Ve výchozím nastavení je JSON minifikovaného. [Kód JSON můžete v podstatě vytisknout](#serialize-to-formatted-json).
* Ve výchozím nastavení jsou malá a velká písmena názvů JSON shodná s názvy .NET. Můžete [přizpůsobit název a velikost písmen JSON](#customize-json-names-and-values).
* Byly zjištěny cyklické odkazy a byly vyvolány výjimky. Další informace najdete v tématu [problém u cyklických odkazů](https://github.com/dotnet/corefx/issues/38579) v úložišti dotnet/Corefx na GitHubu.
* V současné době jsou pole vyloučena.

Mezi podporované typy patří:

* Primitivní prvky .NET, které se mapují na primitivní prvky JavaScriptu, jako jsou číselné typy, řetězce a logická hodnota.
* Uživatelsky definované [prosté staré objekty CLR (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).
* Jednorozměrné a vícenásobná pole (`ArrayName[][]`).
* `Dictionary<string,TValue>`, kde `TValue` je `object`, `JsonElement` nebo POCO.
* Kolekce z následujících oborů názvů. Další informace najdete v tématu věnovaném [problému s podporou shromažďování](https://github.com/dotnet/corefx/issues/36643) v úložišti dotnet/Corefx na GitHubu.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

[Vlastní převaděče můžete implementovat](system-text-json-converters-how-to.md) pro zpracování dalších typů nebo poskytování funkcí, které nejsou podporované integrovanými převaděči.

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Postup čtení formátu JSON do objektů .NET (deserializace)

Chcete-li provést deserializaci z řetězce nebo souboru, zavolejte metodu <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.

Následující příklad přečte JSON z řetězce:

```csharp
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

Chcete-li provést deserializaci ze souboru pomocí synchronního kódu, přečtěte si soubor do řetězce, jak je znázorněno v následujícím příkladu:

```csharp
string jsonString = File.ReadAllText(inputFileName);
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

Chcete-li provést deserializaci ze souboru pomocí asynchronního kódu, zavolejte metodu <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A>:

```csharp
using (FileStream fs = File.OpenRead(inputFileName))
{
    weatherForecast = await JsonSerializer.DeserializeAsync<WeatherForecast>(fs);
}
```

Vzorový typ a odpovídající JSON najdete v části [příklad serializace](#serialization-example) .

### <a name="deserialize-from-utf-8"></a>Deserializace ze znakové sady UTF-8

Chcete-li provést deserializaci ze znakové sady UTF-8, zavolejte <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> přetížení, které přebírá `Utf8JsonReader` nebo `ReadOnlySpan<byte>`, jak je znázorněno v následujících příkladech. V příkladech se předpokládá, že je JSON v bajtovém poli s názvem jsonUtf8Bytes.

```csharp
var readOnlySpan = new ReadOnlySpan<byte>(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
var utf8Reader = new Utf8JsonReader(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a>Chování deserializace

* Ve výchozím nastavení se při porovnávání názvů vlastností rozlišují velká a malá písmena. Můžete [zadat nerozlišování velkých a malých písmen](#case-insensitive-property-matching).
* Pokud JSON obsahuje hodnotu vlastnosti jen pro čtení, hodnota je ignorována a není vyvolána žádná výjimka.
* Deserializace na odkazové typy bez bezparametrového konstruktoru není podporována.
* Deserializace u neměnných objektů nebo vlastností jen pro čtení není podporována. Další informace najdete v tématu věnovaném problému na GitHubu [s neproměnlivou podporou objektů](https://github.com/dotnet/corefx/issues/38569) a [problému s podporou vlastnosti jen pro čtení](https://github.com/dotnet/corefx/issues/38163) v úložišti dotnet/corefx na GitHubu.
* Ve výchozím nastavení jsou výčty podporovány jako čísla. [Názvy výčtů můžete serializovat jako řetězce](#enums-as-strings).
* Pole nejsou podporována.
* Ve výchozím nastavení komentáře nebo koncové čárky ve formátu JSON vyvolají výjimky. Můžete [povolovat komentáře a koncové čárky](#allow-comments-and-trailing-commas).
* [Výchozí maximální hloubka](xref:System.Text.Json.JsonReaderOptions.MaxDepth) je 64.

[Vlastní převaděče můžete implementovat](system-text-json-converters-how-to.md) pro poskytování funkcí, které nejsou podporované integrovanými převaděči.

## <a name="serialize-to-formatted-json"></a>Serializovat do formátovaného formátu JSON

Chcete-li, aby výstup JSON byl poměrně vytištěn, nastavte <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> na `true`:

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Tady je příklad typu pro serializaci a poměrně tištěné výstup JSON:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a>Přizpůsobení názvů a hodnot JSON

Ve výchozím nastavení se názvy vlastností a klíče slovníku ve výstupu JSON nezměnily, včetně případu. Hodnoty výčtu jsou reprezentovány jako čísla. V této části se dozvíte, jak:

* Přizpůsobení jednotlivých názvů vlastností
* Převést názvy všech vlastností na velikost ve stylu CamelCase
* Implementace vlastní zásady pro pojmenovávání vlastností
* Převede klíče slovníku na ve stylu CamelCase případ.
* Převod výčtů na řetězce a ve stylu CamelCase velikost písmen 

Pro jiné scénáře, které vyžadují speciální zpracování názvů a hodnot vlastností JSON, můžete [implementovat vlastní převaděče](system-text-json-converters-how-to.md).

### <a name="customize-individual-property-names"></a>Přizpůsobení jednotlivých názvů vlastností

Chcete-li nastavit název jednotlivých vlastností, použijte atribut [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .

Tady je příklad typu k serializaci a výslednému formátu JSON:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

Název vlastnosti nastavený tímto atributem:

* Platí v obou směrech pro serializaci a deserializaci.
* Má přednost před zásadami pro pojmenovávání vlastností.

### <a name="use-camel-case-for-all-json-property-names"></a>Pro všechny názvy vlastností JSON použijte ve stylu CamelCase Case

Pro použití ve stylu CamelCase pro všechny názvy vlastností JSON nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na `JsonNamingPolicy.CamelCase`, jak je znázorněno v následujícím příkladu:

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Tady je příklad třídy pro serializaci a výstup JSON:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

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

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

Pak nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na instanci třídy zásad pojmenování:

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Tady je příklad třídy pro serializaci a výstup JSON:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATUREC": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

Zásady pojmenování vlastností JSON:

* Platí pro serializaci a deserializaci.
* Je přepsán `[JsonPropertyName]` atributy. Důvodem je, že název vlastnosti JSON `Wind` v příkladu není velká písmena.

### <a name="camel-case-dictionary-keys"></a>Klíče slovníku případů ve stylu CamelCase

Pokud je vlastnost objektu, která má být serializována, typu `Dictionary<string,TValue>`, klíče `string` lze převést na ve stylu CamelCase případ. To provedete tak, že nastavíte <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> na `JsonNamingPolicy.CamelCase`, jak je znázorněno v následujícím příkladu:

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Serializace objektu se slovníkem s názvem `TemperatureRanges`, který má páry klíč-hodnota `"ColdMinTemp", 20` a `"HotMinTemp", 40` by vedlo jako výstup JSON jako v následujícím příkladu:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
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

```csharp
class WeatherForecastWithEnum
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public Summary Summary { get; set; }
}

public enum Summary
{
    Cold, Cool, Warm, Hot
}
```

Pokud je souhrn `Hot`, ve výchozím nastavení má serializovaný formát JSON číselnou hodnotu 3:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": 3
}
```

Následující vzorový kód místo toho serializace názvy výčtů a převede je na ve stylu CamelCase případ:

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
jsonWithEnumsAsStrings = JsonSerializer.Serialize(weatherForecastWithEnum, options);
```

Výsledný kód JSON vypadá jako v následujícím příkladu:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "hot"
}
```

Podpora výčtů jako řetězců platí také pro deserializaci, jak je znázorněno v následujícím příkladu:

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
weatherForecastWithEnum = JsonSerializer.Deserialize<WeatherForecastWithEnum>(jsonWithEnumsAsStrings, options);
```

## <a name="exclude-properties-from-serialization"></a>Vyloučit vlastnosti ze serializace

Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti. Pokud nechcete, aby se některé z nich zobrazovaly ve výstupu JSON, máte několik možností. V této části se dozvíte, jak vyloučit:

* Jednotlivé vlastnosti
* Všechny vlastnosti jen pro čtení
* Všechny vlastnosti s hodnotou null 

### <a name="exclude-individual-properties"></a>Vyloučení individuálních vlastností

Chcete-li ignorovat jednotlivé vlastnosti, použijte atribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .

Tady je příklad typu pro serializaci a výstup JSON:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonIgnore]
    public int WindSpeed { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

### <a name="exclude-all-read-only-properties"></a>Vyloučit všechny vlastnosti jen pro čtení

Vlastnost je jen pro čtení, pokud obsahuje veřejnou metodu getter, ale ne veřejnou metodu setter. Chcete-li vyloučit všechny vlastnosti jen pro čtení, nastavte <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> na `true`, jak je znázorněno v následujícím příkladu:

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Tady je příklad typu pro serializaci a výstup JSON:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public int WindSpeed { get; private set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

Tato možnost se vztahuje pouze na serializaci. Během deserializace jsou vlastnosti jen pro čtení ve výchozím nastavení ignorovány.

### <a name="exclude-all-null-value-properties"></a>Vyloučit všechny vlastnosti hodnoty null

Chcete-li vyloučit všechny vlastnosti hodnoty null, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> na hodnotu `true`, jak je znázorněno v následujícím příkladu:

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Zde je příklad objektu pro serializaci a výstup JSON:

|Vlastnost |Hodnota  |
|---------|---------|
| Datum    | 8/1/2019 12:00:00 DOP. 07:00|
| TemperatureC| 0,25 |
| Souhrn| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

Toto nastavení platí pro serializaci a deserializaci. Informace o jeho vlivu na deserializaci naleznete v tématu [Ignore null Při deserializaci](#ignore-null-when-deserializing).

## <a name="customize-character-encoding"></a>Přizpůsobení kódování znaků

Ve výchozím nastavení serializátor řídí všechny znaky jiné než ASCII.  To znamená, že je nahradí je `\uxxxx`, kde `xxxxx` je kód Unicode znaku.  Například pokud je vlastnost `Summary` nastavena na жаркоa v cyrilici, `WeatherForecast` objekt je serializován, jak je znázorněno v následujícím příkladu:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Serializovat znakové sady jazyků

Chcete-li serializovat znakové sady jednoho nebo více jazyků, zadejte [rozsahy Unicode](xref:System.Text.Unicode.UnicodeRanges) při vytváření instance <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, jak je znázorněno v následujícím příkladu:

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;
```

```csharp
var options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.Create(UnicodeRanges.Cyrillic, UnicodeRanges.GreekExtended)
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Tento kód serializovat cyrilici a řecké znaky. V následujícím příkladu jsou uvedeny znaky cyriliceu:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жарко",
}
```

Chcete-li určit všechny jazyky, použijte <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.

### <a name="serialize-specific-characters"></a>Serializovat konkrétní znaky

Alternativou je zadání jednotlivých znaků, které chcete použít, bez nutnosti řídicích znaků. Následující příklad serializace pouze prvních dvou znaků жарко:

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;
```

```csharp
var encoderSettings = new TextEncoderSettings();
encoderSettings.AllowCharacters('\u0436', '\u0430');
options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.Create(encoderSettings)
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Zde je příklad kódu JSON vytvořeného předchozím kódem:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>Serializovat všechny znaky

Chcete-li minimalizovat uvozovací znaky, můžete použít <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, jak je znázorněno v následujícím příkladu:

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
```

```csharp
options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.UnsafeRelaxedJsonEscaping
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

> [!CAUTION]
> Na rozdíl od výchozího kodéru `UnsafeRelaxedJsonEscaping` kodér:
>
> * Neřídí znaky citlivé na HTML, například `<`, `>`, `&`a `'`.
> * Nenabízí žádné další ochrany proti důkladné ochraně před útoky XSS nebo informací, jako jsou ty, které by mohly vést k tomu *, že klient*a server nesouhlasí.
> * Je přísnější než výchozí kodér, na kterém jsou povoleny znaky bez řídicích znaků.
>
> Nezabezpečený kodér používejte pouze v případě, že je známo, že klient bude interpretovat výslednou datovou část jako JSON kódovaný v kódování UTF-8. Můžete ji například použít, pokud server odesílá hlavičku odpovědi `Content-Type: application/json; charset=utf-8`. Nikdy nepovolujte výstup nezpracovaného `UnsafeRelaxedJsonEscaping` do stránky HTML nebo elementu `<script>`.

## <a name="serialize-properties-of-derived-classes"></a>Serializovat vlastnosti odvozených tříd

Polymorfní serializace není podporována, pokud zadáte v době kompilace typ, který se má serializovat. Předpokládejme například, že máte třídu `WeatherForecast` a odvozenou třídu `WeatherForecastWithWind`:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
class WeatherForecastWithWind : WeatherForecast
{
    public int WindSpeed { get; set; }
}
```

A Předpokládejme, že argument typu metody `Serialize` v době kompilace je `WeatherForecast`:

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

V tomto scénáři není vlastnost `WindSpeed` serializována, i když je objekt `weatherForecast` ve skutečnosti objekt `WeatherForecastWithWind`. Serializovat se budou jenom vlastnosti základní třídy:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

Toto chování je určeno k tomu, aby se zabránilo náhodnému úniku dat v odvozeném typu vytvořeném modulem runtime.

Chcete-li serializovat vlastnosti odvozeného typu, použijte jeden z následujících přístupů:

* Zavolejte přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A>, které umožňuje určit typ za běhu:

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* Deklarujte objekt, který se má serializovat jako `object`.

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

V předchozím ukázkovém scénáři oba přístupy způsobí, že se vlastnost `WindSpeed` zahrne do výstupu JSON:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

Informace o polymorfní deserializaci naleznete v tématu [Podpora polymorfního deserializace](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

## <a name="allow-comments-and-trailing-commas"></a>Povolí komentáře a koncové čárky.

Ve výchozím nastavení se komentáře a koncové čárky ve formátu JSON nepovolují. Chcete-li ve formátu JSON dovolit komentáře, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> na hodnotu `JsonCommentHandling.Skip`. A pokud chcete koncovým čárkám povolený, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> na hodnotu `true`. Následující příklad ukazuje, jak je možné:

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

Tady je příklad JSON s komentáři a koncovou čárkou:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>Porovnávání vlastností bez rozlišení velkých a malých písmen

Ve výchozím nastavení deserializace hledá název vlastnosti rozlišující velká a malá písmena mezi vlastnostmi JSON a cílovým objektem. Chcete-li toto chování změnit, nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> na `true`:

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

Tady je příklad JSON s názvy vlastností Case ve stylu CamelCase. Lze deserializovat do následujícího typu, který má názvy vlastností Case typu Pascal.

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "summary": "Hot",
}
```

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="handle-overflow-json"></a>Přetečení JSON popisovače

Při deserializaci můžete přijímat data ve formátu JSON, která nejsou reprezentovaná vlastnostmi cílového typu. Předpokládejme například, že váš cílový typ je:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

A JSON, který se má deserializovat, je:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
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

Pokud deserializaci kódu JSON zobrazeného na zobrazeném typu, vlastnosti `DatesAvailable` a `SummaryWords` mají nikde k přechodu a jsou ztraceny. Chcete-li zachytit další data, jako jsou tyto vlastnosti, použijte atribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) na vlastnost typu `Dictionary<string,object>` nebo `Dictionary<string,JsonElement>`:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonExtensionData]
    public Dictionary<string, object> ExtensionData { get; set; }
}
```

Při deserializaci formátu JSON zobrazeného dříve do tohoto ukázkového typu se data dalších dat stávají páry klíč-hodnota vlastnosti `ExtensionData`:

|Vlastnost |Hodnota  |Poznámky  |
|---------|---------|---------|
| Datum    | 8/1/2019 12:00:00 DOP. 07:00||
| TemperatureC| 0,8 | Neshoda malých a velkých písmen (`temperatureC` ve formátu JSON), takže vlastnost není nastavená. |
| Souhrn | Provozu ||
| ExtensionData – | temperatureC: 25 |Vzhledem k tomu, že se neshoduje velká a malá písmena, je tato vlastnost JSON extra a ve slovníku se stala dvojicí klíč-hodnota.|
|| DatesAvailable:<br>  8/1/2019 12:00:00 DOP. 07:00<br>8/2/2019 12:00:00 DOP. 07:00 |Vlastnost extra z formátu JSON se stávají dvojicí klíč-hodnota s polem jako objektem hodnoty.|
| |SummaryWords:<br>Dobré<br>Vítr<br>Humid |Vlastnost extra z formátu JSON se stávají dvojicí klíč-hodnota s polem jako objektem hodnoty.|

Při serializaci cílového objektu se dvojice hodnoty klíče dat rozšíření stanou vlastnostmi JSON stejně, jako kdyby byly ve vstupním formátu JSON:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 0,
  "Summary": "Hot",
  "temperatureC": 25,
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

```csharp
class WeatherForecastWithDefault
{
    public WeatherForecastWithDefault()
    {
        Summary = "No summary";
    }
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

A Předpokládejme, že následující kód JSON je deserializovaný:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": null,
}
```

Po deserializaci má vlastnost `Summary` objektu `WeatherForecastWithDefault` hodnotu null.

Chcete-li toto chování změnit, nastavte <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> na `true`, jak je znázorněno v následujícím příkladu:

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithDefault>(json, options);
```

Při této možnosti je vlastnost `Summary` objektu `WeatherForecastWithDefault` výchozí hodnotou "No Summary" po deserializaci.

Hodnoty null ve formátu JSON jsou ignorovány pouze v případě, že jsou platné. Hodnoty null pro typy hodnot, které neumožňují hodnotu null, způsobují výjimky. Další informace najdete v tématu [problém s typy hodnot, které](https://github.com/dotnet/corefx/issues/40922) neumožňují hodnotu null v úložišti dotnet/Corefx na GitHubu.

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter a JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> je pro text JSON s kódováním UTF-8 s vysokým výkonem, který je určený jen pro čtení, načtený z `ReadOnlySpan<byte>`. `Utf8JsonReader` je typ nízké úrovně, který lze použít k vytvoření vlastních analyzátorů a deserializace. Metoda <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> používá `Utf8JsonReader` v rámci pokrývání.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> je vysoce výkonný způsob, jak psát text JSON kódovaný v kódování UTF-8 ze běžných typů .NET, jako jsou `String`, `Int32`a `DateTime`. Zapisovač je typ nižší úrovně, který lze použít k vytvoření vlastních serializátorů. Metoda <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> používá `Utf8JsonWriter` v rámci pokrývání.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> poskytuje možnost vytvářet model DOM (Document Object Model) DOM (jen pro čtení) pomocí `Utf8JsonReader`. Model DOM poskytuje náhodný přístup k datům v datové části JSON. K elementům JSON, které tvoří datovou část, lze přistupovat prostřednictvím <xref:System.Text.Json.JsonElement>ho typu. `JsonElement` poskytuje enumerátory Array a Object společně s rozhraními API pro převod textu JSON na běžné typy .NET. `JsonDocument` zpřístupňuje vlastnost <xref:System.Text.Json.JsonDocument.RootElement>.

Následující části ukazují, jak používat tyto nástroje pro čtení a zápis JSON.

## <a name="use-jsondocument-for-access-to-data"></a>Použití JsonDocument pro přístup k datům

Následující příklad ukazuje, jak použít třídu <xref:System.Text.Json.JsonDocument> pro náhodný přístup k datům:

```csharp
double sum = 0;
int count = 0;

using (JsonDocument document = JsonDocument.Parse(jsonString))
{
    JsonElement root = document.RootElement;
    JsonElement studentsElement = root.GetProperty("Students");
    foreach (JsonElement student in studentsElement.EnumerateArray())
    {
        if (student.TryGetProperty("Grade", out JsonElement gradeElement))
        {
            sum += gradeElement.GetDouble();
        }
        else
        {
            sum += 70;
        }
        count++;
    }
}

double average = sum / count;
Console.WriteLine($"Average grade: {average}");
```

Předchozí kód:

* Předpokládá, že se JSON, který se má analyzovat, nachází v řetězci s názvem `jsonString`.
* Vypočítá průměrnou třídu pro objekty v `Students` poli, které mají vlastnost `Grade`. 
* Přiřadí výchozí stupeň 70 pro studenty, kteří nemají třídu.
* Počítá studenty zvýšením `count` proměnné s každou iterací. Alternativou je volání <xref:System.Text.Json.JsonElement.GetArrayLength%2A>:

  ```csharp
  count = studentsElement.GetArrayLength();
  ```

Zde je příklad kódu JSON, který tento kód zpracovává:

```json
{
  "Class Name": "Science",
  "Teacher's Name": "Jane",
  "Semester": "2019-01-01",
  "Students": [
    {
      "Name": "John",
      "Grade": 94.3
    },
    {
      "Name": "James",
      "Grade": 81.0
    },
    {
      "Name": "Julia",
      "Grade": 91.9
    },
    {
      "Name": "Jessica",
      "Grade": 72.4
    },
    {
      "Name": "Johnathan"
    }
  ],
  "Final": true
}
```

## <a name="use-jsondocument-to-write-json"></a>Zápis JSON pomocí JsonDocument

Následující příklad ukazuje, jak zapsat JSON z <xref:System.Text.Json.JsonDocument>:

```csharp
string jsonString = File.ReadAllText(inputFileName);

var writerOptions = new JsonWriterOptions { Indented = true };
var documentOptions = new JsonDocumentOptions { CommentHandling = JsonCommentHandling.Skip };

using (FileStream fs = File.Create(outputFileName))
using (var writer = new Utf8JsonWriter(fs, options: writerOptions))
using (JsonDocument document = JsonDocument.Parse(jsonString, documentOptions))
{
    JsonElement root = document.RootElement;

    if (root.ValueKind == JsonValueKind.Object)
    {
        writer.WriteStartObject();
    }
    else
    {
        return;
    }

    foreach (JsonProperty property in root.EnumerateObject())
    {
        property.WriteTo(writer);
    }

    writer.WriteEndObject();

    writer.Flush();
}
```

Předchozí kód:

* Přečte soubor JSON, načte data do `JsonDocument`a zapisuje do souboru formát JSON s formátováním (poměrně vytištěného).
* Používá <xref:System.Text.Json.JsonDocumentOptions> k určení, že komentáře ve vstupním JSON jsou povolené, ale ignorují se.
* Po dokončení volání zavolá <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> na zapisovači. Alternativou je umožnit zapisovači AutoFlush při jeho uvolnění. 

Tady je příklad vstupu JSON, který se má zpracovat v příkladu kódu:

```json
{"Class Name": "Science","Teacher's Name": "Jane","Semester": "2019-01-01","Students": [{"Name": "John","Grade": 94.3},{"Name": "James","Grade": 81.0},{"Name": "Julia","Grade": 91.9},{"Name": "Jessica","Grade": 72.4},{"Name": "Johnathan"}],"Final": true}
```

Výsledkem je následující poměrně tištěný výstup JSON:

```json
{
  "Class Name": "Science",
  "Teacher\u0027s Name": "Jane",
  "Semester": "2019-01-01",
  "Students": [
    {
      "Name": "John",
      "Grade": 94.3
    },
    {
      "Name": "James",
      "Grade": 81.0
    },
    {
      "Name": "Julia",
      "Grade": 91.9
    },
    {
      "Name": "Jessica",
      "Grade": 72.4
    },
    {
      "Name": "Johnathan"
    }
  ],
  "Final": true
}
```

## <a name="use-utf8jsonwriter"></a>Použití Utf8JsonWriter

Následující příklad ukazuje, jak použít třídu <xref:System.Text.Json.Utf8JsonWriter>:

```csharp
var options = new JsonWriterOptions
{
    Indented = true
};

using (var stream = new MemoryStream())
{
    using (var writer = new Utf8JsonWriter(stream, options))
    {
        writer.WriteStartObject();
        writer.WriteString("date", DateTimeOffset.UtcNow);
        writer.WriteNumber("temp", 42);
        writer.WriteEndObject();
    }

    string json = Encoding.UTF8.GetString(stream.ToArray());
    Console.WriteLine(json);
}
```

## <a name="use-utf8jsonreader"></a>Použití Utf8JsonReader

Následující příklad ukazuje, jak použít třídu <xref:System.Text.Json.Utf8JsonReader>:

```csharp
var options = new JsonReaderOptions
{
    AllowTrailingCommas = true,
    CommentHandling = JsonCommentHandling.Skip
};
Utf8JsonReader reader = new Utf8JsonReader(jsonUtf8, options);

while (reader.Read())
{
    Console.Write(reader.TokenType);

    switch (reader.TokenType)
    {
        case JsonTokenType.PropertyName:
        case JsonTokenType.String:
            {
                string text = reader.GetString();
                Console.Write(" ");
                Console.Write(text);
                break;
            }

        case JsonTokenType.Number:
            {
                int value = reader.GetInt32();
                Console.Write(" ");
                Console.Write(value);
                break;
            }

            // Other token types elided for brevity
    }

    Console.WriteLine();
}
```

Předchozí kód předpokládá, že proměnná `jsonUtf8` je bajtové pole, které obsahuje platný kód JSON kódovaný jako UTF-8.

### <a name="filter-data-using-utf8jsonreader"></a>Filtrování dat pomocí Utf8JsonReader

Následující příklad ukazuje, jak číst soubor synchronně a vyhledat hodnotu:

```csharp
class Program
{
    private static readonly byte[] s_nameUtf8 = Encoding.UTF8.GetBytes("name");
    private static readonly byte[] s_universityUtf8 = Encoding.UTF8.GetBytes("University");

    private static void ReaderFromFileSync(string fileName)
    {
         string jsonString = File.ReadAllText(fileName);
         ReadOnlySpan<byte> jsonReadOnlySpan = Encoding.UTF8.GetBytes(jsonString);

        int count = 0;
        int total = 0;

        var json = new Utf8JsonReader(jsonReadOnlySpan, isFinalBlock: true, state: default);

        while (json.Read())
        {
            JsonTokenType tokenType = json.TokenType;

            switch (tokenType)
            {
                case JsonTokenType.StartObject:
                    total++;
                    break;
                case JsonTokenType.PropertyName:
                    if (json.ValueSpan.SequenceEqual(s_nameUtf8))
                    {
                        bool result = json.Read();

                        Debug.Assert(result);  // Assume valid JSON
                        Debug.Assert(json.TokenType == JsonTokenType.String);   // Assume known, valid JSON schema

                        if (json.ValueSpan.EndsWith(s_universityUtf8))
                        {
                            count++;
                        }
                    }
                    break;
            }
        }
        Console.WriteLine($"{count} out of {total} have names that end with 'University'");
    }
}
```

Předchozí kód:

* Předpokládá, že soubor je kódovaný jako UTF-16 a překóduje ho do UTF-8. Soubor kódovaný jako UTF-8 lze číst přímo do `ReadOnlySpan<byte>`pomocí následujícího kódu:

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* Předpokládá, že JSON obsahuje pole objektů a každý objekt může obsahovat vlastnost Name typu String.
* Počítá objekty a `name` hodnoty vlastností, které končí na "University".

Zde je ukázka JSON, kterou může předchozí kód přečíst. Výsledná Souhrnná zpráva je "2 z čtvrtého" má názvy, které končí na "University" ":

```json
[
  {
    "web_pages": [ "https://contoso.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "contoso.edu" ],
    "name": "Contoso Community College"
  },
  {
    "web_pages": [ "http://fabrikam.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "fabrikam.edu" ],
    "name": "Fabrikam Community College"
  },
  {
    "web_pages": [ "http://www.contosouniversity.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "contosouniversity.edu" ],
    "name": "Contoso University"
  },
  {
    "web_pages": [ "http://www.fabrikamuniversity.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "fabrikamuniversity.edu" ],
    "name": "Fabrikam University"
  }
]
```

## <a name="additional-resources"></a>Další zdroje

* [Přehled System. text. JSON](system-text-json-overview.md)
* [Reference k rozhraní API System. text. JSON](xref:System.Text.Json)
* [Zápis vlastních převaděčů pro System. text. JSON](system-text-json-converters-how-to.md)
* [Podpora DateTime a DateTimeOffset v System. text. JSON](../datetime/system-text-json-support.md)
