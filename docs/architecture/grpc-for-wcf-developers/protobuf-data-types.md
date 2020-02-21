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
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="36ab9-103">Skalární datové typy protobuf</span><span class="sxs-lookup"><span data-stu-id="36ab9-103">Protobuf scalar data types</span></span>

<span data-ttu-id="36ab9-104">Vyrovnávací paměť protokolu (Protobuf) podporuje rozsah nativních typů skalárních hodnot.</span><span class="sxs-lookup"><span data-stu-id="36ab9-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="36ab9-105">V následující tabulce jsou uvedeny všechny s ekvivalentním C# typem:</span><span class="sxs-lookup"><span data-stu-id="36ab9-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="36ab9-106">Typ Protobuf</span><span class="sxs-lookup"><span data-stu-id="36ab9-106">Protobuf type</span></span> | <span data-ttu-id="36ab9-107">C#textový</span><span class="sxs-lookup"><span data-stu-id="36ab9-107">C# type</span></span>      | <span data-ttu-id="36ab9-108">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="36ab9-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="36ab9-109">1</span><span class="sxs-lookup"><span data-stu-id="36ab9-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="36ab9-110">1</span><span class="sxs-lookup"><span data-stu-id="36ab9-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="36ab9-111">1</span><span class="sxs-lookup"><span data-stu-id="36ab9-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="36ab9-112">1</span><span class="sxs-lookup"><span data-stu-id="36ab9-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="36ab9-113">2</span><span class="sxs-lookup"><span data-stu-id="36ab9-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="36ab9-114">2</span><span class="sxs-lookup"><span data-stu-id="36ab9-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="36ab9-115">2</span><span class="sxs-lookup"><span data-stu-id="36ab9-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="36ab9-116">2</span><span class="sxs-lookup"><span data-stu-id="36ab9-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="36ab9-117">3</span><span class="sxs-lookup"><span data-stu-id="36ab9-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="36ab9-118">4</span><span class="sxs-lookup"><span data-stu-id="36ab9-118">4</span></span>     |

<span data-ttu-id="36ab9-119">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="36ab9-119">Notes:</span></span>

1. <span data-ttu-id="36ab9-120">Standardní kódování pro `int32` a `int64` je neefektivní, když pracujete s podepsanými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="36ab9-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="36ab9-121">Pokud pole může obsahovat záporná čísla, použijte místo toho `sint32` nebo `sint64`.</span><span class="sxs-lookup"><span data-stu-id="36ab9-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="36ab9-122">Tyto typy jsou mapovány C# na `int` a `long` typy v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="36ab9-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="36ab9-123">`fixed` pole vždy používají stejný počet bajtů bez ohledu na to, jaká hodnota je.</span><span class="sxs-lookup"><span data-stu-id="36ab9-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="36ab9-124">Díky tomuto chování je serializace a deserializace rychlejší pro větší hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36ab9-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="36ab9-125">Protobuf řetězce mají kódování UTF-8 (nebo 7 bitů ASCII).</span><span class="sxs-lookup"><span data-stu-id="36ab9-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="36ab9-126">Kódovaná délka nesmí být větší než 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="36ab9-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="36ab9-127">Modul runtime Protobuf poskytuje typ `ByteString`, který se snadno mapuje do `byte[]` C# polí a z nich.</span><span class="sxs-lookup"><span data-stu-id="36ab9-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="36ab9-128">Jiné primitivní typy .NET</span><span class="sxs-lookup"><span data-stu-id="36ab9-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="36ab9-129">Data a časy</span><span class="sxs-lookup"><span data-stu-id="36ab9-129">Dates and times</span></span>

<span data-ttu-id="36ab9-130">Nativní skalární typy neposkytují hodnoty data a času, které C#jsou ekvivalentní <xref:System.DateTimeOffset>, <xref:System.DateTime>a <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="36ab9-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="36ab9-131">Tyto typy můžete zadat pomocí některých rozšíření "známé typy" Google.</span><span class="sxs-lookup"><span data-stu-id="36ab9-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="36ab9-132">Tato rozšíření poskytují podporu generování kódu a běhové prostředí pro komplexní typy polí napříč podporovanými platformami.</span><span class="sxs-lookup"><span data-stu-id="36ab9-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span> 

