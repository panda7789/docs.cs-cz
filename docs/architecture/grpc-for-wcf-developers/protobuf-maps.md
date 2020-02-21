---
title: Protobuf Maps for slovníks – gRPC pro vývojáře WCF
description: Naučte se používat mapy Protobuf k reprezentování typů slovníků v .NET.
ms.date: 09/09/2019
ms.openlocfilehash: bf848bbc7e3618f6d78e280fcd85d5eb88d5cfae
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543128"
---
# <a name="protobuf-maps-for-dictionaries"></a>Mapování protobuf pro slovníky

Je důležité, aby bylo možné vyjádřit libovolné kolekce pojmenovaných hodnot ve zprávách. V rozhraní .NET se to obvykle zpracovává prostřednictvím typů slovníků. Ekvivalentem typu <xref:System.Collections.Generic.IDictionary%602> .NET v vyrovnávací paměti protokolu (Protobuf) je typ `map<key_type, value_type>`. V této části se dozvíte, jak deklarovat `map` typ v Protobuf a jak použít generovaný kód.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

V generovaném kódu `map` pole používají třídu `Google.Protobuf.Collections.MapField<TKey, TValue>`. Tato třída implementuje standardní rozhraní kolekce .NET, včetně <xref:System.Collections.Generic.IDictionary%602>.

Pole mapování nelze přímo zopakovat v definici zprávy. Můžete ale vytvořit vnořenou zprávu obsahující mapu a použít `repeated` pro typ zprávy, jako v následujícím příkladu:

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a>Použití vlastností MapField v kódu

Vlastnosti `MapField` generované z polí `map` jsou jen pro čtení a nikdy nebudou `null`. Chcete-li nastavit vlastnost mapy, použijte k zkopírování hodnot z libovolného slovníku .NET metodu `Add(IDictionary<TKey,TValue> values)` pro prázdnou vlastnost `MapField`.

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
