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
ms.openlocfilehash: 04e0e3c613b194ac85241d50d3bc5fd5dc0b6e54
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73977327"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a><span data-ttu-id="c837f-103">Podpora DateTime a DateTimeOffset v System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="c837f-103">DateTime and DateTimeOffset support in System.Text.Json</span></span>

<span data-ttu-id="c837f-104">Knihovna System. text. JSON analyzuje a zapisuje hodnoty <xref:System.DateTime> a <xref:System.DateTimeOffset> podle rozšířeného profilu ISO 8601:-2019.</span><span class="sxs-lookup"><span data-stu-id="c837f-104">The System.Text.Json library parses and writes <xref:System.DateTime> and <xref:System.DateTimeOffset> values according to the ISO 8601:-2019 extended profile.</span></span>
<span data-ttu-id="c837f-105">[Převaděče](xref:System.Text.Json.Serialization.JsonConverter%601) poskytují vlastní podporu pro serializaci a deserializaci pomocí <xref:System.Text.Json.JsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="c837f-105">[Converters](xref:System.Text.Json.Serialization.JsonConverter%601) provide custom support for serializing and deserializing with <xref:System.Text.Json.JsonSerializer>.</span></span>
<span data-ttu-id="c837f-106">Vlastní podporu je taky možné implementovat při použití <xref:System.Text.Json.Utf8JsonReader> a <xref:System.Text.Json.Utf8JsonWriter>.</span><span class="sxs-lookup"><span data-stu-id="c837f-106">Custom support can also be implemented when using <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter>.</span></span>

## <a name="support-for-the-iso-8601-12019-format"></a><span data-ttu-id="c837f-107">Podpora formátu ISO 8601-1:2019</span><span class="sxs-lookup"><span data-stu-id="c837f-107">Support for the ISO 8601-1:2019 format</span></span>

<span data-ttu-id="c837f-108"><xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>a <xref:System.Text.Json.JsonElement> typy analyzují a zapisují <xref:System.DateTime> a <xref:System.DateTimeOffset> text reprezentovat podle rozšířeného profilu formátu ISO 8601-1:2019; například 2019-07-26T16:59:57-05:00.</span><span class="sxs-lookup"><span data-stu-id="c837f-108">The <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>, and <xref:System.Text.Json.JsonElement> types parse and write <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations according to the extended profile of the ISO 8601-1:2019 format; for example, 2019-07-26T16:59:57-05:00.</span></span>

<span data-ttu-id="c837f-109">data <xref:System.DateTime> a <xref:System.DateTimeOffset> je možné serializovat pomocí <xref:System.Text.Json.JsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="c837f-109"><xref:System.DateTime> and <xref:System.DateTimeOffset> data can be serialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

<span data-ttu-id="c837f-110">Lze je také deserializovat pomocí <xref:System.Text.Json.JsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="c837f-110">They can also be deserialized with <xref:System.Text.Json.JsonSerializer>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

<span data-ttu-id="c837f-111">Ve výchozím nastavení musí být vstupní <xref:System.DateTime> a <xref:System.DateTimeOffset> reprezentace textu v souladu s rozšířeným profilem ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="c837f-111">With default options, input <xref:System.DateTime> and <xref:System.DateTimeOffset> text representations must conform to the extended ISO 8601-1:2019 profile.</span></span>
<span data-ttu-id="c837f-112">Při pokusu o deserializaci reprezentace, která není v souladu s profilem, dojde k vygenerování <xref:System.Text.Json.JsonException><xref:System.Text.Json.JsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="c837f-112">Attempting to deserialize representations that don't conform to the profile will cause <xref:System.Text.Json.JsonSerializer> to throw a <xref:System.Text.Json.JsonException>:</span></span>

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

<span data-ttu-id="c837f-113"><xref:System.Text.Json.JsonDocument> poskytuje strukturovaný přístup k obsahu datové části JSON, včetně <xref:System.DateTime> a <xref:System.DateTimeOffset> reprezentace.</span><span class="sxs-lookup"><span data-stu-id="c837f-113">The <xref:System.Text.Json.JsonDocument> provides structured access to the contents of a JSON payload, including <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span> <span data-ttu-id="c837f-114">Níže uvedený příklad ukazuje, jak se při dané kolekci teplot vypočte průměrná teplota v pondělí:</span><span class="sxs-lookup"><span data-stu-id="c837f-114">The example below shows how, when given a collection of temperatures, the average temperature on Mondays can be calculated:</span></span>

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

