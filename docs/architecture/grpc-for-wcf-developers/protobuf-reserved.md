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
# <a name="protobuf-reserved-fields"></a>Vyhrazená pole protobuf

Záruky zpětné kompatibility ve vyrovnávací paměti protokolu (Protobuf) spoléhají na čísla polí, vždy představují stejnou datovou položku. Pokud se pole odebere ze zprávy v nové verzi služby, toto číslo pole by se nikdy nepoužilo. Můžete to enfore pomocí klíčového slova `reserved`. 

Pokud se pole `displayName` a `marketId` odebrala ze zprávy `Stock` definované dříve, jejich čísla polí by měla být vyhrazena jako v následujícím příkladu.

```protobuf
syntax "proto3";

message Stock {

    reserved 3, 4;
    int32 id = 1;
    string symbol = 2;

}
```

Klíčové slovo `reserved` můžete použít také jako zástupný symbol pro pole, která mohou být v budoucnu přidána. Souvislá čísla polí můžete vyjádřit jako rozsah pomocí klíčového slova `to`.

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
