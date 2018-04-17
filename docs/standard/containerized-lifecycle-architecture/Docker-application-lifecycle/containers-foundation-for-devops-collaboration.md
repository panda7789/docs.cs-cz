---
title: Kontejnery jako základ pro spolupráci DevOps
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f7d0f9b1d72f353b2c22f846f723c82f769f6a4e
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>Kontejnery jako základ pro spolupráci DevOps

Velmi povahu kontejnery a Docker technologie vývojáři mohou sdílet jejich softwaru a závislosti snadno s IT oddělení a provozní prostředí při odstranění typické excuse "ho pracuje na můj počítač". Kontejnery řešení konfliktů aplikací mezi různých prostředích. Nepřímo kontejnery a Docker vývojáře a IT oddělení blíže společně nabídnou, snadněji pro je efektivní spolupracovat. Přijetí kontejneru pracovního postupu poskytuje mnoho zákazníků kontinuita DevOps jste žádá o provedeném dříve museli implementovat prostřednictvím složitější konfigurace pro verzi a sestavení kanály. Kontejnery zjednodušit sestavení a testů nebo zavést kanály v DevOps.

![](./media/image1.png)

Obrázek 2 – 1: hlavní úlohy na "osoby" v životním cyklu aplikací kontejnerizované Docker

Pomocí Docker kontejnery, vývojáři vlastní co je v rámci kontejneru (aplikace a služby a závislosti rozhraní a součástí) a kontejnery a služby chování společně jako aplikace sestává z kolekce služeb. Vzájemné závislosti několika kontejnerů, které jsou definovány v soubor docker-compose.yml nebo co může být volána *– manifest nasazení*. Mezitím se IT oddělení (Odborníci v oblasti IT a správy) můžou zaměřit na správu provozní prostředí; Infrastruktura; škálovatelnost; monitorování; a nakonec, zajistíte, že aplikace jsou správně doručení pro koncové uživatele, aniž by museli znát obsah různé kontejnery. Proto název kontejner, vrací analogie s kontejnery reálného přesouvání. Proto vlastníci obsahu kontejner nemusí vztahovat na samotných s jak se má odeslat kontejneru a přenosů přenosy společnosti kontejner z původního bodu do cíle bez vědomí nebo caring o obsahu. Vývojáři podobným způsobem můžete vytvořit a vlastní obsah v rámci kontejner Docker bez nutnosti sami se týkají s mechanismy "přenos".

V pilíře na levé straně obrázek 2-1 vývojáři zápisu a místní spuštění kódu v Docker kontejnerů pomocí Docker pro systém Windows nebo Mac. Definuje provozní prostředí pro kód pomocí soubor Docker, která určuje základní operační systém spustit i kroky sestavení pro vytváření svůj kód do bitové kopie Docker. Vývojáři definovat, jak bude jeden nebo více bitových kopií spolupracovat pomocí výše uvedenému *docker-compose.yml* souboru – manifest nasazení. Po dokončení své místní vývoj, jejich nabízená svůj kód aplikace a konfigurační soubory Docker úložiště kódu libovolný (to znamená, že úložiště Git).

Pilíře DevOps definuje kanálů sestavení – souvislý integrace (CI), pomocí soubor Docker součástí úložiště kódu. CI systém vrátí kontejner základní Image z vybraných Docker registru a vytvoří vlastní imagí Dockeru pro aplikaci. Bitové kopie jsou poté ověřit a instaluje do registru Docker použít pro nasazení do několika prostředí.

V pilíře na pravé straně operace, které týmy Spravovat nasazení aplikace a infrastrukturu v produkčním prostředí při monitorování prostředí a aplikace tak, aby mohli poskytnout zpětnou vazbu a statistickými vývojový tým o tom, jak může být aplikace Vylepšená. Kontejner aplikace jsou obvykle běžet v produkčním prostředí pomocí orchestrators kontejneru.

Prostřednictvím základní platformu (Docker kontejnerů), která poskytuje oddělené oblasti zájmu jako kontraktu, při výraznému zlepšení spolupráce dvou týmy v životním cyklu aplikace jsou spolupráce dvou týmy. Vývojáři vlastníkem obsahu kontejneru, jeho provozní prostředí a vzájemné závislosti kontejneru, zatímco týmy operace trvat vytvořené bitové kopie společně s manifest a spustí je v systému jejich orchestration.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Úvod do obecných začátku do konce Docker aplikace životní cyklus pracovního postupu

