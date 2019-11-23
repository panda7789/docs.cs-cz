---
title: Protobuf Maps for slovníks – gRPC pro vývojáře WCF
description: Seznamte se s použitím Protobuf Maps k vyjádření. Typy slovníků netto.
ms.date: 09/09/2019
ms.openlocfilehash: 8b4f29daa263f329dc533d3ddc596d0f47c1b6e0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967417"
---
# <a name="protobuf-maps-for-dictionaries"></a>Mapování protobuf pro slovníky

Je důležité, aby bylo možné vyjádřit libovolné kolekce pojmenovaných hodnot ve zprávách. V rozhraní .NET to se běžně zpracovává pomocí typů slovníků. Protobuf ekvivalentem typu .NET <xref:System.Collections.Generic.IDictionary%602> je `map<key_type, value_type>` typ. V této části se dozvíte, jak deklarovat `map` v Protobuf a jak používat generovaný kód.

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

Ve vygenerovaném kódu `map` pole používají třídu `Google.Protobuf.Collections.MapField<TKey, TValue>`, která implementuje standardní rozhraní kolekce .NET, včetně <xref:System.Collections.Generic.IDictionary%602>.

Pole mapování nelze přímo zopakovat v definici zprávy, ale můžete vytvořit vnořenou zprávu obsahující mapu a použít `repeated` pro typ zprávy, jako v následujícím příkladu:

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
