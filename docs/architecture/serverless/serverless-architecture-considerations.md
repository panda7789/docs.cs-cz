---
title: Aspekty architektury bez serveru - Aplikace bez serveru
description: Seznamte se s výzvami, které jsou výzvou navrhování aplikací bez serveru, od správy stavu a trvalého úložiště až po škálování, protokolování, trasování a diagnostiku.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: c856683cf6910be98661e634246cd003b93a6d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522426"
---
# <a name="serverless-architecture-considerations"></a>Důležité informace o bezserverové architektuře

Přijetí architektury bez serveru přichází s určitými výzvami. Tato část popisuje některé z běžnějších aspektů, které je třeba znát. Všechny tyto výzvy mají řešení. Stejně jako u všech možností architektury by rozhodnutí jít bez serveru mělo být provedeno pouze po pečlivém zvážení klady a zápory. V závislosti na potřebách vaší aplikace se můžete rozhodnout, že implementace bez serveru není pro určité součásti správným řešením.

## <a name="managing-state"></a>Správa stavu

Funkce bez serveru, stejně jako u mikroslužeb obecně, jsou bezstavové ve výchozím nastavení. Vyhnout se stavu umožňuje bez serveru být dočasný, horizontální navýšení kapacity a poskytnout odolnost proti chybám bez centrální bod selhání. V některých případech vyžadují obchodní procesy stav. Pokud proces vyžaduje stav, máte dvě možnosti. Můžete přijmout jiný model než bez serveru nebo pracovat se samostatnou službou, která poskytuje stav. Přidání stavu může zkomplikovat řešení a ztížit škálování a potenciálně vytvořit jeden bod selhání. Pečlivě zvažte, zda vaše funkce absolutně vyžaduje stav. Pokud je odpověď "ano", zjistěte, zda má stále smysl implementovat ji bez serveru.

Existuje několik řešení, jak přijmout stav bez ohrožení výhod bez serveru. Některé z více populárních řešení patří:

- Použití dočasného úložiště dat nebo distribuované mezipaměti, například Redis
- Stav úložiště v databázi, jako je SQL nebo CosmosDB
- Zpracování stavu prostřednictvím modulu pracovního postupu, jako jsou odolné funkce

Pointa je, že byste měli být vědomi potřeby pro všechny správy stavu v rámci procesů, které uvažujete o implementaci s bez serveru.

## <a name="long-running-processes"></a>Dlouhotrvající procesy

Mnoho výhod bez serveru závisí na procesech dočasných. Krátké časy běhu usnadňují poskytovateli bez serveru uvolnit prostředky jako funkce ukončení a sdílení funkcí mezi hostiteli. Většina poskytovatelů cloudu omezuje celkovou dobu, po kterou může vaše funkce běžet, na přibližně 10 minut. Pokud váš proces může trvat déle, můžete zvážit alternativní implementaci.

Existuje několik výjimek a řešení. Jedním z řešení může být rozdělit proces do menších součástí, které jednotlivě trvat kratší dobu ke spuštění. Pokud váš proces běží dlouho z důvodu závislostí, můžete také zvážit asynchronní pracovní postup pomocí řešení, jako jsou trvalé funkce. Trvalé funkce pozastavují a udržují stav procesu, zatímco čeká na dokončení externího procesu. Asynchronní zpracování zkracuje dobu spuštění skutečného procesu.

## <a name="startup-time"></a>Čas spuštění

Jedním z potenciálních obav z implementace bez serveru je čas spuštění. Pro úsporu zdrojů mnoho poskytovatelů bez serveru vytváří infrastrukturu "na vyžádání". Pokud je funkce bez serveru spuštěna po určité době, může být nutné vytvořit nebo restartovat prostředky pro hostování funkce. V některých situacích mohou studené starty způsobit zpoždění několika sekund. Doba spouštění se v jednotlivých zprostředkovatelích a úrovních služeb liší. Existuje několik přístupů k řešení času spuštění, pokud je důležité minimalizovat pro úspěch aplikace.

