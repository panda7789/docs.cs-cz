---
title: Scalární datové typy Protobuf - gRPC pro vývojáře WCF
description: Seznamte se se základními a dobře známými datovými typy, které Protobuf a gRPC podporují v .NET Core.
ms.date: 09/09/2019
ms.openlocfilehash: ea3b53426ecf6f50f3bae22a537e227b07248508
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249432"
---
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="a5ac9-103">Skalární datové typy protobuf</span><span class="sxs-lookup"><span data-stu-id="a5ac9-103">Protobuf scalar data types</span></span>

<span data-ttu-id="a5ac9-104">Buffer protokolu (Protobuf) podporuje řadu nativních typů skalárních hodnot.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-104">Protocol Buffer (Protobuf) supports a range of native scalar value types.</span></span> <span data-ttu-id="a5ac9-105">V následující tabulce jsou uvedeny všechny s jejich ekvivalentní c# typu:</span><span class="sxs-lookup"><span data-stu-id="a5ac9-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="a5ac9-106">Typ Protobuf</span><span class="sxs-lookup"><span data-stu-id="a5ac9-106">Protobuf type</span></span> | <span data-ttu-id="a5ac9-107">C# typ</span><span class="sxs-lookup"><span data-stu-id="a5ac9-107">C# type</span></span>      | <span data-ttu-id="a5ac9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5ac9-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="a5ac9-109">1</span><span class="sxs-lookup"><span data-stu-id="a5ac9-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="a5ac9-110">1</span><span class="sxs-lookup"><span data-stu-id="a5ac9-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="a5ac9-111">1</span><span class="sxs-lookup"><span data-stu-id="a5ac9-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="a5ac9-112">1</span><span class="sxs-lookup"><span data-stu-id="a5ac9-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="a5ac9-113">2</span><span class="sxs-lookup"><span data-stu-id="a5ac9-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="a5ac9-114">2</span><span class="sxs-lookup"><span data-stu-id="a5ac9-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="a5ac9-115">2</span><span class="sxs-lookup"><span data-stu-id="a5ac9-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="a5ac9-116">2</span><span class="sxs-lookup"><span data-stu-id="a5ac9-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="a5ac9-117">3</span><span class="sxs-lookup"><span data-stu-id="a5ac9-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="a5ac9-118">4</span><span class="sxs-lookup"><span data-stu-id="a5ac9-118">4</span></span>     |

<span data-ttu-id="a5ac9-119">Poznámky:</span><span class="sxs-lookup"><span data-stu-id="a5ac9-119">Notes:</span></span>

1. <span data-ttu-id="a5ac9-120">Standardní kódování pro `int32` `int64` a je neefektivní při práci s podepsanými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-120">The standard encoding for `int32` and `int64` is inefficient when you're working with signed values.</span></span> <span data-ttu-id="a5ac9-121">Pokud je pravděpodobné, že pole `sint32` bude `sint64` obsahovat záporná čísla, použijte nebo místo toho.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="a5ac9-122">Tyto typy mapovat `int` c# a `long` typy, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-122">These types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="a5ac9-123">Pole `fixed` vždy používají stejný počet bajtů bez ohledu na to, jaká je hodnota.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="a5ac9-124">Toto chování umožňuje serializace a deserializace rychlejší pro větší hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="a5ac9-125">Řetězce Protobuf jsou kódovány utf-8 (nebo 7bitový ASCII).</span><span class="sxs-lookup"><span data-stu-id="a5ac9-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded.</span></span> <span data-ttu-id="a5ac9-126">Zakódovaná délka nesmí být větší než 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-126">The encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="a5ac9-127">Protobuf runtime poskytuje `ByteString` typ, který mapuje `byte[]` snadno a z c# pole.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-127">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="a5ac9-128">Jiné primitivní typy .NET</span><span class="sxs-lookup"><span data-stu-id="a5ac9-128">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="a5ac9-129">Data a časy</span><span class="sxs-lookup"><span data-stu-id="a5ac9-129">Dates and times</span></span>

<span data-ttu-id="a5ac9-130">Nativní skalární typy neposkytují hodnoty data a času, ekvivalentní <xref:System.DateTimeOffset> <xref:System.DateTime>C#' s , a <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-130">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="a5ac9-131">Tyto typy můžete zadat pomocí některých rozšíření Google "Známé typy".</span><span class="sxs-lookup"><span data-stu-id="a5ac9-131">You can specify these types by using some of Google's "Well Known Types" extensions.</span></span> <span data-ttu-id="a5ac9-132">Tato rozšíření poskytují generování kódu a podporu modulu runtime pro složité typy polí napříč podporovanými platformami.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-132">These extensions provide code generation and runtime support for complex field types across the supported platforms.</span></span>

