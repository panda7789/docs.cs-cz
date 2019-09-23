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
# <a name="protobuf-scalar-data-types"></a><span data-ttu-id="b81ab-103">Protobuf skalárních datových typů</span><span class="sxs-lookup"><span data-stu-id="b81ab-103">Protobuf scalar data types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="b81ab-104">Protobuf podporuje rozsah nativních typů skalárních hodnot.</span><span class="sxs-lookup"><span data-stu-id="b81ab-104">Protobuf supports a range of native scalar value types.</span></span> <span data-ttu-id="b81ab-105">V následující tabulce jsou uvedeny všechny s ekvivalentním C# typem:</span><span class="sxs-lookup"><span data-stu-id="b81ab-105">The following table lists them all with their equivalent C# type:</span></span>

| <span data-ttu-id="b81ab-106">Typ Protobuf</span><span class="sxs-lookup"><span data-stu-id="b81ab-106">Protobuf type</span></span> | <span data-ttu-id="b81ab-107">C#textový</span><span class="sxs-lookup"><span data-stu-id="b81ab-107">C# type</span></span>      | <span data-ttu-id="b81ab-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b81ab-108">Notes</span></span> |
| ------------- | ------------ | ----- |
| `double`      | `double`     |       |
| `float`       | `float`      |       |
| `int32`       | `int`        | <span data-ttu-id="b81ab-109">1</span><span class="sxs-lookup"><span data-stu-id="b81ab-109">1</span></span>     |
| `int64`       | `long`       | <span data-ttu-id="b81ab-110">1</span><span class="sxs-lookup"><span data-stu-id="b81ab-110">1</span></span>     |
| `uint32`      | `uint`       |       |
| `uint64`      | `ulong`      |       |
| `sint32`      | `int`        | <span data-ttu-id="b81ab-111">1</span><span class="sxs-lookup"><span data-stu-id="b81ab-111">1</span></span>     |
| `sint64`      | `long`       | <span data-ttu-id="b81ab-112">1</span><span class="sxs-lookup"><span data-stu-id="b81ab-112">1</span></span>     |
| `fixed32`     | `uint`       | <span data-ttu-id="b81ab-113">2</span><span class="sxs-lookup"><span data-stu-id="b81ab-113">2</span></span>     |
| `fixed64`     | `ulong`      | <span data-ttu-id="b81ab-114">2</span><span class="sxs-lookup"><span data-stu-id="b81ab-114">2</span></span>     |
| `sfixed32`    | `int`        | <span data-ttu-id="b81ab-115">2</span><span class="sxs-lookup"><span data-stu-id="b81ab-115">2</span></span>     |
| `sfixed64`    | `long`       | <span data-ttu-id="b81ab-116">2</span><span class="sxs-lookup"><span data-stu-id="b81ab-116">2</span></span>     |
| `bool`        | `bool`       |       |
| `string`      | `string`     | <span data-ttu-id="b81ab-117">3</span><span class="sxs-lookup"><span data-stu-id="b81ab-117">3</span></span>     |
| `bytes`       | `ByteString` | <span data-ttu-id="b81ab-118">4</span><span class="sxs-lookup"><span data-stu-id="b81ab-118">4</span></span>     |

## <a name="notes"></a><span data-ttu-id="b81ab-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b81ab-119">Notes</span></span>

1. <span data-ttu-id="b81ab-120">Standardní kódování pro `int32` a `int64` je neefektivní při práci s podepsanými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="b81ab-120">The standard encoding for `int32` and `int64` is inefficient when working with signed values.</span></span> <span data-ttu-id="b81ab-121">Pokud pole může obsahovat záporná čísla, použijte `sint32` nebo `sint64` místo toho.</span><span class="sxs-lookup"><span data-stu-id="b81ab-121">If your field is likely to contain negative numbers, use `sint32` or `sint64` instead.</span></span> <span data-ttu-id="b81ab-122">Oba typy jsou C# `int` mapovány na `long` typy a v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="b81ab-122">Both types map to the C# `int` and `long` types, respectively.</span></span>
2. <span data-ttu-id="b81ab-123">`fixed` Pole vždycky používají stejný počet bajtů bez ohledu na to, jaká hodnota je.</span><span class="sxs-lookup"><span data-stu-id="b81ab-123">The `fixed` fields always use the same number of bytes no matter what the value is.</span></span> <span data-ttu-id="b81ab-124">Díky tomuto chování je serializace a deserializace rychlejší pro větší hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b81ab-124">This behavior makes serialization and deserialization faster for larger values.</span></span>
3. <span data-ttu-id="b81ab-125">Protobuf řetězce jsou zakódované UTF-8 (nebo 7 bitů ASCII) a Kódovaná délka nesmí být větší než 2<sup>32</sup>.</span><span class="sxs-lookup"><span data-stu-id="b81ab-125">Protobuf strings are UTF-8 (or 7-bit ASCII) encoded, and the encoded length can't be greater than 2<sup>32</sup>.</span></span>
4. <span data-ttu-id="b81ab-126">Modul runtime Protobuf poskytuje `ByteString` typ, který se snadno mapuje na pole a z C# `byte[]` nich.</span><span class="sxs-lookup"><span data-stu-id="b81ab-126">The Protobuf runtime provides a `ByteString` type that maps easily to and from C# `byte[]` arrays.</span></span>

