---
title: Zápis vlastních převaděčů pro serializaci JSON – .NET
author: tdykstra
ms.author: tdykstra
ms.date: 10/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 361818a0bda8863f8878b86e5fb377dc0faf5246
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741890"
---
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a><span data-ttu-id="dbb0a-102">Zápis vlastních převaděčů pro serializaci JSON v .NET</span><span class="sxs-lookup"><span data-stu-id="dbb0a-102">How to write custom converters for JSON serialization in .NET</span></span>

<span data-ttu-id="dbb0a-103">Tento článek ukazuje, jak vytvořit vlastní převaděče pro třídy serializace JSON, které jsou k dispozici v oboru názvů <xref:System.Text.Json>.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="dbb0a-104">Úvod do `System.Text.Json`naleznete [v tématu How to serializovat and deserializovat JSON v rozhraní .NET](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="dbb0a-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="dbb0a-105">*Převodník* je třída, která převádí objekt nebo hodnotu na a z formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="dbb0a-106">Obor názvů `System.Text.Json` obsahuje integrované převaděče pro většinu primitivních typů, které jsou mapovány na primitivní prvky jazyka JavaScript.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="dbb0a-107">Můžete psát vlastní převaděče:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-107">You can write custom converters:</span></span>

* <span data-ttu-id="dbb0a-108">Chcete-li přepsat výchozí chování vestavěného převaděče.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="dbb0a-109">Můžete například chtít, aby byly hodnoty `DateTime` ve formátu mm/dd/rrrr namísto výchozího formátu ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="dbb0a-110">Pro podporu vlastního typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-110">To support a custom value type.</span></span> <span data-ttu-id="dbb0a-111">Například struktura `PhoneNumber`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="dbb0a-112">Můžete také napsat vlastní převaděče pro rozšiřování `System.Text.Json` s funkcemi, které nejsou součástí aktuální verze.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-112">You can also write custom converters to extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="dbb0a-113">Následující scénáře jsou pokryté dále v tomto článku:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="dbb0a-114">[Deserializace odvozených typů do vlastností objektu](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="dbb0a-114">[Deserialize inferred types to Object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="dbb0a-115">[Slovník podpory s jiným neřetězcovým klíčem](#support-dictionary-with-non-string-key)</span><span class="sxs-lookup"><span data-stu-id="dbb0a-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="dbb0a-116">[Podpora polymorfního deserializace](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="dbb0a-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="dbb0a-117">Vlastní vzory převaděče</span><span class="sxs-lookup"><span data-stu-id="dbb0a-117">Custom converter patterns</span></span>

<span data-ttu-id="dbb0a-118">Existují dva vzory pro vytvoření vlastního převaděče: základní vzor a model továrny.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="dbb0a-119">Vzor továrny je pro převaděče, které zpracovávají typ `Enum` nebo otevřít obecné typy.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="dbb0a-120">Základní vzor je pro neobecný a uzavřený obecný typ.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="dbb0a-121">Například převaděče pro následující typy vyžadují model továrny:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="dbb0a-122">Mezi příklady typů, které lze zpracovat pomocí základního vzoru, patří:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="dbb0a-123">Základní vzor vytvoří třídu, která může zpracovat jeden typ.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="dbb0a-124">Model továrny vytvoří třídu, která určuje za běhu, který konkrétní typ vyžaduje, a dynamicky vytvoří odpovídající převaděč.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="dbb0a-125">Ukázka základního převaděče</span><span class="sxs-lookup"><span data-stu-id="dbb0a-125">Sample basic converter</span></span>

<span data-ttu-id="dbb0a-126">Následující ukázka je převaděč, který přepisuje výchozí serializaci pro existující datový typ.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="dbb0a-127">Převaděč používá formát mm/dd/rrrr pro `DateTimeOffset` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

```csharp
private class ExampleDateTimeOffsetConverter : JsonConverter<DateTimeOffset>
{
    public override DateTimeOffset Read(
        ref Utf8JsonReader reader, 
        Type typeToConvert, 
        JsonSerializerOptions options)
    {
        return DateTimeOffset.ParseExact(reader.GetString(), 
            "MM/dd/yyyy", CultureInfo.InvariantCulture);
    }

    public override void Write(
        Utf8JsonWriter writer, 
        DateTimeOffset value, 
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString(
            "MM/dd/yyyy", CultureInfo.InvariantCulture));
    }
}
```

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="dbb0a-128">Ukázkový konvertor vzorků výrobního modelu</span><span class="sxs-lookup"><span data-stu-id="dbb0a-128">Sample factory pattern converter</span></span>

<span data-ttu-id="dbb0a-129">Následující kód ukazuje vlastní převaděč, který pracuje s `Dictionary<Enum,TValue>`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="dbb0a-130">Kód řídí model továrny, protože první parametr obecného typu je `Enum` a druhý je otevřen.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="dbb0a-131">Metoda `CanConvert` vrací `true` pouze pro `Dictionary` se dvěma obecnými parametry, první z nich je `Enum` typ.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="dbb0a-132">Vnitřní převaděč získá existující převaděč, který zpracuje typ, který je poskytován za běhu pro `TValue`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span> 

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

<span data-ttu-id="dbb0a-133">Předchozí kód je stejný jako ten, který je zobrazen ve [slovníku podpory s jiným než řetězcovým klíčem](#support-dictionary-with-non-string-key) , dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="dbb0a-134">Postup pro postup pro základní vzor</span><span class="sxs-lookup"><span data-stu-id="dbb0a-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="dbb0a-135">Následující postup vysvětluje, jak vytvořit převaděč podle základního vzoru:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="dbb0a-136">Vytvořte třídu, která je odvozena z <xref:System.Text.Json.Serialization.JsonConverter%601>, kde `T` je typ k serializaci a deserializaci.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-136">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="dbb0a-137">Přepište metodu `Read` pro deserializaci příchozího JSON a převeďte ji na typ `T`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="dbb0a-138">Použijte <xref:System.Text.Json.Utf8JsonReader>, která je předána metodě pro čtení formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-138">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="dbb0a-139">Přepište metodu `Write` k serializaci příchozího objektu typu `T`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="dbb0a-140">Použijte <xref:System.Text.Json.Utf8JsonWriter>, která je předána metodě pro zápis formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-140">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="dbb0a-141">Metodu `CanConvert` popište pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="dbb0a-142">Výchozí implementace vrátí `true`, když typ, který má být převeden, je typ `T`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-142">The default implementation returns `true` when the type to convert is type `T`.</span></span> <span data-ttu-id="dbb0a-143">Proto převaděče, které podporují pouze typ `T`, nemusejí přepsat tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="dbb0a-144">Příklad převaděče, který musí přepsat tuto metodu, naleznete v části [polymorfní deserializace](#support-polymorphic-deserialization) dále v tomto článku.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="dbb0a-145">Můžete odkazovat na [předdefinovaný zdrojový kód převaděče](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) jako referenční implementace pro psaní vlastních převaděčů.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-145">You can refer to the [built-in converters source code](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="dbb0a-146">Postup pro postup pro model výroby</span><span class="sxs-lookup"><span data-stu-id="dbb0a-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="dbb0a-147">Následující postup vysvětluje, jak vytvořit převaděč podle vzorce pro vytváření:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="dbb0a-148">Vytvořte třídu, která je odvozena z <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-148">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="dbb0a-149">Přepište metodu `CanConvert`, aby vracela hodnotu true, pokud je typ převodu ten, který může převaděč zpracovat.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="dbb0a-150">Pokud je například převaděč určený pro `List<T>` může zpracovat pouze `List<int>`, `List<string>`a `List<DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span> 
* <span data-ttu-id="dbb0a-151">Přepište metodu `CreateConverter` pro vrácení instance třídy převaděče, která bude zpracovávat typ k převodu, který je k dispozici za běhu.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="dbb0a-152">Vytvořte třídu převaděče, kterou vytváří instance metody `CreateConverter`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-152">Create the converter class that the `CreateConverter` method instantiates.</span></span> 

<span data-ttu-id="dbb0a-153">Model továrny je vyžadován pro otevřené generické typy, protože kód pro převod objektu na a z řetězce není stejný pro všechny typy.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="dbb0a-154">Převaděč pro otevřený obecný typ (`List<T>`, například) musí vytvořit převaděč pro uzavřený obecný typ (`List<DateTime>`, například) na pozadí.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="dbb0a-155">Kód musí být napsán pro zpracování každého uzavřeného a obecného typu, který může převaděč zpracovat.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="dbb0a-156">Typ `Enum` je podobný otevřenému obecnému typu: převaděč pro `Enum` musí vytvořit převaděč pro konkrétní `Enum` (například`WeekdaysEnum`) na pozadí.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span> 

## <a name="error-handling"></a><span data-ttu-id="dbb0a-157">Zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="dbb0a-157">Error handling</span></span>

<span data-ttu-id="dbb0a-158">Pokud potřebujete vyvolat výjimku v kódu pro zpracování chyb, zvažte vyvolání <xref:System.Text.Json.JsonException> bez zprávy.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-158">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="dbb0a-159">Tento typ výjimky automaticky vytvoří zprávu, která obsahuje cestu k části JSON, která způsobila chybu.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="dbb0a-160">Například příkaz `throw new JsonException();` vytvoří chybovou zprávu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```text
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="dbb0a-161">Pokud zadáte zprávu (například `throw new JsonException("Error occurred)`, výjimka stále poskytne cestu ve vlastnosti <xref:System.Text.Json.JsonException.Path>.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-161">If you do provide a message (for example, `throw new JsonException("Error occurred)`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="dbb0a-162">Registrace vlastního převaděče</span><span class="sxs-lookup"><span data-stu-id="dbb0a-162">Register a custom converter</span></span>

<span data-ttu-id="dbb0a-163">*Zaregistrujte* vlastní převaděč a nastavte `Serialize` a metody `Deserialize` ho použít.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="dbb0a-164">Vyberte jeden z následujících přístupů:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="dbb0a-165">Přidejte instanci třídy Converter do kolekce <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-165">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="dbb0a-166">Použijte atribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) pro vlastnosti, které vyžadují vlastní převaděč.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-166">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="dbb0a-167">Použijte atribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) pro třídu nebo strukturu, která představuje vlastní typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="dbb0a-168">Registrace ukázek – kolekce převaděčů</span><span class="sxs-lookup"><span data-stu-id="dbb0a-168">Registration sample - Converters collection</span></span> 

<span data-ttu-id="dbb0a-169">Tady je příklad, který nastaví `ExampleDateTimeOffsetConverter` jako výchozí pro vlastnosti typu `DateTimeOffset`:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-169">Here's an example that makes the `ExampleDateTimeOffsetConverter` the default for properties of type `DateTimeOffset`:</span></span>

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
string json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="dbb0a-170">Předpokládejme, že jste serializováni následující typ:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-170">Suppose you serialize the following type:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="dbb0a-171">Tady je příklad výstupu JSON, který ukazuje použití vlastního převaděče:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="dbb0a-172">Následující kód používá stejný přístup k deserializaci pomocí vlastního převaděče `DateTimeOffset`:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json, options);
```

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="dbb0a-173">Ukázka registrace – [JsonConverter] u vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dbb0a-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="dbb0a-174">Následující kód vybere vlastní převaděč pro vlastnost `Date`:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-174">The following code selects a custom converter for the `Date` property:</span></span>

```csharp
class WeatherForecastWithConverter
{
    [JsonConverter(typeof(ExampleDateTimeOffsetConverter))]
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="dbb0a-175">Kód pro serializaci a deserializaci `WeatherForecastWithConverter` nevyžaduje použití `JsonSerializeOptions.Converters`:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-175">The code to serialize and deserialize `WeatherForecastWithConverter` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

```csharp
string json = JsonSerializer.Serialize(weatherForecastWithConverter);
```

```csharp
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithConverter>(json);
```

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="dbb0a-176">Ukázka registrace – [JsonConverter] na typu</span><span class="sxs-lookup"><span data-stu-id="dbb0a-176">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="dbb0a-177">Zde je kód, který vytvoří strukturu a na ni aplikuje atribut `[JsonConverter]`:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-177">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

```csharp
[JsonConverter(typeof(TemperatureConverter))]
public struct Temperature
{
    public Temperature(int degrees, bool celsius)
    {
        _degrees = degrees;
        _isCelsius = celsius;
    }
    private bool _isCelsius;
    private int _degrees;
    public int Degrees => _degrees;
    public bool IsCelsius => _isCelsius; 
    public bool IsFahrenheit => !_isCelsius;
    public override string ToString() =>
        $"{_degrees.ToString()}{(_isCelsius ? "C" : "F")}";
    public static Temperature Parse(string input)
    {
        int degrees = int.Parse(input.Substring(0, input.Length - 1));
        bool celsius = (input.Substring(input.Length - 1) == "C");
        return new Temperature(degrees, celsius);
    }
}
```

<span data-ttu-id="dbb0a-178">Tady je vlastní převaděč pro předchozí strukturu:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-178">Here's the custom converter for the preceding struct:</span></span>

```csharp
public class TemperatureConverter : JsonConverter<Temperature>
{
    public override Temperature Read(
        ref Utf8JsonReader reader,
        Type typeToConvert,
        JsonSerializerOptions options)
    {
        Debug.Assert(typeToConvert == typeof(Temperature));
        return Temperature.Parse(reader.GetString());
    }

    public override void Write(
        Utf8JsonWriter writer,
        Temperature value,
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString());
    }
}
```

<span data-ttu-id="dbb0a-179">Atribut `[JsonConvert]` ve struktuře registruje vlastní převaděč jako výchozí hodnotu pro vlastnosti typu `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-179">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="dbb0a-180">Při serializaci nebo deserializaci se převaděč automaticky použije na vlastnost `TemperatureC` následujícího typu:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-180">The converter is automatically used on the `TemperatureC` property of the following type when you serialize or deserialize it:</span></span>

```csharp
class WeatherForecastWithTemperatureStruct
{
    public DateTimeOffset Date { get; set; }
    public Temperature TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="converter-registration-precedence"></a><span data-ttu-id="dbb0a-181">Priorita registrace převaděče</span><span class="sxs-lookup"><span data-stu-id="dbb0a-181">Converter registration precedence</span></span>

<span data-ttu-id="dbb0a-182">Při serializaci nebo deserializaci se pro každý prvek JSON v uvedeném pořadí vybere konvertor, který je uvedený z nejvyšší priority na nejnižší:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-182">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="dbb0a-183">`[JsonConverter]` použito pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-183">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="dbb0a-184">Převaděč přidaný do kolekce `Converters`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-184">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="dbb0a-185">`[JsonConverter]` použito pro vlastní typ hodnoty nebo POCO.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-185">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="dbb0a-186">Pokud je v kolekci `Converters` zaregistrováno více vlastních převaděčů pro typ, je použit první převaděč, který vrací hodnotu true pro `CanConvert`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-186">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="dbb0a-187">Vestavěný převaděč je zvolen pouze v případě, že není registrován žádný použitelný vlastní převaděč.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-187">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="dbb0a-188">Ukázky převaděčů pro běžné scénáře</span><span class="sxs-lookup"><span data-stu-id="dbb0a-188">Converter samples for common scenarios</span></span>

<span data-ttu-id="dbb0a-189">V následujících částech jsou uvedeny ukázky konvertorů, které řeší některé běžné scénáře, které vestavěná funkce nezpracovává.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-189">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="dbb0a-190">Deserializace odvozených typů do vlastností objektu</span><span class="sxs-lookup"><span data-stu-id="dbb0a-190">Deserialize inferred types to Object properties</span></span>

<span data-ttu-id="dbb0a-191">Při deserializaci na vlastnost typu `Object`je vytvořen objekt `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-191">When deserializing to a property of type `Object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="dbb0a-192">Důvodem je, že deserializátor nezná typ CLR, který se má vytvořit, a nepokusí se odhadnout.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-192">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="dbb0a-193">Například pokud má vlastnost JSON hodnotu "true", deserializátor neodvodí, že hodnota je `Boolean`a pokud má element "01/01/2019", deserializátor neodvodí, že se jedná o `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-193">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="dbb0a-194">Odvození typu může být nepřesné.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-194">Type inference can be inaccurate.</span></span> <span data-ttu-id="dbb0a-195">Pokud deserializátor analyzuje číslo JSON, které nemá žádné desetinné místo jako `long`, což může vést k problémům mimo rozsah, pokud byla hodnota původně serializována jako `ulong` nebo `BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-195">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="dbb0a-196">Analýza čísla s desetinnou čárkou jako `double` může přijít o přesnost, pokud bylo číslo původně serializováno jako `decimal`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-196">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="dbb0a-197">Pro scénáře, které vyžadují odvození typu, ukazuje následující kód vlastní převaděč pro `Object` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-197">For scenarios that require type inference, the following code shows a custom converter for `Object` properties.</span></span> <span data-ttu-id="dbb0a-198">Kód převede:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-198">The code converts:</span></span>

* <span data-ttu-id="dbb0a-199">`true` a `false` na `Boolean`</span><span class="sxs-lookup"><span data-stu-id="dbb0a-199">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="dbb0a-200">Čísla `long` nebo `double`</span><span class="sxs-lookup"><span data-stu-id="dbb0a-200">Numbers to `long` or `double`</span></span>
* <span data-ttu-id="dbb0a-201">Kalendářní data `DateTime`</span><span class="sxs-lookup"><span data-stu-id="dbb0a-201">Dates to `DateTime`</span></span>
* <span data-ttu-id="dbb0a-202">Řetězce, které se mají `string`</span><span class="sxs-lookup"><span data-stu-id="dbb0a-202">Strings to `string`</span></span>
* <span data-ttu-id="dbb0a-203">Všechno ostatní `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="dbb0a-203">Everything else to `JsonElement`</span></span>

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ObjectToInferredTypesConverter
        : JsonConverter<object>
    {
        public override object Read(
            ref Utf8JsonReader reader,
            Type typeToConvert,
            JsonSerializerOptions options)
        {
            if (reader.TokenType == JsonTokenType.True)
            {
                return true;
            }

            if (reader.TokenType == JsonTokenType.False)
            {
                return false;
            }

            if (reader.TokenType == JsonTokenType.Number)
            {
                if (reader.TryGetInt64(out long l))
                {
                    return l;
                }

                return reader.GetDouble();
            }

            if (reader.TokenType == JsonTokenType.String)
            {
                if (reader.TryGetDateTime(out DateTime datetime))
                {
                    return datetime;
                }

                return reader.GetString();
            }

            // Use JsonElement as fallback.
            // Newtonsoft uses JArray or JObject.
            using (JsonDocument document = JsonDocument.ParseValue(ref reader))
            {
                return document.RootElement.Clone();
            }
        }

        public override void Write(
            Utf8JsonWriter writer,
            object value,
            JsonSerializerOptions options)
        {
            throw new InvalidOperationException("Should not get here.");
        }
    }
}
```

<span data-ttu-id="dbb0a-204">Následující kód registruje převaděč:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-204">The following code registers the converter:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new ObjectToInferredTypesConverter());
```

<span data-ttu-id="dbb0a-205">Tady je příklad typu s vlastností objektu:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-205">Here's an example type with an Object property:</span></span>

```csharp
public class WeatherForecastWithObjectProperties
{
    public object Date { get; set; }
    public object TemperatureC { get; set; }
    public object Summary { get; set; }
}
```

<span data-ttu-id="dbb0a-206">Následující příklad JSON pro deserializaci obsahuje hodnoty, které budou deserializovat jako `DateTime`, `long`a `string`:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-206">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="dbb0a-207">Bez vlastního převaděče je deserializace v každé vlastnosti `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-207">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="dbb0a-208">[Složka testování částí](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) v oboru názvů `System.Text.Json.Serialization` obsahuje další příklady vlastních převaděčů, které zpracovávají deserializaci na vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-208">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to Object properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="dbb0a-209">Slovník podpory s jiným neřetězcovým klíčem</span><span class="sxs-lookup"><span data-stu-id="dbb0a-209">Support Dictionary with non-string key</span></span>

<span data-ttu-id="dbb0a-210">Integrovaná podpora pro kolekce slovníků je určena pro `Dictionary<string, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-210">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="dbb0a-211">To znamená, že klíč musí být řetězec.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-211">That is, the key must be a string.</span></span> <span data-ttu-id="dbb0a-212">Pro podporu slovníku s celým číslem nebo jiným typem jako klíč je vyžadován vlastní převaděč.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-212">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="dbb0a-213">Následující kód ukazuje vlastní převaděč, který spolupracuje s `Dictionary<Enum,TValue>`:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-213">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

<span data-ttu-id="dbb0a-214">Následující kód registruje převaděč:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-214">The following code registers the converter:</span></span>

```csharp
var serializeOptions = new JsonSerializerOptions();
serializeOptions.Converters.Add(new ConverterDictionaryTKeyEnumTValue());
```

<span data-ttu-id="dbb0a-215">Konvertor může serializovat a deserializovat vlastnost `TemperatureRanges` následující třídy, která používá následující `Enum`:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-215">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

```csharp
public class WeatherForecastWithEnumDictionary
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public Dictionary<SummaryWordsEnum, int> TemperatureRanges { get; set; }
}

public enum SummaryWordsEnum
{
    Cold, Hot
}
```

<span data-ttu-id="dbb0a-216">Výstup JSON z serializace vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-216">The JSON output from serialization looks like the following example:</span></span>

```json
{

  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

<span data-ttu-id="dbb0a-217">[Složka testování částí](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) v oboru názvů `System.Text.Json.Serialization` obsahuje další příklady vlastních převaděčů, které zpracovávají slovníky neřetězcových klíčů.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-217">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="dbb0a-218">Podpora polymorfního deserializace</span><span class="sxs-lookup"><span data-stu-id="dbb0a-218">Support polymorphic deserialization</span></span>

<span data-ttu-id="dbb0a-219">[Polymorfní serializace](system-text-json-how-to.md#serialize-properties-of-derived-classes) nevyžaduje vlastní převaděč, ale deserializace vyžaduje vlastní převaděč.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-219">[Polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) doesn't require a custom converter, but deserialization does require a custom converter.</span></span>

<span data-ttu-id="dbb0a-220">Předpokládejme například, že máte abstraktní základní třídu `Person` s `Employee` a `Customer` odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-220">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="dbb0a-221">Polymorfní deserializace znamená, že v době návrhu můžete zadat `Person` jako cíl deserializace a `Customer` a `Employee` objekty ve formátu JSON jsou správně deserializovány za běhu.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-221">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="dbb0a-222">Během deserializace je nutné najít podoby, které identifikují požadovaný typ ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-222">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="dbb0a-223">Typy, které jsou k dispozici, se liší podle jednotlivých scénářů.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-223">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="dbb0a-224">Například může být k dispozici vlastnost diskriminátoru nebo může být nutné spoléhat na přítomnost určité vlastnosti nebo absence konkrétní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-224">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="dbb0a-225">Aktuální verze `System.Text.Json` neposkytuje atributy pro určení způsobu zpracování polymorfních scénářů deserializace, takže jsou vyžadovány vlastní převaděče.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-225">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="dbb0a-226">Následující kód ukazuje základní třídu, dvě odvozené třídy a vlastní konvertor pro ně.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-226">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="dbb0a-227">Převaděč používá vlastnost diskriminátor k provedení polymorfního deserializace.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-227">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="dbb0a-228">Diskriminátor typu není v definicích třídy, ale je vytvořen během serializace a je čten během deserializace.</span><span class="sxs-lookup"><span data-stu-id="dbb0a-228">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

```csharp
public class Person
{
    public string Name { get; set; }
}

public class Customer : Person
{
    public decimal CreditLimit { get; set; }
}

public class Employee : Person
{
    public string OfficeNumber { get; set; }
}
```

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class PersonConverterWithTypeDiscriminator : JsonConverter<Person>
    {
        enum TypeDiscriminator
        {
            Customer = 1,
            Employee = 2
        }

        public override bool CanConvert(Type typeToConvert)
        {
            return typeof(Person).IsAssignableFrom(typeToConvert);
        }

        public override Person Read(ref Utf8JsonReader reader, Type typeToConvert, JsonSerializerOptions options)
        {
            if (reader.TokenType != JsonTokenType.StartObject)
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.PropertyName)
            {
                throw new JsonException();
            }

            string propertyName = reader.GetString();
            if (propertyName != "TypeDiscriminator")
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.Number)
            {
                throw new JsonException();
            }

            Person value;
            TypeDiscriminator typeDiscriminator = (TypeDiscriminator)reader.GetInt32();
            switch (typeDiscriminator)
            {
                case TypeDiscriminator.Customer:
                    value = new Customer();
                    break;

                case TypeDiscriminator.Employee:
                    value = new Employee();
                    break;

                default:
                    throw new JsonException();
            }

            while (reader.Read())
            {
                if (reader.TokenType == JsonTokenType.EndObject)
                {
                    return value;
                }

                if (reader.TokenType == JsonTokenType.PropertyName)
                {
                    propertyName = reader.GetString();
                    reader.Read();
                    switch (propertyName)
                    {
                        case "CreditLimit":
                            decimal creditLimit = reader.GetDecimal();
                            ((Customer)value).CreditLimit = creditLimit;
                            break;
                        case "OfficeNumber":
                            string officeNumber = reader.GetString();
                            ((Employee)value).OfficeNumber = officeNumber;
                            break;
                        case "Name":
                            string name = reader.GetString();
                            value.Name = name;
                            break;
                    }
                }
            }

            throw new JsonException();
        }

        public override void Write(Utf8JsonWriter writer, Person value, JsonSerializerOptions options)
        {
            writer.WriteStartObject();

            if (value is Customer customer)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Customer);
                writer.WriteNumber("CreditLimit", customer.CreditLimit);
            }
            else if (value is Employee employee)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Employee);
                writer.WriteString("OfficeNumber", employee.OfficeNumber);
            }

            writer.WriteString("Name", value.Name);

            writer.WriteEndObject();
        }
    }
}
```

<span data-ttu-id="dbb0a-229">Následující kód registruje převaděč:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-229">The following code registers the converter:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new PersonConverterWithTypeDiscriminator());
```

