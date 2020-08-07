---
title: Podpora DateTime a DateTimeOffset v System.Text.Json
description: Přehled způsobu, jakým jsou typy DateTime a DateTimeOffset podporovány v System.Text.Jsv knihovně.
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
ms.openlocfilehash: 1c573712f458d3e22cd59112b9e79e85391270c1
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87854890"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>Podpora DateTime a DateTimeOffset v System.Text.Json

System.Text.Jsv knihovně analyzuje a zapisuje <xref:System.DateTime> <xref:System.DateTimeOffset> hodnoty a hodnoty podle ROZŠÍŘENÉHO profilu ISO 8601:-2019.
[Převaděče](xref:System.Text.Json.Serialization.JsonConverter%601) poskytují vlastní podporu pro serializaci a deserializaci pomocí <xref:System.Text.Json.JsonSerializer> .
Vlastní podporu je také možné implementovat při použití <xref:System.Text.Json.Utf8JsonReader> a <xref:System.Text.Json.Utf8JsonWriter> .

## <a name="support-for-the-iso-8601-12019-format"></a>Podpora formátu ISO 8601-1:2019

<xref:System.Text.Json.JsonSerializer>Typy, <xref:System.Text.Json.Utf8JsonReader> , <xref:System.Text.Json.Utf8JsonWriter> a <xref:System.Text.Json.JsonElement> analyzují a zapisují <xref:System.DateTime> a <xref:System.DateTimeOffset> text reprezentují v závislosti na rozšířeném profilu formátu ISO 8601-1:2019, například 2019-07-26T16:59:57-05:00.

<xref:System.DateTime>a <xref:System.DateTimeOffset> data lze serializovat pomocí <xref:System.Text.Json.JsonSerializer> :

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

Lze je také deserializovat pomocí <xref:System.Text.Json.JsonSerializer> :

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

S výchozími možnostmi <xref:System.DateTime> <xref:System.DateTimeOffset> musí být vstupní a textové reprezentace v souladu s rozšířeným profilem ISO 8601-1:2019.
Pokus o rekonstrukci reprezentace, která není v souladu s profilem, by způsobil <xref:System.Text.Json.JsonSerializer> vyvolání <xref:System.Text.Json.JsonException> :

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

<xref:System.Text.Json.JsonDocument>Poskytuje strukturovaný přístup k obsahu datové části JSON, včetně <xref:System.DateTime> a <xref:System.DateTimeOffset> reprezentace. Níže uvedený příklad ukazuje, jak se při dané kolekci teplot vypočte průměrná teplota v pondělí:

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

Pokud se pokusíte vypočítat průměrnou teplotu pro datovou část s neodpovídajícími <xref:System.DateTime> reprezentacemi, bude <xref:System.Text.Json.JsonDocument> vyvolávat <xref:System.FormatException> :

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

<xref:System.Text.Json.Utf8JsonWriter>Zápisy <xref:System.DateTime> a data nižší úrovně <xref:System.DateTimeOffset> :

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader>analyzuje <xref:System.DateTime> a <xref:System.DateTimeOffset> data:

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

Při pokusu o čtení nekompatibilních formátů se <xref:System.Text.Json.Utf8JsonReader> způsobí, že vyvolá výjimku <xref:System.FormatException> :

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>Vlastní podpora pro <xref:System.DateTime> a<xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>Při použití<xref:System.Text.Json.JsonSerializer>

Pokud chcete, aby serializátor prováděl vlastní analýzu nebo formátování, můžete implementovat [vlastní převaděče](xref:System.Text.Json.Serialization.JsonConverter%601).
Tady je pár příkladů:

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>Používání `DateTime(Offset).Parse` a`DateTime(Offset).ToString`

Pokud nemůžete určit formáty vstupních <xref:System.DateTime> nebo <xref:System.DateTimeOffset> textových reprezentace, můžete použít `DateTime(Offset).Parse` metodu v logice Read. To vám umožní použít. Rozsáhlá podpora pro analýzu různých <xref:System.DateTime> <xref:System.DateTimeOffset> formátů textu, včetně řetězců jiných než ISO 8601 a formátů ISO 8601, které neodpovídají rozšířenému profilu ISO 8601-1:2019. Tento přístup je výrazně menší než použití nativní implementace serializátoru.

Pro serializaci můžete použít `DateTime(Offset).ToString` metodu ve vaší logice zápisu převaděče. To vám umožní zapisovat <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty pomocí libovolného [standardního formátu data a času](../base-types/standard-date-and-time-format-strings.md)a [vlastních formátů data a času](../base-types/custom-date-and-time-format-strings.md).
To je také podstatně méně prováděno, než použití nativní implementace serializátoru.

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> Při implementaci <xref:System.Text.Json.Serialization.JsonConverter%601> , `T` <xref:System.DateTime> `typeToConvert` parametr bude vždy `typeof(DateTime)` .
Parametr je vhodný pro zpracování polymorfních případů a při použití obecných typů k získání `typeof(T)` v provedených způsobech.

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>Používání <xref:System.Buffers.Text.Utf8Parser> a<xref:System.Buffers.Text.Utf8Formatter>

