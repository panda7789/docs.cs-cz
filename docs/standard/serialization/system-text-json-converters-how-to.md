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
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a>Zápis vlastních převaděčů pro serializaci JSON v .NET

Tento článek ukazuje, jak vytvořit vlastní převaděče pro třídy serializace JSON, které jsou k dispozici v oboru názvů <xref:System.Text.Json>. Úvod do `System.Text.Json`naleznete [v tématu How to serializovat and deserializovat JSON v rozhraní .NET](system-text-json-how-to.md).

*Převodník* je třída, která převádí objekt nebo hodnotu na a z formátu JSON. Obor názvů `System.Text.Json` obsahuje integrované převaděče pro většinu primitivních typů, které jsou mapovány na primitivní prvky jazyka JavaScript. Můžete psát vlastní převaděče:

* Chcete-li přepsat výchozí chování vestavěného převaděče. Můžete například chtít, aby byly hodnoty `DateTime` ve formátu mm/dd/rrrr namísto výchozího formátu ISO 8601-1:2019.
* Pro podporu vlastního typu hodnoty. Například struktura `PhoneNumber`.

Můžete také napsat vlastní převaděče pro rozšiřování `System.Text.Json` s funkcemi, které nejsou součástí aktuální verze. Následující scénáře jsou pokryté dále v tomto článku:

