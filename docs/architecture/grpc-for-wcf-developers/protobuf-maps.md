---
title: Protobuf Maps for slovníks – gRPC pro vývojáře WCF
description: Seznamte se s použitím Protobuf Maps k vyjádření. Typy slovníků netto.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: f6a71fb7940145571a94eaf5c8bae9dfc91a30db
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184209"
---
# <a name="protobuf-maps-for-dictionaries"></a>Protobuf Maps pro slovníky

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Je důležité, aby bylo možné vyjádřit libovolné kolekce pojmenovaných hodnot ve zprávách. V rozhraní .NET to se běžně zpracovává pomocí typů slovníků. Typ je ekvivalentem Protobuf typu <xref:System.Collections.Generic.IDictionary%602>.NET. `map<key_type, value_type>` `map` V této části se dozvíte, jak deklarovat v Protobuf a jak používat generovaný kód.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

Ve vygenerovaném kódu `map` pole `Google.Protobuf.Collections.MapField<TKey, TValue>` používá třídu, která implementuje standardní rozhraní kolekce .NET, včetně <xref:System.Collections.Generic.IDictionary%602>.

Pole mapování nelze přímo zopakovat v definici zprávy, ale můžete vytvořit vnořenou zprávu obsahující mapu a použít `repeated` ji jako typ zprávy, jako v následujícím příkladu:

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>Použití vlastností MapField v kódu

Vlastnosti generované z `map` polí jsou jen pro čtení a nikdy `null`nebudou. `MapField` Chcete-li nastavit vlastnost mapy, použijte `Add(IDictionary<TKey,TValue> values)` k kopírování hodnot z `MapField` libovolného slovníku .NET metodu pro vlastnost Empty.

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>Další čtení

Další informace o Protobuf najdete v oficiální [dokumentaci k Protobuf](https://developers.google.com/protocol-buffers/docs/overview).

>[!div class="step-by-step"]
>[Předchozí](protobuf-enums.md)
>[Další](wcf-services-to-grpc-comparison.md)