V logice převaděče můžete použít rychlou metodu analýzy a formátování založenou na kódování UTF-8, <xref:System.DateTime> Pokud <xref:System.DateTimeOffset> jsou vstupní nebo textové reprezentace kompatibilní s jedním z [řetězců formátu data a času standardu](../base-types/standard-date-and-time-format-strings.md)"R", "l", "O" nebo "G" nebo pokud chcete zapisovat do jednoho z těchto formátů. To je mnohem rychlejší než použití `DateTime(Offset).Parse` a `DateTime(Offset).ToString` .

Tento příklad ukazuje vlastní převaděč, který serializace a deserializace <xref:System.DateTime> hodnoty podle [standardního formátu "R"](../base-types/standard-date-and-time-format-strings.md#the-rfc1123-r-r-format-specifier):

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> Standardní formát "R" bude vždy 29 znaků dlouhý.
>
> Formát "l" (malými písmeny "L") není dokumentován v jiných [standardních formátovacích řetězcích data a času](../base-types/standard-date-and-time-format-strings.md) , protože je podporován pouze `Utf8Parser` `Utf8Formatter` typy a. Formát je malými písmeny RFC 1123 (v malých verzích formátu "R"), například: "čtvrtek, 25 červenec 2019 06:36:07 GMT".

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>Použití `DateTime(Offset).Parse` jako záložní pro nativní analýzu serializátoru

Pokud obecně očekáváte, že váš vstup <xref:System.DateTime> nebo <xref:System.DateTimeOffset> data budou v souladu s rozšířeným profilem ISO 8601-1:2019, můžete použít logiku nativní analýzy pro serializátor. Můžete také implementovat záložní mechanismus jenom pro případ.
Tento příklad ukazuje, že po selhání analýzy <xref:System.DateTime> textové reprezentace pomocí <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)> převaděče úspěšně analyzuje data pomocí <xref:System.DateTime.Parse(System.String)> .

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>Při psaní pomocí<xref:System.Text.Json.Utf8JsonWriter>

Chcete-li napsat vlastní <xref:System.DateTime> nebo <xref:System.DateTimeOffset> textovou reprezentaci pomocí <xref:System.Text.Json.Utf8JsonWriter> , můžete vlastní reprezentaci naformátovat na <xref:System.String> , `ReadOnlySpan<Byte>` , `ReadOnlySpan<Char>` nebo <xref:System.Text.Json.JsonEncodedText> , a pak ji předat odpovídající <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A?displayProperty=nameWithType> nebo <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A?displayProperty=nameWithType> metodě.

Následující příklad ukazuje <xref:System.DateTime> , jak lze vytvořit vlastní formát pomocí <xref:System.DateTime.ToString(System.String,System.IFormatProvider)> , pak napsaný pomocí <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)> metody:

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>Při čtení pomocí<xref:System.Text.Json.Utf8JsonReader>

Pokud si chcete přečíst vlastní <xref:System.DateTime> nebo <xref:System.DateTimeOffset> textovou reprezentaci pomocí <xref:System.Text.Json.Utf8JsonReader> , můžete získat hodnotu aktuálního tokenu JSON jako <xref:System.String> using <xref:System.Text.Json.Utf8JsonReader.GetString> a pak analyzovat hodnotu pomocí vlastní logiky.

Následující příklad ukazuje <xref:System.DateTimeOffset> , jak lze načíst vlastní textovou reprezentaci pomocí <xref:System.Text.Json.Utf8JsonReader.GetString> a poté analyzovat pomocí <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)> :

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>Rozšířený profil ISO 8601-1:2019 v System.Text.Jszapnutý

### <a name="date-and-time-components"></a>Komponenty data a času

Rozšířený profil ISO 8601-1:2019 implementovaný v nástroji <xref:System.Text.Json> definuje následující komponenty pro reprezentace data a času. Tyto komponenty se používají k definování různých úrovní členitosti při analýze a formátování <xref:System.DateTime> a <xref:System.DateTimeOffset> reprezentace.

| Komponenta       | Formát                      | Popis                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Year            | "yyyy"                      | 0001-9999                                                                       |
| Month           | "MM"                        | 01-12                                                                           |
| Den             | "dd"                        | 01-28, 01-29, 01-30, 01-31 v závislosti na měsíci/roce                                  |
| Hodina            | "HH"                        | 00-23                                                                           |
| Minuta          | "mm"                        | 00-59                                                                           |
| Second          | "ss"                        | 00-59                                                                           |
| Druhý zlomek | "FFFFFFF"                   | Minimálně jedna číslice, maximálně 16 číslic                                      |
| Časový posun     | "K"                         | Buď "Z" nebo "(" + "/"-") HH": mm "                                                |
| Částečný čas    | "HH": ' mm ': ' ss [FFFFFFF] '     | Čas bez informací o posunu UTC                                             |
| Celé datum       | "yyyy-yyyy '-'dd"            | Datum kalendáře                                                                   |
| Plný čas       | "' Partial time'K           | UTC v den nebo místní čas s časovým posunem mezi místním časem a UTC |
| Datum a čas       | "" Celé datum "nemá plný čas" " | Datum a čas kalendáře, např. 2019-07-26T16:59:57-05:00                   |

