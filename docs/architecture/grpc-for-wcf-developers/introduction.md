---
title: Úvod – gRPC pro vývojáře WCF
description: Úvod
ms.date: 09/02/2019
ms.openlocfilehash: 2f36d6294e2c76309b051fb3af21157cbfc1087a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711239"
---
# <a name="introduction"></a>Úvod

Napomáháte počítačům navzájem komunikovat s jednou z primárních pracovních verzí digitálního stáří. K určení optimálního vzdáleného komunikačního mechanismu, který bude vyhovovat požadavkům na interoperabilitu aktuální infrastruktury, se konkrétně jedná o nepřetržité úsilí. Jak můžete představovat, tento mechanismus se mění jak v rámci požadavků, tak ve vývojovém infrastruktuře.

Verze .NET Core 3,0 označuje Shift způsob, jakým společnost Microsoft dodává řešení pro vzdálenou komunikaci vývojářům, kteří chtějí poskytovat služby v rámci celé řady platforem. .NET Core nenabízí Windows Communication Foundation (WCF), ale s vydáním ASP.NET Core 3,0 poskytuje vestavěnou funkci gRPC.

gRPC je oblíbená architektura v širší komunitě pro software. Používá je vývojářům v mnoha programovacích jazycích pro moderní scénáře RPC. Komunita a ekosystém jsou zářivé a aktivní. Do součástí infrastruktury, jako jsou Kubernetes, sítě, služby Vyrovnávání zatížení a další, se přidávají podpora protokolu gRPC. Tyto faktory spolu s výkonem, efektivitou a kompatibilitou mezi platformami gRPC přirozené možnosti pro nové aplikace a aplikace WCF, které se přesunou do .NET Core.

## <a name="history"></a>Historie

Základní princip počítačové sítě jako nevětšího počtu počítačů, který vyměňuje data mezi sebou, aby se zajistilo, že sada vzájemně souvisejících úloh se od svého zahájení nezměnila. Ale složitost, škálování a očekávání se exponenciálně zvětšily.  

Během 1990s byl důraz hlavně na vylepšení interních sítí, které používaly stejný jazyk a platformy. Pro tento typ komunikace se stala standardem Gold protokol TCP/IP.

Fokus se brzy přesune na to, jak nejlépe optimalizujete komunikaci napříč různými platformami, a to tak, že povýšíte nezávisláý přístup. Architektura zaměřená na služby (SOA) poskytuje strukturu pro volný spojování široké kolekce služeb, které by mohly být poskytnuty aplikaci.

K vývoji *webových služeb* došlo, když všechny hlavní platformy získají přístup k Internetu, ale stále se nemůžou vzájemně komunikovat. Webové služby mají otevřené standardy a protokoly, včetně:

- XML pro označení a data kódu.
- Protokol SOAP (Simple Object Access Protocol) pro přenos dat.
- Jazyk WSDL (Web Services Definition Language), který popisuje a připojuje webové služby k klientským aplikacím.
- Universal Description, Discovery a Integration (UDDI), aby webové služby byly zjistitelné jinými službami.

SOAP definuje pravidla, podle kterých mohou distribuované prvky aplikace vzájemně komunikovat, a to i v případě, že jsou na různých platformách. Protokol SOAP je založen na XML, takže je čitelný pro člověka. Usmrcení pro snazší porozumění protokolu SOAP má velikost; Zprávy SOAP jsou větší než zprávy v srovnatelných protokolech. Protokol SOAP byl navržen pro přerušení aplikací monolitické do formy s více komponentami, aniž by došlo ke ztrátě zabezpečení nebo řízení. Proto služba WCF byla navržena pro práci s tímto druhem systému, na rozdíl od gRPC, která začala jako distribuovaný systém. Služba WCF vyřešila některá z těchto omezení tím, že vyvíjí a zdokumentují proprietární protokoly rozšíření pro zásobník protokolu SOAP, ale za cenu nedostatku podpory od jiných platforem.

