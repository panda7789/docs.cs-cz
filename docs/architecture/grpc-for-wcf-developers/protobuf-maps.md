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
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="f751e-103">Mapování protobuf pro slovníky</span><span class="sxs-lookup"><span data-stu-id="f751e-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="f751e-104">Je důležité, aby bylo možné vyjádřit libovolné kolekce pojmenovaných hodnot ve zprávách.</span><span class="sxs-lookup"><span data-stu-id="f751e-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="f751e-105">V rozhraní .NET to se běžně zpracovává pomocí typů slovníků.</span><span class="sxs-lookup"><span data-stu-id="f751e-105">In .NET this is commonly handled using dictionary types.</span></span> <span data-ttu-id="f751e-106">Protobuf ekvivalentem typu .NET <xref:System.Collections.Generic.IDictionary%602> je `map<key_type, value_type>` typ.</span><span class="sxs-lookup"><span data-stu-id="f751e-106">Protobuf's equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="f751e-107">V této části se dozvíte, jak deklarovat `map` v Protobuf a jak používat generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="f751e-107">This section shows how to declare a `map` in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="f751e-108">Ve vygenerovaném kódu `map` pole používají třídu `Google.Protobuf.Collections.MapField<TKey, TValue>`, která implementuje standardní rozhraní kolekce .NET, včetně <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="f751e-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class, which implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="f751e-109">Pole mapování nelze přímo zopakovat v definici zprávy, ale můžete vytvořit vnořenou zprávu obsahující mapu a použít `repeated` pro typ zprávy, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f751e-109">Map fields can't be directly repeated in a message definition, but you can create a nested message containing a map and use `repeated` on the message type, like in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="f751e-110">Použití vlastností MapField v kódu</span><span class="sxs-lookup"><span data-stu-id="f751e-110">Using MapField properties in code</span></span>

<span data-ttu-id="f751e-111">Vlastnosti `MapField` generované z polí `map` jsou jen pro čtení a nikdy nebudou `null`.</span><span class="sxs-lookup"><span data-stu-id="f751e-111">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="f751e-112">Chcete-li nastavit vlastnost mapy, použijte k zkopírování hodnot z libovolného slovníku .NET metodu `Add(IDictionary<TKey,TValue> values)` pro prázdnou vlastnost `MapField`.</span><span class="sxs-lookup"><span data-stu-id="f751e-112">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="f751e-113">Další čtení</span><span class="sxs-lookup"><span data-stu-id="f751e-113">Further reading</span></span>

<span data-ttu-id="f751e-114">Další informace o Protobuf najdete v oficiální [dokumentaci k Protobuf](https://developers.google.com/protocol-buffers/docs/overview).</span><span class="sxs-lookup"><span data-stu-id="f751e-114">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="f751e-115">[Předchozí](protobuf-enums.md)
>[Další](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="f751e-115">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
