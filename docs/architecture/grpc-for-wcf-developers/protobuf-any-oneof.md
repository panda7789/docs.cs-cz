---
title: Protobuf jakákoli pole a oneof pro typy variant – gRPC pro vývojáře WCF
description: Naučte se používat libovolný typ a klíčové slovo oneof k reprezentaci typů objektů variant ve zprávách.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 10f55288eb4a6aa603228da5b4850317d6bde614
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846383"
---
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Protobuf všechna pole a oneof pro typy variant

Manipulace s dynamickými typy vlastností (to znamená, vlastnosti typu `object`) ve službě WCF je složitá. Je nutné zadat serializátory, musí být zadány atributy [Třída KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) a tak dále.

Protobuf poskytuje dvě jednodušší možnosti pro práci s hodnotami, které mohou být více než jedním typem. Typ `Any` může představovat libovolný známý typ zprávy Protobuf, zatímco klíčové slovo `oneof` umožňuje určit, že v dané zprávě lze nastavit pouze jeden z rozsahů polí.

## <a name="any"></a>Jakýmikoli

`Any` je jedním z "dobře známých typů" Protobuf: kolekce užitečných a opakovaně použitelných typů zpráv s implementacemi ve všech podporovaných jazycích. Chcete-li použít typ `Any`, je nutné naimportovat definici `google/protobuf/any.proto`.

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

V C# kódu poskytuje třída`Any`metody pro nastavení pole, extrakci zprávy a kontrolu typu.

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

`Descriptor` statické pole každého generovaného typu je používáno vnitřním kódem reflexe Protobuf k překladu `Any` typů polí. K dispozici je také metoda `TryUnpack<T>`, která vytvoří neinicializované instance `T` i v případě, že se nezdařila, takže je lepší použít metodu `Is`, jak je uvedeno výše.

## <a name="oneof"></a>Oneof

Pole oneof jsou funkcí jazyka: klíčové slovo `oneof` je při generování třídy zprávy zpracováno kompilátorem. Použití `oneof` k určení `ChangeNotification` zprávy může vypadat takto:

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

Pole v rámci `oneof` sady musí mít v rámci celkové deklarace zprávy jedinečné číselné pole.

Při použití `oneof`generovaný C# kód obsahuje výčet, který určuje, která z polí byla nastavena. Chcete-li zjistit, které pole je nastaveno, můžete otestovat výčet. Pole, která nejsou nastavena jako návratová `null` nebo výchozí hodnota namísto vyvolání výjimky.

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

Když se nastaví jakékoli pole, které je součástí `oneof` sady, automaticky se vymaže všechna ostatní pole v sadě. `repeated` nelze použít s `oneof`. Místo toho můžete vytvořit vnořenou zprávu s použitím opakujícího se pole nebo `oneof` sady, aby toto omezení bylo možné vyřešit.

>[!div class="step-by-step"]
>[Předchozí](protobuf-reserved.md)
>[Další](protobuf-enums.md)
