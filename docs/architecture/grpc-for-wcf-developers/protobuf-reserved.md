---
title: Reserved pole Protobuf - gRPC pro vývojáře WCF
description: Informace o vyhrazených polích pro kompatibilitu mezi verzemi.
ms.date: 09/09/2019
ms.openlocfilehash: bde658c671e970b7ec841d71d5b4284eb91195f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147942"
---
# <a name="protobuf-reserved-fields"></a>Vyhrazená pole protobuf

Záruky zpětné kompatibility v protokolu Buffer (Protobuf) spoléhají na čísla polí vždy představující stejnou datovou položku. Pokud je pole odebráno ze zprávy v nové verzi služby, toto číslo pole by nikdy nemělo být znovu použito. Můžete to enfore pomocí `reserved` klíčového slova.

Pokud `displayName` pole `marketId` a byla `Stock` odebrána ze zprávy definované dříve, jejich čísla polí by měla být rezervována jako v následujícím příkladu.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

`reserved` Klíčové slovo můžete také použít jako zástupný symbol pro pole, která mohou být přidána v budoucnu. Souvislá čísla polí můžete vyjádřit jako oblast `to` pomocí klíčového slova.

```protobuf
syntax "proto3";

message Info {

    reserved 2, 9 to 11, 15;
    // ...
}
```

>[!div class="step-by-step"]
>[Předchozí](protobuf-repeated.md)
>[další](protobuf-any-oneof.md)
