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
# <a name="protobuf-reserved-fields"></a>Vyhrazená pole protobuf

Záruky zpětné kompatibility Protobuf spoléhají na čísla polí, která vždy představují stejnou datovou položku. Pokud se pole odebere ze zprávy v nové verzi služby, toto číslo pole by se nikdy nepoužilo. To je možné vyhovět pomocí klíčového slova `reserved`. Pokud se pole `displayName` a `marketId` odebrala ze zprávy `Stock` definované dříve, jejich čísla polí by měla být vyhrazena jako v následujícím příkladu.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

Klíčové slovo `reserved` lze také použít jako zástupný text pro pole, která mohou být v budoucnu přidána. Souvislá čísla polí lze vyjádřit jako rozsah pomocí klíčového slova `to`.

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[Předchozí](protobuf-repeated.md)
>[Další](protobuf-any-oneof.md)
