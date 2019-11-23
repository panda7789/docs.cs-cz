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
