---
title: Protobuf vyhrazená pole – gRPC pro vývojáře WCF
description: Přečtěte si o vyhrazených polích pro kompatibilitu mezi verzemi.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: d4d40ca12d41ec37e0baebf10de9d0690e4297cc
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184174"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="d904b-103">Protobuf vyhrazená pole</span><span class="sxs-lookup"><span data-stu-id="d904b-103">Protobuf reserved fields</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="d904b-104">Záruky zpětné kompatibility Protobuf spoléhají na čísla polí, která vždy představují stejnou datovou položku.</span><span class="sxs-lookup"><span data-stu-id="d904b-104">Protobuf's backward-compatibility guarantees rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="d904b-105">Pokud se pole odebere ze zprávy v nové verzi služby, toto číslo pole by se nikdy nepoužilo.</span><span class="sxs-lookup"><span data-stu-id="d904b-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="d904b-106">To je možné vyhovět pomocí `reserved` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="d904b-106">This can be enforced using the `reserved` keyword.</span></span> <span data-ttu-id="d904b-107">Pokud byla `marketId` pole a odebrána ze zprávy definované dříve, jejich čísla polí by měla být vyhrazena jako v následujícím příkladu. `Stock` `displayName`</span><span class="sxs-lookup"><span data-stu-id="d904b-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="d904b-108">`reserved` Klíčové slovo lze použít také jako zástupný text pro pole, která mohou být v budoucnu přidána.</span><span class="sxs-lookup"><span data-stu-id="d904b-108">The `reserved` keyword can also be used as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="d904b-109">Souvislá čísla polí lze vyjádřit jako rozsah pomocí `to` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="d904b-109">Contiguous field numbers can be expressed as a range using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="d904b-110">[Předchozí](protobuf-repeated.md)
>[Další](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="d904b-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
