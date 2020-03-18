---
title: Vyrovnávací paměti protokolu - gRPC pro vývojáře WCF
description: Úvod do drátového formátu Protocol Buffers používaného pro sítě gRPC.
ms.date: 09/09/2019
ms.openlocfilehash: 35319d299a8bc2866a87954b3e54bfda9314ffe8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147929"
---
# <a name="protocol-buffers"></a>Vyrovnávací paměti protokolu

gRPC služby odesílat a přijímat data jako *protokol buffer (Protobuf) zprávy*, podobně jako datové smlouvy v Systému Windows Communication Foundation (WCF). Protobuf je efektivní způsob serializace strukturovaných dat pro počítače ke čtení a zápisu, bez režie, které člověk čitelné formáty jako XML nebo JSON vzniknou.

Tato kapitola popisuje, jak Protobuf funguje a jak definovat vlastní zprávy Protobuf.

## <a name="how-protobuf-works"></a>Jak přípravek Protobuf působí

Většina technik serializace objektů .NET, včetně kontraktů dat WCF, pracuje pomocí reflexe k analýze struktury objektu za běhu. Naproti tomu většina knihoven Protobuf vyžaduje, abyste definovali strukturu předem pomocí vyhrazeného jazyka (*Jazyk vyrovnávací paměti protokolu*) v souboru. `.proto` Kompilátor pak používá tento soubor ke generování kódu pro některou z podporovaných platforem. Mezi podporované platformy patří .NET, Java, C/C++, JavaScript a mnoho dalších.

Kompilátor Protobuf `protoc`, je spravován společností Google, i když jsou k dispozici alternativní implementace. Generovaný kód je efektivní a optimalizovaný pro rychlou serializaci a deserializaci dat.

Formát drátu Protobuf je binární kódování. Používá některé chytré triky, aby se minimalizoval počet bajtů používaných k reprezentaci zpráv. Znalost binárního formátu kódování není nutné používat Protobuf. Ale pokud máte zájem, můžete se dozvědět více o tom na [webových stránkách protocol buffers](https://developers.google.com/protocol-buffers/docs/encoding).

>[!div class="step-by-step"]
>[Předchozí](why-grpc.md)
>[další](protobuf-messages.md)