<span data-ttu-id="c837f-115">Při pokusu o výpočet průměrné teploty pro datovou část s nevyhovujícími <xref:System.DateTime> reprezentující by <xref:System.Text.Json.JsonDocument> vyvolala <xref:System.FormatException>:</span><span class="sxs-lookup"><span data-stu-id="c837f-115">Attempting to compute the average temperature given a payload with non-compliant <xref:System.DateTime> representations will cause <xref:System.Text.Json.JsonDocument> to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

<span data-ttu-id="c837f-116"><xref:System.Text.Json.Utf8JsonWriter> nižší úrovně zapisuje <xref:System.DateTime> a <xref:System.DateTimeOffset> data:</span><span class="sxs-lookup"><span data-stu-id="c837f-116">The lower level <xref:System.Text.Json.Utf8JsonWriter> writes <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<span data-ttu-id="c837f-117"><xref:System.Text.Json.Utf8JsonReader> analyzuje <xref:System.DateTime> a <xref:System.DateTimeOffset> data:</span><span class="sxs-lookup"><span data-stu-id="c837f-117"><xref:System.Text.Json.Utf8JsonReader> parses <xref:System.DateTime> and <xref:System.DateTimeOffset> data:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

<span data-ttu-id="c837f-118">Při pokusu o čtení nekompatibilních formátů pomocí <xref:System.Text.Json.Utf8JsonReader> způsobí, že vyvolá <xref:System.FormatException>:</span><span class="sxs-lookup"><span data-stu-id="c837f-118">Attempting to read non-compliant formats with <xref:System.Text.Json.Utf8JsonReader> will cause it to throw a <xref:System.FormatException>:</span></span>

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a><span data-ttu-id="c837f-119">Vlastní podpora pro <xref:System.DateTime> a <xref:System.DateTimeOffset></span><span class="sxs-lookup"><span data-stu-id="c837f-119">Custom support for <xref:System.DateTime> and <xref:System.DateTimeOffset></span></span>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a><span data-ttu-id="c837f-120">Při použití <xref:System.Text.Json.JsonSerializer></span><span class="sxs-lookup"><span data-stu-id="c837f-120">When using <xref:System.Text.Json.JsonSerializer></span></span>

