---
title: Kontejnery jako základ pro spolupráci DevOps
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: ccc8ef765cadfec31a2f714767d8e6eb76508093
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126624"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>Kontejnery jako základ pro spolupráci DevOps

Podle povahy kontejnery a technologie Dockeru vývojáři mohou jejich software a závislosti snadné sdílení s IT oddělení a produkční prostředí a nemusíte typické excuse "to funguje na mém počítači". Kontejnery řešení konfliktů aplikací mezi různými prostředími. Nepřímo kontejnery a Docker pohromadě vývojářům a IT operace blíže snadnější je efektivní spolupráci. Mnoho zákazníků přechodu pracovního postupu kontejneru poskytuje kontinuitu DevOps jsme chtěli ale dříve museli implementovat prostřednictvím složitější konfigurace pro vydání a sestavit kanály. Kontejnery zjednodušují kanály sestavení, testování a nasazení na DevOps.

![](./media/image1.png)

Obrázek 2 – 1: Hlavní úlohy za "osob" v životní cyklus kontejnerizované aplikace Dockeru

S kontejnery Dockeru, vývojáři vlastní co je v rámci kontejneru (aplikace a služby a závislostí architektury a komponenty) a kontejnery a služby chování společně jako aplikace vytváří kolekce služeb. Vzájemné závislosti z několika kontejnerů jsou definovány v souboru docker-compose.yml nebo co může být volána *manifest nasazení*. Mezitím provozní týmy IT (Odborníci v oblasti IT a správy) soustředit se na správu produkční prostředí; infrastruktury škálovatelnost; monitorování; a nakonec, zajištění, že aplikace přinášejí správně pro koncové uživatele, aniž by museli znát obsah různých kontejnerů. Proto název "kontejneru," vrací analogie reálné kontejnery. Díky tomu se vlastníci obsahu kontejneru nemusí vztahovat na s jak budou dostupné kontejneru a přenosů přenosy společnosti kontejneru z jejich původního bodu na cílové umístění bez vědomí nebo caring o obsahu. Vývojáři podobným způsobem můžete vytvořit a vlastní obsah v rámci kontejneru Dockeru bez nutnosti starat mechanismy "přenos".

V pilíř na levé straně obrázek 2-1 vývojáři psání a spouštění kódu místně v kontejnery Dockeru pomocí Docker pro Windows nebo Mac. Definují prostředí operačního systému kódu s použitím souboru Dockerfile, který určuje základní operační systém pro spuštění a také kroky sestavení pro vytváření svůj kód do image Dockeru. Vývojáři definovat, jak bude jednu nebo víc imagí spolupracovat pomocí výše uvedenému *docker-compose.yml* soubor manifestu nasazení. Po dokončení jejich místního vývojového, se vložit kód jejich aplikace a konfigurační soubory Docker do úložiště kódu podle vlastní volby (to znamená, že úložiště Git).

Pilíř DevOps definuje kanálů sestavení – kontinuální integrace (CI), pomocí soubor Dockerfile v úložišti kódu. Systém CI vyžádá imagí kontejnerů základní z vybraných registru Dockeru a sestaví vlastní Image Dockeru pro aplikaci. Image se pak ověří a nahrány do registru Dockeru, používá se pro nasazení do různých prostředí.

V pilíř na pravé straně operace, které týmům Spravovat nasazení aplikace a infrastrukturu v produkčním prostředí při monitorování prostředí a aplikací můžete poskytnout zpětnou vazbu a přehledů vývojovému týmu o tom, jak může být aplikace vylepšení. Container apps jsou obvykle běží v produkčním prostředí pomocí orchestrátorů kontejnerů.

Jsou dva týmy spolupracovat prostřednictvím základní platformy (kontejnery Dockeru), která poskytuje oddělení oblastí zájmu jako kontrakt, současně výrazně vylepšuje spolupráci dva týmy v životním cyklu aplikace. Vývojáři vlastní obsah kontejneru, jeho provozní prostředí a vzájemné závislosti kontejneru, že provozní týmy trvat sestavené Image spolu s manifest a provádí s nimi v jejich systému Orchestrace.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Úvod do obecných začátku do konce Docker aplikace životního cyklu pracovního postupu

