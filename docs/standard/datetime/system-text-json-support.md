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
ms.openlocfilehash: 83b1b3a7db63154dccc07325b1a1948a2db3953a
ms.sourcegitcommit: 3ac05b2c386c8cc5e73f4c7665f6c0a7ed3da1bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2019
ms.locfileid: "71151828"
---
# <a name="datetime-and-datetimeoffset-support-in-systemtextjson"></a>Podpora DateTime a DateTimeOffset v System.Text.Json

Knihovna System. text. JSON analyzuje a zapisuje <xref:System.DateTime> <xref:System.DateTimeOffset> a hodnotuje hodnoty podle rozšířeného profilu ISO 8601:-2019.
[Převaděče](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0) poskytují vlastní podporu pro serializaci a deserializaci <xref:System.Text.Json.JsonSerializer>pomocí.
Vlastní podporu je také možné implementovat při použití <xref:System.Text.Json.Utf8JsonReader> a <xref:System.Text.Json.Utf8JsonWriter>.

## <a name="support-for-the-iso-8601-12019-format"></a>Podpora formátu ISO 8601-1:2019

<xref:System.DateTime> Typy <xref:System.Text.Json.JsonSerializer>, <xref:System.Text.Json.Utf8JsonReader>, a<xref:System.Text.Json.Utf8JsonWriter> <xref:System.DateTimeOffset> analyzují a zapisují a zapisují text v závislosti na rozšířeném profilu formátu ISO 8601-1:2019, například 2019-07-26T16 <xref:System.Text.Json.JsonElement> : 59:57-05:00.

<xref:System.DateTime>a <xref:System.DateTimeOffset> data lze serializovat pomocí <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-serializing-with-jsonserializer](~/samples/snippets/standard/datetime/json/csharp/serializing-with-jsonserializer/Program.cs)]

Lze je také deserializovat pomocí <xref:System.Text.Json.JsonSerializer>:

[!code-csharp[example-deserializing-with-jsonserializer-valid](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-valid/Program.cs)]

S výchozími možnostmi <xref:System.DateTime> musí <xref:System.DateTimeOffset> být vstupní a textové reprezentace v souladu s rozšířeným profilem ISO 8601-1:2019.
Pokus o rekonstrukci reprezentace, která není v souladu s profilem, by způsobil <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonException>vyvolání:

[!code-csharp[example-deserializing-with-jsonserializer-error](~/samples/snippets/standard/datetime/json/csharp/deserializing-with-jsonserializer-error/Program.cs)]

Poskytuje strukturovaný přístup k obsahu datové části JSON, včetně <xref:System.DateTime> a <xref:System.DateTimeOffset> reprezentace. <xref:System.Text.Json.JsonDocument> Níže uvedený příklad ukazuje, jak se při dané kolekci teplot vypočte průměrná teplota v pondělí:

[!code-csharp[example-computing-with-jsondocument-valid](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-valid/Program.cs)]

Pokud se pokusíte vypočítat průměrnou teplotu pro datovou část s neodpovídajícími <xref:System.DateTime> reprezentacemi, <xref:System.Text.Json.JsonDocument> bude vyvolávat <xref:System.FormatException>:

[!code-csharp[example-computing-with-jsondocument-error](~/samples/snippets/standard/datetime/json/csharp/computing-with-jsondocument-error/Program.cs)]

Zápisy <xref:System.Text.Json.Utf8JsonWriter> <xref:System.DateTime> a<xref:System.DateTimeOffset> data nižší úrovně:

[!code-csharp[example-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/writing-with-utf8jsonwriter/Program.cs)]

<xref:System.Text.Json.Utf8JsonReader>analyzuje <xref:System.DateTimeOffset>adata: <xref:System.DateTime>

[!code-csharp[example-reading-with-utf8jsonreader-valid](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-valid/Program.cs)]

Při pokusu o čtení nekompatibilních formátů <xref:System.Text.Json.Utf8JsonReader> se způsobí, že <xref:System.FormatException>vyvolá výjimku:

[!code-csharp[example-reading-with-utf8jsonreader-error](~/samples/snippets/standard/datetime/json/csharp/reading-with-utf8jsonreader-error/Program.cs)]

## <a name="custom-support-for-xrefsystemdatetime-and-xrefsystemdatetimeoffset"></a>Vlastní podpora pro <xref:System.DateTime> a<xref:System.DateTimeOffset>

### <a name="when-using-xrefsystemtextjsonjsonserializer"></a>Při použití<xref:System.Text.Json.JsonSerializer>