<span data-ttu-id="dbb0a-230">Konvertor může deserializovat JSON, který byl vytvořen pomocí stejného převaděče k serializaci, například:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-230">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

## <a name="other-custom-converter-samples"></a><span data-ttu-id="dbb0a-231">Další ukázky vlastního převaděče</span><span class="sxs-lookup"><span data-stu-id="dbb0a-231">Other custom converter samples</span></span>

<span data-ttu-id="dbb0a-232">[Složka testování částí](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) ve zdrojovém kódu `System.Text.Json.Serialization` obsahuje další ukázky vlastního převaděče, jako například:</span><span class="sxs-lookup"><span data-stu-id="dbb0a-232">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="dbb0a-233">převaděč `Int32`, který při deserializaci převede hodnotu null na 0</span><span class="sxs-lookup"><span data-stu-id="dbb0a-233">`Int32` converter that converts null to 0 on deserialize</span></span>
* <span data-ttu-id="dbb0a-234">převaděč `Int32`, který umožňuje v případě deserializace řetězcové i číselné hodnoty</span><span class="sxs-lookup"><span data-stu-id="dbb0a-234">`Int32` converter that allows both string and number values on deserialize</span></span>
* <span data-ttu-id="dbb0a-235">převaděč `Enum`</span><span class="sxs-lookup"><span data-stu-id="dbb0a-235">`Enum` converter</span></span>
* <span data-ttu-id="dbb0a-236">převaděč `List<T>`, který přijímá externí data</span><span class="sxs-lookup"><span data-stu-id="dbb0a-236">`List<T>` converter that accepts external data</span></span>
* <span data-ttu-id="dbb0a-237">převaděč `Long[]`, který pracuje se seznamem čísel oddělených čárkami</span><span class="sxs-lookup"><span data-stu-id="dbb0a-237">`Long[]` converter that works with a comma-delimited list of numbers</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="dbb0a-238">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="dbb0a-238">Additional resources</span></span>

