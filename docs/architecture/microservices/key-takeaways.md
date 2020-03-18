---
title: Základní poznatky
description: Získejte klíčové stánek s jídlem z .NET Microservices Architecture pro containerized .NET Aplikace průvodce/e-book, chcete-li mít rychlý přehled o vysoké úrovni problémy spojené s použitím architektury mikroslužeb, jako jsou výhody a nevýhody, DDD vzory pro návrh a vývoj, stejně jako odolnost proti chybám, zabezpečení a použití orchestrátorů.
ms.date: 10/19/2018
ms.openlocfilehash: 3b8b7be9b3903c64221cba7c6abdb1e38f5d944f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70296025"
---
# <a name="key-takeaways"></a>Klíčové stánek s jídlem

Jako shrnutí a klíčové stánek s jídlem, následující jsou nejdůležitější závěry z této příručky.

**Výhody používání kontejnerů.** Řešení založená na kontejnerech poskytují významné úspory nákladů, protože pomáhají snížit problémy s nasazením způsobené selháním závislostí v produkčním prostředí. Kontejnery výrazně zlepšit DevOps a výrobní operace.

**Kontejnery budou všudypřítomné.** Kontejnery založené na Dockeru se stávají de facto standardem v oboru, podporovaným klíčovými dodavateli v ekosystémech Windows a Linux, jako jsou Microsoft, Amazon AWS, Google a IBM. Docker bude pravděpodobně brzy všudypřítomné v cloudu i místní datové centra.

**Kontejnery jako jednotka nasazení.** Kontejner Dockeru se stává standardní jednotkou nasazení pro všechny serverové aplikace nebo služby.

**Mikroslužeb.** Architektura mikroslužeb se stává upřednostňovaným přístupem pro distribuované a rozsáhlé nebo složité kritické aplikace založené na mnoha nezávislých subsystémech ve formě autonomních služeb. V architektuře založené na mikroslužbách je aplikace vytvořena jako kolekce služeb, které jsou vyvíjeny, testovány, verzí, nasazeny a škálovány nezávisle. Každá služba může obsahovat jakoukoli související autonomní databázi.

**Návrh řízený doménou a SOA.** Vzory architektury mikroslužeb jsou odvozeny od architektury orientované na služby (SOA) a návrhu řízeného doménou (DDD). Při navrhování a vývoji mikroslužeb pro prostředí s vyvíjejícími se obchodními potřebami a pravidly je důležité zvážit přístupy a vzory DDD.

**Mikroslužeb výzvy.** Mikroslužby nabízejí mnoho výkonných funkcí, jako je nezávislé nasazení, silné hranice subsystému a rozmanitost technologií. Vyvolávají však také mnoho nových výzev souvisejících s vývojem distribuovaných aplikací, jako jsou roztříštěné a nezávislé datové modely, odolná komunikace mezi mikroslužbami, konečná konzistence a provozní složitost, která je výsledkem agregace protokolování a monitorování informací z více mikroslužeb. Tyto aspekty zavádějí mnohem vyšší úroveň složitosti než tradiční monolitická aplikace. V důsledku toho jsou vhodné pouze konkrétní scénáře pro aplikace založené na mikroslužbách. Patří mezi ně velké a složité aplikace s více vyvíjejícími se subsystémy. V těchto případech stojí za to investovat do složitější softwarové architektury, protože poskytne lepší dlouhodobou flexibilitu a údržbu aplikací.

**Kontejnery pro každou aplikaci.** Kontejnery jsou vhodné pro mikroslužby, ale může být také užitečné pro monolitické aplikace založené na tradiční rozhraní .NET Framework, při použití kontejnerů systému Windows. Výhody používání Dockeru, jako je řešení mnoha problémů s nasazením a produkčních a poskytování nejmodernějších prostředí Pro vývoj a testování, platí pro mnoho různých typů aplikací.

**CLI versus IDE.** Pomocí nástrojů společnosti Microsoft můžete vyvíjet kontejnerizované aplikace .NET pomocí upřednostňovaného přístupu. Můžete vyvíjet pomocí rozhraní CLI a prostředí založeného na editoru pomocí rozhraní cli Dockeru a kódu Visual Studio. Nebo můžete použít přístup zaměřený na ide s Visual Studio a jeho jedinečné funkce pro Docker, jako je například ladění více kontejnerů.

**Odolné cloudové aplikace.** V cloudových systémech a distribuovaných systémech obecně existuje vždy riziko částečného selhání. Vzhledem k tomu, že klienti a služby jsou samostatné procesy (kontejnery), služba nemusí být schopna včas reagovat na požadavek klienta. Služba může být například mimo provoz z důvodu částečné poruchy nebo údržby. služba může být přetížena a může pomalu reagovat na požadavky; nebo nemusí být k dispozici krátkou dobu z důvodu problémů se sítí. Proto cloudová aplikace musí přijmout tyto chyby a mít strategii na místě reagovat na tyto chyby. Tyto strategie mohou zahrnovat zásady opakování (opakované odesílání zpráv nebo opakování požadavků) a implementaci schémat jističů, aby se zabránilo exponenciálnímu zatížení opakovaných požadavků. V podstatě musí mít cloudové aplikace odolné mechanismy – buď založené na cloudové infrastruktuře, nebo na vlastní úrovni, jako ty na vysoké úrovni poskytované orchestrátory nebo servisními sběrnicemi.

**Zabezpečení.** Náš moderní svět kontejnerů a mikroslužeb může odhalit nové chyby zabezpečení. Existuje několik způsobů, jak implementovat základní zabezpečení aplikace na základě ověřování a autorizace. Zabezpečení kontejneru však musí zvážit další klíčové součásti, které mají za následek ze své podstaty bezpečnější aplikace. Klíčovým prvkem vytváření bezpečnějších aplikací je bezpečný způsob komunikace s jinými aplikacemi a systémy, což často vyžaduje přihlašovací údaje, tokeny, hesla a podobně, běžně označované jako tajné kódy aplikací. Jakékoli zabezpečené řešení musí dodržovat osvědčené postupy zabezpečení, jako je například šifrování tajných kódů při přenosu a v klidovém stavu a zabránění úniku tajných kódů při spotřebování konečnou aplikací. Tyto tajné klíče je třeba bezpečně uložit a uchovávat, jako při použití služby Azure Key Vault.

**Orchestrátoři.** Orchestrators založené na kontejnerech, jako je například Služba Azure Kubernetes a Azure Service Fabric jsou klíčovou součástí jakékoli významné mikroslužby a aplikace založené na kontejnerech. Tyto aplikace s sebou nesou vysokou složitost, potřeby škálovatelnosti a procházejí neustálým vývojem. Tato příručka zavedla orchestrators a jejich roli v řešeních založených na mikroslužbách a kontejnerech. Pokud vaše aplikace potřebuje se pohybuje směrem ke složitým kontejnerizované aplikace, zjistíte, že je užitečné hledat další prostředky pro další informace o orchestrators.

>[!div class="step-by-step"]
>[Předchozí](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)
