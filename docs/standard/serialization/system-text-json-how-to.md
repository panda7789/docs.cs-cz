---
title: Postup serializace JSON-.NET
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 8ccd7afe4abb928e7723aa740507774012fc85d1
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083100"
---
# <a name="how-to-serialize-json-in-net"></a>Postup serializace JSON v .NET

> [!IMPORTANT]
> Dokumentace serializace JSON je vytvářena. Tento článek se nezabývá všemi scénáři. Další informace najdete v části [System. text. JSON – problémy](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) v úložišti dotnet/Corefx na GitHubu, zejména ty, které jsou označené jako [JSON-funkce-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).

Tento článek ukazuje, jak použít <xref:System.Text.Json> obor názvů k serializaci a deserializaci do a z JavaScript Object Notation (JSON). Pokyny a vzorový kód používají knihovnu přímo, nikoli prostřednictvím rozhraní, jako je například [ASP.NET Core](/aspnet/core/).

## <a name="namespaces"></a>Jmenné prostory

<xref:System.Text.Json> Obor názvů obsahuje všechny vstupní body a hlavní typy. <xref:System.Text.Json.Serialization> Obor názvů obsahuje atributy a rozhraní API pro pokročilé scénáře a přizpůsobení specifické pro serializaci a deserializaci. Proto příklady kódu, které jsou uvedeny v tomto článku, vyžadují jednu nebo obě následující `using` direktivy:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

Atributy z oboru <xref:System.Runtime.Serialization> názvů se v `System.Text.Json`současné době nepodporují.

## <a name="how-to-write-net-objects-to-json-serialize"></a>Zápis objektů .NET do formátu JSON (serializace)

Chcete-li zapsat JSON do řetězce, zavolejte <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> metodu. Následující příklad používá přetížení s parametrem obecného typu:

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

Můžete vynechat parametr obecného typu a místo toho použít odvození obecného typu:

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

Zde je příklad typu k serializaci, který obsahuje kolekce a vnořené třídy:

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

Výstup JSON je ve výchozím nastavení minifikovaného: 

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

Přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A> umožňují serializovat <xref:System.IO.Stream>na. Jsou k dispozici `Stream` asynchronní verze přetížení.

### <a name="serialize-to-utf-8"></a>Serializovat do UTF-8

Pro serializaci do UTF-8 volejte <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> metodu:

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

Alternativně <xref:System.Text.Json.JsonSerializer.Serialize%2A> <xref:System.Text.Json.Utf8JsonWriter> je k dispozici přetížení, které přijímá.

Serializace do UTF-8 je přibližně 5-10% rychlejší než použití metod založených na řetězci. Rozdíl je z důvodu, že bajty (jako UTF-8) není nutné převést na řetězce (UTF-16).

## <a name="serialization-behavior"></a>Chování serializace

* Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti. Můžete [určit vlastnosti, které se mají vyloučit](#exclude-properties).
* [Výchozí kodér](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) řídí znaky jiné než ASCII, znaky citlivé na jazyk HTML v rozsahu ASCII a znaky, které musí být uvozeny podle [specifikace JSON](https://tools.ietf.org/html/rfc8259#section-7).
* Ve výchozím nastavení je JSON minifikovaného. [Kód JSON můžete v podstatě vytisknout](#serialize-to-formatted-json).
* Ve výchozím nastavení jsou malá a velká písmena názvů JSON shodná s názvy .NET. Můžete [přizpůsobit název a velikost písmen JSON](#customize-json-names).
* Byly zjištěny cyklické odkazy a byly vyvolány výjimky. Další informace najdete v tématu [problém u cyklických odkazů](https://github.com/dotnet/corefx/issues/38579) v úložišti dotnet/Corefx na GitHubu.
* V současné době jsou pole vyloučena.

Mezi podporované typy patří:

* Primitivní prvky .NET, které se mapují na primitivní prvky JavaScriptu, jako jsou číselné typy, řetězce a logická hodnota.
* Uživatelsky definované [prosté staré objekty CLR (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).
* Jednorozměrné a vícenásobná pole (`ArrayName[][]`).
* `Dictionary<string,TValue>`Where `TValue` je `object` ,`JsonElement`nebo POCO.
* Kolekce z následujících oborů názvů. Další informace najdete v tématu věnovaném [problému s podporou shromažďování](https://github.com/dotnet/corefx/issues/36643) v úložišti dotnet/Corefx na GitHubu.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a>Postup čtení formátu JSON do objektů .NET (deserializace)

Chcete-li provést deserializaci z řetězce <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> , zavolejte metodu, jak je znázorněno v následujícím příkladu:

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

Příklad naleznete v části [serializovat](#how-to-write-net-objects-to-json-serialize) . Objekt JSON a objekt .NET jsou stejné, ale směr je obrácený.

Přetížení <xref:System.Text.Json.JsonSerializer.Deserialize*> umožňují deserializovat `Stream`z.  Jsou k dispozici `Stream` asynchronní verze přetížení.

### <a name="deserialize-from-utf-8"></a>Deserializace ze znakové sady UTF-8

Chcete-li deserializovat ze znakové sady UTF- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> 8, zavolejte přetížení `Utf8JsonReader` , které `ReadOnlySpan<byte>`přijímá nebo, jak je znázorněno v následujících příkladech:

```csharp
byte[] utf8Json;
//...
var readOnlySpan = new ReadOnlySpan<byte>(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
byte[] utf8Json;
//...
var utf8Reader = new Utf8JsonReader(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a>Chování deserializace

* Ve výchozím nastavení se při porovnávání názvů vlastností rozlišují velká a malá písmena. Můžete [zadat nerozlišování velkých a malých písmen](#case-insensitive-property-matching).
* Pokud JSON obsahuje hodnotu vlastnosti jen pro čtení, hodnota je ignorována a není vyvolána žádná výjimka.
* Deserializace na odkazové typy bez bezparametrového konstruktoru není podporována.
* Deserializace u neměnných objektů nebo vlastností jen pro čtení není podporována. Další informace najdete v tématu věnovaném problému na GitHubu [s neproměnlivou podporou objektů](https://github.com/dotnet/corefx/issues/38569) a [problému s podporou vlastnosti jen pro čtení](https://github.com/dotnet/corefx/issues/38163) v úložišti dotnet/corefx na GitHubu.
* Ve výchozím nastavení jsou výčty podporovány jako čísla.
* Pole nejsou podporována.
* Ve výchozím nastavení komentáře nebo koncové čárky ve formátu JSON vyvolají výjimky. V případě potřeby můžete v případě potřeby [povolovat komentáře a koncové čárky](#allow-comments-and-trailing-commas) .
* [Výchozí maximální hloubka](xref:System.Text.Json.JsonReaderOptions.MaxDepth) je 64.

## <a name="serialize-to-formatted-json"></a>Serializovat do formátovaného formátu JSON

Pro poměrně vytisknutí výstupu JSON nastavte <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> na: `true`

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Zde je příklad typu pro serializaci a výstup JSON:

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

## <a name="allow-comments-and-trailing-commas"></a>Povolí komentáře a koncové čárky.

Výchozí komentáře a koncové čárky nejsou ve formátu JSON povoleny. Chcete-li ve formátu JSON dovolit komentáře, <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> nastavte vlastnost `JsonCommentHandling.Skip`na hodnotu. A chcete-li použít koncové čárky, nastavte <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> vlastnost na `true`hodnotu. Následující příklad ukazuje, jak je možné:

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

## <a name="customize-json-names"></a>Přizpůsobení názvů JSON

Ve výchozím nastavení se názvy vlastností a klíče slovníku ve výstupu JSON nezměnily, včetně případu. V této části se dozvíte, jak:

* Přizpůsobení jednotlivých názvů vlastností
* Převést názvy všech vlastností na velikost ve stylu CamelCase
* Implementace vlastní zásady pro pojmenovávání vlastností
* Převede klíče slovníku na ve stylu CamelCase případ.

V současné době neexistuje žádná podpora pro automatické převádění výčtů na ve stylu CamelCase případ. Další informace najdete v tématu [problém ve stylu CamelCase enum – podpora případu](https://github.com/dotnet/corefx/issues/37725) v úložišti dotnet/Corefx na GitHubu.

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
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "summary": "Hot",
  "Wind": 35
}
```

Zásada pro pojmenování vlastností případu ve stylu CamelCase:

* Platí pro serializaci a deserializaci.
* Je potlačen `[JsonPropertyName]` atributy.

### <a name="use-a-custom-json-property-naming-policy"></a>Použít vlastní zásady pojmenování vlastností JSON

Chcete-li použít vlastní zásadu pojmenovávání vlastností JSON, vytvořte třídu, která <xref:System.Text.Json.JsonNamingPolicy> je odvozena <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> z třídy, a přepište metodu, jak je znázorněno v následujícím příkladu:

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

Pak nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> vlastnost na instanci třídy zásad pojmenování:

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
* Je potlačen `[JsonPropertyName]` atributy.

### <a name="camel-case-dictionary-keys"></a>Klíče slovníku případů ve stylu CamelCase

Pokud je vlastnost objektu `Dictionary<string,TValue>` `string` , který má být serializován, typu, lze klíče převést na ve stylu CamelCase případ. To provedete tak <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> , `JsonNamingPolicy.CamelCase`že nastavíte na, jak je znázorněno v následujícím příkladu:

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Zde je příklad objektu pro serializaci a výstup JSON:

|Vlastnost |Value  |
|---------|---------|
| Datum    | 8/1/2019 12:00:00 DOP. 07:00|
| TemperatureC| 25 |
| Souhrn| Provozu|
| TemperatureRanges | Studená, 20<br>Horká, 40|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "cold": 20,
    "hot": 40
  }
}
```

Zásady pro pojmenování případů ve stylu CamelCase se vztahují pouze na serializaci.

## <a name="exclude-properties"></a>Vlastnosti vyloučení

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

Chcete-li vyloučit všechny vlastnosti jen pro čtení, <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> nastavte `true`na, jak je znázorněno v následujícím příkladu:

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

Tato možnost se vztahuje pouze na serializaci. Během deserializace jsou vlastnosti jen pro čtení ve výchozím nastavení ignorovány. Vlastnost je jen pro čtení, pokud obsahuje veřejnou metodu getter, ale ne veřejnou metodu setter.

### <a name="exclude-all-null-value-properties"></a>Vyloučit všechny vlastnosti hodnoty null

Chcete-li vyloučit všechny vlastnosti hodnoty null, <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> nastavte vlastnost `true`na hodnotu, jak je znázorněno v následujícím příkladu:

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Zde je příklad objektu pro serializaci a výstup JSON:

|Vlastnost |Value  |
|---------|---------|
| Datum    | 8/1/2019 12:00:00 DOP. 07:00|
| TemperatureC| 25 |
| Souhrn| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

Toto nastavení platí pro serializaci a deserializaci. Během deserializace jsou hodnoty null ve formátu JSON ignorovány pouze v případě, že jsou platné. Hodnoty null pro typy hodnot, které neumožňují hodnotu null, způsobují výjimky. Další informace najdete v tématu [problém s typy hodnot, které](https://github.com/dotnet/corefx/issues/40922) neumožňují hodnotu null v úložišti dotnet/Corefx na GitHubu.

## <a name="case-insensitive-property-matching"></a>Porovnávání vlastností bez rozlišení velkých a malých písmen

Ve výchozím nastavení deserializace hledá název vlastnosti rozlišující velká a malá písmena mezi vlastnostmi JSON a cílovým objektem. Chcete-li toto chování změnit, <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> nastavte `true`na:

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

## <a name="include-properties-of-derived-classes"></a>Zahrnout vlastnosti odvozených tříd

Polymorfní serializace není podporována, pokud zadáte v době kompilace typ, který se má serializovat. Předpokládejme například, že máte `WeatherForecast` třídu a odvozenou třídu: `WeatherForecastWithWind`

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

A Předpokládejme, že typ předaný do nebo odvozený `Serialize` je metoda v `WeatherForecast`době kompilace:

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

V tomto scénáři není `WindSpeed` Vlastnost serializována i v `weatherForecast` případě, že objekt je ve skutečnosti `WeatherForecastWithWind` objekt. Serializovat se budou jenom vlastnosti základní třídy:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

Toto chování je určeno k tomu, aby se zabránilo náhodnému úniku dat v odvozeném typu vytvořeném modulem runtime.

Chcete-li serializovat vlastnosti odvozeného typu, použijte jeden z následujících přístupů:

* Zavolejte přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A> , které umožňuje určit typ za běhu:

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* Deklarujte objekt, který se má `object`serializovat jako.

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

V předchozím ukázkovém scénáři oba přístupy způsobí, že `WindSpeed` vlastnost bude obsažena ve výstupu JSON:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
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

Pokud deserializaci kódu JSON zobrazeného na zobrazeném typu, `DatesAvailable` vlastnosti `SummaryWords` a se nikde k přechodu a jsou ztraceny. Chcete-li zachytit další data, jako jsou tyto vlastnosti, použijte atribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) na vlastnost typu `Dictionary<string,object>` nebo `Dictionary<string,JsonElement>`:

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

Při deserializaci formátu JSON zobrazeného dříve do tohoto ukázkového typu se data dalších dat stávají páry `ExtensionData` klíč-hodnota vlastnosti:

|Vlastnost |Value  |Poznámky  |
|---------|---------|---------|
| Datum    | 8/1/2019 12:00:00 DOP. 07:00||
| TemperatureC| 0 | Neshoda malých a velkých`temperatureC` písmen (ve formátu JSON), takže vlastnost není nastavena. |
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

Všimněte si, `ExtensionData` že název vlastnosti se ve formátu JSON nezobrazuje. Díky tomuto chování může JSON vytvořit zpáteční cestu, aniž by došlo ke ztrátě dalších dat, která by jinak nebyla deserializována.

## <a name="use-utf8jsonwriter-directly"></a>Použití Utf8JsonWriter přímo

Následující příklad ukazuje, jak použít <xref:System.Text.Json.Utf8JsonWriter> třídu přímo.

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

## <a name="use-utf8jsonreader-directly"></a>Použití Utf8JsonReader přímo

Následující příklad ukazuje, jak použít <xref:System.Text.Json.Utf8JsonReader> třídu přímo. Kód předpokládá, že `jsonUtf8` proměnná je bajtové pole, které obsahuje platný kód JSON kódovaný jako UTF-8.

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

## <a name="additional-resources"></a>Další zdroje

* [Přehled System. text. JSON](system-text-json-overview.md)
* [Reference k rozhraní API System. text. JSON](xref:System.Text.Json)
* [Podpora DateTime a DateTimeOffset v System. text. JSON](../datetime/system-text-json-support.md)
