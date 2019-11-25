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
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>Podpora DateTime a DateTimeOffset v System.Text.Json

Knihovna System. text. JSON analyzuje a zapisuje hodnoty <xref:System.DateTime> a <xref:System.DateTimeOffset> podle rozšířeného profilu ISO 8601:-2019.
[Převaděče](xref:System.Text.Json.Serialization.JsonConverter%601) poskytují vlastní podporu pro serializaci a deserializaci pomocí <xref:System.Text.Json.JsonSerializer>.
Vlastní podporu je taky možné implementovat při použití <xref:System.Text.Json.Utf8JsonReader> a <xref:System.Text.Json.Utf8JsonWriter>.

## <a name="support-for-the-iso-8601-12019-format"></a>Podpora formátu ISO 8601-1:2019

<xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, <xref:System.Text.Json.Utf8JsonWriter>a <xref:System.Text.Json.JsonElement> typy analyzují a zapisují <xref:System.DateTime> a <xref:System.DateTimeOffset> text reprezentovat podle rozšířeného profilu formátu ISO 8601-1:2019; například 2019-07-26T16:59:57-05:00.

data <xref:System.DateTime> a <xref:System.DateTimeOffset> je možné serializovat pomocí <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

Lze je také deserializovat pomocí <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

Ve výchozím nastavení musí být vstupní <xref:System.DateTime> a <xref:System.DateTimeOffset> reprezentace textu v souladu s rozšířeným profilem ISO 8601-1:2019.
Při pokusu o deserializaci reprezentace, která není v souladu s profilem, dojde k vygenerování <xref:System.Text.Json.JsonException><xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

<xref:System.Text.Json.JsonDocument> poskytuje strukturovaný přístup k obsahu datové části JSON, včetně <xref:System.DateTime> a <xref:System.DateTimeOffset> reprezentace. Níže uvedený příklad ukazuje, jak se při dané kolekci teplot vypočte průměrná teplota v pondělí:

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

Při pokusu o výpočet průměrné teploty pro datovou část s nevyhovujícími <xref:System.DateTime> reprezentující by <xref:System.Text.Json.JsonDocument> vyvolala <xref:System.FormatException>:

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

<xref:System.Text.Json.Utf8JsonWriter> nižší úrovně zapisuje <xref:System.DateTime> a <xref:System.DateTimeOffset> data:

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader> analyzuje <xref:System.DateTime> a <xref:System.DateTimeOffset> data:

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

Při pokusu o čtení nekompatibilních formátů pomocí <xref:System.Text.Json.Utf8JsonReader> způsobí, že vyvolá <xref:System.FormatException>:

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>Vlastní podpora pro <xref:System.DateTime> a <xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>Při použití <xref:System.Text.Json.JsonSerializer>

Pokud chcete, aby serializátor prováděl vlastní analýzu nebo formátování, můžete implementovat [vlastní převaděče](xref:System.Text.Json.Serialization.JsonConverter%601).
Tady je několik příkladů:

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>Používání `DateTime(Offset).Parse` a `DateTime(Offset).ToString`

Pokud nemůžete určit formáty vstupních <xref:System.DateTime> nebo <xref:System.DateTimeOffset> reprezentace textu, můžete použít metodu `DateTime(Offset).Parse` v logice Read. To vám umožní použít. Rozsáhlá podpora pro analýzu různých formátů <xref:System.DateTime> a <xref:System.DateTimeOffset> textu, včetně řetězců jiných než ISO 8601 a formátů ISO 8601, které neodpovídají rozšířenému profilu ISO 8601-1:2019. Tento přístup je výrazně menší než použití nativní implementace serializátoru.

Pro serializaci můžete použít metodu `DateTime(Offset).ToString` ve vaší logice zápisu převaděče. To umožňuje psát <xref:System.DateTime> a <xref:System.DateTimeOffset> hodnoty pomocí libovolného [standardního formátu data a času](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)a [vlastních formátů data a času](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).
To je také podstatně méně prováděno, než použití nativní implementace serializátoru.

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> Při implementaci <xref:System.Text.Json.Serialization.JsonConverter%601>a `T` je <xref:System.DateTime>, parametr `typeToConvert` bude vždy `typeof(DateTime)`.
Parametr je vhodný pro zpracování polymorfních případů a při použití obecných typů k získání `typeof(T)` způsobem.

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>Používání <xref:System.Buffers.Text.Utf8Parser> a <xref:System.Buffers.Text.Utf8Formatter>

V logice převaděče můžete použít rychlé metody analýzy a formátování založené na kódování UTF-8, pokud vstupní <xref:System.DateTime> nebo <xref:System.DateTimeOffset> textové reprezentace jsou v souladu s jedním z [řetězců formátu data a času standard](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)"R", "l", "O" nebo "G" nebo chcete zapisovat do jednoho z těchto formátů. To je mnohem rychlejší než použití `DateTime(Offset).Parse` a `DateTime(Offset).ToString`.

