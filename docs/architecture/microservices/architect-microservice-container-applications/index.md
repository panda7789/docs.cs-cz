---
title: Navrhování kontejnerů a aplikací založených na mikroslužbách
description: Navrhování kontejneru a aplikace založené na mikroslužbách není malý výkon a neměly by být brány na lehkou váhu. Naučte se základní pojmy v této kapitole.
ms.date: 09/20/2018
ms.openlocfilehash: aff30c907f1140b94dbcae330ed7cb633b0a744b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "70295516"
---
# <a name="architecting-container-and-microservice-based-applications"></a>Navrhování kontejnerů a aplikací založených na mikroslužbách

*Mikroslužby nabízejí velké výhody, ale také vyvolávají obrovské nové výzvy. Vzory architektury mikroslužeb jsou základní pilíře při vytváření aplikace založené na mikroslužbách.*

Dříve v této příručce jste se naučili základní koncepty o kontejnerech a Dockeru. To byly minimální informace, které jste potřebovali, abyste mohli začít s kontejnery. I když i v případě, že kontejnery jsou enablers a vhodné pro mikroslužeb, nejsou povinné pro architekturu mikroslužeb a mnoho architektonických konceptů v této části architektury lze použít bez kontejnerů, příliš. Tyto pokyny se však zaměřuje na průsečík obou kvůli již zavedené důležitosti kontejnerů.

Podnikové aplikace mohou být složité a často se skládají z více služeb namísto jedné aplikace založené na službě. V těchto případech je třeba pochopit další architektonické přístupy, jako jsou například mikroslužeb a některé vzory návrhu řízeného doménou (DDD) plus koncepty orchestrace kontejnerů. Všimněte si, že tato kapitola popisuje nejen mikroslužeb na kontejnery, ale všechny kontejnerizované aplikace, také.

## <a name="container-design-principles"></a>Principy návrhu kontejnerů

V modelu kontejneru představuje instance image kontejneru jeden proces. Definováním image kontejneru jako hranice procesu můžete vytvořit primitiva, která lze použít ke změně měřítka procesu nebo k jeho dávkování.

Při návrhu image kontejneru, uvidíte [entrypoint](https://docs.docker.com/engine/reference/builder/#entrypoint) definice v Dockerfile. To definuje proces, jehož životnost řídí životnost kontejneru. Po dokončení procesu končí životní cyklus kontejneru. Kontejnery mohou představovat dlouhotrvající procesy, jako jsou webové servery, ale mohou také představovat krátkodobé procesy, jako jsou dávkové úlohy, které dříve mohly být implementovány jako Azure [WebJobs](https://github.com/Azure/azure-webjobs-sdk/wiki).

Pokud proces selže, kontejner končí a orchestrátor převezme. Pokud byl orchestrator nakonfigurován tak, aby udržel spuštěno pět instancí a jedna selhala, orchestrátor vytvoří jinou instanci kontejneru, která nahradí neúspěšný proces. V dávkové úloze je proces zahájen s parametry. Po dokončení procesu je práce dokončena. Toto pokyny vrtá dolů na orchestrátory, později.

Můžete najít scénář, kde chcete více procesů spuštěných v jednom kontejneru. Pro tento scénář, protože může existovat pouze jeden vstupní bod na kontejner, můžete spustit skript v rámci kontejneru, který spustí tolik programů podle potřeby. Můžete například použít [supervisor](http://supervisord.org/) nebo podobný nástroj, abyste se postarali o spuštění více procesů uvnitř jednoho kontejneru. Však i když můžete najít architektury, které mají více procesů na kontejner, tento přístup není příliš běžné.

>[!div class="step-by-step"]
>[Předchozí](../net-core-net-framework-containers/official-net-docker-images.md)
>[další](containerize-monolithic-applications.md)
