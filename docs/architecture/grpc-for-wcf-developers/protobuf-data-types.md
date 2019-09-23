---
title: Protobuf skalárních datových typů – gRPC pro vývojáře WCF
description: Přečtěte si o základních a známých datových typech podporovaných Protobuf a gRPC v .NET Core.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 8c8db795e927a44e9f75ec828336630ec9978eb6
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184265"
---
# <a name="protobuf-scalar-data-types"></a>Protobuf skalárních datových typů

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Protobuf podporuje rozsah nativních typů skalárních hodnot. V následující tabulce jsou uvedeny všechny s ekvivalentním C# typem:

| Typ Protobuf | C#textový      | Poznámky |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | 1     |
| `int64`       | `long`       | 1     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | 1     |
| `sint64`      | `long`       | 1     |
| `fixed32`     | `uint`       | 2     |
| `fixed64`     | `ulong`      | 2     |
| `sfixed32`    | `int`        | 2     |
| `sfixed64`    | `long`       | 2     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | 3     |
| `bytes`       | `ByteString` | 4     |

## <a name="notes"></a>Poznámky

1. Standardní kódování pro `int32` a `int64` je neefektivní při práci s podepsanými hodnotami. Pokud pole může obsahovat záporná čísla, použijte `sint32` nebo `sint64` místo toho. Oba typy jsou C# `int` mapovány na `long` typy a v uvedeném pořadí.
2. `fixed` Pole vždycky používají stejný počet bajtů bez ohledu na to, jaká hodnota je. Díky tomuto chování je serializace a deserializace rychlejší pro větší hodnoty.
3. Protobuf řetězce jsou zakódované UTF-8 (nebo 7 bitů ASCII) a Kódovaná délka nesmí být větší než 2<sup>32</sup>.
4. Modul runtime Protobuf poskytuje `ByteString` typ, který se snadno mapuje na pole a z C# `byte[]` nich.

## <a name="other-net-primitive-types"></a>Jiné primitivní typy .NET

### <a name="dates-and-times"></a>Data a časy

Nativní skalární typy neposkytují hodnoty data a času C#, ekvivalentní hodnotě <xref:System.DateTimeOffset>, <xref:System.DateTime>a <xref:System.TimeSpan>. Tyto typy lze zadat pomocí některých rozšíření "dobře známých typů" Google, které poskytují generování kódu a podporu modulu runtime pro komplexnější typy polí napříč podporovanými platformami. V následující tabulce jsou uvedeny typy data a času:

| C#textový | Protobuf dobře známý typ |
| ------- | ------------------------ |
| `DateTimeOffset` | `google.protobuf.Timestamp` |
| `DateTime` | `google.protobuf.Timestamp` |
| `TimeSpan` | `google.protobuf.Duration` |

```protobuf  
syntax = "proto3"

import "google/protobuf/duration.proto";  
import "google/protobuf/timestamp.proto";

message Meeting {

    string subject = 1;
    google.protobuf.Timestamp time = 2;
    google.protobuf.Duration duration = 3;

}  
```

Vygenerované vlastnosti ve C# třídě nejsou typy data a času .NET. Vlastnosti používají `Timestamp` třídy a `DateTime` `DateTimeOffset` `TimeSpan`v oboru názvů, které poskytují metody pro převod na a z, a. `Google.Protobuf.WellKnownTypes` `Duration`

```csharp
// Create Timestamp and Duration from .NET DateTimeOffset and TimeSpan
var meeting = new Meeting
{
    Time = Timestamp.FromDateTimeOffset(meetingTime), // also FromDateTime()
    Duration = Duration.FromTimeSpan(meetingLength)
};

// Convert Timestamp and Duration to .NET DateTimeOffset and TimeSpan
DateTimeOffset time = meeting.Time.ToDateTimeOffset();
TimeSpan? duration = meeting.Duration?.ToTimeSpan();
```

> [!NOTE]
> `Timestamp` Typ pracuje s časy UTC; hodnoty vždy mají posun nula `DateTime.Kind` a vlastnost bude vždy `DateTimeKind.Utc`. `DateTimeOffset`

### <a name="systemguid"></a>System.Guid

