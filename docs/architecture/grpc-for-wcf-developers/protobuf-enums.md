---
title: Výčty Protobuf – gRPC pro vývojáře WCF
description: Naučte se deklarovat a používat výčty v Protobuf.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 37fd55e4cbc3c1e1e96e32875ddb3dcae0ca8355
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771646"
---
# <a name="protobuf-enumerations"></a>Výčty protobuf

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Protobuf podporuje výčtové typy, jak je vidět v předchozí části, kde byl pro určení typu `oneof` pole použit výčet. Můžete definovat vlastní typy výčtu a Protobuf je zkompiluje do C# výčtových typů. Vzhledem k tomu, že Protobuf lze použít s různými jazyky, zásady vytváření názvů pro výčty se C# liší od konvencí. Generátor kódu je však chytřejší a převádí názvy na tradiční C# případ. Pokud je ekvivalent názvu pole v jazyce Pascal shodný s názvem výčtu, bude odstraněn.

Například v tomto výčtu Protobuf jsou pole s předponou `ACCOUNT_STATUS`, která odpovídá názvu výčtu Case Case Enum: `AccountStatus`.

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

Definice výčtu Protobuf **musí** mít jako první pole nulovou konstantu. Jako v C#můžete deklarovat více polí se stejnou hodnotou, ale tuto možnost musíte explicitně povolit pomocí možnosti `allow_alias` ve výčtu:

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

Výčty můžete deklarovat na nejvyšší úrovni v souboru `.proto` nebo jsou vnořené v rámci definice zprávy. Vnořené výčty – podobně jako vnořené zprávy – budou deklarovány v rámci `.Types` statické třídy ve třídě generované zprávy.

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
  Region available_in = 1;
}
```

Nastavíte-li `product.AvailableIn` na `Region.NorthAmerica | Region.SouthAmerica`, je serializován jako celočíselná hodnota `3`. Když se klient nebo server pokusí hodnotu deserializovat, nenajde shodu v definici výčtu pro `3` a výsledek bude `Region.None`.

Nejlepším způsobem, jak pracovat s více hodnotami výčtu v Protobuf, je použít pole `repeated` typu výčtu.

>[!div class="step-by-step"]
>[Předchozí](protobuf-any-oneof.md)
>[Další](protobuf-maps.md)
