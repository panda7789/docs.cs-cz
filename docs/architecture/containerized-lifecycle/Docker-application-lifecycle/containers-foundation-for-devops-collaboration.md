---
title: Kontejnery jako základ pro spolupráci DevOps
description: Pochopte klíčovou roli kontejnerů, abyste zjednodušili DevOps.
ms.date: 08/06/2020
ms.openlocfilehash: af28c1add8b2e6befbd2f3e6ae9fe707ccc5b106
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916015"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>Kontejnery jako základ pro spolupráci DevOps

Díky velmi povaze kontejnerů a technologii Docker mohou vývojáři sdílet svůj software a závislosti snadno pomocí provozu IT a produkčních prostředí a zároveň odstranit typické možnosti "funguje na mém počítači" výmluvou. Kontejnery řeší konflikty aplikací mezi různými prostředími. Nepřímo, kontejnery a Docker přinášejí vývojářům a IT operace společně, což usnadňuje spolupráci. Přijetí pracovního postupu kontejneru poskytuje mnoho zákazníků s DevOps kontinuitou, kterou si vyžádal, ale dříve museli implementovat složitější konfiguraci pro kanály vydaných verzí a sestavení. Kontejnery zjednodušují kanály pro sestavování, testování a nasazování v DevOps.

![Diagram znázorňující vlastnictví životního cyklu aplikace Docker.](./media/containers-foundation-for-devops-collaboration/persona-workloads-docker-container-lifecycle.png)

**Obrázek 2-1.** Hlavní úlohy na "osoby" v životním cyklu pro kontejnerované aplikace Docker

Pomocí kontejnerů Docker můžou vývojáři dělat, co je v rámci kontejneru (aplikace a služby, závislosti na architekturách a komponent) a jak se budou kontejnery a služby chovat společně jako aplikace, která se skládá z kolekce služeb. Vzájemné závislosti v rámci více kontejnerů jsou definovány v `docker-compose.yml` souboru nebo jako *manifest nasazení*. Provozní týmy IT (IT specialisté a správa) se tak můžou zaměřit na správu produkčních prostředí. infrastrukturu škálovatelnost sledovaný a nakonec zajišťuje správné doručování aplikací koncovým uživatelům, aniž byste museli znát obsah různých kontejnerů. Proto název "kontejner", "znovu volá analogii na skutečné přepravní kontejnery. Proto si vlastníci obsahu kontejneru nemusí zabývat tím, jak se kontejner dokončí, a společnost pro expedici přesměruje kontejner z místa původu do svého umístění, aniž by k tomu věděl nebo caring obsah. Podobným způsobem můžou vývojáři vytvořit a vlastnit obsah v kontejneru Docker, aniž by se museli zabývat mechanismem přenosu.

V pilíři na levé straně obrázku 2-1 vývojáři zapisují a spouštějí kód místně v kontejnerech Docker pomocí Docker for Windows nebo Mac. Definují operační prostředí pro kód pomocí souboru Dockerfile, který určuje základní operační systém, který se má spustit, a kroky sestavení pro sestavení kódu do image Docker. Vývojáři definují, jak bude jeden nebo více imagí spolupracovat pomocí výše uvedeného `docker-compose.yml` manifestu nasazení souboru. Jak dokončí svůj místní vývoj, načtou svůj aplikační kód a konfigurační soubory Docker do úložiště kódu podle svého výběru (tzn. úložiště Git).

Pilíř DevOps definuje kanály sestavení – kontinuální integrace (CI) s využitím souboru Dockerfile, které jsou k dispozici v úložišti kódu. Systém CI načte základní image kontejneru z vybraného registru Docker a vytvoří vlastní image Docker pro aplikaci. Bitové kopie pak budou ověřeny a vloženy do registru Docker, který se používá pro nasazení do více prostředí.

