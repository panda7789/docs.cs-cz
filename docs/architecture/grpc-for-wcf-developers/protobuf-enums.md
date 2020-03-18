---
title: Protobuf výčty - gRPC pro vývojáře WCF
description: Naučte se deklarovat a používat výčty v Protobuf.
ms.date: 09/09/2019
ms.openlocfilehash: 2177f568a671fa0e651625c6e025ac70c243feb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148072"
---
# <a name="protobuf-enumerations"></a>Výčty protobuf

Protobuf podporuje typy výčtu. Tuto podporu jste viděli v předchozí části, kde byl použit `Oneof` výčt k určení typu pole. Můžete definovat vlastní typy výčtu a Protobuf je zkompiluje do c# výčtu.

Vzhledem k tomu, že můžete použít Protobuf s různými jazyky, konvence pojmenování pro výčty se liší od c# konvence. Generátor kódu však převádí názvy na tradiční případ Jazyka C#. Pokud pascal-case ekvivalent názvu pole začíná názvem výčtu, pak je odebrán.

Například v následujícím výčtu Protobuf jsou pole `ACCOUNT_STATUS`předponou . Tato předpona je ekvivalentní pascal-case `AccountStatus`výčtu název .

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

Generátor vytvoří výčt c# ekvivalentní následující kód:

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

Protobuf výčtu definice *musí* mít nulovou konstantu jako jejich první pole. Stejně jako v c#, můžete deklarovat více polí se stejnou hodnotou. Ale musíte explicitně povolit `allow_alias` tuto možnost pomocí možnosti ve výčtu:

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

Výčty na nejvyšší úrovni v souboru `.proto` můžete deklarovat nebo vnořené v rámci definice zprávy. Vnořené výčty – jako vnořené `.Types` zprávy – budou deklarovány v rámci statické třídy ve třídě generované zprávy.

Neexistuje žádný způsob, jak použít [[Flags]](xref:System.FlagsAttribute) atribut Protobuf generované výčtu a Protobuf nerozumí bitové výčtu kombinace. Podívejte se na následující příklad:

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

Pokud nastavíte `product.AvailableIn` hodnotu `Region.NorthAmerica | Region.SouthAmerica`, bude serializována `3`jako celá hodnota . Když se klient nebo server pokusí rekonstruovat hodnotu, nenajde shodu v `3`definici výčtu pro . Výsledkem bude `Region.None`.

Nejlepší způsob, jak pracovat s více hodnotami výčtu v Protobuf je použít `repeated` pole typu výčtu.

>[!div class="step-by-step"]
>[Předchozí](protobuf-any-oneof.md)
>[další](protobuf-maps.md)