## <a name="other-net-primitive-types"></a><span data-ttu-id="b81ab-127">Jiné primitivní typy .NET</span><span class="sxs-lookup"><span data-stu-id="b81ab-127">Other .NET primitive types</span></span>

### <a name="dates-and-times"></a><span data-ttu-id="b81ab-128">Data a časy</span><span class="sxs-lookup"><span data-stu-id="b81ab-128">Dates and times</span></span>

<span data-ttu-id="b81ab-129">Nativní skalární typy neposkytují hodnoty data a času C#, ekvivalentní hodnotě <xref:System.DateTimeOffset>, <xref:System.DateTime>a <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="b81ab-129">The native scalar types don't provide for date and time values, equivalent to C#'s <xref:System.DateTimeOffset>, <xref:System.DateTime>, and <xref:System.TimeSpan>.</span></span> <span data-ttu-id="b81ab-130">Tyto typy lze zadat pomocí některých rozšíření "dobře známých typů" Google, které poskytují generování kódu a podporu modulu runtime pro komplexnější typy polí napříč podporovanými platformami.</span><span class="sxs-lookup"><span data-stu-id="b81ab-130">These types can be specified using some of Google's "Well Known Types" extensions, which provide code generation and runtime support for more complex field types across the supported platforms.</span></span> <span data-ttu-id="b81ab-131">V následující tabulce jsou uvedeny typy data a času:</span><span class="sxs-lookup"><span data-stu-id="b81ab-131">The following table shows the date and time types:</span></span>

| <span data-ttu-id="b81ab-132">C#textový</span><span class="sxs-lookup"><span data-stu-id="b81ab-132">C# type</span></span> | <span data-ttu-id="b81ab-133">Protobuf dobře známý typ</span><span class="sxs-lookup"><span data-stu-id="b81ab-133">Protobuf well-known type</span></span> |
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

<span data-ttu-id="b81ab-134">Vygenerované vlastnosti ve C# třídě nejsou typy data a času .NET.</span><span class="sxs-lookup"><span data-stu-id="b81ab-134">The generated properties in the C# class aren't the .NET date and time types.</span></span> <span data-ttu-id="b81ab-135">Vlastnosti používají `Timestamp` třídy a `DateTime` `DateTimeOffset` `TimeSpan`v oboru názvů, které poskytují metody pro převod na a z, a. `Google.Protobuf.WellKnownTypes` `Duration`</span><span class="sxs-lookup"><span data-stu-id="b81ab-135">The properties use the `Timestamp` and `Duration` classes in the `Google.Protobuf.WellKnownTypes` namespace, which provide methods for converting to and from `DateTimeOffset`, `DateTime`, and `TimeSpan`.</span></span>

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
> <span data-ttu-id="b81ab-136">`Timestamp` Typ pracuje s časy UTC; hodnoty vždy mají posun nula `DateTime.Kind` a vlastnost bude vždy `DateTimeKind.Utc`. `DateTimeOffset`</span><span class="sxs-lookup"><span data-stu-id="b81ab-136">The `Timestamp` type works with UTC times; `DateTimeOffset` values always have an offset of zero, and the `DateTime.Kind` property will always be `DateTimeKind.Utc`.</span></span>

### <a name="systemguid"></a><span data-ttu-id="b81ab-137">System.Guid</span><span class="sxs-lookup"><span data-stu-id="b81ab-137">System.Guid</span></span>

