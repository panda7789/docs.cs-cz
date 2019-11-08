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
# <a name="how-to-serialize-and-deserialize-json-in-net"></a><span data-ttu-id="c1301-102">Postup serializace a deserializace JSON v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="c1301-102">How to serialize and deserialize JSON in .NET</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c1301-103">Dokumentace serializace JSON je vytvářena.</span><span class="sxs-lookup"><span data-stu-id="c1301-103">The JSON serialization documentation is under construction.</span></span> <span data-ttu-id="c1301-104">Tento článek se nezabývá všemi scénáři.</span><span class="sxs-lookup"><span data-stu-id="c1301-104">This article doesn't cover all scenarios.</span></span> <span data-ttu-id="c1301-105">Další informace najdete v části [System. text. JSON – problémy](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) v úložišti dotnet/Corefx na GitHubu, zejména ty, které jsou označené jako [JSON-funkce-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span><span class="sxs-lookup"><span data-stu-id="c1301-105">For more information, examine [System.Text.Json issues](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) in the dotnet/corefx repository on GitHub, especially those labeled [json-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span></span>

<span data-ttu-id="c1301-106">Tento článek ukazuje, jak použít obor názvů <xref:System.Text.Json> k serializaci a deserializaci do a z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="c1301-106">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="c1301-107">Pokyny a vzorový kód používají knihovnu přímo, nikoli prostřednictvím rozhraní, jako je například [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="c1301-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

## <a name="namespaces"></a><span data-ttu-id="c1301-108">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="c1301-108">Namespaces</span></span>

<span data-ttu-id="c1301-109">Obor názvů <xref:System.Text.Json> obsahuje všechny vstupní body a hlavní typy.</span><span class="sxs-lookup"><span data-stu-id="c1301-109">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="c1301-110">Obor názvů <xref:System.Text.Json.Serialization> obsahuje atributy a rozhraní API pro pokročilé scénáře a přizpůsobení specifické pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="c1301-110">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="c1301-111">Příklady kódu, které jsou uvedené v tomto článku, vyžadují direktivy `using` pro jeden nebo oba tyto obory názvů:</span><span class="sxs-lookup"><span data-stu-id="c1301-111">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="c1301-112">Atributy z oboru názvů <xref:System.Runtime.Serialization> nejsou v současné době podporovány v `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="c1301-112">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="c1301-113">Zápis objektů .NET do formátu JSON (serializace)</span><span class="sxs-lookup"><span data-stu-id="c1301-113">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="c1301-114">Chcete-li zapsat JSON do řetězce nebo do souboru, zavolejte metodu <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c1301-114">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c1301-115">Následující příklad vytvoří JSON jako řetězec:</span><span class="sxs-lookup"><span data-stu-id="c1301-115">The following example creates JSON as a string:</span></span>

```csharp
string json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="c1301-116">Následující příklad používá synchronní kód k vytvoření souboru JSON:</span><span class="sxs-lookup"><span data-stu-id="c1301-116">The following example uses synchronous code to create a JSON file:</span></span>

```csharp
File.WriteAllText(outputFileName, JsonSerializer.Serialize(weatherForecast));
```

<span data-ttu-id="c1301-117">Následující příklad používá asynchronní kód k vytvoření souboru JSON:</span><span class="sxs-lookup"><span data-stu-id="c1301-117">The following example uses asynchronous code to create a JSON file:</span></span>

```csharp
using (FileStream fs = File.Create(outputFileName))
{
    await JsonSerializer.SerializeAsync(fs, weatherForecast);
}
```

<span data-ttu-id="c1301-118">Předchozí příklady používají odvození typu pro typ, který je serializován.</span><span class="sxs-lookup"><span data-stu-id="c1301-118">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="c1301-119">Přetížení `Serialize()` přebírá parametr obecného typu:</span><span class="sxs-lookup"><span data-stu-id="c1301-119">An overload of `Serialize()` takes a generic type parameter:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

### <a name="serialization-example"></a><span data-ttu-id="c1301-120">Příklad serializace</span><span class="sxs-lookup"><span data-stu-id="c1301-120">Serialization example</span></span>

<span data-ttu-id="c1301-121">Zde je příklad typu, který obsahuje kolekce a vnořené třídy:</span><span class="sxs-lookup"><span data-stu-id="c1301-121">Here's an example type that contains collections and nested classes:</span></span>

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

<span data-ttu-id="c1301-122">Výstup JSON z serializace instance předchozího typu vypadá jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c1301-122">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="c1301-123">Výstup JSON je ve výchozím nastavení minifikovaného:</span><span class="sxs-lookup"><span data-stu-id="c1301-123">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="c1301-124">Následující příklad ukazuje stejný formát JSON (to znamená, že je poměrně vytištěn s prázdným znakem a odsazením):</span><span class="sxs-lookup"><span data-stu-id="c1301-124">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="c1301-125">Serializovat do UTF-8</span><span class="sxs-lookup"><span data-stu-id="c1301-125">Serialize to UTF-8</span></span>

<span data-ttu-id="c1301-126">Chcete-li serializovat do UTF-8, zavolejte metodu <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="c1301-126">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

```csharp
byte[] jsonUtf8Bytes = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="c1301-127">K dispozici je také přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A>, které přijímá <xref:System.Text.Json.Utf8JsonWriter>.</span><span class="sxs-lookup"><span data-stu-id="c1301-127">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="c1301-128">Serializace do UTF-8 je přibližně 5-10% rychlejší než použití metod založených na řetězci.</span><span class="sxs-lookup"><span data-stu-id="c1301-128">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="c1301-129">Rozdíl je z důvodu, že bajty (jako UTF-8) není nutné převést na řetězce (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="c1301-129">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="c1301-130">Chování serializace</span><span class="sxs-lookup"><span data-stu-id="c1301-130">Serialization behavior</span></span>

* <span data-ttu-id="c1301-131">Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c1301-131">By default, all public properties are serialized.</span></span> <span data-ttu-id="c1301-132">Můžete [určit vlastnosti, které se mají vyloučit](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="c1301-132">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="c1301-133">[Výchozí kodér](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) řídí znaky jiné než ASCII, znaky citlivé na jazyk HTML v rozsahu ASCII a znaky, které musí být uvozeny podle [specifikace JSON](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="c1301-133">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="c1301-134">Ve výchozím nastavení je JSON minifikovaného.</span><span class="sxs-lookup"><span data-stu-id="c1301-134">By default, JSON is minified.</span></span> <span data-ttu-id="c1301-135">[Kód JSON můžete v podstatě vytisknout](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="c1301-135">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="c1301-136">Ve výchozím nastavení jsou malá a velká písmena názvů JSON shodná s názvy .NET.</span><span class="sxs-lookup"><span data-stu-id="c1301-136">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="c1301-137">Můžete [přizpůsobit název a velikost písmen JSON](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="c1301-137">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="c1301-138">Byly zjištěny cyklické odkazy a byly vyvolány výjimky.</span><span class="sxs-lookup"><span data-stu-id="c1301-138">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="c1301-139">Další informace najdete v tématu [problém u cyklických odkazů](https://github.com/dotnet/corefx/issues/38579) v úložišti dotnet/Corefx na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="c1301-139">For more information, see the [issue on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="c1301-140">V současné době jsou pole vyloučena.</span><span class="sxs-lookup"><span data-stu-id="c1301-140">Currently, fields are excluded.</span></span>

<span data-ttu-id="c1301-141">Mezi podporované typy patří:</span><span class="sxs-lookup"><span data-stu-id="c1301-141">Supported types include:</span></span>

* <span data-ttu-id="c1301-142">Primitivní prvky .NET, které se mapují na primitivní prvky JavaScriptu, jako jsou číselné typy, řetězce a logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="c1301-142">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="c1301-143">Uživatelsky definované [prosté staré objekty CLR (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="c1301-143">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="c1301-144">Jednorozměrné a vícenásobná pole (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="c1301-144">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="c1301-145">`Dictionary<string,TValue>`, kde `TValue` je `object`, `JsonElement` nebo POCO.</span><span class="sxs-lookup"><span data-stu-id="c1301-145">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="c1301-146">Kolekce z následujících oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="c1301-146">Collections from the following namespaces.</span></span> <span data-ttu-id="c1301-147">Další informace najdete v tématu věnovaném [problému s podporou shromažďování](https://github.com/dotnet/corefx/issues/36643) v úložišti dotnet/Corefx na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="c1301-147">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="c1301-148">[Vlastní převaděče můžete implementovat](system-text-json-converters-how-to.md) pro zpracování dalších typů nebo poskytování funkcí, které nejsou podporované integrovanými převaděči.</span><span class="sxs-lookup"><span data-stu-id="c1301-148">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="c1301-149">Postup čtení formátu JSON do objektů .NET (deserializace)</span><span class="sxs-lookup"><span data-stu-id="c1301-149">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="c1301-150">Chcete-li provést deserializaci z řetězce nebo souboru, zavolejte metodu <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c1301-150">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="c1301-151">Následující příklad přečte JSON z řetězce:</span><span class="sxs-lookup"><span data-stu-id="c1301-151">The following example reads JSON from a string:</span></span>

```csharp
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

<span data-ttu-id="c1301-152">Chcete-li provést deserializaci ze souboru pomocí synchronního kódu, přečtěte si soubor do řetězce, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c1301-152">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

```csharp
string jsonString = File.ReadAllText(inputFileName);
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

<span data-ttu-id="c1301-153">Chcete-li provést deserializaci ze souboru pomocí asynchronního kódu, zavolejte metodu <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A>:</span><span class="sxs-lookup"><span data-stu-id="c1301-153">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

```csharp
using (FileStream fs = File.OpenRead(inputFileName))
{
    weatherForecast = await JsonSerializer.DeserializeAsync<WeatherForecast>(fs);
}
```

<span data-ttu-id="c1301-154">Vzorový typ a odpovídající JSON najdete v části [příklad serializace](#serialization-example) .</span><span class="sxs-lookup"><span data-stu-id="c1301-154">For an example type and corresponding JSON, see the [Serialization example](#serialization-example) section.</span></span>

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="c1301-155">Deserializace ze znakové sady UTF-8</span><span class="sxs-lookup"><span data-stu-id="c1301-155">Deserialize from UTF-8</span></span>

<span data-ttu-id="c1301-156">Chcete-li provést deserializaci ze znakové sady UTF-8, zavolejte <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> přetížení, které přebírá `Utf8JsonReader` nebo `ReadOnlySpan<byte>`, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="c1301-156">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="c1301-157">V příkladech se předpokládá, že je JSON v bajtovém poli s názvem jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="c1301-157">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

```csharp
var readOnlySpan = new ReadOnlySpan<byte>(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
var utf8Reader = new Utf8JsonReader(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a><span data-ttu-id="c1301-158">Chování deserializace</span><span class="sxs-lookup"><span data-stu-id="c1301-158">Deserialization behavior</span></span>

* <span data-ttu-id="c1301-159">Ve výchozím nastavení se při porovnávání názvů vlastností rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="c1301-159">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="c1301-160">Můžete [zadat nerozlišování velkých a malých písmen](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="c1301-160">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="c1301-161">Pokud JSON obsahuje hodnotu vlastnosti jen pro čtení, hodnota je ignorována a není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="c1301-161">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="c1301-162">Deserializace na odkazové typy bez bezparametrového konstruktoru není podporována.</span><span class="sxs-lookup"><span data-stu-id="c1301-162">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="c1301-163">Deserializace u neměnných objektů nebo vlastností jen pro čtení není podporována.</span><span class="sxs-lookup"><span data-stu-id="c1301-163">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="c1301-164">Další informace najdete v tématu věnovaném problému na GitHubu [s neproměnlivou podporou objektů](https://github.com/dotnet/corefx/issues/38569) a [problému s podporou vlastnosti jen pro čtení](https://github.com/dotnet/corefx/issues/38163) v úložišti dotnet/corefx na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="c1301-164">For more information, see the GitHub [issue on immutable object support](https://github.com/dotnet/corefx/issues/38569) and the [issue on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="c1301-165">Ve výchozím nastavení jsou výčty podporovány jako čísla.</span><span class="sxs-lookup"><span data-stu-id="c1301-165">By default, enums are supported as numbers.</span></span> <span data-ttu-id="c1301-166">[Názvy výčtů můžete serializovat jako řetězce](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="c1301-166">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="c1301-167">Pole nejsou podporována.</span><span class="sxs-lookup"><span data-stu-id="c1301-167">Fields aren't supported.</span></span>
* <span data-ttu-id="c1301-168">Ve výchozím nastavení komentáře nebo koncové čárky ve formátu JSON vyvolají výjimky.</span><span class="sxs-lookup"><span data-stu-id="c1301-168">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="c1301-169">Můžete [povolovat komentáře a koncové čárky](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="c1301-169">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="c1301-170">[Výchozí maximální hloubka](xref:System.Text.Json.JsonReaderOptions.MaxDepth) je 64.</span><span class="sxs-lookup"><span data-stu-id="c1301-170">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="c1301-171">[Vlastní převaděče můžete implementovat](system-text-json-converters-how-to.md) pro poskytování funkcí, které nejsou podporované integrovanými převaděči.</span><span class="sxs-lookup"><span data-stu-id="c1301-171">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="c1301-172">Serializovat do formátovaného formátu JSON</span><span class="sxs-lookup"><span data-stu-id="c1301-172">Serialize to formatted JSON</span></span>

<span data-ttu-id="c1301-173">Chcete-li, aby výstup JSON byl poměrně vytištěn, nastavte <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> na `true`:</span><span class="sxs-lookup"><span data-stu-id="c1301-173">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="c1301-174">Tady je příklad typu pro serializaci a poměrně tištěné výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="c1301-174">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

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

## <a name="customize-json-names-and-values"></a><span data-ttu-id="c1301-175">Přizpůsobení názvů a hodnot JSON</span><span class="sxs-lookup"><span data-stu-id="c1301-175">Customize JSON names and values</span></span>

<span data-ttu-id="c1301-176">Ve výchozím nastavení se názvy vlastností a klíče slovníku ve výstupu JSON nezměnily, včetně případu.</span><span class="sxs-lookup"><span data-stu-id="c1301-176">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="c1301-177">Hodnoty výčtu jsou reprezentovány jako čísla.</span><span class="sxs-lookup"><span data-stu-id="c1301-177">Enum values are represented as numbers.</span></span> <span data-ttu-id="c1301-178">V této části se dozvíte, jak:</span><span class="sxs-lookup"><span data-stu-id="c1301-178">This section explains how to:</span></span>

* <span data-ttu-id="c1301-179">Přizpůsobení jednotlivých názvů vlastností</span><span class="sxs-lookup"><span data-stu-id="c1301-179">Customize individual property names</span></span>
* <span data-ttu-id="c1301-180">Převést názvy všech vlastností na velikost ve stylu CamelCase</span><span class="sxs-lookup"><span data-stu-id="c1301-180">Convert all property names to camel case</span></span>
* <span data-ttu-id="c1301-181">Implementace vlastní zásady pro pojmenovávání vlastností</span><span class="sxs-lookup"><span data-stu-id="c1301-181">Implement a custom property naming policy</span></span>
* <span data-ttu-id="c1301-182">Převede klíče slovníku na ve stylu CamelCase případ.</span><span class="sxs-lookup"><span data-stu-id="c1301-182">Convert dictionary keys to camel case</span></span>
* <span data-ttu-id="c1301-183">Převod výčtů na řetězce a ve stylu CamelCase velikost písmen</span><span class="sxs-lookup"><span data-stu-id="c1301-183">Convert enums to strings and camel case</span></span> 

<span data-ttu-id="c1301-184">Pro jiné scénáře, které vyžadují speciální zpracování názvů a hodnot vlastností JSON, můžete [implementovat vlastní převaděče](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="c1301-184">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="c1301-185">Přizpůsobení jednotlivých názvů vlastností</span><span class="sxs-lookup"><span data-stu-id="c1301-185">Customize individual property names</span></span>

<span data-ttu-id="c1301-186">Chcete-li nastavit název jednotlivých vlastností, použijte atribut [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="c1301-186">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="c1301-187">Tady je příklad typu k serializaci a výslednému formátu JSON:</span><span class="sxs-lookup"><span data-stu-id="c1301-187">Here's an example type to serialize and resulting JSON:</span></span>

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

<span data-ttu-id="c1301-188">Název vlastnosti nastavený tímto atributem:</span><span class="sxs-lookup"><span data-stu-id="c1301-188">The property name set by this attribute:</span></span>

* <span data-ttu-id="c1301-189">Platí v obou směrech pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="c1301-189">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="c1301-190">Má přednost před zásadami pro pojmenovávání vlastností.</span><span class="sxs-lookup"><span data-stu-id="c1301-190">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="c1301-191">Pro všechny názvy vlastností JSON použijte ve stylu CamelCase Case</span><span class="sxs-lookup"><span data-stu-id="c1301-191">Use camel case for all JSON property names</span></span>

<span data-ttu-id="c1301-192">Pro použití ve stylu CamelCase pro všechny názvy vlastností JSON nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na `JsonNamingPolicy.CamelCase`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c1301-192">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="c1301-193">Tady je příklad třídy pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="c1301-193">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="c1301-194">Zásada pro pojmenování vlastností případu ve stylu CamelCase:</span><span class="sxs-lookup"><span data-stu-id="c1301-194">The camel case property naming policy:</span></span>

* <span data-ttu-id="c1301-195">Platí pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="c1301-195">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="c1301-196">Je přepsán `[JsonPropertyName]` atributy.</span><span class="sxs-lookup"><span data-stu-id="c1301-196">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="c1301-197">To je důvod, proč název vlastnosti JSON `Wind` v příkladu není ve stylu CamelCase Case.</span><span class="sxs-lookup"><span data-stu-id="c1301-197">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="c1301-198">Použít vlastní zásady pojmenování vlastností JSON</span><span class="sxs-lookup"><span data-stu-id="c1301-198">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="c1301-199">Chcete-li použít vlastní zásadu pojmenovávání vlastností JSON, vytvořte třídu, která je odvozena z <xref:System.Text.Json.JsonNamingPolicy> a přepište metodu <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c1301-199">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

<span data-ttu-id="c1301-200">Pak nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na instanci třídy zásad pojmenování:</span><span class="sxs-lookup"><span data-stu-id="c1301-200">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="c1301-201">Tady je příklad třídy pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="c1301-201">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="c1301-202">Zásady pojmenování vlastností JSON:</span><span class="sxs-lookup"><span data-stu-id="c1301-202">The JSON property naming policy:</span></span>

* <span data-ttu-id="c1301-203">Platí pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="c1301-203">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="c1301-204">Je přepsán `[JsonPropertyName]` atributy.</span><span class="sxs-lookup"><span data-stu-id="c1301-204">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="c1301-205">Důvodem je, že název vlastnosti JSON `Wind` v příkladu není velká písmena.</span><span class="sxs-lookup"><span data-stu-id="c1301-205">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="c1301-206">Klíče slovníku případů ve stylu CamelCase</span><span class="sxs-lookup"><span data-stu-id="c1301-206">Camel case dictionary keys</span></span>

<span data-ttu-id="c1301-207">Pokud je vlastnost objektu, která má být serializována, typu `Dictionary<string,TValue>`, klíče `string` lze převést na ve stylu CamelCase případ.</span><span class="sxs-lookup"><span data-stu-id="c1301-207">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="c1301-208">To provedete tak, že nastavíte <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> na `JsonNamingPolicy.CamelCase`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c1301-208">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="c1301-209">Serializace objektu se slovníkem s názvem `TemperatureRanges`, který má páry klíč-hodnota `"ColdMinTemp", 20` a `"HotMinTemp", 40` by vedlo jako výstup JSON jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c1301-209">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="c1301-210">Zásady pro pojmenovávání ve stylu CamelCase pro klíče slovníku se vztahují pouze na serializaci.</span><span class="sxs-lookup"><span data-stu-id="c1301-210">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="c1301-211">Pokud deserializaci slovníku, klíče budou odpovídat souboru JSON, i když zadáte `JsonNamingPolicy.CamelCase` pro `DictionaryKeyPolicy`.</span><span class="sxs-lookup"><span data-stu-id="c1301-211">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="c1301-212">Výčty jako řetězce</span><span class="sxs-lookup"><span data-stu-id="c1301-212">Enums as strings</span></span>

<span data-ttu-id="c1301-213">Ve výchozím nastavení jsou výčty serializovány jako čísla.</span><span class="sxs-lookup"><span data-stu-id="c1301-213">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="c1301-214">Chcete-li serializovat názvy výčtu jako řetězce, použijte <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span><span class="sxs-lookup"><span data-stu-id="c1301-214">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="c1301-215">Předpokládejme například, že potřebujete serializovat následující třídu, která má výčet:</span><span class="sxs-lookup"><span data-stu-id="c1301-215">For example, suppose you need to serialize the following class that has an enum:</span></span>

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

<span data-ttu-id="c1301-216">Pokud je souhrn `Hot`, ve výchozím nastavení má serializovaný formát JSON číselnou hodnotu 3:</span><span class="sxs-lookup"><span data-stu-id="c1301-216">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": 3
}
```

<span data-ttu-id="c1301-217">Následující vzorový kód místo toho serializace názvy výčtů a převede je na ve stylu CamelCase případ:</span><span class="sxs-lookup"><span data-stu-id="c1301-217">The following sample code serializes the enum names instead, and converts them to camel case:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
jsonWithEnumsAsStrings = JsonSerializer.Serialize(weatherForecastWithEnum, options);
```

<span data-ttu-id="c1301-218">Výsledný kód JSON vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c1301-218">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="c1301-219">Podpora výčtů jako řetězců platí také pro deserializaci, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c1301-219">The support for enums as strings applies to deserialization also, as shown in the following example:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
weatherForecastWithEnum = JsonSerializer.Deserialize<WeatherForecastWithEnum>(jsonWithEnumsAsStrings, options);
```

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="c1301-220">Vyloučit vlastnosti ze serializace</span><span class="sxs-lookup"><span data-stu-id="c1301-220">Exclude properties from serialization</span></span>

<span data-ttu-id="c1301-221">Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c1301-221">By default, all public properties are serialized.</span></span> <span data-ttu-id="c1301-222">Pokud nechcete, aby se některé z nich zobrazovaly ve výstupu JSON, máte několik možností.</span><span class="sxs-lookup"><span data-stu-id="c1301-222">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="c1301-223">V této části se dozvíte, jak vyloučit:</span><span class="sxs-lookup"><span data-stu-id="c1301-223">This section explains how to exclude:</span></span>

* <span data-ttu-id="c1301-224">Jednotlivé vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c1301-224">Individual properties</span></span>
* <span data-ttu-id="c1301-225">Všechny vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c1301-225">All read-only properties</span></span>
* <span data-ttu-id="c1301-226">Všechny vlastnosti s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="c1301-226">All null-value properties</span></span> 

### <a name="exclude-individual-properties"></a><span data-ttu-id="c1301-227">Vyloučení individuálních vlastností</span><span class="sxs-lookup"><span data-stu-id="c1301-227">Exclude individual properties</span></span>

<span data-ttu-id="c1301-228">Chcete-li ignorovat jednotlivé vlastnosti, použijte atribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="c1301-228">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="c1301-229">Tady je příklad typu pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="c1301-229">Here's an example type to serialize and JSON output:</span></span>

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

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="c1301-230">Vyloučit všechny vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c1301-230">Exclude all read-only properties</span></span>

<span data-ttu-id="c1301-231">Vlastnost je jen pro čtení, pokud obsahuje veřejnou metodu getter, ale ne veřejnou metodu setter.</span><span class="sxs-lookup"><span data-stu-id="c1301-231">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="c1301-232">Chcete-li vyloučit všechny vlastnosti jen pro čtení, nastavte <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> na `true`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c1301-232">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="c1301-233">Tady je příklad typu pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="c1301-233">Here's an example type to serialize and JSON output:</span></span>

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

<span data-ttu-id="c1301-234">Tato možnost se vztahuje pouze na serializaci.</span><span class="sxs-lookup"><span data-stu-id="c1301-234">This option applies only to serialization.</span></span> <span data-ttu-id="c1301-235">Během deserializace jsou vlastnosti jen pro čtení ve výchozím nastavení ignorovány.</span><span class="sxs-lookup"><span data-stu-id="c1301-235">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="c1301-236">Vyloučit všechny vlastnosti hodnoty null</span><span class="sxs-lookup"><span data-stu-id="c1301-236">Exclude all null value properties</span></span>

<span data-ttu-id="c1301-237">Chcete-li vyloučit všechny vlastnosti hodnoty null, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> na hodnotu `true`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c1301-237">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="c1301-238">Zde je příklad objektu pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="c1301-238">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="c1301-239">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c1301-239">Property</span></span> |<span data-ttu-id="c1301-240">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c1301-240">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="c1301-241">Datum</span><span class="sxs-lookup"><span data-stu-id="c1301-241">Date</span></span>    | <span data-ttu-id="c1301-242">8/1/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="c1301-242">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="c1301-243">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="c1301-243">TemperatureC</span></span>| <span data-ttu-id="c1301-244">0,25</span><span class="sxs-lookup"><span data-stu-id="c1301-244">25</span></span> |
| <span data-ttu-id="c1301-245">Souhrn</span><span class="sxs-lookup"><span data-stu-id="c1301-245">Summary</span></span>| <span data-ttu-id="c1301-246">null</span><span class="sxs-lookup"><span data-stu-id="c1301-246">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

<span data-ttu-id="c1301-247">Toto nastavení platí pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="c1301-247">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="c1301-248">Informace o jeho vlivu na deserializaci naleznete v tématu [Ignore null Při deserializaci](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="c1301-248">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="c1301-249">Přizpůsobení kódování znaků</span><span class="sxs-lookup"><span data-stu-id="c1301-249">Customize character encoding</span></span>

<span data-ttu-id="c1301-250">Ve výchozím nastavení serializátor řídí všechny znaky jiné než ASCII.</span><span class="sxs-lookup"><span data-stu-id="c1301-250">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="c1301-251">To znamená, že je nahradí je `\uxxxx`, kde `xxxxx` je kód Unicode znaku.</span><span class="sxs-lookup"><span data-stu-id="c1301-251">That is, it replaces them with `\uxxxx` where `xxxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="c1301-252">Například pokud je vlastnost `Summary` nastavena na жаркоa v cyrilici, `WeatherForecast` objekt je serializován, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c1301-252">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="c1301-253">Serializovat znakové sady jazyků</span><span class="sxs-lookup"><span data-stu-id="c1301-253">Serialize language character sets</span></span>

<span data-ttu-id="c1301-254">Chcete-li serializovat znakové sady jednoho nebo více jazyků, zadejte [rozsahy Unicode](xref:System.Text.Unicode.UnicodeRanges) při vytváření instance <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c1301-254">To serialize the character set(s) of one or more languages, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

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

<span data-ttu-id="c1301-255">Tento kód serializovat cyrilici a řecké znaky.</span><span class="sxs-lookup"><span data-stu-id="c1301-255">This code serializes Cyrillic and Greek characters.</span></span> <span data-ttu-id="c1301-256">V následujícím příkladu jsou uvedeny znaky cyriliceu:</span><span class="sxs-lookup"><span data-stu-id="c1301-256">Cyrillic characters are shown in the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жарко",
}
```

<span data-ttu-id="c1301-257">Chcete-li určit všechny jazyky, použijte <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c1301-257">To specify all languages, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="c1301-258">Serializovat konkrétní znaky</span><span class="sxs-lookup"><span data-stu-id="c1301-258">Serialize specific characters</span></span>

<span data-ttu-id="c1301-259">Alternativou je zadání jednotlivých znaků, které chcete použít, bez nutnosti řídicích znaků.</span><span class="sxs-lookup"><span data-stu-id="c1301-259">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="c1301-260">Následující příklad serializace pouze prvních dvou znaků жарко:</span><span class="sxs-lookup"><span data-stu-id="c1301-260">The following example serializes only the first two characters of жарко:</span></span>

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

<span data-ttu-id="c1301-261">Zde je příklad kódu JSON vytvořeného předchozím kódem:</span><span class="sxs-lookup"><span data-stu-id="c1301-261">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="c1301-262">Serializovat všechny znaky</span><span class="sxs-lookup"><span data-stu-id="c1301-262">Serialize all characters</span></span>

<span data-ttu-id="c1301-263">Chcete-li minimalizovat uvozovací znaky, můžete použít <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c1301-263">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

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
> <span data-ttu-id="c1301-264">Na rozdíl od výchozího kodéru `UnsafeRelaxedJsonEscaping` kodér:</span><span class="sxs-lookup"><span data-stu-id="c1301-264">Unlike the default encoder, the `UnsafeRelaxedJsonEscaping` encoder:</span></span>
>
> * <span data-ttu-id="c1301-265">Neřídí znaky citlivé na HTML, například `<`, `>`, `&`a `'`.</span><span class="sxs-lookup"><span data-stu-id="c1301-265">Doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="c1301-266">Nenabízí žádné další ochrany proti důkladné ochraně před útoky XSS nebo informací, jako jsou ty, které by mohly vést k tomu *, že klient*a server nesouhlasí.</span><span class="sxs-lookup"><span data-stu-id="c1301-266">Doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
> * <span data-ttu-id="c1301-267">Je přísnější než výchozí kodér, na kterém jsou povoleny znaky bez řídicích znaků.</span><span class="sxs-lookup"><span data-stu-id="c1301-267">Is more permissive than the default encoder on which characters are allowed to pass through unescaped.</span></span>
>
> <span data-ttu-id="c1301-268">Nezabezpečený kodér používejte pouze v případě, že je známo, že klient bude interpretovat výslednou datovou část jako JSON kódovaný v kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c1301-268">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="c1301-269">Můžete ji například použít, pokud server odesílá hlavičku odpovědi `Content-Type: application/json; charset=utf-8`.</span><span class="sxs-lookup"><span data-stu-id="c1301-269">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="c1301-270">Nikdy nepovolujte výstup nezpracovaného `UnsafeRelaxedJsonEscaping` do stránky HTML nebo elementu `<script>`.</span><span class="sxs-lookup"><span data-stu-id="c1301-270">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="c1301-271">Serializovat vlastnosti odvozených tříd</span><span class="sxs-lookup"><span data-stu-id="c1301-271">Serialize properties of derived classes</span></span>

<span data-ttu-id="c1301-272">Polymorfní serializace není podporována, pokud zadáte v době kompilace typ, který se má serializovat.</span><span class="sxs-lookup"><span data-stu-id="c1301-272">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="c1301-273">Předpokládejme například, že máte třídu `WeatherForecast` a odvozenou třídu `WeatherForecastWithWind`:</span><span class="sxs-lookup"><span data-stu-id="c1301-273">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

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

<span data-ttu-id="c1301-274">A Předpokládejme, že argument typu metody `Serialize` v době kompilace je `WeatherForecast`:</span><span class="sxs-lookup"><span data-stu-id="c1301-274">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="c1301-275">V tomto scénáři není vlastnost `WindSpeed` serializována, i když je objekt `weatherForecast` ve skutečnosti objekt `WeatherForecastWithWind`.</span><span class="sxs-lookup"><span data-stu-id="c1301-275">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="c1301-276">Serializovat se budou jenom vlastnosti základní třídy:</span><span class="sxs-lookup"><span data-stu-id="c1301-276">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="c1301-277">Toto chování je určeno k tomu, aby se zabránilo náhodnému úniku dat v odvozeném typu vytvořeném modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="c1301-277">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="c1301-278">Chcete-li serializovat vlastnosti odvozeného typu, použijte jeden z následujících přístupů:</span><span class="sxs-lookup"><span data-stu-id="c1301-278">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="c1301-279">Zavolejte přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A>, které umožňuje určit typ za běhu:</span><span class="sxs-lookup"><span data-stu-id="c1301-279">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* <span data-ttu-id="c1301-280">Deklarujte objekt, který se má serializovat jako `object`.</span><span class="sxs-lookup"><span data-stu-id="c1301-280">Declare the object to be serialized as `object`.</span></span>

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

<span data-ttu-id="c1301-281">V předchozím ukázkovém scénáři oba přístupy způsobí, že se vlastnost `WindSpeed` zahrne do výstupu JSON:</span><span class="sxs-lookup"><span data-stu-id="c1301-281">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

<span data-ttu-id="c1301-282">Informace o polymorfní deserializaci naleznete v tématu [Podpora polymorfního deserializace](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="c1301-282">For information about polymorphic deserialization, see [Support polymorphic deserialization](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="c1301-283">Povolí komentáře a koncové čárky.</span><span class="sxs-lookup"><span data-stu-id="c1301-283">Allow comments and trailing commas</span></span>

<span data-ttu-id="c1301-284">Ve výchozím nastavení se komentáře a koncové čárky ve formátu JSON nepovolují.</span><span class="sxs-lookup"><span data-stu-id="c1301-284">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="c1301-285">Chcete-li ve formátu JSON dovolit komentáře, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> na hodnotu `JsonCommentHandling.Skip`.</span><span class="sxs-lookup"><span data-stu-id="c1301-285">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span> <span data-ttu-id="c1301-286">A pokud chcete koncovým čárkám povolený, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> na hodnotu `true`.</span><span class="sxs-lookup"><span data-stu-id="c1301-286">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="c1301-287">Následující příklad ukazuje, jak je možné:</span><span class="sxs-lookup"><span data-stu-id="c1301-287">The following example shows how to allow both:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="c1301-288">Tady je příklad JSON s komentáři a koncovou čárkou:</span><span class="sxs-lookup"><span data-stu-id="c1301-288">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="c1301-289">Porovnávání vlastností bez rozlišení velkých a malých písmen</span><span class="sxs-lookup"><span data-stu-id="c1301-289">Case-insensitive property matching</span></span>

<span data-ttu-id="c1301-290">Ve výchozím nastavení deserializace hledá název vlastnosti rozlišující velká a malá písmena mezi vlastnostmi JSON a cílovým objektem.</span><span class="sxs-lookup"><span data-stu-id="c1301-290">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="c1301-291">Chcete-li toto chování změnit, nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> na `true`:</span><span class="sxs-lookup"><span data-stu-id="c1301-291">To change that behavior, set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

<span data-ttu-id="c1301-292">Tady je příklad JSON s názvy vlastností Case ve stylu CamelCase.</span><span class="sxs-lookup"><span data-stu-id="c1301-292">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="c1301-293">Lze deserializovat do následujícího typu, který má názvy vlastností Case typu Pascal.</span><span class="sxs-lookup"><span data-stu-id="c1301-293">It can be deserialized into the following type that has Pascal case property names.</span></span>

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

## <a name="handle-overflow-json"></a><span data-ttu-id="c1301-294">Přetečení JSON popisovače</span><span class="sxs-lookup"><span data-stu-id="c1301-294">Handle overflow JSON</span></span>

<span data-ttu-id="c1301-295">Při deserializaci můžete přijímat data ve formátu JSON, která nejsou reprezentovaná vlastnostmi cílového typu.</span><span class="sxs-lookup"><span data-stu-id="c1301-295">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="c1301-296">Předpokládejme například, že váš cílový typ je:</span><span class="sxs-lookup"><span data-stu-id="c1301-296">For example, suppose your target type is this:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="c1301-297">A JSON, který se má deserializovat, je:</span><span class="sxs-lookup"><span data-stu-id="c1301-297">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="c1301-298">Pokud deserializaci kódu JSON zobrazeného na zobrazeném typu, vlastnosti `DatesAvailable` a `SummaryWords` mají nikde k přechodu a jsou ztraceny.</span><span class="sxs-lookup"><span data-stu-id="c1301-298">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="c1301-299">Chcete-li zachytit další data, jako jsou tyto vlastnosti, použijte atribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) na vlastnost typu `Dictionary<string,object>` nebo `Dictionary<string,JsonElement>`:</span><span class="sxs-lookup"><span data-stu-id="c1301-299">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

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

<span data-ttu-id="c1301-300">Při deserializaci formátu JSON zobrazeného dříve do tohoto ukázkového typu se data dalších dat stávají páry klíč-hodnota vlastnosti `ExtensionData`:</span><span class="sxs-lookup"><span data-stu-id="c1301-300">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="c1301-301">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c1301-301">Property</span></span> |<span data-ttu-id="c1301-302">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c1301-302">Value</span></span>  |<span data-ttu-id="c1301-303">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1301-303">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="c1301-304">Datum</span><span class="sxs-lookup"><span data-stu-id="c1301-304">Date</span></span>    | <span data-ttu-id="c1301-305">8/1/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="c1301-305">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="c1301-306">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="c1301-306">TemperatureC</span></span>| <span data-ttu-id="c1301-307">0,8</span><span class="sxs-lookup"><span data-stu-id="c1301-307">0</span></span> | <span data-ttu-id="c1301-308">Neshoda malých a velkých písmen (`temperatureC` ve formátu JSON), takže vlastnost není nastavená.</span><span class="sxs-lookup"><span data-stu-id="c1301-308">Case-sensitive mismatch (`temperatureC` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="c1301-309">Souhrn</span><span class="sxs-lookup"><span data-stu-id="c1301-309">Summary</span></span> | <span data-ttu-id="c1301-310">Provozu</span><span class="sxs-lookup"><span data-stu-id="c1301-310">Hot</span></span> ||
| <span data-ttu-id="c1301-311">ExtensionData –</span><span class="sxs-lookup"><span data-stu-id="c1301-311">ExtensionData</span></span> | <span data-ttu-id="c1301-312">temperatureC: 25</span><span class="sxs-lookup"><span data-stu-id="c1301-312">temperatureC: 25</span></span> |<span data-ttu-id="c1301-313">Vzhledem k tomu, že se neshoduje velká a malá písmena, je tato vlastnost JSON extra a ve slovníku se stala dvojicí klíč-hodnota.</span><span class="sxs-lookup"><span data-stu-id="c1301-313">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="c1301-314">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="c1301-314">DatesAvailable:</span></span><br>  <span data-ttu-id="c1301-315">8/1/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="c1301-315">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="c1301-316">8/2/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="c1301-316">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="c1301-317">Vlastnost extra z formátu JSON se stávají dvojicí klíč-hodnota s polem jako objektem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c1301-317">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="c1301-318">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="c1301-318">SummaryWords:</span></span><br><span data-ttu-id="c1301-319">Dobré</span><span class="sxs-lookup"><span data-stu-id="c1301-319">Cool</span></span><br><span data-ttu-id="c1301-320">Vítr</span><span class="sxs-lookup"><span data-stu-id="c1301-320">Windy</span></span><br><span data-ttu-id="c1301-321">Humid</span><span class="sxs-lookup"><span data-stu-id="c1301-321">Humid</span></span> |<span data-ttu-id="c1301-322">Vlastnost extra z formátu JSON se stávají dvojicí klíč-hodnota s polem jako objektem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c1301-322">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="c1301-323">Při serializaci cílového objektu se dvojice hodnoty klíče dat rozšíření stanou vlastnostmi JSON stejně, jako kdyby byly ve vstupním formátu JSON:</span><span class="sxs-lookup"><span data-stu-id="c1301-323">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="c1301-324">Všimněte si, že název vlastnosti `ExtensionData` se ve formátu JSON nezobrazuje.</span><span class="sxs-lookup"><span data-stu-id="c1301-324">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="c1301-325">Díky tomuto chování může JSON vytvořit zpáteční cestu, aniž by došlo ke ztrátě dalších dat, která by jinak nebyla deserializována.</span><span class="sxs-lookup"><span data-stu-id="c1301-325">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="c1301-326">Při deserializaci ignorovat hodnotu null</span><span class="sxs-lookup"><span data-stu-id="c1301-326">Ignore null when deserializing</span></span>

<span data-ttu-id="c1301-327">Ve výchozím nastavení platí, že pokud je vlastnost ve formátu JSON null, odpovídající vlastnost v cílovém objektu je nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c1301-327">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="c1301-328">V některých scénářích může cílová vlastnost mít výchozí hodnotu a nechcete, aby hodnota null přepsala výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c1301-328">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="c1301-329">Předpokládejme například, že následující kód představuje cílový objekt:</span><span class="sxs-lookup"><span data-stu-id="c1301-329">For example, suppose the following code represents your target object:</span></span>

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

<span data-ttu-id="c1301-330">A Předpokládejme, že následující kód JSON je deserializovaný:</span><span class="sxs-lookup"><span data-stu-id="c1301-330">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": null,
}
```

<span data-ttu-id="c1301-331">Po deserializaci má vlastnost `Summary` objektu `WeatherForecastWithDefault` hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c1301-331">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="c1301-332">Chcete-li toto chování změnit, nastavte <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> na `true`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c1301-332">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithDefault>(json, options);
```

<span data-ttu-id="c1301-333">Při této možnosti je vlastnost `Summary` objektu `WeatherForecastWithDefault` výchozí hodnotou "No Summary" po deserializaci.</span><span class="sxs-lookup"><span data-stu-id="c1301-333">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="c1301-334">Hodnoty null ve formátu JSON jsou ignorovány pouze v případě, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="c1301-334">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="c1301-335">Hodnoty null pro typy hodnot, které neumožňují hodnotu null, způsobují výjimky.</span><span class="sxs-lookup"><span data-stu-id="c1301-335">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="c1301-336">Další informace najdete v tématu [problém s typy hodnot, které](https://github.com/dotnet/corefx/issues/40922) neumožňují hodnotu null v úložišti dotnet/Corefx na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="c1301-336">For more information, see the [issue on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="c1301-337">Utf8JsonReader, Utf8JsonWriter a JsonDocument</span><span class="sxs-lookup"><span data-stu-id="c1301-337">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="c1301-338"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> je pro text JSON s kódováním UTF-8 s vysokým výkonem, který je určený jen pro čtení, načtený z `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="c1301-338"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="c1301-339">`Utf8JsonReader` je typ nízké úrovně, který lze použít k vytvoření vlastních analyzátorů a deserializace.</span><span class="sxs-lookup"><span data-stu-id="c1301-339">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="c1301-340">Metoda <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> používá `Utf8JsonReader` v rámci pokrývání.</span><span class="sxs-lookup"><span data-stu-id="c1301-340">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="c1301-341"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> je vysoce výkonný způsob, jak psát text JSON kódovaný v kódování UTF-8 ze běžných typů .NET, jako jsou `String`, `Int32`a `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="c1301-341"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="c1301-342">Zapisovač je typ nižší úrovně, který lze použít k vytvoření vlastních serializátorů.</span><span class="sxs-lookup"><span data-stu-id="c1301-342">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="c1301-343">Metoda <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> používá `Utf8JsonWriter` v rámci pokrývání.</span><span class="sxs-lookup"><span data-stu-id="c1301-343">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="c1301-344"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> poskytuje možnost vytvářet model DOM (Document Object Model) DOM (jen pro čtení) pomocí `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="c1301-344"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="c1301-345">Model DOM poskytuje náhodný přístup k datům v datové části JSON.</span><span class="sxs-lookup"><span data-stu-id="c1301-345">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="c1301-346">K elementům JSON, které tvoří datovou část, lze přistupovat prostřednictvím <xref:System.Text.Json.JsonElement>ho typu.</span><span class="sxs-lookup"><span data-stu-id="c1301-346">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="c1301-347">`JsonElement` poskytuje enumerátory Array a Object společně s rozhraními API pro převod textu JSON na běžné typy .NET.</span><span class="sxs-lookup"><span data-stu-id="c1301-347">The `JsonElement` provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="c1301-348">`JsonDocument` zpřístupňuje vlastnost <xref:System.Text.Json.JsonDocument.RootElement>.</span><span class="sxs-lookup"><span data-stu-id="c1301-348">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="c1301-349">Následující části ukazují, jak používat tyto nástroje pro čtení a zápis JSON.</span><span class="sxs-lookup"><span data-stu-id="c1301-349">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="c1301-350">Použití JsonDocument pro přístup k datům</span><span class="sxs-lookup"><span data-stu-id="c1301-350">Use JsonDocument for access to data</span></span>

<span data-ttu-id="c1301-351">Následující příklad ukazuje, jak použít třídu <xref:System.Text.Json.JsonDocument> pro náhodný přístup k datům:</span><span class="sxs-lookup"><span data-stu-id="c1301-351">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data:</span></span>

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

<span data-ttu-id="c1301-352">Předchozí kód:</span><span class="sxs-lookup"><span data-stu-id="c1301-352">The preceding code:</span></span>

* <span data-ttu-id="c1301-353">Předpokládá, že se JSON, který se má analyzovat, nachází v řetězci s názvem `jsonString`.</span><span class="sxs-lookup"><span data-stu-id="c1301-353">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="c1301-354">Vypočítá průměrnou třídu pro objekty v `Students` poli, které mají vlastnost `Grade`.</span><span class="sxs-lookup"><span data-stu-id="c1301-354">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span> 
* <span data-ttu-id="c1301-355">Přiřadí výchozí stupeň 70 pro studenty, kteří nemají třídu.</span><span class="sxs-lookup"><span data-stu-id="c1301-355">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="c1301-356">Počítá studenty zvýšením `count` proměnné s každou iterací.</span><span class="sxs-lookup"><span data-stu-id="c1301-356">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="c1301-357">Alternativou je volání <xref:System.Text.Json.JsonElement.GetArrayLength%2A>:</span><span class="sxs-lookup"><span data-stu-id="c1301-357">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>:</span></span>

  ```csharp
  count = studentsElement.GetArrayLength();
  ```

<span data-ttu-id="c1301-358">Zde je příklad kódu JSON, který tento kód zpracovává:</span><span class="sxs-lookup"><span data-stu-id="c1301-358">Here's an example of the JSON that this code processes:</span></span>

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

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="c1301-359">Zápis JSON pomocí JsonDocument</span><span class="sxs-lookup"><span data-stu-id="c1301-359">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="c1301-360">Následující příklad ukazuje, jak zapsat JSON z <xref:System.Text.Json.JsonDocument>:</span><span class="sxs-lookup"><span data-stu-id="c1301-360">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

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

<span data-ttu-id="c1301-361">Předchozí kód:</span><span class="sxs-lookup"><span data-stu-id="c1301-361">The preceding code:</span></span>

* <span data-ttu-id="c1301-362">Přečte soubor JSON, načte data do `JsonDocument`a zapisuje do souboru formát JSON s formátováním (poměrně vytištěného).</span><span class="sxs-lookup"><span data-stu-id="c1301-362">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="c1301-363">Používá <xref:System.Text.Json.JsonDocumentOptions> k určení, že komentáře ve vstupním JSON jsou povolené, ale ignorují se.</span><span class="sxs-lookup"><span data-stu-id="c1301-363">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="c1301-364">Po dokončení volání zavolá <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> na zapisovači.</span><span class="sxs-lookup"><span data-stu-id="c1301-364">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="c1301-365">Alternativou je umožnit zapisovači AutoFlush při jeho uvolnění.</span><span class="sxs-lookup"><span data-stu-id="c1301-365">An alternative is to let the writer autoflush when it's disposed.</span></span> 

<span data-ttu-id="c1301-366">Tady je příklad vstupu JSON, který se má zpracovat v příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="c1301-366">Here's an example of JSON input to be processed by the example code:</span></span>

```json
{"Class Name": "Science","Teacher's Name": "Jane","Semester": "2019-01-01","Students": [{"Name": "John","Grade": 94.3},{"Name": "James","Grade": 81.0},{"Name": "Julia","Grade": 91.9},{"Name": "Jessica","Grade": 72.4},{"Name": "Johnathan"}],"Final": true}
```

<span data-ttu-id="c1301-367">Výsledkem je následující poměrně tištěný výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="c1301-367">The result is the following pretty-printed JSON output:</span></span>

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

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="c1301-368">Použití Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="c1301-368">Use Utf8JsonWriter</span></span>

<span data-ttu-id="c1301-369">Následující příklad ukazuje, jak použít třídu <xref:System.Text.Json.Utf8JsonWriter>:</span><span class="sxs-lookup"><span data-stu-id="c1301-369">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

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

## <a name="use-utf8jsonreader"></a><span data-ttu-id="c1301-370">Použití Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="c1301-370">Use Utf8JsonReader</span></span>

<span data-ttu-id="c1301-371">Následující příklad ukazuje, jak použít třídu <xref:System.Text.Json.Utf8JsonReader>:</span><span class="sxs-lookup"><span data-stu-id="c1301-371">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

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

<span data-ttu-id="c1301-372">Předchozí kód předpokládá, že proměnná `jsonUtf8` je bajtové pole, které obsahuje platný kód JSON kódovaný jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c1301-372">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="c1301-373">Filtrování dat pomocí Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="c1301-373">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="c1301-374">Následující příklad ukazuje, jak číst soubor synchronně a vyhledat hodnotu:</span><span class="sxs-lookup"><span data-stu-id="c1301-374">The following example shows how to read a file synchronously and search for a value:</span></span>

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

<span data-ttu-id="c1301-375">Předchozí kód:</span><span class="sxs-lookup"><span data-stu-id="c1301-375">The preceding code:</span></span>

* <span data-ttu-id="c1301-376">Předpokládá, že soubor je kódovaný jako UTF-16 a překóduje ho do UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c1301-376">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="c1301-377">Soubor kódovaný jako UTF-8 lze číst přímo do `ReadOnlySpan<byte>`pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="c1301-377">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* <span data-ttu-id="c1301-378">Předpokládá, že JSON obsahuje pole objektů a každý objekt může obsahovat vlastnost Name typu String.</span><span class="sxs-lookup"><span data-stu-id="c1301-378">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="c1301-379">Počítá objekty a `name` hodnoty vlastností, které končí na "University".</span><span class="sxs-lookup"><span data-stu-id="c1301-379">Counts objects and `name` property values that end with "University".</span></span>

<span data-ttu-id="c1301-380">Zde je ukázka JSON, kterou může předchozí kód přečíst.</span><span class="sxs-lookup"><span data-stu-id="c1301-380">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="c1301-381">Výsledná Souhrnná zpráva je "2 z čtvrtého" má názvy, které končí na "University" ":</span><span class="sxs-lookup"><span data-stu-id="c1301-381">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="c1301-382">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="c1301-382">Additional resources</span></span>

* [<span data-ttu-id="c1301-383">Přehled System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="c1301-383">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="c1301-384">Reference k rozhraní API System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="c1301-384">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="c1301-385">Zápis vlastních převaděčů pro System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="c1301-385">Write custom converters for System.Text.Json</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="c1301-386">Podpora DateTime a DateTimeOffset v System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="c1301-386">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
