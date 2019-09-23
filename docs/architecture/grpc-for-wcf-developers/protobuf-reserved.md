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
# <a name="protobuf-reserved-fields"></a>Protobuf vyhrazená pole

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Záruky zpětné kompatibility Protobuf spoléhají na čísla polí, která vždy představují stejnou datovou položku. Pokud se pole odebere ze zprávy v nové verzi služby, toto číslo pole by se nikdy nepoužilo. To je možné vyhovět pomocí `reserved` klíčového slova. Pokud byla `marketId` pole a odebrána ze zprávy definované dříve, jejich čísla polí by měla být vyhrazena jako v následujícím příkladu. `Stock` `displayName`

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

`reserved` Klíčové slovo lze použít také jako zástupný text pro pole, která mohou být v budoucnu přidána. Souvislá čísla polí lze vyjádřit jako rozsah pomocí `to` klíčového slova.

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
