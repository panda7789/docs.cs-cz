---
title: Podpora DateTime a DateTimeOffset v System.Text.Json
description: Přehled způsobu, jakým jsou typy DateTime a DateTimeOffset podporovány v knihovně System. text. JSON.
ms.technology: dotnet-standard
author: layomia
ms.author: laakinri
ms.date: 07/22/2019
helpviewer_keywords:
- JSON, Serializer, Utf8
- JSON DateTime, JSON DateTimeOffset
- DateTime, DateTimeOffset
- JsonSerializer, Utf8JsonReader, Utf8JsonWriter, JsonElement, JsonDocument
- JSON Serializer, JSON Reader, JSON Writer
- Converter, JSON Converter, DateTime Converter
- ISO, ISO 8601, ISO 8601-1:2019
ms.openlocfilehash: 5bff01b10b2bdea4fdcfee86e348c47f44d50103
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374480"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a><span data-ttu-id="5e755-103">Podpora DateTime a DateTimeOffset v System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="5e755-103">DateTime and DateTimeOffset support in System.Text.Json</span></span>

<span data-ttu-id="5e755-104">Knihovna System. text. JSON analyzuje a zapisuje <xref:System.DateTime> <xref:System.DateTimeOffset> a hodnotuje hodnoty podle rozšířeného profilu ISO 8601:-2019.</span><span class="sxs-lookup"><span data-stu-id="5e755-104">The System.Text.Json library parses and writes <xref:System.DateTime> and <xref:System.DateTimeOffset> values according to the ISO 8601:-2019 extended profile.</span></span>
<span data-ttu-id="5e755-105">[Převaděče](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) poskytují vlastní podporu pro serializaci a deserializaci <xref:System.Text.Json.JsonSerializer>pomocí.</span><span class="sxs-lookup"><span data-stu-id="5e755-105">[Converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) provide custom support for serializing and deserializing with <xref:System.Text.Json.JsonSerializer>.</span></span>

## <a name="support-for-the-iso-8601-12019-format"></a><span data-ttu-id="5e755-106">Podpora formátu ISO 8601-1:2019</span><span class="sxs-lookup"><span data-stu-id="5e755-106">Support for the ISO 8601-1:2019 format</span></span>

<span data-ttu-id="5e755-107"><xref:System.DateTime> Typy <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, a<xref:System.Text.Json.Utf8JsonWriter> <xref:System.DateTimeOffset> analyzují a zapisují a zapisují text v závislosti na rozšířeném profilu formátu ISO 8601-1:2019, například 2019-07-26T16 <xref:System.Text.Json.JsonElement> : 59:57-05:00.</span><span class="sxs-lookup"><span data-stu-id="5e755-107">The <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>, and <xref:System.Text.Json.JsonElement> types parse and write <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations according to the extended profile of the ISO 8601-1:2019 format; for example, 2019-07-26T16:59:57-05:00.</span></span>

<span data-ttu-id="5e755-108"><xref:System.DateTime>a <xref:System.DateTimeOffset> data lze serializovat pomocí <xref:System.Text.Json.JsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="5e755-108"><xref:System.DateTime> and <xref:System.DateTimeOffset> data can be serialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/serializing-with-jsonserializer.cs)]

<span data-ttu-id="5e755-109">Lze je také deserializovat pomocí <xref:System.Text.Json.JsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="5e755-109">They can also be deserialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-valid.cs)]

<span data-ttu-id="5e755-110">S výchozími možnostmi <xref:System.DateTime> musí <xref:System.DateTimeOffset> být vstupní a textové reprezentace v souladu s rozšířeným profilem ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="5e755-110">With default options, input <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations must conform to the extended ISO 8601-1:2019 profile.</span></span>
<span data-ttu-id="5e755-111">Pokus o rekonstrukci reprezentace, která není v souladu s profilem, by způsobil <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonException>vyvolání:</span><span class="sxs-lookup"><span data-stu-id="5e755-111">Attempting to deserialize representations that don't conform to the profile will cause <xref:System.Text.Json.JsonSerializer> to throw a <xref:System.Text.Json.JsonException>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/deserializing-with-jsonserializer-error.cs)]

