---
title: Architekty aplikací založených na kontejnerech a mikroslužbách
description: Navrhování kontejnerů a aplikací založených na mikroslužbách není nijak malé Feat a neměli byste je považovat za lehce. Seznamte se se základními koncepty v této kapitole.
ms.date: 09/20/2018
ms.openlocfilehash: aff30c907f1140b94dbcae330ed7cb633b0a744b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295516"
---
# <a name="architecting-container-and-microservice-based-applications"></a>Architekty aplikací založených na kontejnerech a mikroslužbách

*Mikroslužby nabízejí skvělé výhody, ale také vyvolává velké nové problémy. Modely architektury mikroslužeb jsou základní pilíře při vytváření aplikací založených na mikroslužbách.*

Výše v tomto průvodci jste zjistili základní koncepty o kontejnerech a Docker. To bylo minimální informace, které jste potřebovali k zahájení práce s kontejnery. I když jsou kontejnery zablokované a velmi vhodné pro mikroslužby, nemusejí být pro architekturu mikroslužeb povinné a mnoho konceptů architektury v této architektuře může být taky možné použít bez kontejnerů. Tento návod se ale zaměřuje na průnik obou z důvodu již zavedeného důležitosti kontejnerů.

Podnikové aplikace můžou být složité a často se skládají z několika služeb namísto jedné aplikace založené na službách. V takových případech potřebujete pochopit další přístupy k architektuře, jako jsou mikroslužby a určité vzory návrhu založené na doméně (DDD) a koncepty orchestrace kontejnerů. Všimněte si, že tato kapitola popisuje nejen mikroslužby na kontejnerech, ale také všechny aplikace v kontejneru.

## <a name="container-design-principles"></a>Principy návrhu kontejneru

V modelu kontejneru představuje instance image kontejneru jeden proces. Definováním image kontejneru jako hranice procesu můžete vytvořit primitivní prvky, které lze použít ke škálování procesu nebo k vytvoření dávky.

Při návrhu image kontejneru se na souboru Dockerfile zobrazí definice [ENTRYPOINT](https://docs.docker.com/engine/reference/builder/#entrypoint) . Tím se definuje proces, jehož životnost řídí dobu života kontejneru. Po dokončení procesu skončí životní cyklus kontejneru. Kontejnery mohou představovat dlouhotrvající procesy, jako jsou webové servery, ale mohou také představovat krátkodobé procesy, jako jsou dávkové úlohy, které dříve mohly být implementovány jako Azure [WebJobs](https://github.com/Azure/azure-webjobs-sdk/wiki).

Pokud se proces nezdařil, kontejner skončí a nástroj Orchestrator převezme. Pokud byl produkt Orchestrator nakonfigurován tak, aby zachoval pět instancí a jeden selže, nástroj Orchestrator vytvoří jinou instanci kontejneru, aby nahradila neúspěšný proces. V úloze Batch se proces spouští s parametry. Po dokončení procesu se práce dokončí. Tato příručka se podrobněji rozchází na orchestrací, a to později.

Můžete najít scénář, ve kterém chcete, aby více procesů běželo v jednom kontejneru. V tomto scénáři, protože může existovat pouze jeden vstupní bod pro každý kontejner, můžete spustit skript v rámci kontejneru, který v případě potřeby spustí tolik programů. Můžete například použít [správce](http://supervisord.org/) nebo podobný nástroj k tomu, abyste se mohli postarat o spuštění více procesů uvnitř jednoho kontejneru. I když ale můžete najít architektury, které obsahují více procesů na kontejner, tento přístup není velmi běžný.

>[!div class="step-by-step"]
>[Předchozí](../net-core-net-framework-containers/official-net-docker-images.md)Další
>[](containerize-monolithic-applications.md)
