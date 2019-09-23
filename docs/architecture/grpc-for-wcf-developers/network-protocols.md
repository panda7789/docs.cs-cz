---
title: Síťové protokoly – gRPC pro vývojáře WCF
description: Přehled síťových protokolů gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: a176d3e84f5f454f746273c9cc7e7afe7c7f9d8a
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184286"
---
# <a name="network-protocols"></a>Síťové protokoly

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Na rozdíl od služby WCF používá gRPC jako základ pro svou síť protokol HTTP/2. To nabízí významné výhody oproti WCF a protokolu SOAP, které pracují pouze s HTTP/1.1. Pro vývojáře, kteří chtějí používat gRPC, se vzhledem k tomu, že neexistuje žádná alternativa k HTTP/2, by to bylo ideální okamžik pro prozkoumání HTTP/2 podrobněji a určení dalších výhod používání gRPC.

Protokol HTTP/2 vydaný internetovou úlohou vysílaný v 2015 byl odvozený od experimentálního protokolu SPDY, který už používá Google. Konkrétně je navržený tak, aby byl efektivnější, rychlejší a bezpečnější než HTTP/1.1.

## <a name="key-features-of-http2"></a>Klíčové funkce HTTP/2

Následující seznam uvádí některé klíčové funkce a výhody protokolu HTTP/2:

### <a name="binary-protocol"></a>Binární protokol

Cykly požadavků a odpovědí již nepotřebují textové příkazy. Tím se zjednoduší a urychlí implementace příkazů. Konkrétně analýza dat je rychlejší a používá méně paměti, latence sítě se zkracuje se zjevně souvisejícími vylepšeními rychlosti a existuje celkové lepší využití síťových prostředků.

### <a name="streams"></a>Datové proudy

Streamy umožňují vytvářet dlouhodobá připojení mezi odesílatelem a příjemcem, přes který se dá asynchronně odeslat víc zpráv nebo rámců. Více datových proudů může pracovat nezávisle na jednom připojení HTTP/2.

### <a name="request-multiplexing-over-a-single-tcp-connection"></a>Vyžádat multiplexování přes jedno připojení TCP

Tato funkce je jednou z nejdůležitějších inovací HTTP/2. Když povolíte více paralelních požadavků na data, je teď možné stahovat webové soubory souběžně z jednoho serveru. Websites se rychleji načítají a nutnost optimalizace se zkrátí. Blokování na konci řádku (HOL), kde musí být připravené odpovědi čekat, dokud nebude dokončena předchozí žádost, dojde také k omezení (i když se na úrovni transportu TCP stále může vyskytovat).

### <a name="nettcp-like-performance-cross-platform"></a>NetTCP jako výkon, více platforem

V podstatě kombinace gRPC a HTTP/2 nabízí vývojářům alespoň ekvivalentní rychlost a efektivitu vazeb NetTCP pro WCF a v některých případech i větší rychlost a efektivitu. Nicméně na rozdíl od NetTCP se gRPC přes HTTP/2 neomezuje na aplikace .NET.

>[!div class="step-by-step"]
>[Předchozí](interface-definition-language.md)
>[Další](why-grpc.md)
