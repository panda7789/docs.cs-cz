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
# <a name="protobuf-reserved-fields"></a>Vyhrazená pole protobuf

Záruky zpětné kompatibility v protokolu Buffer (Protobuf) spoléhají na čísla polí vždy představující stejnou datovou položku. Pokud je pole odebráno ze zprávy v nové verzi služby, toto číslo pole by nikdy nemělo být znovu použito. Můžete vynutit pomocí `reserved` klíčového slova.

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