* [Deserializace odvozených typů do vlastností objektu](#deserialize-inferred-types-to-object-properties).
* [Slovník podpory s jiným neřetězcovým klíčem](#support-dictionary-with-non-string-key)
* [Podpora polymorfního deserializace](#support-polymorphic-deserialization).

## <a name="custom-converter-patterns"></a>Vlastní vzory převaděče

Existují dva vzory pro vytvoření vlastního převaděče: základní vzor a model továrny. Vzor továrny je pro převaděče, které zpracovávají typ `Enum` nebo otevřít obecné typy. Základní vzor je pro neobecný a uzavřený obecný typ.  Například převaděče pro následující typy vyžadují model továrny:

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

Mezi příklady typů, které lze zpracovat pomocí základního vzoru, patří:

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

Základní vzor vytvoří třídu, která může zpracovat jeden typ. Model továrny vytvoří třídu, která určuje za běhu, který konkrétní typ vyžaduje, a dynamicky vytvoří odpovídající převaděč.

## <a name="sample-basic-converter"></a>Ukázka základního převaděče

Následující ukázka je převaděč, který přepisuje výchozí serializaci pro existující datový typ. Převaděč používá formát mm/dd/rrrr pro `DateTimeOffset` vlastnosti.

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

## <a name="sample-factory-pattern-converter"></a>Ukázkový konvertor vzorků výrobního modelu

Následující kód ukazuje vlastní převaděč, který pracuje s `Dictionary<Enum,TValue>`. Kód řídí model továrny, protože první parametr obecného typu je `Enum` a druhý je otevřen. Metoda `CanConvert` vrací `true` pouze pro `Dictionary` se dvěma obecnými parametry, první z nich je `Enum` typ. Vnitřní převaděč získá existující převaděč, který zpracuje typ, který je poskytován za běhu pro `TValue`. 

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

Předchozí kód je stejný jako ten, který je zobrazen ve [slovníku podpory s jiným než řetězcovým klíčem](#support-dictionary-with-non-string-key) , dále v tomto článku.

## <a name="steps-to-follow-the-basic-pattern"></a>Postup pro postup pro základní vzor

Následující postup vysvětluje, jak vytvořit převaděč podle základního vzoru:

* Vytvořte třídu, která je odvozena z <xref:System.Text.Json.Serialization.JsonConverter%601>, kde `T` je typ k serializaci a deserializaci.
* Přepište metodu `Read` pro deserializaci příchozího JSON a převeďte ji na typ `T`. Použijte <xref:System.Text.Json.Utf8JsonReader>, která je předána metodě pro čtení formátu JSON.
* Přepište metodu `Write` k serializaci příchozího objektu typu `T`. Použijte <xref:System.Text.Json.Utf8JsonWriter>, která je předána metodě pro zápis formátu JSON.
* Metodu `CanConvert` popište pouze v případě potřeby. Výchozí implementace vrátí `true`, když typ, který má být převeden, je typ `T`. Proto převaděče, které podporují pouze typ `T`, nemusejí přepsat tuto metodu. Příklad převaděče, který musí přepsat tuto metodu, naleznete v části [polymorfní deserializace](#support-polymorphic-deserialization) dále v tomto článku.

Můžete odkazovat na [předdefinovaný zdrojový kód převaděče](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) jako referenční implementace pro psaní vlastních převaděčů.

## <a name="steps-to-follow-the-factory-pattern"></a>Postup pro postup pro model výroby

Následující postup vysvětluje, jak vytvořit převaděč podle vzorce pro vytváření:

* Vytvořte třídu, která je odvozena z <xref:System.Text.Json.Serialization.JsonConverterFactory>.
* Přepište metodu `CanConvert`, aby vracela hodnotu true, pokud je typ převodu ten, který může převaděč zpracovat. Pokud je například převaděč určený pro `List<T>` může zpracovat pouze `List<int>`, `List<string>`a `List<DateTime>`. 
* Přepište metodu `CreateConverter` pro vrácení instance třídy převaděče, která bude zpracovávat typ k převodu, který je k dispozici za běhu.
* Vytvořte třídu převaděče, kterou vytváří instance metody `CreateConverter`. 

Model továrny je vyžadován pro otevřené generické typy, protože kód pro převod objektu na a z řetězce není stejný pro všechny typy. Převaděč pro otevřený obecný typ (`List<T>`, například) musí vytvořit převaděč pro uzavřený obecný typ (`List<DateTime>`, například) na pozadí. Kód musí být napsán pro zpracování každého uzavřeného a obecného typu, který může převaděč zpracovat.

Typ `Enum` je podobný otevřenému obecnému typu: převaděč pro `Enum` musí vytvořit převaděč pro konkrétní `Enum` (například`WeekdaysEnum`) na pozadí. 

## <a name="error-handling"></a>Zpracování chyb

Pokud potřebujete vyvolat výjimku v kódu pro zpracování chyb, zvažte vyvolání <xref:System.Text.Json.JsonException> bez zprávy. Tento typ výjimky automaticky vytvoří zprávu, která obsahuje cestu k části JSON, která způsobila chybu. Například příkaz `throw new JsonException();` vytvoří chybovou zprávu jako v následujícím příkladu:

```text
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

Pokud zadáte zprávu (například `throw new JsonException("Error occurred)`, výjimka stále poskytne cestu ve vlastnosti <xref:System.Text.Json.JsonException.Path>.

## <a name="register-a-custom-converter"></a>Registrace vlastního převaděče

*Zaregistrujte* vlastní převaděč a nastavte `Serialize` a metody `Deserialize` ho použít. Vyberte jeden z následujících přístupů:

* Přidejte instanci třídy Converter do kolekce <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.
* Použijte atribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) pro vlastnosti, které vyžadují vlastní převaděč.
* Použijte atribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) pro třídu nebo strukturu, která představuje vlastní typ hodnoty.

## <a name="registration-sample---converters-collection"></a>Registrace ukázek – kolekce převaděčů 

Tady je příklad, který nastaví `ExampleDateTimeOffsetConverter` jako výchozí pro vlastnosti typu `DateTimeOffset`:

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
string json = JsonSerializer.Serialize(weatherForecast, options);
```

Předpokládejme, že jste serializováni následující typ:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

Tady je příklad výstupu JSON, který ukazuje použití vlastního převaděče:

```json
{
  "Date": "08/01/2019",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

Následující kód používá stejný přístup k deserializaci pomocí vlastního převaděče `DateTimeOffset`:

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json, options);
```

## <a name="registration-sample---jsonconverter-on-a-property"></a>Ukázka registrace – [JsonConverter] u vlastnosti

Následující kód vybere vlastní převaděč pro vlastnost `Date`:

```csharp
class WeatherForecastWithConverter
{
    [JsonConverter(typeof(ExampleDateTimeOffsetConverter))]
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

Kód pro serializaci a deserializaci `WeatherForecastWithConverter` nevyžaduje použití `JsonSerializeOptions.Converters`:

```csharp
string json = JsonSerializer.Serialize(weatherForecastWithConverter);
```

```csharp
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithConverter>(json);
```

## <a name="registration-sample---jsonconverter-on-a-type"></a>Ukázka registrace – [JsonConverter] na typu

Zde je kód, který vytvoří strukturu a na ni aplikuje atribut `[JsonConverter]`:

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

Tady je vlastní převaděč pro předchozí strukturu:

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

Atribut `[JsonConvert]` ve struktuře registruje vlastní převaděč jako výchozí hodnotu pro vlastnosti typu `Temperature`. Při serializaci nebo deserializaci se převaděč automaticky použije na vlastnost `TemperatureC` následujícího typu:

```csharp
class WeatherForecastWithTemperatureStruct
{
    public DateTimeOffset Date { get; set; }
    public Temperature TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="converter-registration-precedence"></a>Priorita registrace převaděče

Při serializaci nebo deserializaci se pro každý prvek JSON v uvedeném pořadí vybere konvertor, který je uvedený z nejvyšší priority na nejnižší:

* `[JsonConverter]` použito pro vlastnost.
* Převaděč přidaný do kolekce `Converters`.
* `[JsonConverter]` použito pro vlastní typ hodnoty nebo POCO.

Pokud je v kolekci `Converters` zaregistrováno více vlastních převaděčů pro typ, je použit první převaděč, který vrací hodnotu true pro `CanConvert`.

Vestavěný převaděč je zvolen pouze v případě, že není registrován žádný použitelný vlastní převaděč.

## <a name="converter-samples-for-common-scenarios"></a>Ukázky převaděčů pro běžné scénáře

V následujících částech jsou uvedeny ukázky konvertorů, které řeší některé běžné scénáře, které vestavěná funkce nezpracovává.

### <a name="deserialize-inferred-types-to-object-properties"></a>Deserializace odvozených typů do vlastností objektu

Při deserializaci na vlastnost typu `Object`je vytvořen objekt `JsonElement`. Důvodem je, že deserializátor nezná typ CLR, který se má vytvořit, a nepokusí se odhadnout. Například pokud má vlastnost JSON hodnotu "true", deserializátor neodvodí, že hodnota je `Boolean`a pokud má element "01/01/2019", deserializátor neodvodí, že se jedná o `DateTime`.

Odvození typu může být nepřesné. Pokud deserializátor analyzuje číslo JSON, které nemá žádné desetinné místo jako `long`, což může vést k problémům mimo rozsah, pokud byla hodnota původně serializována jako `ulong` nebo `BigInteger`. Analýza čísla s desetinnou čárkou jako `double` může přijít o přesnost, pokud bylo číslo původně serializováno jako `decimal`.

Pro scénáře, které vyžadují odvození typu, ukazuje následující kód vlastní převaděč pro `Object` vlastnosti. Kód převede:

* `true` a `false` na `Boolean`
* Čísla `long` nebo `double`
* Kalendářní data `DateTime`
* Řetězce, které se mají `string`
* Všechno ostatní `JsonElement`

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

Následující kód registruje převaděč:

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new ObjectToInferredTypesConverter());
```

Tady je příklad typu s vlastností objektu:

```csharp
public class WeatherForecastWithObjectProperties
{
    public object Date { get; set; }
    public object TemperatureC { get; set; }
    public object Summary { get; set; }
}
```

Následující příklad JSON pro deserializaci obsahuje hodnoty, které budou deserializovat jako `DateTime`, `long`a `string`:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

Bez vlastního převaděče je deserializace v každé vlastnosti `JsonElement`.

[Složka testování částí](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) v oboru názvů `System.Text.Json.Serialization` obsahuje další příklady vlastních převaděčů, které zpracovávají deserializaci na vlastnosti objektu.

### <a name="support-dictionary-with-non-string-key"></a>Slovník podpory s jiným neřetězcovým klíčem

Integrovaná podpora pro kolekce slovníků je určena pro `Dictionary<string, TValue>`. To znamená, že klíč musí být řetězec. Pro podporu slovníku s celým číslem nebo jiným typem jako klíč je vyžadován vlastní převaděč.

Následující kód ukazuje vlastní převaděč, který spolupracuje s `Dictionary<Enum,TValue>`:

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

Následující kód registruje převaděč:

```csharp
var serializeOptions = new JsonSerializerOptions();
serializeOptions.Converters.Add(new ConverterDictionaryTKeyEnumTValue());
```

Konvertor může serializovat a deserializovat vlastnost `TemperatureRanges` následující třídy, která používá následující `Enum`:

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

Výstup JSON z serializace vypadá jako v následujícím příkladu:

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

[Složka testování částí](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) v oboru názvů `System.Text.Json.Serialization` obsahuje další příklady vlastních převaděčů, které zpracovávají slovníky neřetězcových klíčů.

### <a name="support-polymorphic-deserialization"></a>Podpora polymorfního deserializace

[Polymorfní serializace](system-text-json-how-to.md#serialize-properties-of-derived-classes) nevyžaduje vlastní převaděč, ale deserializace vyžaduje vlastní převaděč.

Předpokládejme například, že máte abstraktní základní třídu `Person` s `Employee` a `Customer` odvozené třídy. Polymorfní deserializace znamená, že v době návrhu můžete zadat `Person` jako cíl deserializace a `Customer` a `Employee` objekty ve formátu JSON jsou správně deserializovány za běhu. Během deserializace je nutné najít podoby, které identifikují požadovaný typ ve formátu JSON. Typy, které jsou k dispozici, se liší podle jednotlivých scénářů. Například může být k dispozici vlastnost diskriminátoru nebo může být nutné spoléhat na přítomnost určité vlastnosti nebo absence konkrétní vlastnosti. Aktuální verze `System.Text.Json` neposkytuje atributy pro určení způsobu zpracování polymorfních scénářů deserializace, takže jsou vyžadovány vlastní převaděče.

Následující kód ukazuje základní třídu, dvě odvozené třídy a vlastní konvertor pro ně. Převaděč používá vlastnost diskriminátor k provedení polymorfního deserializace. Diskriminátor typu není v definicích třídy, ale je vytvořen během serializace a je čten během deserializace.

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

Následující kód registruje převaděč:

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new PersonConverterWithTypeDiscriminator());
```

Konvertor může deserializovat JSON, který byl vytvořen pomocí stejného převaděče k serializaci, například:

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

## <a name="other-custom-converter-samples"></a>Další ukázky vlastního převaděče

[Složka testování částí](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) ve zdrojovém kódu `System.Text.Json.Serialization` obsahuje další ukázky vlastního převaděče, jako například:

* převaděč `Int32`, který při deserializaci převede hodnotu null na 0
* převaděč `Int32`, který umožňuje v případě deserializace řetězcové i číselné hodnoty
* převaděč `Enum`
* převaděč `List<T>`, který přijímá externí data
* převaděč `Long[]`, který pracuje se seznamem čísel oddělených čárkami 

## <a name="additional-resources"></a>Další zdroje

* [Přehled System. text. JSON](system-text-json-overview.md)
* [Reference k rozhraní API System. text. JSON](xref:System.Text.Json)
* [Jak používat System. text. JSON](system-text-json-how-to.md)
* [Zdrojový kód pro předdefinované převaděče](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* Problémy GitHubu související s vlastními převaděči pro `System.Text.Json`
  * [36639 Představujeme vlastní převaděče](https://github.com/dotnet/corefx/issues/36639)
  * [38713 o deserializaci do objektu](https://github.com/dotnet/corefx/issues/38713)
  * [40120 o slovnících bez řetězcových klíčů](https://github.com/dotnet/corefx/issues/40120)
  * [37787 o polymorfní deserializaci](https://github.com/dotnet/corefx/issues/37787)
