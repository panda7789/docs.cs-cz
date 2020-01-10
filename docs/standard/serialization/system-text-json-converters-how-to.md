---
title: Zápis vlastních převaděčů pro serializaci JSON – .NET
ms.date: 10/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: efbaf852f07b2b59111f0e330cf52470e3eca4c3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705805"
---
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a><span data-ttu-id="70f35-102">Zápis vlastních převaděčů pro serializaci JSON v .NET</span><span class="sxs-lookup"><span data-stu-id="70f35-102">How to write custom converters for JSON serialization in .NET</span></span>

<span data-ttu-id="70f35-103">Tento článek ukazuje, jak vytvořit vlastní převaděče pro třídy serializace JSON, které jsou k dispozici v oboru názvů <xref:System.Text.Json>.</span><span class="sxs-lookup"><span data-stu-id="70f35-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="70f35-104">Úvod do `System.Text.Json`naleznete [v tématu How to serializovat and deserializovat JSON v rozhraní .NET](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="70f35-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="70f35-105">*Převodník* je třída, která převádí objekt nebo hodnotu na a z formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="70f35-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="70f35-106">Obor názvů `System.Text.Json` obsahuje integrované převaděče pro většinu primitivních typů, které jsou mapovány na primitivní prvky jazyka JavaScript.</span><span class="sxs-lookup"><span data-stu-id="70f35-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="70f35-107">Můžete psát vlastní převaděče:</span><span class="sxs-lookup"><span data-stu-id="70f35-107">You can write custom converters:</span></span>

