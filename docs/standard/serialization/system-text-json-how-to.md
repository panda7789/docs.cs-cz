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
ms.openlocfilehash: 3c988a0151f57b67db19f41aeb88c6fb9b808cb3
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179204"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a><span data-ttu-id="ca7b6-102">Postup serializace a deserializace JSON v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="ca7b6-102">How to serialize and deserialize JSON in .NET</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ca7b6-103">Dokumentace serializace JSON je vytvářena.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-103">The JSON serialization documentation is under construction.</span></span> <span data-ttu-id="ca7b6-104">Tento článek se nezabývá všemi scénáři.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-104">This article doesn't cover all scenarios.</span></span> <span data-ttu-id="ca7b6-105">Další informace najdete v části [System. text. JSON – problémy](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) v úložišti dotnet/Corefx na GitHubu, zejména ty, které jsou označené jako [JSON-funkce-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span><span class="sxs-lookup"><span data-stu-id="ca7b6-105">For more information, examine [System.Text.Json issues](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) in the dotnet/corefx repository on GitHub, especially those labeled [json-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span></span>

<span data-ttu-id="ca7b6-106">Tento článek ukazuje, jak použít obor názvů <xref:System.Text.Json> k serializaci a deserializaci do a z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="ca7b6-106">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="ca7b6-107">Pokyny a vzorový kód používají knihovnu přímo, nikoli prostřednictvím rozhraní, jako je například [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="ca7b6-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

## <a name="namespaces"></a><span data-ttu-id="ca7b6-108">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="ca7b6-108">Namespaces</span></span>

<span data-ttu-id="ca7b6-109">Obor názvů <xref:System.Text.Json> obsahuje všechny vstupní body a hlavní typy.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-109">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="ca7b6-110">Obor názvů <xref:System.Text.Json.Serialization> obsahuje atributy a rozhraní API pro pokročilé scénáře a přizpůsobení specifické pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-110">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="ca7b6-111">Proto příklady kódu, které jsou uvedeny v tomto článku, vyžadují jednu nebo obě následující direktivy `using`:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-111">Therefore, the code examples shown in this article require one or both of the following `using` directives:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="ca7b6-112">Atributy z oboru názvů <xref:System.Runtime.Serialization> nejsou v současné době podporovány v `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-112">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="ca7b6-113">Zápis objektů .NET do formátu JSON (serializace)</span><span class="sxs-lookup"><span data-stu-id="ca7b6-113">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="ca7b6-114">Chcete-li zapsat JSON do řetězce, zavolejte metodu <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-114">To write JSON to a string, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ca7b6-115">Následující příklad používá přetížení s parametrem obecného typu:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-115">The following example uses an overload with a generic type parameter:</span></span>

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="ca7b6-116">Můžete vynechat parametr obecného typu a místo toho použít odvození obecného typu:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-116">You can omit the generic type parameter and use generic type inference instead:</span></span>

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="ca7b6-117">Zde je příklad typu k serializaci, který obsahuje kolekce a vnořené třídy:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-117">Here's an example type to be serialized, which contains collections and nested classes:</span></span>

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

<span data-ttu-id="ca7b6-118">Výstup JSON je ve výchozím nastavení minifikovaného:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-118">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="ca7b6-119">Následující příklad ukazuje stejný formát JSON (to znamená, že je poměrně vytištěn s prázdným znakem a odsazením):</span><span class="sxs-lookup"><span data-stu-id="ca7b6-119">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

<span data-ttu-id="ca7b6-120">Přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A> vám umožní serializovat na <xref:System.IO.Stream>.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-120">Overloads of <xref:System.Text.Json.JsonSerializer.Serialize%2A> let you serialize to a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="ca7b6-121">Jsou k dispozici asynchronní verze `Stream` přetížení.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-121">Async versions of the `Stream` overloads are available.</span></span>

### <a name="serialize-to-utf-8"></a><span data-ttu-id="ca7b6-122">Serializovat do UTF-8</span><span class="sxs-lookup"><span data-stu-id="ca7b6-122">Serialize to UTF-8</span></span>

<span data-ttu-id="ca7b6-123">Pro serializaci do UTF-8 volejte metodu <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-123">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="ca7b6-124">Alternativně je k dispozici přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A>, které přijímá <xref:System.Text.Json.Utf8JsonWriter>.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-124">As an alternative, a <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is available.</span></span>

<span data-ttu-id="ca7b6-125">Serializace do UTF-8 je přibližně 5-10% rychlejší než použití metod založených na řetězci.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-125">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="ca7b6-126">Rozdíl je z důvodu, že bajty (jako UTF-8) není nutné převést na řetězce (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="ca7b6-126">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="ca7b6-127">Chování serializace</span><span class="sxs-lookup"><span data-stu-id="ca7b6-127">Serialization behavior</span></span>

* <span data-ttu-id="ca7b6-128">Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-128">By default, all public properties are serialized.</span></span> <span data-ttu-id="ca7b6-129">Můžete [určit vlastnosti, které se mají vyloučit](#exclude-properties).</span><span class="sxs-lookup"><span data-stu-id="ca7b6-129">You can [specify properties to exclude](#exclude-properties).</span></span>
* <span data-ttu-id="ca7b6-130">[Výchozí kodér](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) řídí znaky jiné než ASCII, znaky citlivé na jazyk HTML v rozsahu ASCII a znaky, které musí být uvozeny podle [specifikace JSON](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="ca7b6-130">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="ca7b6-131">Ve výchozím nastavení je JSON minifikovaného.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-131">By default, JSON is minified.</span></span> <span data-ttu-id="ca7b6-132">[Kód JSON můžete v podstatě vytisknout](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="ca7b6-132">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="ca7b6-133">Ve výchozím nastavení jsou malá a velká písmena názvů JSON shodná s názvy .NET.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-133">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="ca7b6-134">Můžete [přizpůsobit název a velikost písmen JSON](#customize-json-names).</span><span class="sxs-lookup"><span data-stu-id="ca7b6-134">You can [customize JSON name casing](#customize-json-names).</span></span>
* <span data-ttu-id="ca7b6-135">Byly zjištěny cyklické odkazy a byly vyvolány výjimky.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-135">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="ca7b6-136">Další informace najdete v tématu [problém u cyklických odkazů](https://github.com/dotnet/corefx/issues/38579) v úložišti dotnet/Corefx na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-136">For more information, see the [issue on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="ca7b6-137">V současné době jsou pole vyloučena.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-137">Currently, fields are excluded.</span></span>

<span data-ttu-id="ca7b6-138">Mezi podporované typy patří:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-138">Supported types include:</span></span>

* <span data-ttu-id="ca7b6-139">Primitivní prvky .NET, které se mapují na primitivní prvky JavaScriptu, jako jsou číselné typy, řetězce a logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-139">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="ca7b6-140">Uživatelsky definované [prosté staré objekty CLR (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="ca7b6-140">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="ca7b6-141">Jednorozměrné a vícenásobná pole (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="ca7b6-141">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="ca7b6-142">`Dictionary<string,TValue>`, kde `TValue` je `object`, `JsonElement` nebo POCO.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-142">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="ca7b6-143">Kolekce z následujících oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-143">Collections from the following namespaces.</span></span> <span data-ttu-id="ca7b6-144">Další informace najdete v tématu věnovaném [problému s podporou shromažďování](https://github.com/dotnet/corefx/issues/36643) v úložišti dotnet/Corefx na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-144">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="ca7b6-145">Postup čtení formátu JSON do objektů .NET (deserializace)</span><span class="sxs-lookup"><span data-stu-id="ca7b6-145">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="ca7b6-146">Chcete-li provést deserializaci z řetězce, zavolejte metodu <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-146">To deserialize from a string, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method, as shown in the following example:</span></span>

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="ca7b6-147">Příklad naleznete v části [serializovat](#how-to-write-net-objects-to-json-serialize) .</span><span class="sxs-lookup"><span data-stu-id="ca7b6-147">For an example, see the [serialize](#how-to-write-net-objects-to-json-serialize) section.</span></span> <span data-ttu-id="ca7b6-148">Objekt JSON a objekt .NET jsou stejné, ale směr je obrácený.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-148">The JSON and .NET object are the same, but the direction is reversed.</span></span>

<span data-ttu-id="ca7b6-149">Přetížení <xref:System.Text.Json.JsonSerializer.Deserialize*> umožňuje deserializaci z `Stream`.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-149">Overloads of <xref:System.Text.Json.JsonSerializer.Deserialize*> let you deserialize from a `Stream`.</span></span>  <span data-ttu-id="ca7b6-150">Jsou k dispozici asynchronní verze `Stream` přetížení.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-150">Async versions of the `Stream` overloads are available.</span></span>

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="ca7b6-151">Deserializace ze znakové sady UTF-8</span><span class="sxs-lookup"><span data-stu-id="ca7b6-151">Deserialize from UTF-8</span></span>

<span data-ttu-id="ca7b6-152">Chcete-li provést deserializaci ze znakové sady UTF-8, zavolejte přetížení <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>, které přebírá `Utf8JsonReader` nebo `ReadOnlySpan<byte>`, jak je znázorněno v následujících příkladech:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-152">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples:</span></span>

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

## <a name="deserialization-behavior"></a><span data-ttu-id="ca7b6-153">Chování deserializace</span><span class="sxs-lookup"><span data-stu-id="ca7b6-153">Deserialization behavior</span></span>

* <span data-ttu-id="ca7b6-154">Ve výchozím nastavení se při porovnávání názvů vlastností rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-154">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="ca7b6-155">Můžete [zadat nerozlišování velkých a malých písmen](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="ca7b6-155">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="ca7b6-156">Pokud JSON obsahuje hodnotu vlastnosti jen pro čtení, hodnota je ignorována a není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-156">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="ca7b6-157">Deserializace na odkazové typy bez bezparametrového konstruktoru není podporována.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-157">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="ca7b6-158">Deserializace u neměnných objektů nebo vlastností jen pro čtení není podporována.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-158">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="ca7b6-159">Další informace najdete v tématu věnovaném problému na GitHubu [s neproměnlivou podporou objektů](https://github.com/dotnet/corefx/issues/38569) a [problému s podporou vlastnosti jen pro čtení](https://github.com/dotnet/corefx/issues/38163) v úložišti dotnet/corefx na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-159">For more information, see the GitHub [issue on immutable object support](https://github.com/dotnet/corefx/issues/38569) and the [issue on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="ca7b6-160">Ve výchozím nastavení jsou výčty podporovány jako čísla.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-160">By default, enums are supported as numbers.</span></span>
* <span data-ttu-id="ca7b6-161">Pole nejsou podporována.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-161">Fields aren't supported.</span></span>
* <span data-ttu-id="ca7b6-162">Ve výchozím nastavení komentáře nebo koncové čárky ve formátu JSON vyvolají výjimky.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-162">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="ca7b6-163">V případě potřeby můžete v případě potřeby [povolovat komentáře a koncové čárky](#allow-comments-and-trailing-commas) .</span><span class="sxs-lookup"><span data-stu-id="ca7b6-163">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas) if needed.</span></span>
* <span data-ttu-id="ca7b6-164">[Výchozí maximální hloubka](xref:System.Text.Json.JsonReaderOptions.MaxDepth) je 64.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-164">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="ca7b6-165">Serializovat do formátovaného formátu JSON</span><span class="sxs-lookup"><span data-stu-id="ca7b6-165">Serialize to formatted JSON</span></span>

<span data-ttu-id="ca7b6-166">Chcete-li, aby výstup JSON byl poměrně vytištěn, nastavte <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> na `true`:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-166">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="ca7b6-167">Zde je příklad typu pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-167">Here's an example type to be serialized and JSON output:</span></span>

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

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="ca7b6-168">Povolí komentáře a koncové čárky.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-168">Allow comments and trailing commas</span></span>

<span data-ttu-id="ca7b6-169">Výchozí komentáře a koncové čárky nejsou ve formátu JSON povoleny.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-169">By default comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="ca7b6-170">Chcete-li ve formátu JSON dovolit komentáře, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> na hodnotu `JsonCommentHandling.Skip`.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-170">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span> <span data-ttu-id="ca7b6-171">A pokud chcete koncovým čárkám povolený, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-171">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="ca7b6-172">Následující příklad ukazuje, jak je možné:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-172">The following example shows how to allow both:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="ca7b6-173">Tady je příklad JSON s komentáři a koncovou čárkou:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-173">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="customize-json-names"></a><span data-ttu-id="ca7b6-174">Přizpůsobení názvů JSON</span><span class="sxs-lookup"><span data-stu-id="ca7b6-174">Customize JSON names</span></span>

<span data-ttu-id="ca7b6-175">Ve výchozím nastavení se názvy vlastností a klíče slovníku ve výstupu JSON nezměnily, včetně případu.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-175">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="ca7b6-176">V této části se dozvíte, jak:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-176">This section explains how to:</span></span>

* <span data-ttu-id="ca7b6-177">Přizpůsobení jednotlivých názvů vlastností</span><span class="sxs-lookup"><span data-stu-id="ca7b6-177">Customize individual property names</span></span>
* <span data-ttu-id="ca7b6-178">Převést názvy všech vlastností na velikost ve stylu CamelCase</span><span class="sxs-lookup"><span data-stu-id="ca7b6-178">Convert all property names to camel case</span></span>
* <span data-ttu-id="ca7b6-179">Implementace vlastní zásady pro pojmenovávání vlastností</span><span class="sxs-lookup"><span data-stu-id="ca7b6-179">Implement a custom property naming policy</span></span>
* <span data-ttu-id="ca7b6-180">Převede klíče slovníku na ve stylu CamelCase případ.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-180">Convert dictionary keys to camel case</span></span>

<span data-ttu-id="ca7b6-181">V současné době neexistuje žádná podpora pro automatické převádění výčtů na ve stylu CamelCase případ.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-181">Currently, there's no support for automatically converting enums to camel case.</span></span> <span data-ttu-id="ca7b6-182">Další informace najdete v tématu [problém ve stylu CamelCase enum – podpora případu](https://github.com/dotnet/corefx/issues/37725) v úložišti dotnet/Corefx na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-182">For more information, see the [issue on enum camel case support](https://github.com/dotnet/corefx/issues/37725) in the dotnet/corefx repository on GitHub.</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="ca7b6-183">Přizpůsobení jednotlivých názvů vlastností</span><span class="sxs-lookup"><span data-stu-id="ca7b6-183">Customize individual property names</span></span>

<span data-ttu-id="ca7b6-184">Chcete-li nastavit název jednotlivých vlastností, použijte atribut [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="ca7b6-184">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="ca7b6-185">Tady je příklad typu k serializaci a výslednému formátu JSON:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-185">Here's an example type to serialize and resulting JSON:</span></span>

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

<span data-ttu-id="ca7b6-186">Název vlastnosti nastavený tímto atributem:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-186">The property name set by this attribute:</span></span>

* <span data-ttu-id="ca7b6-187">Platí v obou směrech pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-187">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="ca7b6-188">Má přednost před zásadami pro pojmenovávání vlastností.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-188">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="ca7b6-189">Pro všechny názvy vlastností JSON použijte ve stylu CamelCase Case</span><span class="sxs-lookup"><span data-stu-id="ca7b6-189">Use camel case for all JSON property names</span></span>

<span data-ttu-id="ca7b6-190">Pro použití ve stylu CamelCase pro všechny názvy vlastností JSON nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na `JsonNamingPolicy.CamelCase`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-190">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="ca7b6-191">Tady je příklad třídy pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-191">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="ca7b6-192">Zásada pro pojmenování vlastností případu ve stylu CamelCase:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-192">The camel case property naming policy:</span></span>

* <span data-ttu-id="ca7b6-193">Platí pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-193">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="ca7b6-194">Je přepsán pomocí atributů `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-194">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="ca7b6-195">Použít vlastní zásady pojmenování vlastností JSON</span><span class="sxs-lookup"><span data-stu-id="ca7b6-195">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="ca7b6-196">Chcete-li použít vlastní zásadu pojmenovávání vlastností JSON, vytvořte třídu, která je odvozena z <xref:System.Text.Json.JsonNamingPolicy> a přepište metodu <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-196">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

<span data-ttu-id="ca7b6-197">Pak nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na instanci třídy zásad pojmenování:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-197">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="ca7b6-198">Tady je příklad třídy pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-198">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="ca7b6-199">Zásady pojmenování vlastností JSON:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-199">The JSON property naming policy:</span></span>

* <span data-ttu-id="ca7b6-200">Platí pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-200">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="ca7b6-201">Je přepsán pomocí atributů `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-201">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="ca7b6-202">Klíče slovníku případů ve stylu CamelCase</span><span class="sxs-lookup"><span data-stu-id="ca7b6-202">Camel case dictionary keys</span></span>

<span data-ttu-id="ca7b6-203">Pokud je vlastnost objektu, která má být serializována, typu `Dictionary<string,TValue>`, klíče `string` lze převést na ve stylu CamelCase případ.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-203">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="ca7b6-204">To provedete tak, že nastavíte <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> na `JsonNamingPolicy.CamelCase`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-204">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="ca7b6-205">Zde je příklad objektu pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-205">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="ca7b6-206">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ca7b6-206">Property</span></span> |<span data-ttu-id="ca7b6-207">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ca7b6-207">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="ca7b6-208">Datum</span><span class="sxs-lookup"><span data-stu-id="ca7b6-208">Date</span></span>    | <span data-ttu-id="ca7b6-209">8/1/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="ca7b6-209">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="ca7b6-210">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="ca7b6-210">TemperatureC</span></span>| <span data-ttu-id="ca7b6-211">0,25</span><span class="sxs-lookup"><span data-stu-id="ca7b6-211">25</span></span> |
| <span data-ttu-id="ca7b6-212">Souhrn</span><span class="sxs-lookup"><span data-stu-id="ca7b6-212">Summary</span></span>| <span data-ttu-id="ca7b6-213">Provozu</span><span class="sxs-lookup"><span data-stu-id="ca7b6-213">Hot</span></span>|
| <span data-ttu-id="ca7b6-214">TemperatureRanges</span><span class="sxs-lookup"><span data-stu-id="ca7b6-214">TemperatureRanges</span></span> | <span data-ttu-id="ca7b6-215">Studená, 20</span><span class="sxs-lookup"><span data-stu-id="ca7b6-215">Cold, 20</span></span><br><span data-ttu-id="ca7b6-216">Horká, 40</span><span class="sxs-lookup"><span data-stu-id="ca7b6-216">Hot, 40</span></span>|

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

<span data-ttu-id="ca7b6-217">Zásady pro pojmenování případů ve stylu CamelCase se vztahují pouze na serializaci.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-217">The camel case naming policy applies to serialization only.</span></span>

## <a name="exclude-properties"></a><span data-ttu-id="ca7b6-218">Vlastnosti vyloučení</span><span class="sxs-lookup"><span data-stu-id="ca7b6-218">Exclude properties</span></span>

<span data-ttu-id="ca7b6-219">Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-219">By default, all public properties are serialized.</span></span> <span data-ttu-id="ca7b6-220">Pokud nechcete, aby se některé z nich zobrazovaly ve výstupu JSON, máte několik možností.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-220">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="ca7b6-221">V této části se dozvíte, jak vyloučit:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-221">This section explains how to exclude:</span></span>

* <span data-ttu-id="ca7b6-222">Jednotlivé vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ca7b6-222">Individual properties</span></span>
* <span data-ttu-id="ca7b6-223">Všechny vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ca7b6-223">All read-only properties</span></span>
* <span data-ttu-id="ca7b6-224">Všechny vlastnosti s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="ca7b6-224">All null-value properties</span></span> 

### <a name="exclude-individual-properties"></a><span data-ttu-id="ca7b6-225">Vyloučení individuálních vlastností</span><span class="sxs-lookup"><span data-stu-id="ca7b6-225">Exclude individual properties</span></span>

<span data-ttu-id="ca7b6-226">Chcete-li ignorovat jednotlivé vlastnosti, použijte atribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="ca7b6-226">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="ca7b6-227">Tady je příklad typu pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-227">Here's an example type to serialize and JSON output:</span></span>

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

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="ca7b6-228">Vyloučit všechny vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ca7b6-228">Exclude all read-only properties</span></span>

<span data-ttu-id="ca7b6-229">Chcete-li vyloučit všechny vlastnosti jen pro čtení, nastavte <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> na `true`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-229">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="ca7b6-230">Tady je příklad typu pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-230">Here's an example type to serialize and JSON output:</span></span>

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

<span data-ttu-id="ca7b6-231">Tato možnost se vztahuje pouze na serializaci.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-231">This option applies only to serialization.</span></span> <span data-ttu-id="ca7b6-232">Během deserializace jsou vlastnosti jen pro čtení ve výchozím nastavení ignorovány.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-232">During deserialization, read-only properties are ignored by default.</span></span> <span data-ttu-id="ca7b6-233">Vlastnost je jen pro čtení, pokud obsahuje veřejnou metodu getter, ale ne veřejnou metodu setter.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-233">A property is read-only if it contains a public getter but not a public setter.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="ca7b6-234">Vyloučit všechny vlastnosti hodnoty null</span><span class="sxs-lookup"><span data-stu-id="ca7b6-234">Exclude all null value properties</span></span>

<span data-ttu-id="ca7b6-235">Chcete-li vyloučit všechny vlastnosti hodnoty null, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> na hodnotu `true`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-235">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="ca7b6-236">Zde je příklad objektu pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-236">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="ca7b6-237">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ca7b6-237">Property</span></span> |<span data-ttu-id="ca7b6-238">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ca7b6-238">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="ca7b6-239">Datum</span><span class="sxs-lookup"><span data-stu-id="ca7b6-239">Date</span></span>    | <span data-ttu-id="ca7b6-240">8/1/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="ca7b6-240">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="ca7b6-241">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="ca7b6-241">TemperatureC</span></span>| <span data-ttu-id="ca7b6-242">0,25</span><span class="sxs-lookup"><span data-stu-id="ca7b6-242">25</span></span> |
| <span data-ttu-id="ca7b6-243">Souhrn</span><span class="sxs-lookup"><span data-stu-id="ca7b6-243">Summary</span></span>| <span data-ttu-id="ca7b6-244">null</span><span class="sxs-lookup"><span data-stu-id="ca7b6-244">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

<span data-ttu-id="ca7b6-245">Toto nastavení platí pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-245">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="ca7b6-246">Během deserializace jsou hodnoty null ve formátu JSON ignorovány pouze v případě, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-246">During deserialization, null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="ca7b6-247">Hodnoty null pro typy hodnot, které neumožňují hodnotu null, způsobují výjimky.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-247">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="ca7b6-248">Další informace najdete v tématu [problém s typy hodnot, které](https://github.com/dotnet/corefx/issues/40922) neumožňují hodnotu null v úložišti dotnet/Corefx na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-248">For more information, see the [issue on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="ca7b6-249">Porovnávání vlastností bez rozlišení velkých a malých písmen</span><span class="sxs-lookup"><span data-stu-id="ca7b6-249">Case-insensitive property matching</span></span>

<span data-ttu-id="ca7b6-250">Ve výchozím nastavení deserializace hledá název vlastnosti rozlišující velká a malá písmena mezi vlastnostmi JSON a cílovým objektem.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-250">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="ca7b6-251">Chcete-li toto chování změnit, nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> na `true`:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-251">To change that behavior, set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

<span data-ttu-id="ca7b6-252">Tady je příklad JSON s názvy vlastností Case ve stylu CamelCase.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-252">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="ca7b6-253">Lze deserializovat do následujícího typu, který má názvy vlastností Case typu Pascal.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-253">It can be deserialized into the following type that has Pascal case property names.</span></span>

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

## <a name="include-properties-of-derived-classes"></a><span data-ttu-id="ca7b6-254">Zahrnout vlastnosti odvozených tříd</span><span class="sxs-lookup"><span data-stu-id="ca7b6-254">Include properties of derived classes</span></span>

<span data-ttu-id="ca7b6-255">Polymorfní serializace není podporována, pokud zadáte v době kompilace typ, který se má serializovat.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-255">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="ca7b6-256">Předpokládejme například, že máte třídu `WeatherForecast` a odvozenou třídu `WeatherForecastWithWind`:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-256">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

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

<span data-ttu-id="ca7b6-257">A Předpokládejme, že typ předaný do nebo odvozený je metoda `Serialize` v době kompilace `WeatherForecast`:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-257">And suppose the type passed to, or inferred by, the `Serialize` method at compile time is `WeatherForecast`:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="ca7b6-258">V tomto scénáři není vlastnost `WindSpeed` serializována, i když je objekt `weatherForecast` ve skutečnosti objekt `WeatherForecastWithWind`.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-258">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="ca7b6-259">Serializovat se budou jenom vlastnosti základní třídy:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-259">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="ca7b6-260">Toto chování je určeno k tomu, aby se zabránilo náhodnému úniku dat v odvozeném typu vytvořeném modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-260">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="ca7b6-261">Chcete-li serializovat vlastnosti odvozeného typu, použijte jeden z následujících přístupů:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-261">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="ca7b6-262">Zavolejte přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A>, které umožňuje určit typ za běhu:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-262">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* <span data-ttu-id="ca7b6-263">Deklarujte objekt, který se má serializovat jako `object`.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-263">Declare the object to be serialized as `object`.</span></span>

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

<span data-ttu-id="ca7b6-264">V předchozím ukázkovém scénáři oba přístupy způsobí, že se vlastnost `WindSpeed` zahrne do výstupu JSON:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-264">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

## <a name="handle-overflow-json"></a><span data-ttu-id="ca7b6-265">Přetečení JSON popisovače</span><span class="sxs-lookup"><span data-stu-id="ca7b6-265">Handle overflow JSON</span></span>

<span data-ttu-id="ca7b6-266">Při deserializaci můžete přijímat data ve formátu JSON, která nejsou reprezentovaná vlastnostmi cílového typu.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-266">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="ca7b6-267">Předpokládejme například, že váš cílový typ je:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-267">For example, suppose your target type is this:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="ca7b6-268">A JSON, který se má deserializovat, je:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-268">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="ca7b6-269">Pokud deserializaci kódu JSON zobrazeného na zobrazeném typu, vlastnosti `DatesAvailable` a `SummaryWords` mají nikde k přechodu a jsou ztraceny.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-269">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="ca7b6-270">Chcete-li zachytit další data, jako jsou tyto vlastnosti, použijte atribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) na vlastnost typu `Dictionary<string,object>` nebo `Dictionary<string,JsonElement>`:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-270">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

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

<span data-ttu-id="ca7b6-271">Při deserializaci formátu JSON zobrazeného dříve do tohoto ukázkového typu se data dalších dat stávají páry klíč-hodnota vlastnosti `ExtensionData`:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-271">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="ca7b6-272">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="ca7b6-272">Property</span></span> |<span data-ttu-id="ca7b6-273">Hodnota</span><span class="sxs-lookup"><span data-stu-id="ca7b6-273">Value</span></span>  |<span data-ttu-id="ca7b6-274">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ca7b6-274">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="ca7b6-275">Datum</span><span class="sxs-lookup"><span data-stu-id="ca7b6-275">Date</span></span>    | <span data-ttu-id="ca7b6-276">8/1/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="ca7b6-276">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="ca7b6-277">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="ca7b6-277">TemperatureC</span></span>| <span data-ttu-id="ca7b6-278">0,8</span><span class="sxs-lookup"><span data-stu-id="ca7b6-278">0</span></span> | <span data-ttu-id="ca7b6-279">Neshoda malých a velkých písmen (`temperatureC` ve formátu JSON), takže vlastnost není nastavená.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-279">Case-sensitive mismatch (`temperatureC` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="ca7b6-280">Souhrn</span><span class="sxs-lookup"><span data-stu-id="ca7b6-280">Summary</span></span> | <span data-ttu-id="ca7b6-281">Provozu</span><span class="sxs-lookup"><span data-stu-id="ca7b6-281">Hot</span></span> ||
| <span data-ttu-id="ca7b6-282">ExtensionData –</span><span class="sxs-lookup"><span data-stu-id="ca7b6-282">ExtensionData</span></span> | <span data-ttu-id="ca7b6-283">temperatureC: 25</span><span class="sxs-lookup"><span data-stu-id="ca7b6-283">temperatureC: 25</span></span> |<span data-ttu-id="ca7b6-284">Vzhledem k tomu, že se neshoduje velká a malá písmena, je tato vlastnost JSON extra a ve slovníku se stala dvojicí klíč-hodnota.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-284">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="ca7b6-285">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-285">DatesAvailable:</span></span><br>  <span data-ttu-id="ca7b6-286">8/1/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="ca7b6-286">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="ca7b6-287">8/2/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="ca7b6-287">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="ca7b6-288">Vlastnost extra z formátu JSON se stávají dvojicí klíč-hodnota s polem jako objektem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-288">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="ca7b6-289">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-289">SummaryWords:</span></span><br><span data-ttu-id="ca7b6-290">Dobré</span><span class="sxs-lookup"><span data-stu-id="ca7b6-290">Cool</span></span><br><span data-ttu-id="ca7b6-291">Vítr</span><span class="sxs-lookup"><span data-stu-id="ca7b6-291">Windy</span></span><br><span data-ttu-id="ca7b6-292">Humid</span><span class="sxs-lookup"><span data-stu-id="ca7b6-292">Humid</span></span> |<span data-ttu-id="ca7b6-293">Vlastnost extra z formátu JSON se stávají dvojicí klíč-hodnota s polem jako objektem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-293">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="ca7b6-294">Při serializaci cílového objektu se dvojice hodnoty klíče dat rozšíření stanou vlastnostmi JSON stejně, jako kdyby byly ve vstupním formátu JSON:</span><span class="sxs-lookup"><span data-stu-id="ca7b6-294">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="ca7b6-295">Všimněte si, že název vlastnosti `ExtensionData` se ve formátu JSON nezobrazuje.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-295">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="ca7b6-296">Díky tomuto chování může JSON vytvořit zpáteční cestu, aniž by došlo ke ztrátě dalších dat, která by jinak nebyla deserializována.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-296">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="use-utf8jsonwriter-directly"></a><span data-ttu-id="ca7b6-297">Použití Utf8JsonWriter přímo</span><span class="sxs-lookup"><span data-stu-id="ca7b6-297">Use Utf8JsonWriter directly</span></span>

<span data-ttu-id="ca7b6-298">Následující příklad ukazuje, jak použít třídu <xref:System.Text.Json.Utf8JsonWriter> přímo.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-298">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class directly.</span></span>

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

## <a name="use-utf8jsonreader-directly"></a><span data-ttu-id="ca7b6-299">Použití Utf8JsonReader přímo</span><span class="sxs-lookup"><span data-stu-id="ca7b6-299">Use Utf8JsonReader directly</span></span>

<span data-ttu-id="ca7b6-300">Následující příklad ukazuje, jak použít třídu <xref:System.Text.Json.Utf8JsonReader> přímo.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-300">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class directly.</span></span> <span data-ttu-id="ca7b6-301">Kód předpokládá, že proměnná `jsonUtf8` je pole bajtů, které obsahuje platný kód JSON kódovaný jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ca7b6-301">The code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="ca7b6-302">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ca7b6-302">Additional resources</span></span>

* [<span data-ttu-id="ca7b6-303">Přehled System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="ca7b6-303">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="ca7b6-304">Reference k rozhraní API System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="ca7b6-304">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="ca7b6-305">Podpora DateTime a DateTimeOffset v System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="ca7b6-305">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
