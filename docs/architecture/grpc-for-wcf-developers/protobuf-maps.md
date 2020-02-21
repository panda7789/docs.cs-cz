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
# <a name="protobuf-maps-for-dictionaries"></a><span data-ttu-id="cb87f-103">Mapování protobuf pro slovníky</span><span class="sxs-lookup"><span data-stu-id="cb87f-103">Protobuf maps for dictionaries</span></span>

<span data-ttu-id="cb87f-104">Je důležité, aby bylo možné vyjádřit libovolné kolekce pojmenovaných hodnot ve zprávách.</span><span class="sxs-lookup"><span data-stu-id="cb87f-104">It's important to be able to represent arbitrary collections of named values in messages.</span></span> <span data-ttu-id="cb87f-105">V rozhraní .NET se to obvykle zpracovává prostřednictvím typů slovníků.</span><span class="sxs-lookup"><span data-stu-id="cb87f-105">In .NET, this is commonly handled through dictionary types.</span></span> <span data-ttu-id="cb87f-106">Ekvivalentem typu <xref:System.Collections.Generic.IDictionary%602> .NET v vyrovnávací paměti protokolu (Protobuf) je typ `map<key_type, value_type>`.</span><span class="sxs-lookup"><span data-stu-id="cb87f-106">The equivalent of the .NET <xref:System.Collections.Generic.IDictionary%602> type in Protocol Buffer (Protobuf) is the `map<key_type, value_type>` type.</span></span> <span data-ttu-id="cb87f-107">V této části se dozvíte, jak deklarovat `map` typ v Protobuf a jak použít generovaný kód.</span><span class="sxs-lookup"><span data-stu-id="cb87f-107">This section shows how to declare a `map` type in Protobuf, and how to use the generated code.</span></span>

```protobuf
message StockPrices {
    map<string, double> prices = 1;
}
```

<span data-ttu-id="cb87f-108">V generovaném kódu `map` pole používají třídu `Google.Protobuf.Collections.MapField<TKey, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="cb87f-108">In the generated code, `map` fields use the `Google.Protobuf.Collections.MapField<TKey, TValue>` class.</span></span> <span data-ttu-id="cb87f-109">Tato třída implementuje standardní rozhraní kolekce .NET, včetně <xref:System.Collections.Generic.IDictionary%602>.</span><span class="sxs-lookup"><span data-stu-id="cb87f-109">This class implements the standard .NET collection interfaces, including <xref:System.Collections.Generic.IDictionary%602>.</span></span>

<span data-ttu-id="cb87f-110">Pole mapování nelze přímo zopakovat v definici zprávy.</span><span class="sxs-lookup"><span data-stu-id="cb87f-110">Map fields can't be directly repeated in a message definition.</span></span> <span data-ttu-id="cb87f-111">Můžete ale vytvořit vnořenou zprávu obsahující mapu a použít `repeated` pro typ zprávy, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cb87f-111">But you can create a nested message that contains a map and use `repeated` on the message type, as in the following example:</span></span>

```protobuf
message Order {
    message Attributes {
        map<string, string> values = 1;
    }
    repeated Attributes attributes = 1;
}
```

## <a name="using-mapfield-properties-in-code"></a><span data-ttu-id="cb87f-112">Použití vlastností MapField v kódu</span><span class="sxs-lookup"><span data-stu-id="cb87f-112">Using MapField properties in code</span></span>

<span data-ttu-id="cb87f-113">Vlastnosti `MapField` generované z polí `map` jsou jen pro čtení a nikdy nebudou `null`.</span><span class="sxs-lookup"><span data-stu-id="cb87f-113">The `MapField` properties generated from `map` fields are read-only, and will never be `null`.</span></span> <span data-ttu-id="cb87f-114">Chcete-li nastavit vlastnost mapy, použijte k zkopírování hodnot z libovolného slovníku .NET metodu `Add(IDictionary<TKey,TValue> values)` pro prázdnou vlastnost `MapField`.</span><span class="sxs-lookup"><span data-stu-id="cb87f-114">To set a map property, use the `Add(IDictionary<TKey,TValue> values)` method on the empty `MapField` property to copy values from any .NET dictionary.</span></span>

```csharp
public Order CreateOrder(Dictionary<string, string> attributes)
{
    var order = new Order();
    order.Attributes.Add(attributes);
    return order;
}
```

## <a name="further-reading"></a><span data-ttu-id="cb87f-115">Další čtení</span><span class="sxs-lookup"><span data-stu-id="cb87f-115">Further reading</span></span>

<span data-ttu-id="cb87f-116">Další informace o Protobuf najdete v oficiální [dokumentaci k Protobuf](https://developers.google.com/protocol-buffers/docs/overview).</span><span class="sxs-lookup"><span data-stu-id="cb87f-116">For more information about Protobuf, see the official [Protobuf documentation](https://developers.google.com/protocol-buffers/docs/overview).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="cb87f-117">[Předchozí](protobuf-enums.md)
>[Další](wcf-services-to-grpc-comparison.md)</span><span class="sxs-lookup"><span data-stu-id="cb87f-117">[Previous](protobuf-enums.md)
[Next](wcf-services-to-grpc-comparison.md)</span></span>