* <span data-ttu-id="70f35-108">Chcete-li přepsat výchozí chování vestavěného převaděče.</span><span class="sxs-lookup"><span data-stu-id="70f35-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="70f35-109">Můžete například chtít, aby byly hodnoty `DateTime` ve formátu mm/dd/rrrr namísto výchozího formátu ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="70f35-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="70f35-110">Pro podporu vlastního typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="70f35-110">To support a custom value type.</span></span> <span data-ttu-id="70f35-111">Například struktura `PhoneNumber`.</span><span class="sxs-lookup"><span data-stu-id="70f35-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="70f35-112">Můžete také napsat vlastní převaděče pro rozšiřování `System.Text.Json` s funkcemi, které nejsou součástí aktuální verze.</span><span class="sxs-lookup"><span data-stu-id="70f35-112">You can also write custom converters to extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="70f35-113">Následující scénáře jsou pokryté dále v tomto článku:</span><span class="sxs-lookup"><span data-stu-id="70f35-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="70f35-114">[Deserializace odvozených typů do vlastností objektu](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="70f35-114">[Deserialize inferred types to Object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="70f35-115">[Slovník podpory s jiným neřetězcovým klíčem](#support-dictionary-with-non-string-key)</span><span class="sxs-lookup"><span data-stu-id="70f35-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="70f35-116">[Podpora polymorfního deserializace](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="70f35-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="70f35-117">Vlastní vzory převaděče</span><span class="sxs-lookup"><span data-stu-id="70f35-117">Custom converter patterns</span></span>

<span data-ttu-id="70f35-118">Existují dva vzory pro vytvoření vlastního převaděče: základní vzor a model továrny.</span><span class="sxs-lookup"><span data-stu-id="70f35-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="70f35-119">Vzor továrny je pro převaděče, které zpracovávají typ `Enum` nebo otevřít obecné typy.</span><span class="sxs-lookup"><span data-stu-id="70f35-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="70f35-120">Základní vzor je pro neobecný a uzavřený obecný typ.</span><span class="sxs-lookup"><span data-stu-id="70f35-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="70f35-121">Například převaděče pro následující typy vyžadují model továrny:</span><span class="sxs-lookup"><span data-stu-id="70f35-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="70f35-122">Mezi příklady typů, které lze zpracovat pomocí základního vzoru, patří:</span><span class="sxs-lookup"><span data-stu-id="70f35-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="70f35-123">Základní vzor vytvoří třídu, která může zpracovat jeden typ.</span><span class="sxs-lookup"><span data-stu-id="70f35-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="70f35-124">Model továrny vytvoří třídu, která určuje za běhu, který konkrétní typ vyžaduje, a dynamicky vytvoří odpovídající převaděč.</span><span class="sxs-lookup"><span data-stu-id="70f35-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="70f35-125">Ukázka základního převaděče</span><span class="sxs-lookup"><span data-stu-id="70f35-125">Sample basic converter</span></span>

<span data-ttu-id="70f35-126">Následující ukázka je převaděč, který přepisuje výchozí serializaci pro existující datový typ.</span><span class="sxs-lookup"><span data-stu-id="70f35-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="70f35-127">Převaděč používá formát mm/dd/rrrr pro `DateTimeOffset` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="70f35-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="70f35-128">Ukázkový konvertor vzorků výrobního modelu</span><span class="sxs-lookup"><span data-stu-id="70f35-128">Sample factory pattern converter</span></span>

<span data-ttu-id="70f35-129">Následující kód ukazuje vlastní převaděč, který pracuje s `Dictionary<Enum,TValue>`.</span><span class="sxs-lookup"><span data-stu-id="70f35-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="70f35-130">Kód řídí model továrny, protože první parametr obecného typu je `Enum` a druhý je otevřen.</span><span class="sxs-lookup"><span data-stu-id="70f35-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="70f35-131">Metoda `CanConvert` vrací `true` pouze pro `Dictionary` se dvěma obecnými parametry, první z nich je `Enum` typ.</span><span class="sxs-lookup"><span data-stu-id="70f35-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="70f35-132">Vnitřní převaděč získá existující převaděč, který zpracuje typ, který je poskytován za běhu pro `TValue`.</span><span class="sxs-lookup"><span data-stu-id="70f35-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span> 

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="70f35-133">Předchozí kód je stejný jako ten, který je zobrazen ve [slovníku podpory s jiným než řetězcovým klíčem](#support-dictionary-with-non-string-key) , dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="70f35-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="70f35-134">Postup pro postup pro základní vzor</span><span class="sxs-lookup"><span data-stu-id="70f35-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="70f35-135">Následující postup vysvětluje, jak vytvořit převaděč podle základního vzoru:</span><span class="sxs-lookup"><span data-stu-id="70f35-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="70f35-136">Vytvořte třídu, která je odvozena z <xref:System.Text.Json.Serialization.JsonConverter%601>, kde `T` je typ k serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="70f35-136">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="70f35-137">Přepište metodu `Read` pro deserializaci příchozího JSON a převeďte ji na typ `T`.</span><span class="sxs-lookup"><span data-stu-id="70f35-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="70f35-138">Použijte <xref:System.Text.Json.Utf8JsonReader>, která je předána metodě pro čtení formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="70f35-138">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="70f35-139">Přepište metodu `Write` k serializaci příchozího objektu typu `T`.</span><span class="sxs-lookup"><span data-stu-id="70f35-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="70f35-140">Použijte <xref:System.Text.Json.Utf8JsonWriter>, která je předána metodě pro zápis formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="70f35-140">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="70f35-141">Metodu `CanConvert` popište pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="70f35-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="70f35-142">Výchozí implementace vrátí `true`, když typ, který má být převeden, je typ `T`.</span><span class="sxs-lookup"><span data-stu-id="70f35-142">The default implementation returns `true` when the type to convert is type `T`.</span></span> <span data-ttu-id="70f35-143">Proto převaděče, které podporují pouze typ `T`, nemusejí přepsat tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="70f35-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="70f35-144">Příklad převaděče, který musí přepsat tuto metodu, naleznete v části [polymorfní deserializace](#support-polymorphic-deserialization) dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="70f35-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="70f35-145">Můžete odkazovat na [předdefinovaný zdrojový kód převaděče](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) jako referenční implementace pro psaní vlastních převaděčů.</span><span class="sxs-lookup"><span data-stu-id="70f35-145">You can refer to the [built-in converters source code](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="70f35-146">Postup pro postup pro model výroby</span><span class="sxs-lookup"><span data-stu-id="70f35-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="70f35-147">Následující postup vysvětluje, jak vytvořit převaděč podle vzorce pro vytváření:</span><span class="sxs-lookup"><span data-stu-id="70f35-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="70f35-148">Vytvořte třídu, která je odvozena z <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="70f35-148">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="70f35-149">Přepište metodu `CanConvert`, aby vracela hodnotu true, pokud je typ převodu ten, který může převaděč zpracovat.</span><span class="sxs-lookup"><span data-stu-id="70f35-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="70f35-150">Pokud je například převaděč určený pro `List<T>` může zpracovat pouze `List<int>`, `List<string>`a `List<DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="70f35-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span> 
* <span data-ttu-id="70f35-151">Přepište metodu `CreateConverter` pro vrácení instance třídy převaděče, která bude zpracovávat typ k převodu, který je k dispozici za běhu.</span><span class="sxs-lookup"><span data-stu-id="70f35-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="70f35-152">Vytvořte třídu převaděče, kterou vytváří instance metody `CreateConverter`.</span><span class="sxs-lookup"><span data-stu-id="70f35-152">Create the converter class that the `CreateConverter` method instantiates.</span></span> 

<span data-ttu-id="70f35-153">Model továrny je vyžadován pro otevřené generické typy, protože kód pro převod objektu na a z řetězce není stejný pro všechny typy.</span><span class="sxs-lookup"><span data-stu-id="70f35-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="70f35-154">Převaděč pro otevřený obecný typ (`List<T>`, například) musí vytvořit převaděč pro uzavřený obecný typ (`List<DateTime>`, například) na pozadí.</span><span class="sxs-lookup"><span data-stu-id="70f35-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="70f35-155">Kód musí být napsán pro zpracování každého uzavřeného a obecného typu, který může převaděč zpracovat.</span><span class="sxs-lookup"><span data-stu-id="70f35-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="70f35-156">Typ `Enum` je podobný otevřenému obecnému typu: převaděč pro `Enum` musí vytvořit převaděč pro konkrétní `Enum` (například`WeekdaysEnum`) na pozadí.</span><span class="sxs-lookup"><span data-stu-id="70f35-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span> 

## <a name="error-handling"></a><span data-ttu-id="70f35-157">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="70f35-157">Error handling</span></span>

<span data-ttu-id="70f35-158">Pokud potřebujete vyvolat výjimku v kódu pro zpracování chyb, zvažte vyvolání <xref:System.Text.Json.JsonException> bez zprávy.</span><span class="sxs-lookup"><span data-stu-id="70f35-158">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="70f35-159">Tento typ výjimky automaticky vytvoří zprávu, která obsahuje cestu k části JSON, která způsobila chybu.</span><span class="sxs-lookup"><span data-stu-id="70f35-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="70f35-160">Například příkaz `throw new JsonException();` vytvoří chybovou zprávu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="70f35-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="70f35-161">Pokud zadáte zprávu (například `throw new JsonException("Error occurred")`, výjimka stále poskytne cestu ve vlastnosti <xref:System.Text.Json.JsonException.Path>.</span><span class="sxs-lookup"><span data-stu-id="70f35-161">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="70f35-162">Registrace vlastního převaděče</span><span class="sxs-lookup"><span data-stu-id="70f35-162">Register a custom converter</span></span>

<span data-ttu-id="70f35-163">*Zaregistrujte* vlastní převaděč a nastavte `Serialize` a metody `Deserialize` ho použít.</span><span class="sxs-lookup"><span data-stu-id="70f35-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="70f35-164">Vyberte jeden z následujících přístupů:</span><span class="sxs-lookup"><span data-stu-id="70f35-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="70f35-165">Přidejte instanci třídy Converter do kolekce <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="70f35-165">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="70f35-166">Použijte atribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) pro vlastnosti, které vyžadují vlastní převaděč.</span><span class="sxs-lookup"><span data-stu-id="70f35-166">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="70f35-167">Použijte atribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) pro třídu nebo strukturu, která představuje vlastní typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="70f35-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="70f35-168">Registrace ukázek – kolekce převaděčů</span><span class="sxs-lookup"><span data-stu-id="70f35-168">Registration sample - Converters collection</span></span> 

<span data-ttu-id="70f35-169">Tady je příklad, který nastaví <xref:System.ComponentModel.DateTimeOffsetConverter> jako výchozí pro vlastnosti typu <xref:System.DateTimeOffset>:</span><span class="sxs-lookup"><span data-stu-id="70f35-169">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="70f35-170">Předpokládejme, že jste serializováni instanci následujícího typu:</span><span class="sxs-lookup"><span data-stu-id="70f35-170">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="70f35-171">Tady je příklad výstupu JSON, který ukazuje použití vlastního převaděče:</span><span class="sxs-lookup"><span data-stu-id="70f35-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="70f35-172">Následující kód používá stejný přístup k deserializaci pomocí vlastního převaděče `DateTimeOffset`:</span><span class="sxs-lookup"><span data-stu-id="70f35-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="70f35-173">Ukázka registrace – [JsonConverter] u vlastnosti</span><span class="sxs-lookup"><span data-stu-id="70f35-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="70f35-174">Následující kód vybere vlastní převaděč pro vlastnost `Date`:</span><span class="sxs-lookup"><span data-stu-id="70f35-174">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="70f35-175">Kód pro serializaci `WeatherForecastWithConverterAttribute` nevyžaduje použití `JsonSerializeOptions.Converters`:</span><span class="sxs-lookup"><span data-stu-id="70f35-175">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="70f35-176">Kód k deserializaci také nevyžaduje použití `Converters`:</span><span class="sxs-lookup"><span data-stu-id="70f35-176">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="70f35-177">Ukázka registrace – [JsonConverter] na typu</span><span class="sxs-lookup"><span data-stu-id="70f35-177">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="70f35-178">Zde je kód, který vytvoří strukturu a na ni aplikuje atribut `[JsonConverter]`:</span><span class="sxs-lookup"><span data-stu-id="70f35-178">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Temperature.cs)]

<span data-ttu-id="70f35-179">Tady je vlastní převaděč pro předchozí strukturu:</span><span class="sxs-lookup"><span data-stu-id="70f35-179">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/TemperatureConverter.cs)]

<span data-ttu-id="70f35-180">Atribut `[JsonConvert]` ve struktuře registruje vlastní převaděč jako výchozí hodnotu pro vlastnosti typu `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="70f35-180">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="70f35-181">Při serializaci nebo deserializaci se převaděč automaticky použije na vlastnost `TemperatureCelsius` následujícího typu:</span><span class="sxs-lookup"><span data-stu-id="70f35-181">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="70f35-182">Priorita registrace převaděče</span><span class="sxs-lookup"><span data-stu-id="70f35-182">Converter registration precedence</span></span>

<span data-ttu-id="70f35-183">Při serializaci nebo deserializaci se pro každý prvek JSON v uvedeném pořadí vybere konvertor, který je uvedený z nejvyšší priority na nejnižší:</span><span class="sxs-lookup"><span data-stu-id="70f35-183">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="70f35-184">`[JsonConverter]` použito pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="70f35-184">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="70f35-185">Převaděč přidaný do kolekce `Converters`.</span><span class="sxs-lookup"><span data-stu-id="70f35-185">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="70f35-186">`[JsonConverter]` použito pro vlastní typ hodnoty nebo POCO.</span><span class="sxs-lookup"><span data-stu-id="70f35-186">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="70f35-187">Pokud je v kolekci `Converters` zaregistrováno více vlastních převaděčů pro typ, je použit první převaděč, který vrací hodnotu true pro `CanConvert`.</span><span class="sxs-lookup"><span data-stu-id="70f35-187">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="70f35-188">Vestavěný převaděč je zvolen pouze v případě, že není registrován žádný použitelný vlastní převaděč.</span><span class="sxs-lookup"><span data-stu-id="70f35-188">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="70f35-189">Ukázky převaděčů pro běžné scénáře</span><span class="sxs-lookup"><span data-stu-id="70f35-189">Converter samples for common scenarios</span></span>

<span data-ttu-id="70f35-190">V následujících částech jsou uvedeny ukázky konvertorů, které řeší některé běžné scénáře, které vestavěná funkce nezpracovává.</span><span class="sxs-lookup"><span data-stu-id="70f35-190">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

* [<span data-ttu-id="70f35-191">Deserializace odvozených typů do vlastností objektu</span><span class="sxs-lookup"><span data-stu-id="70f35-191">Deserialize inferred types to Object properties</span></span>](#deserialize-inferred-types-to-object-properties)
* [<span data-ttu-id="70f35-192">Slovník podpory s jiným neřetězcovým klíčem</span><span class="sxs-lookup"><span data-stu-id="70f35-192">Support Dictionary with non-string key</span></span>](#support-dictionary-with-non-string-key)
* [<span data-ttu-id="70f35-193">Podpora polymorfního deserializace</span><span class="sxs-lookup"><span data-stu-id="70f35-193">Support polymorphic deserialization</span></span>](#support-polymorphic-deserialization)

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="70f35-194">Deserializace odvozených typů do vlastností objektu</span><span class="sxs-lookup"><span data-stu-id="70f35-194">Deserialize inferred types to Object properties</span></span>

<span data-ttu-id="70f35-195">Při deserializaci na vlastnost typu `Object`je vytvořen objekt `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="70f35-195">When deserializing to a property of type `Object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="70f35-196">Důvodem je, že deserializátor nezná typ CLR, který se má vytvořit, a nepokusí se odhadnout.</span><span class="sxs-lookup"><span data-stu-id="70f35-196">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="70f35-197">Například pokud má vlastnost JSON hodnotu "true", deserializátor neodvodí, že hodnota je `Boolean`a pokud má element "01/01/2019", deserializátor neodvodí, že se jedná o `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="70f35-197">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="70f35-198">Odvození typu může být nepřesné.</span><span class="sxs-lookup"><span data-stu-id="70f35-198">Type inference can be inaccurate.</span></span> <span data-ttu-id="70f35-199">Pokud deserializátor analyzuje číslo JSON, které nemá žádné desetinné místo jako `long`, což může vést k problémům mimo rozsah, pokud byla hodnota původně serializována jako `ulong` nebo `BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="70f35-199">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="70f35-200">Analýza čísla s desetinnou čárkou jako `double` může přijít o přesnost, pokud bylo číslo původně serializováno jako `decimal`.</span><span class="sxs-lookup"><span data-stu-id="70f35-200">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="70f35-201">Pro scénáře, které vyžadují odvození typu, ukazuje následující kód vlastní převaděč pro `Object` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="70f35-201">For scenarios that require type inference, the following code shows a custom converter for `Object` properties.</span></span> <span data-ttu-id="70f35-202">Kód převede:</span><span class="sxs-lookup"><span data-stu-id="70f35-202">The code converts:</span></span>

* <span data-ttu-id="70f35-203">`true` a `false` na `Boolean`</span><span class="sxs-lookup"><span data-stu-id="70f35-203">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="70f35-204">Čísla `long` nebo `double`</span><span class="sxs-lookup"><span data-stu-id="70f35-204">Numbers to `long` or `double`</span></span>
* <span data-ttu-id="70f35-205">Kalendářní data `DateTime`</span><span class="sxs-lookup"><span data-stu-id="70f35-205">Dates to `DateTime`</span></span>
* <span data-ttu-id="70f35-206">Řetězce, které se mají `string`</span><span class="sxs-lookup"><span data-stu-id="70f35-206">Strings to `string`</span></span>
* <span data-ttu-id="70f35-207">Všechno ostatní `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="70f35-207">Everything else to `JsonElement`</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="70f35-208">Následující kód registruje převaděč:</span><span class="sxs-lookup"><span data-stu-id="70f35-208">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="70f35-209">Tady je příklad typu s `Object`mi vlastnostmi:</span><span class="sxs-lookup"><span data-stu-id="70f35-209">Here's an example type with `Object` properties:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="70f35-210">Následující příklad JSON pro deserializaci obsahuje hodnoty, které budou deserializovat jako `DateTime`, `long`a `string`:</span><span class="sxs-lookup"><span data-stu-id="70f35-210">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="70f35-211">Bez vlastního převaděče je deserializace v každé vlastnosti `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="70f35-211">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="70f35-212">[Složka testování částí](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) v oboru názvů `System.Text.Json.Serialization` obsahuje další příklady vlastních převaděčů, které zpracovávají deserializaci na vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="70f35-212">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to Object properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="70f35-213">Slovník podpory s jiným neřetězcovým klíčem</span><span class="sxs-lookup"><span data-stu-id="70f35-213">Support Dictionary with non-string key</span></span>

<span data-ttu-id="70f35-214">Integrovaná podpora pro kolekce slovníků je určena pro `Dictionary<string, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="70f35-214">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="70f35-215">To znamená, že klíč musí být řetězec.</span><span class="sxs-lookup"><span data-stu-id="70f35-215">That is, the key must be a string.</span></span> <span data-ttu-id="70f35-216">Pro podporu slovníku s celým číslem nebo jiným typem jako klíč je vyžadován vlastní převaděč.</span><span class="sxs-lookup"><span data-stu-id="70f35-216">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="70f35-217">Následující kód ukazuje vlastní převaděč, který spolupracuje s `Dictionary<Enum,TValue>`:</span><span class="sxs-lookup"><span data-stu-id="70f35-217">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="70f35-218">Následující kód registruje převaděč:</span><span class="sxs-lookup"><span data-stu-id="70f35-218">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="70f35-219">Konvertor může serializovat a deserializovat vlastnost `TemperatureRanges` následující třídy, která používá následující `Enum`:</span><span class="sxs-lookup"><span data-stu-id="70f35-219">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="70f35-220">Výstup JSON z serializace vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="70f35-220">The JSON output from serialization looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

<span data-ttu-id="70f35-221">[Složka testování částí](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) v oboru názvů `System.Text.Json.Serialization` obsahuje další příklady vlastních převaděčů, které zpracovávají slovníky neřetězcových klíčů.</span><span class="sxs-lookup"><span data-stu-id="70f35-221">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="70f35-222">Podpora polymorfního deserializace</span><span class="sxs-lookup"><span data-stu-id="70f35-222">Support polymorphic deserialization</span></span>

<span data-ttu-id="70f35-223">[Polymorfní serializace](system-text-json-how-to.md#serialize-properties-of-derived-classes) nevyžaduje vlastní převaděč, ale deserializace vyžaduje vlastní převaděč.</span><span class="sxs-lookup"><span data-stu-id="70f35-223">[Polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) doesn't require a custom converter, but deserialization does require a custom converter.</span></span>

<span data-ttu-id="70f35-224">Předpokládejme například, že máte abstraktní základní třídu `Person` s `Employee` a `Customer` odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="70f35-224">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="70f35-225">Polymorfní deserializace znamená, že v době návrhu můžete zadat `Person` jako cíl deserializace a `Customer` a `Employee` objekty ve formátu JSON jsou správně deserializovány za běhu.</span><span class="sxs-lookup"><span data-stu-id="70f35-225">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="70f35-226">Během deserializace je nutné najít podoby, které identifikují požadovaný typ ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="70f35-226">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="70f35-227">Typy, které jsou k dispozici, se liší podle jednotlivých scénářů.</span><span class="sxs-lookup"><span data-stu-id="70f35-227">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="70f35-228">Například může být k dispozici vlastnost diskriminátoru nebo může být nutné spoléhat na přítomnost určité vlastnosti nebo absence konkrétní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="70f35-228">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="70f35-229">Aktuální verze `System.Text.Json` neposkytuje atributy pro určení způsobu zpracování polymorfních scénářů deserializace, takže jsou vyžadovány vlastní převaděče.</span><span class="sxs-lookup"><span data-stu-id="70f35-229">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="70f35-230">Následující kód ukazuje základní třídu, dvě odvozené třídy a vlastní konvertor pro ně.</span><span class="sxs-lookup"><span data-stu-id="70f35-230">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="70f35-231">Převaděč používá vlastnost diskriminátor k provedení polymorfního deserializace.</span><span class="sxs-lookup"><span data-stu-id="70f35-231">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="70f35-232">Diskriminátor typu není v definicích třídy, ale je vytvořen během serializace a je čten během deserializace.</span><span class="sxs-lookup"><span data-stu-id="70f35-232">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="70f35-233">Následující kód registruje převaděč:</span><span class="sxs-lookup"><span data-stu-id="70f35-233">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="70f35-234">Konvertor může deserializovat JSON, který byl vytvořen pomocí stejného převaděče k serializaci, například:</span><span class="sxs-lookup"><span data-stu-id="70f35-234">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

## <a name="other-custom-converter-samples"></a><span data-ttu-id="70f35-235">Další ukázky vlastního převaděče</span><span class="sxs-lookup"><span data-stu-id="70f35-235">Other custom converter samples</span></span>

<span data-ttu-id="70f35-236">[Složka testování částí](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) ve zdrojovém kódu `System.Text.Json.Serialization` obsahuje další ukázky vlastního převaděče, jako například:</span><span class="sxs-lookup"><span data-stu-id="70f35-236">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="70f35-237">převaděč `Int32`, který při deserializaci převede hodnotu null na 0</span><span class="sxs-lookup"><span data-stu-id="70f35-237">`Int32` converter that converts null to 0 on deserialize</span></span>
* <span data-ttu-id="70f35-238">převaděč `Int32`, který umožňuje v případě deserializace řetězcové i číselné hodnoty</span><span class="sxs-lookup"><span data-stu-id="70f35-238">`Int32` converter that allows both string and number values on deserialize</span></span>
* <span data-ttu-id="70f35-239">převaděč `Enum`</span><span class="sxs-lookup"><span data-stu-id="70f35-239">`Enum` converter</span></span>
* <span data-ttu-id="70f35-240">převaděč `List<T>`, který přijímá externí data</span><span class="sxs-lookup"><span data-stu-id="70f35-240">`List<T>` converter that accepts external data</span></span>
* <span data-ttu-id="70f35-241">převaděč `Long[]`, který pracuje se seznamem čísel oddělených čárkami</span><span class="sxs-lookup"><span data-stu-id="70f35-241">`Long[]` converter that works with a comma-delimited list of numbers</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="70f35-242">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="70f35-242">Additional resources</span></span>

* [<span data-ttu-id="70f35-243">Přehled System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="70f35-243">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="70f35-244">Reference k rozhraní API System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="70f35-244">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="70f35-245">Jak používat System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="70f35-245">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="70f35-246">Zdrojový kód pro předdefinované převaděče</span><span class="sxs-lookup"><span data-stu-id="70f35-246">Source code for built-in converters</span></span>](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* <span data-ttu-id="70f35-247">Problémy GitHubu související s vlastními převaděči pro `System.Text.Json`</span><span class="sxs-lookup"><span data-stu-id="70f35-247">GitHub issues related to custom converters for `System.Text.Json`</span></span>
  * [<span data-ttu-id="70f35-248">36639 Představujeme vlastní převaděče</span><span class="sxs-lookup"><span data-stu-id="70f35-248">36639 Introducing custom converters</span></span>](https://github.com/dotnet/corefx/issues/36639)
  * [<span data-ttu-id="70f35-249">38713 o deserializaci do objektu</span><span class="sxs-lookup"><span data-stu-id="70f35-249">38713 About deserializing to Object</span></span>](https://github.com/dotnet/corefx/issues/38713)
  * [<span data-ttu-id="70f35-250">40120 o slovnících bez řetězcových klíčů</span><span class="sxs-lookup"><span data-stu-id="70f35-250">40120 About non-string-key dictionaries</span></span>](https://github.com/dotnet/corefx/issues/40120)
  * [<span data-ttu-id="70f35-251">37787 o polymorfní deserializaci</span><span class="sxs-lookup"><span data-stu-id="70f35-251">37787 About polymorphic deserialization</span></span>](https://github.com/dotnet/corefx/issues/37787)