Tento příklad ukazuje vlastní převaděč, který serializace a deserializace <xref:System.DateTime> hodnoty podle [standardního formátu "R"](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> Standardní formát "R" bude vždy 29 znaků dlouhý.

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>Použití `DateTime(Offset).Parse` jako záložního pro nativní analýzu serializátoru

Pokud jste obecně očekávali, že vstupní <xref:System.DateTime> nebo <xref:System.DateTimeOffset> data v souladu s rozšířeným profilem ISO 8601-1:2019, můžete použít logiku nativní analýzy pro serializátor. Můžete také implementovat záložní mechanismus jenom pro případ.
Tento příklad ukazuje, že po selhání analýzy <xref:System.DateTime> textové reprezentace pomocí <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>převaděč úspěšně analyzuje data pomocí <xref:System.DateTime.Parse(System.String)>.

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>Při psaní pomocí <xref:System.Text.Json.Utf8JsonWriter>

Pokud chcete napsat vlastní <xref:System.DateTime> nebo <xref:System.DateTimeOffset> textovou reprezentaci pomocí <xref:System.Text.Json.Utf8JsonWriter>, můžete vlastní reprezentaci naformátovat na <xref:System.String>, `ReadOnlySpan<Byte>`, `ReadOnlySpan<Char>`nebo <xref:System.Text.Json.JsonEncodedText>, a pak ji předat odpovídající metodě [Utf8JsonWriter. WriteStringValue](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestringvalue?view=netcore-3.0) nebo [Utf8JsonWriter. WriteString](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestring?view=netcore-3.0) .

Následující příklad ukazuje, jak lze vytvořit vlastní <xref:System.DateTime> formát pomocí <xref:System.DateTime.ToString(System.String,System.IFormatProvider)>a následně napsaný metodou <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)>:

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>Při čtení pomocí <xref:System.Text.Json.Utf8JsonReader>

Pokud chcete číst vlastní <xref:System.DateTime> nebo <xref:System.DateTimeOffset> textovou reprezentaci <xref:System.Text.Json.Utf8JsonReader>, můžete získat hodnotu aktuálního tokenu JSON jako <xref:System.String> pomocí <xref:System.Text.Json.Utf8JsonReader.GetString>a pak hodnotu analyzovat pomocí vlastní logiky.

Následující příklad ukazuje, jak lze načíst vlastní <xref:System.DateTimeOffset> textovou reprezentaci pomocí <xref:System.Text.Json.Utf8JsonReader.GetString>a pak analyzovat pomocí <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>:

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>Rozšířený profil ISO 8601-1:2019 v souboru System. text. JSON

### <a name="date-and-time-components"></a>Komponenty data a času

Rozšířený profil ISO 8601-1:2019 implementovaný v <xref:System.Text.Json> definuje následující komponenty pro reprezentace data a času. Tyto komponenty se používají k definování různých úrovní členitosti při analýze a formátování <xref:System.DateTime> a <xref:System.DateTimeOffset> reprezentace.

| Součást       | Formát                      | Popis                                                                     |
|-----------------|-----------------------------|---------------------------------------------------------------------------------|
| Rok            | "yyyy"                      | 0001-9999                                                                       |
| Měsíčně           | "MM"                        | 01-12                                                                           |
| Den             | "dd"                        | 01-28, 01-29, 01-30, 01-31 v závislosti na měsíci/roce                                  |
| Hodina            | "HH"                        | 00-23                                                                           |
| Minuta          | "mm"                        | 00-59                                                                           |
| Sekunda          | "ss"                        | 00-59                                                                           |
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
    1. "yyyy-yyyy '-DD 't": ' mm ': ' ss ' ([specifikátor formátu ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))
    2. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF

4. "" Celé datum "t" Časová hodina "": minuta "časový posun" "
    1. "yyyy-yyyy '-DD 't": ' mmZ '
    2. "yyyy-yyyy '-DD 't": ' mm (' + '/'-') HH ': ' mm '

5. ' Datum a čas '
    1. "yyyy-yyyy '-DD 't": ' mm ': ' ssZ '
    2. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFFZ"
    3. "yyyy-yyyy '-DD 't": ' mm ': ' ss ' (' + '/'-') HH ': ' mm '
    4. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF (+ '/'-') HH ': mm

Pokud pro sekundy existují desetinné zlomky, musí existovat alespoň jedna číslice. `2019-07-26T00:00:00.` není povolená.
I když je povolený až 16 zlomkových číslic, analyzují se jenom prvních sedm. Vše nad rámec, který je považován za nulu.
Například `2019-07-26T00:00:00.1234567890` bude analyzován jako `2019-07-26T00:00:00.1234567`.
To je udržování kompatibility s implementací <xref:System.DateTime>, což je omezené na toto řešení.

Přestupné sekundy nejsou podporovány.

### <a name="support-for-formatting"></a>Podpora formátování

Pro formátování jsou definovány následující úrovně členitosti:

1. "" Celé datum "t" v částečný čas ""
    1. "yyyy-yyyy '-DD 't": ' mm ': ' ss ' ([specifikátor formátu ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))

        Slouží k formátování <xref:System.DateTime> bez zlomků sekund a bez informací o posunu.

    2. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF

        Slouží k formátování <xref:System.DateTime> s zlomky sekund, ale bez informací o posunu.

2. ' Datum a čas '
    1. "yyyy-yyyy '-DD 't": ' mm ': ' ssZ '

        Slouží k formátování <xref:System.DateTime> bez zlomků sekund, ale s posunem UTC.

    2. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFFZ"

        Slouží k formátování <xref:System.DateTime> se zlomkem sekund a s posunem UTC.

    3. "yyyy-yyyy '-DD 't": ' mm ': ' ss ' (' + '/'-') HH ': ' mm '

        Slouží k formátování <xref:System.DateTime> nebo <xref:System.DateTimeOffset> bez zlomkových sekund, ale s lokálním posunem.

    4. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF (+ '/'-') HH ': mm

        Slouží k formátování <xref:System.DateTime> nebo <xref:System.DateTimeOffset> se zlomky sekund a s místním posunem.

Je-li k dispozici, je zapsána maximálně 7 zlomkových číslic. Tím se zarovnává s implementací <xref:System.DateTime>, která je omezena na toto řešení.
