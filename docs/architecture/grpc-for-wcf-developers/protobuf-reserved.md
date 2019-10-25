---
title: Protobuf vyhrazená pole – gRPC pro vývojáře WCF
description: Přečtěte si o vyhrazených polích pro kompatibilitu mezi verzemi.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 34697371299bdc5d9a58c0696c1ce7d19816ca87
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846328"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="62ca4-103">Vyhrazená pole protobuf</span><span class="sxs-lookup"><span data-stu-id="62ca4-103">Protobuf reserved fields</span></span>

<span data-ttu-id="62ca4-104">Záruky zpětné kompatibility Protobuf spoléhají na čísla polí, která vždy představují stejnou datovou položku.</span><span class="sxs-lookup"><span data-stu-id="62ca4-104">Protobuf's backward-compatibility guarantees rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="62ca4-105">Pokud se pole odebere ze zprávy v nové verzi služby, toto číslo pole by se nikdy nepoužilo.</span><span class="sxs-lookup"><span data-stu-id="62ca4-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="62ca4-106">To je možné vyhovět pomocí klíčového slova `reserved`.</span><span class="sxs-lookup"><span data-stu-id="62ca4-106">This can be enforced using the `reserved` keyword.</span></span> <span data-ttu-id="62ca4-107">Pokud se pole `displayName` a `marketId` odebrala ze zprávy `Stock` definované dříve, jejich čísla polí by měla být vyhrazena jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="62ca4-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="62ca4-108">Klíčové slovo `reserved` lze také použít jako zástupný text pro pole, která mohou být v budoucnu přidána.</span><span class="sxs-lookup"><span data-stu-id="62ca4-108">The `reserved` keyword can also be used as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="62ca4-109">Souvislá čísla polí lze vyjádřit jako rozsah pomocí klíčového slova `to`.</span><span class="sxs-lookup"><span data-stu-id="62ca4-109">Contiguous field numbers can be expressed as a range using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="62ca4-110">[Předchozí](protobuf-repeated.md)
>[Další](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="62ca4-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
