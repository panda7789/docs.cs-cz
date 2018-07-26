---
title: Aspekty architektury bez serveru – aplikace bez serveru
description: Vysvětlení obtíže spojené s aplikační architektura založená na aplikace bez serveru, správu stavu a trvalé úložiště, pokud chcete škálovat, protokolování, sledování a diagnostiky.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8b0b5241e6bae0bb4c77451e500b6c623c206fbf
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404896"
---
# <a name="serverless-architecture-considerations"></a>Aspekty architektury bez serveru

Přijetí architektury bez serveru jsou dostupné určité problémy. Tato část popisuje některé z běžnějších požadavky je potřeba vědět. Všechny tyto výzvy mají řešení. Stejně jako u všech možností architektur, je třeba rozhodnutí do prostředí bez serveru až po pečlivého zvážení výhody a nevýhody. V závislosti na potřebách vaší aplikace můžete rozhodnout, že bez serveru implementace není má to pravé řešení pro určité součásti.

## <a name="managing-state"></a>Správa stavu

Funkce bez serveru, stejně jako u mikroslužby v obecné, jsou bezstavové ve výchozím nastavení. Nejkonkrétnější – vyhněte stavu umožňuje bez serveru bude dočasné pro horizontální navýšení kapacity a zajistit odolnost proti chybám bez centrální bod selhání. V některých případech vyžadovat obchodních procesů stavu. Pokud váš proces vyžaduje stav, máte dvě možnosti. Při přijetí modelu jiné než v případě bez serveru a práci s samostatná služba, která poskytuje stav. Přidání stavu může zkomplikovat řešení znesnadnit škálování a potenciálně vytvořit jediný bod selhání. Pečlivě zvažte, jestli vaše funkce požaduje naprosto stavu. Pokud odpověď je "Ano", určete, zda stále dává smysl pro implementaci s architekturou bez serveru.

Existuje několik řešení, která přijme stavu bez negativního vlivu výhod prostředí bez serveru. Mezi další oblíbená řešení, patří:

* Použijte dočasné úložiště dat nebo distribuované mezipaměti, jako jsou Redis
* Store stavu v databázi, jako je SQL nebo cosmos DB
* Zpracování stavu prostřednictvím modulu pracovního postupu, jako je odolná služba functions

Dolní řádek je, že byste měli vědět o nutnosti jakékoli správy stavu v rámci procesy, které byste chtěli provádět s architekturou bez serveru.

## <a name="long-running-processes"></a>Dlouho běžící procesy

Spolehněte se na procesy, které se dočasné řadu výhod prostředí bez serveru. Krátká doba spuštění usnadňují bez serveru zprostředkovatele tím se uvolní prostředky, jak funguje funkce end a sdílené složky v hostitelích. Většina poskytovatelů cloudových služeb omezení celkové doby, kterou funkci můžete spustit na přibližně 10 minut. Pokud váš proces může trvat delší dobu, můžete zvážit alternativní implementace.

Existuje pár výjimek a řešení. Jedním řešením může být ke vstupu do menších komponent, které jednotlivě trvat kratší dobu pro spuštění procesu. Pokud váš proces běží dlouho z důvodu závislosti, můžete také zvážit asynchronního pracovního postupu pomocí řešení, jako je odolná služba functions. Odolná služba functions pozastavit a Udržovat stav procesu, zatímco čekáte na externí proces dokončete. Asynchronní zpracování snižuje čas, kdy se skutečný proces běží.

## <a name="startup-time"></a>Čas spuštění

Jeden potenciální problém s implementacemi bez serveru je čas spuštění. Pokud chcete ušetřit prostředky, vytvořit mnoho poskytovatelů bez serveru infrastruktury "na vyžádání." Když funkci bez serveru se aktivuje po určitou dobu, prostředky pro hostování funkce možná muset vytvořit ani restartovat. V některých případech může způsobit zpoždění několik sekund souvisejícím s úplným spuštěním. Čas spuštění se liší od poskytovatelů a úrovně služeb. Pokud je důležité, abyste minimalizovali týkající se úspěšnosti aplikace nejsou několik přístupů na dobu spuštění adresu.

