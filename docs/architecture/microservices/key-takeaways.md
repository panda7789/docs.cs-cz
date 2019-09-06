---
title: Základní poznatky
description: Získejte službu Key poznatky od architektury mikroslužeb .NET pro kontejnerové aplikace .NET – příručka a elektronickou knihu, abyste se mohli rychle podívat na problémy vysoké úrovně, které se týkají při používání architektury mikroslužeb, jako jsou výhody a nevýhody, DDD vzory pro návrh a vývoj a také odolnost, zabezpečení a používání orchestrací.
ms.date: 10/19/2018
ms.openlocfilehash: 3b8b7be9b3903c64221cba7c6abdb1e38f5d944f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296025"
---
# <a name="key-takeaways"></a>Key poznatky

Níže jsou uvedené nejdůležitější závěry z tohoto průvodce jako souhrn a Key poznatky.

**Výhody používání kontejnerů.** Řešení založená na kontejnerech poskytují důležité úspory nákladů, protože umožňují snižovat problémy s nasazením způsobené selháním závislostí v produkčních prostředích. Kontejnery významně zlepšují DevOps a produkční operace.

**Kontejnery budou všudypřítomný.** Kontejnery založené na Docker se v oboru stanou de facto standardem, které podporují dodavatelé klíčů v ekosystémech Windows a Linux, jako je Microsoft, Amazon AWS, Google a IBM. Docker bude pravděpodobně brzy všudypřítomný v cloudových i místních datových centrech.

**Kontejnery jako jednotka nasazení.** Kontejner Docker se stává standardní jednotkou nasazení pro jakoukoli serverovou aplikaci nebo službu.

**Mikroslužeb.** Architektura mikroslužeb se stává upřednostňovaným přístupem k distribuovaným a rozsáhlým nebo složitým podnikovým aplikacím, které jsou založené na mnoha nezávislých subsystémech ve formě autonomních služeb. V architektuře založené na mikroslužbách je aplikace sestavena jako kolekce služeb, které jsou vyvíjeny, testovány, nasazeny, nasazeny a škálovat nezávisle. Každá služba může zahrnovat všechny související autonomní databáze.

**Návrh založený na doméně a SOA.** Modely architektury mikroslužeb jsou odvozeny od architektury SOA (Service-orientované) a návrhu založeného na doméně (DDD). Při navrhování a vývoji mikroslužeb pro prostředí s vývojem obchodních potřeb a pravidel je důležité zvážit DDD přístupy a vzory.

**Výzvy k mikroslužbám.** Mikroslužby nabízejí mnoho výkonných možností, jako je nezávislé nasazení, silné hranice subsystému a odlišná technologie. Také vyvolává mnoho nových výzev souvisejících s vývojem distribuovaných aplikací, jako jsou fragmentované a nezávislé datové modely, odolná komunikace mezi mikroslužbami, konečnou konzistencí a provozní složitou, která je výsledkem agregace informací o protokolování a monitorování z více mikroslužeb. Tyto aspekty představují mnohem vyšší úroveň složitosti než tradiční aplikace v monolitické. V důsledku toho jsou pro aplikace založené na mikroslužbách vhodné jenom konkrétní scénáře. Mezi ně patří velké a komplexní aplikace s několika vyvíjejícími se subsystémy. V těchto případech se jedná o investici do složitější softwarové architektury, protože zajišťuje lepší dlouhodobou flexibilitu a údržbu aplikací.

**Kontejnery pro libovolnou aplikaci.** Kontejnery jsou vhodné pro mikroslužby, ale můžou být užitečné i pro monolitické aplikace založené na tradičních .NET Framework, při použití kontejnerů Windows. Výhody použití Docker, jako je řešení mnoha problémů s nasazením do produkčního prostředí a poskytování nejmodernějších vývojových a testovacích prostředí, se vztahují na mnoho různých typů aplikací.

**Rozhraní příkazového řádku versus IDE** Pomocí nástrojů Microsoftu můžete vyvíjet kontejnerové aplikace .NET s využitím preferovaného přístupu. Můžete vyvíjet pomocí CLI a prostředí založeného na editoru pomocí rozhraní Docker CLI a Visual Studio Code. Nebo můžete použít přístup zaměřený na integrované vývojové prostředí (IDE) se sadou Visual Studio a jedinečné funkce pro Docker, jako je například ladění více kontejnerů.

**Odolné cloudové aplikace.** V cloudových systémech a distribuovaných systémech je obecně vždy riziko částečného selhání. Vzhledem k tomu, že klienti a služby jsou samostatné procesy (kontejnery), nemusí být služba schopná reagovat včas na požadavky klienta. Například služba může být mimo provoz z důvodu částečného selhání nebo údržby; Služba může být přetížená a reaguje pomalu na požadavky. nebo nemusí být k dispozici po krátkou dobu kvůli problémům se sítí. Cloudová aplikace proto musí tyto chyby doložit a mít k dispozici strategii pro reakci na tyto chyby. Tyto strategie můžou zahrnovat zásady opakování (opakované odeslání zpráv nebo opakování požadavků) a implementace vzorů pro dělení na okruhy, aby nedocházelo k exponenciálnímu zatížení opakovaných požadavků. Cloudové aplikace musí mít odolný mechanismus, a to v závislosti na infrastruktuře cloudu nebo vlastním, jako na nejvyšší úrovni poskytované orchestrací nebo sběrnicí služeb.

**Bezpečnost.** Náš moderní svět kontejnerů a mikroslužeb může vystavovat nová ohrožení zabezpečení. Existuje několik způsobů, jak implementovat základní zabezpečení aplikací v závislosti na ověřování a autorizaci. Zabezpečení kontejneru ale musí vzít v úvahu další klíčové komponenty, které vedou k v podstatě bezpečnějším aplikacím. Důležitým prvkem pro sestavování bezpečnějších aplikací je zabezpečený způsob komunikace s dalšími aplikacemi a systémy, což často vyžaduje přihlašovací údaje, tokeny, hesla a podobně, které se běžně označují jako tajné klíče pro aplikace. Jakékoli zabezpečené řešení musí splňovat osvědčené postupy zabezpečení, jako je šifrování tajných kódů během přenosu a v klidovém režimu, a zabránění úniku tajných klíčů, pokud je spotřebovává konečná aplikace. Tyto tajné kódy je potřeba ukládat a bezpečně uchovávat, jako při použití Azure Key Vault.

**Orchestrators.** Orchestrace založená na kontejnerech, jako je služba Azure Kubernetes a Azure Service Fabric, jsou klíčovou součástí jakékoli významné aplikace založené na mikroslužbách a kontejneru. Tyto aplikace jsou s vysokou složitostí a potřebou škálovatelnosti a procházejí průběžným vývojem. Tato příručka zavedla Orchestrace a jejich roli v řešeních založených na mikroslužbách a kontejnerech. Pokud vaše aplikace potřebuje přesunout se ke složitým kontejnerovým aplikacím, zjistíte, že je užitečné si vyžádat další materiály, které vám pomůžou se dozvědět víc o orchestrcích.

>[!div class="step-by-step"]
>[Předchozí](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)
