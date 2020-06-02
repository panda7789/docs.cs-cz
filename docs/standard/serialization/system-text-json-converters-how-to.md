---
title: Zápis vlastních převaděčů pro serializaci JSON – .NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: abda23ea538c2c0da6ada4f359ce745602dca45d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279760"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a>Zápis vlastních převaděčů pro serializaci JSON (zařazování) v .NET

Tento článek ukazuje, jak vytvořit vlastní převaděče pro třídy serializace JSON, které jsou k dispozici v <xref:System.Text.Json> oboru názvů. Úvod do najdete `System.Text.Json` [v tématu jak serializovat a deserializovat JSON v rozhraní .NET](system-text-json-how-to.md).

*Převodník* je třída, která převádí objekt nebo hodnotu na a z formátu JSON. `System.Text.Json`Obor názvů obsahuje integrované převaděče pro většinu primitivních typů, které jsou mapovány na primitivní prvky jazyka JavaScript. Můžete psát vlastní převaděče:

* Chcete-li přepsat výchozí chování vestavěného převaděče. Například můžete chtít, `DateTime` aby hodnoty byly reprezentovány ve formátu mm/dd/rrrr namísto výchozího formátu ISO 8601-1:2019.
* Pro podporu vlastního typu hodnoty. Například `PhoneNumber` Struktura.

Můžete také napsat vlastní převaděče pro přizpůsobení nebo rozšiřování `System.Text.Json` s funkcemi, které nejsou součástí aktuální verze. Následující scénáře jsou pokryté dále v tomto článku:

