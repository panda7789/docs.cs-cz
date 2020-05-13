---
title: Postup serializace a deserializace JSON pomocí C#-.NET
description: V tomto článku se dozvíte, jak použít System.Text.Json obor názvů k serializaci a deserializaci z formátu JSON v rozhraní .NET. Obsahuje vzorový kód.
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: ad748508b73c3e141ae345efa0abb66c009740cd
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378727"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="f3200-104">Jak serializovat a deserializovat (zařazování a zrušit zařazení) JSON v .NET</span><span class="sxs-lookup"><span data-stu-id="f3200-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="f3200-105">Tento článek ukazuje, jak použít <xref:System.Text.Json> obor názvů k serializaci a deserializaci do a z JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="f3200-105">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="f3200-106">Pokud přenášíte existující kód z nástroje `Newtonsoft.Json` , přečtěte si téma [Jak `System.Text.Json` migrovat na ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="f3200-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="f3200-107">Pokyny a vzorový kód používají knihovnu přímo, nikoli prostřednictvím rozhraní, jako je například [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="f3200-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="f3200-108">Většina ukázkových kódů serializace se nastaví na <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` "poměrně tištěné" formát JSON (s odsazením a prázdným znakem pro lidskou čitelnost).</span><span class="sxs-lookup"><span data-stu-id="f3200-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="f3200-109">V případě produkčního použití byste obvykle přijímají výchozí hodnotu `false` pro toto nastavení.</span><span class="sxs-lookup"><span data-stu-id="f3200-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="f3200-110">Příklady kódu odkazují na následující třídu a varianty:</span><span class="sxs-lookup"><span data-stu-id="f3200-110">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="f3200-111">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="f3200-111">Namespaces</span></span>

<span data-ttu-id="f3200-112"><xref:System.Text.Json>Obor názvů obsahuje všechny vstupní body a hlavní typy.</span><span class="sxs-lookup"><span data-stu-id="f3200-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="f3200-113"><xref:System.Text.Json.Serialization>Obor názvů obsahuje atributy a rozhraní API pro pokročilé scénáře a přizpůsobení specifické pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="f3200-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="f3200-114">Příklady kódu, které jsou uvedeny v tomto článku, vyžadují `using` direktivy pro jeden nebo oba tyto obory názvů:</span><span class="sxs-lookup"><span data-stu-id="f3200-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="f3200-115">Atributy z <xref:System.Runtime.Serialization> oboru názvů se v současné době nepodporují `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="f3200-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="f3200-116">Zápis objektů .NET do formátu JSON (serializace)</span><span class="sxs-lookup"><span data-stu-id="f3200-116">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="f3200-117">Chcete-li zapsat JSON do řetězce nebo do souboru, zavolejte <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="f3200-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="f3200-118">Následující příklad vytvoří JSON jako řetězec:</span><span class="sxs-lookup"><span data-stu-id="f3200-118">The following example creates JSON as a string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="f3200-119">Následující příklad používá synchronní kód k vytvoření souboru JSON:</span><span class="sxs-lookup"><span data-stu-id="f3200-119">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="f3200-120">Následující příklad používá asynchronní kód k vytvoření souboru JSON:</span><span class="sxs-lookup"><span data-stu-id="f3200-120">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="f3200-121">Předchozí příklady používají odvození typu pro typ, který je serializován.</span><span class="sxs-lookup"><span data-stu-id="f3200-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="f3200-122">Přetížení `Serialize()` přebírá parametr obecného typu:</span><span class="sxs-lookup"><span data-stu-id="f3200-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="f3200-123">Příklad serializace</span><span class="sxs-lookup"><span data-stu-id="f3200-123">Serialization example</span></span>

<span data-ttu-id="f3200-124">Tady je ukázková třída, která obsahuje kolekce a vnořenou třídu:</span><span class="sxs-lookup"><span data-stu-id="f3200-124">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="f3200-125">Výstup JSON z serializace instance předchozího typu vypadá jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f3200-125">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="f3200-126">Výstup JSON je ve výchozím nastavení minifikovaného:</span><span class="sxs-lookup"><span data-stu-id="f3200-126">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="f3200-127">Následující příklad ukazuje stejný formát JSON (to znamená, že je poměrně vytištěn s prázdným znakem a odsazením):</span><span class="sxs-lookup"><span data-stu-id="f3200-127">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="f3200-128">Serializovat do UTF-8</span><span class="sxs-lookup"><span data-stu-id="f3200-128">Serialize to UTF-8</span></span>

<span data-ttu-id="f3200-129">Pro serializaci do UTF-8 volejte <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> metodu:</span><span class="sxs-lookup"><span data-stu-id="f3200-129">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="f3200-130"><xref:System.Text.Json.JsonSerializer.Serialize%2A> <xref:System.Text.Json.Utf8JsonWriter> K dispozici je také přetížení, které přijímá objekt.</span><span class="sxs-lookup"><span data-stu-id="f3200-130">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="f3200-131">Serializace do UTF-8 je přibližně 5-10% rychlejší než použití metod založených na řetězci.</span><span class="sxs-lookup"><span data-stu-id="f3200-131">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="f3200-132">Rozdíl je z důvodu, že bajty (jako UTF-8) není nutné převést na řetězce (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="f3200-132">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="f3200-133">Chování serializace</span><span class="sxs-lookup"><span data-stu-id="f3200-133">Serialization behavior</span></span>

* <span data-ttu-id="f3200-134">Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f3200-134">By default, all public properties are serialized.</span></span> <span data-ttu-id="f3200-135">Můžete [určit vlastnosti, které se mají vyloučit](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="f3200-135">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="f3200-136">[Výchozí kodér](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) řídí znaky jiné než ASCII, znaky citlivé na jazyk HTML v rozsahu ASCII a znaky, které musí být uvozeny podle [specifikace JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="f3200-136">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="f3200-137">Ve výchozím nastavení je JSON minifikovaného.</span><span class="sxs-lookup"><span data-stu-id="f3200-137">By default, JSON is minified.</span></span> <span data-ttu-id="f3200-138">[Kód JSON můžete v podstatě vytisknout](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="f3200-138">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="f3200-139">Ve výchozím nastavení jsou malá a velká písmena názvů JSON shodná s názvy .NET.</span><span class="sxs-lookup"><span data-stu-id="f3200-139">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="f3200-140">Můžete [přizpůsobit název a velikost písmen JSON](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="f3200-140">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="f3200-141">Byly zjištěny cyklické odkazy a byly vyvolány výjimky.</span><span class="sxs-lookup"><span data-stu-id="f3200-141">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="f3200-142">V současné době jsou pole vyloučena.</span><span class="sxs-lookup"><span data-stu-id="f3200-142">Currently, fields are excluded.</span></span>

<span data-ttu-id="f3200-143">Mezi podporované typy patří:</span><span class="sxs-lookup"><span data-stu-id="f3200-143">Supported types include:</span></span>

* <span data-ttu-id="f3200-144">Primitivní prvky .NET, které se mapují na primitivní prvky JavaScriptu, jako jsou číselné typy, řetězce a logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="f3200-144">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="f3200-145">Uživatelsky definované [prosté staré objekty CLR (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="f3200-145">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="f3200-146">Jednorozměrné a vícenásobná pole ( `ArrayName[][]` ).</span><span class="sxs-lookup"><span data-stu-id="f3200-146">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="f3200-147">`Dictionary<string,TValue>`Where `TValue` je `object` , `JsonElement` nebo POCO.</span><span class="sxs-lookup"><span data-stu-id="f3200-147">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="f3200-148">Kolekce z následujících oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="f3200-148">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="f3200-149">[Vlastní převaděče můžete implementovat](system-text-json-converters-how-to.md) pro zpracování dalších typů nebo pro poskytování funkcí, které integrované převaděče nepodporují.</span><span class="sxs-lookup"><span data-stu-id="f3200-149">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="f3200-150">Postup čtení formátu JSON do objektů .NET (deserializace)</span><span class="sxs-lookup"><span data-stu-id="f3200-150">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="f3200-151">Chcete-li provést deserializaci z řetězce nebo souboru, zavolejte <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="f3200-151">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="f3200-152">Následující příklad přečte JSON z řetězce a vytvoří instanci `WeatherForecast` třídy uvedené dříve pro [příklad serializace](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="f3200-152">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="f3200-153">Chcete-li provést deserializaci ze souboru pomocí synchronního kódu, přečtěte si soubor do řetězce, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-153">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="f3200-154">Chcete-li provést deserializaci ze souboru pomocí asynchronního kódu, zavolejte <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> metodu:</span><span class="sxs-lookup"><span data-stu-id="f3200-154">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="f3200-155">Deserializace ze znakové sady UTF-8</span><span class="sxs-lookup"><span data-stu-id="f3200-155">Deserialize from UTF-8</span></span>

<span data-ttu-id="f3200-156">Chcete-li deserializovat ze znakové sady UTF-8, zavolejte <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> přetížení, které přijímá `Utf8JsonReader` nebo `ReadOnlySpan<byte>` , jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="f3200-156">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="f3200-157">V příkladech se předpokládá, že je JSON v bajtovém poli s názvem jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="f3200-157">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="f3200-158">Chování deserializace</span><span class="sxs-lookup"><span data-stu-id="f3200-158">Deserialization behavior</span></span>

* <span data-ttu-id="f3200-159">Ve výchozím nastavení se při porovnávání názvů vlastností rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="f3200-159">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="f3200-160">Můžete [zadat nerozlišování velkých a malých písmen](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="f3200-160">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="f3200-161">Pokud JSON obsahuje hodnotu vlastnosti jen pro čtení, hodnota je ignorována a není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="f3200-161">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="f3200-162">Deserializace na odkazové typy bez bezparametrového konstruktoru není podporována.</span><span class="sxs-lookup"><span data-stu-id="f3200-162">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="f3200-163">Deserializace u neměnných objektů nebo vlastností jen pro čtení není podporována.</span><span class="sxs-lookup"><span data-stu-id="f3200-163">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="f3200-164">Ve výchozím nastavení jsou výčty podporovány jako čísla.</span><span class="sxs-lookup"><span data-stu-id="f3200-164">By default, enums are supported as numbers.</span></span> <span data-ttu-id="f3200-165">[Názvy výčtů můžete serializovat jako řetězce](#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="f3200-165">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="f3200-166">Pole nejsou podporována.</span><span class="sxs-lookup"><span data-stu-id="f3200-166">Fields aren't supported.</span></span>
* <span data-ttu-id="f3200-167">Ve výchozím nastavení komentáře nebo koncové čárky ve formátu JSON vyvolají výjimky.</span><span class="sxs-lookup"><span data-stu-id="f3200-167">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="f3200-168">Můžete [povolovat komentáře a koncové čárky](#allow-comments-and-trailing-commas).</span><span class="sxs-lookup"><span data-stu-id="f3200-168">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="f3200-169">[Výchozí maximální hloubka](xref:System.Text.Json.JsonReaderOptions.MaxDepth) je 64.</span><span class="sxs-lookup"><span data-stu-id="f3200-169">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="f3200-170">[Vlastní převaděče můžete implementovat](system-text-json-converters-how-to.md) pro poskytování funkcí, které nejsou podporované integrovanými převaděči.</span><span class="sxs-lookup"><span data-stu-id="f3200-170">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="f3200-171">Serializovat do formátovaného formátu JSON</span><span class="sxs-lookup"><span data-stu-id="f3200-171">Serialize to formatted JSON</span></span>

<span data-ttu-id="f3200-172">Pro poměrně vytisknutí výstupu JSON nastavte <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> na `true` :</span><span class="sxs-lookup"><span data-stu-id="f3200-172">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="f3200-173">Tady je příklad typu pro serializaci a poměrně tištěné výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="f3200-173">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="f3200-174">Přizpůsobení názvů a hodnot JSON</span><span class="sxs-lookup"><span data-stu-id="f3200-174">Customize JSON names and values</span></span>

<span data-ttu-id="f3200-175">Ve výchozím nastavení se názvy vlastností a klíče slovníku ve výstupu JSON nezměnily, včetně případu.</span><span class="sxs-lookup"><span data-stu-id="f3200-175">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="f3200-176">Hodnoty výčtu jsou reprezentovány jako čísla.</span><span class="sxs-lookup"><span data-stu-id="f3200-176">Enum values are represented as numbers.</span></span> <span data-ttu-id="f3200-177">V této části se dozvíte, jak:</span><span class="sxs-lookup"><span data-stu-id="f3200-177">This section explains how to:</span></span>

* [<span data-ttu-id="f3200-178">Přizpůsobení jednotlivých názvů vlastností</span><span class="sxs-lookup"><span data-stu-id="f3200-178">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="f3200-179">Převést názvy všech vlastností na velikost ve stylu CamelCase</span><span class="sxs-lookup"><span data-stu-id="f3200-179">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="f3200-180">Implementace vlastní zásady pro pojmenovávání vlastností</span><span class="sxs-lookup"><span data-stu-id="f3200-180">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="f3200-181">Převede klíče slovníku na ve stylu CamelCase případ.</span><span class="sxs-lookup"><span data-stu-id="f3200-181">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="f3200-182">Převod výčtů na řetězce a ve stylu CamelCase velikost písmen</span><span class="sxs-lookup"><span data-stu-id="f3200-182">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="f3200-183">Pro jiné scénáře, které vyžadují speciální zpracování názvů a hodnot vlastností JSON, můžete [implementovat vlastní převaděče](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="f3200-183">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="f3200-184">Přizpůsobení jednotlivých názvů vlastností</span><span class="sxs-lookup"><span data-stu-id="f3200-184">Customize individual property names</span></span>

<span data-ttu-id="f3200-185">Chcete-li nastavit název jednotlivých vlastností, použijte atribut [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) .</span><span class="sxs-lookup"><span data-stu-id="f3200-185">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="f3200-186">Tady je příklad typu k serializaci a výslednému formátu JSON:</span><span class="sxs-lookup"><span data-stu-id="f3200-186">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="f3200-187">Název vlastnosti nastavený tímto atributem:</span><span class="sxs-lookup"><span data-stu-id="f3200-187">The property name set by this attribute:</span></span>

* <span data-ttu-id="f3200-188">Platí v obou směrech pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="f3200-188">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="f3200-189">Má přednost před zásadami pro pojmenovávání vlastností.</span><span class="sxs-lookup"><span data-stu-id="f3200-189">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="f3200-190">Pro všechny názvy vlastností JSON použijte ve stylu CamelCase Case</span><span class="sxs-lookup"><span data-stu-id="f3200-190">Use camel case for all JSON property names</span></span>

<span data-ttu-id="f3200-191">Pro použití ve stylu CamelCase pro všechny názvy vlastností JSON nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> na `JsonNamingPolicy.CamelCase` , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-191">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="f3200-192">Tady je příklad třídy pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="f3200-192">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="f3200-193">Zásada pro pojmenování vlastností případu ve stylu CamelCase:</span><span class="sxs-lookup"><span data-stu-id="f3200-193">The camel case property naming policy:</span></span>

* <span data-ttu-id="f3200-194">Platí pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="f3200-194">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="f3200-195">Je potlačen `[JsonPropertyName]` atributy.</span><span class="sxs-lookup"><span data-stu-id="f3200-195">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="f3200-196">To je důvod, proč název vlastnosti JSON `Wind` v příkladu není ve stylu CamelCase Case.</span><span class="sxs-lookup"><span data-stu-id="f3200-196">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="f3200-197">Použít vlastní zásady pojmenování vlastností JSON</span><span class="sxs-lookup"><span data-stu-id="f3200-197">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="f3200-198">Chcete-li použít vlastní zásadu pojmenovávání vlastností JSON, vytvořte třídu, která je odvozena z třídy <xref:System.Text.Json.JsonNamingPolicy> , a přepište <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> metodu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-198">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="f3200-199">Pak nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> vlastnost na instanci třídy zásad pojmenování:</span><span class="sxs-lookup"><span data-stu-id="f3200-199">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="f3200-200">Tady je příklad třídy pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="f3200-200">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="f3200-201">Zásady pojmenování vlastností JSON:</span><span class="sxs-lookup"><span data-stu-id="f3200-201">The JSON property naming policy:</span></span>

* <span data-ttu-id="f3200-202">Platí pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="f3200-202">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="f3200-203">Je potlačen `[JsonPropertyName]` atributy.</span><span class="sxs-lookup"><span data-stu-id="f3200-203">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="f3200-204">To je důvod, proč název vlastnosti JSON `Wind` v příkladu není velká písmena.</span><span class="sxs-lookup"><span data-stu-id="f3200-204">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="f3200-205">Klíče slovníku případů ve stylu CamelCase</span><span class="sxs-lookup"><span data-stu-id="f3200-205">Camel case dictionary keys</span></span>

<span data-ttu-id="f3200-206">Pokud je vlastnost objektu, který má být serializován `Dictionary<string,TValue>` , typu, `string` lze klíče převést na ve stylu CamelCase případ.</span><span class="sxs-lookup"><span data-stu-id="f3200-206">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="f3200-207">To provedete tak, že nastavíte <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> na `JsonNamingPolicy.CamelCase` , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-207">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="f3200-208">Serializace objektu se slovníkem s názvem `TemperatureRanges` , který má páry klíč-hodnota `"ColdMinTemp", 20` a `"HotMinTemp", 40` výsledkem by byl výstup JSON jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-208">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="f3200-209">Zásady pro pojmenovávání ve stylu CamelCase pro klíče slovníku se vztahují pouze na serializaci.</span><span class="sxs-lookup"><span data-stu-id="f3200-209">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="f3200-210">Při deserializaci slovníku budou klíče odpovídat souboru JSON, i když zadáte `JsonNamingPolicy.CamelCase` pro `DictionaryKeyPolicy` .</span><span class="sxs-lookup"><span data-stu-id="f3200-210">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="f3200-211">Výčty jako řetězce</span><span class="sxs-lookup"><span data-stu-id="f3200-211">Enums as strings</span></span>

<span data-ttu-id="f3200-212">Ve výchozím nastavení jsou výčty serializovány jako čísla.</span><span class="sxs-lookup"><span data-stu-id="f3200-212">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="f3200-213">Chcete-li serializovat názvy výčtu jako řetězce, použijte <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .</span><span class="sxs-lookup"><span data-stu-id="f3200-213">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="f3200-214">Předpokládejme například, že potřebujete serializovat následující třídu, která má výčet:</span><span class="sxs-lookup"><span data-stu-id="f3200-214">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="f3200-215">Pokud je souhrn `Hot` , ve výchozím nastavení má serializovaný formát JSON číselnou hodnotu 3:</span><span class="sxs-lookup"><span data-stu-id="f3200-215">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="f3200-216">Následující vzorový kód místo číselných hodnot serializace názvy výčtu a převede názvy na ve stylu CamelCase případ:</span><span class="sxs-lookup"><span data-stu-id="f3200-216">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="f3200-217">Výsledný kód JSON vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-217">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="f3200-218">Názvy řetězců výčtu lze deserializovat také, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-218">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="f3200-219">Vyloučit vlastnosti ze serializace</span><span class="sxs-lookup"><span data-stu-id="f3200-219">Exclude properties from serialization</span></span>

<span data-ttu-id="f3200-220">Ve výchozím nastavení jsou serializovány všechny veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f3200-220">By default, all public properties are serialized.</span></span> <span data-ttu-id="f3200-221">Pokud nechcete, aby se některé z nich zobrazovaly ve výstupu JSON, máte několik možností.</span><span class="sxs-lookup"><span data-stu-id="f3200-221">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="f3200-222">V této části se dozvíte, jak vyloučit:</span><span class="sxs-lookup"><span data-stu-id="f3200-222">This section explains how to exclude:</span></span>

* [<span data-ttu-id="f3200-223">Jednotlivé vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f3200-223">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="f3200-224">Všechny vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f3200-224">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="f3200-225">Všechny vlastnosti s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="f3200-225">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="f3200-226">Vyloučení individuálních vlastností</span><span class="sxs-lookup"><span data-stu-id="f3200-226">Exclude individual properties</span></span>

<span data-ttu-id="f3200-227">Chcete-li ignorovat jednotlivé vlastnosti, použijte atribut [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) .</span><span class="sxs-lookup"><span data-stu-id="f3200-227">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="f3200-228">Tady je příklad typu pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="f3200-228">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="f3200-229">Vyloučit všechny vlastnosti jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f3200-229">Exclude all read-only properties</span></span>

<span data-ttu-id="f3200-230">Vlastnost je jen pro čtení, pokud obsahuje veřejnou metodu getter, ale ne veřejnou metodu setter.</span><span class="sxs-lookup"><span data-stu-id="f3200-230">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="f3200-231">Chcete-li vyloučit všechny vlastnosti jen pro čtení, nastavte na <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> `true` , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-231">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="f3200-232">Tady je příklad typu pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="f3200-232">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="f3200-233">Tato možnost se vztahuje pouze na serializaci.</span><span class="sxs-lookup"><span data-stu-id="f3200-233">This option applies only to serialization.</span></span> <span data-ttu-id="f3200-234">Během deserializace jsou vlastnosti jen pro čtení ve výchozím nastavení ignorovány.</span><span class="sxs-lookup"><span data-stu-id="f3200-234">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="f3200-235">Vyloučit všechny vlastnosti hodnoty null</span><span class="sxs-lookup"><span data-stu-id="f3200-235">Exclude all null value properties</span></span>

<span data-ttu-id="f3200-236">Chcete-li vyloučit všechny vlastnosti hodnoty null, nastavte <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> vlastnost na hodnotu `true` , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-236">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="f3200-237">Zde je příklad objektu pro serializaci a výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="f3200-237">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="f3200-238">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="f3200-238">Property</span></span> |<span data-ttu-id="f3200-239">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f3200-239">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="f3200-240">Datum</span><span class="sxs-lookup"><span data-stu-id="f3200-240">Date</span></span>    | <span data-ttu-id="f3200-241">8/1/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="f3200-241">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="f3200-242">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="f3200-242">TemperatureCelsius</span></span>| <span data-ttu-id="f3200-243">25</span><span class="sxs-lookup"><span data-stu-id="f3200-243">25</span></span> |
| <span data-ttu-id="f3200-244">Souhrn</span><span class="sxs-lookup"><span data-stu-id="f3200-244">Summary</span></span>| <span data-ttu-id="f3200-245">null</span><span class="sxs-lookup"><span data-stu-id="f3200-245">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="f3200-246">Toto nastavení platí pro serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="f3200-246">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="f3200-247">Informace o jeho vlivu na deserializaci naleznete v tématu [Ignore null Při deserializaci](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="f3200-247">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="f3200-248">Přizpůsobení kódování znaků</span><span class="sxs-lookup"><span data-stu-id="f3200-248">Customize character encoding</span></span>

<span data-ttu-id="f3200-249">Ve výchozím nastavení serializátor řídí všechny znaky jiné než ASCII.</span><span class="sxs-lookup"><span data-stu-id="f3200-249">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="f3200-250">To znamená, že je nahradí `\uxxxx` `xxxx` znakem, kde je kód Unicode znaku.</span><span class="sxs-lookup"><span data-stu-id="f3200-250">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="f3200-251">Například pokud `Summary` je vlastnost nastavena na жаркоa v cyrilici, `WeatherForecast` objekt je serializován, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-251">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="f3200-252">Serializovat znakové sady jazyků</span><span class="sxs-lookup"><span data-stu-id="f3200-252">Serialize language character sets</span></span>

<span data-ttu-id="f3200-253">Chcete-li serializovat znakové sady jednoho nebo více jazyků bez uvozovacího znaku, určete [Rozsah znaků Unicode](xref:System.Text.Unicode.UnicodeRanges) při vytváření instance <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-253">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="f3200-254">Tento kód neřídí cyrilici ani řecké znaky.</span><span class="sxs-lookup"><span data-stu-id="f3200-254">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="f3200-255">Pokud `Summary` je vlastnost nastavena na жаркоa v cyrilici, `WeatherForecast` objekt je serializován, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-255">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="f3200-256">Chcete-li serializovat všechny jazykové sady bez použití uvozovacího, použijte <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f3200-256">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="f3200-257">Serializovat konkrétní znaky</span><span class="sxs-lookup"><span data-stu-id="f3200-257">Serialize specific characters</span></span>

<span data-ttu-id="f3200-258">Alternativou je zadání jednotlivých znaků, které chcete použít, bez nutnosti řídicích znaků.</span><span class="sxs-lookup"><span data-stu-id="f3200-258">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="f3200-259">Následující příklad serializace pouze prvních dvou znaků жарко:</span><span class="sxs-lookup"><span data-stu-id="f3200-259">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="f3200-260">Zde je příklad kódu JSON vytvořeného předchozím kódem:</span><span class="sxs-lookup"><span data-stu-id="f3200-260">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="f3200-261">Serializovat všechny znaky</span><span class="sxs-lookup"><span data-stu-id="f3200-261">Serialize all characters</span></span>

<span data-ttu-id="f3200-262">K minimalizaci řídicích znaků, které můžete použít <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType> , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-262">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="f3200-263">V porovnání s výchozím kodérem `UnsafeRelaxedJsonEscaping` je kodér více opravňujícím, aby bylo možné předávat znaky bez řídicích znaků:</span><span class="sxs-lookup"><span data-stu-id="f3200-263">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="f3200-264">Neřídí znaky citlivé na HTML `<` , například, `>` , `&` a `'` .</span><span class="sxs-lookup"><span data-stu-id="f3200-264">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="f3200-265">Nenabízí žádné další ochrany proti důkladné ochraně před útoky XSS nebo informací, jako jsou ty, které by mohly vzniknout ze strany klienta a *serveru na znakovou sadu.*</span><span class="sxs-lookup"><span data-stu-id="f3200-265">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="f3200-266">Nezabezpečený kodér používejte pouze v případě, že je známo, že klient bude interpretovat výslednou datovou část jako JSON kódovaný v kódování UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f3200-266">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="f3200-267">Můžete ho například použít, pokud server posílá hlavičku odpovědi `Content-Type: application/json; charset=utf-8` .</span><span class="sxs-lookup"><span data-stu-id="f3200-267">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="f3200-268">Nikdy nepovolujte, aby se nezpracovaný `UnsafeRelaxedJsonEscaping` výstup vygeneroval do stránky HTML nebo `<script>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f3200-268">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="f3200-269">Serializovat vlastnosti odvozených tříd</span><span class="sxs-lookup"><span data-stu-id="f3200-269">Serialize properties of derived classes</span></span>

<span data-ttu-id="f3200-270">Serializace hierarchie polymorfního typu není podporována.</span><span class="sxs-lookup"><span data-stu-id="f3200-270">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="f3200-271">Například pokud je vlastnost definována jako rozhraní nebo abstraktní třída, jsou serializovány pouze vlastnosti definované v rozhraní nebo abstraktní třídě, a to i v případě, že typ modulu runtime má další vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f3200-271">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="f3200-272">Výjimky z tohoto chování jsou vysvětleny v této části.</span><span class="sxs-lookup"><span data-stu-id="f3200-272">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="f3200-273">Předpokládejme například, že máte `WeatherForecast` třídu a odvozenou třídu `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="f3200-273">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="f3200-274">A Předpokládejme, že argument typu `Serialize` metody v době kompilace je `WeatherForecast` :</span><span class="sxs-lookup"><span data-stu-id="f3200-274">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="f3200-275">V tomto scénáři není `WindSpeed` Vlastnost serializována i v případě, že `weatherForecast` objekt je ve skutečnosti `WeatherForecastDerived` objekt.</span><span class="sxs-lookup"><span data-stu-id="f3200-275">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="f3200-276">Serializovat se budou jenom vlastnosti základní třídy:</span><span class="sxs-lookup"><span data-stu-id="f3200-276">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="f3200-277">Toto chování je určeno k tomu, aby se zabránilo náhodnému úniku dat v odvozeném typu vytvořeném modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="f3200-277">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="f3200-278">Chcete-li serializovat vlastnosti odvozeného typu v předchozím příkladu, použijte jeden z následujících přístupů:</span><span class="sxs-lookup"><span data-stu-id="f3200-278">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="f3200-279">Zavolejte přetížení <xref:System.Text.Json.JsonSerializer.Serialize%2A> , které umožňuje určit typ za běhu:</span><span class="sxs-lookup"><span data-stu-id="f3200-279">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="f3200-280">Deklarujte objekt, který se má serializovat jako `object` .</span><span class="sxs-lookup"><span data-stu-id="f3200-280">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="f3200-281">V předchozím ukázkovém scénáři oba přístupy způsobí, že `WindSpeed` vlastnost bude obsažena ve výstupu JSON:</span><span class="sxs-lookup"><span data-stu-id="f3200-281">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="f3200-282">Tyto přístupy poskytují polymorfní serializaci pouze pro kořenový objekt, který má být serializován, nikoli pro vlastnosti daného kořenového objektu.</span><span class="sxs-lookup"><span data-stu-id="f3200-282">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="f3200-283">Můžete získat polymorfní serializaci pro objekty nižší úrovně, pokud je definujete jako typ `object` .</span><span class="sxs-lookup"><span data-stu-id="f3200-283">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="f3200-284">Předpokládejme například, že vaše `WeatherForecast` Třída má vlastnost s názvem `PreviousForecast` , která může být definována jako typ `WeatherForecast` nebo `object` :</span><span class="sxs-lookup"><span data-stu-id="f3200-284">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="f3200-285">Pokud `PreviousForecast` vlastnost obsahuje instanci `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="f3200-285">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="f3200-286">Výstup JSON ze serializace `WeatherForecastWithPrevious` **neobsahuje** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="f3200-286">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="f3200-287">Výstup JSON ze serializace `WeatherForecastWithPreviousAsObject` **obsahuje** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="f3200-287">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="f3200-288">Pro serializaci `WeatherForecastWithPreviousAsObject` není nutné volat `Serialize<object>` nebo `GetType` , protože kořenový objekt není ten, který může být odvozeného typu.</span><span class="sxs-lookup"><span data-stu-id="f3200-288">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="f3200-289">Následující příklad kódu nevolá `Serialize<object>` nebo `GetType` :</span><span class="sxs-lookup"><span data-stu-id="f3200-289">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="f3200-290">Předchozí kód správně serializace `WeatherForecastWithPreviousAsObject` :</span><span class="sxs-lookup"><span data-stu-id="f3200-290">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="f3200-291">Stejný přístup k definování vlastností jako `object` funguje s rozhraními.</span><span class="sxs-lookup"><span data-stu-id="f3200-291">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="f3200-292">Předpokládejme, že máte následující rozhraní a implementaci a chcete serializovat třídu s vlastnostmi, které obsahují instance implementace:</span><span class="sxs-lookup"><span data-stu-id="f3200-292">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

<span data-ttu-id="f3200-293">Při serializaci instance je `Forecasts` `Tuesday` zobrazena pouze `WindSpeed` vlastnost, protože `Tuesday` je definována jako `object` :</span><span class="sxs-lookup"><span data-stu-id="f3200-293">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="f3200-294">Následující příklad ukazuje kód JSON, který je výsledkem předchozího kódu:</span><span class="sxs-lookup"><span data-stu-id="f3200-294">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="f3200-295">Další informace o polymorfní **serializaci**a informace o **deserializaci**naleznete v tématu [How to migruje from Newtonsoft. JSON to System. text. JSON](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="f3200-295">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="f3200-296">Povolí komentáře a koncové čárky.</span><span class="sxs-lookup"><span data-stu-id="f3200-296">Allow comments and trailing commas</span></span>

<span data-ttu-id="f3200-297">Ve výchozím nastavení se komentáře a koncové čárky ve formátu JSON nepovolují.</span><span class="sxs-lookup"><span data-stu-id="f3200-297">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="f3200-298">Chcete-li ve formátu JSON dovolit komentáře, nastavte <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> vlastnost na hodnotu `JsonCommentHandling.Skip` .</span><span class="sxs-lookup"><span data-stu-id="f3200-298">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="f3200-299">A chcete-li použít koncové čárky, nastavte <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> vlastnost na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="f3200-299">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="f3200-300">Následující příklad ukazuje, jak je možné:</span><span class="sxs-lookup"><span data-stu-id="f3200-300">The following example shows how to allow both:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="f3200-301">Tady je příklad JSON s komentáři a koncovou čárkou:</span><span class="sxs-lookup"><span data-stu-id="f3200-301">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="f3200-302">Porovnávání vlastností bez rozlišení velkých a malých písmen</span><span class="sxs-lookup"><span data-stu-id="f3200-302">Case-insensitive property matching</span></span>

<span data-ttu-id="f3200-303">Ve výchozím nastavení deserializace hledá název vlastnosti rozlišující velká a malá písmena mezi vlastnostmi JSON a cílovým objektem.</span><span class="sxs-lookup"><span data-stu-id="f3200-303">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="f3200-304">Chcete-li toto chování změnit, nastavte <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> na `true` :</span><span class="sxs-lookup"><span data-stu-id="f3200-304">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="f3200-305">Tady je příklad JSON s názvy vlastností Case ve stylu CamelCase.</span><span class="sxs-lookup"><span data-stu-id="f3200-305">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="f3200-306">Lze deserializovat do následujícího typu, který má názvy vlastností Case typu Pascal.</span><span class="sxs-lookup"><span data-stu-id="f3200-306">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="f3200-307">Přetečení JSON popisovače</span><span class="sxs-lookup"><span data-stu-id="f3200-307">Handle overflow JSON</span></span>

<span data-ttu-id="f3200-308">Při deserializaci můžete přijímat data ve formátu JSON, která nejsou reprezentovaná vlastnostmi cílového typu.</span><span class="sxs-lookup"><span data-stu-id="f3200-308">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="f3200-309">Předpokládejme například, že váš cílový typ je:</span><span class="sxs-lookup"><span data-stu-id="f3200-309">For example, suppose your target type is this:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="f3200-310">A JSON, který se má deserializovat, je:</span><span class="sxs-lookup"><span data-stu-id="f3200-310">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="f3200-311">Pokud deserializaci kódu JSON zobrazeného na zobrazeném typu, `DatesAvailable` vlastnosti a se `SummaryWords` nikde k přechodu a jsou ztraceny.</span><span class="sxs-lookup"><span data-stu-id="f3200-311">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="f3200-312">Chcete-li zachytit další data, jako jsou tyto vlastnosti, použijte atribut [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) na vlastnost typu `Dictionary<string,object>` nebo `Dictionary<string,JsonElement>` :</span><span class="sxs-lookup"><span data-stu-id="f3200-312">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="f3200-313">Při deserializaci formátu JSON zobrazeného dříve do tohoto ukázkového typu se data dalších dat stávají páry klíč-hodnota `ExtensionData` vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f3200-313">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="f3200-314">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="f3200-314">Property</span></span> |<span data-ttu-id="f3200-315">Hodnota</span><span class="sxs-lookup"><span data-stu-id="f3200-315">Value</span></span>  |<span data-ttu-id="f3200-316">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3200-316">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="f3200-317">Datum</span><span class="sxs-lookup"><span data-stu-id="f3200-317">Date</span></span>    | <span data-ttu-id="f3200-318">8/1/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="f3200-318">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="f3200-319">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="f3200-319">TemperatureCelsius</span></span>| <span data-ttu-id="f3200-320">0</span><span class="sxs-lookup"><span data-stu-id="f3200-320">0</span></span> | <span data-ttu-id="f3200-321">Neshoda malých a velkých písmen ( `temperatureCelsius` ve formátu JSON), takže vlastnost není nastavena.</span><span class="sxs-lookup"><span data-stu-id="f3200-321">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="f3200-322">Souhrn</span><span class="sxs-lookup"><span data-stu-id="f3200-322">Summary</span></span> | <span data-ttu-id="f3200-323">Hot</span><span class="sxs-lookup"><span data-stu-id="f3200-323">Hot</span></span> ||
| <span data-ttu-id="f3200-324">ExtensionData –</span><span class="sxs-lookup"><span data-stu-id="f3200-324">ExtensionData</span></span> | <span data-ttu-id="f3200-325">temperatureCelsius: 25</span><span class="sxs-lookup"><span data-stu-id="f3200-325">temperatureCelsius: 25</span></span> |<span data-ttu-id="f3200-326">Vzhledem k tomu, že se neshoduje velká a malá písmena, je tato vlastnost JSON extra a ve slovníku se stala dvojicí klíč-hodnota.</span><span class="sxs-lookup"><span data-stu-id="f3200-326">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="f3200-327">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="f3200-327">DatesAvailable:</span></span><br>  <span data-ttu-id="f3200-328">8/1/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="f3200-328">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="f3200-329">8/2/2019 12:00:00 DOP. 07:00</span><span class="sxs-lookup"><span data-stu-id="f3200-329">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="f3200-330">Vlastnost extra z formátu JSON se stávají dvojicí klíč-hodnota s polem jako objektem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f3200-330">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="f3200-331">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="f3200-331">SummaryWords:</span></span><br><span data-ttu-id="f3200-332">Cool</span><span class="sxs-lookup"><span data-stu-id="f3200-332">Cool</span></span><br><span data-ttu-id="f3200-333">Vítr</span><span class="sxs-lookup"><span data-stu-id="f3200-333">Windy</span></span><br><span data-ttu-id="f3200-334">Humid</span><span class="sxs-lookup"><span data-stu-id="f3200-334">Humid</span></span> |<span data-ttu-id="f3200-335">Vlastnost extra z formátu JSON se stávají dvojicí klíč-hodnota s polem jako objektem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f3200-335">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="f3200-336">Při serializaci cílového objektu se dvojice hodnoty klíče dat rozšíření stanou vlastnostmi JSON stejně, jako kdyby byly ve vstupním formátu JSON:</span><span class="sxs-lookup"><span data-stu-id="f3200-336">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="f3200-337">Všimněte si, že `ExtensionData` název vlastnosti se ve formátu JSON nezobrazuje.</span><span class="sxs-lookup"><span data-stu-id="f3200-337">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="f3200-338">Díky tomuto chování může JSON vytvořit zpáteční cestu, aniž by došlo ke ztrátě dalších dat, která by jinak nebyla deserializována.</span><span class="sxs-lookup"><span data-stu-id="f3200-338">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="f3200-339">Při deserializaci ignorovat hodnotu null</span><span class="sxs-lookup"><span data-stu-id="f3200-339">Ignore null when deserializing</span></span>

<span data-ttu-id="f3200-340">Ve výchozím nastavení platí, že pokud je vlastnost ve formátu JSON null, odpovídající vlastnost v cílovém objektu je nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="f3200-340">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="f3200-341">V některých scénářích může cílová vlastnost mít výchozí hodnotu a nechcete, aby hodnota null přepsala výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f3200-341">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="f3200-342">Předpokládejme například, že následující kód představuje cílový objekt:</span><span class="sxs-lookup"><span data-stu-id="f3200-342">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="f3200-343">A Předpokládejme, že následující kód JSON je deserializovaný:</span><span class="sxs-lookup"><span data-stu-id="f3200-343">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="f3200-344">Po deserializaci má `Summary` vlastnost `WeatherForecastWithDefault` objektu hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="f3200-344">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="f3200-345">Chcete-li toto chování změnit, nastavte <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> na hodnotu `true` , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-345">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="f3200-346">S touto možností `Summary` `WeatherForecastWithDefault` je vlastnost objektu výchozí hodnotou "No Summary" po deserializaci.</span><span class="sxs-lookup"><span data-stu-id="f3200-346">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="f3200-347">Hodnoty null ve formátu JSON jsou ignorovány pouze v případě, že jsou platné.</span><span class="sxs-lookup"><span data-stu-id="f3200-347">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="f3200-348">Hodnoty null pro typy hodnot, které neumožňují hodnotu null, způsobují výjimky.</span><span class="sxs-lookup"><span data-stu-id="f3200-348">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="f3200-349">Utf8JsonReader, Utf8JsonWriter a JsonDocument</span><span class="sxs-lookup"><span data-stu-id="f3200-349">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="f3200-350"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>je vysoce výkonné, nízké přidělení, jen pro čtení pro text JSON s kódováním UTF-8, načtené z `ReadOnlySpan<byte>` nebo `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="f3200-350"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="f3200-351">`Utf8JsonReader`Je typ nižší úrovně, který lze použít k vytvoření vlastních analyzátorů a deserializace.</span><span class="sxs-lookup"><span data-stu-id="f3200-351">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="f3200-352"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>Metoda používá `Utf8JsonReader` v rámci pokrývání.</span><span class="sxs-lookup"><span data-stu-id="f3200-352">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="f3200-353"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>je vysoce výkonný způsob, jak psát text JSON kódovaný v kódování UTF-8 ze běžných typů .NET `String` , jako jsou, `Int32` a `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="f3200-353"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="f3200-354">Zapisovač je typ nižší úrovně, který lze použít k vytvoření vlastních serializátorů.</span><span class="sxs-lookup"><span data-stu-id="f3200-354">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="f3200-355"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>Metoda používá `Utf8JsonWriter` v rámci pokrývání.</span><span class="sxs-lookup"><span data-stu-id="f3200-355">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="f3200-356"><xref:System.Text.Json.JsonDocument?displayProperty=fullName>poskytuje možnost sestavit model DOM (Document Object Model) (DOM) jen pro čtení pomocí `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="f3200-356"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="f3200-357">Model DOM poskytuje náhodný přístup k datům v datové části JSON.</span><span class="sxs-lookup"><span data-stu-id="f3200-357">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="f3200-358">K prvkům JSON, které tvoří datovou část, lze přistupovat prostřednictvím <xref:System.Text.Json.JsonElement> typu.</span><span class="sxs-lookup"><span data-stu-id="f3200-358">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="f3200-359">`JsonElement`Typ poskytuje enumerátory polí a objektů spolu s rozhraními API pro převod textu JSON na běžné typy .NET.</span><span class="sxs-lookup"><span data-stu-id="f3200-359">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="f3200-360">`JsonDocument`zpřístupňuje <xref:System.Text.Json.JsonDocument.RootElement> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f3200-360">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="f3200-361">Následující části ukazují, jak používat tyto nástroje pro čtení a zápis JSON.</span><span class="sxs-lookup"><span data-stu-id="f3200-361">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="f3200-362">Použití JsonDocument pro přístup k datům</span><span class="sxs-lookup"><span data-stu-id="f3200-362">Use JsonDocument for access to data</span></span>

<span data-ttu-id="f3200-363">Následující příklad ukazuje, jak použít <xref:System.Text.Json.JsonDocument> třídu pro náhodný přístup k datům v řetězci JSON:</span><span class="sxs-lookup"><span data-stu-id="f3200-363">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="f3200-364">Předcházející kód:</span><span class="sxs-lookup"><span data-stu-id="f3200-364">The preceding code:</span></span>

* <span data-ttu-id="f3200-365">Předpokládá, že se JSON, který se má analyzovat, nachází v řetězci s názvem `jsonString` .</span><span class="sxs-lookup"><span data-stu-id="f3200-365">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="f3200-366">Vypočítá průměrnou třídu pro objekty v `Students` poli, které mají `Grade` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f3200-366">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="f3200-367">Přiřadí výchozí stupeň 70 pro studenty, kteří nemají třídu.</span><span class="sxs-lookup"><span data-stu-id="f3200-367">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="f3200-368">Spočítá studenty zvýšením `count` proměnné s každou iterací.</span><span class="sxs-lookup"><span data-stu-id="f3200-368">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="f3200-369">Alternativou je volání <xref:System.Text.Json.JsonElement.GetArrayLength%2A> , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f3200-369">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="f3200-370">Zde je příklad kódu JSON, který tento kód zpracovává:</span><span class="sxs-lookup"><span data-stu-id="f3200-370">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="f3200-371">Zápis JSON pomocí JsonDocument</span><span class="sxs-lookup"><span data-stu-id="f3200-371">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="f3200-372">Následující příklad ukazuje, jak zapsat JSON z <xref:System.Text.Json.JsonDocument> :</span><span class="sxs-lookup"><span data-stu-id="f3200-372">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="f3200-373">Předcházející kód:</span><span class="sxs-lookup"><span data-stu-id="f3200-373">The preceding code:</span></span>

* <span data-ttu-id="f3200-374">Přečte soubor JSON, načte data do a `JsonDocument` zapisuje do souboru formát JSON s formátováním (poměrně vytištěného).</span><span class="sxs-lookup"><span data-stu-id="f3200-374">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="f3200-375">Používá <xref:System.Text.Json.JsonDocumentOptions> se k určení, že komentáře ve vstupním JSON jsou povolené, ale ignorují se.</span><span class="sxs-lookup"><span data-stu-id="f3200-375">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="f3200-376">Po dokončení volání do <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> zapisovače.</span><span class="sxs-lookup"><span data-stu-id="f3200-376">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="f3200-377">Alternativou je umožnit zapisovači AutoFlush při jeho uvolnění.</span><span class="sxs-lookup"><span data-stu-id="f3200-377">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="f3200-378">Tady je příklad vstupu JSON, který se má zpracovat v příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="f3200-378">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

<span data-ttu-id="f3200-379">Výsledkem je následující poměrně tištěný výstup JSON:</span><span class="sxs-lookup"><span data-stu-id="f3200-379">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="f3200-380">Použití Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="f3200-380">Use Utf8JsonWriter</span></span>

<span data-ttu-id="f3200-381">Následující příklad ukazuje, jak použít <xref:System.Text.Json.Utf8JsonWriter> třídu:</span><span class="sxs-lookup"><span data-stu-id="f3200-381">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="f3200-382">Použití Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="f3200-382">Use Utf8JsonReader</span></span>

<span data-ttu-id="f3200-383">Následující příklad ukazuje, jak použít <xref:System.Text.Json.Utf8JsonReader> třídu:</span><span class="sxs-lookup"><span data-stu-id="f3200-383">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="f3200-384">Předchozí kód předpokládá, že `jsonUtf8` proměnná je bajtové pole, které obsahuje platný kód JSON kódovaný jako UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f3200-384">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="f3200-385">Filtrování dat pomocí Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="f3200-385">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="f3200-386">Následující příklad ukazuje, jak číst soubor synchronně a vyhledat hodnotu:</span><span class="sxs-lookup"><span data-stu-id="f3200-386">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="f3200-387">Předcházející kód:</span><span class="sxs-lookup"><span data-stu-id="f3200-387">The preceding code:</span></span>

* <span data-ttu-id="f3200-388">Předpokládá, že JSON obsahuje pole objektů a každý objekt může obsahovat vlastnost Name typu String.</span><span class="sxs-lookup"><span data-stu-id="f3200-388">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="f3200-389">Spočítá hodnoty vlastností Objects a Name, které končí na "University".</span><span class="sxs-lookup"><span data-stu-id="f3200-389">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="f3200-390">Předpokládá, že soubor je kódovaný jako UTF-16 a překóduje ho do UTF-8.</span><span class="sxs-lookup"><span data-stu-id="f3200-390">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="f3200-391">Soubor kódovaný jako UTF-8 lze číst přímo do a `ReadOnlySpan<byte>` pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="f3200-391">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="f3200-392">Pokud soubor obsahuje znak pořadí bajtů UTF-8 (BOM), odeberte ho před předáním bajtů do `Utf8JsonReader` , protože čtecí modul očekává text.</span><span class="sxs-lookup"><span data-stu-id="f3200-392">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="f3200-393">V opačném případě se kusovník považuje za neplatný kód JSON a čtenář vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="f3200-393">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="f3200-394">Zde je ukázka JSON, kterou může předchozí kód přečíst.</span><span class="sxs-lookup"><span data-stu-id="f3200-394">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="f3200-395">Výsledná Souhrnná zpráva je "2 z čtvrtého" má názvy, které končí na "University" ":</span><span class="sxs-lookup"><span data-stu-id="f3200-395">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a><span data-ttu-id="f3200-396">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="f3200-396">Additional resources</span></span>

* <span data-ttu-id="f3200-397">[System.Text.JsonPřehled](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="f3200-397">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* [<span data-ttu-id="f3200-398">Postup zápisu vlastních převaděčů</span><span class="sxs-lookup"><span data-stu-id="f3200-398">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="f3200-399">[Postup migrace zNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="f3200-399">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="f3200-400">[Podpora DateTime a DateTimeOffset vSystem.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="f3200-400">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="f3200-401">[System.Text.JsonReference k rozhraní API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="f3200-401">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
