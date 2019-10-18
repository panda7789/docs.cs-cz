---
title: Požadavky na architekturu bez serveru – aplikace bez serveru
description: Seznamte se s problémy při navrhování aplikací bez serveru, od správy stavů a trvalého úložiště pro škálování, protokolování, trasování a diagnostiku.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c856683cf6910be98661e634246cd003b93a6d76
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522426"
---
# <a name="serverless-architecture-considerations"></a>Důležité informace o bezserverové architektuře

Při přijetí architektury bez serveru se dokončí některé problémy. V této části se seznámíte s některými častými požadavky, které je třeba znát. Všechny tyto výzvy mají řešení. Stejně jako u všech možností architektury by rozhodnutí o použití bez serveru mělo být provedeno až po pečlivém zvážení specialistů a nevýhody. V závislosti na potřebách vaší aplikace se můžete rozhodnout, že implementace bez serveru není správného řešení pro určité součásti.

## <a name="managing-state"></a>Správa stavu

Funkce bez serveru, stejně jako u mikroslužeb obecně, jsou ve výchozím nastavení bezstavové. Zamezení stavu umožňuje neprovádět dočasné navýšení kapacity bez serveru, škálovat je a zajistit odolnost bez centrálního bodu selhání. V některých případech obchodní procesy vyžadují stav. Pokud váš proces vyžaduje stav, máte dvě možnosti. Můžete použít jiný model než bez serveru nebo pracovat se samostatnou službou, která poskytuje stav. Přidáním stavu můžete řešení zkomplikovat a ztížit jeho škálování a potenciálně vytvořit jediný bod selhání. Pečlivě zvažte, jestli vaše funkce naprosto vyžaduje stav. Pokud je odpověď "Ano", určí, jestli je stále vhodná pro implementaci bez serveru.

Existuje několik řešení, která je potřeba přijmout, aniž byste ohrozili výhody bez serveru. Mezi oblíbená řešení patří:

- Použít dočasné úložiště dat nebo distribuovanou mezipaměť, jako je Redis
- Uložení stavu v databázi, jako je SQL nebo CosmosDB
- Stav zpracování prostřednictvím modulu pracovního postupu, jako jsou trvalé funkce

Dolním řádkem je, že byste měli znát potřebu jakékoli správy stavů v rámci procesů, které zvažujete k implementaci bez serveru.

## <a name="long-running-processes"></a>Dlouhotrvající procesy

Mnohé výhody bez serveru se spoléhají na procesy, které jsou v dočasném případě. Krátkou dobu běhu usnadňuje poskytovateli bez serveru uvolnění prostředků jako funkcí end a sdílení funkcí napříč hostiteli. Většina poskytovatelů cloudu omezuje celkovou dobu, po kterou může být funkce spuštěná přibližně na 10 minut. Pokud váš proces může trvat delší dobu, můžete zvážit alternativní implementaci.

Existuje několik výjimek a řešení. Jedním z řešení může být přerušit proces na menší součásti, které jsou jednotlivě časově spouštěny. Pokud proces běží dlouho z důvodu závislostí, můžete také zvážit asynchronní pracovní postup pomocí řešení, jako jsou trvalé funkce. Trvalé funkce se pozastaví a udržují stav procesu, zatímco čeká na dokončení externího procesu. Asynchronní zpracování zkracuje čas skutečného spuštění procesu.

## <a name="startup-time"></a>Čas spuštění

Jedním z možných obav s implementacemi bez serveru je čas spuštění. Pro zachování prostředků mnoho poskytovatelů bez serveru vytvoří infrastrukturu "na vyžádání". Pokud se po uplynutí určité doby aktivuje funkce bez serveru, může být potřeba vytvořit nebo restartovat prostředky pro hostování funkce. V některých situacích může studené zahájení způsobit zpoždění v několika sekundách. Čas spuštění se liší mezi poskytovateli a úrovněmi služeb. K dispozici je několik přístupů, které řeší dobu spuštění, pokud je důležité minimalizovat úspěšnost aplikace.