<span data-ttu-id="a5ac9-133">V následující tabulce jsou uvedeny typy dat a času:</span><span class="sxs-lookup"><span data-stu-id="a5ac9-133">The following table shows the date and time types:</span></span>

| <span data-ttu-id="a5ac9-134">C# typ</span><span class="sxs-lookup"><span data-stu-id="a5ac9-134">C# type</span></span> | <span data-ttu-id="a5ac9-135">Protobuf známý typ</span><span class="sxs-lookup"><span data-stu-id="a5ac9-135">Protobuf well-known type</span></span> |
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

<span data-ttu-id="a5ac9-136">Generované vlastnosti ve třídě C# nejsou typy data a času .NET.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-136">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="a5ac9-137">Vlastnosti používají `Timestamp` `Duration` třídy `Google.Protobuf.WellKnownTypes` a v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-137">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace.</span></span> <span data-ttu-id="a5ac9-138">Tyto třídy poskytují metody převodu `DateTime`do `TimeSpan`a z `DateTimeOffset`, a .</span><span class="sxs-lookup"><span data-stu-id="a5ac9-138">These classes provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="a5ac9-139">Typ `Timestamp` pracuje s časy UTC.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-139">The `Timestamp` type works with UTC times.</span></span> <span data-ttu-id="a5ac9-140">`DateTimeOffset`hodnoty mají vždy posun nula `DateTime.Kind` a `DateTimeKind.Utc`vlastnost je vždy .</span><span class="sxs-lookup"><span data-stu-id="a5ac9-140">`DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property is always `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="a5ac9-141">System.Guid</span><span class="sxs-lookup"><span data-stu-id="a5ac9-141">System.Guid</span></span>

<span data-ttu-id="a5ac9-142">Protobuf přímo nepodporuje <xref:System.Guid> typ, známý `UUID` jako na jiných platformách.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-142">Protobuf doesn't directly support the <xref:System.Guid> type, known as `UUID` on other platforms.</span></span> <span data-ttu-id="a5ac9-143">Není pro to žádný známý typ.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-143">There's no well-known type for it.</span></span>

<span data-ttu-id="a5ac9-144">Nejlepším přístupem je `Guid` zpracování hodnot `string` jako pole pomocí `8-4-4-4-12` standardního šestnáctkového formátu `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`(například).</span><span class="sxs-lookup"><span data-stu-id="a5ac9-144">The best approach is to handle `Guid` values as a `string` field, by using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`).</span></span> <span data-ttu-id="a5ac9-145">Všechny jazyky a platformy můžete analyzovat tento formát.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-145">All languages and platforms can parse that format.</span></span>

<span data-ttu-id="a5ac9-146">Nepoužívejte `bytes` pole pro `Guid` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-146">Don't use a `bytes` field for `Guid` values.</span></span> <span data-ttu-id="a5ac9-147">Problémy s *endianness* [(Definice Wikipedie)](https://en.wikipedia.org/wiki/Endianness)může mít za následek nevyzpytatelné chování, když Protobuf je interakci s jinými platformami, jako je Java.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-147">Problems with *endianness* ([Wikipedia definition](https://en.wikipedia.org/wiki/Endianness)) can result in erratic behavior when Protobuf is interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="a5ac9-148">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="a5ac9-148">Nullable types</span></span>

<span data-ttu-id="a5ac9-149">Generování kódu Protobuf pro C# používá nativní typy, například `int` pro `int32`.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-149">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="a5ac9-150">Takže hodnoty jsou vždy zahrnuty a nemůže být null.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-150">So the values are always included and can't be null.</span></span>

<span data-ttu-id="a5ac9-151">Pro hodnoty, které vyžadují explicitní `int?` null, například pomocí v kódu Jazyka C#, Protobuf je "Dobře známé typy" zahrnout obálky, které jsou kompilovány na null C# typy.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-151">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="a5ac9-152">Chcete-li je `wrappers.proto` použít, importujte `.proto` do souboru takto:</span><span class="sxs-lookup"><span data-stu-id="a5ac9-152">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="a5ac9-153">Protobuf použije pro `T?` vygenerovanou vlastnost zprávy jednoduché `int?`(například).</span><span class="sxs-lookup"><span data-stu-id="a5ac9-153">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="a5ac9-154">V následující tabulce je uveden úplný seznam typů obálky s jejich ekvivalentním typem C#:</span><span class="sxs-lookup"><span data-stu-id="a5ac9-154">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="a5ac9-155">C# typ</span><span class="sxs-lookup"><span data-stu-id="a5ac9-155">C# type</span></span>   | <span data-ttu-id="a5ac9-156">Obálka známého typu</span><span class="sxs-lookup"><span data-stu-id="a5ac9-156">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="a5ac9-157">Známé typy `Timestamp` a `Duration` jsou reprezentovány v .NET jako třídy.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-157">The well-known types `Timestamp` and `Duration` are represented in .NET as classes.</span></span> <span data-ttu-id="a5ac9-158">V C# 8 a dále můžete použít typy odkazů s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-158">In C# 8 and beyond, you can use nullable reference types.</span></span> <span data-ttu-id="a5ac9-159">Ale je důležité zkontrolovat null na vlastnosti těchto typů při `DateTimeOffset` převodu do nebo `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-159">But it's important to check for null on properties of those types when you're converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="a5ac9-160">Desetinná místa</span><span class="sxs-lookup"><span data-stu-id="a5ac9-160">Decimals</span></span>

