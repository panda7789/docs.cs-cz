---
title: Protobuf skalárních datových typů – gRPC pro vývojáře WCF
description: Seznamte se se základními a známými datovými typy, které Protobuf a gRPC podporují v .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: f5215550a6a2d54dfe2e859c574a34f641fdb68d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543154"
---
# <a name="protobuf-scalar-data-types"></a>Skalární datové typy protobuf

Vyrovnávací paměť protokolu (Protobuf) podporuje rozsah nativních typů skalárních hodnot. V následující tabulce jsou uvedeny všechny s ekvivalentním C# typem:

| Typ Protobuf | C#textový      | Poznámky: |
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

Poznámky:

1. Standardní kódování pro `int32` a `int64` je neefektivní, když pracujete s podepsanými hodnotami. Pokud pole může obsahovat záporná čísla, použijte místo toho `sint32` nebo `sint64`. Tyto typy jsou mapovány C# na `int` a `long` typy v uvedeném pořadí.
2. `fixed` pole vždy používají stejný počet bajtů bez ohledu na to, jaká hodnota je. Díky tomuto chování je serializace a deserializace rychlejší pro větší hodnoty.
3. Protobuf řetězce mají kódování UTF-8 (nebo 7 bitů ASCII). Kódovaná délka nesmí být větší než 2<sup>32</sup>.
4. Modul runtime Protobuf poskytuje typ `ByteString`, který se snadno mapuje do `byte[]` C# polí a z nich.

## <a name="other-net-primitive-types"></a>Jiné primitivní typy .NET

### <a name="dates-and-times"></a>Data a časy

Nativní skalární typy neposkytují hodnoty data a času, které C#jsou ekvivalentní <xref:System.DateTimeOffset>, <xref:System.DateTime>a <xref:System.TimeSpan>. Tyto typy můžete zadat pomocí některých rozšíření "známé typy" Google. Tato rozšíření poskytují podporu generování kódu a běhové prostředí pro komplexní typy polí napříč podporovanými platformami. 

V následující tabulce jsou uvedeny typy data a času:

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

Vygenerované vlastnosti ve C# třídě nejsou typy data a času .NET. Vlastnosti používají třídy `Timestamp` a `Duration` v oboru názvů `Google.Protobuf.WellKnownTypes`. Tyto třídy poskytují metody pro převod na a z `DateTimeOffset`, `DateTime`a `TimeSpan`.

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
> Typ `Timestamp` pracuje s časy UTC. hodnoty `DateTimeOffset` vždy mají posun nula a vlastnost `DateTime.Kind` je vždy `DateTimeKind.Utc`.

### <a name="systemguid"></a>System.Guid

Protobuf nepodporují přímo typ <xref:System.Guid>, který se označuje jako `UUID` na jiných platformách. Pro něj není k dispozici žádný známý typ. 

Nejlepším řešením je zpracovávat `Guid` hodnoty jako `string` pole pomocí standardu `8-4-4-4-12` šestnáctkového formátu (například `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`). Všechny jazyky a platformy mohou tento formát analyzovat.

Nepoužívejte pole `bytes` pro hodnoty `Guid`. Problémy s *endian* ([definice Wikipedii](https://en.wikipedia.org/wiki/Endianness)) můžou mít za následek nestabilní chování, pokud Protobuf pracuje na jiných platformách, jako je Java.

### <a name="nullable-types"></a>Typy s povolenou hodnotou Null

Generování kódu Protobuf pro C# používá nativní typy, například `int` pro `int32`. Takže hodnoty jsou vždycky zahrnuté a nesmí mít hodnotu null. 

Pro hodnoty, které vyžadují explicitní hodnotu null, jako je například použití C# `int?` ve vašem kódu, jsou "dobře známé typy" Protobuf zahrnuty obálky, které C# jsou kompilovány na typy s možnou hodnotou null. Pokud je chcete použít, importujte `wrappers.proto` do souboru `.proto`, například takto:

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

Známé typy `Timestamp` a `Duration` jsou reprezentovány v .NET jako třídy, takže není nutné mít k dispozici verzi s možnou hodnotou null. Při převodu na `DateTimeOffset` nebo `TimeSpan`je ale důležité, abyste u vlastností těchto typů kontrolovali hodnotu null.

## <a name="decimals"></a>Desetinných míst

Protobuf netivně podporuje typ `decimal` .NET, stačí `double` a `float`. V projektu Protobuf je průběžná diskuze o tom, jak přidat standardní `Decimal` typ do známých typů, s podporou platforem pro jazyky a architektury, které ji podporují. Ještě nic není implementované.

Je možné vytvořit definici zprávy, která bude představovat `decimal` typ, který bude fungovat pro bezpečnou serializaci mezi klienty a servery rozhraní .NET. Ale vývojáři na jiných platformách by museli porozumět použitému formátu a implementovat jeho vlastní zpracování.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Vytvoření vlastního typu desetinného čísla pro Protobuf

Jednoduchá implementace může být podobná nestandardnímu typu `Money`, který používají některá rozhraní API Google, bez pole `currency`.

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

`nanos` pole představuje hodnoty z `0.999_999_999` na `-0.999_999_999`. Například hodnota `decimal` `1.5m` by byla reprezentovaná jako `{ units = 1, nanos = 500_000_000 }`. To je důvod, proč pole `nanos` v tomto příkladu používá typ `sfixed32`, který kóduje efektivněji než `int32` pro větší hodnoty. Pokud je pole `units` záporné, mělo by být pole `nanos` také záporné.

> [!NOTE]
> Pro kódování `decimal` hodnoty je k dispozici více algoritmů jako bajtů, ale tato zpráva je snazší pochopit, než je některý z nich. Hodnoty nejsou ovlivněny endian na různých platformách.

Konverze mezi tímto typem a typem BCL `decimal` může být implementována C# takto:

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
> Kdykoli použijete vlastní typy zpráv, *musíte* je dokumentovat s komentáři v `.proto`. Ostatní vývojáři pak mohou implementovat převod do a z ekvivalentního typu ve svém vlastním jazyce nebo rozhraní.

>[!div class="step-by-step"]
>[Předchozí](protobuf-messages.md)
>[Další](protobuf-nested-types.md)
