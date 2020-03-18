---
title: Běžné zásady návrhu kontejneru
description: Naučte se základní princip dobrého návrhu kontejneru, je to, že kontejner by měl hostit pouze jeden proces.
ms.date: 02/15/2019
ms.openlocfilehash: 69f3ff6c9303f0c4082695d861a8c90031295b6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295329"
---
# <a name="common-container-design-principles"></a>Běžné zásady návrhu kontejneru

Před dostat se do procesu vývoje existuje několik základních konceptů stojí za zmínku, pokud jde o to, jak používat kontejnery.

## <a name="container-equals-a-process"></a>Kontejner se rovná procesu

V modelu kontejneru kontejner představuje jeden proces. Definováním kontejneru jako hranice procesu začnete vytvářet primitiva používaná k škálování nebo dávkovému vypnutí procesů. Když spustíte kontejner Dockeru, zobrazí se definice [ENTRYPOINT.](https://docs.docker.com/engine/reference/builder/#/entrypoint) To definuje proces a životnost kontejneru. Po dokončení procesu končí životní cyklus kontejneru. Existují dlouhotrvající procesy, jako jsou webové servery, a krátkodobé procesy, jako jsou dávkové úlohy, které mohly být implementovány jako Microsoft Azure [WebJobs](https://azure.microsoft.com/documentation/articles/websites-webjobs-resources/). Pokud proces selže, kontejner končí a orchestrátor převezme. Pokud byl orchestrator instruován, aby udržel spuštěno pět instancí a jedna selhala, orchestrátor vytvoří jiný kontejner, který nahradí neúspěšný proces. V dávkové úloze je proces zahájen s parametry. Po dokončení procesu je práce dokončena.

Můžete najít scénář, ve kterém chcete více procesů spuštěných v jednom kontejneru. V každém dokumentu architektury, tam je nikdy "nikdy", ani tam je vždy "vždy". Pro scénáře, které vyžadují více procesů, běžný vzor je použít [supervisor](http://supervisord.org/).

>[!div class="step-by-step"]
>[Předchozí](design-docker-applications.md)
>[další](monolithic-applications.md)
