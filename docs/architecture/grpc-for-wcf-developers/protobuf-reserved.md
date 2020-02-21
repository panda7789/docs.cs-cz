---
title: Protobuf vyhrazená pole – gRPC pro vývojáře WCF
description: Přečtěte si o vyhrazených polích pro kompatibilitu mezi verzemi.
ms.date: 09/09/2019
ms.openlocfilehash: 50082a1aab2e7707a1839b9d56455124a9e4a6a1
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77542973"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="aa20c-103">Vyhrazená pole protobuf</span><span class="sxs-lookup"><span data-stu-id="aa20c-103">Protobuf reserved fields</span></span>

<span data-ttu-id="aa20c-104">Záruky zpětné kompatibility ve vyrovnávací paměti protokolu (Protobuf) spoléhají na čísla polí, vždy představují stejnou datovou položku.</span><span class="sxs-lookup"><span data-stu-id="aa20c-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="aa20c-105">Pokud se pole odebere ze zprávy v nové verzi služby, toto číslo pole by se nikdy nepoužilo.</span><span class="sxs-lookup"><span data-stu-id="aa20c-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="aa20c-106">Můžete to enfore pomocí klíčového slova `reserved`.</span><span class="sxs-lookup"><span data-stu-id="aa20c-106">You can enfore this by using the `reserved` keyword.</span></span> 

<span data-ttu-id="aa20c-107">Pokud se pole `displayName` a `marketId` odebrala ze zprávy `Stock` definované dříve, jejich čísla polí by měla být vyhrazena jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="aa20c-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="aa20c-108">Klíčové slovo `reserved` můžete použít také jako zástupný symbol pro pole, která mohou být v budoucnu přidána.</span><span class="sxs-lookup"><span data-stu-id="aa20c-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="aa20c-109">Souvislá čísla polí můžete vyjádřit jako rozsah pomocí klíčového slova `to`.</span><span class="sxs-lookup"><span data-stu-id="aa20c-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="aa20c-110">[Předchozí](protobuf-repeated.md)
>[Další](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="aa20c-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
