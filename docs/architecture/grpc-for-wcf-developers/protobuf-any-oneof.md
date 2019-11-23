---
title: Protobuf jakákoli pole a oneof pro typy variant – gRPC pro vývojáře WCF
description: Naučte se používat libovolný typ a klíčové slovo oneof k reprezentaci typů objektů variant ve zprávách.
ms.date: 09/09/2019
ms.openlocfilehash: af3ba22c238aa80a8c6119f62d5d8914770cad68
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971620"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="db3ee-103">Protobuf všechna pole a oneof pro typy variant</span><span class="sxs-lookup"><span data-stu-id="db3ee-103">Protobuf Any and Oneof fields for variant types</span></span>

<span data-ttu-id="db3ee-104">Manipulace s dynamickými typy vlastností (to znamená, vlastnosti typu `object`) ve službě WCF je složitá.</span><span class="sxs-lookup"><span data-stu-id="db3ee-104">Handling dynamic property types (that is, properties of type `object`) in WCF is complicated.</span></span> <span data-ttu-id="db3ee-105">Je nutné zadat serializátory, musí být zadány atributy [Třída KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) a tak dále.</span><span class="sxs-lookup"><span data-stu-id="db3ee-105">Serializers must be specified, [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes must be provided, and so on.</span></span>

<span data-ttu-id="db3ee-106">Protobuf poskytuje dvě jednodušší možnosti pro práci s hodnotami, které mohou být více než jedním typem.</span><span class="sxs-lookup"><span data-stu-id="db3ee-106">Protobuf provides two simpler options for dealing with values that may be of more than one type.</span></span> <span data-ttu-id="db3ee-107">Typ `Any` může představovat libovolný známý typ zprávy Protobuf, zatímco klíčové slovo `oneof` umožňuje určit, že v dané zprávě lze nastavit pouze jeden z rozsahů polí.</span><span class="sxs-lookup"><span data-stu-id="db3ee-107">The `Any` type can represent any known Protobuf message type, while the `oneof` keyword allows you to specify that only one of a range of fields can be set in any given message.</span></span>

## <a name="any"></a><span data-ttu-id="db3ee-108">Vše</span><span class="sxs-lookup"><span data-stu-id="db3ee-108">Any</span></span>

<span data-ttu-id="db3ee-109">`Any` je jedním z "dobře známých typů" Protobuf: kolekce užitečných a opakovaně použitelných typů zpráv s implementacemi ve všech podporovaných jazycích.</span><span class="sxs-lookup"><span data-stu-id="db3ee-109">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="db3ee-110">Chcete-li použít typ `Any`, je nutné naimportovat definici `google/protobuf/any.proto`.</span><span class="sxs-lookup"><span data-stu-id="db3ee-110">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

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

<span data-ttu-id="db3ee-111">V C# kódu poskytuje třída `Any` metody pro nastavení pole, extrakci zprávy a kontrolu typu.</span><span class="sxs-lookup"><span data-stu-id="db3ee-111">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

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

<span data-ttu-id="db3ee-112">`Descriptor` statické pole každého generovaného typu je používáno vnitřním kódem reflexe Protobuf k překladu `Any` typů polí.</span><span class="sxs-lookup"><span data-stu-id="db3ee-112">The `Descriptor` static field on each generated type is used by Protobuf's internal reflection code to resolve `Any` field types.</span></span> <span data-ttu-id="db3ee-113">K dispozici je také metoda `TryUnpack<T>`, která vytvoří neinicializované instance `T` i v případě, že se nezdařila, takže je lepší použít metodu `Is`, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="db3ee-113">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails, so it's better to use the `Is` method as shown above.</span></span>

## <a name="oneof"></a><span data-ttu-id="db3ee-114">Oneof</span><span class="sxs-lookup"><span data-stu-id="db3ee-114">Oneof</span></span>

<span data-ttu-id="db3ee-115">Pole oneof jsou funkcí jazyka: klíčové slovo `oneof` je při generování třídy zprávy zpracováno kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="db3ee-115">Oneof fields are a language feature: the `oneof` keyword is handled by the compiler when it generates the message class.</span></span> <span data-ttu-id="db3ee-116">Použití `oneof` k určení `ChangeNotification` zprávy může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="db3ee-116">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

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

<span data-ttu-id="db3ee-117">Pole v rámci `oneof` sady musí mít v rámci celkové deklarace zprávy jedinečné číselné pole.</span><span class="sxs-lookup"><span data-stu-id="db3ee-117">Fields within the `oneof` set must have unique field numbers within the overall message declaration.</span></span>

<span data-ttu-id="db3ee-118">Při použití `oneof`generovaný C# kód obsahuje výčet, který určuje, která z polí byla nastavena.</span><span class="sxs-lookup"><span data-stu-id="db3ee-118">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="db3ee-119">Chcete-li zjistit, které pole je nastaveno, můžete otestovat výčet.</span><span class="sxs-lookup"><span data-stu-id="db3ee-119">You can test the enum to find which field is set.</span></span> <span data-ttu-id="db3ee-120">Pole, která nejsou nastavena jako návratová `null` nebo výchozí hodnota namísto vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="db3ee-120">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

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

<span data-ttu-id="db3ee-121">Když se nastaví jakékoli pole, které je součástí `oneof` sady, automaticky se vymaže všechna ostatní pole v sadě.</span><span class="sxs-lookup"><span data-stu-id="db3ee-121">Setting any field that is part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="db3ee-122">`repeated` nelze použít s `oneof`.</span><span class="sxs-lookup"><span data-stu-id="db3ee-122">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="db3ee-123">Místo toho můžete vytvořit vnořenou zprávu s použitím opakujícího se pole nebo `oneof` sady, aby toto omezení bylo možné vyřešit.</span><span class="sxs-lookup"><span data-stu-id="db3ee-123">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="db3ee-124">[Předchozí](protobuf-reserved.md)
>[Další](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="db3ee-124">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