- Někteří poskytovatelé umožňují uživatelům platit za úrovně služeb, které zaručují, že infrastruktura je "vždy zapnutá".
- Implementujte mechanismus udržování (ping koncový bod, aby byl "vzhůru").
- Použijte orchestraci jako Kubernetes s kontejnerizovaným přístupem funkce (hostitel je již spuštěn, takže předení nových instancí je velmi rychlé).

## <a name="database-updates-and-migrations"></a>Aktualizace a migrace databáze

Výhodou kódu bez serveru je, že můžete uvolnit nové funkce bez nutnosti znovu nasadit celou aplikaci. Tato výhoda se může stát nevýhodou, pokud se jedná o relační databázi. Změny schémat databáze je obtížné synchronizovat s aktualizacemi bez serveru. Další výzvy jsou kladeny, když se něco pokazí a změny musí být vráceny zpět. Integrita dat je jedním z důvodů, že osvědčeným postupem pro mikroslužeb a bezserverové funkce je, že vlastní vlastní data. Je možné nasadit změny jako jednu jednotku výpočetních prostředků a dat. Skutečností je, že mnoho starších systémů obsahuje velkou databázi back-end, která musí být sladěna s architekturou bez serveru.

Populární přístup k řešení správy verzí schématu je nikdy upravit existující vlastnosti a sloupce, ale místo toho přidat nové informace. Zvažte například změnu pro přesun z logického příznaku dokončení seznamu úkolů na "datum dokončení". Namísto odebrání starého pole bude změna databáze:

1. Přidejte nové pole "datum dokončení".
1. Transformujte "dokončené" logické pole na vypočítanou funkci, která vyhodnocuje, zda je datum dokončení po aktuálním datu.
1. Přidejte aktivační událost pro nastavení dokončeného data na aktuální datum, kdy je dokončená logická hodnota nastavena na hodnotu true.

Posloupnost změn zajišťuje, že starší kód bude nadále spuštěn "tak, jak je", zatímco novější bezserverové funkce mohou využít nové pole.

Další informace o datech v architekturách bez serveru naleznete v [tématu Výzvy a řešení pro správu distribuovaných dat](../microservices/architect-microservice-container-applications/distributed-data-management.md).

## <a name="scaling"></a>Škálování

Je to běžná mylná představa, že bez serveru znamená "žádný server". Je to ve skutečnosti "méně server." Skutečnost, že existuje záložní infrastruktura, je důležité pochopit, pokud jde o škálování. Většina platforem bez serveru poskytuje sadu ovládacích prvků pro zpracování toho, jak by měla infrastruktura škálovat, když se zvýší hustota událostí. Můžete si vybrat z různých možností, ale vaše strategie se může lišit v závislosti na funkci. Kromě toho funkce jsou obvykle spuštěny pod související hostitele, tak, aby funkce na stejném hostiteli mají stejné možnosti škálování. Proto je nutné uspořádat a strategii, které funkce jsou hostovány společně na základě požadavků na škálování.

Pravidla často určují, jak vertikálně navýšit kapacitu (zvýšit prostředky hostitele) a horizontální navýšení kapacity (zvýšit počet instancí hostitele) na základě různých parametrů. Aktivační události pro škály mohou zahrnovat plán, sazby požadavků, využití procesoru a využití paměti. Vyšší výkon často přichází s vyššími náklady. Levnější přístupy založené na spotřebě se nemusí škálovat tak rychle, když se náhle zvýší míra požadavků. Tam je kompromis mezi placenídopředu "náklady na pojištění" versus platit přísně "as you go" a riskovat pomalejší reakce v důsledku náhlého zvýšení poptávky.

## <a name="monitoring-tracing-and-logging"></a>Monitorování, trasování a protokolování

