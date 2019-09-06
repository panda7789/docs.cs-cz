---
title: Pracovní postup DevOps aplikací Dockeru pomocí nástrojů Microsoft
description: Kontejnerový životní cyklus aplikace Docker s platformou a nástroji Microsoftu pro DevOps pomocí nástrojů Microsoftu
ms.date: 02/15/2019
ms.openlocfilehash: 6b138301a7e6794ce0a7b15957684b3b73e9f89f
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295740"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Pracovní postup DevOps aplikací Dockeru pomocí nástrojů Microsoft

*Microsoft Visual Studio, Azure DevOps Services, Team Foundation Server a Azure Monitor poskytují ucelený ekosystém pro vývoj a IT operace, které týmu poskytují nástroje pro správu projektů a rychlé sestavování, testování a nasazování kontejnerů. vyrovnání.*

Pomocí sady Visual Studio a Azure DevOps Services v cloudu spolu s Team Foundation Server místních vývojových týmů může vyvíjet aplikace pro vytváření, testování a uvolňování kontejnerů, které cílí na Windows nebo Linux.

Nástroje společnosti Microsoft mohou tento kanál automatizovat pro konkrétní implementace kontejnerových aplikací – Docker, .NET Core nebo libovolná kombinace s jinými platformami – od globálních sestavení a průběžné integrace (CI) a testů s Azure DevOps Services nebo týmem. Foundation Server, pro průběžné nasazování (CD) do prostředí Docker (vývoj, příprava, produkce) a pro přenos analytických informací o službách do vývojového týmu prostřednictvím Azure Monitor. Každé potvrzení kódu může iniciovat sestavení (CI) a automaticky nasazovat služby na konkrétní kontejnerová prostředí (CD).

Vývojáři a testeri můžou snadno a rychle zřídit vývojové a testovací prostředí v produkčním prostředí založeném na Docker pomocí šablon v Microsoft Azure.

Složitost vývoje kontejnerů aplikací se v závislosti na složitosti podniku a potřebě škálovatelnosti neustále zvětšuje. Dobrým příkladem této složitosti jsou aplikace založené na architektuře mikroslužeb. V takovém prostředí musí projekt automatizovat celý životní cyklus – nejen sestavení a nasazení, ale také musí spravovat verze společně s kolekcí telemetrie. Azure DevOps Services a Azure nabízejí následující možnosti:

- Správa zdrojového kódu Azure DevOps Services/Team Foundation Server (na základě Gitu nebo Správa verzí Team Foundation), podporuje se agilní plánování (agilní, Scrum a CMMI), CI, Release Management a další nástroje pro agilní týmy.

- Azure DevOps Services a Team Foundation Server zahrnují výkonný a rostoucí ekosystém prvních a dalších rozšíření, se kterými můžete snadno vytvořit kanál pro správu CI, sestavování, testování, doručování a vydávání verzí pro mikroslužby.

- Spustit automatizované testy jako součást kanálu sestavení v Azure DevOps Services.

- Azure DevOps Services může zvýšit životní cyklus DevOps pomocí doručování do několika prostředí, nejen pro produkční prostředí, ale také pro testování, včetně experimentů/B, zkušebních [verzí](https://martinfowler.com/bliki/CanaryRelease.html)a tak dále.

- Organizace můžou snadno zřizovat kontejnery Docker z privátních imagí uložených v Azure Container Registry spolu se všemi závislostmi na komponentách Azure (data, PaaS atd.) pomocí Azure Resource Manager šablon s nástroji, které už jsou pohodlné.

>[!div class="step-by-step"]
>[Předchozí](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)Další
>[](docker-application-outer-loop-devops-workflow.md)