* Někteří poskytovatelé umožňují uživatelům k úhradě úrovně služeb, které zaručuje, že je infrastruktura "always on".
* Implementujte mechanismus zachování (ping koncový bod zachovat "vzhůru").
* Orchestrace, jako je Kubernetes pomocí funkce kontejnerizovaných přístup (na hostiteli se používá už tedy velmi rychlý rozbíhání nové instance).

## <a name="database-updates-and-migrations"></a>Aktualizace databáze a migrace

Výhodou kódu bez serveru je, že můžete uvolnit nové funkce bez nutnosti znovu nasadit celou aplikaci. Nevýhodou této výhody se můžou stát, když je zapojené relační databáze. Změny v databázových schématech je složité synchronizovat ho s aktualizacemi bez serveru. Další problémy se k hlasování, když se něco zvrtne a změny musí být vrácena zpět. Integritu dat je jedním z osvědčený postup pro mikroslužby a bezserverové funkce je, že vlastníte svá vlastní data. Je možné nasadit změny jako jednu jednotku výpočetních operací a data. Je, že mnoho starší verze systémů funkce velké databáze back-end, který musí být sloučeny s architekturou bez serveru.

Oblíbené přístupů k řešení správy verzí schématu je nikdy měnit existující vlastnosti a sloupce, ale místo toho přidejte nové informace. Představte si třeba změny přesunout z typu Boolean "dokončeno" příznak pro seznam úkolů "dokončené datum". Místo aby odebrala stará pole, změna databáze bude:

1. Přidejte pole nové "Completed (dokončeno datum).
1. Transformujte pole "dokončených" logická vypočítané funkci, která vyhodnotí, jestli je datum dokončení po aktuálním datu.
1. Přidání triggeru pro nastavit datum dokončení na aktuální datum, pokud je dokončené logická hodnota nastavená na hodnotu true.

Posloupnost změny zajišťuje, že starší verze kódu nadále běžel "tak jak jsou", zatímco novější funkce bez serveru můžete využít výhod nového pole.

Další informace o datech v architektur bez serveru, naleznete v tématu [výzvy a řešení pro správu dat distribuovaných](../microservices-architecture/architect-microservice-container-applications/distributed-data-management.md).

## <a name="scaling"></a>Škálování

Je to Běžná mylná představa, že bez serveru znamená "žádný server". Je ve skutečnosti "méně server". Skutečnost, že je, že je důležité pochopit, pokud jde o škálování základní infrastruktury. Většina bez serveru platformy poskytují sadu ovládacích prvků pro zpracování, jak by se měly škálovat infrastrukturu, když hustota událostí se zvyšuje. Můžete si vybrat z celé řady možností, ale vaše strategie může lišit v závislosti na funkci. Kromě toho jsou funkce obvykle běží pod související hostitele tak, aby funkce na stejném hostiteli mají stejné možnosti škálování. Proto je nezbytné pro organizaci a určit, které funkce jsou hostované podle požadavků na škálování.

Pravidla často určit způsob vertikálně navýšit kapacitu (zvýšit prostředky hostitele) a horizontální navýšení kapacity (zvýšení počtu instancí hostitele) na základě různých parametrů. Aktivační události pro škálování může zahrnovat plán, požadavků, využití procesoru a využití paměti. Často vyššího výkonu se dodává s větší náklady. Přístupy levnější, založenou na skutečné spotřebě nemůže škálovat podle rychle při frekvence požadavků prudce zvyšuje. Je kompromis mezi platit až přední "pojištění" náklady a platit výhradně "při přechodu" a neohrozit pomalejší odpovědi z důvodu náhlé zvýšení poptávky.

## <a name="monitoring-tracing-and-logging"></a>Monitorování, trasování a protokolování

