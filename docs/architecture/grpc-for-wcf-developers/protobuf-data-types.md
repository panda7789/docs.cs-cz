---
title: Scalární datové typy Protobuf - gRPC pro vývojáře WCF
description: Seznamte se se základními a dobře známými datovými typy, které Protobuf a gRPC podporují v .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: a40f51fa32ddb97ba417ec01f31e1f0187f0d544
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148124"
---
# <a name="protobuf-scalar-data-types"></a>Skalární datové typy protobuf

Buffer protokolu (Protobuf) podporuje řadu nativních typů skalárních hodnot. V následující tabulce jsou uvedeny všechny s jejich ekvivalentní c# typu:

| Typ Protobuf | C# typ      | Poznámky |
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

1. Standardní kódování pro `int32` `int64` a je neefektivní při práci s podepsanými hodnotami. Pokud je pravděpodobné, že pole `sint32` bude `sint64` obsahovat záporná čísla, použijte nebo místo toho. Tyto typy mapovat `int` c# a `long` typy, v uvedeném pořadí.
2. Pole `fixed` vždy používají stejný počet bajtů bez ohledu na to, jaká je hodnota. Toto chování umožňuje serializace a deserializace rychlejší pro větší hodnoty.
3. Řetězce Protobuf jsou kódovány utf-8 (nebo 7bitový ASCII). Zakódovaná délka nesmí být větší než 2<sup>32</sup>.
4. Protobuf runtime poskytuje `ByteString` typ, který mapuje `byte[]` snadno a z c# pole.

## <a name="other-net-primitive-types"></a>Jiné primitivní typy .NET

### <a name="dates-and-times"></a>Data a časy

Nativní skalární typy neposkytují hodnoty data a času, ekvivalentní <xref:System.DateTimeOffset> <xref:System.DateTime>C#' s , a <xref:System.TimeSpan>. Tyto typy můžete zadat pomocí některých rozšíření Google "Známé typy". Tato rozšíření poskytují generování kódu a podporu modulu runtime pro složité typy polí napříč podporovanými platformami.

V následující tabulce jsou uvedeny typy dat a času:

| C# typ | Protobuf známý typ |
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

Generované vlastnosti ve třídě C# nejsou typy data a času .NET. Vlastnosti používají `Timestamp` `Duration` třídy `Google.Protobuf.WellKnownTypes` a v oboru názvů. Tyto třídy poskytují metody převodu `DateTime`do `TimeSpan`a z `DateTimeOffset`, a .

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
> Typ `Timestamp` pracuje s časy UTC. `DateTimeOffset`hodnoty mají vždy posun nula `DateTime.Kind` a `DateTimeKind.Utc`vlastnost je vždy .

### <a name="systemguid"></a>System.Guid

Protobuf přímo nepodporuje <xref:System.Guid> typ, známý `UUID` jako na jiných platformách. Není pro to žádný známý typ.

Nejlepším přístupem je `Guid` zpracování hodnot `string` jako pole pomocí `8-4-4-4-12` standardního šestnáctkového formátu `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`(například). Všechny jazyky a platformy můžete analyzovat tento formát.

Nepoužívejte `bytes` pole pro `Guid` hodnoty. Problémy s *endianness* [(Definice Wikipedie)](https://en.wikipedia.org/wiki/Endianness)může mít za následek nevyzpytatelné chování, když Protobuf je interakci s jinými platformami, jako je Java.

### <a name="nullable-types"></a>Typy s povolenou hodnotou Null

Generování kódu Protobuf pro C# používá nativní typy, například `int` pro `int32`. Takže hodnoty jsou vždy zahrnuty a nemůže být null.

Pro hodnoty, které vyžadují explicitní `int?` null, například pomocí v kódu Jazyka C#, Protobuf je "Dobře známé typy" zahrnout obálky, které jsou kompilovány na null C# typy. Chcete-li je `wrappers.proto` použít, importujte `.proto` do souboru takto:

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

Protobuf použije pro `T?` vygenerovanou vlastnost zprávy jednoduché `int?`(například).

V následující tabulce je uveden úplný seznam typů obálky s jejich ekvivalentním typem C#:

| C# typ   | Obálka známého typu       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

Známé typy `Timestamp` a `Duration` jsou reprezentovány v .NET jako třídy, takže není potřeba verze s možnou hodnotou null. Ale je důležité zkontrolovat null na vlastnosti těchto typů při `DateTimeOffset` převodu do nebo `TimeSpan`.

## <a name="decimals"></a>Desetinná místa

Protobuf nepodporuje nativně typ `decimal` .NET, `double` `float`jen a . V projektu Protobuf probíhá diskuse o možnosti přidání `Decimal` standardního typu ke známým typům s podporou platformy pro jazyky a architektury, které jej podporují. Zatím nebylo nic implementováno.

Je možné vytvořit definici zprávy reprezentovat `decimal` typ, který by pracoval pro bezpečné serializace mezi klienty .NET a servery. Ale vývojáři na jiných platformách by museli pochopit formát, který se používá, a implementovat pro něj vlastní zpracování.

### <a name="creating-a-custom-decimal-type-for-protobuf"></a>Vytvoření vlastního desetinného typu pro Protobuf

Jednoduchá implementace může být podobná `Money` nestandardnímu typu, který používají `currency` některá api Google bez pole.

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

Pole `nanos` představuje hodnoty `0.999_999_999` `-0.999_999_999`od do . Například `decimal` hodnota `1.5m` by být `{ units = 1, nanos = 500_000_000 }`reprezentován jako . To je `nanos` důvod, proč pole `sfixed32` v tomto příkladu používá `int32` typ, který kóduje efektivněji než pro větší hodnoty. Pokud `units` je pole záporné, `nanos` mělo by být záporné.

> [!NOTE]
> Existuje několik dalších algoritmů `decimal` pro kódování hodnot jako bajtové řetězce, ale tato zpráva je srozumitelnější než kterýkoli z nich. Hodnoty nejsou ovlivněny endianness na různých platformách.

Převod mezi tímto typem a typem BCL `decimal` může být implementován v c# takto:

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
> Kdykoli používáte vlastní typy zpráv, jako je `.proto`tento, je *nutné* je dokumentovat s komentáři v . Ostatní vývojáři pak můžete implementovat převod do a z ekvivalentního typu ve svém vlastním jazyce nebo rámci.

>[!div class="step-by-step"]
>[Předchozí](protobuf-messages.md)
>[další](protobuf-nested-types.md)