Typ, známý jako `UUID` na jiných platformách, není přímo podporován Protobuf a neexistuje žádný známý typ. <xref:System.Guid> Nejlepším `Guid` řešením je zpracovávat hodnoty jako `string` pole pomocí standardního `8-4-4-4-12` šestnáctkového formátu (například `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), který lze analyzovat pomocí všech jazyků a platforem. Nepoužívejte `bytes` pro `Guid` hodnoty pole, protože problémy s endian můžou způsobit nestabilní chování při komunikaci s jinými platformami, jako je Java.

### <a name="nullable-types"></a>Typy s povolenou hodnotou Null

Generování kódu Protobuf pro C# používá nativní typy, `int` jako například pro. `int32` To znamená, že hodnoty jsou vždycky zahrnuté a nesmí mít hodnotu null. Pro hodnoty, které vyžadují explicitní null, jako je `int?` například použití C# ve vašem kódu, jsou "dobře známé typy" Protobuf zahrnuty obálky, které jsou C# kompilovány na typy s možnou hodnotou null. Pokud je chcete použít, `wrappers.proto` importujte je `.proto` do souboru následujícím způsobem:

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf bude pro generovanou vlastnost `T?` zprávy používat jednoduché ( `int?`například).

Následující tabulka uvádí úplný seznam typů obálek s ekvivalentním C# typem:

| C#textový   | Obálka dobře známého typu       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

Známé typy `Timestamp` a `Duration` jsou reprezentovány v rozhraní .NET jako třídy, takže není nutné mít k dispozici verzi s možnou hodnotou null, je však důležité při převodu na nebo `TimeSpan`provést `DateTimeOffset` kontrolu hodnot null u vlastností těchto typů.

## <a name="decimals"></a>Desetinných míst

Protobuf netivně podporuje typ .NET `decimal` , a to jenom `double` a. `float` V projektu Protobuf je průběžná diskuze o tom, jak přidat standardní `Decimal` typ k dobře známým typům, s podporou platforem pro jazyky a architektury, které ho podporují, ale ještě nic se neimplementovalo.

Je možné vytvořit definici zprávy, která bude představovat `decimal` typ, který by fungoval pro bezpečnou serializaci mezi klienty a servery rozhraní .NET, ale vývojáři na jiných platformách by museli porozumět použitému formátu a implementovat své vlastní. zpracování.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Vytvoření vlastního typu desetinného čísla pro Protobuf

Velmi jednoduchá implementace může být podobná nestandardnímu `Money` typu, který používají některá rozhraní API Google, `currency` bez pole.

```protobuf
package CustomTypes;

// Example: 12345.6789 -> { units = 12345, nanos = 678900000 }
message Decimal {

    // Whole units part of the amount
    int64 units = 1;

    // Nano units of the amount (10^-9)
    // Must be same sign as units
    sfixed32 nanos = 2;
}
```

Pole představuje hodnoty z `0.999_999_999` do `-0.999_999_999`. `nanos` `decimal` `sfixed32` Hodnota `int32` `nanos` by například byla reprezentovaná jako `{ units = 1, nanos = 500_000_000 }` (to je důvod, proč pole v tomto příkladu používá typ, který kóduje efektivněji než pro větší hodnoty). `1.5m` Pokud je `nanos` pole záporné, mělo by být pole také záporné. `units`

> [!NOTE]
> K dispozici je několik dalších algoritmů pro kódování `decimal` hodnot jako bajtů, ale tato zpráva je mnohem jednodušší, než je některý z nich, a hodnoty neovlivní *[endian](https://en.wikipedia.org/wiki/Endianness)* na různých platformách.

Konverze mezi tímto typem a typem BCL `decimal` by mohla být implementována C# jako.

```csharp
namespace CustomTypes
{
    public partial class GrpcDecimal
    {
        private const decimal NanoFactor = 1_000_000_000;
        public GrpcDecimal(long units, int nanos)
        {
            Units = units;
            Nanos = nanos;
        }

        public long Units { get; }
        public int Nanos { get; }

        public static implicit operator decimal(CustomTypes.Decimal grpcDecimal)
        {
            return grpcDecimal.Units + grpcDecimal.Nanos / NanoFactor;
        }

        public static implicit operator CustomTypes.Decimal(decimal value)
        {
            var units = decimal.ToInt64(value);
            var nanos = decimal.ToInt32((value - units) * NanoFactor);
            return new CustomTypes.Decimal(units, nanos);
        }
    }
}
```

> [!IMPORTANT]
> Vždy, když použijete vlastní typy zpráv nástroje, **musíte** je dokumentovat s komentáři v `.proto` , aby ostatní vývojáři mohli implementovat převod na a z ekvivalentního typu v jejich vlastním jazyce nebo rozhraní.

>[!div class="step-by-step"]
>[Předchozí](protobuf-messages.md)
>[Další](protobuf-nested-types.md)