- Někteří poskytovatelé umožňují uživatelům platit za úrovně služeb, které zaručují infrastrukturu "Always On".
- Implementujte mechanismus Keep-Alive (pomocí příkazu příkazového koncového bodu otestujte koncový bod a zachovejte ho).
- Použijte orchestraci jako Kubernetes s přístupem k vydaným funkcím (hostitel už je spuštěný, takže rozchází nové instance je velmi rychlé).

## <a name="database-updates-and-migrations"></a>Aktualizace a migrace databáze

Výhodou kódu bez serveru je, že můžete uvolnit nové funkce, aniž byste museli znovu nasazovat celou aplikaci. Tato výhoda se může stát nevýhodou, když se účastní relační databáze. Změny v schématech databáze je obtížné synchronizovat s aktualizacemi bez serveru. K dalším problémům dochází, když se něco nepovede a změny se musí vrátit zpátky. Integrita dat je jedním z důvodů, že pro mikroslužby a funkce bez serveru je vhodné, aby si vlastní data. Změny je možné nasadit jako jednu jednotku výpočetních prostředků a dat. Realitou je, že mnoho starších systémů funguje jako Velká databáze back-end, která musí být odsouhlasena s architekturou bez serveru.

Oblíbeným přístupem k řešení správy verzí schématu je nikdy Neupravovat stávající vlastnosti a sloupce, ale místo toho přidat nové informace. Zvažte například změnu pro přesun z logického příznaku "dokončeno" pro seznam TODO na "datum dokončení". Místo odebrání starého pole bude tato změna databáze:

1. Přidejte nové pole "datum dokončení".
1. Transformujte pole "dokončeno" Boolean na vypočtenou funkci, která vyhodnotí, zda je datum dokončení po aktuálním datu.
1. Přidejte Trigger, který nastaví datum dokončení na aktuální datum, kdy je dokončená logická hodnota nastavena na true (pravda).

Sekvence změn zajišťuje, že starší verze kódu nadále běží "tak jak jsou", zatímco novější funkce bez serveru můžou využít nové pole.

Další informace o datech v architekturách bez serveru najdete v tématu [výzvy a řešení pro správu distribuovaných dat](../microservices/architect-microservice-container-applications/distributed-data-management.md).

## <a name="scaling"></a>Změně

Jedná se o běžný nepojmový koncept, který znamená bez serveru. Je ve skutečnosti "méně serveru". Je důležité, abyste pochopili, že při škálování dojde k tomu, že budete vědět, co je záložní infrastruktura. Většina platforem bez serveru poskytuje sadu ovládacích prvků, které zpracovávají, jak by se měla infrastruktura škálovat při zvyšování hustoty událostí. Můžete si vybrat z nejrůznějších možností, ale vaše strategie se může lišit v závislosti na funkci. Kromě toho jsou funkce obvykle spouštěny v rámci souvisejícího hostitele, takže funkce na stejném hostiteli mají stejné možnosti škálování. Proto je nutné organizovat a strategize, které funkce jsou hostovány společně na základě požadavků na škálování.

Pravidla často určují způsob horizontálního navýšení kapacity (zvýšení počtu prostředků hostitele) a horizontální navýšení kapacity (zvýšení počtu instancí hostitele) na základě různých parametrů. Aktivační události pro škálování můžou zahrnovat plán, sazby požadavků, využití procesoru a využití paměti. Vyšší výkon často přináší větší náklady. Levnější přístupy založené na spotřebě se nemusí škálovat tak rychle, když se míra požadavků náhle rozroste. Existuje kompromis mezi platbou předem před "náklady na pojištění" a riziky pomalejších reakcí z důvodu náhlého nárůstu zatížení.

## <a name="monitoring-tracing-and-logging"></a>Monitorování, trasování a protokolování