V rámci pilíře na pravé straně provozní týmy spravují nasazené aplikace a infrastrukturu v produkčním prostředí a při monitorování prostředí a aplikací tak, aby mohli poskytovat zpětnou vazbu a poznatky vývojovému týmu o tom, jak může být aplikace Vylepšená. Aplikace typu kontejner jsou obvykle spouštěny v produkčním prostředí pomocí orchestrací kontejnerů, jako je [Kubernetes](https://kubernetes.io/), kde se obvykle používají [grafy Helm](https://helm.sh/) ke konfiguraci jednotek nasazení místo souborů Docker-skládání.

Tyto dva týmy spolupracují na základní platformě (Docker Containers), která poskytuje oddělení obav jako kontrakt, a přitom významně vylepšuje spolupráci dvou týmů v životním cyklu aplikace. Vývojáři vlastní obsah kontejneru, jeho operační prostředí a mezizávislosti kontejneru, zatímco týmy provozu přebírají sestavené image společně s manifestem a spouštějí je v systému orchestrace.

## <a name="challenges-in-the-application-life-cycle-when-using-docker"></a>Problémy v životním cyklu aplikace při použití Docker.

Existuje mnoho důvodů, které zvýší počet kontejnerových aplikací v nadcházejících letech. jedním z těchto důvodů je vytváření aplikací založených na mikroslužbách.

Během posledních 15 let bylo použití webových služeb základem tisíců aplikací a pravděpodobně po několika letech se stejnou situaci týkají aplikací založených na mikroslužbách spuštěných v kontejnerech Docker.

Také je třeba uvést, že můžete také použít kontejnery Docker pro aplikace monolitické a stále získáte většinu výhod Docker. Kontejnery necílí jenom na mikroslužby.

Použití kontejnerů Docker a mikroslužeb způsobuje nové problémy v procesu vývoje vaší organizace. Proto potřebujete plnou strategii pro udržení mnoha kontejnerů a mikroslužeb spuštěných v produkčních systémech. Nakonec budou mít podnikové aplikace stovky nebo tisíce kontejnerů/instancí spuštěných v produkčním prostředí.

Tyto výzvy vytvářejí nové požadavky při použití nástrojů DevOps, takže budete muset definovat nové procesy ve svých aktivitách DevOps a vyhledat odpovědi na následující typy otázek:

- Jaké nástroje můžu použít pro vývoj, CI/CD, správu a operace?

- Jak může IT společnost spravovat chyby v kontejnerech při spuštění v produkčním prostředí?

- Jak můžeme změnit části našeho softwaru v produkčním prostředí s minimálním výpadkem?

- Jak můžu škálovat a monitorovat Náš produkční systém?

- Jak můžeme do našeho kanálu vydaných verzí zahrnout testování a nasazení kontejnerů?

- Jak můžeme používat Open Source nástroje/platformy pro kontejnery v Microsoft Azure?

Pokud můžete odpovědět na všechny tyto otázky, budete lépe připraveni přesunout své aplikace (existující nebo nové aplikace) do kontejnerů Docker.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Seznámení s obecným pracovním postupem pro kompletní životní cyklus aplikací Docker

Obrázek 2-2 představuje podrobnější pracovní postup pro životní cyklus aplikací Docker a zaměřuje se na tuto instanci na konkrétní DevOps aktivity a prostředky.

![Diagram znázorňující obecný životní cyklus kompletního životního cyklu aplikace Docker.](./media/containers-foundation-for-devops-collaboration/generic-end-to-enddpcker-app-life-cycle.png)

**Obrázek 2-2.** Pracovní postup na vysoké úrovni pro životní cyklus aplikací Docker v kontejneru

Vše začíná vývojářem, který spustí psaní kódu v pracovním postupu s vnitřní smyčkou. Fáze Inner smyčky je tam, kde vývojáři definují všechno, co se stane před vložením kódu do úložiště kódu (například do systému správy zdrojového kódu, jako je git). Po potvrzení úložiště spustí průběžnou integraci (CI) a zbytek pracovního postupu.

Vnitřní smyčka se skládá z typických kroků, jako je "kód", "běh", "test" a "ladění" a další kroky, které jsou potřeba hned před tím, než aplikaci spustíte místně. Toto je proces vývojáře pro spuštění a testování aplikace jako kontejneru Docker. Pracovní postup vnitřní smyčky bude vysvětlen v následujících částech.

Když se vrátíte zpět k zobrazení kompletního pracovního postupu, pracovní postup DevOps je více než technologie nebo sada nástrojů, jedná se o místo, který vyžaduje kulturní vývoj. Jedná se o osoby, procesy a příslušné nástroje, díky kterým je životní cyklus aplikace rychlejší a předvídatelný. Podniky, které přijmou kontejnerový pracovní postup obvykle přestrukturují své organizace tak, aby představovali lidi a procesy, které odpovídají zadanému pracovnímu postupu.

Praktické DevOps může přispět k tomu, že týmy rychleji reagují na konkurenční tlak tím, že nahrazuje ruční procesy náchylné k chybám díky automatizaci, což vede k lepší sledovatelnosti a k opakovaným pracovním postupům. Organizace také mohou spravovat prostředí efektivněji a realizovat úspory nákladů pomocí kombinace místních a cloudových prostředků a také úzce integrovaných nástrojů.

Při implementaci pracovního postupu DevOps pro aplikace Docker uvidíte, že technologie Docker jsou přítomny v téměř všech fázích pracovního postupu, a to z vašeho vývojového pole při práci na vnitřní smyčce (kód, spuštění, ladění), fázi sestavení-test-CI a nakonec na nasazení těchto kontejnerů do pracovních a produkčních prostředí.

Zlepšení postupů kvality pomáhá odhalit vady v předstihu v cyklu vývoje, což snižuje náklady na jejich opravu. Zahrnutím prostředí a závislostí do image a přijetím filozofie nasazení stejné image napříč různými prostředími povýšíte obor extrakce konfigurací specifických pro prostředí, které usnadňují nasazení.

Bohatá data získaná prostřednictvím efektivní instrumentace (monitorování a Diagnostika) poskytují přehled o problémech s výkonem a chování uživatelů při plánování budoucích priorit a investic.

DevOps by měla být považována za cestu, nikoli cíl. Měl by se implementovat přírůstkově prostřednictvím odpovídajících projektů vymezených v oboru, ze kterých můžete Ukázat úspěch, seznámení a vývoj.

## <a name="benefits-of-devops-for-containerized-applications"></a>Výhody DevOps pro kontejnerové aplikace

Tady jsou některé z nejdůležitějších výhod poskytovaných plným pracovním postupem DevOps:

- Poskytněte lepší kvalitu softwaru, rychlejší a lepší dodržování předpisů.

- Průběžné vylepšování a úpravy byly dřívější a efektivnější.

- Zvyšte transparentnost a spolupráci mezi zúčastněnými stranami zapojenými do poskytování a provozního softwaru.

- Řízení nákladů a využívání zřizovacích prostředků efektivněji při minimalizaci rizik zabezpečení.

- Zapojte se do technologie Plug and Play a spoustu vašich stávajících investic do DevOps, včetně investic do Open Source.

>[!div class="step-by-step"]
>[Předchozí](index.md) 
> [Další](../Microsoft-platform-tools-containerized-apps/index.md)
