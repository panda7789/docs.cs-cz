---
title: Úvod - gRPC pro vývojáře WCF
description: Úvod
ms.date: 09/02/2019
ms.openlocfilehash: 41f470eb02a77b1b6a26a7d4c2ca347ad07d828d
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988931"
---
# <a name="introduction"></a>Úvod

Pomoc strojům komunikovat mezi sebou byla jedním z hlavních zájmů digitálního věku. Zejména, tam je pokračující úsilí o určení optimálního mechanismu dálkové komunikace, která bude vyhovovat požadavky interoperability současné infrastruktury. Jak si dokážete představit, tento mechanismus se mění, jak se vyvíjejí požadavky nebo infrastruktura.

Vydání rozhraní .NET Core 3.0 znamená posun ve způsobu, jakým Microsoft poskytuje řešení vzdálené komunikace vývojářům, kteří chtějí poskytovat služby na různých platformách. .NET Core nenabízí Windows Communication Foundation (WCF) po vybalení z krabice, ale s vydáním ASP.NET Core 3.0 poskytuje vestavěnou funkci gRPC.

gRPC je populární rámec v širší softwarové komunitě. Používá se vývojáři v mnoha programovacích jazycích pro moderní scénáře Vzdáleného volání procedur. Komunita a ekosystém jsou živé a aktivní. Podpora protokolu gRPC se přidává do součástí infrastruktury, jako jsou Kubernetes, servisní adresy, nástroj pro vyrovnávání zatížení a další. Tyto faktory spolu s výkonem, efektivitou a kompatibilitou napříč platformami činí gRPC přirozenou volbou pro nové aplikace a aplikace WCF, které se přesouvají do .NET Core.

## <a name="history"></a>Historie

Základní princip počítačové sítě jako nic víc než skupina počítačů, které si vzájemně vyměňují data, aby dosáhly souboru vzájemně souvisejících úkolů, se od svého vzniku nezměnil. Složitost, rozsah a očekávání však exponenciálně vzrostly.  

V devadesátých letech byl kladen důraz především na zlepšení vnitřních sítí, které používaly stejný jazyk a platformy. TCP/IP se stal zlatým standardem pro tento typ komunikace.

Zaměření se brzy přesunulo na to, jak nejlépe optimalizovat komunikaci napříč různými platformami podporou přístupu agnostika jazyka. Architektura orientovaná na služby (SOA) poskytla strukturu pro volné propojení široké kolekce služeb, které by mohly být poskytnuty aplikaci.

K rozvoji *webových služeb* došlo, když všechny hlavní platformy mohly přistupovat k internetu, ale stále spolu nemohly komunikovat. Webové služby mají otevřené standardy a protokoly, včetně:

- XML pro tagy a kódová data.
- Protokol SOAP (Simple Object Access Protocol) pro přenos dat.
- Jazyk wsdl (Web Services Definition Language) pro popis a připojení webových služeb ke klientským aplikacím.
- Univerzální popis, zjišťování a integrace (UDDI), aby webové služby zjistitelné jinými službami.

SOAP definuje pravidla, podle kterých distribuované prvky aplikace mohou vzájemně komunikovat, i když jsou na různých platformách. SOAP je založen na XML, takže je čitelný pro člověka. Oběť pro to, aby soap snadno pochopitelné, je velikost; SOAP zprávy jsou větší než zprávy ve srovnatelných protokolech. SOAP byl navržen tak, aby rozdělit monolitické aplikace do vícesložkové formě bez ztráty zabezpečení nebo kontroly. Takže WCF byl navržen pro práci s tímto druhem systému, na rozdíl od gRPC, který začal jako distribuovaný systém. WCF řeší některá z těchto omezení tím, že vyvíjí a dokumentuje proprietární rozšiřující protokoly pro zásobník SOAP, ale za cenu nedostatku podpory z jiných platforem.

