---
title: Proč doporučujeme gRPC pro vývojáře WCF – gRPC pro vývojáře WCF
description: Diskuzi o tom, proč je gRPC vhodná pro vývojáře WCF, kteří chtějí migrovat na moderní architektury a platformy.
ms.date: 09/02/2019
ms.openlocfilehash: fc93ca4c8f2a28dc4d3a0b0466d19c86273b40b8
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503320"
---
# <a name="why-we-recommend-grpc-for-wcf-developers"></a>Proč doporučujeme gRPC pro vývojáře WCF

Předtím, než jsme podrobněi do jazyka a technik gRPC, je vhodné pojednávat o tom, proč je gRPC správným řešením pro vývojáře Windows Communication Foundation (WCF), kteří chtějí migrovat na .NET Core.

## <a name="similarity-to-wcf"></a>Podobnost k WCF

I když je implementace a přístup odlišná pro gRPC, možnosti vývoje a využívání služeb s gRPC by měly být intuitivní pro vývojáře WCF. Základní cíl je stejný: umožňuje psaní kódu, jako by klient a server byly na stejné platformě, aniž by se museli starat o sítě. 

Obě platformy sdílí princip deklarování a následné implementace rozhraní, a to i v případě, že proces pro deklarování tohoto rozhraní je jiný. A jak vidíte v kapitole 5, různé typy volání RPC, které gRPC podporuje, jsou dobře mapované na vazby, které jsou k dispozici pro služby WCF.

## <a name="benefits-of-grpc"></a>Výhody gRPC

gRPC představuje další řešení z následujících důvodů.

### <a name="performance"></a>Výkon

Použití HTTP/2 místo HTTP/1.1 odstraní požadavek na zprávy čitelné pro čtení a místo toho používá menší, rychlejší binární protokol. To je efektivnější pro počítače k analýze. HTTP/2 také podporuje multiplexování požadavků v rámci jednoho připojení. Tato podpora umožňuje odeslat odpovědi ihned po jejich přípravě, aniž by bylo nutné čekat ve frontě. (V HTTP/1.1 se tento problém označuje jako "blokování na konci řádku (HOL)") Při použití gRPC potřebujete méně prostředků, díky čemuž je vhodné řešení používat pro mobilní zařízení a pomalejší sítě.

### <a name="interoperability"></a>Vzájemná funkční spolupráce

K dispozici jsou nástroje a knihovny gRPC pro všechny hlavní programovací jazyky a platformy, včetně .NET, Java, Python, C++cestách, Node. js, SWIFT, DART, Ruby a php. Díky ukládání binárních přenosů do vyrovnávací paměti protokolů a efektivní generování kódu pro každou platformu můžou vývojáři vytvářet výkonné aplikace a pořád využívat plnou podporu pro víc platforem.

### <a name="usability-and-productivity"></a>Použitelnost a produktivita

gRPC je komplexní řešení RPC. Funguje konzistentně napříč různými jazyky a platformami. Nabízí také skvělé nástroje, které jsou automaticky vygenerovány z mnoha nezbytných často vygenerovaných kódů. Proto je pro obchodní logiku zdarma Zaměřte se na více vývojářských časů.

### <a name="streaming"></a>Streamování

gRPC má plný obousměrný Stream, který poskytuje podobné funkce jako plně duplexní služby WCF. gRPC streaming může pracovat přes běžná připojení k Internetu, nástroje pro vyrovnávání zatížení a sítě.

### <a name="deadlinetimeouts-and-cancellation"></a>Konečný termín, vypršení časového limitu a zrušení

gRPC umožňuje klientům zadat maximální dobu, po kterou se RPC bude dokončit. Pokud je překročen zadaný konečný termín, server může operaci zrušit nezávisle na klientovi. Termíny a zrušení lze rozšířit prostřednictvím dalších volání gRPC, která vám pomůžou vyhodnotit omezení využití prostředků. Klienti mohou také zastavit operace při překročení konečného termínu nebo dříve, pokud je to nutné (například kvůli interakci uživatele).

### <a name="security"></a>Zabezpečení

gRPC je implicitně zabezpečená, pokud používá protokol HTTP/2 přes komplexní šifrované připojení TLS. Podpora ověřování klientského certifikátu (viz [Kapitola 6](security.md)) dále zvyšuje zabezpečení a důvěryhodnost mezi klientem a serverem.

>[!div class="step-by-step"]
>[Předchozí](network-protocols.md)
>[Další](protocol-buffers.md)
