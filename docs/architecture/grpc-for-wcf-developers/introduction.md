---
title: Úvod – gRPC pro vývojáře WCF
description: Úvod
ms.date: 09/02/2019
ms.openlocfilehash: 3fb7ae440f65cc2daa2a2c984d01d0c0c1eac0aa
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73967623"
---
# <a name="introduction"></a>Úvod

Napomáháte počítačům navzájem komunikovat s jednou z primárních pracovních verzí digitálního stáří. K určení optimálního vzdáleného komunikačního mechanismu, který bude vyhovovat požadavkům na interoperabilitu aktuální infrastruktury, je zejména průběžné úsilí. Jak můžete představovat, tento mechanismus se mění jak v rámci požadavků, tak ve vývojovém infrastruktuře.

Verze .NET Core 3,0 označuje Shift způsob, jakým společnost Microsoft dodává řešení pro vzdálenou komunikaci vývojářům, kteří chtějí poskytovat služby v rámci celé řady platforem. .NET Core nenabízí Windows Communication Foundation (WCF), ale s vydáním verze ASP.NET Core 3,0 poskytuje vestavěnou funkci gRPC.

gRPC je oblíbená architektura v širší komunitě pro software, kterou vývojáři využívají v různých programovacích jazycích pro moderní scénáře RPC. Komunita a ekosystém jsou zářivé a aktivní, s podporou protokolu gRPC přidávaného do součástí infrastruktury, jako je Kubernetes, sítě pro služby, nástroje pro vyrovnávání zatížení a další. Tyto faktory, jakož i výkon, efektivitu a kompatibilitu mezi platformami, gRPC přirozené možnosti pro nové aplikace a aplikace WCF, které se přesunou do .NET Core.

## <a name="history"></a>Historie

Základní princip počítačové sítě jako nevětšího počtu počítačů, který vyměňuje data mezi sebou, aby se zajistilo, že sada vzájemně souvisejících úloh se od svého zahájení nezměnila. Nicméně složitost, měřítko a očekávání se exponenciálně zvětšily.  

Během 1990s se důraz zaměřuje hlavně na vylepšení interních sítí pomocí stejného jazyka a platforem. Pro tento typ komunikace se stala standardem Gold protokol TCP/IP.

Fokus se ale brzo přesune na to, jak nejlépe optimalizujete komunikaci napříč různými platformami, které podporují nezávisláý přístup k jazyku. Architektura zaměřená na služby (SOA) poskytuje strukturu pro volný spojování široké kolekce služeb, které by mohly být poskytnuty aplikaci.

K vývoji *webových služeb* došlo, když všechny hlavní platformy získají přístup k Internetu, ale stále se nemůžou vzájemně komunikovat. Webové služby mají otevřené standardy a protokoly, mezi které patří:

- XML pro označení a data kódu;
- Protokol SOAP (Simple Object Access Protocol) pro přenos dat;
- WSDL (Web Services Definition Language) – popisuje a připojuje webovou službu ke klientské aplikaci. *a*
- Služba UDDI (Universal Description Discovery Integration) – povoluje, aby webové služby byly zjistitelné jinými službami.

SOAP definuje pravidla, podle kterých mohou distribuované prvky aplikace vzájemně komunikovat, a to i v případě, že jsou na různých platformách. Protokol SOAP je založen na XML, takže je čitelný pro člověka. Usmrcení pro snazší porozumění protokolu SOAP má velikost; Zprávy SOAP jsou větší než zprávy v srovnatelných protokolech. Protokol SOAP byl navržen pro rozdělení monolitické aplikací do formuláře s více komponentami, aniž by došlo ke ztrátě zabezpečení nebo řízení. Proto služba WCF byla navržena pro práci s tímto druhem systému, na rozdíl od gRPC, která začala jako distribuovaný systém. Služba WCF vyřešila některá z těchto omezení tím, že vyvíjí a zdokumentuje proprietární protokoly rozšíření pro zásobník protokolu SOAP, ale za cenu nedostatku podpory od jiných platforem.

