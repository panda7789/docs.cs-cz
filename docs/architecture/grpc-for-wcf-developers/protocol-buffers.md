---
title: Vyrovnávací paměti protokolu – gRPC pro vývojáře WCF
description: Seznámení s formátem přenosu vyrovnávací paměti protokolu používaného pro gRPC sítě.
ms.date: 09/09/2019
ms.openlocfilehash: dbe8cb43475cfeec19051daf68452ef86269372f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967291"
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
