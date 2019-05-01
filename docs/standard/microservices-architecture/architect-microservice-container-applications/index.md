---
title: Aplikační architektura založená na kontejner a aplikací založených na mikroslužbách
description: Aplikační architektura založená na kontejner a aplikací založených na mikroslužbách se žádné malé feat a by neměl být přijata lehce. Naučte se základní koncepty v této kapitole.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 6b1d5f7f0ab18e4f1d4b5c2200ac0c6f40c701ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62026052"
---
# <a name="architecting-container-and-microservice-based-applications"></a>Aplikační architektura založená na kontejner a aplikací založených na mikroslužbách

*Mikroslužby nabízí skvělé výhody, ale také přinášejí velké výzvy nové. Vzory architektury Mikroslužeb jsou základní pilíře při vytváření aplikací založených na mikroslužbách.*

Dříve v tomto průvodci jste zjistili, základnímu konceptu kontejnery a Docker. To bylo minimum informací, že je potřeba začít pracovat s kontejnery. I když i v případě, že kontejnery jsou předpokladů a skvěle hodí pro mikroslužby, a proto nejsou povinné pro architekturu mikroslužeb a mnoho konceptů architektury v této části architektury můžete uplatnit bez kontejnery, příliš. Tyto pokyny ale se zaměřuje na průnik obou z důvodu již zavedení důležitost kontejnery.

Podnikové aplikace může být složité a často se skládají z několika služeb namísto jedné aplikace založené na službách. Pro případy musíte pochopit další architektonických přístupech, jako jsou mikroslužby a určité vzory návrhu Domain-Driven (DDD) a koncepty Orchestrace kontejnerů. Všimněte si, že tato kapitola popisuje na kontejnery, ale žádné kontejnerizované aplikace, a ne jenom mikroslužeb.

## <a name="container-design-principles"></a>Zásady návrhu kontejneru

V modelu container instance image kontejneru představuje jeden proces. Definuje image kontejneru jako hranice procesu, můžete vytvořit primitivních elementů, které je možné škálovat procesu nebo ho dávce.

Při návrhu image kontejneru, zobrazí se vám [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#entrypoint) definice v souboru Dockerfile. Definuje proces, jehož doba života řídí životnost kontejneru. Po dokončení procesu kontejneru životní cyklus se ukončí. Kontejnery může představovat dlouho běžící procesy, jako jsou webové servery, ale můžete také představují krátkodobou procesy, jako jsou dávkové úlohy, které dříve může u je implementovaná jako Azure [WebJobs](https://github.com/Azure/azure-webjobs-sdk/wiki).

Pokud proces selže, konce kontejneru a orchestrátor převezme. Pokud byl orchestrátoru konfiguraci, která uchovává spuštěných 5 instancí a jeden server selže, vytvoří orchestrátoru jiná instance kontejneru nahradit procesu, který selhal. V rámci úlohy služby batch je proces spuštěn s parametry. Po dokončení procesu je práce dokončena. Tento návod na zvolené orchestrátory dolů cvičení později.

Může pro vás scénář, kde má více procesů spuštěných ve jedním kontejnerem. Pro tento scénář protože může existovat pouze jeden vstupní bod na kontejner, může spustit skript v rámci kontejneru, který spouští tolik programy podle potřeby. Například můžete použít [Supervisor](http://supervisord.org/) nebo něco podobného postará o spuštění více procesů v rámci jednoho kontejneru. Ale i v případě, že můžete najít architektury, které obsahují více procesů na kontejner, tento přístup není zcela běžný.

>[!div class="step-by-step"]
>[Předchozí](../net-core-net-framework-containers/official-net-docker-images.md)
>[další](containerize-monolithic-applications.md)