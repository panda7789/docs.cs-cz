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
# <a name="protobuf-any-and-oneof-fields-for-variant-types"></a>Protobuf všechna pole a oneof pro typy variant

Manipulace s dynamickými typy vlastností (to znamená, vlastnosti typu `object`) v Windows Communication Foundation (WCF) jsou komplikované. Například je nutné zadat serializátory a zadat atributy [Třída KnownType](xref:System.Runtime.Serialization.KnownTypeAttribute) .

Vyrovnávací paměť protokolu (Protobuf) poskytuje dvě jednodušší možnosti pro práci s hodnotami, které mohou být více než jedním typem. Typ `Any` může představovat libovolný známý typ zprávy Protobuf. Pomocí klíčového slova `oneof` lze určit, že v libovolné zprávě lze nastavit pouze jeden z rozsahů polí.

## <a name="any"></a>Všechny

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

V C# kódu poskytuje třída `Any` metody pro nastavení pole, extrakci zprávy a kontrolu typu.

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

Vnitřní kód reflexe Protobuf používá pole static `Descriptor` u každého generovaného typu k překladu `Any` typů polí. K dispozici je také metoda `TryUnpack<T>`, která vytvoří neinicializované instance `T` i v případě, že dojde k chybě. Je lepší používat metodu `Is`, jak je uvedeno výše.

## <a name="oneof"></a>Oneof

Pole oneof jsou funkcí jazyka: kompilátor zpracovává klíčové slovo `oneof`, když generuje třídu zprávy. Použití `oneof` k určení `ChangeNotification` zprávy může vypadat takto:

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

Pole v sadě `oneof` musí mít v celkové deklaraci zprávy jedinečné číselné pole.

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
