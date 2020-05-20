---
title: ''
ms.date: ''
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords: []
ms.openlocfilehash: 69c11df8217ac6dbdddd98c550f084075b901ea6
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703605"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="3a7c7-101">Zápis vlastních převaděčů pro serializaci JSON (zařazování) v .NET</span><span class="sxs-lookup"><span data-stu-id="3a7c7-101">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="3a7c7-102">Tento článek ukazuje, jak vytvořit vlastní převaděče pro třídy serializace JSON, které jsou k dispozici v <xref:System.Text.Json> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-102">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="3a7c7-103">Úvod do najdete `System.Text.Json` [v tématu jak serializovat a deserializovat JSON v rozhraní .NET](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="3a7c7-103">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="3a7c7-104">*Převodník* je třída, která převádí objekt nebo hodnotu na a z formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-104">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="3a7c7-105">`System.Text.Json`Obor názvů obsahuje integrované převaděče pro většinu primitivních typů, které jsou mapovány na primitivní prvky jazyka JavaScript.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-105">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="3a7c7-106">Můžete psát vlastní převaděče:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-106">You can write custom converters:</span></span>

* <span data-ttu-id="3a7c7-107">Chcete-li přepsat výchozí chování vestavěného převaděče.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-107">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="3a7c7-108">Například můžete chtít, `DateTime` aby hodnoty byly reprezentovány ve formátu mm/dd/rrrr namísto výchozího formátu ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-108">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="3a7c7-109">Pro podporu vlastního typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-109">To support a custom value type.</span></span> <span data-ttu-id="3a7c7-110">Například `PhoneNumber` Struktura.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-110">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="3a7c7-111">Můžete také napsat vlastní převaděče pro přizpůsobení nebo rozšiřování `System.Text.Json` s funkcemi, které nejsou součástí aktuální verze.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-111">You can also write custom converters to customize or extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="3a7c7-112">Následující scénáře jsou pokryté dále v tomto článku:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-112">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="3a7c7-113">[Deserializace odvozených typů do vlastností objektu](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="3a7c7-113">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="3a7c7-114">[Slovník podpory s jiným neřetězcovým klíčem](#support-dictionary-with-non-string-key)</span><span class="sxs-lookup"><span data-stu-id="3a7c7-114">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="3a7c7-115">[Podpora polymorfního deserializace](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="3a7c7-115">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>
* <span data-ttu-id="3a7c7-116">[Podpora zpátečního přenosu pro zásobník \< T>](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="3a7c7-116">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="3a7c7-117">Vlastní vzory převaděče</span><span class="sxs-lookup"><span data-stu-id="3a7c7-117">Custom converter patterns</span></span>

<span data-ttu-id="3a7c7-118">Existují dva vzory pro vytvoření vlastního převaděče: základní vzor a model továrny.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="3a7c7-119">Vzor továrny je pro převaděče, které zpracovávají typy `Enum` nebo otevřou obecné typy.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="3a7c7-120">Základní vzor je pro neobecný a uzavřený obecný typ.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="3a7c7-121">Například převaděče pro následující typy vyžadují model továrny:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="3a7c7-122">Mezi příklady typů, které lze zpracovat pomocí základního vzoru, patří:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="3a7c7-123">Základní vzor vytvoří třídu, která může zpracovat jeden typ.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="3a7c7-124">Model továrny vytvoří třídu, která určuje za běhu, který konkrétní typ vyžaduje, a dynamicky vytvoří odpovídající převaděč.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="3a7c7-125">Ukázka základního převaděče</span><span class="sxs-lookup"><span data-stu-id="3a7c7-125">Sample basic converter</span></span>

<span data-ttu-id="3a7c7-126">Následující ukázka je převaděč, který přepisuje výchozí serializaci pro existující datový typ.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="3a7c7-127">Převaděč používá pro vlastnosti formát mm/dd/rrrr `DateTimeOffset` .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="3a7c7-128">Ukázkový konvertor vzorků výrobního modelu</span><span class="sxs-lookup"><span data-stu-id="3a7c7-128">Sample factory pattern converter</span></span>

<span data-ttu-id="3a7c7-129">Následující kód ukazuje vlastní převaděč, který pracuje s `Dictionary<Enum,TValue>` .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="3a7c7-130">Kód se řídí modelem továrny, protože první parametr obecného typu je `Enum` a druhý je otevřený.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="3a7c7-131">`CanConvert`Metoda vrátí `true` pouze pro a `Dictionary` se dvěma obecnými parametry, první z nich je `Enum` typ.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="3a7c7-132">Vnitřní převaděč získá existující převaděč pro zpracování podle typu za běhu pro `TValue` .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="3a7c7-133">Předchozí kód je stejný jako ten, který je zobrazen ve [slovníku podpory s jiným než řetězcovým klíčem](#support-dictionary-with-non-string-key) , dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="3a7c7-134">Postup pro postup pro základní vzor</span><span class="sxs-lookup"><span data-stu-id="3a7c7-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="3a7c7-135">Následující postup vysvětluje, jak vytvořit převaděč podle základního vzoru:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="3a7c7-136">Vytvořte třídu, která je odvozena z <xref:System.Text.Json.Serialization.JsonConverter%601> Where `T` je typ k serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-136">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="3a7c7-137">Přepsat `Read` metodu pro deserializaci příchozího JSON a převést jej na typ `T` .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="3a7c7-138">Použijte <xref:System.Text.Json.Utf8JsonReader> metodu, která je předána metodě pro čtení formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-138">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="3a7c7-139">Přepsat `Write` metodu pro serializaci příchozího objektu typu `T` .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="3a7c7-140">Použijte <xref:System.Text.Json.Utf8JsonWriter> metodu, která je předána metodě pro zápis formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-140">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="3a7c7-141">Metodu popište `CanConvert` pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="3a7c7-142">Výchozí implementace vrátí, `true` když typ, který má být převeden, je typu `T` .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-142">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="3a7c7-143">Proto převaděče, které podporují pouze typ, `T` nemusejí přepisovat tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="3a7c7-144">Příklad převaděče, který musí přepsat tuto metodu, naleznete v části [polymorfní deserializace](#support-polymorphic-deserialization) dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="3a7c7-145">Můžete odkazovat na [předdefinovaný zdrojový kód převaděče](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) jako referenční implementace pro psaní vlastních převaděčů.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-145">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="3a7c7-146">Postup pro postup pro model výroby</span><span class="sxs-lookup"><span data-stu-id="3a7c7-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="3a7c7-147">Následující postup vysvětluje, jak vytvořit převaděč podle vzorce pro vytváření:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="3a7c7-148">Vytvořte třídu, která je odvozena z <xref:System.Text.Json.Serialization.JsonConverterFactory> .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-148">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="3a7c7-149">Přepsat `CanConvert` metodu pro vrácení hodnoty true, pokud typ, který má být převeden, je ten, který může převaděč zpracovat.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="3a7c7-150">Například pokud je převodník pro `List<T>` IT, může zpracovat pouze `List<int>` , `List<string>` , a `List<DateTime>` .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="3a7c7-151">Přepsat `CreateConverter` metodu pro vrácení instance třídy převaděče, která bude zpracovávat typ k převodu, který je k dispozici za běhu.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="3a7c7-152">Vytvořte třídu převaděče, kterou `CreateConverter` Metoda vytvoří.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-152">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="3a7c7-153">Model továrny je vyžadován pro otevřené generické typy, protože kód pro převod objektu na a z řetězce není stejný pro všechny typy.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="3a7c7-154">Převaděč pro otevřený obecný typ (například `List<T>` ) musí vytvořit převaděč pro uzavřený obecný typ ( `List<DateTime>` například) na pozadí.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="3a7c7-155">Kód musí být napsán pro zpracování každého uzavřeného a obecného typu, který může převaděč zpracovat.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="3a7c7-156">`Enum`Typ je podobný otevřenému obecnému typu: převaděč pro `Enum` musí vytvořit převodník pro konkrétní `Enum` ( `WeekdaysEnum` například) na pozadí.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="3a7c7-157">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="3a7c7-157">Error handling</span></span>

<span data-ttu-id="3a7c7-158">Pokud potřebujete vyvolat výjimku v kódu pro zpracování chyb, zvažte vyvolání <xref:System.Text.Json.JsonException> bez zprávy.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-158">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="3a7c7-159">Tento typ výjimky automaticky vytvoří zprávu, která obsahuje cestu k části JSON, která způsobila chybu.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="3a7c7-160">Například příkaz `throw new JsonException();` vytvoří chybovou zprávu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="3a7c7-161">Pokud zadáte zprávu (například `throw new JsonException("Error occurred")` , výjimka stále poskytuje cestu ve <xref:System.Text.Json.JsonException.Path> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-161">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="3a7c7-162">Registrace vlastního převaděče</span><span class="sxs-lookup"><span data-stu-id="3a7c7-162">Register a custom converter</span></span>

<span data-ttu-id="3a7c7-163">*Zaregistrujte* vlastní převaděč, pomocí kterého budou `Serialize` `Deserialize` metody a použity.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="3a7c7-164">Vyberte jeden z následujících přístupů:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="3a7c7-165">Přidejte do kolekce instanci třídy Converter <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-165">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="3a7c7-166">Použijte atribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) pro vlastnosti, které vyžadují vlastní převaděč.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-166">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="3a7c7-167">Použijte atribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) pro třídu nebo strukturu, která představuje vlastní typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="3a7c7-168">Registrace ukázek – kolekce převaděčů</span><span class="sxs-lookup"><span data-stu-id="3a7c7-168">Registration sample - Converters collection</span></span>

<span data-ttu-id="3a7c7-169">Tady je příklad, který nastaví <xref:System.ComponentModel.DateTimeOffsetConverter> výchozí nastavení pro vlastnosti typu <xref:System.DateTimeOffset> :</span><span class="sxs-lookup"><span data-stu-id="3a7c7-169">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="3a7c7-170">Předpokládejme, že jste serializováni instanci následujícího typu:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-170">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="3a7c7-171">Tady je příklad výstupu JSON, který ukazuje použití vlastního převaděče:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="3a7c7-172">Následující kód používá stejný přístup k deserializaci pomocí vlastního `DateTimeOffset` převaděče:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="3a7c7-173">Ukázka registrace – [JsonConverter] u vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3a7c7-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="3a7c7-174">Následující kód vybere vlastní převaděč pro `Date` vlastnost:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-174">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="3a7c7-175">Kód pro serializaci `WeatherForecastWithConverterAttribute` nevyžaduje použití `JsonSerializeOptions.Converters` :</span><span class="sxs-lookup"><span data-stu-id="3a7c7-175">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="3a7c7-176">Kód k deserializaci také nevyžaduje použití `Converters` :</span><span class="sxs-lookup"><span data-stu-id="3a7c7-176">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="3a7c7-177">Ukázka registrace – [JsonConverter] na typu</span><span class="sxs-lookup"><span data-stu-id="3a7c7-177">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="3a7c7-178">Zde je kód, který vytvoří strukturu a použije `[JsonConverter]` atribut na něj:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-178">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Temperature.cs)]

<span data-ttu-id="3a7c7-179">Tady je vlastní převaděč pro předchozí strukturu:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-179">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/TemperatureConverter.cs)]

<span data-ttu-id="3a7c7-180">`[JsonConvert]`Atribut ve struktuře registruje vlastní převaděč jako výchozí hodnotu vlastností typu `Temperature` .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-180">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="3a7c7-181">`TemperatureCelsius`Při serializaci nebo deserializaci se převaděč automaticky použije u vlastnosti následujícího typu:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-181">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="3a7c7-182">Priorita registrace převaděče</span><span class="sxs-lookup"><span data-stu-id="3a7c7-182">Converter registration precedence</span></span>

<span data-ttu-id="3a7c7-183">Při serializaci nebo deserializaci se pro každý prvek JSON v uvedeném pořadí vybere konvertor, který je uvedený z nejvyšší priority na nejnižší:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-183">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="3a7c7-184">`[JsonConverter]`použito pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-184">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="3a7c7-185">Převaděč přidaný do `Converters` kolekce.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-185">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="3a7c7-186">`[JsonConverter]`použito pro vlastní typ hodnoty nebo POCO.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-186">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="3a7c7-187">Pokud je v kolekci zaregistrováno více vlastních převaděčů pro typ `Converters` , je použit první převaděč, který vrací hodnotu true pro `CanConvert` .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-187">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="3a7c7-188">Vestavěný převaděč je zvolen pouze v případě, že není registrován žádný použitelný vlastní převaděč.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-188">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="3a7c7-189">Ukázky převaděčů pro běžné scénáře</span><span class="sxs-lookup"><span data-stu-id="3a7c7-189">Converter samples for common scenarios</span></span>

<span data-ttu-id="3a7c7-190">V následujících částech jsou uvedeny ukázky konvertorů, které řeší některé běžné scénáře, které vestavěná funkce nezpracovává.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-190">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

* [<span data-ttu-id="3a7c7-191">Deserializace odvozených typů do vlastností objektu</span><span class="sxs-lookup"><span data-stu-id="3a7c7-191">Deserialize inferred types to object properties</span></span>](#deserialize-inferred-types-to-object-properties)
* [<span data-ttu-id="3a7c7-192">Slovník podpory s jiným neřetězcovým klíčem</span><span class="sxs-lookup"><span data-stu-id="3a7c7-192">Support Dictionary with non-string key</span></span>](#support-dictionary-with-non-string-key)
* [<span data-ttu-id="3a7c7-193">Podpora polymorfního deserializace</span><span class="sxs-lookup"><span data-stu-id="3a7c7-193">Support polymorphic deserialization</span></span>](#support-polymorphic-deserialization)
* <span data-ttu-id="3a7c7-194">[Podpora zpátečního přenosu pro zásobník \< T>](#support-round-trip-for-stackt).</span><span class="sxs-lookup"><span data-stu-id="3a7c7-194">[Support round-trip for Stack\<T>](#support-round-trip-for-stackt).</span></span>

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="3a7c7-195">Deserializace odvozených typů do vlastností objektu</span><span class="sxs-lookup"><span data-stu-id="3a7c7-195">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="3a7c7-196">Při deserializaci na vlastnost typu `object` `JsonElement` je vytvořen objekt.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-196">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="3a7c7-197">Důvodem je, že deserializátor nezná typ CLR, který se má vytvořit, a nepokusí se odhadnout.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-197">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="3a7c7-198">Například pokud má vlastnost JSON hodnotu "true", deserializátor neodvodí, že hodnota je a `Boolean` Pokud má element "01/01/2019", deserializátor neodvodí, že se jedná o `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-198">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="3a7c7-199">Odvození typu může být nepřesné.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-199">Type inference can be inaccurate.</span></span> <span data-ttu-id="3a7c7-200">Pokud deserializátor analyzuje číslo JSON, které nemá desetinnou čárku jako `long` , což může vést k problémům mimo rozsah, pokud byla hodnota původně serializována jako `ulong` nebo `BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-200">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="3a7c7-201">Analýza čísla, které má desetinnou čárku jako `double` může přijít o přesnost, pokud bylo číslo původně serializováno jako `decimal` .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-201">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="3a7c7-202">Pro scénáře, které vyžadují odvození typu, následující kód ukazuje vlastní převaděč pro `object` Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-202">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="3a7c7-203">Kód převede:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-203">The code converts:</span></span>

* <span data-ttu-id="3a7c7-204">`true`a `false` na`Boolean`</span><span class="sxs-lookup"><span data-stu-id="3a7c7-204">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="3a7c7-205">Čísla bez desetinné čárky`long`</span><span class="sxs-lookup"><span data-stu-id="3a7c7-205">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="3a7c7-206">Čísla s desetinným čárkou`double`</span><span class="sxs-lookup"><span data-stu-id="3a7c7-206">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="3a7c7-207">Data do`DateTime`</span><span class="sxs-lookup"><span data-stu-id="3a7c7-207">Dates to `DateTime`</span></span>
* <span data-ttu-id="3a7c7-208">Řetězce na`string`</span><span class="sxs-lookup"><span data-stu-id="3a7c7-208">Strings to `string`</span></span>
* <span data-ttu-id="3a7c7-209">Všechno ostatní k`JsonElement`</span><span class="sxs-lookup"><span data-stu-id="3a7c7-209">Everything else to `JsonElement`</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="3a7c7-210">Následující kód registruje převaděč:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-210">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="3a7c7-211">Tady je příklad typu s `object` vlastnostmi:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-211">Here's an example type with `object` properties:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="3a7c7-212">Následující příklad JSON pro deserializaci obsahuje hodnoty, které budou deserializovat jako `DateTime` , `long` a `string` :</span><span class="sxs-lookup"><span data-stu-id="3a7c7-212">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="3a7c7-213">Bez vlastního převaděče zaznamená deserializace `JsonElement` v každé vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-213">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="3a7c7-214">[Složka testování částí](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) v `System.Text.Json.Serialization` oboru názvů obsahuje další příklady vlastních převaděčů, které zpracovávají deserializaci na `object` Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-214">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="3a7c7-215">Slovník podpory s jiným neřetězcovým klíčem</span><span class="sxs-lookup"><span data-stu-id="3a7c7-215">Support Dictionary with non-string key</span></span>

<span data-ttu-id="3a7c7-216">Integrovaná podpora pro kolekce slovníku je určena pro `Dictionary<string, TValue>` .</span><span class="sxs-lookup"><span data-stu-id="3a7c7-216">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="3a7c7-217">To znamená, že klíč musí být řetězec.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-217">That is, the key must be a string.</span></span> <span data-ttu-id="3a7c7-218">Pro podporu slovníku s celým číslem nebo jiným typem jako klíč je vyžadován vlastní převaděč.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-218">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="3a7c7-219">Následující kód ukazuje vlastní převaděč, který spolupracuje s `Dictionary<Enum,TValue>` :</span><span class="sxs-lookup"><span data-stu-id="3a7c7-219">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="3a7c7-220">Následující kód registruje převaděč:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-220">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="3a7c7-221">Konvertor může serializovat a deserializovat `TemperatureRanges` vlastnost následující třídy, která používá následující `Enum` :</span><span class="sxs-lookup"><span data-stu-id="3a7c7-221">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="3a7c7-222">Výstup JSON z serializace vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-222">The JSON output from serialization looks like the following example:</span></span>

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

<span data-ttu-id="3a7c7-223">[Složka testování částí](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) v `System.Text.Json.Serialization` oboru názvů obsahuje další příklady vlastních převaděčů, které zpracovávají slovníky nepoužívající řetězce.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-223">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="3a7c7-224">Podpora polymorfního deserializace</span><span class="sxs-lookup"><span data-stu-id="3a7c7-224">Support polymorphic deserialization</span></span>

<span data-ttu-id="3a7c7-225">Integrované funkce poskytují omezený rozsah [polymorfní serializace](system-text-json-how-to.md#serialize-properties-of-derived-classes) , ale vůbec nepodporují deserializaci.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-225">Built-in features provide a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but no support for deserialization at all.</span></span> <span data-ttu-id="3a7c7-226">Deserializace vyžaduje vlastní převaděč.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-226">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="3a7c7-227">Předpokládejme například, že máte `Person` abstraktní základní třídu s `Employee` a `Customer` odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-227">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="3a7c7-228">Polymorfní deserializace znamená, že v době návrhu můžete určit `Person` jako cíl deserializace a `Customer` `Employee` objekty ve formátu JSON jsou správně deserializovány za běhu.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-228">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="3a7c7-229">Během deserializace je nutné najít podoby, které identifikují požadovaný typ ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-229">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="3a7c7-230">Typy, které jsou k dispozici, se liší podle jednotlivých scénářů.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-230">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="3a7c7-231">Například může být k dispozici vlastnost diskriminátoru nebo může být nutné spoléhat na přítomnost určité vlastnosti nebo absence konkrétní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-231">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="3a7c7-232">Aktuální verze `System.Text.Json` neposkytuje atributy pro určení způsobu zpracování polymorfních scénářů deserializace, takže jsou vyžadovány vlastní převaděče.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-232">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="3a7c7-233">Následující kód ukazuje základní třídu, dvě odvozené třídy a vlastní konvertor pro ně.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-233">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="3a7c7-234">Převaděč používá vlastnost diskriminátor k provedení polymorfního deserializace.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-234">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="3a7c7-235">Diskriminátor typu není v definicích třídy, ale je vytvořen během serializace a je čten během deserializace.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-235">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="3a7c7-236">Následující kód registruje převaděč:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-236">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="3a7c7-237">Konvertor může deserializovat JSON, který byl vytvořen pomocí stejného převaděče k serializaci, například:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-237">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

<span data-ttu-id="3a7c7-238">Kód převaděče v předchozím příkladu čte a zapisuje každou vlastnost ručně.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-238">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="3a7c7-239">Alternativou je volání `Deserialize` nebo `Serialize` k provedení některé práce.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-239">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="3a7c7-240">Příklad najdete v [tomto příspěvku StackOverflow](https://stackoverflow.com/a/59744873/12509023).</span><span class="sxs-lookup"><span data-stu-id="3a7c7-240">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

### <a name="support-round-trip-for-stackt"></a><span data-ttu-id="3a7c7-241">Podpora zpátečního přenosu pro zásobník \< T></span><span class="sxs-lookup"><span data-stu-id="3a7c7-241">Support round-trip for Stack\<T></span></span>

<span data-ttu-id="3a7c7-242">Pokud deserializovat řetězec JSON na <xref:System.Collections.Generic.Stack%601> objekt a potom tento objekt serializovat, je obsah zásobníku v opačném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-242">If you deserialize a JSON string into a <xref:System.Collections.Generic.Stack%601> object and then serialize that object, the contents of the stack are in reverse order.</span></span> <span data-ttu-id="3a7c7-243">Toto chování platí pro následující typy a rozhraní a uživatelsky definované typy, které jsou z nich odvozeny:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-243">This behavior applies to the following types and interface, and user-defined types that derive from them:</span></span>

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

<span data-ttu-id="3a7c7-244">Pro podporu serializace a deserializace, která uchovává původní pořadí v zásobníku, je vyžadován vlastní převaděč.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-244">To support serialization and deserialization that retains the original order in the stack, a custom converter is required.</span></span>

<span data-ttu-id="3a7c7-245">Následující kód ukazuje vlastní převaděč, který umožňuje příkaz Round-Trip do a z `Stack<T>` objektů:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-245">The following code shows a custom converter that enables round-tripping to and from `Stack<T>` objects:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs)]

<span data-ttu-id="3a7c7-246">Následující kód registruje převaděč:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-246">The following code registers the converter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs?name=SnippetRegister)]

## <a name="other-custom-converter-samples"></a><span data-ttu-id="3a7c7-247">Další ukázky vlastního převaděče</span><span class="sxs-lookup"><span data-stu-id="3a7c7-247">Other custom converter samples</span></span>

<span data-ttu-id="3a7c7-248">Článek [migrace z Newtonsoft.Json na System.Text.Json ](system-text-json-migrate-from-newtonsoft-how-to.md) verzi obsahuje další ukázky vlastních převaděčů.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-248">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="3a7c7-249">[Složka testování částí](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) ve `System.Text.Json.Serialization` zdrojovém kódu zahrnuje další ukázky převaděčů, například:</span><span class="sxs-lookup"><span data-stu-id="3a7c7-249">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="3a7c7-250">[Konvertor Int32, který při deserializaci převede hodnotu null na 0](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span><span class="sxs-lookup"><span data-stu-id="3a7c7-250">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="3a7c7-251">[Konvertor Int32, který umožňuje řetězcové i číselné hodnoty při deserializaci](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span><span class="sxs-lookup"><span data-stu-id="3a7c7-251">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="3a7c7-252">[Konvertor Enum](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span><span class="sxs-lookup"><span data-stu-id="3a7c7-252">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="3a7c7-253">[\<Převaděč T>, který přijímá externí data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="3a7c7-253">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="3a7c7-254">[Long [] převaděč, který funguje se seznamem čísel oddělených čárkami](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="3a7c7-254">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="3a7c7-255">Pokud potřebujete vytvořit převaděč, který upraví chování existujícího integrovaného převaděče, můžete získat [zdrojový kód existujícího převaděče](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) , který slouží jako výchozí bod pro přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="3a7c7-255">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="3a7c7-256">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="3a7c7-256">Additional resources</span></span>

* <span data-ttu-id="3a7c7-257">[Zdrojový kód pro předdefinované převaděče](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="3a7c7-257">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span></span>
* <span data-ttu-id="3a7c7-258">[Podpora DateTime a DateTimeOffset vSystem.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="3a7c7-258">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="3a7c7-259">[System.Text.JsonPřehled](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="3a7c7-259">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* <span data-ttu-id="3a7c7-260">[Jak používatSystem.Text.Json](system-text-json-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="3a7c7-260">[How to use System.Text.Json](system-text-json-how-to.md)</span></span>
* <span data-ttu-id="3a7c7-261">[Postup migrace zNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="3a7c7-261">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="3a7c7-262">[System.Text.JsonReference k rozhraní API](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="3a7c7-262">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="3a7c7-263">[System.Text.Json. Reference k rozhraní API serializace](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="3a7c7-263">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