Obrázek 2-2 představuje podrobnější pracovního postupu pro Docker životního cyklu aplikace, zaměřuje se na konkrétní aktivity DevOps a prostředky v této instanci.

![](./media/image2.png)

Obrázek 2 – 2: Pracovní postup vysoké úrovně pro životní cyklus kontejnerizované aplikace Dockeru

Všechno začíná pro vývojáře, který zahajuje psaní kódu v pracovním postupu vnitřní smyčky. Fázi vnitřní smyčky je tady vývojářům definovat vše, co se stane před doručením (push) kód do úložiště kódu (například systém správy zdrojového kódu jako je Git). Po nebude potvrzena změna, aktivuje úložiště kontinuální integrace (CI) a zbytkem pracovního postupu.

Vnitřní smyčky v podstatě se skládá z obvyklé kroky, například "kód" "spuštění," "test" a "ladění" a navíc další kroky přímo před spuštěním aplikace místně. To je, když vývojář spustí a testuje aplikace jako kontejner Dockeru. Vnitřní smyčky pracovní postup bude vysvětlené v následujících částech.

Přijetí kroku zpět podívat se na pracovním postupu end end, pracovních postupů DevOps je větší než technologie nebo sadu nástrojů: je to způsob myšlení, který vyžaduje kulturní vývoj. Je lidi, procesy a vhodné nástroje, aby životního cyklu aplikací rychlejší a předvídatelnější. Podnikům, které obvykle přijmout kontejnerizovaných pracovního postupu změnit strukturu svých organizací k reprezentaci lidi a procesy, které odpovídají kontejnerizovaných pracovního postupu.

Cvičení DevOps může pomoci týmům rychlejší reakce společně na konkurenční zpožďuje nahrazením náchylné ruční procesy pomocí automatizace, což vede k zlepšení sledovatelnosti a opakovatelné pracovní postupy. Organizace také můžete efektivněji spravovat prostředí a realizovat úsporách nákladů díky službě kombinace místních a cloudových prostředků a také úzce integrovaných nástrojů.

Při implementaci pracovních postupů DevOps pro aplikace Dockeru, uvidíte, že technologie Dockeru jsou k dispozici v téměř každé fázi pracovního postupu, v rozevíracím seznamu vaše vývojové při práci v vnitřní smyčky (spuštění kódu, ladění), na fázi položky konfigurace sestavení testu a, samozřejmě na produkční a přípravné prostředí a nasazení kontejnerů do těchto prostředích.

Zlepšování kvality postupů pomáhá identifikovat chyb v rané fázi vývojového cyklu, což snižuje náklady na jejich implementace vyžadovala. Zahrnutím prostředí a závislostech v bitové kopii a přijetí filozofie nasazení napříč několika prostředími stejnou bitovou kopii, podporovat disciplína extrahování konfigurace specifických pro prostředí provádění nasazení spolehlivější.

Velké množství dat, které získali prostřednictvím efektivní instrumentace (monitorováním a diagnostikou) nabízí pohled na problémy s výkonem a chování uživatelů na budoucí priority a investice.

DevOps považovat za cestu, ne cíl. To by měla být implementována postupně prostřednictvím odpovídajícím způsobem s vymezeným oborem projektů, ze kterých můžete ukazují úspěšné, přečtěte si a vyvíjí.

## <a name="benefits-of-devops-for-containerized-applications"></a>Výhody DevOps pro kontejnerizované aplikace

Tady jsou některé z vašich nejdůležitějších výhody poskytované modulem solid pracovních postupů DevOps:

-   Lepší kvalitě software doručovat rychleji a s lepší dodržování předpisů

-   Dříve a ekonomicky jednotka neustálé vylepšování a přizpůsobení

-   Zvýšení transparentnosti a umožnění spolupráce mezi účastníky účastnící se doručování a provozování softwaru

-   Mít náklady pod kontrolou a efektivněji využívat zřízené prostředky při současné minimalizaci rizika zabezpečení

-   S mnoha stávající investice DevOps, včetně investice do opensourcové technologie Plug and play

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](../Microsoft-platform-tools-containerized-apps/index.md)