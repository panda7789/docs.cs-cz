---
title: Protobuf Maps for slovníks – gRPC pro vývojáře WCF
description: Naučte se používat mapy Protobuf k reprezentování typů slovníků v .NET.
ms.date: 09/09/2019
ms.openlocfilehash: 2c2ae76d47b2309227d22235b5acbe2afa794158
ms.sourcegitcommit: b9122d1af21898eaba81e990c70fef46fef74a8d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2020
ms.locfileid: "88867462"
---
# <a name="protobuf-maps-for-dictionaries"></a>Mapování protobuf pro slovníky

Je důležité, aby bylo možné vyjádřit libovolné kolekce pojmenovaných hodnot ve zprávách. V rozhraní .NET se to obvykle zpracovává prostřednictvím typů slovníků. Ekvivalentem <xref:System.Collections.Generic.IDictionary%602> typu .NET v vyrovnávací paměti protokolu (Protobuf) je `map<key_type, value_type>` typ. Tato část ukazuje, jak deklarovat `map` typ v Protobuf a jak použít generovaný kód.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

Ve vygenerovaném kódu `map` jsou pole reprezentována vlastnostmi typu, který je jen pro čtení [`Google.Protobuf.Collections.MapField<TKey, TValue>`][map-field] . Tento typ implementuje standardní rozhraní kolekce .NET, včetně <xref:System.Collections.Generic.IDictionary%602> .

Pole mapování nelze přímo zopakovat v definici zprávy. Můžete ale vytvořit vnořenou zprávu obsahující mapu a použít `repeated` ji jako typ zprávy, jak je uvedeno v následujícím příkladu:

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>Použití vlastností MapField v kódu

`MapField`Vlastnosti generované z `map` polí jsou jen pro čtení a nikdy nebudou `null` . Chcete-li nastavit vlastnost mapy, použijte k `Add(IDictionary<TKey,TValue> values)` `MapField` Kopírování hodnot z libovolného slovníku .NET metodu pro vlastnost Empty.

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a>Další materiály

Další informace o Protobuf najdete v oficiální [dokumentaci k Protobuf](https://developers.google.com/protocol-buffers/docs/overview).

[map-field]: https://developers.google.cn/protocol-buffers/docs/reference/csharp/class/google/protobuf/collections/map-field-t-key-t-value-

>[!div class="step-by-step"]
>[Předchozí](protobuf-enums.md) 
> [Další](wcf-services-to-grpc-comparison.md)