<span data-ttu-id="a5ac9-161">Protobuf nepodporuje nativně typ `decimal` .NET, `double` `float`jen a .</span><span class="sxs-lookup"><span data-stu-id="a5ac9-161">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="a5ac9-162">V projektu Protobuf probíhá diskuse o možnosti přidání `Decimal` standardního typu ke známým typům s podporou platformy pro jazyky a architektury, které jej podporují.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-162">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it.</span></span> <span data-ttu-id="a5ac9-163">Zatím nebylo nic implementováno.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-163">Nothing has been implemented yet.</span></span>

<span data-ttu-id="a5ac9-164">Je možné vytvořit definici zprávy reprezentovat `decimal` typ, který by pracoval pro bezpečné serializace mezi klienty .NET a servery.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-164">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers.</span></span> <span data-ttu-id="a5ac9-165">Ale vývojáři na jiných platformách by museli pochopit formát, který se používá, a implementovat pro něj vlastní zpracování.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-165">But developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="a5ac9-166">Vytvoření vlastního desetinného typu pro Protobuf</span><span class="sxs-lookup"><span data-stu-id="a5ac9-166">Creating a custom decimal type for Protobuf</span></span>

<span data-ttu-id="a5ac9-167">Jednoduchá implementace může být podobná `Money` nestandardnímu typu, který používají `currency` některá api Google bez pole.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-167">A simple implementation might be similar to the nonstandard `Money` type that some Google APIs use, without the `currency` field.</span></span>

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

<span data-ttu-id="a5ac9-168">Pole `nanos` představuje hodnoty `0.999_999_999` `-0.999_999_999`od do .</span><span class="sxs-lookup"><span data-stu-id="a5ac9-168">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="a5ac9-169">Například `decimal` hodnota `1.5m` by být `{ units = 1, nanos = 500_000_000 }`reprezentován jako .</span><span class="sxs-lookup"><span data-stu-id="a5ac9-169">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }`.</span></span> <span data-ttu-id="a5ac9-170">To je `nanos` důvod, proč pole `sfixed32` v tomto příkladu používá `int32` typ, který kóduje efektivněji než pro větší hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-170">This is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values.</span></span> <span data-ttu-id="a5ac9-171">Pokud `units` je pole záporné, `nanos` mělo by být záporné.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-171">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="a5ac9-172">Existuje několik dalších algoritmů `decimal` pro kódování hodnot jako bajtové řetězce, ale tato zpráva je srozumitelnější než kterýkoli z nich.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-172">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is easier to understand than any of them.</span></span> <span data-ttu-id="a5ac9-173">Hodnoty nejsou ovlivněny endianness na různých platformách.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-173">The values are not affected by endianness on different platforms.</span></span>

<span data-ttu-id="a5ac9-174">Převod mezi tímto typem a typem BCL `decimal` může být implementován v c# takto:</span><span class="sxs-lookup"><span data-stu-id="a5ac9-174">Conversion between this type and the BCL `decimal` type might be implemented in C# like this:</span></span>

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
> <span data-ttu-id="a5ac9-175">Kdykoli používáte vlastní typy zpráv, jako je `.proto`tento, je *nutné* je dokumentovat s komentáři v .</span><span class="sxs-lookup"><span data-stu-id="a5ac9-175">Whenever you use custom message types like this, you *must* document them with comments in `.proto`.</span></span> <span data-ttu-id="a5ac9-176">Ostatní vývojáři pak můžete implementovat převod do a z ekvivalentního typu ve svém vlastním jazyce nebo rámci.</span><span class="sxs-lookup"><span data-stu-id="a5ac9-176">Other developers can then implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a5ac9-177">[Předchozí](protobuf-messages.md)
>[další](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="a5ac9-177">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
