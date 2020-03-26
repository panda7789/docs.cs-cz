---
title: Reserved pole Protobuf - gRPC pro vývojáře WCF
description: Informace o vyhrazených polích pro kompatibilitu mezi verzemi.
ms.date: 09/09/2019
ms.openlocfilehash: f89513c4659a02cbc94e1c659baecb9e750acbdc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111033"
---
# <a name="protobuf-reserved-fields"></a><span data-ttu-id="0f723-103">Vyhrazená pole protobuf</span><span class="sxs-lookup"><span data-stu-id="0f723-103">Protobuf reserved fields</span></span>

<span data-ttu-id="0f723-104">Záruky zpětné kompatibility v protokolu Buffer (Protobuf) spoléhají na čísla polí vždy představující stejnou datovou položku.</span><span class="sxs-lookup"><span data-stu-id="0f723-104">The backward-compatibility guarantees in Protocol Buffer (Protobuf) rely on field numbers always representing the same data item.</span></span> <span data-ttu-id="0f723-105">Pokud je pole odebráno ze zprávy v nové verzi služby, toto číslo pole by nikdy nemělo být znovu použito.</span><span class="sxs-lookup"><span data-stu-id="0f723-105">If a field is removed from a message in a new version of the service, that field number should never be reused.</span></span> <span data-ttu-id="0f723-106">Můžete vynutit pomocí `reserved` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="0f723-106">You can enforce this by using the `reserved` keyword.</span></span>

<span data-ttu-id="0f723-107">Pokud `displayName` pole `marketId` a byla `Stock` odebrána ze zprávy definované dříve, jejich čísla polí by měla být rezervována jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0f723-107">If the `displayName` and `marketId` fields were removed from the `Stock` message defined earlier, their field numbers should be reserved as in the following example.</span></span>

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

<span data-ttu-id="0f723-108">`reserved` Klíčové slovo můžete také použít jako zástupný symbol pro pole, která mohou být přidána v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="0f723-108">You can also use the `reserved` keyword as a placeholder for fields that might be added in the future.</span></span> <span data-ttu-id="0f723-109">Souvislá čísla polí můžete vyjádřit jako oblast `to` pomocí klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="0f723-109">You can express contiguous field numbers as a range by using the `to` keyword.</span></span>

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
><span data-ttu-id="0f723-110">[Předchozí](protobuf-repeated.md)
>[další](protobuf-any-oneof.md)</span><span class="sxs-lookup"><span data-stu-id="0f723-110">[Previous](protobuf-repeated.md)
[Next](protobuf-any-oneof.md)</span></span>
