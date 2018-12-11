---
title: Stěžejní zjištění
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | stěžejní zjištění
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: d6e09b9856396e99c9b03d595c1896e2451724fe
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152254"
---
# <a name="key-takeaways"></a>Stěžejní zjištění

Jako souhrn a stěžejní zjištění tady jsou důležité závěry v této příručce.

**Výhody použití kontejnerů.** Řešení založených na kontejnerech poskytnout důležitou výhodou metody úspory nákladů, protože jsou kontejnery, řešení problémů s nasazením kvůli absenci závislosti v produkčním prostředí. Kontejnery výrazně zlepšit operace DevOps a produkčním prostředí.

**Kontejnery bude všudypřítomná.** Kontejnery dockeru se stávají de facto standardem v odvětví kontejneru, podporovány jsou nejdůležitější dodavatelé v ekosystémů Windows a Linux. To zahrnuje Microsoft, Amazon AWS, Google a IBM. V blízké budoucnosti Docker bude pravděpodobně všudypřítomná v cloudových i místních datových centrech.

**Kontejnery jako jednotky nasazení.** Kontejner Dockeru se standardní jednotkou nasazení pro všechny serverové aplikace nebo služba.

**Mikroslužby.** Architektura mikroslužeb se mění na upřednostňovaný způsob pro distribuované a rozsáhlých nebo složitých důležité podnikové aplikace založené na více nezávislých subsystémy ve formě autonomních služeb. V architektuře s využitím mikroslužeb je aplikace sestavená jako kolekce služeb, které mohou být vyvinuté, otestované, verze, nasazené a škálované nezávisle na sobě; To může zahrnovat všechny související autonomní databáze.

**Návrhy řízené doménou a SOA.** Vzory architektury mikroslužeb jsou odvozeny z architektury orientované na služby (SOA) a návrhu řízeného doménou (DDD). Při návrhu a vývoj mikroslužeb pro prostředí s vyvíjí obchodní pravidla v určité doméně tvarování, je důležité zohlednit účet DDD přístupy a vzory.

**Mikroslužby úkoly.** Mikroslužby nabízí mnoho výkonné funkce, jako nezávislé nasazení subsystému silné hranice a technologie rozmanitosti. Ale také vyvolají mnoho nové výzvy související s vývoj distribuovaných aplikací, jako je fragmentaci a nezávislé datové modely, odolné komunikaci mezi mikroslužeb, konzistencí a provozní složitost, která je výsledkem agregování informací o protokolování a monitorování z několika mikroslužeb. Tyto aspekty zavést vyšší úroveň složitosti než u tradičních monolitické aplikace. V důsledku toho pouze konkrétní scénáře jsou vhodné pro aplikace založené na mikroslužbách. Patří mezi ně velkých a složitých aplikací s více subsystémů vyvíjející; v těchto případech je vhodné prošetřují složitější softwarovou architekturu, protože bude poskytovat lepší dlouhodobé flexibilitu a údržbu aplikace.

**Kontejnery pro každou aplikaci.** Kontejnery jsou vhodné pro mikroslužby, ale nejsou pro ně exkluzivní. Kontejnery můžete použít také s monolitické aplikace, včetně starších aplikací založené na tradiční rozhraní .NET Framework a modernizovala prostřednictvím kontejnerů Windows. Výhody použití Dockeru, jako je například mnoho problémů nasazení do produkčního prostředí a poskytuje nejmodernější optimalizaci pspo vývojové a testovací prostředí, platí pro mnoho různých typů aplikací.

**Rozhraní příkazového řádku a integrované vývojové prostředí.** Pomocí nástrojů Microsoftu můžete vyvíjet kontejnerizované aplikace .NET pomocí svůj oblíbený přístup. Můžete vyvíjet pomocí rozhraní příkazového řádku a prostředí na základě editoru pomocí rozhraní příkazového řádku Dockeru a Visual Studio Code. Nebo můžete použít přístup zaměřený na integrované vývojové prostředí s Visual Studio a její jedinečné funkce pro Docker, jako například nebudou moct laďte vícekontejnerové aplikace.

**Odolné cloudové aplikace.** V cloudových systémů a distribuovaných systémů, je vždycky riziko částečného selhání. Od klientů a služeb jsou samostatné procesy (kontejnerů), služba nemusí být schopné reagovat včas na žádost klienta. Například služba může být mimo provoz kvůli částečného selhání nebo kvůli údržbě; Služba může být přetížená a reagovat na velmi pomalu požádá; nebo jednoduše je přístupná po krátkou dobu z důvodu problémů se sítí. Aplikace založené na cloudu musí proto využívat tyto chyby a mít strategii reagovat na tyto chyby. Tato strategie může obsahovat zásady opakování (opakovaném posílání zpráv nebo opakování požadavků) a implementující vzory jistič – aby se zabránilo exponenciální načíst opakovaných požadavků. V podstatě cloudové aplikace, musí mít odolné mechanismy – vlastní těch, které jsou, nebo těch, které jsou založené na cloudové infrastruktury, jako je například vyšší úrovně rozhraní z orchestrátorů nebo sběrnice služby.

**Zabezpečení.** Našem moderním světě kontejnery a mikroslužby mohou vystavit nová ohrožení zabezpečení. Základním zabezpečení aplikací je založený na ověřování a autorizaci; k implementaci těchto existovat několika způsoby. Zabezpečení kontejneru však zahrnuje další klíčové komponenty, jejichž výsledkem je ze své podstaty bezpečnější aplikace. Důležitý krok vytvářet bezpečnější aplikace dochází k danému bezpečný způsob komunikace s ostatními aplikace a systémy, něco, které často vyžaduje přihlašovací údaje, tokeny, hesla a další typy důvěrných informací – obvykle označovány jako tajné kódy aplikace. Jakékoli zabezpečené řešení musí dodržujte doporučené postupy zabezpečení, třeba šifrování tajných kódů v průběhu přenosu; šifrování tajných klíčů v klidovém stavu; a brání tajné kódy, abyste zabránili úniku neúmyslně při používané konečné aplikace. Tyto tajné kódy potřeba ukládat a v bezpečí někde. Abychom se zabezpečením, můžete využít výhod infrastruktury pro zvolený orchestrátor nebo cloudové infrastruktury, jako je Azure Key Vault a způsoby, kterými poskytuje pro aplikace kód pro jeho použití.

**Orchestrátory.** Založených na kontejnerech orchestrátorů, jako jsou k dispozici v Azure Container Service (Kubernetes, Mesos DC/OS a Docker Swarm) a Azure Service Fabric jsou nezbytné pro všechny aplikace připravené pro produkční prostředí založených na mikroslužbách a pro jakékoli více kontejnerů aplikace s významnou složitost, požadavky na škálovatelnost a konstantní vývoj. Tento průvodce přináší orchestrátorů a jejich role v řešení založených na mikroslužbách a založených na kontejnerech. Pokud potřeby vaší aplikace se přesouvají směrem k komplexní kontejnerizovaných aplikací, najdete je užitečná k vyhledání dalších prostředků pro získání informací o orchestrátorů

>[!div class="step-by-step"]
>[Předchozí](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)