---
title: Protobuf jakákoli pole a oneof pro typy variant – gRPC pro vývojáře WCF
description: Naučte se používat libovolný typ a klíčové slovo oneof k reprezentaci typů objektů variant ve zprávách.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 9e730e96bfdb25ef6e07ee10967921408c6f2e84
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184279"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a><span data-ttu-id="2198c-103">Protobuf všechna pole a oneof pro typy variant</span><span class="sxs-lookup"><span data-stu-id="2198c-103">Protobuf Any and Oneof fields for variant types</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="2198c-104">Manipulace s dynamickými typy vlastností (to znamená, vlastnosti `object`typu) ve službě WCF je složitá.</span><span class="sxs-lookup"><span data-stu-id="2198c-104">Handling dynamic property types (that is, properties of type `object`) in WCF is complicated.</span></span> <span data-ttu-id="2198c-105">Je nutné zadat serializátory, musí být zadány atributy [Třída KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) a tak dále.</span><span class="sxs-lookup"><span data-stu-id="2198c-105">Serializers must be specified, [KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) attributes must be provided, and so on.</span></span>

<span data-ttu-id="2198c-106">Protobuf poskytuje dvě jednodušší možnosti pro práci s hodnotami, které mohou být více než jedním typem.</span><span class="sxs-lookup"><span data-stu-id="2198c-106">Protobuf provides two simpler options for dealing with values that may be of more than one type.</span></span> <span data-ttu-id="2198c-107">Typ může představovat libovolný známý typ zprávy Protobuf, `oneof` zatímco klíčové slovo umožňuje určit, že v dané zprávě lze nastavit pouze jeden z rozsahů polí. `Any`</span><span class="sxs-lookup"><span data-stu-id="2198c-107">The `Any` type can represent any known Protobuf message type, while the `oneof` keyword allows you to specify that only one of a range of fields can be set in any given message.</span></span>

## <a name="any"></a><span data-ttu-id="2198c-108">Any</span><span class="sxs-lookup"><span data-stu-id="2198c-108">Any</span></span>

<span data-ttu-id="2198c-109">`Any`je jedním z "dobře známých typů" Protobuf: kolekce užitečných a opakovaně použitelných typů zpráv s implementacemi ve všech podporovaných jazycích.</span><span class="sxs-lookup"><span data-stu-id="2198c-109">`Any` is one of Protobuf's "well-known types": a collection of useful, reusable message types with implementations in all supported languages.</span></span> <span data-ttu-id="2198c-110">Chcete-li `Any` použít typ, je nutné `google/protobuf/any.proto` importovat definici.</span><span class="sxs-lookup"><span data-stu-id="2198c-110">To use the `Any` type, you must import the `google/protobuf/any.proto` definition.</span></span>

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

<span data-ttu-id="2198c-111">V C# kódu `Any` Třída poskytuje metody pro nastavení pole, extrakci zprávy a kontrolu typu.</span><span class="sxs-lookup"><span data-stu-id="2198c-111">In the C# code, the `Any` class provides methods for setting the field, extracting the message, and checking the type.</span></span>

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

<span data-ttu-id="2198c-112">Statické pole každého generovaného typu je používáno vnitřním kódem reflexe Protobuf k řešení `Any` typů polí. `Descriptor`</span><span class="sxs-lookup"><span data-stu-id="2198c-112">The `Descriptor` static field on each generated type is used by Protobuf's internal reflection code to resolve `Any` field types.</span></span> <span data-ttu-id="2198c-113">Existuje také `TryUnpack<T>` metoda, která vytvoří neinicializované instance i v `T` případě, že se nezdařila, takže je lepší použít `Is` metodu, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="2198c-113">There's also a `TryUnpack<T>` method, but that creates an uninitialized instance of `T` even when it fails, so it's better to use the `Is` method as shown above.</span></span>

## <a name="oneof"></a><span data-ttu-id="2198c-114">Oneof</span><span class="sxs-lookup"><span data-stu-id="2198c-114">Oneof</span></span>

<span data-ttu-id="2198c-115">Pole oneof jsou funkcí jazyka: `oneof` klíčové slovo je při generování třídy zprávy zpracováno kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="2198c-115">Oneof fields are a language feature: the `oneof` keyword is handled by the compiler when it generates the message class.</span></span> <span data-ttu-id="2198c-116">Použití `oneof` k`ChangeNotification` určení zprávy může vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="2198c-116">Using `oneof` to specify the `ChangeNotification` message might look like this:</span></span>

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

<span data-ttu-id="2198c-117">Pole v `oneof` sadě musí mít v rámci celkové deklarace zprávy jedinečné číselné pole.</span><span class="sxs-lookup"><span data-stu-id="2198c-117">Fields within the `oneof` set must have unique field numbers within the overall message declaration.</span></span>

<span data-ttu-id="2198c-118">Při použití `oneof`, vygenerovaný C# kód obsahuje výčet, který určuje, která z polí byla nastavena.</span><span class="sxs-lookup"><span data-stu-id="2198c-118">When you use `oneof`, the generated C# code includes an enum that specifies which of the fields has been set.</span></span> <span data-ttu-id="2198c-119">Chcete-li zjistit, které pole je nastaveno, můžete otestovat výčet.</span><span class="sxs-lookup"><span data-stu-id="2198c-119">You can test the enum to find which field is set.</span></span> <span data-ttu-id="2198c-120">Pole, která nejsou nastavena `null` jako návratová hodnota nebo výchozí hodnotu, namísto vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="2198c-120">Fields that aren't set return `null` or the default value, rather than throwing an exception.</span></span>

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

<span data-ttu-id="2198c-121">Nastavení libovolného pole, které je součástí `oneof` sady, bude automaticky vyjasnit všechna ostatní pole v sadě.</span><span class="sxs-lookup"><span data-stu-id="2198c-121">Setting any field that is part of a `oneof` set will automatically clear any other fields in the set.</span></span> <span data-ttu-id="2198c-122">Nelze použít `repeated` s `oneof`.</span><span class="sxs-lookup"><span data-stu-id="2198c-122">You can't use `repeated` with `oneof`.</span></span> <span data-ttu-id="2198c-123">Místo toho můžete vytvořit vnořenou zprávu s tímto omezením buď pomocí opakujícího `oneof` se pole, nebo nastavením.</span><span class="sxs-lookup"><span data-stu-id="2198c-123">Instead, you can create a nested message with either the repeated field or the `oneof` set to work around this limitation.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="2198c-124">[Předchozí](protobuf-reserved.md)
>[Další](protobuf-enums.md)</span><span class="sxs-lookup"><span data-stu-id="2198c-124">[Previous](protobuf-reserved.md)
[Next](protobuf-enums.md)</span></span>
