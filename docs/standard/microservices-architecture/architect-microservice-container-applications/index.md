---
title: Aplikace založené na aplikační architektura založená na kontejnerech a Mikroslužbách
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Aplikace založené na aplikační architektura založená na kontejnerech a Mikroslužbách
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: f7933cc25a5fde13113d0c9c278e9bd1730d4f9d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780710"
---
# <a name="architecting-container--and-microservice-based-applications"></a>Navrhování aplikací založené na kontejnerech a Mikroslužbách

*Mikroslužby nabízí skvělé výhody, ale také přinášejí velké výzvy nové. Vzory architektury Mikroslužeb jsou základní pilíře při vytváření aplikací založených na mikroslužbách.*

Dříve v tomto průvodci jste zjistili, základnímu konceptu kontejnery a Docker. To bylo minimum informací, které potřebujete, abyste mohli začít pracovat s kontejnery. I když i v případě, že kontejnery jsou předpokladů a skvěle hodí pro mikroslužby, nejsou povinné pro architekturu mikroslužeb a mnoho konceptů architektury v této části architektury můžete uplatnit bez kontejnery, příliš. Tyto pokyny ale se zaměřuje na průnik obou z důvodu již zavedení důležitost kontejnery.

Podnikové aplikace může být složité a často se skládají z několika služeb namísto jedné aplikace založené na službách. Pro případy musíte pochopit další architektonických přístupech, jako jsou mikroslužby a určité vzory návrhu Domain-Driven (DDD) a koncepty Orchestrace kontejnerů. Všimněte si, že tato kapitola popisuje na kontejnery, ale žádné kontejnerizované aplikace, a ne jenom mikroslužeb.

## <a name="container-design-principles"></a>Zásady návrhu kontejneru

V modelu container instance image kontejneru představuje jeden proces. Definuje image kontejneru jako hranice procesu, můžete vytvořit primitivních elementů, které je možné škálovat procesu nebo ho dávce.

Při návrhu image kontejneru, zobrazí se [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/) definice v souboru Dockerfile. Definuje proces, jehož doba života řídí životnost kontejneru. Po dokončení procesu kontejneru životní cyklus se ukončí. Kontejnery může představovat dlouho běžící procesy, jako jsou webové servery, ale můžete také představují krátkodobou procesy, jako jsou dávkové úlohy, které dříve může u je implementovaná jako Azure [WebJobs](https://docs.microsoft.com/azure/app-service-web/websites-webjobs-resources).

Pokud proces selže, konce kontejneru a orchestrátor převezme. Pokud byl orchestrátoru konfiguraci, která uchovává spuštěných 5 instancí a jeden server selže, vytvoří orchestrátoru jiná instance kontejneru nahradit procesu, který selhal. V rámci úlohy služby batch je proces spuštěn s parametry. Po dokončení procesu je práce dokončena. Tento návod na zvolené orchestrátory dolů cvičení později.

Může pro vás scénář, kde má více procesů spuštěných ve jedním kontejnerem. Pro tento scénář protože může existovat pouze jeden vstupní bod na kontejner, může spustit skript v rámci kontejneru, který spouští tolik programy podle potřeby. Například můžete použít [Supervisor](http://supervisord.org/) nebo něco podobného postará o spuštění více procesů v rámci jednoho kontejneru. Ale i v případě, že můžete najít architektury, které obsahují více procesů na kontejner, tento přístup není zcela běžný.


>[!div class="step-by-step"]
[Předchozí](../net-core-net-framework-containers/official-net-docker-images.md)
[další](containerize-monolithic-applications.md)
