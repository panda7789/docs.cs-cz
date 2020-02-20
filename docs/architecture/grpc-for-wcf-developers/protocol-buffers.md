---
title: Vyrovnávací paměti protokolu – gRPC pro vývojáře WCF
description: Seznámení s formátem přenosu vyrovnávací paměti protokolu používaného pro gRPC sítě.
ms.date: 09/09/2019
ms.openlocfilehash: cc4ff272a9912d6f2dd8f8ddb1972c7369f980fe
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503452"
---
# <a name="protocol-buffers"></a>Vyrovnávací paměti protokolu

gRPC Services odesílají a přijímají zprávy o datech jako *vyrovnávací paměť protokolu (Protobuf)* , podobně jako kontrakty dat v Windows Communication Foundation (WCF). Protobuf je efektivní způsob serializace strukturovaných dat pro počítače ke čtení a zápisu bez režie, kterou uživatelsky čitelné formáty, jako je například XML nebo JSON, neúčtují.

Tato kapitola popisuje, jak Protobuf funguje, a jak definovat vlastní zprávy Protobuf.

## <a name="how-protobuf-works"></a>Jak funguje Protobuf

Většina metod serializace objektů rozhraní .NET, včetně kontraktů dat WCF, funguje pomocí reflexe k analýze struktury objektů za běhu. Naproti tomu většina Protobuf knihoven vyžaduje, abyste definovali strukturu předem pomocí vyhrazeného jazyka (*jazyk vyrovnávací paměti protokolu*) v souboru `.proto`. Kompilátor potom pomocí tohoto souboru vygeneruje kód pro libovolnou z podporovaných platforem. Mezi podporované platformy patří .NET, Java, CC++/, JavaScript a spousta dalších. 

Kompilátor Protobuf, `protoc`, je udržován v Google, i když jsou k dispozici alternativní implementace. Generovaný kód je efektivní a optimalizovaný pro rychlou serializaci a deserializaci dat.

Formát Protobuf drátu je binární kódování. K minimalizaci počtu bajtů použitých k reprezentování zpráv používá některé chytřejší triky. Znalost formátu binárního kódování není nutná k použití Protobuf. Pokud vás ale zajímá, můžete o něm získat další informace na [webu vyrovnávací paměti protokolu](https://developers.google.com/protocol-buffers/docs/encoding).

>[!div class="step-by-step"]
>[Předchozí](why-grpc.md)
>[Další](protobuf-messages.md)
