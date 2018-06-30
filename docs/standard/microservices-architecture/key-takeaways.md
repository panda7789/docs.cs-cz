---
title: Klíče takeaways
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | klíče takeaways
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 3366fa2494615db841b768f9149a070a65da58ee
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105511"
---
# <a name="key-takeaways"></a>Klíče Takeaways

Jako souhrn a takeaways klíče jsou následující nejdůležitější závěrů z této příručky.

**Výhody použití kontejnerů.** Řešení založená na kontejneru poskytnout důležité výhodou úsporu nákladů, protože jsou kontejnery řešení problémů s nasazením kvůli absenci závislostí v produkčním prostředí. Kontejnery výrazně zlepšit operace DevOps a produkční.

**Kontejnery bude všudypřítomný.** Na základě docker kontejnery se stávají de facto standardem v kontejneru odvětví, jsou nejdůležitější dodavatelé v systému Windows a Linux ekosystémů nepodporuje. To zahrnuje Microsoft, Amazon AWS, Google a IBM. V blízké budoucnosti Docker bude pravděpodobně všudypřítomný v datových centrech cloudové i místní.

**Kontejnery jako jednotky nasazení.** Kontejner Docker se stává stále standardní jednotka nasazení pro všechny služby nebo aplikace na serveru.

**Mikroslužeb.** Architektura mikroslužeb se stává stále žádoucí pro distribuované a velké nebo složité kritické aplikace založené na více nezávislých subsystémy ve formě autonomního služby. V architektuře na základě mikroslužbu je aplikace vytvořená jako kolekce služeb, které můžou být vyvinuté, otestovaný, verzí, nasazení a škálovat nezávisle; To může zahrnovat všechny související autonomního databáze.

**Řízené domény návrhu a SOA.** Architektura vzory mikroslužeb odvozen od orientované na služby architektura (SOA) a řízené domény návrh (DDD). Pokud návrh a vývoj mikroslužeb pro prostředí se vznikajícími obchodní pravidla shaping konkrétní domény, je důležité vzít v účtu DDD přístupy a vzory.

**Mikroslužeb problémy.** Mikroslužeb nabízí mnoho výkonné možnosti, jako je nezávislé nasazení, silné subsystému hranice a různorodost technologie. Však také vyvolají mnoho nové problémy související s vývoj distribuovaných aplikací, jako je fragmentací a nezávislé datové modely, odolné komunikaci mezi mikroslužeb, konzistence typu případné a provozní složitost, která je výsledkem agregace informací o protokolování a monitorování z několika mikroslužeb. Tyto aspekty zavést na vyšší úrovni složitější než tradiční monolitický aplikace. V důsledku toho jsou vhodné pro aplikace založené na mikroslužbu pouze konkrétní scénáře. Patří mezi ně velké a složité aplikace s více subsystémy vyvíjejícími; v těchto případech je vhodné Investujete do složitější architektura softwaru, protože zajistí lepší dlouhodobé flexibility a údržba aplikace.

**Kontejnery pro každou aplikaci.** Kontejnery jsou vhodné pro mikroslužeb, ale nejsou výhradní pro ně. Kontejnery můžete použít taky s monolitický aplikací, včetně starší verze aplikací založena na tradiční rozhraní .NET Framework a modernized prostřednictvím Windows kontejnery. Výhody použití Docker, jako je například řešení problémů, mnoho nasazení produkční a poskytuje nejmodernější prostředí vývoje a testování, se vztahují na mnoha různých typů aplikací.

**Rozhraní příkazového řádku a IDE.** Nástroje Microsoft můžete vyvíjet kontejnerizované aplikací .NET pomocí vaší žádoucí. Můžete vyvíjet pomocí rozhraní příkazového řádku a prostředí na základě editor pomocí příkazového řádku Dockeru a Visual Studio Code. Nebo můžete použít zaměřené na IDE způsob sadou Visual Studio a její jedinečné funkce pro Docker, například jako schopnost ladění aplikace s více kontejneru.

**Odolné cloudové aplikace.** V cloudu a distribuované systémy obecně není vždy riziko částečné selhání. Vzhledem k tomu, že služby a klienti jsou samostatné procesy (kontejnerů), služba nemusí být schopné reagovat včas na žádost klienta. Například služby může být mimo provoz z důvodu částečné selhání nebo kvůli údržbě; Služba může být přetížené a reagovat na velmi pomalu požadavky; nebo ho jednoduše možná není přístupný po krátkou dobu z důvodu problémů se sítí. Aplikace založené na cloudu na proto musíte použít tyto chyby a zavedené strategie reagovat na tyto chyby. Tato strategie může obsahovat zásady opakování (odešlete zprávy nebo opakování požadavků) a implementuje vzory jistič – aby se zabránilo exponenciální načíst opakovaných požadavků. V podstatě, cloudové aplikace musí mít odolné mechanismy – buď vlastní těch, které jsou, nebo těch, které jsou založené na cloudové infrastruktury, jako je například základní architektury z orchestrators nebo sběrnice služby.

**Zabezpečení.** Naše moderní world kontejnery a mikroslužeb můžou zpřístupnit nová ohrožení zabezpečení. Zabezpečení základních aplikací je založena na ověřování a autorizace; k implementaci těchto existovat více způsobů. Kontejner zabezpečení však zahrnuje další klíčové komponenty, jejichž výsledkem ze své podstaty bezpečnější aplikace. Element kritické vytváření bezpečnější aplikace s zabezpečenou komunikaci s jiným aplikacím a systémů, něco to často vyžaduje přihlašovací údaje, tokeny, hesel a dalších typů důvěrné informace – obvykle označuje jako tajné klíče aplikace. Řešení zabezpečeného musí dodržujte doporučené postupy zabezpečení, třeba šifrování tajné klíče v průběhu přenosu; šifrované tajné klíče v klidovém stavu; a zabráněním tajné klíče, abyste zabránili úniku neúmyslně při spotřebovávají konečné aplikace. Těchto tajných klíčů je potřeba ukládat a uchovávat bezpečné, někde. Usnadní zabezpečení, můžete využít výhod infrastruktury zvolené orchestrator, nebo cloudové infrastruktury, jako je Azure Key Vault a způsoby poskytuje pro kód aplikace pro použití.

**Orchestrators.** Orchestrators kontejneru jako ty, které jsou uvedeny v Azure Container Service (Kubernetes, Mesos DC/OS a Docker Swarm) a Azure Service Fabric jsou nezbytné pro všechny aplikace na základě mikroslužbu produkční prostředí a pro všechny služby kontejneru aplikace s významné složitost, škálovatelnost potřeb a konstantní vývoj. Tato příručka obsahuje zavedla orchestrators a jejich role v řešení na základě mikroslužbu a na základě kontejneru. Pokud potřebám vaší aplikace jsou přesun směrem k komplexní kontejnerizované aplikace, najdete je užitečná k vyhledání na další zdroje dalších informací o orchestrators

>[!div class="step-by-step"]
[Předchozí](secure-net-microservices-web-applications/azure-key-vault-protects-secrets.md)