* [<span data-ttu-id="dbb0a-239">Přehled System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="dbb0a-239">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="dbb0a-240">Reference k rozhraní API System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="dbb0a-240">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="dbb0a-241">Jak používat System. text. JSON</span><span class="sxs-lookup"><span data-stu-id="dbb0a-241">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="dbb0a-242">Zdrojový kód pro předdefinované převaděče</span><span class="sxs-lookup"><span data-stu-id="dbb0a-242">Source code for built-in converters</span></span>](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* <span data-ttu-id="dbb0a-243">Problémy GitHubu související s vlastními převaděči pro `System.Text.Json`</span><span class="sxs-lookup"><span data-stu-id="dbb0a-243">GitHub issues related to custom converters for `System.Text.Json`</span></span>
  * [<span data-ttu-id="dbb0a-244">36639 Představujeme vlastní převaděče</span><span class="sxs-lookup"><span data-stu-id="dbb0a-244">36639 Introducing custom converters</span></span>](https://github.com/dotnet/corefx/issues/36639)
  * [<span data-ttu-id="dbb0a-245">38713 o deserializaci do objektu</span><span class="sxs-lookup"><span data-stu-id="dbb0a-245">38713 About deserializing to Object</span></span>](https://github.com/dotnet/corefx/issues/38713)
  * [<span data-ttu-id="dbb0a-246">40120 o slovnících bez řetězcových klíčů</span><span class="sxs-lookup"><span data-stu-id="dbb0a-246">40120 About non-string-key dictionaries</span></span>](https://github.com/dotnet/corefx/issues/40120)
  * [<span data-ttu-id="dbb0a-247">37787 o polymorfní deserializaci</span><span class="sxs-lookup"><span data-stu-id="dbb0a-247">37787 About polymorphic deserialization</span></span>](https://github.com/dotnet/corefx/issues/37787)
