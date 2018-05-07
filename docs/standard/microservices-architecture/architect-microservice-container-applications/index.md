---
title: Aplikace založené na architektury Mikroslužby a kontejneru
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Aplikace založené na architektury Mikroslužby a kontejneru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 91f63343ba2d7458d0d3b03978ac79a3a7e8427a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="architecting-container--and-microservice-based-applications"></a>Architektury aplikace založená na kontejner a Mikroslužbu

*Mikroslužeb nabízí skvělý výhody, ale zároveň vyvolává obrovské další výzvy. Vzory architektury Mikroslužby jsou základní pilíře při vytváření aplikace na základě mikroslužby.*

Dříve v tomto průvodci jste se dozvěděli o kontejnery a Docker základní koncepty. Minimální informace, které potřebujete, aby bylo možné začít pracovat s kontejnery, který byl. I když i v případě, že kontejnery jsou předpokladů a skvělé přizpůsobit pro mikroslužeb, nejsou povinné architektury mikroslužby a mnohé koncepty architektury v této části architektura může být použit bez kontejnery, příliš. V tomto návodu se však zaměřuje na průnik i z důvodu již přináší význam kontejnery.

Podnikové aplikace, které může být složité a často skládat z několika služeb místo jedné aplikace založené na službě. Pro případy musíte pochopit další architektury postupy, jako například mikroslužeb a určité vzory návrhu Domain-Driven (DDD) a koncepty orchestration kontejneru. Všimněte si, že tato kapitola popisuje nejenom mikroslužeb na kontejnery, ale všechny kontejnerizované aplikace, také.

## <a name="container-design-principles"></a>Principy návrhu kontejneru

V kontejneru modelu do kontejneru image instance představuje jeden proces. Definováním bitovou kopii kontejneru jako hranice procesu můžete vytvořit základní prvky, které lze použít škálovat proces nebo ho dávky.

Při návrhu bitovou kopii kontejner se zobrazí [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/) definice v soubor Docker. Definuje proces, jejichž doba platnosti řídí životnost kontejneru. Po dokončení procesu životního cyklu kontejneru se ukončí. Kontejnery může představovat dlouho běžící procesy, jako jsou webové servery, ale můžete také představují krátkodobou procesy, jako dávkové úlohy, které dříve může mít implementována jako Azure [WebJobs](https://docs.microsoft.com/azure/app-service-web/websites-webjobs-resources).

Pokud proces selže, elementy end kontejneru a orchestrator má. Pokud chcete zachovat pět instancí spuštěných byla nakonfigurována orchestrator a jeden server selže, vytvoří orchestrator jiná instance kontejneru nahradit selhal proces. V rámci úlohy batch je proces spuštěn s parametry. Po dokončení procesu, práce je dokončena. V tomto návodu projde dolů na orchestrators, později.

Můžete se setkat scénář, kde se má více procesů spuštěných ve jediný kontejner. Pro tento scénář protože může existovat pouze jedna položka bod na kontejner, může spustit skript v rámci kontejneru, který spustí tolik programy podle potřeby. Například můžete použít [nadřízeného](http://supervisord.org/) nebo podobné nástroj, který se postará o spuštění více procesů uvnitř jediný kontejner. Nicméně i když můžete najít architektury, které mají více procesů na kontejner, tento přístup není velmi běžné.


>[!div class="step-by-step"]
[Předchozí] (../net-core-net-framework-containers/official-net-docker-images.md) [Další] (containerize-monolithic-applications.md)