<span data-ttu-id="36ab9-133">V následující tabulce jsou uvedeny typy data a času:</span><span class="sxs-lookup"><span data-stu-id="36ab9-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="36ab9-134">C#textový</span><span class="sxs-lookup"><span data-stu-id="36ab9-134">C# type</span></span> | <span data-ttu-id="36ab9-135">Protobuf dobře známý typ</span><span class="sxs-lookup"><span data-stu-id="36ab9-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="36ab9-136">Vygenerované vlastnosti ve C# třídě nejsou typy data a času .NET.</span><span class="sxs-lookup"><span data-stu-id="36ab9-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="36ab9-137">Vlastnosti používají třídy `Timestamp` a `Duration` v oboru názvů `Google.Protobuf.WellKnownTypes`.</span><span class="sxs-lookup"><span data-stu-id="36ab9-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="36ab9-138">Tyto třídy poskytují metody pro převod na a z `DateTimeOffset`, `DateTime`a `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="36ab9-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="36ab9-139">Typ `Timestamp` pracuje s časy UTC.</span><span class="sxs-lookup"><span data-stu-id="36ab9-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="36ab9-140">hodnoty `DateTimeOffset` vždy mají posun nula a vlastnost `DateTime.Kind` je vždy `DateTimeKind.Utc`.</span><span class="sxs-lookup"><span data-stu-id="36ab9-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="36ab9-141">System.Guid</span><span class="sxs-lookup"><span data-stu-id="36ab9-141">System.Guid</span></span>

<span data-ttu-id="36ab9-142">Protobuf nepodporují přímo typ <xref:System.Guid>, který se označuje jako `UUID` na jiných platformách.</span><span class="sxs-lookup"><span data-stu-id="36ab9-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="36ab9-143">Pro něj není k dispozici žádný známý typ.</span><span class="sxs-lookup"><span data-stu-id="36ab9-143">There's no well-known type for it.</span></span> 

