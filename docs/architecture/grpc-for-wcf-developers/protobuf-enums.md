---
title: Výčty Protobuf – gRPC pro vývojáře WCF
description: Naučte se deklarovat a používat výčty v Protobuf.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d93319b713588129a19246976a82bb03a90ce680
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184237"
---
# <a name="protobuf-enumerations"></a>Výčty Protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Protobuf podporuje výčtové typy, jak je vidět v předchozí části, kde byl pro určení typu `oneof` pole použit výčet. Můžete definovat vlastní typy výčtu a Protobuf je zkompiluje do C# výčtových typů. Vzhledem k tomu, že Protobuf lze použít s různými jazyky, zásady vytváření názvů pro výčty se C# liší od konvencí. Generátor kódu je však chytřejší a převádí názvy na tradiční C# případ. Pokud je ekvivalent názvu pole v jazyce Pascal shodný s názvem výčtu, bude odstraněn.

Například v tomto výčtu Protobuf jsou pole předponou `ACCOUNT_STATUS`, což je ekvivalent názvu výčtu Case Case:. `AccountStatus`

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

Generátor proto vytvoří C# výčet podobný následujícímu kódu:

```csharp
public enum AccountStatus
{
    Unknown = 0,
    Pending = 1,
    Active = 2,
    Suspended = 3,
    Closed = 4
}
```

Definice výčtu Protobuf **musí** mít jako první pole nulovou konstantu. Jako v C#můžete deklarovat více polí se stejnou hodnotou, ale tuto možnost musíte explicitně povolit pomocí `allow_alias` možnosti ve výčtu:

```protobuf
enum AccountStatus {
  option allow_alias = true;
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
  ACCOUNT_STATUS_CANCELLED = 4;
}
```

Výčty můžete deklarovat na nejvyšší úrovni v `.proto` souboru nebo v definici zprávy. Vnořené výčty – podobně jako vnořené zprávy – budou deklarovány v `.Types` rámci statické třídy ve třídě vygenerované zprávy.

Neexistuje žádný způsob, jak použít atribut [[Flags]](xref:System.FlagsAttribute) u výčtu generovaného Protobuf a Protobuf nerozumí kombinací bitových výčtů. Podívejte se na následující příklad:

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region availableIn = 1;
}
```

Pokud nastavíte `product.AvailableIn` na `Region.NorthAmerica | Region.SouthAmerica`, je serializován jako celočíselná hodnota `3`. Když se klient nebo server pokusí hodnotu deserializovat, nenajde shodu v definici výčtu pro `3` a výsledek `Region.None`bude.

Nejlepším způsobem, jak pracovat s více hodnotami výčtu v Protobuf, je použít `repeated` pole typu výčtu.

>[!div class="step-by-step"]
>[Předchozí](protobuf-any-oneof.md)
>[Další](protobuf-maps.md)