### <a name="support-for-parsing"></a>Podpora pro analýzu

Pro analýzu jsou definovány následující úrovně členitosti:

1. "Celé datum"
    1. "yyyy-yyyy '-'dd"

2. "" Celé datum "t" hodina "": "min" "
    1. "yyyy-yyyy '-DD 't": "mm"

3. "" Celé datum "t" v částečný čas ""
    1. "yyyy-yyyy '-DD 't": ' mm ': ' ss ' ([specifikátor formátu ("s")](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))
    2. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF

4. "" Celé datum "t" Časová hodina "": minuta "časový posun" "
    1. "yyyy-yyyy '-DD 't": ' mmZ '
    2. "yyyy-yyyy '-DD 't": ' mm (' + '/'-') HH ': ' mm '

5. ' Datum a čas '
    1. "yyyy-yyyy '-DD 't": ' mm ': ' ssZ '
    2. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFFZ"
    3. "yyyy-yyyy '-DD 't": ' mm ': ' ss ' (' + '/'-') HH ': ' mm '
    4. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF (+ '/'-') HH ': mm

Pokud pro sekundy existují desetinné zlomky, musí existovat alespoň jedna číslice. `2019-07-26T00:00:00.`není povoleno.
I když je povolený až 16 zlomkových číslic, analyzují se jenom prvních sedm. Vše nad rámec, který je považován za nulu.
Například `2019-07-26T00:00:00.1234567890` se bude analyzovat, jako by to bylo `2019-07-26T00:00:00.1234567` .
Je tak udržování kompatibility s <xref:System.DateTime> implementací, což je omezeno na toto řešení.

Přestupné sekundy nejsou podporovány.

### <a name="support-for-formatting"></a>Podpora formátování

Pro formátování jsou definovány následující úrovně členitosti:

1. "" Celé datum "t" v částečný čas ""
    1. "yyyy-yyyy '-DD 't": ' mm ': ' ss ' ([specifikátor formátu ("s")](../base-types/standard-date-and-time-format-strings.md#the-sortable-s-format-specifier))

        Používá se k formátování <xref:System.DateTime> bez zlomků sekund a bez informací o posunu.

    2. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF

        Používá se k formátování <xref:System.DateTime> s zlomky sekund, ale bez informací o posunu.

2. ' Datum a čas '
    1. "yyyy-yyyy '-DD 't": ' mm ': ' ssZ '

        Používá se k formátování <xref:System.DateTime> bez zlomků sekund, ale s posunem UTC.

    2. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFFZ"

        Používá se k formátování na <xref:System.DateTime> zlomky sekund a s posunem UTC.

    3. "yyyy-yyyy '-DD 't": ' mm ': ' ss ' (' + '/'-') HH ': ' mm '

        Používá se k formátování <xref:System.DateTime> nebo <xref:System.DateTimeOffset> bez zlomků sekund, ale s lokálním posunem.

    4. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF (+ '/'-') HH ': mm

        Používá se k formátování <xref:System.DateTime> nebo <xref:System.DateTimeOffset> se zlomky sekund a s místním posunem.

Pokud je ve [formátu Round-Trip](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) reprezentace <xref:System.DateTime> instance nebo na <xref:System.DateTimeOffset> konci zlomků sekund, pak <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.Utf8JsonWriter> se naformátuje reprezentace instance bez koncových nul.
Například <xref:System.DateTime> instance, jejíž reprezentace [formátu Round-Trip](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) je `2019-04-24T14:50:17.1010000Z` , bude formátována jako `2019-04-24T14:50:17.101Z` <xref:System.Text.Json.JsonSerializer> a <xref:System.Text.Json.Utf8JsonWriter> .

Pokud je ve [formátu Round-Trip](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) reprezentace <xref:System.DateTime> instance nebo <xref:System.DateTimeOffset> v rámci zlomků sekund nula, pak <xref:System.Text.Json.JsonSerializer> a <xref:System.Text.Json.Utf8JsonWriter> naformátuje reprezentaci instance bez zlomků sekund.
Například <xref:System.DateTime> instance, jejíž reprezentace [formátu Round-Trip](../base-types/standard-date-and-time-format-strings.md#the-round-trip-o-o-format-specifier) je `2019-04-24T14:50:17.0000000+02:00` , bude formátována jako `2019-04-24T14:50:17+02:00` <xref:System.Text.Json.JsonSerializer> a <xref:System.Text.Json.Utf8JsonWriter> .

Zkrácení nul ve zlomkových číslicích umožňuje psát nejmenší výstup potřebný k zapsání informací o zpátečním přenosu.

Zapisuje se maximálně 7 číslic za desetinnou čárkou. Tím se zarovnává s <xref:System.DateTime> implementací, která je omezena na toto řešení.
