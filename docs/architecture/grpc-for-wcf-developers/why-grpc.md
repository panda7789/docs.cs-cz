---
title: Proč se gRPC doporučuje pro vývojáře WCF – gRPC pro vývojáře WCF
description: Diskuzi o tom, proč se gRPC hodí pro vývojáře WCF, kteří chtějí migrovat na moderní architektury a platformy.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7e80936eb36bbba92958c349b5f1c0cb389d6b8d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184034"
---
# <a name="why-grpc-is-recommended-for-wcf-developers"></a>Proč se doporučuje gRPC pro vývojáře WCF

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Předtím, než se začnete do jazyka a technik gRPC, je vhodné pojednávat o tom, proč je gRPC správným řešením pro vývojáře WCF, kteří chtějí migrovat na .NET Core, a to s ohledem na dostupné alternativy.

## <a name="similarity-to-wcf"></a>Podobnost k WCF

I když je jeho implementace a přístup odlišná, vlastní zkušenosti s vývojem a používáním služeb gRPC by měly být pro vývojáře WCF velmi intuitivní. Základní cíl, který umožňuje psaní kódu, jako kdyby byl klient a server na stejné platformě, nemuseli se starat o sítě. Obě platformy sdílí princip deklarování a následné implementace rozhraní, a to i v případě, že proces pro deklarování tohoto rozhraní je jiný. A jak uvidíte v kapitole 5, různé typy volání RPC, které podporuje mapa gRPC, velmi dobře na různé vazby, které jsou dostupné pro služby WCF.

## <a name="benefits-of-grpc"></a>Výhody gRPC

Další důvody, proč gRPC představuje více než další řešení:

### <a name="performance"></a>Výkon

Jak už bylo popsáno, použití HTTP/2 místo HTTP/1.1 odstraní požadavek na zprávy čitelné pro čtení a místo toho používá menší rychlejší binární protokol. To je efektivnější pro počítače k analýze. HTTP/2 podporuje také multiplexování požadavků přes jedno připojení, které umožňuje posílání odpovědí ihned po jejich dokončení, aniž by bylo nutné čekat ve frontě (problém v HTTP/1.1 se označuje jako "blokování na začátku řádku"). Při použití gRPC je potřeba mít méně prostředků, díky čemuž je vhodné řešení používat pro mobilní zařízení a pomalejší sítě.

### <a name="interoperability"></a>Interoperabilita

K dispozici jsou nástroje a knihovny gRPC pro všechny hlavní programovací jazyky a platformy, včetně .NET, Java, Python, C++cestách, Node. js, SWIFT, DART, Ruby a php. Díky ukládání binárních přenosů do vyrovnávací paměti protokolů a efektivní generování kódu pro každou platformu můžou vývojáři vytvářet výkonné aplikace a pořád využívat plnou podporu pro víc platforem.

### <a name="usability-and-productivity"></a>Použitelnost a produktivita

gRPC je komplexní řešení RPC. Funguje konzistentně napříč různými jazyky a platformami a nabízí vynikající nástroje, s využitím automaticky vygenerovaného často používaného automatického kódu, takže se do obchodní logiky zaměří více času pro vývojáře.

### <a name="streaming"></a>Streamování

gRPC má plnohodnotné obousměrné streamování, které poskytuje velmi podobné funkce jako plně duplexní služby WCF. gRPC streaming může pracovat přes běžná připojení k Internetu, nástroje pro vyrovnávání zatížení a sítě.

### <a name="deadlinetimeouts-and-cancellation"></a>Konečný termín, vypršení časového limitu a zrušení

gRPC umožňuje klientům zadat maximální dobu, po kterou se RPC dokončí. Pokud je překročen zadaný konečný termín, server může operaci zrušit nezávisle na klientovi. Termíny a zrušení lze rozšířit prostřednictvím dalších volání gRPC, která vám pomůžou vyhodnotit omezení využití prostředků. Klienti mohou také přerušit operace, když je překročen konečný termín, nebo dříve, pokud je to nutné (např. z důvodu interakce s uživatelem).

### <a name="security"></a>Zabezpečení

gRPC je implicitně zabezpečený při použití HTTP/2 přes komplexní šifrované připojení TLS. Podpora ověřování klientského certifikátu (viz kapitola 6) dále zvyšuje zabezpečení a důvěryhodnost mezi klientem a serverem.

>[!div class="step-by-step"]
>[Předchozí](network-protocols.md)
>[Další](protocol-buffers.md)
