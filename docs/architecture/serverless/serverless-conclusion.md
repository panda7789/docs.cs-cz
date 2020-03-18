---
title: Klíčové stánek s jídlem - Aplikace bez serveru
description: Serverless poskytuje mnoho výhod a má své vlastní problémy. Shrnutí klíčových stánek s jídlem z této příručky.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: ae9fc47bf07a7e28688942b856b4743ae7aadc36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676688"
---
# <a name="conclusion"></a>Závěr

Následující klíčové stánek s jídlem jsou nejdůležitější závěry z této příručky.

**Výhody použití bez serveru.** Řešení bez serveru poskytují důležitou výhodu úspor nákladů, protože bez serveru je implementována v modelu pay-per-use. Bez serveru umožňuje nezávisle škálovat, testovat a nasazovat jednotlivé součásti vaší aplikace. Bez serveru je jedinečně hodí k implementaci architektury mikroslužeb a plně integruje do kanálu DevOps.

**Kód jako jednotka nasazení.** Serverless abstrahuje hardware, operační systém a runtime mimo aplikaci. Bez serveru umožňuje zaměřit se na obchodní logiku v kódu jako jednotka nasazení.

**Aktivační události a vazby.** Bez serveru usnadňuje integraci s úložištěm, API a dalšími cloudovými prostředky. Funkce Azure poskytuje aktivační události pro spuštění kódu a vazby pro interakci s prostředky.

**Mikroslužeb.** Architektura mikroslužeb se stává upřednostňovaným přístupem pro distribuované a rozsáhlé nebo složité důležité aplikace, které jsou založeny na více nezávislých subsystémech ve formě autonomních služeb. V architektuře založené na mikroslužbách je aplikace vytvořena jako kolekce služeb, které lze vyvíjet, testovat, nastavovat verzemi, nasazovat a škálovat nezávisle. Serverless je architektura vhodná pro vytváření těchto služeb.

**Serverové platformy.** Bez serveru není jen o kódu. Platformy, které podporují architektury bez serveru, zahrnují pracovní postupy bez serveru a orchestraci, služby zasílání zpráv bez serveru a služby událostí bez serveru a databáze bez serveru.

**Serverové výzvy.** Serverless představuje výzvy související s vývojem distribuovaných aplikací, jako jsou fragmentované a nezávislé datové modely, odolnost proti chybám, správa verzí a zjišťování služeb. Bez serveru nemusí být ideální pro dlouhotrvající procesy nebo součásti, které využívají užší párování.

**Bez serveru jako nástroj, ne panel nástrojů.** Bez serveru není výhradní řešení architektury aplikace. Jedná se o nástroj, který lze využít jako součást hybridní aplikace, která může obsahovat tradiční úrovně, monolit back-endy a kontejnery. Bez serveru lze vylepšit stávající řešení a není vše nebo nic přístup k vývoji aplikací.

>[!div class="step-by-step"]
>[Předchozí](serverless-business-scenarios.md)