Často přehlíženy aspekt DevOps je monitorování aplikací po nasazení. Je důležité mít strategii pro monitorování funkcí bez serveru. Největší výzvou je často korelace, nebo rozpoznání, když uživatel volá více funkcí jako součást stejné interakce. Většina platforem bez serveru umožňuje protokolování konzoly, které lze importovat do nástrojů třetích stran. Existují také možnosti, jak automatizovat shromažďování telemetrických dat, generovat a sledovat ID korelace a sledovat konkrétní akce, které poskytují podrobné přehledy. Azure poskytuje pokročilou [platformu Application Insights](https://docs.microsoft.com/azure/azure-functions/functions-monitoring) pro monitorování a analýzy.

## <a name="inter-service-dependencies"></a>Závislosti mezi službami

Architektura bez serveru může zahrnovat funkce, které jsou závislé na jiných funkcích. Ve skutečnosti není neobvyklé v architektuře bez serveru mít více služeb, které se navzájem volají jako součást interakce nebo distribuované transakce. Chcete-li se vyhnout silné muka, doporučujese, aby služby neodkazovali navzájem přímo. Když koncový bod pro službu potřebuje změnit, přímé odkazy může mít za následek hlavní refaktoring. Navrhované řešení je poskytnout mechanismus zjišťování služby, jako je například registr, který poskytuje odpovídající koncový bod pro typ požadavku. Dalším řešením je využít služby zasílání zpráv, jako jsou fronty nebo témata pro komunikaci mezi službami.

## <a name="managing-failure-and-providing-resiliency"></a>Řízení selhání a zajištění odolnosti proti chybám

Je také důležité vzít v úvahu *schéma jističe*: Pokud z nějakého důvodu služba nadále selhává, není vhodné tuto službu volat opakovaně. Místo toho je volána alternativní služba nebo zpráva vrácena, dokud není obnoven stav závislé služby. Architektura bez serveru musí brát v úvahu strategii pro řešení a správu závislostí mezi službami.

Chcete-li pokračovat ve vzoru jističe, musí být služby odolné proti chybám a odolné. Odolnost proti chybám odkazuje na schopnost aplikace pokračovat v běhu i po výskytu neočekávaných výjimek nebo neplatných stavů. Odolnost proti chybám je obvykle funkce samotného kódu a jak je zapsán pro zpracování výjimek. Odolnost proti chybám odkazuje na to, jak schopná je aplikace zotavit se z chyb. Odolnost proti chybám je často spravována platformou bez serveru. Platforma by měla být schopna střídat novou instanci funkce bez serveru, když se nezdaří stávající. Platforma by měla být také dostatečně inteligentní, aby přestala střídat nové instance, když se nezdaří každá nová instance.

Další informace naleznete v [tématu Implementace vzoru jističe](../microservices/implement-resilient-applications/implement-circuit-breaker-pattern.md).

## <a name="versioning-and-greenblue-deployments"></a>Správa verzí a zelená/modrá nasazení

Hlavní výhodou bez serveru je možnost upgradovat určitou funkci bez nutnosti znovu nasadit celou aplikaci. Aby byly upgrady úspěšné, musí být funkce verzí, aby služby, které je volají, byly směrovány na správnou verzi kódu. Strategie pro nasazení nových verzí je také důležité. Běžným přístupem je použití "zelených/modrých nasazení". Zelené nasazení je aktuální funkce. Nová "modrá" verze je nasazena do produkčního prostředí a testována. Při testování projde, zelené a modré verze jsou vyměněny tak nová verze přichází žít. Pokud dojde k nějaké problémy, mohou být vyměněny zpět. Podpora správy verzí a nasazení zeleno-modré vyžaduje kombinaci vytváření funkcí pro přizpůsobení změn verzí a práce s platformou bez serveru pro zpracování nasazení. Jedním z možných přístupů je použití proxy serverů, které jsou popsány v kapitole [platformy Azure bez serveru.](azure-functions.md#proxies)

>[!div class="step-by-step"]
>[Předchozí](serverless-architecture.md)
>[další](serverless-design-examples.md)
