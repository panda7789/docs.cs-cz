---
title: Protobuf vyhrazená pole – gRPC pro vývojáře WCF
description: Přečtěte si o vyhrazených polích pro kompatibilitu mezi verzemi.
ms.date: 09/09/2019
ms.openlocfilehash: e589cd38a712ce014fa2c4d847fbde359d538dd0
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967303"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="2372c-103">Vyhrazená pole protobuf</span><span class="sxs-lookup"><span data-stu-id="2372c-103">Protobuf reserved fields</span></span>

<span data-ttu-id="2372c-104">Záruky zpětné kompatibility Protobuf spoléhají na čísla polí, která vždy představují stejnou datovou položku.</span><span class="sxs-lookup"><span data-stu-id="2372c-104">Protobuf's backward-compatibility guarantees rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="2372c-105">Pokud se pole odebere ze zprávy v nové verzi služby, toto číslo pole by se nikdy nepoužilo.</span><span class="sxs-lookup"><span data-stu-id="2372c-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="2372c-106">To je možné vyhovět pomocí klíčového slova `reserved`.</span><span class="sxs-lookup"><span data-stu-id="2372c-106">This can be enforced using the `reserved` keyword.</span></span> <span data-ttu-id="2372c-107">Pokud se pole `displayName` a `marketId` odebrala ze zprávy `Stock` definované dříve, jejich čísla polí by měla být vyhrazena jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2372c-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="2372c-108">Klíčové slovo `reserved` lze také použít jako zástupný text pro pole, která mohou být v budoucnu přidána.</span><span class="sxs-lookup"><span data-stu-id="2372c-108">The `reserved` keyword can also be used as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="2372c-109">Souvislá čísla polí lze vyjádřit jako rozsah pomocí klíčového slova `to`.</span><span class="sxs-lookup"><span data-stu-id="2372c-109">Contiguous field numbers can be expressed as a range using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="2372c-110">[Předchozí](protobuf-repeated.md)
>[Další](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="2372c-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
