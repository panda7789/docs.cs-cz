---
title: Základní poznatky
description: Získat stěžejní z architektury Mikroslužby .NET Kontejnerizovaných aplikací .NET/elektronická kniha průvodce, aby rychlý přehled vysoké úrovně problémy zahrnuty při použití architektury mikroslužeb, jako je výhody a nevýhody, vzorů DDD pro návrh a vývoj, jakož i odolnost proti chybám, zabezpečení a použití orchestrátorů.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 90babf9a32d1e139216cbc8eb1c629401b8e83e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62020171"
---
# <a name="key-takeaways"></a>Stěžejní zjištění

Jako souhrn a stěžejní zjištění tady jsou důležité závěry v této příručce.

**Výhody použití kontejnerů.** Řešení založených na kontejnerech poskytují důležité úspory, protože pomáhají snížit způsobeno neúspěšné závislosti v produkčních prostředích problémů s nasazením. Kontejnery výrazně zlepšit operace DevOps a produkčním prostředí.

**Kontejnery bude všudypřítomná.** Kontejnery dockeru se stávají de facto standardem v odvětví, podporuje klíče dodavatelů v ekosystémů Windows a Linux, jako jsou Microsoft, Amazon AWS, Google a IBM. Docker se pravděpodobně už brzy bude všudypřítomná v cloudových i místních datových centrech.

**Kontejnery jako jednotky nasazení.** Kontejner Dockeru se standardní jednotkou nasazení pro všechny serverové aplikace nebo služba.

**Mikroslužby.** Architektura mikroslužeb se mění na upřednostňovaný způsob pro distribuované a velké nebo složité důležité podnikové aplikace založené na mnoha nezávislých subsystémy ve formě autonomních služeb. V architektuře s využitím mikroslužeb je aplikace sestavená jako kolekce služeb, které jsou vyvinuté, otestované, verze, nasazené a škálované nezávisle. Každá služba může zahrnovat všechny související autonomní databáze.

**Návrhy řízené doménou a SOA.** Vzory architektury mikroslužeb jsou odvozeny z architektury orientované na služby (SOA) a návrhu řízeného doménou (DDD). Při návrhu a vývoj mikroslužeb pro prostředí s vyvíjí obchodní potřeby a pravidla, je důležité vzít v úvahu DDD postupy a vzory.

**Mikroslužby úkoly.** Mikroslužby nabízí mnoho výkonné funkce, jako nezávislé nasazení subsystému silné hranice a technologie rozmanitosti. Ale také vyvolají mnoho nové výzvy související s vývoj distribuovaných aplikací, jako je fragmentaci a nezávislé datové modely, odolné komunikaci mezi mikroslužeb, konzistencí a provozní složitost, která je výsledkem agregování informací o protokolování a monitorování z několika mikroslužeb. Tyto aspekty zavést mnohem vyšší úroveň složitosti než u tradičních monolitické aplikace. V důsledku toho pouze konkrétní scénáře jsou vhodné pro aplikace založené na mikroslužbách. Patří mezi ně velkých a složitých aplikací s více vyvíjející subsystémů. V těchto případech je vhodné prošetřují složitější softwarovou architekturu, protože bude poskytovat lepší dlouhodobé flexibilitu a údržbu aplikace.

**Kontejnery pro každou aplikaci.** Kontejnery jsou vhodné pro mikroslužby, ale můžou být také užitečné pro monolitické aplikace založené na tradiční rozhraní .NET Framework, při použití kontejnerů Windows. Výhody použití Dockeru, jako je například mnoho problémů nasazení do produkčního prostředí a poskytuje stav moderní vývojové a testovací prostředí, platí pro mnoho různých typů aplikací.

**Rozhraní příkazového řádku a integrované vývojové prostředí.** Pomocí nástrojů Microsoftu můžete vyvíjet kontejnerizované aplikace .NET pomocí svůj oblíbený přístup. Můžete vyvíjet pomocí rozhraní příkazového řádku a prostředí na základě editoru pomocí rozhraní příkazového řádku Dockeru a Visual Studio Code. Nebo můžete použít přístup zaměřený na integrované vývojové prostředí s Visual Studio a její jedinečné funkce pro Docker, jako je ladění více kontejnerů.

**Odolné cloudové aplikace.** V cloudových systémů a distribuovaných systémů, je vždycky riziko částečného selhání. Od klientů a služeb jsou samostatné procesy (kontejnerů), služba nemusí být schopné reagovat včas na žádost klienta. Například služba může být mimo provoz kvůli částečného selhání nebo kvůli údržbě; Služba může být přetížená a reagovat na pomalu požádá; nebo nemusí být dostupný na krátkou dobu z důvodu problémů se sítí. Aplikace založené na cloudu musí proto využívat tyto chyby a mít strategii reagovat na tyto chyby. Tato strategie může obsahovat zásady opakování (opakovaném posílání zpráv nebo opakování požadavků) a implementující vzory jistič – aby se zabránilo exponenciální načíst opakovaných požadavků. V podstatě cloudové aplikace, musí mít odolné mechanismy – podle cloudové infrastruktury nebo vlastní, jaké vysoké úrovně jsou poskytované orchestrátorů nebo sběrnice služby.

**Zabezpečení.** Našem moderním světě kontejnery a mikroslužby mohou vystavit nová ohrožení zabezpečení. Existuje několik způsobů, jak implementovat zabezpečení základních aplikací, na základě ověřování a autorizace. Zabezpečení kontejneru však nutné vzít v úvahu další klíčové komponenty, jejichž výsledkem je ze své podstaty bezpečnější aplikace. Důležitý krok vytvářet bezpečnější aplikace dochází k danému bezpečný způsob komunikace s jinými aplikacemi a systémy, něco, často vyžaduje přihlašovací údaje, tokeny, hesla a podobně, co se obvykle označuje jako tajné kódy aplikace. Jakékoli zabezpečené řešení postupujte podle osvědčené postupy zabezpečení, jako je například šifrování tajných kódů při přenášená i neaktivní uložená a zabráněním tajné kódy, abyste zabránili úniku při používané konečné aplikace. Těchto tajných klíčů potřebu být uloženy a bezpečně, jako při použití Azure Key Vault.

**Orchestrators.** Založených na kontejnerech orchestrátorů, jako jsou služby Azure Kubernetes Service a Azure Service Fabric jsou klíčovou součástí žádné významné mikroslužby a aplikace založené na kontejnerech. Tyto aplikace provádět s nimi vysokou složitost, požadavky na škálovatelnost a přejít přes konstantní vývoj. Tento průvodce přináší orchestrátorů a jejich role v řešení založených na mikroslužbách a založených na kontejnerech. Pokud se potřeby vaší aplikace se přesouvají směrem k komplexní kontejnerizované aplikace, bude užitečné Hledat další prostředky pro získání informací o orchestrátorů.

>[!div class="step-by-step"]
>[Předchozí](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)