Windows Communication Foundation je rozhraní pro vytváření služeb. Byla navržena v 2000s, aby usnadnila vývojářům použití prvotního SOA ke správě složitosti práce s protokolem SOAP. I když odebere požadavek, aby vývojář mohl zapisovat svoje vlastní protokoly SOAP, WCF dál používá protokol SOAP, aby bylo možné vzájemnou spolupráci s jinými systémy. Služba WCF byla také navržena tak, aby poskytovala řešení pro různé protokoly (HTTP/1.1, NetTCP a tak dále).

## <a name="microservices"></a>Mikroslužby

V architektuře mikroslužeb jsou velké aplikace sestavené jako kolekce menších modulárních služeb. Každá součást provede konkrétní úlohu nebo proces a komponenty jsou navrženy tak, aby fungovaly, ale mohou být izolované podle potřeby.

Mezi výhody pro mikroslužby patří:

- Změny a upgrady je možné zpracovat nezávisle.
- Zpracování chyb je efektivnější, protože problémy lze trasovat na konkrétní služby, které jsou následně izolované, znovu sestaveny, testovány a znovu nasazeny nezávisle na ostatních službách.
- Škálovatelnost může být omezen na konkrétní instance nebo služby, nikoli na celou aplikaci.
- Vývoj může nastat napříč několika týmy, s menším třením, než nastane, když spousta týmů pracuje na jednom základu kódu.

Přechod ke zvýšení virtualizace, cloud computingu, kontejnerům a Internet věcí přispěl k průběžnému nárůstu mikroslužeb. Mikroslužby ale nemají žádné výzvy. Fragmentovaná nebo decentralizovaná infrastruktura se podrobněji zakládá na potřebě jednoduchosti a rychlosti při komunikaci mezi službami. Tím se zaznamenala pozornost na určitou pracné a neobčanskoprávní povahu protokolu SOAP.

Bylo v tomto prostředí, které gRPC bylo spuštěno, 10 let po prvním vydání služby WCF od společnosti Microsoft. GRPC se vyvinula přímo z interní infrastruktury vzdáleného volání procedur (Stubby) Google na základě stejných standardů a protokolů, které informovaly o parametrech řady předchozích vzdálených volání procedur (RPC). Kromě toho gRPCa na základě HTTP/2 a to je důvod, proč by se mohl nakreslit na nové funkce, které poskytují rozšířený transportní protokol. Konkrétně obousměrné streamování, binární zasílání zpráv a multiplexing.

## <a name="about-this-guide"></a>O této příručce

Tato příručka se věnuje klíčovým funkcím gRPC. Úvodní kapitoly přebírají nejvyšší úroveň v hlavních funkcích WCF a porovnávají je s gRPC. Identifikuje, kde jsou přímé korelace mezi WCF a gRPC a také tam, kde gRPC nabízí výhodu. V případě, že není žádná korelace mezi WCF a gRPC nebo kde gRPC není schopná nabídnout stejné řešení jako WCF, bude tato příručka navrhovat alternativní řešení nebo místa, kde se dozvíte, kde můžete získat další informace.

Pomocí sady ukázkových aplikací WCF je kapitola 5 obsáhlá podrobněá, která se přechází na převod hlavních typů služby WCF (jednoduchá požadavek-odpověď, jednosměrná a streamovaná) na jejich ekvivalenty v gRPC.

V poslední části této knihy se dozvíte, jak získat nejlepší z gRPC v praxi, včetně použití dalších nástrojů, jako jsou kontejnery Docker nebo Kubernetes, k využití efektivity gRPC a podrobného zobrazení sledování pomocí protokolování, metrik a distribuovaných probíhá.

## <a name="whom-this-guide-is-for"></a>Pro kterou je tato příručka určena

Tato příručka je určená pro vývojáře, kteří pracují v .NET Framework nebo .NET Core, kteří dříve používali WCF a kteří chtějí migrovat své aplikace do moderního prostředí RPC pro .NET Core 3,0 a novější verze. Průvodce může být také obecně používán pro vývojáře, kteří upgradují nebo berou v úvahách o upgradu na rozhraní .NET Core 3,0, kteří chtějí používat integrované nástroje gRPC.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](grpc-overview.md)