<span data-ttu-id="5e755-112">Poskytuje strukturovaný přístup k obsahu datové části JSON, včetně <xref:System.DateTime> a <xref:System.DateTimeOffset> reprezentace. <xref:System.Text.Json.JsonDocument></span><span class="sxs-lookup"><span data-stu-id="5e755-112">The <xref:System.Text.Json.JsonDocument> provides structured access to the contents of a JSON payload, including <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span> <span data-ttu-id="5e755-113">Níže uvedený příklad ukazuje, jak se při dané kolekci teplot vypočte průměrná teplota v pondělí:</span><span class="sxs-lookup"><span data-stu-id="5e755-113">The example below shows how, when given a collection of temperatures, the average temperature on Mondays can be calculated:</span></span>

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-valid.cs)]

<span data-ttu-id="5e755-114">Pokud se pokusíte vypočítat průměrnou teplotu pro datovou část s neodpovídajícími <xref:System.DateTime> reprezentacemi, <xref:System.Text.Json.JsonDocument> bude vyvolávat <xref:System.FormatException>:</span><span class="sxs-lookup"><span data-stu-id="5e755-114">Attempting to compute the average temperature given a payload with non-compliant <xref:System.DateTime> representations will cause <xref:System.Text.Json.JsonDocument> to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/computing-with-jsondocument-error.cs)]

<span data-ttu-id="5e755-115">Zápisy <xref:System.Text.Json.Utf8JsonWriter> <xref:System.DateTime> a<xref:System.DateTimeOffset> data nižší úrovně:</span><span class="sxs-lookup"><span data-stu-id="5e755-115">The lower level <xref:System.Text.Json.Utf8JsonWriter> writes <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/writing-with-utf8jsonwriter.cs)]

<span data-ttu-id="5e755-116"><xref:System.Text.Json.Utf8JsonReader>analyzuje <xref:System.DateTimeOffset>adata: <xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="5e755-116"><xref:System.Text.Json.Utf8JsonReader> parses <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-valid.cs)]

<span data-ttu-id="5e755-117">Při pokusu o čtení nekompatibilních formátů <xref:System.Text.Json.Utf8JsonReader> se způsobí, že <xref:System.FormatException>vyvolá výjimku:</span><span class="sxs-lookup"><span data-stu-id="5e755-117">Attempting to read non-compliant formats with <xref:System.Text.Json.Utf8JsonReader> will cause it to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/reading-with-utf8jsonreader-error.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset-in-xrefsystemtextjsonjsonserializer"></a><span data-ttu-id="5e755-118">Vlastní podpora pro <xref:System.DateTime> a <xref:System.DateTimeOffset> v<xref:System.Text.Json.JsonSerializer></span><span class="sxs-lookup"><span data-stu-id="5e755-118">Custom support for <xref:System.DateTime> and <xref:System.DateTimeOffset> in <xref:System.Text.Json.JsonSerializer></span></span>

<span data-ttu-id="5e755-119">Pokud chcete, aby serializátor prováděl vlastní analýzu nebo formátování, můžete implementovat [vlastní převaděče](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).</span><span class="sxs-lookup"><span data-stu-id="5e755-119">If you want the serializer to perform custom parsing or formatting, you can implement [custom converters](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).</span></span>
<span data-ttu-id="5e755-120">Tady je několik příkladů:</span><span class="sxs-lookup"><span data-stu-id="5e755-120">Here are a few examples:</span></span>

### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a><span data-ttu-id="5e755-121">Používání `DateTime(Offset).Parse` a`DateTime(Offset).ToString`</span><span class="sxs-lookup"><span data-stu-id="5e755-121">Using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`</span></span>

