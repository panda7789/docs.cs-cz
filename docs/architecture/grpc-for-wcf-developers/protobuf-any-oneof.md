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
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Protobuf všechna pole a oneof pro typy variant

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Manipulace s dynamickými typy vlastností (to znamená, vlastnosti `object`typu) ve službě WCF je složitá. Je nutné zadat serializátory, musí být zadány atributy [Třída KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) a tak dále.

Protobuf poskytuje dvě jednodušší možnosti pro práci s hodnotami, které mohou být více než jedním typem. Typ může představovat libovolný známý typ zprávy Protobuf, `oneof` zatímco klíčové slovo umožňuje určit, že v dané zprávě lze nastavit pouze jeden z rozsahů polí. `Any`

## <a name="any"></a>Any

`Any`je jedním z "dobře známých typů" Protobuf: kolekce užitečných a opakovaně použitelných typů zpráv s implementacemi ve všech podporovaných jazycích. Chcete-li `Any` použít typ, je nutné `google/protobuf/any.proto` importovat definici.

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

V C# kódu `Any` Třída poskytuje metody pro nastavení pole, extrakci zprávy a kontrolu typu.

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

Statické pole každého generovaného typu je používáno vnitřním kódem reflexe Protobuf k řešení `Any` typů polí. `Descriptor` Existuje také `TryUnpack<T>` metoda, která vytvoří neinicializované instance i v `T` případě, že se nezdařila, takže je lepší použít `Is` metodu, jak je uvedeno výše.

## <a name="oneof"></a>Oneof

Pole oneof jsou funkcí jazyka: `oneof` klíčové slovo je při generování třídy zprávy zpracováno kompilátorem. Použití `oneof` k`ChangeNotification` určení zprávy může vypadat takto:

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

Pole v `oneof` sadě musí mít v rámci celkové deklarace zprávy jedinečné číselné pole.

Při použití `oneof`, vygenerovaný C# kód obsahuje výčet, který určuje, která z polí byla nastavena. Chcete-li zjistit, které pole je nastaveno, můžete otestovat výčet. Pole, která nejsou nastavena `null` jako návratová hodnota nebo výchozí hodnotu, namísto vyvolání výjimky.

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

Nastavení libovolného pole, které je součástí `oneof` sady, bude automaticky vyjasnit všechna ostatní pole v sadě. Nelze použít `repeated` s `oneof`. Místo toho můžete vytvořit vnořenou zprávu s tímto omezením buď pomocí opakujícího `oneof` se pole, nebo nastavením.

>[!div class="step-by-step"]
>[Předchozí](protobuf-reserved.md)
>[Další](protobuf-enums.md)
