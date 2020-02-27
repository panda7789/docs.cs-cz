---
title: Síťové protokoly – gRPC pro vývojáře WCF
description: Přehled síťových protokolů gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 1ceb140f7b7ac7e796a87612ebb9d21e28d33968
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628485"
---
# <a name="network-protocols"></a>Síťové protokoly

Na rozdíl od Windows Communication Foundation (WCF) používá gRPC jako základ pro svou síť protokol HTTP/2. To nabízí významné výhody oproti WCF a protokolu SOAP, které fungují pouze na HTTP/1.1. Pro vývojáře, kteří chtějí používat gRPC, se vzhledem k tomu, že neexistuje žádná alternativa k HTTP/2, by to bylo ideální okamžik pro prozkoumání HTTP/2 podrobněji a určení dalších výhod používání gRPC.

Protokol HTTP/2 vydaný internetovou úlohou vysílaný v 2015 byl odvozený od experimentálního protokolu SPDY, který už používá Google. Konkrétně je navržený tak, aby byl efektivnější, rychlejší a bezpečnější než HTTP/1.1.

## <a name="key-features-of-http2"></a>Klíčové funkce HTTP/2

Tento seznam obsahuje některé klíčové funkce a výhody protokolu HTTP/2:

### <a name="binary-protocol"></a>Binární protokol

Cykly požadavků a odpovědí již nepotřebují textové příkazy. Tím se zjednoduší a urychlí implementace příkazů. Konkrétně analýza dat je rychlejší a používá méně paměti, latence sítě se zkracuje se zjevně souvisejícími vylepšeními rychlosti a existuje celkové lepší využití síťových prostředků.

### <a name="streams"></a>Datové proudy

Streamy umožňují vytvářet dlouhodobá připojení mezi odesílatelem a příjemcem, přes který se dá asynchronně odeslat víc zpráv nebo rámců. Více datových proudů může pracovat nezávisle na jednom připojení HTTP/2.

### <a name="request-multiplexing-over-a-single-tcp-connection"></a>Vyžádat multiplexování přes jedno připojení TCP

Tato funkce je jednou z nejdůležitějších inovací HTTP/2. Vzhledem k tomu, že umožňuje více paralelních požadavků na data, je nyní možné stahovat webové soubory souběžně z jednoho serveru. Websites se rychleji načítají a nutnost optimalizace se zkrátí. Blokové blokování (HOL), ve kterém musí být připravené odpovědi čekat, dokud nebude dokončena předchozí žádost, dojde také k omezení (i když se na úrovni protokolu TCP-Transport stále může vyskytovat).

### <a name="nettcp-like-performance-cross-platform"></a>Výkon typu NET. TCP, platforma pro různé platformy

V podstatě kombinace gRPC a HTTP/2 nabízí vývojářům přinejmenším ekvivalentní rychlost a efektivitu vazeb NET. TCP pro WCF a v některých případech i větší rychlost a efektivitu. Ale na rozdíl od NET. TCP, gRPC přes HTTP/2 není omezený na aplikace .NET.

>[!div class="step-by-step"]
>[Předchozí](interface-definition-language.md)
>[Další](why-grpc.md)