Obrázek 2-2 uvede podrobnější pracovního postupu pro Docker životního cyklu aplikace, zaměřené na konkrétní aktivity DevOps a prostředky v této instanci.

![](./media/image2.png)

Obrázek 2 – 2: základní pracovní postup pro Docker kontejnerizované životní cyklus

Všechno, co začíná vývojář, který zahajuje psaní kódu v pracovním postupu vnitřní smyčky. Fáze vnitřní smyčky je, kde vývojáři definovat vše, co se stane před odesláním kód do úložiště kódu (například systému správy zdrojů například Git). Po potvrzení úložiště aktivuje nepřetržité integrace (CI) a zbytek z pracovního postupu.

Vnitřní smyčky v podstatě se skládá z obvyklé kroky jako "kód," "spustit," "test" a "ladění", plus další kroky přímo před spuštěním aplikace místně. To je, když vývojáři spustí a testy aplikace jako kontejner Docker. Vnitřní smyčky pracovní postup bude vysvětlené v následujících částech.

Přijetí krok zpět se podívat na pracovním postupu end end, DevOps pracovního postupu je větší než technologie nebo sada nástrojů: je přistupovat, která vyžaduje kulturního vývoj. Je osoby, procesy a vhodných nástrojů, aby životního cyklu aplikace rychlejší a předvídatelnější. Podnikům, které obvykle přijmout kontejnerizované pracovního postupu změny struktury jejich organizace k reprezentaci osoby a procesy, které odpovídají kontejnerizované pracovního postupu.

Cvičení DevOps může pomoci týmy reagovat rychlejší společně na konkurenční tlak nahrazením náchylné manuálních procesů automatizace, což vede k zlepšení sledovatelnosti a opakovatelných pracovních postupů. Organizace také můžete efektivněji spravovat prostředí a Uvědomte si, úsporu nákladů s kombinací místních a cloudových prostředků a také úzce integrované nástrojů.

Při implementaci DevOps pracovního postupu pro Docker aplikace, se zobrazí, že technologie pro Docker se nacházejí v téměř každé fáze pracovního postupu, vaše vývoj poli při práci s vnitřní smyčky (code, spuštění, ladění), do fáze sestavení. testovací CI a, kurzu, na produkční a pracovní prostředí a nasazení kontejnerů do těchto prostředí.

Zlepšování kvality postupů pomáhá identifikovat defekty již v rané fázi v cyklu vývoje, což snižuje náklady na jejich oprava. Včetně prostředí a závislosti v bitové kopii a přijetí filosofie stejnou bitovou kopii nasazení ve více prostředích, povýšíte extrahování konfigurace specifické pro prostředí provádění nasazení spolehlivější pravidly.

Bohaté dat získaných prostřednictvím efektivní instrumentace (monitorování a Diagnostika) poskytuje náhled do problémy s výkonem a chování uživatele na požadované budoucí priority a investice.

DevOps považovat za cesty, ne do cílového umístění. Ho by měly být prováděny postupně správně vymezená projekty, ze kterých můžete předvedení úspěch, zjistěte a momentální.

## <a name="benefits-of-devops-for-containerized-applications"></a>Výhody DevOps pro kontejnerové aplikace

Zde jsou některé z vašich nejdůležitějších výhod poskytovaných plnou DevOps pracovního postupu:

-   Poskytovat lepší kvality softwaru rychleji a s lepší dodržování předpisů

-   Jednotka neustálé zlepšování a úpravy dříve a více ekonomického

-   Zvýšit průhlednost a spolupráce mezi zúčastněným stranám zahrnutých v doručení a provozování softwaru

-   Řízení nákladů a efektivněji využívat zřízené prostředky a současně minimalizujete její rizika zabezpečení

-   Plug and play i s mnoha stávající investice DevOps, včetně investice s otevřeným zdrojem

>[!div class="step-by-step"]
[Předchozí] (index.md) [Další] (.. /Microsoft-Platform-Tools-containerized-Apps/index.MD)