<span data-ttu-id="b81ab-138">Typ, známý jako `UUID` na jiných platformách, není přímo podporován Protobuf a neexistuje žádný známý typ. <xref:System.Guid></span><span class="sxs-lookup"><span data-stu-id="b81ab-138">The <xref:System.Guid> type, known as `UUID` on other platforms, isn't directly supported by Protobuf and there's no well-known type for it.</span></span> <span data-ttu-id="b81ab-139">Nejlepším `Guid` řešením je zpracovávat hodnoty jako `string` pole pomocí standardního `8-4-4-4-12` šestnáctkového formátu (například `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), který lze analyzovat pomocí všech jazyků a platforem.</span><span class="sxs-lookup"><span data-stu-id="b81ab-139">The best approach is to handle `Guid` values as `string` field, using the standard `8-4-4-4-12` hexadecimal format (for example, `45a9fda3-bd01-47a9-8460-c1cd7484b0b3`), which can be parsed by all languages and platforms.</span></span> <span data-ttu-id="b81ab-140">Nepoužívejte `bytes` pro `Guid` hodnoty pole, protože problémy s endian můžou způsobit nestabilní chování při komunikaci s jinými platformami, jako je Java.</span><span class="sxs-lookup"><span data-stu-id="b81ab-140">Don't use a `bytes` field for `Guid` values, as problems with endianness can result in erratic behavior when interacting with other platforms, such as Java.</span></span>

### <a name="nullable-types"></a><span data-ttu-id="b81ab-141">Typy s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="b81ab-141">Nullable types</span></span>

<span data-ttu-id="b81ab-142">Generování kódu Protobuf pro C# používá nativní typy, `int` jako například pro. `int32`</span><span class="sxs-lookup"><span data-stu-id="b81ab-142">The Protobuf code generation for C# uses the native types, such as `int` for `int32`.</span></span> <span data-ttu-id="b81ab-143">To znamená, že hodnoty jsou vždycky zahrnuté a nesmí mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b81ab-143">This means that the values are always included and can't be null.</span></span> <span data-ttu-id="b81ab-144">Pro hodnoty, které vyžadují explicitní null, jako je `int?` například použití C# ve vašem kódu, jsou "dobře známé typy" Protobuf zahrnuty obálky, které jsou C# kompilovány na typy s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b81ab-144">For values that require explicit null, such as using `int?` in your C# code, Protobuf's "Well Known Types" include wrappers that are compiled to nullable C# types.</span></span> <span data-ttu-id="b81ab-145">Pokud je chcete použít, `wrappers.proto` importujte je `.proto` do souboru následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b81ab-145">To use them, import `wrappers.proto` into your `.proto` file, like this:</span></span>

```protobuf  
syntax = "proto3"

import "google/protobuf/wrappers.proto"

message Person {

    ...
    google.protobuf.Int32Value age = 5;

}
```

<span data-ttu-id="b81ab-146">Protobuf bude pro generovanou vlastnost `T?` zprávy používat jednoduché ( `int?`například).</span><span class="sxs-lookup"><span data-stu-id="b81ab-146">Protobuf will use the simple `T?` (for example, `int?`) for the generated message property.</span></span>

<span data-ttu-id="b81ab-147">Následující tabulka uvádí úplný seznam typů obálek s ekvivalentním C# typem:</span><span class="sxs-lookup"><span data-stu-id="b81ab-147">The following table shows the complete list of wrapper types with their equivalent C# type:</span></span>

| <span data-ttu-id="b81ab-148">C#textový</span><span class="sxs-lookup"><span data-stu-id="b81ab-148">C# type</span></span>   | <span data-ttu-id="b81ab-149">Obálka dobře známého typu</span><span class="sxs-lookup"><span data-stu-id="b81ab-149">Well Known Type wrapper</span></span>       |
| --------- | ----------------------------- |
| `double?` | `google.protobuf.DoubleValue` |
| `float?`  | `google.protobuf.FloatValue`  |
| `int?`    | `google.protobuf.Int32Value`  |
| `long?`   | `google.protobuf.Int64Value`  |
| `uint?`   | `google.protobuf.UInt32Value` |
| `ulong?`  | `google.protobuf.UInt64Value` |

<span data-ttu-id="b81ab-150">Známé typy `Timestamp` a `Duration` jsou reprezentovány v rozhraní .NET jako třídy, takže není nutné mít k dispozici verzi s možnou hodnotou null, je však důležité při převodu na nebo `TimeSpan`provést `DateTimeOffset` kontrolu hodnot null u vlastností těchto typů.</span><span class="sxs-lookup"><span data-stu-id="b81ab-150">The well-known types `Timestamp` and `Duration` are represented in .NET as classes, so there's no need for a nullable version, but it's important to check for null on properties of those types when converting to `DateTimeOffset` or `TimeSpan`.</span></span>

## <a name="decimals"></a><span data-ttu-id="b81ab-151">Desetinných míst</span><span class="sxs-lookup"><span data-stu-id="b81ab-151">Decimals</span></span>

<span data-ttu-id="b81ab-152">Protobuf netivně podporuje typ .NET `decimal` , a to jenom `double` a. `float`</span><span class="sxs-lookup"><span data-stu-id="b81ab-152">Protobuf doesn't natively support the .NET `decimal` type, just `double` and `float`.</span></span> <span data-ttu-id="b81ab-153">V projektu Protobuf je průběžná diskuze o tom, jak přidat standardní `Decimal` typ k dobře známým typům, s podporou platforem pro jazyky a architektury, které ho podporují, ale ještě nic se neimplementovalo.</span><span class="sxs-lookup"><span data-stu-id="b81ab-153">There's an ongoing discussion in the Protobuf project about the possibility of adding a standard `Decimal` type to the well-known types, with platform support for languages and frameworks that support it, but nothing has been implemented yet.</span></span>

<span data-ttu-id="b81ab-154">Je možné vytvořit definici zprávy, která bude představovat `decimal` typ, který by fungoval pro bezpečnou serializaci mezi klienty a servery rozhraní .NET, ale vývojáři na jiných platformách by museli porozumět použitému formátu a implementovat své vlastní. zpracování.</span><span class="sxs-lookup"><span data-stu-id="b81ab-154">It's possible to create a message definition to represent the `decimal` type that would work for safe serialization between .NET clients and servers, but developers on other platforms would have to understand the format being used and implement their own handling for it.</span></span>

### <a name="creating-a-custom-decimal-type-for-protobuf"></a><span data-ttu-id="b81ab-155">Vytvoření vlastního typu desetinného čísla pro Protobuf</span><span class="sxs-lookup"><span data-stu-id="b81ab-155">Creating a custom Decimal type for Protobuf</span></span>

<span data-ttu-id="b81ab-156">Velmi jednoduchá implementace může být podobná nestandardnímu `Money` typu, který používají některá rozhraní API Google, `currency` bez pole.</span><span class="sxs-lookup"><span data-stu-id="b81ab-156">A very simple implementation could be similar to the non-standard `Money` type used by some Google APIs, without the `currency` field.</span></span>

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

<span data-ttu-id="b81ab-157">Pole představuje hodnoty z `0.999_999_999` do `-0.999_999_999`. `nanos`</span><span class="sxs-lookup"><span data-stu-id="b81ab-157">The `nanos` field represents values from `0.999_999_999` to `-0.999_999_999`.</span></span> <span data-ttu-id="b81ab-158">`decimal` `sfixed32` Hodnota `int32` `nanos` by například byla reprezentovaná jako `{ units = 1, nanos = 500_000_000 }` (to je důvod, proč pole v tomto příkladu používá typ, který kóduje efektivněji než pro větší hodnoty). `1.5m`</span><span class="sxs-lookup"><span data-stu-id="b81ab-158">For example, the `decimal` value `1.5m` would be represented as `{ units = 1, nanos = 500_000_000 }` (this is why the `nanos` field in this example uses the `sfixed32` type, which encodes more efficiently than `int32` for larger values).</span></span> <span data-ttu-id="b81ab-159">Pokud je `nanos` pole záporné, mělo by být pole také záporné. `units`</span><span class="sxs-lookup"><span data-stu-id="b81ab-159">If the `units` field is negative, the `nanos` field should also be negative.</span></span>

> [!NOTE]
> <span data-ttu-id="b81ab-160">K dispozici je několik dalších algoritmů pro kódování `decimal` hodnot jako bajtů, ale tato zpráva je mnohem jednodušší, než je některý z nich, a hodnoty neovlivní *[endian](https://en.wikipedia.org/wiki/Endianness)* na různých platformách.</span><span class="sxs-lookup"><span data-stu-id="b81ab-160">There are multiple other algorithms for encoding `decimal` values as byte strings, but this message is much easier to understand than any of them, and the values are not affected by *[endianness](https://en.wikipedia.org/wiki/Endianness)* on different platforms.</span></span>

<span data-ttu-id="b81ab-161">Konverze mezi tímto typem a typem BCL `decimal` by mohla být implementována C# jako.</span><span class="sxs-lookup"><span data-stu-id="b81ab-161">Conversion between this type and the BCL `decimal` type could be implemented in C# like this.</span></span>

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
> <span data-ttu-id="b81ab-162">Vždy, když použijete vlastní typy zpráv nástroje, **musíte** je dokumentovat s komentáři v `.proto` , aby ostatní vývojáři mohli implementovat převod na a z ekvivalentního typu v jejich vlastním jazyce nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b81ab-162">Whenever you use custom utility message types like this, you **must** document them with comments in the `.proto` so that other developers can implement conversion to and from the equivalent type in their own language or framework.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b81ab-163">[Předchozí](protobuf-messages.md)
>[Další](protobuf-nested-types.md)</span><span class="sxs-lookup"><span data-stu-id="b81ab-163">[Previous](protobuf-messages.md)
[Next](protobuf-nested-types.md)</span></span>
