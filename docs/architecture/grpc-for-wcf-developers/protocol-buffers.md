---
title: Vyrovnávací paměti protokolu – gRPC pro vývojáře WCF
description: Seznámení s formátem přenosu vyrovnávací paměti protokolu používaného pro gRPC sítě.
author: markrendle
ms.date: 09/09/2019
ms.openlocfilehash: 6b47c7f3576134d8ee44f79e329cc4879661e6c3
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846303"
---
# <a name="protocol-buffers"></a>Vyrovnávací paměti protokolu

gRPC Services odesílají a přijímají zprávy o datech jako *vyrovnávací paměť protokolu (Protobuf)* , podobně jako kontrakty dat WCF. Protobuf je efektivní způsob serializace strukturovaných dat pro počítače ke čtení a zápisu bez režie, kterou uživatelsky čitelné formáty, jako je například XML nebo JSON, neúčtují.

Tato kapitola popisuje, jak Protobuf funguje, a jak definovat vlastní zprávy Protobuf.

## <a name="how-protobuf-works"></a>Jak funguje Protobuf

Většina metod serializace objektů rozhraní .NET, včetně kontraktů dat WCF, funguje pomocí reflexe k analýze struktury objektů za běhu. Naproti tomu většina Protobuf knihoven vyžaduje, abyste v souboru `.proto` definovali strukturu předem pomocí vyhrazeného jazyka (pro*vyrovnávací paměť protokolu*). Tento soubor je poté používán kompilátorem k vygenerování kódu pro libovolnou z podporovaných platforem, včetně .NET, Java, C/C++, JavaScriptu a spousty dalších. Kompilátor Protobuf, `protoc`, je udržován v Google, i když jsou k dispozici alternativní implementace. Generovaný kód je efektivní a optimalizovaný pro rychlou serializaci a deserializaci dat.

Samotný formát Protobuf kabelu je binární kódování, které používá některé chytřejší štychy k minimalizaci počtu bajtů používaných k reprezentování zpráv. Znalost binárního formátu kódování není nutná k používání Protobuf, ale pokud vás zajímá, můžete o něm získat další informace na webu [vyrovnávací paměti protokolu](https://developers.google.com/protocol-buffers/docs/encoding).

>[!div class="step-by-step"]
>[Předchozí](why-grpc.md)
>[Další](protobuf-messages.md)