Často přehlédnutíný aspekt DevOps je monitorování aplikací po nasazení. Je důležité mít strategii pro monitorování funkcí bez serveru. Největší výzvou je často korelace nebo rozpoznávání, když uživatel volá více funkcí jako součást stejné interakce. Většina platforem bez serveru umožňuje protokolování konzoly, které lze importovat do nástrojů třetích stran. K dispozici jsou také možnosti pro automatizaci shromažďování telemetrie, generování a sledování ID korelace a sledování konkrétních akcí, které poskytují podrobné přehledy. Azure poskytuje pokročilou [Application Insights platformu](https://docs.microsoft.com/azure/azure-functions/functions-monitoring) pro monitorování a analýzu.

## <a name="inter-service-dependencies"></a>Závislosti mezi službami

Architektura bez serveru může zahrnovat funkce, které spoléhají na jiné funkce. Ve skutečnosti se nejedná o architekturu bez serveru, aby mohla více služeb navzájem volat v rámci interakce nebo distribuované transakce. Aby se zabránilo silnému propojení, doporučujeme, aby se služby přímo neodkazovaly na sebe. Pokud je potřeba změnit koncový bod služby, může přímý odkaz vést k významnému refaktoringu. Navrhovaným řešením je poskytnout mechanismus zjišťování služby, jako je například registr, který poskytuje příslušný koncový bod pro typ požadavku. Dalším řešením je využít služby zasílání zpráv, jako jsou fronty nebo témata pro komunikaci mezi službami.

## <a name="managing-failure-and-providing-resiliency"></a>Správa selhání a zajištění odolnosti

Je také důležité vzít v úvahu *model přerušení okruhu*: Pokud z nějakého důvodu dojde k selhání služby, není vhodné tuto službu volat opakovaně. Místo toho se zavolá alternativní služba nebo se vrátí zpráva, dokud není znovu vytvořen stav závislé služby. Architektura bez serveru musí vzít v úvahu strategii pro řešení a správu závislostí mezi službami.

Aby bylo možné pokračovat ve vzorku okruhu, je nutné, aby služba byla odolná proti chybám a odolná. Odolnost proti chybám znamená schopnost vaší aplikace pokračovat v běhu i po neočekávaných výjimkách nebo při zjištění neplatných stavů. Odolnost proti chybám je obvykle funkcí samotného kódu a způsobu jejich zápisu pro zpracování výjimek. Odolnost proti chybám označuje, jak může aplikace při obnovování selhat. Odolnost proti chybám je často spravovaná platformou bez serveru. Platforma by měla být schopná aktivovat novou instanci funkce bez serveru, když se stávající instance nezdařila. Platforma by měla být také inteligentní, aby zastavila nové instance, když dojde k chybě každé nové instance.

Další informace najdete v tématu [implementace vzoru pro přerušení okruhů](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md).

## <a name="versioning-and-greenblue-deployments"></a>Nasazování verzí a zelených a modrých nasazení

Hlavní výhodou bez serveru je možnost upgradovat konkrétní funkci, aniž by bylo nutné znovu nasazovat celou aplikaci. Aby bylo možné upgrady provést, musí být funkce zavedeny se správou verzí, aby je služba volající je směrovala na správnou verzi kódu. Strategie pro nasazení nových verzí je taky důležitá. Běžným přístupem je použití zelených a modrých nasazení. Zeleným nasazením je aktuální funkce. Nová "modrá" verze se nasadí do produkčního a testovaného. Při testování projde zelená a modrá verze, takže nová verze bude živá. Pokud se vyskytnou nějaké problémy, můžou se znovu zaměnit. Podpora správy verzí a zelených a modrých nasazení vyžaduje kombinaci vytváření funkcí pro přizpůsobení změn verzí a práci s platformou bez serveru pro zpracování nasazení. Jedním z možných způsobů je použití proxy serverů, které jsou popsané v kapitole [platforma bez serveru Azure](azure-functions.md#proxies) .

>[!div class="step-by-step"]
>[Předchozí](serverless-architecture.md)
>[Další](serverless-design-examples.md)