Windows Communication Foundation je rozhraní pro vytváření služeb. Byla navržena v 2000s, aby usnadnila vývojářům použití prvotního SOA ke správě složitosti práce s protokolem SOAP. I když odebere požadavek, aby vývojáři mohli psát vlastní protokoly SOAP, WCF dál používá protokol SOAP, aby bylo možné vzájemnou spolupráci s jinými systémy. Služba WCF byla také navržena tak, aby poskytovala řešení v různých protokolech (HTTP/1.1, NET. TCP atd.).

## <a name="microservices"></a>Mikroslužeb

V architektuře mikroslužeb jsou velké aplikace sestavené jako kolekce menších modulárních služeb. Každá součást provede konkrétní úlohu nebo proces a komponenty jsou navrženy tak, aby fungovaly, ale mohou být izolované podle potřeby.

Mezi výhody pro mikroslužby patří:

- Změny a upgrady je možné zpracovat nezávisle.
- Zpracování chyb je efektivnější, protože problémy lze trasovat na konkrétní služby, které jsou následně izolované, znovu sestaveny, testovány a znovu nasazeny nezávisle na ostatních službách.
- Škálovatelnost může být omezené na konkrétní instance nebo služby, nikoli na celou aplikaci.
- Vývoj může nastat napříč několika týmy, s menším třením, než nastane, když spousta týmů pracuje na jednom základu kódu.

Přechod ke zvýšení virtualizace, cloud computingu, kontejnerům a Internet věcí přispěl k průběžnému nárůstu mikroslužeb. Ale mikroslužby nejsou bez problémů. Fragmentovaná nebo decentralizovaná infrastruktura zavedla větší důraz na nutnost jednoduchosti a rychlosti při komunikaci mezi službami. Tím se zaznamenala pozornost na určitou pracné a neobčanskoprávní povahu protokolu SOAP.

Bylo v tomto prostředí, které gRPC bylo spuštěno, 10 let po prvním vydání služby WCF od společnosti Microsoft. GRPC se vyvinula přímo z interní infrastruktury vzdáleného volání procedur (Stubby) Google na základě stejných standardů a protokolů, které informovaly o parametrech řady předchozích vzdálených volání procedur (RPC). A služba gRPC byla na základě HTTP/2 na minulosti. To je důvod, proč by se mohl nakreslit na nové funkce, které poskytují rozšířený transportní protokol. Konkrétně obousměrné streamování, binární zasílání zpráv a multiplexing.

## <a name="about-this-guide"></a>O této příručce

Tato příručka se věnuje klíčovým funkcím gRPC. Úvodní kapitoly přebírají nejvyšší úroveň v hlavních funkcích WCF a porovnávají je s gRPC. Identifikuje, kde existují přímé korelace mezi WCF a gRPC a také tam, kde gRPC nabízí výhodu. Pokud není k dispozici korelace mezi WCF a gRPC, nebo pokud gRPC není schopné nabídnout stejné řešení jako WCF, bude tato příručka navrhovat alternativní řešení nebo kde přejít na Další informace.

Pomocí sady ukázkových aplikací WCF je kapitola 5 obsáhlý podrobněý pohled na převod hlavních typů služby WCF (Simple Request-Reply, jednosměrná a streamovaná) na jejich ekvivalenty v gRPC.

Poslední část knihy si vyhledá nejlepší z gRPC v praxi. Tato část obsahuje informace o používání dalších nástrojů, jako jsou kontejnery Docker nebo Kubernetes, aby bylo možné využít efektivitu gRPC. Obsahuje také podrobný pohled na monitorování pomocí protokolování, metrik a distribuovaného trasování.

## <a name="who-this-guide-is-for"></a>Koho je tato příručka určena pro

Tato příručka je určená pro vývojáře, kteří pracují v .NET Framework nebo .NET Core, kteří používali WCF a kteří chtějí migrovat své aplikace do moderního prostředí RPC pro .NET Core 3,0 a novější verze. Tato příručka může být také užitečná pro vývojáře, kteří upgradují nebo berou v úvahách o upgradu na rozhraní .NET Core 3,0 a kteří chtějí používat integrované nástroje gRPC.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](grpc-overview.md)