<span data-ttu-id="5e755-122">Pokud nemůžete určit formáty vstupních <xref:System.DateTime> nebo <xref:System.DateTimeOffset> textových reprezentace `DateTime(Offset).Parse` , můžete použít metodu v logice Read.</span><span class="sxs-lookup"><span data-stu-id="5e755-122">If you can't determine the formats of your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations, you can use the `DateTime(Offset).Parse` method in your converter read logic.</span></span> <span data-ttu-id="5e755-123">To vám umožní použít. Rozsáhlá podpora pro analýzu různých <xref:System.DateTime> <xref:System.DateTimeOffset> formátů textu, včetně řetězců jiných než ISO 8601 a formátů ISO 8601, které neodpovídají rozšířenému profilu ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="5e755-123">This allows you to use .NET's extensive support for parsing various <xref:System.DateTime> and <xref:System.DateTimeOffset> text formats, including non-ISO 8601 strings and ISO 8601 formats that don't conform to the extended ISO 8601-1:2019 profile.</span></span> <span data-ttu-id="5e755-124">Tento přístup je výrazně menší než použití nativní implementace serializátoru.</span><span class="sxs-lookup"><span data-stu-id="5e755-124">This approach is significantly less performant than using the serializer's native implementation.</span></span>

<span data-ttu-id="5e755-125">Pro serializaci můžete použít `DateTime(Offset).ToString` metodu ve vaší logice zápisu převaděče.</span><span class="sxs-lookup"><span data-stu-id="5e755-125">For serializing, you can use the `DateTime(Offset).ToString` method in your converter write logic.</span></span> <span data-ttu-id="5e755-126">To vám umožní <xref:System.DateTime> zapisovat a <xref:System.DateTimeOffset> hodnoty pomocí libovolného [standardního formátu data a času](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)a [vlastních formátů data a času](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span><span class="sxs-lookup"><span data-stu-id="5e755-126">This allows you to write <xref:System.DateTime> and <xref:System.DateTimeOffset> values using any of the [standard date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), and the [custom date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span></span>
<span data-ttu-id="5e755-127">To je také podstatně méně prováděno, než použití nativní implementace serializátoru.</span><span class="sxs-lookup"><span data-stu-id="5e755-127">This is also significantly less performant than using the serializer's native implementation.</span></span>

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <span data-ttu-id="5e755-128">Při implementaci <xref:System.Text.Json.Serialization.JsonConverter%601> `T` , <xref:System.DateTime> parametrbude`typeof(DateTime)`vždy. `typeToConvert`</span><span class="sxs-lookup"><span data-stu-id="5e755-128">When implementing <xref:System.Text.Json.Serialization.JsonConverter%601>, and `T` is <xref:System.DateTime>, the `typeToConvert` parameter will always be `typeof(DateTime)`.</span></span>
<span data-ttu-id="5e755-129">Parametr je vhodný pro zpracování polymorfních případů a při použití obecných typů k získání `typeof(T)` v provedených způsobech.</span><span class="sxs-lookup"><span data-stu-id="5e755-129">The parameter is useful for handling polymorphic cases and when using generics to get `typeof(T)` in a performant way.</span></span>

### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a><span data-ttu-id="5e755-130">Používání <xref:System.Buffers.Text.Utf8Parser> a<xref:System.Buffers.Text.Utf8Formatter></span><span class="sxs-lookup"><span data-stu-id="5e755-130">Using <xref:System.Buffers.Text.Utf8Parser> and <xref:System.Buffers.Text.Utf8Formatter></span></span>

<span data-ttu-id="5e755-131">V logice převaděče můžete použít rychlou metodu analýzy a formátování založenou na kódování UTF-8, <xref:System.DateTime> Pokud <xref:System.DateTimeOffset> jsou vstupní nebo textové reprezentace kompatibilní s jedním z [řetězců formátu data a času standardu](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)"R", "l", "O" nebo "G", nebo pokud chcete Pište podle jednoho z těchto formátů.</span><span class="sxs-lookup"><span data-stu-id="5e755-131">You can use fast UTF-8-based parsing and formatting methods in your converter logic if your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations are compliant with one of the "R", "l", "O", or "G" [standard date and time format Strings](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), or you want to write according to one of these formats.</span></span> <span data-ttu-id="5e755-132">To je mnohem rychlejší než použití `DateTime(Offset).Parse` a `DateTime(Offset).ToString`.</span><span class="sxs-lookup"><span data-stu-id="5e755-132">This is much faster than using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`.</span></span>

<span data-ttu-id="5e755-133">Tento příklad ukazuje vlastní převaděč, který serializace a deserializace <xref:System.DateTime> hodnoty podle [standardního formátu "R"](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span><span class="sxs-lookup"><span data-stu-id="5e755-133">This example shows a custom converter that serializes and deserializes <xref:System.DateTime> values according to [the "R" standard format](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span></span>

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> <span data-ttu-id="5e755-134">Standardní formát "R" bude vždy 29 znaků dlouhý.</span><span class="sxs-lookup"><span data-stu-id="5e755-134">The "R" standard format will always be 29 characters long.</span></span>

### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a><span data-ttu-id="5e755-135">Použití `DateTime(Offset).Parse` jako záložní pro nativní analýzu serializátoru</span><span class="sxs-lookup"><span data-stu-id="5e755-135">Using `DateTime(Offset).Parse` as a fallback to the serializer's native parsing</span></span>

<span data-ttu-id="5e755-136">Pokud obecně očekáváte, že <xref:System.DateTime> váš <xref:System.DateTimeOffset> vstup nebo data budou v souladu s rozšířeným profilem ISO 8601-1:2019, můžete použít logiku nativní analýzy pro serializátor.</span><span class="sxs-lookup"><span data-stu-id="5e755-136">If you generally expect your input <xref:System.DateTime> or <xref:System.DateTimeOffset> data to conform to the extended ISO 8601-1:2019 profile, you can use the serializer's native parsing logic.</span></span> <span data-ttu-id="5e755-137">Můžete také implementovat záložní mechanismus jenom pro případ.</span><span class="sxs-lookup"><span data-stu-id="5e755-137">You can also implement a fallback mechanism just in case.</span></span>
<span data-ttu-id="5e755-138">Tento příklad ukazuje, že po selhání analýzy <xref:System.DateTime> textové reprezentace pomocí <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>převaděče úspěšně analyzuje data pomocí <xref:System.DateTime.Parse(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="5e755-138">This example shows that, after failing to parse a <xref:System.DateTime> text representation using <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, the converter successfully parses the data using <xref:System.DateTime.Parse(System.String)>.</span></span>

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/datetime-converter-examples/example3/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a><span data-ttu-id="5e755-139">Rozšířený profil ISO 8601-1:2019 v souboru System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="5e755-139">The extended ISO 8601-1:2019 profile in System.Text.Json</span></span>

### <a name="date-and-time-components"></a><span data-ttu-id="5e755-140">Komponenty data a času</span><span class="sxs-lookup"><span data-stu-id="5e755-140">Date and time components</span></span>

<span data-ttu-id="5e755-141">Rozšířený profil ISO 8601-1:2019 implementovaný v <xref:System.Text.Json> nástroji definuje následující komponenty pro reprezentace data a času.</span><span class="sxs-lookup"><span data-stu-id="5e755-141">The extended ISO 8601-1:2019 profile implemented in <xref:System.Text.Json> defines the following components for date and time representations.</span></span> <span data-ttu-id="5e755-142">Tyto komponenty se používají k definování různých úrovní členitosti při analýze a formátování <xref:System.DateTime> a <xref:System.DateTimeOffset> reprezentace.</span><span class="sxs-lookup"><span data-stu-id="5e755-142">These components are used to define various levels of granularity supported when parsing and formatting <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span>

| <span data-ttu-id="5e755-143">Součást</span><span class="sxs-lookup"><span data-stu-id="5e755-143">Component</span></span>       | <span data-ttu-id="5e755-144">Formát</span><span class="sxs-lookup"><span data-stu-id="5e755-144">Format</span></span>                      | <span data-ttu-id="5e755-145">Popis</span><span class="sxs-lookup"><span data-stu-id="5e755-145">Description</span></span>                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| <span data-ttu-id="5e755-146">Rok</span><span class="sxs-lookup"><span data-stu-id="5e755-146">Year</span></span>            | <span data-ttu-id="5e755-147">"yyyy"</span><span class="sxs-lookup"><span data-stu-id="5e755-147">"yyyy"</span></span>                      | <span data-ttu-id="5e755-148">0001-9999</span><span class="sxs-lookup"><span data-stu-id="5e755-148">0001-9999</span></span>                                                                       |
| <span data-ttu-id="5e755-149">Měsíčně</span><span class="sxs-lookup"><span data-stu-id="5e755-149">Month</span></span>           | <span data-ttu-id="5e755-150">"MM"</span><span class="sxs-lookup"><span data-stu-id="5e755-150">"MM"</span></span>                        | <span data-ttu-id="5e755-151">01-12</span><span class="sxs-lookup"><span data-stu-id="5e755-151">01-12</span></span>                                                                           |
| <span data-ttu-id="5e755-152">Den</span><span class="sxs-lookup"><span data-stu-id="5e755-152">Day</span></span>             | <span data-ttu-id="5e755-153">"dd"</span><span class="sxs-lookup"><span data-stu-id="5e755-153">"dd"</span></span>                        | <span data-ttu-id="5e755-154">01-28, 01-29, 01-30, 01-31 v závislosti na měsíci/roce</span><span class="sxs-lookup"><span data-stu-id="5e755-154">01-28, 01-29, 01-30, 01-31 based on month/year</span></span>                                  |
| <span data-ttu-id="5e755-155">Hodina</span><span class="sxs-lookup"><span data-stu-id="5e755-155">Hour</span></span>            | <span data-ttu-id="5e755-156">"HH"</span><span class="sxs-lookup"><span data-stu-id="5e755-156">"HH"</span></span>                        | <span data-ttu-id="5e755-157">00-23</span><span class="sxs-lookup"><span data-stu-id="5e755-157">00-23</span></span>                                                                           |
| <span data-ttu-id="5e755-158">Minuta</span><span class="sxs-lookup"><span data-stu-id="5e755-158">Minute</span></span>          | <span data-ttu-id="5e755-159">"mm"</span><span class="sxs-lookup"><span data-stu-id="5e755-159">"mm"</span></span>                        | <span data-ttu-id="5e755-160">00-59</span><span class="sxs-lookup"><span data-stu-id="5e755-160">00-59</span></span>                                                                           |
| <span data-ttu-id="5e755-161">Sekunda</span><span class="sxs-lookup"><span data-stu-id="5e755-161">Second</span></span>          | <span data-ttu-id="5e755-162">"ss"</span><span class="sxs-lookup"><span data-stu-id="5e755-162">"ss"</span></span>                        | <span data-ttu-id="5e755-163">00-59</span><span class="sxs-lookup"><span data-stu-id="5e755-163">00-59</span></span>                                                                           |
| <span data-ttu-id="5e755-164">Druhý zlomek</span><span class="sxs-lookup"><span data-stu-id="5e755-164">Second fraction</span></span> | <span data-ttu-id="5e755-165">"FFFFFFF"</span><span class="sxs-lookup"><span data-stu-id="5e755-165">"FFFFFFF"</span></span>                   | <span data-ttu-id="5e755-166">Minimálně jedna číslice, maximálně 16 číslic</span><span class="sxs-lookup"><span data-stu-id="5e755-166">Minimum of one digit, maximum of 16 digits</span></span>                                      |
| <span data-ttu-id="5e755-167">Časový posun</span><span class="sxs-lookup"><span data-stu-id="5e755-167">Time offset</span></span>     | <span data-ttu-id="5e755-168">"K"</span><span class="sxs-lookup"><span data-stu-id="5e755-168">"K"</span></span>                         | <span data-ttu-id="5e755-169">Buď "Z" nebo "(" + "/"-") HH": mm "</span><span class="sxs-lookup"><span data-stu-id="5e755-169">Either "Z" or "('+'/'-')HH':'mm"</span></span>                                                |
| <span data-ttu-id="5e755-170">Částečný čas</span><span class="sxs-lookup"><span data-stu-id="5e755-170">Partial time</span></span>    | <span data-ttu-id="5e755-171">"HH": ' mm ': ' ss [FFFFFFF] '</span><span class="sxs-lookup"><span data-stu-id="5e755-171">"HH':'mm':'ss[FFFFFFF]"</span></span>     | <span data-ttu-id="5e755-172">Čas bez informací o posunu UTC</span><span class="sxs-lookup"><span data-stu-id="5e755-172">Time without UTC offset information</span></span>                                             |
| <span data-ttu-id="5e755-173">Celé datum</span><span class="sxs-lookup"><span data-stu-id="5e755-173">Full date</span></span>       | <span data-ttu-id="5e755-174">"yyyy-yyyy '-'dd"</span><span class="sxs-lookup"><span data-stu-id="5e755-174">"yyyy'-'MM'-'dd"</span></span>            | <span data-ttu-id="5e755-175">Datum kalendáře</span><span class="sxs-lookup"><span data-stu-id="5e755-175">Calendar date</span></span>                                                                   |
| <span data-ttu-id="5e755-176">Plný čas</span><span class="sxs-lookup"><span data-stu-id="5e755-176">Full time</span></span>       | <span data-ttu-id="5e755-177">"' Partial time'K</span><span class="sxs-lookup"><span data-stu-id="5e755-177">"'Partial time'K"</span></span>           | <span data-ttu-id="5e755-178">UTC v den nebo místní čas s časovým posunem mezi místním časem a UTC</span><span class="sxs-lookup"><span data-stu-id="5e755-178">UTC of day or Local time of day with the time offset between local time and UTC</span></span> |
| <span data-ttu-id="5e755-179">Datum a čas</span><span class="sxs-lookup"><span data-stu-id="5e755-179">Date time</span></span>       | <span data-ttu-id="5e755-180">"" Celé datum "nemá plný čas" "</span><span class="sxs-lookup"><span data-stu-id="5e755-180">"'Full date''T''Full time'"</span></span> | <span data-ttu-id="5e755-181">Datum a čas kalendáře, např. 2019-07-26T16:59:57-05:00</span><span class="sxs-lookup"><span data-stu-id="5e755-181">Calendar date and time of day, e.g. 2019-07-26T16:59:57-05:00</span></span>                   |

### <a name="support-for-parsing"></a><span data-ttu-id="5e755-182">Podpora pro analýzu</span><span class="sxs-lookup"><span data-stu-id="5e755-182">Support for parsing</span></span>

<span data-ttu-id="5e755-183">Pro analýzu jsou definovány následující úrovně členitosti:</span><span class="sxs-lookup"><span data-stu-id="5e755-183">The following levels of granularity are defined for parsing:</span></span>

1. <span data-ttu-id="5e755-184">"Celé datum"</span><span class="sxs-lookup"><span data-stu-id="5e755-184">'Full date'</span></span>
    1. <span data-ttu-id="5e755-185">"yyyy-yyyy '-'dd"</span><span class="sxs-lookup"><span data-stu-id="5e755-185">"yyyy'-'MM'-'dd"</span></span>

2. <span data-ttu-id="5e755-186">"" Celé datum "t" hodina "": "min" "</span><span class="sxs-lookup"><span data-stu-id="5e755-186">"'Full date''T''Hour'':''Minute'"</span></span>
    1. <span data-ttu-id="5e755-187">"yyyy-yyyy '-DD 't": "mm"</span><span class="sxs-lookup"><span data-stu-id="5e755-187">"yyyy'-'MM'-'dd'T'HH':'mm"</span></span>

3. <span data-ttu-id="5e755-188">"" Celé datum "t" v částečný čas ""</span><span class="sxs-lookup"><span data-stu-id="5e755-188">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="5e755-189">"yyyy-yyyy '-DD 't": ' mm ': ' ss ' ([specifikátor formátu ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="5e755-189">"yyyy'-'MM'-'dd'T'HH':'mm':'ss" ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>
    2. <span data-ttu-id="5e755-190">"yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="5e755-190">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

4. <span data-ttu-id="5e755-191">"" Celé datum "t" Časová hodina "": minuta "časový posun" "</span><span class="sxs-lookup"><span data-stu-id="5e755-191">"'Full date''T''Time hour'':''Minute''Time offset'"</span></span>
    1. <span data-ttu-id="5e755-192">"yyyy-yyyy '-DD 't": ' mmZ '</span><span class="sxs-lookup"><span data-stu-id="5e755-192">"yyyy'-'MM'-'dd'T'HH':'mmZ"</span></span>
    2. <span data-ttu-id="5e755-193">"yyyy-yyyy '-DD 't": ' mm (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="5e755-193">"yyyy'-'MM'-'dd'T'HH':'mm('+'/'-')HH':'mm"</span></span>

5. <span data-ttu-id="5e755-194">' Datum a čas '</span><span class="sxs-lookup"><span data-stu-id="5e755-194">'Date time'</span></span>
    1. <span data-ttu-id="5e755-195">"yyyy-yyyy '-DD 't": ' mm ': ' ssZ '</span><span class="sxs-lookup"><span data-stu-id="5e755-195">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>
    2. <span data-ttu-id="5e755-196">"yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFFZ"</span><span class="sxs-lookup"><span data-stu-id="5e755-196">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>
    3. <span data-ttu-id="5e755-197">"yyyy-yyyy '-DD 't": ' mm ': ' ss ' (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="5e755-197">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>
    4. <span data-ttu-id="5e755-198">"yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF (+ '/'-') HH ': mm</span><span class="sxs-lookup"><span data-stu-id="5e755-198">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

<span data-ttu-id="5e755-199">Pokud pro sekundy existují desetinné zlomky, musí existovat alespoň jedna číslice. `2019-07-26T00:00:00.` není povoleno.</span><span class="sxs-lookup"><span data-stu-id="5e755-199">If there are decimal fractions for seconds, there must be at least one digit; `2019-07-26T00:00:00.` is not allowed.</span></span>
<span data-ttu-id="5e755-200">I když je povolený až 16 zlomkových číslic, analyzují se jenom prvních sedm.</span><span class="sxs-lookup"><span data-stu-id="5e755-200">While up to 16 fractional digits are allowed, only the first seven are parsed.</span></span> <span data-ttu-id="5e755-201">Vše nad rámec, který je považován za nulu.</span><span class="sxs-lookup"><span data-stu-id="5e755-201">Anything beyond that is considered a zero.</span></span>
<span data-ttu-id="5e755-202">Například se bude `2019-07-26T00:00:00.1234567890` analyzovat, jako by `2019-07-26T00:00:00.1234567`to bylo.</span><span class="sxs-lookup"><span data-stu-id="5e755-202">For example, `2019-07-26T00:00:00.1234567890` will be parsed as if it is `2019-07-26T00:00:00.1234567`.</span></span>
<span data-ttu-id="5e755-203">Je tak udržování kompatibility s <xref:System.DateTime> implementací, což je omezeno na toto řešení.</span><span class="sxs-lookup"><span data-stu-id="5e755-203">This is to stay compatible with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>

<span data-ttu-id="5e755-204">Přestupné sekundy nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="5e755-204">Leap seconds are not supported.</span></span>

### <a name="support-for-formatting"></a><span data-ttu-id="5e755-205">Podpora formátování</span><span class="sxs-lookup"><span data-stu-id="5e755-205">Support for formatting</span></span>

<span data-ttu-id="5e755-206">Pro formátování jsou definovány následující úrovně členitosti:</span><span class="sxs-lookup"><span data-stu-id="5e755-206">The following levels of granularity are defined for formatting:</span></span>

1. <span data-ttu-id="5e755-207">"" Celé datum "t" v částečný čas ""</span><span class="sxs-lookup"><span data-stu-id="5e755-207">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="5e755-208">"yyyy-yyyy '-DD 't": ' mm ': ' ss ' ([specifikátor formátu ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="5e755-208">"yyyy'-'MM'-'dd'T'HH':'mm':'ss"  ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>

        <span data-ttu-id="5e755-209">Používá se k formátování <xref:System.DateTime> bez zlomků sekund a bez informací o posunu.</span><span class="sxs-lookup"><span data-stu-id="5e755-209">Used to format a <xref:System.DateTime> without fractional seconds and without offset information.</span></span>

    2. <span data-ttu-id="5e755-210">"yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="5e755-210">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

        <span data-ttu-id="5e755-211">Používá se k formátování <xref:System.DateTime> s zlomky sekund, ale bez informací o posunu.</span><span class="sxs-lookup"><span data-stu-id="5e755-211">Used to format a <xref:System.DateTime> with fractional seconds but without offset information.</span></span>

2. <span data-ttu-id="5e755-212">' Datum a čas '</span><span class="sxs-lookup"><span data-stu-id="5e755-212">'Date time'</span></span>
    1. <span data-ttu-id="5e755-213">"yyyy-yyyy '-DD 't": ' mm ': ' ssZ '</span><span class="sxs-lookup"><span data-stu-id="5e755-213">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>

        <span data-ttu-id="5e755-214">Používá se k formátování <xref:System.DateTime> nebo <xref:System.DateTimeOffset> bez zlomků sekund, ale s posunem UTC.</span><span class="sxs-lookup"><span data-stu-id="5e755-214">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a UTC offset.</span></span>

    2. <span data-ttu-id="5e755-215">"yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFFZ"</span><span class="sxs-lookup"><span data-stu-id="5e755-215">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>

        <span data-ttu-id="5e755-216">Používá se k formátování <xref:System.DateTime> nebo <xref:System.DateTimeOffset> se zlomky sekund a s posunem UTC.</span><span class="sxs-lookup"><span data-stu-id="5e755-216">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a UTC offset.</span></span>

    3. <span data-ttu-id="5e755-217">"yyyy-yyyy '-DD 't": ' mm ': ' ss ' (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="5e755-217">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="5e755-218">Používá se k formátování <xref:System.DateTime> nebo <xref:System.DateTimeOffset> bez zlomků sekund, ale s lokálním posunem.</span><span class="sxs-lookup"><span data-stu-id="5e755-218">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a local offset.</span></span>

    4. <span data-ttu-id="5e755-219">"yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF (+ '/'-') HH ': mm</span><span class="sxs-lookup"><span data-stu-id="5e755-219">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="5e755-220">Používá se k formátování <xref:System.DateTime> nebo <xref:System.DateTimeOffset> se zlomky sekund a s místním posunem.</span><span class="sxs-lookup"><span data-stu-id="5e755-220">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a local offset.</span></span>