Windows Communication Foundation je rámec pro vytváření služeb. Byl navržen na počátku roku 2000, aby pomohl vývojářům, kteří používají rané SOA ke správě složitosti práce s SOAP. Přestože odstraňuje požadavek pro vývojáře psát vlastní protokoly SOAP, WCF stále používá SOAP povolit interoperabilitu s jinými systémy. WCF byl také navržen tak, aby poskytoval řešení napříč více protokoly (HTTP/1.1, Net.TCP a tak dále).

## <a name="microservices"></a>Mikroslužby

V architekturách mikroslužeb jsou velké aplikace vytvořeny jako kolekce menších modulárních služeb. Každá součást provádí určitý úkol nebo proces a součásti jsou navrženy tak, aby fungovaly interoperabilně, ale mohou být podle potřeby izolovány.

Mezi výhody mikroslužeb patří:

- Změny a upgrady lze zpracovat nezávisle.
- Zpracování chyb se stává efektivnější, protože problémy lze sledovat na konkrétní služby, které jsou pak izolované, znovu sestavit, testovány a znovu nasazené nezávisle na ostatních služeb.
- Škálovatelnost může být omezena na konkrétní instance nebo služby, nikoli na celou aplikaci.
- Vývoj může dojít napříč více týmy, s menším třením, než nastane, když mnoho týmů pracovat na jednom základu kódu.

Posun směrem ke zvyšování virtualizace, cloud computingu, kontejnerů a internetu věcí přispěl k pokračujícímu nárůstu mikroslužeb. Ale mikroslužby nejsou bez jejich výzvy. Roztříštěná/decentralizovaná infrastruktura klade větší důraz na potřebu jednoduchosti a rychlosti při komunikaci mezi službami. To zase upozornilo na někdy namáhavou a zkroucenou povahu SOAP.

To bylo do tohoto prostředí, že gRPC byla zahájena, 10 let poté, co Microsoft poprvé vydalwcf. GRPC, který se vyvinul přímo z interní infrastruktury Společnosti Google RPC (Stubby), nebyl nikdy založen na stejných standardech a protokolech, které informovaly o parametrech mnoha dřívějších RPC. A gRPC byl založen pouze na HTTP/2. To je důvod, proč by mohl čerpat z nových schopností, které poskytuje pokročilý transportní protokol. Zejména obousměrné streamování, binární zasílání zpráv a multiplexování.

## <a name="about-this-guide"></a>O této příručce

Tato příručka pokrývá klíčové vlastnosti gRPC. První kapitoly se na vysoké úrovni podívat na hlavní rysy WCF a porovnat je s těmi gRPC. Identifikuje, kde existují přímé korelace mezi WCF a gRPC a také kde gRPC nabízí výhodu. Pokud neexistuje žádná korelace mezi WCF a gRPC, nebo když gRPC není schopen nabídnout ekvivalentní řešení WCF, tato příručka navrhne řešení nebo kam jít pro další informace.

Pomocí sady ukázkových aplikací WCF, kapitola 5 je hloubkový pohled na převod hlavních typů služby WCF (jednoduchá odpověď na požadavek, jednosměrný a streamování) na jejich ekvivalenty v gRPC.

Závěrečná část knihy se zabývá tím, jak získat to nejlepší z gRPC v praxi. Tato část obsahuje informace o použití dalších nástrojů, jako jsou kontejnery Dockernebo Kubernetes, k využití efektivity gRPC. Obsahuje také podrobný pohled na monitorování pomocí protokolování, metrik a distribuovaného trasování.

## <a name="who-this-guide-is-for"></a>Pro koho je tato příručka určena

Tato příručka byla napsána pro vývojáře pracující v rozhraní .NET Framework nebo .NET Core, kteří používají WCF a kteří se snaží migrovat své aplikace do moderního prostředí RPC pro .NET Core 3.0 a novější verze. Průvodce může být také obecněužitečné pro vývojáře upgrade nebo zvažuje upgrade na .NET Core 3.0 a kteří chtějí používat integrované gRPC nástroje.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](grpc-overview.md)
