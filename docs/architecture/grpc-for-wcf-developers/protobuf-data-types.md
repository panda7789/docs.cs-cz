---
title: Protobuf skalárních datových typů – gRPC pro vývojáře WCF
description: Přečtěte si o základních a známých datových typech podporovaných Protobuf a gRPC v .NET Core.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: cae9cc483ffb791a9b53e6a2d9d7c0924d725a67
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846352"
---
# <a name="protobuf-scalar-data-types"></a>Skalární datové typy protobuf

Protobuf podporuje rozsah nativních typů skalárních hodnot. V následující tabulce jsou uvedeny všechny s ekvivalentním C# typem:

| Typ Protobuf | C#textový      | Poznámky |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | první     |
| `int64`       | `long`       | první     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | první     |
| `sint64`      | `long`       | první     |
| `fixed32`     | `uint`       | odst     |
| `fixed64`     | `ulong`      | odst     |
| `sfixed32`    | `int`        | odst     |
| `sfixed64`    | `long`       | odst     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | 3     |
| `bytes`       | `ByteString` | 4     |

## <a name="notes"></a>Poznámky

1. Standardní kódování pro `int32` a `int64` je neefektivní při práci s podepsanými hodnotami. Pokud pole může obsahovat záporná čísla, použijte místo toho `sint32` nebo `sint64`. Oba typy jsou mapovány C# na`int`a`long`typy v uvedeném pořadí.
2. `fixed` pole vždy používají stejný počet bajtů bez ohledu na to, jaká hodnota je. Díky tomuto chování je serializace a deserializace rychlejší pro větší hodnoty.
3. Protobuf řetězce jsou zakódované UTF-8 (nebo 7 bitů ASCII) a Kódovaná délka nesmí být větší než 2<sup>32</sup>.
4. Modul runtime Protobuf poskytuje typ `ByteString`, který se snadno mapuje do`byte[]`C# polí a z nich.

## <a name="other-net-primitive-types"></a>Jiné primitivní typy .NET

### <a name="dates-and-times"></a>Data a časy

Nativní skalární typy neposkytují hodnoty data a času, které C#jsou ekvivalentní<xref:System.DateTimeOffset>,<xref:System.DateTime>a<xref:System.TimeSpan>. Tyto typy lze zadat pomocí některých rozšíření "dobře známých typů" Google, které poskytují generování kódu a podporu modulu runtime pro komplexnější typy polí napříč podporovanými platformami. V následující tabulce jsou uvedeny typy data a času:

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

Vygenerované vlastnosti ve C# třídě nejsou typy data a času .NET. Vlastnosti používají třídy `Timestamp` a `Duration` v oboru názvů `Google.Protobuf.WellKnownTypes`, které poskytují metody pro převod na `DateTimeOffset`, `DateTime`a `TimeSpan`.

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
> Typ `Timestamp` pracuje s časy UTC; hodnoty `DateTimeOffset` vždy mají posun nula a vlastnost `DateTime.Kind` bude vždy `DateTimeKind.Utc`.

### <a name="systemguid"></a>System. GUID

Typ <xref:System.Guid>, který se označuje jako `UUID` na jiných platformách, není přímo podporován Protobuf a neexistuje žádný známý typ. Nejlepším řešením je zpracovávat `Guid` hodnoty jako `string` pole pomocí standardu `8-4-4-4-12` šestnáctkového formátu (například `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), který lze analyzovat pomocí všech jazyků a platforem. Nepoužívejte pole `bytes` pro `Guid` hodnoty, protože problémy s endian můžou způsobit nestabilní chování při komunikaci s jinými platformami, jako je Java.

### <a name="nullable-types"></a>Typy s povolenou hodnotou Null

Generování kódu Protobuf pro C# používá nativní typy, například`int`pro`int32`. To znamená, že hodnoty jsou vždycky zahrnuté a nesmí mít hodnotu null. Pro hodnoty, které vyžadují explicitní hodnotu null, jako je například použití C# `int?` ve vašem kódu, jsou "dobře známé typy" Protobuf zahrnuty obálky, které C# jsou kompilovány na typy s možnou hodnotou null. Pokud je chcete použít, importujte `wrappers.proto` do souboru `.proto`, například takto:

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf bude pro generovanou vlastnost zprávy používat jednoduchý `T?` (například `int?`).

Následující tabulka uvádí úplný seznam typů obálek s ekvivalentním C# typem:

| C#textový   | Obálka dobře známého typu       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

Známé typy `Timestamp` a `Duration` jsou reprezentovány v rozhraní .NET jako třídy, takže není nutné, aby byla povolena verze s možnou hodnotou null, ale při převodu na `DateTimeOffset` nebo `TimeSpan`je důležité vyhledat hodnoty null u vlastností těchto typů.

## <a name="decimals"></a>desetinných míst

Protobuf netivně podporuje typ `decimal` .NET, stačí `double` a `float`. V projektu Protobuf existuje průběžná diskuze o tom, jak přidat standardní `Decimal` typ do známých typů, s podporou platforem pro jazyky a architektury, které ji podporují, ale ještě nic se neimplementovalo.

Je možné vytvořit definici zprávy, která představuje typ `decimal`, který by fungoval pro bezpečnou serializaci mezi klienty rozhraní .NET a servery, ale vývojáři na jiných platformách by museli porozumět použitému formátu a implementovat vlastní zpracování. pro něj.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Vytvoření vlastního typu desetinného čísla pro Protobuf

Velmi jednoduchá implementace může být podobná nestandardnímu typu `Money` používaném některými rozhraními API Google, a to bez pole `currency`.

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

`nanos` pole představuje hodnoty z `0.999_999_999` na `-0.999_999_999`. Například `decimal` hodnota `1.5m` by byla reprezentována jako `{ units = 1, nanos = 500_000_000 }` (to je důvod, proč pole `nanos` v tomto příkladu používá typ `sfixed32`, který kóduje efektivněji než `int32` pro větší hodnoty). Pokud je pole `units` záporné, mělo by být pole `nanos` také záporné.

> [!NOTE]
> Pro kódování `decimal` hodnoty je k dispozici více algoritmů jako bajtů, ale tato zpráva je mnohem jednodušší, než je některý z nich, a hodnoty neovlivní *[endian](https://en.wikipedia.org/wiki/Endianness)* na různých platformách.

Převod mezi tímto typem a typem `decimal` BCL může být implementován C# jako takový.

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
> Vždy, když použijete vlastní typy zpráv nástrojů, je **nutné** je dokumentovat s komentáři v `.proto` tak, aby ostatní vývojáři mohli implementovat převod na a z ekvivalentního typu v jejich vlastním jazyce nebo rozhraní.

>[!div class="step-by-step"]
>[Předchozí](protobuf-messages.md)
>[Další](protobuf-nested-types.md)