<span data-ttu-id="36ab9-144">Nejlepším řešením je zpracovávat `Guid` hodnoty jako `string` pole pomocí standardu `8-4-4-4-12` šestnáctkového formátu (například `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span><span class="sxs-lookup"><span data-stu-id="36ab9-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="36ab9-145">Všechny jazyky a platformy mohou tento formát analyzovat.</span><span class="sxs-lookup"><span data-stu-id="36ab9-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="36ab9-146">Nepoužívejte pole `bytes` pro hodnoty `Guid`.</span><span class="sxs-lookup"><span data-stu-id="36ab9-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="36ab9-147">Problémy s *endian* ([definice Wikipedii](https://en.wikipedia.org/wiki/Endianness)) můžou mít za následek nestabilní chování, pokud Protobuf pracuje na jiných platformách, jako je Java.</span><span class="sxs-lookup"><span data-stu-id="36ab9-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="36ab9-148">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="36ab9-148">Nullable types</span></span>

<span data-ttu-id="36ab9-149">Generování kódu Protobuf pro C# používá nativní typy, například `int` pro `int32`.</span><span class="sxs-lookup"><span data-stu-id="36ab9-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="36ab9-150">Takže hodnoty jsou vždycky zahrnuté a nesmí mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="36ab9-150">So the values are always included and can't be null.</span></span> 

<span data-ttu-id="36ab9-151">Pro hodnoty, které vyžadují explicitní hodnotu null, jako je například použití C# `int?` ve vašem kódu, jsou "dobře známé typy" Protobuf zahrnuty obálky, které C# jsou kompilovány na typy s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="36ab9-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="36ab9-152">Pokud je chcete použít, importujte `wrappers.proto` do souboru `.proto`, například takto:</span><span class="sxs-lookup"><span data-stu-id="36ab9-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="36ab9-153">Protobuf bude pro generovanou vlastnost zprávy používat jednoduchý `T?` (například `int?`).</span><span class="sxs-lookup"><span data-stu-id="36ab9-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="36ab9-154">Následující tabulka uvádí úplný seznam typů obálek s ekvivalentním C# typem:</span><span class="sxs-lookup"><span data-stu-id="36ab9-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="36ab9-155">C#textový</span><span class="sxs-lookup"><span data-stu-id="36ab9-155">C# type</span></span>   | <span data-ttu-id="36ab9-156">Obálka dobře známého typu</span><span class="sxs-lookup"><span data-stu-id="36ab9-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="36ab9-157">Známé typy `Timestamp` a `Duration` jsou reprezentovány v .NET jako třídy, takže není nutné mít k dispozici verzi s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="36ab9-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version.</span></span> <span data-ttu-id="36ab9-158">Při převodu na `DateTimeOffset` nebo `TimeSpan`je ale důležité, abyste u vlastností těchto typů kontrolovali hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="36ab9-158">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="36ab9-159">Desetinných míst</span><span class="sxs-lookup"><span data-stu-id="36ab9-159">Decimals</span></span>

<span data-ttu-id="36ab9-160">Protobuf netivně podporuje typ `decimal` .NET, stačí `double` a `float`.</span><span class="sxs-lookup"><span data-stu-id="36ab9-160">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="36ab9-161">V projektu Protobuf je průběžná diskuze o tom, jak přidat standardní `Decimal` typ do známých typů, s podporou platforem pro jazyky a architektury, které ji podporují.</span><span class="sxs-lookup"><span data-stu-id="36ab9-161">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="36ab9-162">Ještě nic není implementované.</span><span class="sxs-lookup"><span data-stu-id="36ab9-162">Nothing has been implemented yet.</span></span>

<span data-ttu-id="36ab9-163">Je možné vytvořit definici zprávy, která bude představovat `decimal` typ, který bude fungovat pro bezpečnou serializaci mezi klienty a servery rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="36ab9-163">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="36ab9-164">Ale vývojáři na jiných platformách by museli porozumět použitému formátu a implementovat jeho vlastní zpracování.</span><span class="sxs-lookup"><span data-stu-id="36ab9-164">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="36ab9-165">Vytvoření vlastního typu desetinného čísla pro Protobuf</span><span class="sxs-lookup"><span data-stu-id="36ab9-165">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="36ab9-166">Jednoduchá implementace může být podobná nestandardnímu typu `Money`, který používají některá rozhraní API Google, bez pole `currency`.</span><span class="sxs-lookup"><span data-stu-id="36ab9-166">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

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

<span data-ttu-id="36ab9-167">`nanos` pole představuje hodnoty z `0.999_999_999` na `-0.999_999_999`.</span><span class="sxs-lookup"><span data-stu-id="36ab9-167">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="36ab9-168">Například hodnota `decimal` `1.5m` by byla reprezentovaná jako `{ units = 1, nanos = 500_000_000 }`.</span><span class="sxs-lookup"><span data-stu-id="36ab9-168">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="36ab9-169">To je důvod, proč pole `nanos` v tomto příkladu používá typ `sfixed32`, který kóduje efektivněji než `int32` pro větší hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36ab9-169">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="36ab9-170">Pokud je pole `units` záporné, mělo by být pole `nanos` také záporné.</span><span class="sxs-lookup"><span data-stu-id="36ab9-170">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="36ab9-171">Pro kódování `decimal` hodnoty je k dispozici více algoritmů jako bajtů, ale tato zpráva je snazší pochopit, než je některý z nich.</span><span class="sxs-lookup"><span data-stu-id="36ab9-171">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="36ab9-172">Hodnoty nejsou ovlivněny endian na různých platformách.</span><span class="sxs-lookup"><span data-stu-id="36ab9-172">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="36ab9-173">Konverze mezi tímto typem a typem BCL `decimal` může být implementována C# takto:</span><span class="sxs-lookup"><span data-stu-id="36ab9-173">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

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
> <span data-ttu-id="36ab9-174">Kdykoli použijete vlastní typy zpráv, *musíte* je dokumentovat s komentáři v `.proto`.</span><span class="sxs-lookup"><span data-stu-id="36ab9-174">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="36ab9-175">Ostatní vývojáři pak mohou implementovat převod do a z ekvivalentního typu ve svém vlastním jazyce nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="36ab9-175">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="36ab9-176">[Předchozí](protobuf-messages.md)
>[Další](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="36ab9-176">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