<span data-ttu-id="c837f-121">Pokud chcete, aby serializátor prováděl vlastní analýzu nebo formátování, můžete implementovat [vlastní převaděče](xref:System.Text.Json.Serialization.JsonConverter%601).</span><span class="sxs-lookup"><span data-stu-id="c837f-121">If you want the serializer to perform custom parsing or formatting, you can implement [custom converters](xref:System.Text.Json.Serialization.JsonConverter%601).</span></span>
<span data-ttu-id="c837f-122">Tady je několik příkladů:</span><span class="sxs-lookup"><span data-stu-id="c837f-122">Here are a few examples:</span></span>

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a><span data-ttu-id="c837f-123">Používání `DateTime(Offset).Parse` a `DateTime(Offset).ToString`</span><span class="sxs-lookup"><span data-stu-id="c837f-123">Using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`</span></span>

<span data-ttu-id="c837f-124">Pokud nemůžete určit formáty vstupních <xref:System.DateTime> nebo <xref:System.DateTimeOffset> reprezentace textu, můžete použít metodu `DateTime(Offset).Parse` v logice Read.</span><span class="sxs-lookup"><span data-stu-id="c837f-124">If you can't determine the formats of your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations, you can use the `DateTime(Offset).Parse` method in your converter read logic.</span></span> <span data-ttu-id="c837f-125">To vám umožní použít. Rozsáhlá podpora pro analýzu různých formátů <xref:System.DateTime> a <xref:System.DateTimeOffset> textu, včetně řetězců jiných než ISO 8601 a formátů ISO 8601, které neodpovídají rozšířenému profilu ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="c837f-125">This allows you to use .NET's extensive support for parsing various <xref:System.DateTime> and <xref:System.DateTimeOffset> text formats, including non-ISO 8601 strings and ISO 8601 formats that don't conform to the extended ISO 8601-1:2019 profile.</span></span> <span data-ttu-id="c837f-126">Tento přístup je výrazně menší než použití nativní implementace serializátoru.</span><span class="sxs-lookup"><span data-stu-id="c837f-126">This approach is significantly less performant than using the serializer's native implementation.</span></span>

<span data-ttu-id="c837f-127">Pro serializaci můžete použít metodu `DateTime(Offset).ToString` ve vaší logice zápisu převaděče.</span><span class="sxs-lookup"><span data-stu-id="c837f-127">For serializing, you can use the `DateTime(Offset).ToString` method in your converter write logic.</span></span> <span data-ttu-id="c837f-128">To umožňuje psát <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty pomocí libovolného [standardního formátu data a času](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)a [vlastních formátů data a času](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span><span class="sxs-lookup"><span data-stu-id="c837f-128">This allows you to write <xref:System.DateTime> and <xref:System.DateTimeOffset> values using any of the [standard date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), and the [custom date and time formats](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).</span></span>
<span data-ttu-id="c837f-129">To je také podstatně méně prováděno, než použití nativní implementace serializátoru.</span><span class="sxs-lookup"><span data-stu-id="c837f-129">This is also significantly less performant than using the serializer's native implementation.</span></span>

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> <span data-ttu-id="c837f-130">Při implementaci <xref:System.Text.Json.Serialization.JsonConverter%601>a `T` je <xref:System.DateTime>, parametr `typeToConvert` bude vždy `typeof(DateTime)`.</span><span class="sxs-lookup"><span data-stu-id="c837f-130">When implementing <xref:System.Text.Json.Serialization.JsonConverter%601>, and `T` is <xref:System.DateTime>, the `typeToConvert` parameter will always be `typeof(DateTime)`.</span></span>
<span data-ttu-id="c837f-131">Parametr je vhodný pro zpracování polymorfních případů a při použití obecných typů k získání `typeof(T)` způsobem.</span><span class="sxs-lookup"><span data-stu-id="c837f-131">The parameter is useful for handling polymorphic cases and when using generics to get `typeof(T)` in a performant way.</span></span>

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a><span data-ttu-id="c837f-132">Používání <xref:System.Buffers.Text.Utf8Parser> a <xref:System.Buffers.Text.Utf8Formatter></span><span class="sxs-lookup"><span data-stu-id="c837f-132">Using <xref:System.Buffers.Text.Utf8Parser> and <xref:System.Buffers.Text.Utf8Formatter></span></span>

<span data-ttu-id="c837f-133">V logice převaděče můžete použít rychlé metody analýzy a formátování založené na kódování UTF-8, pokud vstupní <xref:System.DateTime> nebo <xref:System.DateTimeOffset> textové reprezentace jsou v souladu s jedním z [řetězců formátu data a času standard](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)"R", "l", "O" nebo "G" nebo chcete zapisovat do jednoho z těchto formátů.</span><span class="sxs-lookup"><span data-stu-id="c837f-133">You can use fast UTF-8-based parsing and formatting methods in your converter logic if your input <xref:System.DateTime> or <xref:System.DateTimeOffset> text representations are compliant with one of the "R", "l", "O", or "G" [standard date and time format strings](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings), or you want to write according to one of these formats.</span></span> <span data-ttu-id="c837f-134">To je mnohem rychlejší než použití `DateTime(Offset).Parse` a `DateTime(Offset).ToString`.</span><span class="sxs-lookup"><span data-stu-id="c837f-134">This is much faster than using `DateTime(Offset).Parse` and `DateTime(Offset).ToString`.</span></span>

<span data-ttu-id="c837f-135">Tento příklad ukazuje vlastní převaděč, který serializace a deserializace <xref:System.DateTime> hodnoty podle [standardního formátu "R"](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span><span class="sxs-lookup"><span data-stu-id="c837f-135">This example shows a custom converter that serializes and deserializes <xref:System.DateTime> values according to [the "R" standard format](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):</span></span>

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> <span data-ttu-id="c837f-136">Standardní formát "R" bude vždy 29 znaků dlouhý.</span><span class="sxs-lookup"><span data-stu-id="c837f-136">The "R" standard format will always be 29 characters long.</span></span>

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a><span data-ttu-id="c837f-137">Použití `DateTime(Offset).Parse` jako záložního pro nativní analýzu serializátoru</span><span class="sxs-lookup"><span data-stu-id="c837f-137">Using `DateTime(Offset).Parse` as a fallback to the serializer's native parsing</span></span>

<span data-ttu-id="c837f-138">Pokud jste obecně očekávali, že vstupní <xref:System.DateTime> nebo <xref:System.DateTimeOffset> data v souladu s rozšířeným profilem ISO 8601-1:2019, můžete použít logiku nativní analýzy pro serializátor.</span><span class="sxs-lookup"><span data-stu-id="c837f-138">If you generally expect your input <xref:System.DateTime> or <xref:System.DateTimeOffset> data to conform to the extended ISO 8601-1:2019 profile, you can use the serializer's native parsing logic.</span></span> <span data-ttu-id="c837f-139">Můžete také implementovat záložní mechanismus jenom pro případ.</span><span class="sxs-lookup"><span data-stu-id="c837f-139">You can also implement a fallback mechanism just in case.</span></span>
<span data-ttu-id="c837f-140">Tento příklad ukazuje, že po selhání analýzy <xref:System.DateTime> textové reprezentace pomocí <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>převaděč úspěšně analyzuje data pomocí <xref:System.DateTime.Parse(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="c837f-140">This example shows that, after failing to parse a <xref:System.DateTime> text representation using <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>, the converter successfully parses the data using <xref:System.DateTime.Parse(System.String)>.</span></span>

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a><span data-ttu-id="c837f-141">Při psaní pomocí <xref:System.Text.Json.Utf8JsonWriter></span><span class="sxs-lookup"><span data-stu-id="c837f-141">When writing with <xref:System.Text.Json.Utf8JsonWriter></span></span>

<span data-ttu-id="c837f-142">Pokud chcete napsat vlastní <xref:System.DateTime> nebo <xref:System.DateTimeOffset> textovou reprezentaci pomocí <xref:System.Text.Json.Utf8JsonWriter>, můžete vlastní reprezentaci naformátovat na <xref:System.String>, `ReadOnlySpan<Byte>`, `ReadOnlySpan<Char>`nebo <xref:System.Text.Json.JsonEncodedText>, a pak ji předat odpovídající metodě [Utf8JsonWriter. WriteStringValue](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestringvalue?view=netcore-3.0) nebo [Utf8JsonWriter. WriteString](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestring?view=netcore-3.0) .</span><span class="sxs-lookup"><span data-stu-id="c837f-142">If you want to write a custom <xref:System.DateTime> or <xref:System.DateTimeOffset> text representation with <xref:System.Text.Json.Utf8JsonWriter>, you can format your custom representation to a <xref:System.String>, `ReadOnlySpan<Byte>`, `ReadOnlySpan<Char>`, or <xref:System.Text.Json.JsonEncodedText>, then pass it to the corresponding [Utf8JsonWriter.WriteStringValue](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestringvalue?view=netcore-3.0) or [Utf8JsonWriter.WriteString](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestring?view=netcore-3.0) method.</span></span>

<span data-ttu-id="c837f-143">Následující příklad ukazuje, jak lze vytvořit vlastní <xref:System.DateTime> formát pomocí <xref:System.DateTime.ToString(System.String,System.IFormatProvider)>a následně napsaný metodou <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)>:</span><span class="sxs-lookup"><span data-stu-id="c837f-143">The following example shows how a custom <xref:System.DateTime> format can be created with <xref:System.DateTime.ToString(System.String,System.IFormatProvider)>, then written with the <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> method:</span></span>

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a><span data-ttu-id="c837f-144">Při čtení pomocí <xref:System.Text.Json.Utf8JsonReader></span><span class="sxs-lookup"><span data-stu-id="c837f-144">When reading with <xref:System.Text.Json.Utf8JsonReader></span></span>

<span data-ttu-id="c837f-145">Pokud chcete číst vlastní <xref:System.DateTime> nebo <xref:System.DateTimeOffset> textovou reprezentaci <xref:System.Text.Json.Utf8JsonReader>, můžete získat hodnotu aktuálního tokenu JSON jako <xref:System.String> pomocí <xref:System.Text.Json.Utf8JsonReader.GetString>a pak hodnotu analyzovat pomocí vlastní logiky.</span><span class="sxs-lookup"><span data-stu-id="c837f-145">If you want to read a custom <xref:System.DateTime> or <xref:System.DateTimeOffset> text representation with <xref:System.Text.Json.Utf8JsonReader>, you can get the value of the current JSON token as a <xref:System.String> using <xref:System.Text.Json.Utf8JsonReader.GetString>, then parse the value using custom logic.</span></span>

<span data-ttu-id="c837f-146">Následující příklad ukazuje, jak lze načíst vlastní <xref:System.DateTimeOffset> textovou reprezentaci pomocí <xref:System.Text.Json.Utf8JsonReader.GetString>a pak analyzovat pomocí <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>:</span><span class="sxs-lookup"><span data-stu-id="c837f-146">The following example shows how a custom <xref:System.DateTimeOffset> text representation can be retrieved using <xref:System.Text.Json.Utf8JsonReader.GetString>, then parsed using <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>:</span></span>

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a><span data-ttu-id="c837f-147">Rozšířený profil ISO 8601-1:2019 v souboru System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="c837f-147">The extended ISO 8601-1:2019 profile in System.Text.Json</span></span>

### <a name="date-and-time-components"></a><span data-ttu-id="c837f-148">Komponenty data a času</span><span class="sxs-lookup"><span data-stu-id="c837f-148">Date and time components</span></span>

<span data-ttu-id="c837f-149">Rozšířený profil ISO 8601-1:2019 implementovaný v <xref:System.Text.Json> definuje následující komponenty pro reprezentace data a času.</span><span class="sxs-lookup"><span data-stu-id="c837f-149">The extended ISO 8601-1:2019 profile implemented in <xref:System.Text.Json> defines the following components for date and time representations.</span></span> <span data-ttu-id="c837f-150">Tyto komponenty se používají k definování různých úrovní členitosti při analýze a formátování <xref:System.DateTime> a <xref:System.DateTimeOffset> reprezentace.</span><span class="sxs-lookup"><span data-stu-id="c837f-150">These components are used to define various levels of granularity supported when parsing and formatting <xref:System.DateTime> and <xref:System.DateTimeOffset> representations.</span></span>

| <span data-ttu-id="c837f-151">Součást</span><span class="sxs-lookup"><span data-stu-id="c837f-151">Component</span></span>       | <span data-ttu-id="c837f-152">Formát</span><span class="sxs-lookup"><span data-stu-id="c837f-152">Format</span></span>                      | <span data-ttu-id="c837f-153">Popis</span><span class="sxs-lookup"><span data-stu-id="c837f-153">Description</span></span>                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| <span data-ttu-id="c837f-154">Rok</span><span class="sxs-lookup"><span data-stu-id="c837f-154">Year</span></span>            | <span data-ttu-id="c837f-155">"yyyy"</span><span class="sxs-lookup"><span data-stu-id="c837f-155">"yyyy"</span></span>                      | <span data-ttu-id="c837f-156">0001-9999</span><span class="sxs-lookup"><span data-stu-id="c837f-156">0001-9999</span></span>                                                                       |
| <span data-ttu-id="c837f-157">Měsíčně</span><span class="sxs-lookup"><span data-stu-id="c837f-157">Month</span></span>           | <span data-ttu-id="c837f-158">"MM"</span><span class="sxs-lookup"><span data-stu-id="c837f-158">"MM"</span></span>                        | <span data-ttu-id="c837f-159">01-12</span><span class="sxs-lookup"><span data-stu-id="c837f-159">01-12</span></span>                                                                           |
| <span data-ttu-id="c837f-160">Den</span><span class="sxs-lookup"><span data-stu-id="c837f-160">Day</span></span>             | <span data-ttu-id="c837f-161">"dd"</span><span class="sxs-lookup"><span data-stu-id="c837f-161">"dd"</span></span>                        | <span data-ttu-id="c837f-162">01-28, 01-29, 01-30, 01-31 v závislosti na měsíci/roce</span><span class="sxs-lookup"><span data-stu-id="c837f-162">01-28, 01-29, 01-30, 01-31 based on month/year</span></span>                                  |
| <span data-ttu-id="c837f-163">Hodina</span><span class="sxs-lookup"><span data-stu-id="c837f-163">Hour</span></span>            | <span data-ttu-id="c837f-164">"HH"</span><span class="sxs-lookup"><span data-stu-id="c837f-164">"HH"</span></span>                        | <span data-ttu-id="c837f-165">00-23</span><span class="sxs-lookup"><span data-stu-id="c837f-165">00-23</span></span>                                                                           |
| <span data-ttu-id="c837f-166">Minuta</span><span class="sxs-lookup"><span data-stu-id="c837f-166">Minute</span></span>          | <span data-ttu-id="c837f-167">"mm"</span><span class="sxs-lookup"><span data-stu-id="c837f-167">"mm"</span></span>                        | <span data-ttu-id="c837f-168">00-59</span><span class="sxs-lookup"><span data-stu-id="c837f-168">00-59</span></span>                                                                           |
| <span data-ttu-id="c837f-169">Sekunda</span><span class="sxs-lookup"><span data-stu-id="c837f-169">Second</span></span>          | <span data-ttu-id="c837f-170">"ss"</span><span class="sxs-lookup"><span data-stu-id="c837f-170">"ss"</span></span>                        | <span data-ttu-id="c837f-171">00-59</span><span class="sxs-lookup"><span data-stu-id="c837f-171">00-59</span></span>                                                                           |
| <span data-ttu-id="c837f-172">Druhý zlomek</span><span class="sxs-lookup"><span data-stu-id="c837f-172">Second fraction</span></span> | <span data-ttu-id="c837f-173">"FFFFFFF"</span><span class="sxs-lookup"><span data-stu-id="c837f-173">"FFFFFFF"</span></span>                   | <span data-ttu-id="c837f-174">Minimálně jedna číslice, maximálně 16 číslic</span><span class="sxs-lookup"><span data-stu-id="c837f-174">Minimum of one digit, maximum of 16 digits</span></span>                                      |
| <span data-ttu-id="c837f-175">Časový posun</span><span class="sxs-lookup"><span data-stu-id="c837f-175">Time offset</span></span>     | <span data-ttu-id="c837f-176">"K"</span><span class="sxs-lookup"><span data-stu-id="c837f-176">"K"</span></span>                         | <span data-ttu-id="c837f-177">Buď "Z" nebo "(" + "/"-") HH": mm "</span><span class="sxs-lookup"><span data-stu-id="c837f-177">Either "Z" or "('+'/'-')HH':'mm"</span></span>                                                |
| <span data-ttu-id="c837f-178">Částečný čas</span><span class="sxs-lookup"><span data-stu-id="c837f-178">Partial time</span></span>    | <span data-ttu-id="c837f-179">"HH": ' mm ': ' ss [FFFFFFF] '</span><span class="sxs-lookup"><span data-stu-id="c837f-179">"HH':'mm':'ss[FFFFFFF]"</span></span>     | <span data-ttu-id="c837f-180">Čas bez informací o posunu UTC</span><span class="sxs-lookup"><span data-stu-id="c837f-180">Time without UTC offset information</span></span>                                             |
| <span data-ttu-id="c837f-181">Celé datum</span><span class="sxs-lookup"><span data-stu-id="c837f-181">Full date</span></span>       | <span data-ttu-id="c837f-182">"yyyy-yyyy '-'dd"</span><span class="sxs-lookup"><span data-stu-id="c837f-182">"yyyy'-'MM'-'dd"</span></span>            | <span data-ttu-id="c837f-183">Datum kalendáře</span><span class="sxs-lookup"><span data-stu-id="c837f-183">Calendar date</span></span>                                                                   |
| <span data-ttu-id="c837f-184">Plný čas</span><span class="sxs-lookup"><span data-stu-id="c837f-184">Full time</span></span>       | <span data-ttu-id="c837f-185">"' Partial time'K</span><span class="sxs-lookup"><span data-stu-id="c837f-185">"'Partial time'K"</span></span>           | <span data-ttu-id="c837f-186">UTC v den nebo místní čas s časovým posunem mezi místním časem a UTC</span><span class="sxs-lookup"><span data-stu-id="c837f-186">UTC of day or Local time of day with the time offset between local time and UTC</span></span> |
| <span data-ttu-id="c837f-187">Datum a čas</span><span class="sxs-lookup"><span data-stu-id="c837f-187">Date time</span></span>       | <span data-ttu-id="c837f-188">"" Celé datum "nemá plný čas" "</span><span class="sxs-lookup"><span data-stu-id="c837f-188">"'Full date''T''Full time'"</span></span> | <span data-ttu-id="c837f-189">Datum a čas kalendáře, např. 2019-07-26T16:59:57-05:00</span><span class="sxs-lookup"><span data-stu-id="c837f-189">Calendar date and time of day, e.g. 2019-07-26T16:59:57-05:00</span></span>                   |

### <a name="support-for-parsing"></a><span data-ttu-id="c837f-190">Podpora pro analýzu</span><span class="sxs-lookup"><span data-stu-id="c837f-190">Support for parsing</span></span>

<span data-ttu-id="c837f-191">Pro analýzu jsou definovány následující úrovně členitosti:</span><span class="sxs-lookup"><span data-stu-id="c837f-191">The following levels of granularity are defined for parsing:</span></span>

1. <span data-ttu-id="c837f-192">"Celé datum"</span><span class="sxs-lookup"><span data-stu-id="c837f-192">'Full date'</span></span>
    1. <span data-ttu-id="c837f-193">"yyyy-yyyy '-'dd"</span><span class="sxs-lookup"><span data-stu-id="c837f-193">"yyyy'-'MM'-'dd"</span></span>

2. <span data-ttu-id="c837f-194">"" Celé datum "t" hodina "": "min" "</span><span class="sxs-lookup"><span data-stu-id="c837f-194">"'Full date''T''Hour'':''Minute'"</span></span>
    1. <span data-ttu-id="c837f-195">"yyyy-yyyy '-DD 't": "mm"</span><span class="sxs-lookup"><span data-stu-id="c837f-195">"yyyy'-'MM'-'dd'T'HH':'mm"</span></span>

3. <span data-ttu-id="c837f-196">"" Celé datum "t" v částečný čas ""</span><span class="sxs-lookup"><span data-stu-id="c837f-196">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="c837f-197">"yyyy-yyyy '-DD 't": ' mm ': ' ss ' ([specifikátor formátu ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="c837f-197">"yyyy'-'MM'-'dd'T'HH':'mm':'ss" ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>
    2. <span data-ttu-id="c837f-198">"yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="c837f-198">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

4. <span data-ttu-id="c837f-199">"" Celé datum "t" Časová hodina "": minuta "časový posun" "</span><span class="sxs-lookup"><span data-stu-id="c837f-199">"'Full date''T''Time hour'':''Minute''Time offset'"</span></span>
    1. <span data-ttu-id="c837f-200">"yyyy-yyyy '-DD 't": ' mmZ '</span><span class="sxs-lookup"><span data-stu-id="c837f-200">"yyyy'-'MM'-'dd'T'HH':'mmZ"</span></span>
    2. <span data-ttu-id="c837f-201">"yyyy-yyyy '-DD 't": ' mm (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="c837f-201">"yyyy'-'MM'-'dd'T'HH':'mm('+'/'-')HH':'mm"</span></span>

5. <span data-ttu-id="c837f-202">' Datum a čas '</span><span class="sxs-lookup"><span data-stu-id="c837f-202">'Date time'</span></span>
    1. <span data-ttu-id="c837f-203">"yyyy-yyyy '-DD 't": ' mm ': ' ssZ '</span><span class="sxs-lookup"><span data-stu-id="c837f-203">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>
    2. <span data-ttu-id="c837f-204">"yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFFZ"</span><span class="sxs-lookup"><span data-stu-id="c837f-204">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>
    3. <span data-ttu-id="c837f-205">"yyyy-yyyy '-DD 't": ' mm ': ' ss ' (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="c837f-205">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>
    4. <span data-ttu-id="c837f-206">"yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF (+ '/'-') HH ': mm</span><span class="sxs-lookup"><span data-stu-id="c837f-206">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

<span data-ttu-id="c837f-207">Pokud pro sekundy existují desetinné zlomky, musí existovat alespoň jedna číslice. `2019-07-26T00:00:00.` není povolená.</span><span class="sxs-lookup"><span data-stu-id="c837f-207">If there are decimal fractions for seconds, there must be at least one digit; `2019-07-26T00:00:00.` is not allowed.</span></span>
<span data-ttu-id="c837f-208">I když je povolený až 16 zlomkových číslic, analyzují se jenom prvních sedm.</span><span class="sxs-lookup"><span data-stu-id="c837f-208">While up to 16 fractional digits are allowed, only the first seven are parsed.</span></span> <span data-ttu-id="c837f-209">Vše nad rámec, který je považován za nulu.</span><span class="sxs-lookup"><span data-stu-id="c837f-209">Anything beyond that is considered a zero.</span></span>
<span data-ttu-id="c837f-210">Například `2019-07-26T00:00:00.1234567890` bude analyzován jako `2019-07-26T00:00:00.1234567`.</span><span class="sxs-lookup"><span data-stu-id="c837f-210">For example, `2019-07-26T00:00:00.1234567890` will be parsed as if it is `2019-07-26T00:00:00.1234567`.</span></span>
<span data-ttu-id="c837f-211">To je udržování kompatibility s implementací <xref:System.DateTime>, což je omezené na toto řešení.</span><span class="sxs-lookup"><span data-stu-id="c837f-211">This is to stay compatible with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>

<span data-ttu-id="c837f-212">Přestupné sekundy nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="c837f-212">Leap seconds are not supported.</span></span>

### <a name="support-for-formatting"></a><span data-ttu-id="c837f-213">Podpora formátování</span><span class="sxs-lookup"><span data-stu-id="c837f-213">Support for formatting</span></span>

<span data-ttu-id="c837f-214">Pro formátování jsou definovány následující úrovně členitosti:</span><span class="sxs-lookup"><span data-stu-id="c837f-214">The following levels of granularity are defined for formatting:</span></span>

1. <span data-ttu-id="c837f-215">"" Celé datum "t" v částečný čas ""</span><span class="sxs-lookup"><span data-stu-id="c837f-215">"'Full date''T''Partial time'"</span></span>
    1. <span data-ttu-id="c837f-216">"yyyy-yyyy '-DD 't": ' mm ': ' ss ' ([specifikátor formátu ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span><span class="sxs-lookup"><span data-stu-id="c837f-216">"yyyy'-'MM'-'dd'T'HH':'mm':'ss"  ([The Sortable ("s") Format Specifier](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))</span></span>

        <span data-ttu-id="c837f-217">Slouží k formátování <xref:System.DateTime> bez zlomků sekund a bez informací o posunu.</span><span class="sxs-lookup"><span data-stu-id="c837f-217">Used to format a <xref:System.DateTime> without fractional seconds and without offset information.</span></span>

    2. <span data-ttu-id="c837f-218">"yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF</span><span class="sxs-lookup"><span data-stu-id="c837f-218">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF"</span></span>

        <span data-ttu-id="c837f-219">Slouží k formátování <xref:System.DateTime> s zlomky sekund, ale bez informací o posunu.</span><span class="sxs-lookup"><span data-stu-id="c837f-219">Used to format a <xref:System.DateTime> with fractional seconds but without offset information.</span></span>

2. <span data-ttu-id="c837f-220">' Datum a čas '</span><span class="sxs-lookup"><span data-stu-id="c837f-220">'Date time'</span></span>
    1. <span data-ttu-id="c837f-221">"yyyy-yyyy '-DD 't": ' mm ': ' ssZ '</span><span class="sxs-lookup"><span data-stu-id="c837f-221">"yyyy'-'MM'-'dd'T'HH':'mm':'ssZ"</span></span>

        <span data-ttu-id="c837f-222">Slouží k formátování <xref:System.DateTime> bez zlomků sekund, ale s posunem UTC.</span><span class="sxs-lookup"><span data-stu-id="c837f-222">Used to format a <xref:System.DateTime> without fractional seconds but with a UTC offset.</span></span>

    2. <span data-ttu-id="c837f-223">"yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFFZ"</span><span class="sxs-lookup"><span data-stu-id="c837f-223">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFFZ"</span></span>

        <span data-ttu-id="c837f-224">Slouží k formátování <xref:System.DateTime> se zlomkem sekund a s posunem UTC.</span><span class="sxs-lookup"><span data-stu-id="c837f-224">Used to format a <xref:System.DateTime> with fractional seconds and with a UTC offset.</span></span>

    3. <span data-ttu-id="c837f-225">"yyyy-yyyy '-DD 't": ' mm ': ' ss ' (' + '/'-') HH ': ' mm '</span><span class="sxs-lookup"><span data-stu-id="c837f-225">"yyyy'-'MM'-'dd'T'HH':'mm':'ss('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="c837f-226">Slouží k formátování <xref:System.DateTime> nebo <xref:System.DateTimeOffset> bez zlomkových sekund, ale s lokálním posunem.</span><span class="sxs-lookup"><span data-stu-id="c837f-226">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> without fractional seconds but with a local offset.</span></span>

    4. <span data-ttu-id="c837f-227">"yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF (+ '/'-') HH ': mm</span><span class="sxs-lookup"><span data-stu-id="c837f-227">"yyyy'-'MM'-'dd'T'HH':'mm':'ss'.'FFFFFFF('+'/'-')HH':'mm"</span></span>

        <span data-ttu-id="c837f-228">Slouží k formátování <xref:System.DateTime> nebo <xref:System.DateTimeOffset> se zlomky sekund a s místním posunem.</span><span class="sxs-lookup"><span data-stu-id="c837f-228">Used to format a <xref:System.DateTime> or <xref:System.DateTimeOffset> with fractional seconds and with a local offset.</span></span>

<span data-ttu-id="c837f-229">Je-li k dispozici, je zapsána maximálně 7 zlomkových číslic.</span><span class="sxs-lookup"><span data-stu-id="c837f-229">If present, a maximum of 7 fractional digits are written.</span></span> <span data-ttu-id="c837f-230">Tím se zarovnává s implementací <xref:System.DateTime>, která je omezena na toto řešení.</span><span class="sxs-lookup"><span data-stu-id="c837f-230">This aligns with the <xref:System.DateTime> implementation, which is limited to this resolution.</span></span>
