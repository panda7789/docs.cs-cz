---
title: Protobuf jakákoli pole a oneof pro typy variant – gRPC pro vývojáře WCF
description: Naučte se používat libovolný typ a klíčové slovo oneof k reprezentaci typů objektů variant ve zprávách.
ms.date: 09/09/2019
ms.openlocfilehash: 6fe7acbd1ec35289f7ad6f3acee8509ab934619d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543193"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="7a89f-103">Protobuf všechna pole a oneof pro typy variant</span><span class="sxs-lookup"><span data-stu-id="7a89f-103">Protobuf Any and Oneof fields for variant types</span></span>

<span data-ttu-id="7a89f-104">Manipulace s dynamickými typy vlastností (to znamená, vlastnosti typu `object`) v Windows Communication Foundation (WCF) jsou komplikované.</span><span class="sxs-lookup"><span data-stu-id="7a89f-104">Handling dynamic property types (that is, properties of type `object`) in Windows Communication Foundation (WCF) is complicated.</span></span> <span data-ttu-id="7a89f-105">Například je nutné zadat serializátory a zadat atributy [Třída KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) .</span><span class="sxs-lookup"><span data-stu-id="7a89f-105">For example, you must specify serializers and provide [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes.</span></span>

<span data-ttu-id="7a89f-106">Vyrovnávací paměť protokolu (Protobuf) poskytuje dvě jednodušší možnosti pro práci s hodnotami, které mohou být více než jedním typem.</span><span class="sxs-lookup"><span data-stu-id="7a89f-106">Protocol Buffer (Protobuf) provides two simpler options for dealing with values that might be of more than one type.</span></span> <span data-ttu-id="7a89f-107">Typ `Any` může představovat libovolný známý typ zprávy Protobuf.</span><span class="sxs-lookup"><span data-stu-id="7a89f-107">The `Any` type can represent any known Protobuf message type.</span></span> <span data-ttu-id="7a89f-108">Pomocí klíčového slova `oneof` lze určit, že v libovolné zprávě lze nastavit pouze jeden z rozsahů polí.</span><span class="sxs-lookup"><span data-stu-id="7a89f-108">And you can use the `oneof` keyword to specify that only one of a range of fields can be set in any message.</span></span>

## <a name="any"></a><span data-ttu-id="7a89f-109">Všechny</span><span class="sxs-lookup"><span data-stu-id="7a89f-109">Any</span></span>

<span data-ttu-id="7a89f-110">`Any` je jedním z "dobře známých typů" Protobuf: kolekce užitečných a opakovaně použitelných typů zpráv s implementacemi ve všech podporovaných jazycích.</span><span class="sxs-lookup"><span data-stu-id="7a89f-110">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="7a89f-111">Chcete-li použít typ `Any`, je nutné naimportovat definici `google/protobuf/any.proto`.</span><span class="sxs-lookup"><span data-stu-id="7a89f-111">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

```protobuf
syntax "proto3"

import "google/protobuf/any.proto"

message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
    int32 id = 1;
    google.protobuf.Any instrument = 2;
}
```

<span data-ttu-id="7a89f-112">V C# kódu poskytuje třída `Any` metody pro nastavení pole, extrakci zprávy a kontrolu typu.</span><span class="sxs-lookup"><span data-stu-id="7a89f-112">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    if (change.Instrument.Is(Stock.Descriptor))
    {
        FormatStock(change.Instrument.Unpack<Stock>());
    }
    else if (change.Instrument.Is(Currency.Descriptor))
    {
        FormatCurrency(change.Instrument.Unpack<Currency>());
    }
    else
    {
        throw new ArgumentException("Unknown instrument type");
    }
}
```

<span data-ttu-id="7a89f-113">Vnitřní kód reflexe Protobuf používá pole static `Descriptor` u každého generovaného typu k překladu `Any` typů polí.</span><span class="sxs-lookup"><span data-stu-id="7a89f-113">Protobuf's internal reflection code uses the `Descriptor` static field on each generated type to resolve `Any` field types.</span></span> <span data-ttu-id="7a89f-114">K dispozici je také metoda `TryUnpack<T>`, která vytvoří neinicializované instance `T` i v případě, že dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="7a89f-114">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails.</span></span> <span data-ttu-id="7a89f-115">Je lepší používat metodu `Is`, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="7a89f-115">It's better to use the `Is` method as shown earlier.</span></span>

## <a name="oneof"></a><span data-ttu-id="7a89f-116">Oneof</span><span class="sxs-lookup"><span data-stu-id="7a89f-116">Oneof</span></span>

<span data-ttu-id="7a89f-117">Pole oneof jsou funkcí jazyka: kompilátor zpracovává klíčové slovo `oneof`, když generuje třídu zprávy.</span><span class="sxs-lookup"><span data-stu-id="7a89f-117">Oneof fields are a language feature: the compiler handles the `oneof` keyword when it generates the message class.</span></span> <span data-ttu-id="7a89f-118">Použití `oneof` k určení `ChangeNotification` zprávy může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="7a89f-118">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

```protobuf
message Stock {
    // Stock-specific data
}

message Currency {
    // Currency-specific data
}

message ChangeNotification {
  int32 id = 1;
  oneof instrument {
    Stock stock = 2;
    Currency currency = 3;
  }
}
```

<span data-ttu-id="7a89f-119">Pole v sadě `oneof` musí mít v celkové deklaraci zprávy jedinečné číselné pole.</span><span class="sxs-lookup"><span data-stu-id="7a89f-119">Fields within the `oneof` set must have unique field numbers in the overall message declaration.</span></span>

<span data-ttu-id="7a89f-120">Při použití `oneof`generovaný C# kód obsahuje výčet, který určuje, která z polí byla nastavena.</span><span class="sxs-lookup"><span data-stu-id="7a89f-120">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="7a89f-121">Chcete-li zjistit, které pole je nastaveno, můžete otestovat výčet.</span><span class="sxs-lookup"><span data-stu-id="7a89f-121">You can test the enum to find which field is set.</span></span> <span data-ttu-id="7a89f-122">Pole, která nejsou nastavena jako návratová `null` nebo výchozí hodnota namísto vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="7a89f-122">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

```csharp
public void FormatChangeNotification(ChangeNotification change)
{
    switch (change.InstrumentCase)
    {
        case ChangeNotification.InstrumentOneofCase.None:
            return;
        case ChangeNotification.InstrumentOneofCase.Stock:
            FormatStock(change.Stock);
            break;
        case ChangeNotification.InstrumentOneofCase.Currency:
            FormatCurrency(change.Currency);
            break;
        default:
            throw new ArgumentException("Unknown instrument type");
    }
}
```

<span data-ttu-id="7a89f-123">Když se nastaví jakékoli pole, které je součástí `oneof` sady, automaticky se vymaže všechna ostatní pole v sadě.</span><span class="sxs-lookup"><span data-stu-id="7a89f-123">Setting any field that's part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="7a89f-124">`repeated` nelze použít s `oneof`.</span><span class="sxs-lookup"><span data-stu-id="7a89f-124">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="7a89f-125">Místo toho můžete vytvořit vnořenou zprávu s použitím opakujícího se pole nebo `oneof` sady, aby toto omezení bylo možné vyřešit.</span><span class="sxs-lookup"><span data-stu-id="7a89f-125">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="7a89f-126">[Předchozí](protobuf-reserved.md)
>[Další](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="7a89f-126">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
