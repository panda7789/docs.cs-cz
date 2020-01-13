---
title: Postup serializace a deserializace JSON C# pomocí-.NET
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 047d5b5c6fa339089d2054eb6bfe8b3066c1d00c
ms.sourcegitcommit: dfad244ba549702b649bfef3bb057e33f24a8fb2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/12/2020
ms.locfileid: "75904661"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="90071-102">Jak serializovat a deserializovat (zařazování a zrušit zařazení) JSON v .NET</span><span class="sxs-lookup"><span data-stu-id="90071-102">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="90071-103">Tento článek ukazuje, jak použít obor názvů <xref:System.Text.Json> k serializaci a deserializaci do a z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="90071-103">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="90071-104">Pokyny a vzorový kód používají knihovnu přímo, nikoli prostřednictvím rozhraní, jako je například [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="90071-104">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="90071-105">Většina vzorových ukázkových kódů v serializaci <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` na "poměrně tištěné" formátu JSON (s odsazením a prázdným znakem pro lidské čitelnost).</span><span class="sxs-lookup"><span data-stu-id="90071-105">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="90071-106">Při použití v produkčním prostředí byste obvykle přijali výchozí hodnotu `false` pro toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="90071-106">For production use, you would typically accept the default value of `false` for this setting.</span></span>

## <a name="namespaces"></a><span data-ttu-id="90071-107">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="90071-107">Namespaces</span></span>

<span data-ttu-id="90071-108">Obor názvů <xref:System.Text.Json> obsahuje všechny vstupní body a hlavní typy.</span><span class="sxs-lookup"><span data-stu-id="90071-108">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="90071-109">Obor názvů <xref:System.Text.Json.Serialization> obsahuje atributy a rozhraní API pro pokročilé scénáře a přizpůsobení specifické pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="90071-109">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="90071-110">Příklady kódu, které jsou uvedené v tomto článku, vyžadují direktivy `using` pro jeden nebo oba tyto obory názvů:</span><span class="sxs-lookup"><span data-stu-id="90071-110">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="90071-111">Atributy z oboru názvů <xref:System.Runtime.Serialization> se v `System.Text.Json`aktuálně nepodporují.</span><span class="sxs-lookup"><span data-stu-id="90071-111">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="90071-112">Zápis objektů .NET do formátu JSON (serializace)</span><span class="sxs-lookup"><span data-stu-id="90071-112">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="90071-113">Chcete-li zapsat JSON do řetězce nebo do souboru, zavolejte metodu <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="90071-113">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="90071-114">Následující příklad vytvoří JSON jako řetězec:</span><span class="sxs-lookup"><span data-stu-id="90071-114">The following example creates JSON as a string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="90071-115">Následující příklad používá synchronní kód k vytvoření souboru JSON:</span><span class="sxs-lookup"><span data-stu-id="90071-115">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="90071-116">Následující příklad používá asynchronní kód k vytvoření souboru JSON:</span><span class="sxs-lookup"><span data-stu-id="90071-116">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="90071-117">Předchozí příklady používají odvození typu pro typ, který je serializován.</span><span class="sxs-lookup"><span data-stu-id="90071-117">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="90071-118">Přetížení `Serialize()` přebírá parametr obecného typu:</span><span class="sxs-lookup"><span data-stu-id="90071-118">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="90071-119">Příklad serializace</span><span class="sxs-lookup"><span data-stu-id="90071-119">Serialization example</span></span>

<span data-ttu-id="90071-120">Tady je ukázková třída, která obsahuje kolekce a vnořenou třídu:</span><span class="sxs-lookup"><span data-stu-id="90071-120">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="90071-121">Výstup JSON z serializace instance předchozího typu vypadá jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="90071-121">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="90071-122">Výstup JSON je ve výchozím nastavení minifikovaného:</span><span class="sxs-lookup"><span data-stu-id="90071-122">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="90071-123">Následující příklad ukazuje stejný formát JSON (to znamená, že je poměrně vytištěn s prázdným znakem a odsazením):</span><span class="sxs-lookup"><span data-stu-id="90071-123">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="90071-124">Serializovat do UTF-8</span><span class="sxs-lookup"><span data-stu-id="90071-124">Serialize to UTF-8</span></span>

<span data-ttu-id="90071-125">Chcete-li serializovat do UTF-8, zavolejte metodu <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="90071-125">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="90071-126">K dispozici je také přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A>, které přijímá <xref:System.Text.Json.Utf8JsonWriter>.</span><span class="sxs-lookup"><span data-stu-id="90071-126">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="90071-127">Serializace do UTF-8 je přibližně 5-10% rychlejší než použití metod založených na řetězci.</span><span class="sxs-lookup"><span data-stu-id="90071-127">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="90071-128">Rozdíl je z důvodu, že bajty (jako UTF-8) není nutné převést na řetězce (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="90071-128">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="90071-129">Chování serializace</span><span class="sxs-lookup"><span data-stu-id="90071-129">Serialization behavior</span></span>

* <span data-ttu-id="90071-130">Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="90071-130">By default, all public properties are serialized.</span></span> <span data-ttu-id="90071-131">Můžete [určit vlastnosti, které se mají vyloučit](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="90071-131">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="90071-132">[Výchozí kodér](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) řídí znaky jiné než ASCII, znaky citlivé na jazyk HTML v rozsahu ASCII a znaky, které musí být uvozeny podle [specifikace JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="90071-132">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="90071-133">Ve výchozím nastavení je JSON minifikovaného.</span><span class="sxs-lookup"><span data-stu-id="90071-133">By default, JSON is minified.</span></span> <span data-ttu-id="90071-134">[Kód JSON můžete v podstatě vytisknout](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="90071-134">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="90071-135">Ve výchozím nastavení jsou malá a velká písmena názvů JSON shodná s názvy .NET.</span><span class="sxs-lookup"><span data-stu-id="90071-135">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="90071-136">Můžete [přizpůsobit název a velikost písmen JSON](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="90071-136">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="90071-137">Byly zjištěny cyklické odkazy a byly vyvolány výjimky.</span><span class="sxs-lookup"><span data-stu-id="90071-137">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="90071-138">V současné době jsou pole vyloučena.</span><span class="sxs-lookup"><span data-stu-id="90071-138">Currently, fields are excluded.</span></span>

<span data-ttu-id="90071-139">Mezi podporované typy patří:</span><span class="sxs-lookup"><span data-stu-id="90071-139">Supported types include:</span></span>

* <span data-ttu-id="90071-140">Primitivní prvky .NET, které se mapují na primitivní prvky JavaScriptu, jako jsou číselné typy, řetězce a logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="90071-140">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="90071-141">Uživatelsky definované [prosté staré objekty CLR (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="90071-141">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="90071-142">Jednorozměrné a vícenásobná pole (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="90071-142">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="90071-143">`Dictionary<string,TValue>`, kde `TValue` je `object`, `JsonElement`nebo POCO.</span><span class="sxs-lookup"><span data-stu-id="90071-143">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="90071-144">Kolekce z následujících oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="90071-144">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="90071-145">[Vlastní převaděče můžete implementovat](system-text-json-converters-how-to.md) pro zpracování dalších typů nebo pro poskytování funkcí, které integrované převaděče nepodporují.</span><span class="sxs-lookup"><span data-stu-id="90071-145">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="90071-146">Postup čtení formátu JSON do objektů .NET (deserializace)</span><span class="sxs-lookup"><span data-stu-id="90071-146">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="90071-147">Chcete-li provést deserializaci z řetězce nebo souboru, zavolejte metodu <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="90071-147">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="90071-148">Následující příklad přečte JSON z řetězce a vytvoří instanci `WeatherForecast` třídy uvedené dříve pro [příklad serializace](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="90071-148">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="90071-149">Chcete-li provést deserializaci ze souboru pomocí synchronního kódu, přečtěte si soubor do řetězce, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-149">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="90071-150">Chcete-li provést deserializaci ze souboru pomocí asynchronního kódu, zavolejte metodu <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A>:</span><span class="sxs-lookup"><span data-stu-id="90071-150">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="90071-151">Deserializace ze znakové sady UTF-8</span><span class="sxs-lookup"><span data-stu-id="90071-151">Deserialize from UTF-8</span></span>

<span data-ttu-id="90071-152">Chcete-li provést deserializaci ze znakové sady UTF-8, zavolejte <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> přetížení, které přebírá `Utf8JsonReader` nebo `ReadOnlySpan<byte>`, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="90071-152">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="90071-153">V příkladech se předpokládá, že je JSON v bajtovém poli s názvem jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="90071-153">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="90071-154">Chování deserializace</span><span class="sxs-lookup"><span data-stu-id="90071-154">Deserialization behavior</span></span>

* <span data-ttu-id="90071-155">Ve výchozím nastavení se při porovnávání názvů vlastností rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="90071-155">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="90071-156">Můžete [zadat nerozlišování velkých a malých písmen](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="90071-156">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="90071-157">Pokud JSON obsahuje hodnotu vlastnosti jen pro čtení, hodnota je ignorována a není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="90071-157">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="90071-158">Deserializace na odkazové typy bez bezparametrového konstruktoru není podporována.</span><span class="sxs-lookup"><span data-stu-id="90071-158">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="90071-159">Deserializace u neměnných objektů nebo vlastností jen pro čtení není podporována.</span><span class="sxs-lookup"><span data-stu-id="90071-159">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="90071-160">Ve výchozím nastavení jsou výčty podporovány jako čísla.</span><span class="sxs-lookup"><span data-stu-id="90071-160">By default, enums are supported as numbers.</span></span> <span data-ttu-id="90071-161">[Názvy výčtů můžete serializovat jako řetězce](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="90071-161">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="90071-162">Pole nejsou podporována.</span><span class="sxs-lookup"><span data-stu-id="90071-162">Fields aren't supported.</span></span>
* <span data-ttu-id="90071-163">Ve výchozím nastavení komentáře nebo koncové čárky ve formátu JSON vyvolají výjimky.</span><span class="sxs-lookup"><span data-stu-id="90071-163">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="90071-164">Můžete [povolovat komentáře a koncové čárky](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="90071-164">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="90071-165">[Výchozí maximální hloubka](xref:System.Text.Json.JsonReaderOptions.MaxDepth) je 64.</span><span class="sxs-lookup"><span data-stu-id="90071-165">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="90071-166">[Vlastní převaděče můžete implementovat](system-text-json-converters-how-to.md) pro poskytování funkcí, které nejsou podporované integrovanými převaděči.</span><span class="sxs-lookup"><span data-stu-id="90071-166">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="90071-167">Serializovat do formátovaného formátu JSON</span><span class="sxs-lookup"><span data-stu-id="90071-167">Serialize to formatted JSON</span></span>

<span data-ttu-id="90071-168">Chcete-li vytvořit poměrně tisk výstupu JSON, nastavte <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> na `true`:</span><span class="sxs-lookup"><span data-stu-id="90071-168">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="90071-169">Tady je příklad typu pro serializaci a poměrně tištěné výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="90071-169">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="90071-170">Přizpůsobení názvů a hodnot JSON</span><span class="sxs-lookup"><span data-stu-id="90071-170">Customize JSON names and values</span></span>

<span data-ttu-id="90071-171">Ve výchozím nastavení se názvy vlastností a klíče slovníku ve výstupu JSON nezměnily, včetně případu.</span><span class="sxs-lookup"><span data-stu-id="90071-171">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="90071-172">Hodnoty výčtu jsou reprezentovány jako čísla.</span><span class="sxs-lookup"><span data-stu-id="90071-172">Enum values are represented as numbers.</span></span> <span data-ttu-id="90071-173">V této části se dozvíte, jak:</span><span class="sxs-lookup"><span data-stu-id="90071-173">This section explains how to:</span></span>

* [<span data-ttu-id="90071-174">Přizpůsobení jednotlivých názvů vlastností</span><span class="sxs-lookup"><span data-stu-id="90071-174">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="90071-175">Převést názvy všech vlastností na velikost ve stylu CamelCase</span><span class="sxs-lookup"><span data-stu-id="90071-175">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="90071-176">Implementace vlastní zásady pro pojmenovávání vlastností</span><span class="sxs-lookup"><span data-stu-id="90071-176">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="90071-177">Převede klíče slovníku na ve stylu CamelCase případ.</span><span class="sxs-lookup"><span data-stu-id="90071-177">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="90071-178">Převod výčtů na řetězce a ve stylu CamelCase velikost písmen</span><span class="sxs-lookup"><span data-stu-id="90071-178">Convert enums to strings and camel case</span></span>](#enums-as-strings) 

<span data-ttu-id="90071-179">Pro jiné scénáře, které vyžadují speciální zpracování názvů a hodnot vlastností JSON, můžete [implementovat vlastní převaděče](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="90071-179">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="90071-180">Přizpůsobení jednotlivých názvů vlastností</span><span class="sxs-lookup"><span data-stu-id="90071-180">Customize individual property names</span></span>

<span data-ttu-id="90071-181">Chcete-li nastavit název jednotlivých vlastností, použijte atribut [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="90071-181">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="90071-182">Tady je příklad typu k serializaci a výslednému formátu JSON:</span><span class="sxs-lookup"><span data-stu-id="90071-182">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="90071-183">Název vlastnosti nastavený tímto atributem:</span><span class="sxs-lookup"><span data-stu-id="90071-183">The property name set by this attribute:</span></span>

* <span data-ttu-id="90071-184">Platí v obou směrech pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="90071-184">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="90071-185">Má přednost před zásadami pro pojmenovávání vlastností.</span><span class="sxs-lookup"><span data-stu-id="90071-185">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="90071-186">Pro všechny názvy vlastností JSON použijte ve stylu CamelCase Case</span><span class="sxs-lookup"><span data-stu-id="90071-186">Use camel case for all JSON property names</span></span>

<span data-ttu-id="90071-187">Pokud chcete u všech názvů vlastností JSON použít ve stylu CamelCase, nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na `JsonNamingPolicy.CamelCase`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-187">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="90071-188">Tady je příklad třídy pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="90071-188">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="90071-189">Zásada pro pojmenování vlastností případu ve stylu CamelCase:</span><span class="sxs-lookup"><span data-stu-id="90071-189">The camel case property naming policy:</span></span>

* <span data-ttu-id="90071-190">Platí pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="90071-190">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="90071-191">Je přepsán `[JsonPropertyName]` atributy.</span><span class="sxs-lookup"><span data-stu-id="90071-191">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="90071-192">To je důvod, proč název vlastnosti JSON `Wind` v příkladu není ve stylu CamelCase Case.</span><span class="sxs-lookup"><span data-stu-id="90071-192">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="90071-193">Použít vlastní zásady pojmenování vlastností JSON</span><span class="sxs-lookup"><span data-stu-id="90071-193">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="90071-194">Chcete-li použít vlastní zásadu pojmenovávání vlastností JSON, vytvořte třídu, která je odvozena z <xref:System.Text.Json.JsonNamingPolicy> a přepište metodu <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A>, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-194">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="90071-195">Pak nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na instanci třídy zásad pojmenování:</span><span class="sxs-lookup"><span data-stu-id="90071-195">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="90071-196">Tady je příklad třídy pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="90071-196">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="90071-197">Zásady pojmenování vlastností JSON:</span><span class="sxs-lookup"><span data-stu-id="90071-197">The JSON property naming policy:</span></span>

* <span data-ttu-id="90071-198">Platí pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="90071-198">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="90071-199">Je přepsán `[JsonPropertyName]` atributy.</span><span class="sxs-lookup"><span data-stu-id="90071-199">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="90071-200">Důvodem je, že název vlastnosti JSON `Wind` v příkladu není velká písmena.</span><span class="sxs-lookup"><span data-stu-id="90071-200">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="90071-201">Klíče slovníku případů ve stylu CamelCase</span><span class="sxs-lookup"><span data-stu-id="90071-201">Camel case dictionary keys</span></span>

<span data-ttu-id="90071-202">Pokud je vlastnost objektu, která má být serializována, typu `Dictionary<string,TValue>`, `string` klíče lze převést na ve stylu CamelCase případ.</span><span class="sxs-lookup"><span data-stu-id="90071-202">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="90071-203">Provedete to tak, že nastavíte <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> na `JsonNamingPolicy.CamelCase`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-203">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="90071-204">Serializace objektu se slovníkem s názvem `TemperatureRanges`, který má páry klíč-hodnota `"ColdMinTemp", 20` a `"HotMinTemp", 40` by vedlo jako výstup JSON jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-204">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="90071-205">Zásady pro pojmenovávání ve stylu CamelCase pro klíče slovníku se vztahují pouze na serializaci.</span><span class="sxs-lookup"><span data-stu-id="90071-205">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="90071-206">Pokud deserializaci slovníku, klíče budou odpovídat souboru JSON, i když zadáte `JsonNamingPolicy.CamelCase` pro `DictionaryKeyPolicy`.</span><span class="sxs-lookup"><span data-stu-id="90071-206">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="90071-207">Výčty jako řetězce</span><span class="sxs-lookup"><span data-stu-id="90071-207">Enums as strings</span></span>

<span data-ttu-id="90071-208">Ve výchozím nastavení jsou výčty serializovány jako čísla.</span><span class="sxs-lookup"><span data-stu-id="90071-208">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="90071-209">Chcete-li serializovat názvy výčtu jako řetězce, použijte <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span><span class="sxs-lookup"><span data-stu-id="90071-209">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="90071-210">Předpokládejme například, že potřebujete serializovat následující třídu, která má výčet:</span><span class="sxs-lookup"><span data-stu-id="90071-210">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="90071-211">Pokud je souhrn `Hot`, ve výchozím nastavení má serializovaný formát JSON číselnou hodnotu 3:</span><span class="sxs-lookup"><span data-stu-id="90071-211">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="90071-212">Následující vzorový kód místo číselných hodnot serializace názvy výčtu a převede názvy na ve stylu CamelCase případ:</span><span class="sxs-lookup"><span data-stu-id="90071-212">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="90071-213">Výsledný kód JSON vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-213">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="90071-214">Názvy řetězců výčtu lze deserializovat také, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-214">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="90071-215">Vyloučit vlastnosti ze serializace</span><span class="sxs-lookup"><span data-stu-id="90071-215">Exclude properties from serialization</span></span>

<span data-ttu-id="90071-216">Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="90071-216">By default, all public properties are serialized.</span></span> <span data-ttu-id="90071-217">Pokud nechcete, aby se některé z nich zobrazovaly ve výstupu JSON, máte několik možností.</span><span class="sxs-lookup"><span data-stu-id="90071-217">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="90071-218">V této části se dozvíte, jak vyloučit:</span><span class="sxs-lookup"><span data-stu-id="90071-218">This section explains how to exclude:</span></span>

* [<span data-ttu-id="90071-219">Jednotlivé vlastnosti</span><span class="sxs-lookup"><span data-stu-id="90071-219">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="90071-220">Všechny vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="90071-220">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="90071-221">Všechny vlastnosti s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="90071-221">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="90071-222">Vyloučení individuálních vlastností</span><span class="sxs-lookup"><span data-stu-id="90071-222">Exclude individual properties</span></span>

<span data-ttu-id="90071-223">Chcete-li ignorovat jednotlivé vlastnosti, použijte atribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="90071-223">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="90071-224">Tady je příklad typu pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="90071-224">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="90071-225">Vyloučit všechny vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="90071-225">Exclude all read-only properties</span></span>

<span data-ttu-id="90071-226">Vlastnost je jen pro čtení, pokud obsahuje veřejnou metodu getter, ale ne veřejnou metodu setter.</span><span class="sxs-lookup"><span data-stu-id="90071-226">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="90071-227">Chcete-li vyloučit všechny vlastnosti jen pro čtení, nastavte <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> na `true`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-227">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="90071-228">Tady je příklad typu pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="90071-228">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="90071-229">Tato možnost se vztahuje pouze na serializaci.</span><span class="sxs-lookup"><span data-stu-id="90071-229">This option applies only to serialization.</span></span> <span data-ttu-id="90071-230">Během deserializace jsou vlastnosti jen pro čtení ve výchozím nastavení ignorovány.</span><span class="sxs-lookup"><span data-stu-id="90071-230">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="90071-231">Vyloučit všechny vlastnosti hodnoty null</span><span class="sxs-lookup"><span data-stu-id="90071-231">Exclude all null value properties</span></span>

<span data-ttu-id="90071-232">Chcete-li vyloučit všechny vlastnosti hodnoty null, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> na hodnotu `true`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-232">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="90071-233">Zde je příklad objektu pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="90071-233">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="90071-234">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="90071-234">Property</span></span> |<span data-ttu-id="90071-235">Hodnota</span><span class="sxs-lookup"><span data-stu-id="90071-235">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="90071-236">Datum</span><span class="sxs-lookup"><span data-stu-id="90071-236">Date</span></span>    | <span data-ttu-id="90071-237">8/1/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="90071-237">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="90071-238">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="90071-238">TemperatureCelsius</span></span>| <span data-ttu-id="90071-239">25</span><span class="sxs-lookup"><span data-stu-id="90071-239">25</span></span> |
| <span data-ttu-id="90071-240">Přehled</span><span class="sxs-lookup"><span data-stu-id="90071-240">Summary</span></span>| <span data-ttu-id="90071-241">null</span><span class="sxs-lookup"><span data-stu-id="90071-241">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="90071-242">Toto nastavení platí pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="90071-242">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="90071-243">Informace o jeho vlivu na deserializaci naleznete v tématu [Ignore null Při deserializaci](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="90071-243">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="90071-244">Přizpůsobení kódování znaků</span><span class="sxs-lookup"><span data-stu-id="90071-244">Customize character encoding</span></span>

<span data-ttu-id="90071-245">Ve výchozím nastavení serializátor řídí všechny znaky jiné než ASCII.</span><span class="sxs-lookup"><span data-stu-id="90071-245">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="90071-246">To znamená, že je nahradí je `\uxxxx`, kde `xxxx` je kód Unicode znaku.</span><span class="sxs-lookup"><span data-stu-id="90071-246">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="90071-247">Například pokud je vlastnost `Summary` nastavena na жаркоa v cyrilici, `WeatherForecast` objekt je serializován, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-247">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="90071-248">Serializovat znakové sady jazyků</span><span class="sxs-lookup"><span data-stu-id="90071-248">Serialize language character sets</span></span>

<span data-ttu-id="90071-249">Chcete-li serializovat znakové sady jednoho nebo více jazyků bez uvozovacího znaku, určete [rozsahy Unicode](xref:System.Text.Unicode.UnicodeRanges) při vytváření instance <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-249">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="90071-250">Tento kód neřídí cyrilici ani řecké znaky.</span><span class="sxs-lookup"><span data-stu-id="90071-250">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="90071-251">Pokud je vlastnost `Summary` nastavena na жаркоa v cyrilici, `WeatherForecast` objekt je serializován, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-251">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="90071-252">Chcete-li serializovat všechny jazykové sady bez uvozovacího uvozovacího, použijte <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="90071-252">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="90071-253">Serializovat konkrétní znaky</span><span class="sxs-lookup"><span data-stu-id="90071-253">Serialize specific characters</span></span>

<span data-ttu-id="90071-254">Alternativou je zadání jednotlivých znaků, které chcete použít, bez nutnosti řídicích znaků.</span><span class="sxs-lookup"><span data-stu-id="90071-254">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="90071-255">Následující příklad serializace pouze prvních dvou znaků жарко:</span><span class="sxs-lookup"><span data-stu-id="90071-255">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="90071-256">Zde je příklad kódu JSON vytvořeného předchozím kódem:</span><span class="sxs-lookup"><span data-stu-id="90071-256">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="90071-257">Serializovat všechny znaky</span><span class="sxs-lookup"><span data-stu-id="90071-257">Serialize all characters</span></span>

<span data-ttu-id="90071-258">Chcete-li minimalizovat uvozovací znaky, můžete použít <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-258">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="90071-259">V porovnání s výchozím kodérem je `UnsafeRelaxedJsonEscaping` kodér více opravňující, aby bylo možné předávat znaky bez řídicích znaků:</span><span class="sxs-lookup"><span data-stu-id="90071-259">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="90071-260">Neřídí znaky citlivé na HTML, například `<`, `>`, `&`a `'`.</span><span class="sxs-lookup"><span data-stu-id="90071-260">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="90071-261">Nenabízí žádné další ochrany proti důkladné ochraně před útoky XSS nebo informací, jako jsou ty, které by mohly vzniknout ze strany klienta a *serveru na znakovou sadu.*</span><span class="sxs-lookup"><span data-stu-id="90071-261">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="90071-262">Nezabezpečený kodér používejte pouze v případě, že je známo, že klient bude interpretovat výslednou datovou část jako JSON kódovaný v kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="90071-262">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="90071-263">Můžete ji například použít, pokud server odesílá hlavičku odpovědi `Content-Type: application/json; charset=utf-8`.</span><span class="sxs-lookup"><span data-stu-id="90071-263">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="90071-264">Nikdy nepovolujte výstup nezpracovaného `UnsafeRelaxedJsonEscaping` do stránky HTML nebo elementu `<script>`.</span><span class="sxs-lookup"><span data-stu-id="90071-264">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="90071-265">Serializovat vlastnosti odvozených tříd</span><span class="sxs-lookup"><span data-stu-id="90071-265">Serialize properties of derived classes</span></span>

<span data-ttu-id="90071-266">Serializace hierarchie polymorfního typu není podporována.</span><span class="sxs-lookup"><span data-stu-id="90071-266">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="90071-267">Například pokud je vlastnost definována jako rozhraní nebo abstraktní třída, jsou serializovány pouze vlastnosti definované v rozhraní nebo abstraktní třídě, a to i v případě, že typ modulu runtime má další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="90071-267">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="90071-268">Výjimky z tohoto chování jsou vysvětleny v této části.</span><span class="sxs-lookup"><span data-stu-id="90071-268">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="90071-269">Předpokládejme například, že máte třídu `WeatherForecast` a odvozenou třídu `WeatherForecastDerived`:</span><span class="sxs-lookup"><span data-stu-id="90071-269">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="90071-270">A Předpokládejme, že argument typu metody `Serialize` v době kompilace je `WeatherForecast`:</span><span class="sxs-lookup"><span data-stu-id="90071-270">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="90071-271">V tomto scénáři není vlastnost `WindSpeed` serializována i v případě, že je objekt `weatherForecast` ve skutečnosti objekt `WeatherForecastDerived`.</span><span class="sxs-lookup"><span data-stu-id="90071-271">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="90071-272">Serializovat se budou jenom vlastnosti základní třídy:</span><span class="sxs-lookup"><span data-stu-id="90071-272">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="90071-273">Toto chování je určeno k tomu, aby se zabránilo náhodnému úniku dat v odvozeném typu vytvořeném modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="90071-273">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="90071-274">Chcete-li serializovat vlastnosti odvozeného typu v předchozím příkladu, použijte jeden z následujících přístupů:</span><span class="sxs-lookup"><span data-stu-id="90071-274">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="90071-275">Zavolejte přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A>, které umožňuje určit typ za běhu:</span><span class="sxs-lookup"><span data-stu-id="90071-275">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="90071-276">Deklarujte objekt, který se má serializovat jako `object`.</span><span class="sxs-lookup"><span data-stu-id="90071-276">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="90071-277">V předchozím ukázkovém scénáři obě přístupy způsobí, že vlastnost `WindSpeed` bude zahrnutá ve výstupu JSON:</span><span class="sxs-lookup"><span data-stu-id="90071-277">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="90071-278">Tyto přístupy poskytují polymorfní serializaci pouze pro kořenový objekt, který má být serializován, nikoli pro vlastnosti daného kořenového objektu.</span><span class="sxs-lookup"><span data-stu-id="90071-278">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span> 

<span data-ttu-id="90071-279">Můžete získat polymorfní serializaci pro objekty nižší úrovně, pokud je definujete jako typ `object`.</span><span class="sxs-lookup"><span data-stu-id="90071-279">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="90071-280">Předpokládejme například, že vaše třída `WeatherForecast` má vlastnost s názvem `PreviousForecast`, kterou lze definovat jako typ `WeatherForecast` nebo `object`:</span><span class="sxs-lookup"><span data-stu-id="90071-280">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="90071-281">Pokud vlastnost `PreviousForecast` obsahuje instanci `WeatherForecastDerived`:</span><span class="sxs-lookup"><span data-stu-id="90071-281">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="90071-282">Výstup JSON pro serializaci `WeatherForecastWithPrevious` **nezahrnuje** `WindSpeed`.</span><span class="sxs-lookup"><span data-stu-id="90071-282">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="90071-283">Výstup JSON pro serializaci `WeatherForecastWithPreviousAsObject` **zahrnuje** `WindSpeed`.</span><span class="sxs-lookup"><span data-stu-id="90071-283">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="90071-284">Pro serializaci `WeatherForecastWithPreviousAsObject`není nutné volat `Serialize<object>` nebo `GetType`, protože kořenový objekt není ten, který může být odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="90071-284">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="90071-285">Následující příklad kódu nevolá `Serialize<object>` nebo `GetType`:</span><span class="sxs-lookup"><span data-stu-id="90071-285">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="90071-286">Předchozí kód správně serializace `WeatherForecastWithPreviousAsObject`:</span><span class="sxs-lookup"><span data-stu-id="90071-286">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="90071-287">Stejný přístup k definování vlastností jako `object` pracuje s rozhraními.</span><span class="sxs-lookup"><span data-stu-id="90071-287">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="90071-288">Předpokládejme, že máte následující rozhraní a implementaci a chcete serializovat třídu s vlastnostmi, které obsahují instance implementace:</span><span class="sxs-lookup"><span data-stu-id="90071-288">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

<span data-ttu-id="90071-289">Při serializaci instance `Forecasts`pouze `Tuesday` zobrazí vlastnost `WindSpeed`, protože `Tuesday` je definován jako `object`:</span><span class="sxs-lookup"><span data-stu-id="90071-289">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="90071-290">Následující příklad ukazuje kód JSON, který je výsledkem předchozího kódu:</span><span class="sxs-lookup"><span data-stu-id="90071-290">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="90071-291">Další informace o polymorfní **serializaci**a informace o **deserializaci**naleznete v tématu [How to migruje from Newtonsoft. JSON to System. text. JSON](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="90071-291">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="90071-292">Povolí komentáře a koncové čárky.</span><span class="sxs-lookup"><span data-stu-id="90071-292">Allow comments and trailing commas</span></span>

<span data-ttu-id="90071-293">Ve výchozím nastavení se komentáře a koncové čárky ve formátu JSON nepovolují.</span><span class="sxs-lookup"><span data-stu-id="90071-293">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="90071-294">Chcete-li ve formátu JSON dovolit komentáře, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> na hodnotu `JsonCommentHandling.Skip`.</span><span class="sxs-lookup"><span data-stu-id="90071-294">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="90071-295">A pokud chcete koncovým čárkám povolený, nastavte vlastnost <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> na `true`.</span><span class="sxs-lookup"><span data-stu-id="90071-295">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="90071-296">Následující příklad ukazuje, jak je možné:</span><span class="sxs-lookup"><span data-stu-id="90071-296">The following example shows how to allow both:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="90071-297">Tady je příklad JSON s komentáři a koncovou čárkou:</span><span class="sxs-lookup"><span data-stu-id="90071-297">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="90071-298">Porovnávání vlastností bez rozlišení velkých a malých písmen</span><span class="sxs-lookup"><span data-stu-id="90071-298">Case-insensitive property matching</span></span>

<span data-ttu-id="90071-299">Ve výchozím nastavení deserializace hledá název vlastnosti rozlišující velká a malá písmena mezi vlastnostmi JSON a cílovým objektem.</span><span class="sxs-lookup"><span data-stu-id="90071-299">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="90071-300">Chcete-li toto chování změnit, nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> na `true`:</span><span class="sxs-lookup"><span data-stu-id="90071-300">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="90071-301">Tady je příklad JSON s názvy vlastností Case ve stylu CamelCase.</span><span class="sxs-lookup"><span data-stu-id="90071-301">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="90071-302">Lze deserializovat do následujícího typu, který má názvy vlastností Case typu Pascal.</span><span class="sxs-lookup"><span data-stu-id="90071-302">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="90071-303">Přetečení JSON popisovače</span><span class="sxs-lookup"><span data-stu-id="90071-303">Handle overflow JSON</span></span>

<span data-ttu-id="90071-304">Při deserializaci můžete přijímat data ve formátu JSON, která nejsou reprezentovaná vlastnostmi cílového typu.</span><span class="sxs-lookup"><span data-stu-id="90071-304">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="90071-305">Předpokládejme například, že váš cílový typ je:</span><span class="sxs-lookup"><span data-stu-id="90071-305">For example, suppose your target type is this:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="90071-306">A JSON, který se má deserializovat, je:</span><span class="sxs-lookup"><span data-stu-id="90071-306">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="90071-307">Pokud deserializaci kódu JSON zobrazeného na zobrazeném typu, `DatesAvailable` a `SummaryWords` vlastnosti mají nikde a budou ztraceny.</span><span class="sxs-lookup"><span data-stu-id="90071-307">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="90071-308">Chcete-li zachytit další data, jako jsou tyto vlastnosti, použijte atribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) na vlastnost typu `Dictionary<string,object>` nebo `Dictionary<string,JsonElement>`:</span><span class="sxs-lookup"><span data-stu-id="90071-308">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="90071-309">Při deserializaci formátu JSON zobrazeného dříve do tohoto ukázkového typu se data dalších dat stávají páry klíč-hodnota vlastnosti `ExtensionData`:</span><span class="sxs-lookup"><span data-stu-id="90071-309">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="90071-310">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="90071-310">Property</span></span> |<span data-ttu-id="90071-311">Hodnota</span><span class="sxs-lookup"><span data-stu-id="90071-311">Value</span></span>  |<span data-ttu-id="90071-312">Poznámky</span><span class="sxs-lookup"><span data-stu-id="90071-312">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="90071-313">Datum</span><span class="sxs-lookup"><span data-stu-id="90071-313">Date</span></span>    | <span data-ttu-id="90071-314">8/1/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="90071-314">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="90071-315">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="90071-315">TemperatureCelsius</span></span>| <span data-ttu-id="90071-316">0</span><span class="sxs-lookup"><span data-stu-id="90071-316">0</span></span> | <span data-ttu-id="90071-317">Neshoda malých a velkých písmen (`temperatureCelsius` ve formátu JSON), takže vlastnost není nastavená.</span><span class="sxs-lookup"><span data-stu-id="90071-317">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="90071-318">Přehled</span><span class="sxs-lookup"><span data-stu-id="90071-318">Summary</span></span> | <span data-ttu-id="90071-319">Horká</span><span class="sxs-lookup"><span data-stu-id="90071-319">Hot</span></span> ||
| <span data-ttu-id="90071-320">ExtensionData –</span><span class="sxs-lookup"><span data-stu-id="90071-320">ExtensionData</span></span> | <span data-ttu-id="90071-321">temperatureCelsius: 25</span><span class="sxs-lookup"><span data-stu-id="90071-321">temperatureCelsius: 25</span></span> |<span data-ttu-id="90071-322">Vzhledem k tomu, že se neshoduje velká a malá písmena, je tato vlastnost JSON extra a ve slovníku se stala dvojicí klíč-hodnota.</span><span class="sxs-lookup"><span data-stu-id="90071-322">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="90071-323">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="90071-323">DatesAvailable:</span></span><br>  <span data-ttu-id="90071-324">8/1/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="90071-324">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="90071-325">8/2/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="90071-325">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="90071-326">Vlastnost extra z formátu JSON se stávají dvojicí klíč-hodnota s polem jako objektem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="90071-326">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="90071-327">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="90071-327">SummaryWords:</span></span><br><span data-ttu-id="90071-328">Studená</span><span class="sxs-lookup"><span data-stu-id="90071-328">Cool</span></span><br><span data-ttu-id="90071-329">Vítr</span><span class="sxs-lookup"><span data-stu-id="90071-329">Windy</span></span><br><span data-ttu-id="90071-330">Humid</span><span class="sxs-lookup"><span data-stu-id="90071-330">Humid</span></span> |<span data-ttu-id="90071-331">Vlastnost extra z formátu JSON se stávají dvojicí klíč-hodnota s polem jako objektem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="90071-331">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="90071-332">Při serializaci cílového objektu se dvojice hodnoty klíče dat rozšíření stanou vlastnostmi JSON stejně, jako kdyby byly ve vstupním formátu JSON:</span><span class="sxs-lookup"><span data-stu-id="90071-332">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="90071-333">Všimněte si, že název vlastnosti `ExtensionData` se ve formátu JSON nezobrazuje.</span><span class="sxs-lookup"><span data-stu-id="90071-333">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="90071-334">Díky tomuto chování může JSON vytvořit zpáteční cestu, aniž by došlo ke ztrátě dalších dat, která by jinak nebyla deserializována.</span><span class="sxs-lookup"><span data-stu-id="90071-334">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="90071-335">Při deserializaci ignorovat hodnotu null</span><span class="sxs-lookup"><span data-stu-id="90071-335">Ignore null when deserializing</span></span>

<span data-ttu-id="90071-336">Ve výchozím nastavení platí, že pokud je vlastnost ve formátu JSON null, odpovídající vlastnost v cílovém objektu je nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="90071-336">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="90071-337">V některých scénářích může cílová vlastnost mít výchozí hodnotu a nechcete, aby hodnota null přepsala výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="90071-337">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="90071-338">Předpokládejme například, že následující kód představuje cílový objekt:</span><span class="sxs-lookup"><span data-stu-id="90071-338">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="90071-339">A Předpokládejme, že následující kód JSON je deserializovaný:</span><span class="sxs-lookup"><span data-stu-id="90071-339">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="90071-340">Po deserializaci má vlastnost `Summary` objektu `WeatherForecastWithDefault` hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="90071-340">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="90071-341">Chcete-li toto chování změnit, nastavte <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> na `true`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-341">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="90071-342">Při této možnosti je vlastnost `Summary` objektu `WeatherForecastWithDefault` výchozí hodnotou "No Summary" po deserializaci.</span><span class="sxs-lookup"><span data-stu-id="90071-342">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="90071-343">Hodnoty null ve formátu JSON jsou ignorovány pouze v případě, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="90071-343">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="90071-344">Hodnoty null pro typy hodnot, které neumožňují hodnotu null, způsobují výjimky.</span><span class="sxs-lookup"><span data-stu-id="90071-344">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="90071-345">Utf8JsonReader, Utf8JsonWriter a JsonDocument</span><span class="sxs-lookup"><span data-stu-id="90071-345">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="90071-346"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> je pro text JSON s kódováním UTF-8 s vysokým výkonem vysoce výkonné, nízké přidělení a je čteno z `ReadOnlySpan<byte>` nebo `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="90071-346"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="90071-347">`Utf8JsonReader` je typ nízké úrovně, který lze použít k vytvoření vlastních analyzátorů a deserializace.</span><span class="sxs-lookup"><span data-stu-id="90071-347">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="90071-348">Metoda <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> používá `Utf8JsonReader` v rámci pokrývání.</span><span class="sxs-lookup"><span data-stu-id="90071-348">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="90071-349"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> je vysoce výkonný způsob, jak psát text JSON kódovaný v kódování UTF-8 ze běžných typů .NET, jako jsou `String`, `Int32`a `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="90071-349"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="90071-350">Zapisovač je typ nižší úrovně, který lze použít k vytvoření vlastních serializátorů.</span><span class="sxs-lookup"><span data-stu-id="90071-350">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="90071-351">Metoda <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> používá `Utf8JsonWriter` v rámci pokrývání.</span><span class="sxs-lookup"><span data-stu-id="90071-351">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="90071-352"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> poskytuje možnost vytvářet model DOM (Document Object Model) DOM (jen pro čtení) pomocí `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="90071-352"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="90071-353">Model DOM poskytuje náhodný přístup k datům v datové části JSON.</span><span class="sxs-lookup"><span data-stu-id="90071-353">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="90071-354">K elementům JSON, které tvoří datovou část, lze přistupovat prostřednictvím <xref:System.Text.Json.JsonElement>ho typu.</span><span class="sxs-lookup"><span data-stu-id="90071-354">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="90071-355">`JsonElement` typ poskytuje enumerátory Array a Object spolu s rozhraními API pro převod textu JSON na běžné typy .NET.</span><span class="sxs-lookup"><span data-stu-id="90071-355">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="90071-356">`JsonDocument` zpřístupňuje vlastnost <xref:System.Text.Json.JsonDocument.RootElement>.</span><span class="sxs-lookup"><span data-stu-id="90071-356">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="90071-357">Následující části ukazují, jak používat tyto nástroje pro čtení a zápis JSON.</span><span class="sxs-lookup"><span data-stu-id="90071-357">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="90071-358">Použití JsonDocument pro přístup k datům</span><span class="sxs-lookup"><span data-stu-id="90071-358">Use JsonDocument for access to data</span></span>

<span data-ttu-id="90071-359">Následující příklad ukazuje, jak použít třídu <xref:System.Text.Json.JsonDocument> pro náhodný přístup k datům v řetězci JSON:</span><span class="sxs-lookup"><span data-stu-id="90071-359">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="90071-360">Předchozí kód:</span><span class="sxs-lookup"><span data-stu-id="90071-360">The preceding code:</span></span>

* <span data-ttu-id="90071-361">Předpokládá, že se JSON, který se má analyzovat, nachází v řetězci s názvem `jsonString`.</span><span class="sxs-lookup"><span data-stu-id="90071-361">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="90071-362">Vypočítá průměrnou třídu pro objekty v `Students` poli, které mají vlastnost `Grade`.</span><span class="sxs-lookup"><span data-stu-id="90071-362">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span> 
* <span data-ttu-id="90071-363">Přiřadí výchozí stupeň 70 pro studenty, kteří nemají třídu.</span><span class="sxs-lookup"><span data-stu-id="90071-363">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="90071-364">Počítá studenty zvýšením `count` proměnné s každou iterací.</span><span class="sxs-lookup"><span data-stu-id="90071-364">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="90071-365">Alternativou je volání <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="90071-365">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="90071-366">Zde je příklad kódu JSON, který tento kód zpracovává:</span><span class="sxs-lookup"><span data-stu-id="90071-366">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="90071-367">Zápis JSON pomocí JsonDocument</span><span class="sxs-lookup"><span data-stu-id="90071-367">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="90071-368">Následující příklad ukazuje, jak zapsat JSON z <xref:System.Text.Json.JsonDocument>:</span><span class="sxs-lookup"><span data-stu-id="90071-368">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="90071-369">Předchozí kód:</span><span class="sxs-lookup"><span data-stu-id="90071-369">The preceding code:</span></span>

* <span data-ttu-id="90071-370">Přečte soubor JSON, načte data do `JsonDocument`a zapisuje do souboru formát JSON s formátováním (poměrně vytištěného).</span><span class="sxs-lookup"><span data-stu-id="90071-370">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="90071-371">Používá <xref:System.Text.Json.JsonDocumentOptions> k určení, že komentáře ve vstupním JSON jsou povolené, ale ignorují se.</span><span class="sxs-lookup"><span data-stu-id="90071-371">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="90071-372">Po dokončení volání zavolá <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> na zapisovači.</span><span class="sxs-lookup"><span data-stu-id="90071-372">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="90071-373">Alternativou je umožnit zapisovači AutoFlush při jeho uvolnění.</span><span class="sxs-lookup"><span data-stu-id="90071-373">An alternative is to let the writer autoflush when it's disposed.</span></span> 

<span data-ttu-id="90071-374">Tady je příklad vstupu JSON, který se má zpracovat v příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="90071-374">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

<span data-ttu-id="90071-375">Výsledkem je následující poměrně tištěný výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="90071-375">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="90071-376">Použití Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="90071-376">Use Utf8JsonWriter</span></span>

<span data-ttu-id="90071-377">Následující příklad ukazuje, jak použít třídu <xref:System.Text.Json.Utf8JsonWriter>:</span><span class="sxs-lookup"><span data-stu-id="90071-377">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="90071-378">Použití Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="90071-378">Use Utf8JsonReader</span></span>

<span data-ttu-id="90071-379">Následující příklad ukazuje, jak použít třídu <xref:System.Text.Json.Utf8JsonReader>:</span><span class="sxs-lookup"><span data-stu-id="90071-379">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="90071-380">Předchozí kód předpokládá, že proměnná `jsonUtf8` je bajtové pole, které obsahuje platný kód JSON kódovaný jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="90071-380">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="90071-381">Filtrování dat pomocí Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="90071-381">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="90071-382">Následující příklad ukazuje, jak číst soubor synchronně a vyhledat hodnotu:</span><span class="sxs-lookup"><span data-stu-id="90071-382">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="90071-383">Předchozí kód:</span><span class="sxs-lookup"><span data-stu-id="90071-383">The preceding code:</span></span>

* <span data-ttu-id="90071-384">Předpokládá, že JSON obsahuje pole objektů a každý objekt může obsahovat vlastnost Name typu String.</span><span class="sxs-lookup"><span data-stu-id="90071-384">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="90071-385">Spočítá hodnoty vlastností Objects a Name, které končí na "University".</span><span class="sxs-lookup"><span data-stu-id="90071-385">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="90071-386">Předpokládá, že soubor je kódovaný jako UTF-16 a překóduje ho do UTF-8.</span><span class="sxs-lookup"><span data-stu-id="90071-386">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="90071-387">Soubor kódovaný jako UTF-8 lze číst přímo do `ReadOnlySpan<byte>`pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="90071-387">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

  <span data-ttu-id="90071-388">Pokud soubor obsahuje znak pořadí bajtů UTF-8 (BOM), odeberte ho před předáním bajtů do `Utf8JsonReader`, protože čtecí modul očekává text.</span><span class="sxs-lookup"><span data-stu-id="90071-388">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="90071-389">V opačném případě se kusovník považuje za neplatný kód JSON a čtenář vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="90071-389">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="90071-390">Zde je ukázka JSON, kterou může předchozí kód přečíst.</span><span class="sxs-lookup"><span data-stu-id="90071-390">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="90071-391">Výsledná Souhrnná zpráva je "2 z čtvrtého" má názvy, které končí na "University" ":</span><span class="sxs-lookup"><span data-stu-id="90071-391">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a><span data-ttu-id="90071-392">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="90071-392">Additional resources</span></span>

* [<span data-ttu-id="90071-393">Přehled System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="90071-393">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="90071-394">Zápis vlastních převaděčů</span><span class="sxs-lookup"><span data-stu-id="90071-394">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="90071-395">Postup migrace z Newtonsoft. JSON</span><span class="sxs-lookup"><span data-stu-id="90071-395">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="90071-396">Podpora DateTime a DateTimeOffset v System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="90071-396">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="90071-397">Reference k rozhraní API System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="90071-397">System.Text.Json API reference</span></span>](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
