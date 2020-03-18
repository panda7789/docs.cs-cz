---
title: Kontejnery jako základ pro spolupráci DevOps
description: Seznamte se s klíčovou rolí kontejnerů pro zjednodušení devops.
ms.date: 02/15/2019
ms.openlocfilehash: 8258f4331212d92376d64fef318adcdff492f61f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73094503"
---
# <a name="containers-as-the-foundation-for-devops-collaboration"></a>Kontejnery jako základ pro spolupráci DevOps

Ze samotné podstaty kontejnerů a technologie Dockeru mohou vývojáři snadno sdílet svůj software a závislosti s it operacemi a produkčními prostředími a zároveň eliminovat typickou výmluvu "funguje to na mém počítači". Kontejnery řeší konflikty aplikací mezi různými prostředími. Kontejnery a Docker nepřímo sbližují vývojáře a operace IT, což jim usnadňuje efektivní spolupráci. Přijetí pracovního postupu kontejneru poskytuje mnoha zákazníkům kontinuitu DevOps, kterou hledali, ale dříve museli implementovat prostřednictvím složitější konfigurace pro vytváření a vytváření kanálů. Kontejnery zjednodušují kanály sestavení/testování/nasazení v DevOps.

![Diagram znázorňující vlastnictví životního cyklu aplikace Dockeru.](./media/containers-foundation-for-devops-collaboration/persona-workloads-docker-container-lifecycle.png)

**Obrázek 2-1.** Hlavní úlohy na "personas" v životním cyklu pro kontejnerizované aplikace Dockeru

S kontejnery Dockeru vývojáři vlastní to, co je v kontejneru (aplikace a služby a závislosti na architektury a součásti) a jak kontejnery a služby chovají společně jako aplikace složené z kolekce služeb. Vzájemné závislosti více kontejnerů jsou definovány v souboru `docker-compose.yml` nebo co by se dalo nazvat manifest *nasazení*. Mezitím se it provozní týmy (IT profesionálové a management) mohou zaměřit na řízení produkčních prostředí; infrastruktury; škálovatelnost; monitorování; a v konečném důsledku zajistit, aby aplikace řádně doručovaly pro koncové uživatele, aniž by bylo třeba znát obsah různých nádob. Proto název "kontejner", připomínající analogii k real-svět přepravních kontejnerů. Majitelé obsahu kontejneru se tedy nemusí zabývat tím, jak bude kontejner odeslán, a přepravní společnost přepravuje kontejner z místa původu do místa určení, aniž by věděla nebo se starala o obsah. Podobným způsobem mohou vývojáři vytvářet a vlastnit obsah v kontejneru Dockeru bez nutnosti zabývat se mechanismy "přenosu".

V pilíři na levé straně obrázku 2-1 vývojáři psát a spouštět kód místně v kontejnerech Dockerpomocí pomocí Dockeru pro Windows nebo Mac. Definují operační prostředí pro kód pomocí Dockerfile, který určuje základní operační systém ke spuštění, stejně jako kroky sestavení pro vytváření jejich kódu do image Dockeru. Vývojáři definují, jak bude jedna nebo více `docker-compose.yml` bitových kopií vzájemně fungovat pomocí výše uvedeného manifestu nasazení souborů. Když dokončí svůj místní vývoj, odsouvají svůj kód aplikace a konfigurační soubory Dockeru do úložiště kódu podle svého výběru (to znamená úložiště Git).

DevOps pilíř definuje sestavení průběžné integrace (CI) kanály pomocí Dockerfile k dispozici v úložišti kódu. Systém CI vytáhne image základního kontejneru z vybraného registru Dockeru a vytvoří vlastní image Dockeru pro aplikaci. Bitové kopie jsou pak ověřeny a zatlačeny do registru Dockeru používaného pro nasazení do více prostředí.

V pilíři vpravo operační týmy spravují nasazené aplikace a infrastrukturu v produkčním prostředí a současně monitorují prostředí a aplikace, aby mohly poskytnout zpětnou vazbu a přehled vývojovému týmu o tom, jak by aplikace mohla být Zlepšení. Kontejnerové aplikace se obvykle spouštějí v produkčním prostředí pomocí orchestrátorů kontejnerů.

Tyto dva týmy spolupracují prostřednictvím základní platformy (kontejnery Dockeru), která poskytuje oddělení obav jako smlouvy a zároveň výrazně zlepšuje spolupráci obou týmů v životním cyklu aplikace. Vývojáři vlastní obsah kontejneru, jeho provozní prostředí a kontejner uzanejší závislosti, zatímco operační týmy přebírají vytvořené bitové kopie spolu s manifestem a spouští je v jejich systému orchestrace.

## <a name="challenges-in-application-life-cycle-when-using-docker"></a>Výzvy v životním cyklu aplikace při používání Dockeru.

Existuje mnoho důvodů, které zvýší počet kontejnerizovaných aplikací v nadcházejících letech a jedním z těchto důvodů je vytváření aplikací založených na mikroslužbách.

Během posledních 15 let bylo používání webových služeb základem tisíců aplikací a pravděpodobně po několika letech najdeme stejnou situaci s aplikacemi založenými na mikroslužbách, které běží na kontejnerech Dockeru.

Je také třeba zmínit, že můžete také použít kontejnery Dockeru pro monolitické aplikace a stále získáte většinu výhod Dockeru. Kontejnery nejsou zaměřeny pouze mikroslužeb.

