---
title: Pracovní postup DevOps aplikací dockeru pomocí nástrojů Microsoftu
description: Kontejnerizované životní cyklus aplikace Dockeru s pracovním postupem platformy Microsoft a nástrojů DevOps s nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: a2d88dda9f3560675fcb6826960c6e76fa7daf92
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219072"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Pracovní postup DevOps aplikací dockeru pomocí nástrojů Microsoftu

Microsoft Visual Studio, Azure DevOps Services, Team Foundation Server a Application Insights poskytuje komplexní ekosystém pro vývoj a IT operace, které dejte týmu nástroje pro řízení projektů a rychle vytvářet, testovat a nasadit kontejnerizované aplikace.

Pomocí sady Visual Studio a služeb Azure DevOps v cloudu, spolu s Team Foundation Server v místním vývojovým týmům produktivní sestavení, testování a vydání kontejnerizovaných aplikací zaměřený na jakoukoli platformu (Windows nebo Linux).

Nástroje sady Microsoft můžete automatizovat kanálu pro konkrétní implementace kontejnerizovaných aplikací – Docker, .NET Core nebo libovolnou kombinaci s jinými platformami – z globální sestavení kontinuální integrace (CI) a testy pomocí služby Azure DevOps nebo týmu Foundation Server, pro průběžné nasazování (CD) do prostředí Docker (vývoje, přípravy, výroby) a k přenosu analytics informace o službách pro vývojový tým pomocí Application Insights. Každé potvrzení kódu můžete zahájit sestavení (CI) a automaticky nasadit službu do konkrétních kontejnerové prostředí (CD).

Vývojáři a testeři mohou snadno a rychle zřídit vývojová a testovací prostředí podobném produkci založené na Dockeru pomocí šablony v Microsoft Azure.

Složitost vývoje kontejnerizovaných aplikací zvyšuje neustále podle potřeb firmy složitost a škálovatelnost. Dobrým příkladem jsou aplikací založených na architekturu mikroslužeb. K úspěšnému v takovém prostředí, musí váš projekt automatizovat celý životní cyklus – nejen sestavení a nasazení, ale také musí spravovat verze spolu s kolekce telemetrie. Azure DevOps služby a Azure nabízejí následující možnosti:

-   Správa zdrojového kódu Azure DevOps Services nebo Team Foundation Server se (na základě Gitu nebo Team Foundation Version Control), agilní plánování (Agile a Scrum, CMMI jsou podporovány), průběžná integrace, release management a další nástroje pro agilní týmy.

-   Azure DevOps Services nebo Team Foundation Server patří výkonné a rostoucí ekosystém rozšíření prvních a třetích stran, se kterými můžete snadno vytvořit položky konfigurace, sestavení, testů, doručování a release management kanálu pro mikroslužby.

-   Spuštění automatizovaných testů v rámci vašeho kanálu sestavení ve službách Azure DevOps.

-   Služby Azure DevOps můžete posílit DevOps životní cyklus doručování do různých prostředí, ne jenom pro produkční prostředí, ale také pro testování, včetně A / B experimentování [testovací verze](https://martinfowler.com/bliki/CanaryRelease.html), a tak dále.

-   Organizace můžou snadno zřídit kontejnery Dockeru z privátních imagí uložená spolu s všechny závislosti v komponentách Azure (Data, PaaS, atd.) ve službě Azure Container Registry pomocí šablon Azure Resource Manageru pomocí nástrojů, se kterými jsou již pohodlné práce.

>[!div class="step-by-step"]
>[Předchozí](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
>[další](docker-application-outer-loop-devops-workflow.md)