Často přehlíženým aspekt DevOps je monitorování aplikací po nasazení. Je důležité mít strategii pro monitorování funkce bez serveru. Největším problémem je často korelace nebo uznání při volání více funkcí v rámci stejné interakce. Většina bez serveru platformy umožní konzoly protokolování, které se dají importovat do nástrojů třetích stran. Existují také Možnosti automatizace shromažďování telemetrických dat, generovat a sledovat ID korelace a monitorovat konkrétní akce, které poskytují podrobné přehledy. Azure poskytuje pokročilé [platformy Application Insights](https://docs.microsoft.com/azure/azure-functions/functions-monitoring) pro monitorování a analýzy.

## <a name="inter-service-dependencies"></a>Komunikace mezi službami závislosti

Využijte architekturu bez serveru může obsahovat funkce, které jsou závislé na dalších funkcí. Ve skutečnosti není běžné ve architektury bez serveru má několik služeb, které volají navzájem jako součást distribuované transakce nebo interakci. Aby se zabránilo silné párování, doporučujeme, že služby není odkazovat na sebe navzájem přímo. Když se koncový bod pro službu musí změnit, přímé odkazy by mohlo způsobit hlavní refaktoring. Navrhované řešení je mechanismus pro zjišťování služby, jako je například registru, který obsahuje příslušný koncový bod pro typ požadavku. Druhým řešením je využívat služby zasílání zpráv, například front nebo témat pro komunikaci mezi službami.

## <a name="managing-failure-and-providing-resiliency"></a>Správa selhání a zajištění odolnosti proti chybám

Je také důležité vzít v úvahu *vzoru circuit breaker*: Pokud z nějakého důvodu služba nadále selhávat, není vhodné opakovaně volání této služby. Místo toho volat alternativní služby nebo zpráva vrácená dokud stavu ze závislých služeb je obnoveno. Architektura bez serveru je potřeba vzít v úvahu strategie pro řešení a správu komunikace mezi službami závislosti.

Pokračujte vzoru circuit breaker musí být odolnost proti chybám a odolných služeb. Odolnost proti chybám odkazuje na schopnosti vaší aplikace, aby kontinuálně běžely, i po neočekávané výjimky nebo se zjistil neplatný stavy. Odolnost proti chybám je obvykle funkce samotného kódu a jak ho zapsala do zpracování výjimek. Odolnost proti chybám odkazuje na je aplikace jak podporující na obnovení v případě selhání. Odolnost proti chybám je často spravuje platforma bez serveru. Abyste mohli spustit novou instanci funkce bez serveru při selhání stávající měl platformu. Platforma by měla být dostatečně inteligentní, zastaví rozbíhání nové instance, pokud selže každé nové instance.

Další informace najdete v tématu [implementace vzoru Circuit Breaker](../microservices-architecture/implement-resilient-applications/implement-circuit-breaker-pattern.md).

## <a name="versioning-and-greenblue-deployments"></a>Nasazení správy verzí a zelená/modrá

Hlavní výhodou bez serveru je možný upgrade konkrétní funkce, aniž byste museli znovu nasadit celou aplikaci. Pro upgrade proběhne úspěšně musí být funkce označené verzí tak, aby jejich volání služby jsou směrovány na správnou verzi kódu. Strategie pro zavedení nové verze je také důležité. Běžným přístupem je použití "zelené a modré nasazení." Zeleného nasazení je aktuální funkce. Nová verze "blue" je nasazená do produkčního prostředí a testování. Při testování PASS, zelené a modré verze jsou přehozeny tak novou verzi se dodává za provozu. Pokud nedojde k žádné problémy, je možné Prohodit zpět. Podpora správy verzí a nasazení zelené a modré vyžaduje kombinaci funkcí a vyřešit tak změny verze pro vytváření a práci s architekturou pro zpracování nasazení. Jedním z možných způsobů je použít proxy servery, které jsou popsány v [./azure-functions.md](Azure serverless platform) kapitoly.

>[!div class="step-by-step"]
[Předchozí](serverless-architecture.md)
[další](serverless-design-examples.md)