Použití kontejnerizace Dockeru a mikroslužeb způsobuje nové problémy v procesu vývoje vašich organizací, a proto potřebujete solidní strategii pro údržbu mnoha kontejnerů a mikroslužeb spuštěných v produkčních systémech. Nakonec podnikové aplikace budou mít stovky nebo tisíce kontejnerů/instancí spuštěných v produkčním prostředí.

Tyto výzvy vytvářejí nové požadavky při používání nástrojů DevOps, takže budete muset definovat nové procesy ve svých aktivitách DevOps a najít odpovědi na tento typ otázek:

- Jaké nástroje mohu použít pro vývoj, pro CI/CD, správu a provoz?

- Jak může moje společnost spravovat chyby v kontejnerech při spuštění v produkčním prostředí?

- Jak můžeme změnit kusy našeho softwaru ve výrobě s minimálními prostoji?

- Jak můžeme škálovat a jak můžeme sledovat náš výrobní systém?

- Jak můžeme zahrnout testování a nasazení kontejnerů v našem kanálu vydání?

- Jak můžeme používat open source nástroje/platformy pro kontejnery v Microsoft Azure?

Pokud můžete odpovědět na všechny tyto otázky, budete lépe připraveni přesunout aplikace (existující nebo nové aplikace) do kontejnerů Dockeru.

## <a name="introduction-to-a-generic-end-to-end-docker-application-life-cycle-workflow"></a>Úvod do obecného komplexního pracovního cyklu životního cyklu aplikace Dockeru

Obrázek 2-2 představuje podrobnější pracovní postup pro životní cyklus aplikací Dockeru se zaměřením v tomto případě na konkrétní aktivity a prostředky DevOps.

![Diagram znázorňující obecný životní cyklus od konce aplikace Dockeru.](./media/containers-foundation-for-devops-collaboration/generic-end-to-enddpcker-app-life-cycle.png)

**Obrázek 2-2.** Pracovní postup na vysoké úrovni pro životní cyklus kontejnerizované aplikace Dockeru

Vše začíná vývojářem, který začne psát kód v pracovním postupu vnitřní smyčky. Fáze vnitřní smyčky je místo, kde vývojáři definují vše, co se stane před odesláním kódu do úložiště kódu (například systém správy zdrojového kódu, jako je Git). Po jeho potvrzené, úložiště aktivuje průběžnou integraci (CI) a zbytek pracovního postupu.

Vnitřní smyčka se v podstatě skládá z typických kroků, jako je "kód", "spustit", "testovat" a "ladění", plus další kroky potřebné přímo před spuštěním aplikace místně. Jedná se o proces vývojáře pro spuštění a testování aplikace jako kontejneru Dockeru. Pracovní postup vnitřní smyčky bude vysvětlen v následujících částech.

Krok zpět a podívejte se na pracovní postup začátku do konce, pracovní postup DevOps je více než technologie nebo sada nástrojů: je to způsob myšlení, který vyžaduje kulturní vývoj. Jsou to lidé, procesy a vhodné nástroje, aby byl váš životní cyklus aplikace rychlejší a předvídatelnější. Podniky, které přijmou kontejnerizovaný pracovní postup, obvykle restrukturalizují své organizace tak, aby reprezentovaly osoby a procesy, které odpovídají kontejnerizovanému pracovnímu postupu.

Cvičení DevOps může pomoci týmům rychleji reagovat společně na konkurenční tlaky nahrazením ručních procesů náchylných k chybám automatizací, což vede ke zlepšení sledovatelnosti a opakovatelných pracovních postupů. Organizace také mohou efektivněji spravovat prostředí a realizovat úspory nákladů díky kombinaci místních a cloudových prostředků a také úzce integrovaným nástrojům.

Při implementaci pracovního postupu DevOps pro aplikace Dockeru uvidíte, že technologie Dockeru jsou k dispozici téměř ve všech fázích pracovního postupu, z vývojového pole při práci ve vnitřní smyčce (kód, spuštění, ladění), fáze sestavení-test-CI a nakonec nasazení těchto kontejnerů do pracovního a produkčního prostředí.

Zlepšení postupů kvality pomáhá identifikovat vady v rané fázi vývojového cyklu, což snižuje náklady na jejich opravu. Zahrnutím prostředí a závislostí do bitové kopie a přijetím filozofie nasazení stejné image ve více prostředích podporujete disciplínu extrahování konfigurací specifických pro prostředí, díky nimž jsou nasazení spolehlivější.

Bohatá data získaná prostřednictvím efektivní instrumentace (monitorování a diagnostika) poskytují přehled o problémech s výkonem a chování uživatelů, které řídí budoucí priority a investice.

DevOps by měly být považovány za cestu, nikoli za cíl. Měl by být implementován postupně prostřednictvím vhodně vymezených projektů, ze kterých můžete prokázat úspěch, učit se a vyvíjet.

## <a name="benefits-of-devops-for-containerized-applications"></a>Výhody devOps pro kontejnerizované aplikace

Zde jsou některé z nejdůležitějších výhod poskytovaných solidní mno žlabem DevOps:

- Doručujte kvalitnější software, rychlejší a lepší dodržování předpisů.

- Poměřte neustálé zlepšování a úpravy dříve a ekonomicky.

- Zvyšte transparentnost a spolupráci mezi zúčastněnými stranami zapojenými do poskytování a provozování softwaru.

- Kontrolujte náklady a efektivněji využijte zřízené prostředky a minimalizujte bezpečnostní rizika.

- Plug and play dobře s mnoha z vašich stávajících investic DevOps, včetně investic do open-source.

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](../Microsoft-platform-tools-containerized-apps/index.md)