* [Deserializace odvozených typů do vlastností objektu](#deserialize-inferred-types-to-object-properties).
* [Slovník podpory s jiným neřetězcovým klíčem](#support-dictionary-with-non-string-key)
* [Podpora polymorfního deserializace](#support-polymorphic-deserialization).
* [Podpora zpátečního přenosu pro zásobník \<T> ](#support-round-trip-for-stackt)

## <a name="custom-converter-patterns"></a>Vlastní vzory převaděče

Existují dva vzory pro vytvoření vlastního převaděče: základní vzor a model továrny. Vzor továrny je pro převaděče, které zpracovávají typy `Enum` nebo otevřou obecné typy. Základní vzor je pro neobecný a uzavřený obecný typ.  Například převaděče pro následující typy vyžadují model továrny:

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

Mezi příklady typů, které lze zpracovat pomocí základního vzoru, patří:

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

Základní vzor vytvoří třídu, která může zpracovat jeden typ. Model Factory vytvoří třídu, která určuje, za běhu, který konkrétní typ je vyžadován, a dynamicky vytvoří odpovídající převaděč.

## <a name="sample-basic-converter"></a>Ukázka základního převaděče

Následující ukázka je převaděč, který přepisuje výchozí serializaci pro existující datový typ. Převaděč používá pro vlastnosti formát mm/dd/rrrr `DateTimeOffset` .

[!code-csharp[](snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a>Ukázkový konvertor vzorků výrobního modelu

Následující kód ukazuje vlastní převaděč, který pracuje s `Dictionary<Enum,TValue>` . Kód se řídí modelem továrny, protože první parametr obecného typu je `Enum` a druhý je otevřený. `CanConvert`Metoda vrátí `true` pouze pro a `Dictionary` se dvěma obecnými parametry, první z nich je `Enum` typ. Vnitřní převaděč získá existující převaděč pro zpracování podle typu, který je k dispozici v době běhu pro `TValue` .

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

Předchozí kód je stejný jako ten, který je zobrazen ve [slovníku podpory s jiným než řetězcovým klíčem](#support-dictionary-with-non-string-key) , dále v tomto článku.

## <a name="steps-to-follow-the-basic-pattern"></a>Postup pro postup pro základní vzor

Následující postup vysvětluje, jak vytvořit převaděč podle základního vzoru:

* Vytvořte třídu, která je odvozena z <xref:System.Text.Json.Serialization.JsonConverter%601> Where `T` je typ k serializaci a deserializaci.
* Přepsat `Read` metodu pro deserializaci příchozího JSON a převést jej na typ `T` . Použijte <xref:System.Text.Json.Utf8JsonReader> metodu, která je předána metodě pro čtení formátu JSON.
* Přepsat `Write` metodu pro serializaci příchozího objektu typu `T` . Použijte <xref:System.Text.Json.Utf8JsonWriter> metodu, která je předána metodě pro zápis formátu JSON.
* Metodu popište `CanConvert` pouze v případě potřeby. Výchozí implementace vrátí, `true` když typ, který má být převeden, je typu `T` . Proto převaděče, které podporují pouze typ, `T` nemusejí přepisovat tuto metodu. Příklad převaděče, který musí přepsat tuto metodu, naleznete v části [polymorfní deserializace](#support-polymorphic-deserialization) dále v tomto článku.

Můžete odkazovat na [předdefinovaný zdrojový kód převaděče](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) jako referenční implementace pro psaní vlastních převaděčů.

## <a name="steps-to-follow-the-factory-pattern"></a>Postup pro postup pro model výroby

Následující postup vysvětluje, jak vytvořit převaděč podle vzorce pro vytváření:

* Vytvořte třídu, která je odvozena z <xref:System.Text.Json.Serialization.JsonConverterFactory> .
* Přepsat `CanConvert` metodu pro vrácení hodnoty true, pokud typ, který má být převeden, je ten, který může převaděč zpracovat. Například pokud je převodník pro `List<T>` IT, může zpracovat pouze `List<int>` , `List<string>` , a `List<DateTime>` .
* Přepsat `CreateConverter` metodu pro vrácení instance třídy převaděče, která bude zpracovávat typ k převodu, který je k dispozici v době běhu.
* Vytvořte třídu převaděče, kterou `CreateConverter` Metoda vytvoří.

Model továrny je vyžadován pro otevřené generické typy, protože kód pro převod objektu na a z řetězce není stejný pro všechny typy. Převaděč pro otevřený obecný typ (například `List<T>` ) musí vytvořit převaděč pro uzavřený obecný typ ( `List<DateTime>` například) na pozadí. Kód musí být napsán pro zpracování každého uzavřeného a obecného typu, který může převaděč zpracovat.

`Enum`Typ je podobný otevřenému obecnému typu: převaděč pro `Enum` musí vytvořit převodník pro konkrétní `Enum` ( `WeekdaysEnum` například) na pozadí.

## <a name="error-handling"></a>Zpracování chyb

Pokud potřebujete vyvolat výjimku v kódu pro zpracování chyb, zvažte vyvolání <xref:System.Text.Json.JsonException> bez zprávy. Tento typ výjimky automaticky vytvoří zprávu, která obsahuje cestu k části JSON, která způsobila chybu. Například příkaz `throw new JsonException();` vytvoří chybovou zprávu jako v následujícím příkladu:

```
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

Pokud zadáte zprávu (například `throw new JsonException("Error occurred")` , výjimka stále poskytuje cestu ve <xref:System.Text.Json.JsonException.Path> Vlastnosti.

## <a name="register-a-custom-converter"></a>Registrace vlastního převaděče

*Zaregistrujte* vlastní převaděč, pomocí kterého budou `Serialize` `Deserialize` metody a použity. Vyberte jeden z následujících přístupů:

* Přidejte do kolekce instanci třídy Converter <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> .
* Použijte atribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) pro vlastnosti, které vyžadují vlastní převaděč.
* Použijte atribut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) pro třídu nebo strukturu, která představuje vlastní typ hodnoty.

## <a name="registration-sample---converters-collection"></a>Registrace ukázek – kolekce převaděčů

Tady je příklad, který nastaví <xref:System.ComponentModel.DateTimeOffsetConverter> výchozí nastavení pro vlastnosti typu <xref:System.DateTimeOffset> :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

Předpokládejme, že jste serializováni instanci následujícího typu:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

Tady je příklad výstupu JSON, který ukazuje použití vlastního převaděče:

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Následující kód používá stejný přístup k deserializaci pomocí vlastního `DateTimeOffset` převaděče:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a>Ukázka registrace – [JsonConverter] u vlastnosti

Následující kód vybere vlastní převaděč pro `Date` vlastnost:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

Kód pro serializaci `WeatherForecastWithConverterAttribute` nevyžaduje použití `JsonSerializeOptions.Converters` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

Kód k deserializaci také nevyžaduje použití `Converters` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a>Ukázka registrace – [JsonConverter] na typu

Zde je kód, který vytvoří strukturu a použije `[JsonConverter]` atribut na něj:

[!code-csharp[](snippets/system-text-json-how-to/csharp/Temperature.cs)]

Tady je vlastní převaděč pro předchozí strukturu:

[!code-csharp[](snippets/system-text-json-how-to/csharp/TemperatureConverter.cs)]

`[JsonConvert]`Atribut ve struktuře registruje vlastní převaděč jako výchozí hodnotu vlastností typu `Temperature` . `TemperatureCelsius`Při serializaci nebo deserializaci se převaděč automaticky použije u vlastnosti následujícího typu:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a>Priorita registrace převaděče

Při serializaci nebo deserializaci se pro každý prvek JSON v uvedeném pořadí vybere konvertor, který je uvedený z nejvyšší priority na nejnižší:

* `[JsonConverter]`použito pro vlastnost.
* Převaděč přidaný do `Converters` kolekce.
* `[JsonConverter]`použito pro vlastní typ hodnoty nebo POCO.

Pokud je v kolekci zaregistrováno více vlastních převaděčů pro typ `Converters` , je použit první převaděč, který vrací hodnotu true pro `CanConvert` .

Vestavěný převaděč je zvolen pouze v případě, že není registrován žádný použitelný vlastní převaděč.

## <a name="converter-samples-for-common-scenarios"></a>Ukázky převaděčů pro běžné scénáře

V následujících částech jsou uvedeny ukázky konvertorů, které řeší některé běžné scénáře, které vestavěná funkce nezpracovává.

* [Deserializace odvozených typů do vlastností objektu](#deserialize-inferred-types-to-object-properties)
* [Slovník podpory s jiným neřetězcovým klíčem](#support-dictionary-with-non-string-key)
* [Podpora polymorfního deserializace](#support-polymorphic-deserialization)
* [Podpora zpátečního přenosu pro zásobník \<T> ](#support-round-trip-for-stackt)

### <a name="deserialize-inferred-types-to-object-properties"></a>Deserializace odvozených typů do vlastností objektu

Při deserializaci na vlastnost typu `object` `JsonElement` je vytvořen objekt. Důvodem je, že deserializátor nezná typ CLR, který se má vytvořit, a nepokusí se odhadnout. Například pokud má vlastnost JSON hodnotu "true", deserializátor neodvodí, že hodnota je a `Boolean` Pokud má element "01/01/2019", deserializátor neodvodí, že se jedná o `DateTime` .

Odvození typu může být nepřesné. Pokud deserializátor analyzuje číslo JSON, které nemá desetinnou čárku jako `long` , což může vést k problémům mimo rozsah, pokud byla hodnota původně serializována jako `ulong` nebo `BigInteger` . Analýza čísla, které má desetinnou čárku jako `double` může přijít o přesnost, pokud bylo číslo původně serializováno jako `decimal` .

Pro scénáře, které vyžadují odvození typu, následující kód ukazuje vlastní převaděč pro `object` Vlastnosti. Kód převede:

* `true`a `false` na`Boolean`
* Čísla bez desetinné čárky`long`
* Čísla s desetinným čárkou`double`
* Data do`DateTime`
* Řetězce na`string`
* Všechno ostatní k`JsonElement`

[!code-csharp[](snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs)]

Následující kód registruje převaděč:

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

Tady je příklad typu s `object` vlastnostmi:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

Následující příklad JSON pro deserializaci obsahuje hodnoty, které budou deserializovat jako `DateTime` , `long` a `string` :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Bez vlastního převaděče zaznamená deserializace `JsonElement` v každé vlastnosti.

[Složka testování částí](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) v `System.Text.Json.Serialization` oboru názvů obsahuje další příklady vlastních převaděčů, které zpracovávají deserializaci na `object` Vlastnosti.

### <a name="support-dictionary-with-non-string-key"></a>Slovník podpory s jiným neřetězcovým klíčem

Integrovaná podpora pro kolekce slovníku je určena pro `Dictionary<string, TValue>` . To znamená, že klíč musí být řetězec. Pro podporu slovníku s celým číslem nebo jiným typem jako klíč je vyžadován vlastní převaděč.

Následující kód ukazuje vlastní převaděč, který spolupracuje s `Dictionary<Enum,TValue>` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs)]

Následující kód registruje převaděč:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

Konvertor může serializovat a deserializovat `TemperatureRanges` vlastnost následující třídy, která používá následující `Enum` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

Výstup JSON z serializace vypadá jako v následujícím příkladu:

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

[Složka testování částí](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) v `System.Text.Json.Serialization` oboru názvů obsahuje další příklady vlastních převaděčů, které zpracovávají slovníky nepoužívající řetězce.

### <a name="support-polymorphic-deserialization"></a>Podpora polymorfního deserializace

Integrované funkce poskytují omezený rozsah [polymorfní serializace](system-text-json-how-to.md#serialize-properties-of-derived-classes) , ale vůbec nepodporují deserializaci. Deserializace vyžaduje vlastní převaděč.

Předpokládejme například, že máte `Person` abstraktní základní třídu s `Employee` a `Customer` odvozené třídy. Polymorfní deserializace znamená, že v době návrhu můžete určit `Person` jako cíl deserializace a `Customer` `Employee` objekty ve formátu JSON jsou v době běhu správně deserializovány. Během deserializace je nutné najít podoby, které identifikují požadovaný typ ve formátu JSON. Typy, které jsou k dispozici, se liší podle jednotlivých scénářů. Například může být k dispozici vlastnost diskriminátoru nebo může být nutné spoléhat na přítomnost určité vlastnosti nebo absence konkrétní vlastnosti. Aktuální verze `System.Text.Json` neposkytuje atributy pro určení způsobu zpracování polymorfních scénářů deserializace, takže jsou vyžadovány vlastní převaděče.

Následující kód ukazuje základní třídu, dvě odvozené třídy a vlastní konvertor pro ně. Převaděč používá vlastnost diskriminátor k provedení polymorfního deserializace. Diskriminátor typu není v definicích třídy, ale je vytvořen během serializace a je čten během deserializace.

[!code-csharp[](snippets/system-text-json-how-to/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs)]

Následující kód registruje převaděč:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

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

Kód převaděče v předchozím příkladu čte a zapisuje každou vlastnost ručně. Alternativou je volání `Deserialize` nebo `Serialize` k provedení některé práce. Příklad najdete v [tomto příspěvku StackOverflow](https://stackoverflow.com/a/59744873/12509023).

### <a name="support-round-trip-for-stackt"></a>Podpora zpátečního přenosu pro zásobník\<T>

Pokud deserializovat řetězec JSON na <xref:System.Collections.Generic.Stack%601> objekt a potom tento objekt serializovat, je obsah zásobníku v opačném pořadí. Toto chování platí pro následující typy a rozhraní a uživatelsky definované typy, které jsou z nich odvozeny:

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

Pro podporu serializace a deserializace, která uchovává původní pořadí v zásobníku, je vyžadován vlastní převaděč.

Následující kód ukazuje vlastní převaděč, který umožňuje příkaz Round-Trip do a z `Stack<T>` objektů:

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs)]

Následující kód registruje převaděč:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs?name=SnippetRegister)]

## <a name="other-custom-converter-samples"></a>Další ukázky vlastního převaděče

Článek [migrace z Newtonsoft.Json na System.Text.Json ](system-text-json-migrate-from-newtonsoft-how-to.md) verzi obsahuje další ukázky vlastních převaděčů.

[Složka testování částí](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) ve `System.Text.Json.Serialization` zdrojovém kódu zahrnuje další ukázky převaděčů, například:

* [Konvertor Int32, který při deserializaci převede hodnotu null na 0](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)
* [Konvertor Int32, který umožňuje řetězcové i číselné hodnoty při deserializaci](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)
* [Konvertor Enum](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)
* [\<T>Převaděč seznamu, který přijímá externí data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)
* [Long [] převaděč, který funguje se seznamem čísel oddělených čárkami](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)

Pokud potřebujete vytvořit převaděč, který upraví chování existujícího integrovaného převaděče, můžete získat [zdrojový kód existujícího převaděče](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) , který slouží jako výchozí bod pro přizpůsobení.

## <a name="additional-resources"></a>Další zdroje

* [Zdrojový kód pro předdefinované převaděče](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)
* [Podpora DateTime a DateTimeOffset vSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.JsonPřehled](system-text-json-overview.md)
* [Jak používatSystem.Text.Json](system-text-json-how-to.md)
* [Postup migrace zNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [System.Text.JsonReference k rozhraní API](xref:System.Text.Json)
* [System.Text.Json. Reference k rozhraní API serializace](xref:System.Text.Json.Serialization)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
