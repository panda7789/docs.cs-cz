---
title: Pracovní postup DevOps aplikací Dockeru pomocí nástrojů Microsoft
description: Kontejnerizovaný životní cyklus aplikací Dockeru s pracovním postupem Microsoft Platform and Tools DevOps s nástroji Microsoftu
ms.date: 02/15/2019
ms.openlocfilehash: 6b138301a7e6794ce0a7b15957684b3b73e9f89f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "70295740"
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Pracovní postup DevOps aplikací Dockeru pomocí nástrojů Microsoft

*Microsoft Visual Studio, Azure DevOps Services, Team Foundation Server a Azure Monitor poskytují komplexní ekosystém pro vývoj a IT operace, které vašemu týmu poskytují nástroje pro správu projektů a rychlé sestavení, testování a nasazování kontejnerových Aplikace.*

S Visual Studio a Azure DevOps Services v cloudu, spolu s Team Foundation Server místně, vývojové týmy můžete produktivně vytvářet, testovat a vydávat kontejnerizované aplikace, které cílí na Windows nebo Linux.

Nástroje Microsoftu můžou automatizovat kanál pro konkrétní implementace kontejnerizovaných aplikací – Docker, .NET Core nebo jakoukoli kombinaci s jinými platformami – z globálních sestavení a průběžné integrace (CI) a testů se službami Azure DevOps nebo Team Foundation Server, na průběžné nasazení (CD) do prostředí Dockeru (vývoj, staging, produkční) a přenášet analytické informace o službách vývojovému týmu prostřednictvím Azure Monitoru. Každé potvrzení kódu můžete zahájit sestavení (CI) a automaticky nasadit služby do konkrétních kontejnerizovaných prostředí (CD).

Vývojáři a testeři můžou snadno a rychle zřídit vývojová a testovací prostředí založená na Dockeru pomocí šablon v Microsoft Azure.

Složitost kontejnerizovaného vývoje aplikací se neustále zvyšuje v závislosti na složitosti podniku a potřebách škálovatelnosti. Dobrým příkladem této složitosti jsou aplikace založené na architekturách mikroslužeb. Chcete-li uspět v takovém prostředí, váš projekt musí automatizovat celý životní cyklus – nejen sestavení a nasazení, ale také musí spravovat verze spolu s kolekcí telemetrie. Azure DevOps Services a Azure nabízejí následující funkce:

- Azure DevOps Services/Team Foundation Server správa zdrojového kódu (na základě Git nebo Team Foundation Version Management), agilní plánování (agilní, Scrum a CMMI jsou podporované), CI, správa verzí a další nástroje pro agilní týmy.

- Služby Azure DevOps services a Team Foundation Server zahrnují výkonný a rostoucí ekosystém rozšíření prvnía a třetího výrobce, pomocí kterých můžete snadno vytvořit kanál pro správu ci, sestavení, testování, doručování a správy verzí pro mikroslužby.

- Spusťte automatizované testy jako součást kanálu sestavení ve službách Azure DevOps Services.

- Služby Azure DevOps services můžou zpřísnit životní cyklus DevOps s doručováním do více prostředí, nejen pro produkční prostředí, ale také pro testování, včetně experimentování A/B, [kanárských verzí](https://martinfowler.com/bliki/CanaryRelease.html)a tak dále.

- Organizace snadno můžou zřazovat kontejnery Dockeru z privátních ibiu uložených v registru kontejnerů Azure spolu s jakoukoli závislostí na součástech Azure (data, PaaS atd.) pomocí šablon Azure Resource Manager s nástroji, které už jsou pohodlné.

>[!div class="step-by-step"]
>[Předchozí](../design-develop-containerized-apps/build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
>[další](docker-application-outer-loop-devops-workflow.md)
