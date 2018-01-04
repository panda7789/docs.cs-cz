---
title: "Pracovní postup docker aplikací devops s nástroji Microsoft"
description: "Kontejnerizované Docker cyklu aplikací s platformy společnosti Microsoft a Toolsdevops pracovního postupu s nástroji Microsoft"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8539e8c0a6d0c6c9d558b91e062184e7ef135856
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="docker-application-devops-workflow-with-microsoft-tools"></a>Pracovní postup docker aplikací DevOps s nástroji Microsoft

Microsoft Visual Studio, Visual Studio Team Services, Team Foundation Server a Application Insights poskytují komplexní ekosystém pro vývoj a IT oddělení, která umožňují váš tým nástroje pro řízení projektů a rychlé vytvoření, testování a nasazení kontejnerové aplikace.

Pomocí sady Visual Studio a Visual Studio Team Services v cloudu, společně s Team Foundation Server – místní vývojové týmy efektivní sestavení, testování a verze kontejnerizované aplikace zaměřený na libovolnou platformu (Windows nebo Linux).

Nástroje sady Microsoft můžete automatizovat kanálu pro konkrétní implementace kontejnerizované aplikací – Docker, .NET Core nebo libovolnou kombinaci s jinými platformami – globální sestavení a nepřetržité integrace (CI) a testy s Visual Studio Team Services nebo Team Foundation Server, na průběžné nasazení (CD) do prostředí Docker (vývoj, pracovní, produkční) a k přenosu analytics informace o službách pro vývojový tým pomocí Application Insights. Každou potvrzenou změnou kódu můžete zahájit sestavení (CI) a automaticky nasadit službu do konkrétní kontejnerizované prostředí (CD).

Vývojáři a testerům, sada můžete snadno a rychle zřizovat produkčního prostředí vývojová a testovací prostředí podle Docker pomocí šablon ve službě Microsoft Azure.

Složitost vývoj kontejnerizované aplikací zvyšuje vytrvale podle obchodních potřeb složitost a škálovatelnost. Dobrým příkladem jsou aplikace založené na mikroslužeb architektury. Při takovém prostředí úspěšná, musí váš projekt automatizovat celý životní cyklus – nejen sestavení a nasazení, ale také musí spravovat verzích, a také kolekce telemetrie. Visual Studio Team Services a Azure nabízí následující možnosti:

-   Správu zdrojového kódu Visual Studio Team Services nebo Team Foundation Server se (na základě Git nebo správy verzí Team Foundation), Agilního plánování (agilní, Scrum a CMMI podporuje), CI, Správa verzí a další nástroje pro agilní týmy.

-   Visual Studio Team Services nebo Team Foundation Server zahrnují výkonný a rostoucí ekosystém rozšíření první a třetí strany, pomocí kterých můžete snadno vytvořit položky konfigurace, sestavení, testovací, doručení a release management kanálu pro mikroslužeb.

-   Spuštění automatizovaných testů v rámci vašeho kanálu sestavení v sadě Visual Studio Team Services.

-   Visual Studio Team Services může posílit DevOps životního cyklu pro doručení na několika prostředích, nejen pro provozní prostředí, ale také pro testování, včetně A / B experimentování, [lesknice verzích](http://martinfowler.com/bliki/CanaryRelease.html)a tak dále.

-   Organizace můžou snadno zřídit Docker kontejnery z privátní bitové kopie uložené v registru kontejner Azure společně s závislost na Azure součásti (Data, PaaS atd.) pomocí nástroje, pomocí kterých jsou již šablon Azure Resource Manageru možnost práce.


>[!div class="step-by-step"]
[Předchozí] (.. / design-develop-containerized-apps/set-up-windows-containers-with-powershell.md) [Další] (docker-application-outer-loop-devops-workflow.md)