Pokud chcete, aby serializátor prováděl vlastní analýzu nebo formátování, můžete implementovat [vlastní převaděče](https://docs.microsoft.com/dotnet/api/system.text.json.serialization.jsonconverter-1?view=netcore-3.0).
Tady je několik příkladů:

#### <a name="using-datetimeoffsetparse-and-datetimeoffsettostring"></a>Používání `DateTime(Offset).Parse` a`DateTime(Offset).ToString`

Pokud nemůžete určit formáty vstupních <xref:System.DateTime> nebo <xref:System.DateTimeOffset> textových reprezentace `DateTime(Offset).Parse` , můžete použít metodu v logice Read. To vám umožní použít. Rozsáhlá podpora pro analýzu různých <xref:System.DateTime> <xref:System.DateTimeOffset> formátů textu, včetně řetězců jiných než ISO 8601 a formátů ISO 8601, které neodpovídají rozšířenému profilu ISO 8601-1:2019. Tento přístup je výrazně menší než použití nativní implementace serializátoru.

Pro serializaci můžete použít `DateTime(Offset).ToString` metodu ve vaší logice zápisu převaděče. To vám umožní <xref:System.DateTime> zapisovat a <xref:System.DateTimeOffset> hodnoty pomocí libovolného [standardního formátu data a času](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)a [vlastních formátů data a času](https://docs.microsoft.com/dotnet/standard/base-types/custom-date-and-time-format-strings).
To je také podstatně méně prováděno, než použití nativní implementace serializátoru.

[!code-csharp[example-showing-datetime-parse](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example1/Program.cs)]

> [!NOTE]
> Při implementaci <xref:System.Text.Json.Serialization.JsonConverter%601> `T` , <xref:System.DateTime> parametrbude`typeof(DateTime)`vždy. `typeToConvert`
Parametr je vhodný pro zpracování polymorfních případů a při použití obecných typů k získání `typeof(T)` v provedených způsobech.

#### <a name="using-xrefsystembufferstextutf8parser-and-xrefsystembufferstextutf8formatter"></a>Používání <xref:System.Buffers.Text.Utf8Parser> a<xref:System.Buffers.Text.Utf8Formatter>

V logice převaděče můžete použít rychlou metodu analýzy a formátování založenou na kódování UTF-8, <xref:System.DateTime> Pokud <xref:System.DateTimeOffset> jsou vstupní nebo textové reprezentace kompatibilní s jedním z [řetězců formátu data a času standardu](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings)"R", "l", "O" nebo "G", nebo pokud chcete Pište podle jednoho z těchto formátů. To je mnohem rychlejší než použití `DateTime(Offset).Parse` a `DateTime(Offset).ToString`.

Tento příklad ukazuje vlastní převaděč, který serializace a deserializace <xref:System.DateTime> hodnoty podle [standardního formátu "R"](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-rfc1123-r-r-format-specifier):

[!code-csharp[example-showing-utf8-parser-and-formatter](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example2/Program.cs)]

> [!NOTE]
> Standardní formát "R" bude vždy 29 znaků dlouhý.

#### <a name="using-datetimeoffsetparse-as-a-fallback-to-the-serializers-native-parsing"></a>Použití `DateTime(Offset).Parse` jako záložní pro nativní analýzu serializátoru

Pokud obecně očekáváte, že <xref:System.DateTime> váš <xref:System.DateTimeOffset> vstup nebo data budou v souladu s rozšířeným profilem ISO 8601-1:2019, můžete použít logiku nativní analýzy pro serializátor. Můžete také implementovat záložní mechanismus jenom pro případ.
Tento příklad ukazuje, že po selhání analýzy <xref:System.DateTime> textové reprezentace pomocí <xref:System.Text.Json.Utf8JsonReader.TryGetDateTime(System.DateTime@)>převaděče úspěšně analyzuje data pomocí <xref:System.DateTime.Parse(System.String)>.

[!code-csharp[example-showing-datetime-parse-as-fallback](~/samples/snippets/standard/datetime/json/csharp/datetime-converter-examples/example3/Program.cs)]

### <a name="when-writing-with-xrefsystemtextjsonutf8jsonwriter"></a>Při psaní pomocí<xref:System.Text.Json.Utf8JsonWriter>

Chcete- <xref:System.DateTime> li napsat vlastní nebo <xref:System.DateTimeOffset> textovou reprezentaci pomocí <xref:System.Text.Json.Utf8JsonWriter>, můžete vlastní reprezentaci `ReadOnlySpan<Char>`naformátovat na <xref:System.String>, `ReadOnlySpan<Byte>`, nebo <xref:System.Text.Json.JsonEncodedText>, a pak ji předat odpovídajícímu [Utf8JsonWriter. WriteStringValue](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestringvalue?view=netcore-3.0) nebo [Utf8JsonWriter. WriteString](https://docs.microsoft.com/dotnet/api/system.text.json.utf8jsonwriter.writestring?view=netcore-3.0) metoda.

Následující příklad ukazuje <xref:System.DateTime> ,jak<xref:System.DateTime.ToString(System.String,System.IFormatProvider)>lze vytvořit vlastní formát pomocí, pak napsaný pomocí metody:<xref:System.Text.Json.Utf8JsonWriter.WriteStringValue(System.String)>

[!code-csharp[example-custom-writing-with-utf8jsonwriter](~/samples/snippets/standard/datetime/json/csharp/custom-writing-with-utf8jsonwriter/Program.cs)]

### <a name="when-reading-with-xrefsystemtextjsonutf8jsonreader"></a>Při čtení pomocí<xref:System.Text.Json.Utf8JsonReader>

Pokud si chcete přečíst vlastní <xref:System.DateTime> nebo <xref:System.DateTimeOffset> textovou reprezentaci <xref:System.Text.Json.Utf8JsonReader>pomocí, můžete získat <xref:System.String> hodnotu aktuálního tokenu JSON jako using <xref:System.Text.Json.Utf8JsonReader.GetString>a pak analyzovat hodnotu pomocí vlastní logiky.

Následující příklad ukazuje, jak lze načíst <xref:System.DateTimeOffset> vlastní textovou reprezentaci pomocí <xref:System.Text.Json.Utf8JsonReader.GetString>a poté analyzovat pomocí <xref:System.DateTimeOffset.ParseExact(System.String,System.String,System.IFormatProvider)>:

[!code-csharp[example-custom-reading-with-utf8jsonreader](~/samples/snippets/standard/datetime/json/csharp/custom-reading-with-utf8jsonreader/Program.cs)]

## <a name="the-extended-iso-8601-12019-profile-in-systemtextjson"></a>Rozšířený profil ISO 8601-1:2019 v souboru System. text. JSON

### <a name="date-and-time-components"></a>Komponenty data a času

Rozšířený profil ISO 8601-1:2019 implementovaný v <xref:System.Text.Json> nástroji definuje následující komponenty pro reprezentace data a času. Tyto komponenty se používají k definování různých úrovní členitosti při analýze a formátování <xref:System.DateTime> a <xref:System.DateTimeOffset> reprezentace.

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

Pokud pro sekundy existují desetinné zlomky, musí existovat alespoň jedna číslice. `2019-07-26T00:00:00.` není povoleno.
I když je povolený až 16 zlomkových číslic, analyzují se jenom prvních sedm. Vše nad rámec, který je považován za nulu.
Například se bude `2019-07-26T00:00:00.1234567890` analyzovat, jako by `2019-07-26T00:00:00.1234567`to bylo.
Je tak udržování kompatibility s <xref:System.DateTime> implementací, což je omezeno na toto řešení.

Přestupné sekundy nejsou podporovány.

### <a name="support-for-formatting"></a>Podpora formátování

Pro formátování jsou definovány následující úrovně členitosti:

1. "" Celé datum "t" v částečný čas ""
    1. "yyyy-yyyy '-DD 't": ' mm ': ' ss ' ([specifikátor formátu ("s")](https://docs.microsoft.com/dotnet/standard/base-types/standard-date-and-time-format-strings#the-sortable-s-format-specifier))

        Používá se k formátování <xref:System.DateTime> bez zlomků sekund a bez informací o posunu.

    2. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF

        Používá se k formátování <xref:System.DateTime> s zlomky sekund, ale bez informací o posunu.

2. ' Datum a čas '
    1. "yyyy-yyyy '-DD 't": ' mm ': ' ssZ '

        Používá se k formátování <xref:System.DateTime> nebo <xref:System.DateTimeOffset> bez zlomků sekund, ale s posunem UTC.

    2. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFFZ"

        Používá se k formátování <xref:System.DateTime> nebo <xref:System.DateTimeOffset> se zlomky sekund a s posunem UTC.

    3. "yyyy-yyyy '-DD 't": ' mm ': ' ss ' (' + '/'-') HH ': ' mm '

        Používá se k formátování <xref:System.DateTime> nebo <xref:System.DateTimeOffset> bez zlomků sekund, ale s lokálním posunem.

    4. "yyyy-yyyy '-DD 't": ' mm ': ' ss '. ' FFFFFFF (+ '/'-') HH ': mm

        Používá se k formátování <xref:System.DateTime> nebo <xref:System.DateTimeOffset> se zlomky sekund a s místním posunem.

Je-li k dispozici, je zapsána maximálně 7 zlomkových číslic. Tím se zarovnává s <xref:System.DateTime> implementací, která je omezena na toto řešení.
