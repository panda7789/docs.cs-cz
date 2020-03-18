---
title: Proč doporučujeme gRPC pro vývojáře WCF - gRPC pro vývojáře WCF
description: Diskuse o tom, proč gRPC je vhodný pro vývojáře WCF, kteří chtějí migrovat na moderní architektury a platformy.
ms.date: 09/02/2019
ms.openlocfilehash: 664781e94c24c1796eafa6a70eb28d453b530d66
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147643"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a>Proč doporučujeme gRPC pro vývojáře WCF

Než se ponoříme hluboko do jazyka a technik gRPC, stojí za to diskutovat o tom, proč je gRPC tím správným řešením pro vývojáře Windows Communication Foundation (WCF), kteří chtějí migrovat do .NET Core.

## <a name="similarity-to-wcf"></a>Podobnost s WCF

Přestože implementace a přístup se liší pro gRPC, zkušenosti s vývojem a využívání služeb s gRPC by měly být intuitivní pro vývojáře WCF. Základní cíl je stejný: aby bylo možné kódovat, jako by klient a server jsou na stejné platformě, aniž by se museli starat o vytváření sítí.

Obě platformy sdílejí princip deklarování a následné implementace rozhraní, i když proces pro deklarování tohoto rozhraní se liší. A jak uvidíte v kapitole 5, různé typy volání Vzdáleného volání, které gRPC podporuje mapování dobře na vazby, které jsou k dispozici pro služby WCF.

## <a name="benefits-of-grpc"></a>Výhody gRPC

gRPC stojí nad jinými řešeními z následujících důvodů.

### <a name="performance"></a>Výkon

Použití HTTP/2 spíše než HTTP/1.1 odstraní požadavek na zprávy čitelné pro člověka a místo toho používá menší, rychlejší binární protokol. To je efektivnější pro počítače analyzovat. HTTP/2 také podporuje multiplexní požadavky přes jedno připojení. Tato podpora umožňuje odpovědi, které mají být odeslány, jakmile jsou připraveny bez nutnosti čekat ve frontě. (V protokolu HTTP/1.1 se tento problém označuje jako "head-of-line (HOL) blokování.") Při používání gRPC potřebujete méně prostředků, což z něj činí dobré řešení pro použití pro mobilní zařízení a přes pomalejší sítě.

### <a name="interoperability"></a>Vzájemná funkční spolupráce

Existují gRPC nástroje a knihovny pro všechny hlavní programovací jazyky a platformy, včetně .NET, Java, Python, Go, C++, Node.js, Swift, Dart, Ruby a PHP. Díky binárnímu drátu protokolu Buffers a efektivnímu generování kódu pro každou platformu mohou vývojáři vytvářet výkonné aplikace a zároveň využívat plnou podporu napříč platformami.

### <a name="usability-and-productivity"></a>Použitelnost a produktivita

gRPC je komplexní RPC řešení. Funguje konzistentně napříč různými jazyky a platformami. Poskytuje také vynikající nástroje, s velkou část potřebného často používaného kódu automaticky generovány. Takže více času pro vývojáře je uvolněno, abyste se mohli soustředit na obchodní logiku.

### <a name="streaming"></a>Streamování

gRPC má úplné obousměrné streamování, které poskytuje podobné funkce jako plně duplexní služby WCF. gRPC streaming může pracovat přes běžné připojení k internetu, vyrovnávání zatížení a sítě služby.

### <a name="deadlinetimeouts-and-cancellation"></a>Termíny/časové lhůty a zrušení

gRPC umožňuje klientům určit maximální dobu dokončení vzdáleného volání procedur. Pokud je překročen zadaný konečný termín, server může zrušit operaci nezávisle na klientovi. Termíny a zrušení lze šířit prostřednictvím dalších volání gRPC pomoci vynutit omezení využití prostředků. Klienti mohou také zastavit operace při překročení konečného termínu nebo dříve, pokud je to nutné (například z důvodu interakce s uživatelem).

### <a name="security"></a>Zabezpečení

gRPC je implicitně bezpečný, když používá HTTP/2 přes šifrované připojení TLS end-to-end. Podpora ověřování klientských certifikátů (viz [kapitola 6)](security.md)dále zvyšuje zabezpečení a důvěryhodnost mezi klientem a serverem.

>[!div class="step-by-step"]
>[Předchozí](network-protocols.md)
>[další](protocol-buffers.md)
