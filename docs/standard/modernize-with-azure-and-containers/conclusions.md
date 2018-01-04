---
title: "Závěrů"
description: "Modernizovat existující aplikace .NET s cloudu Azure a Windows kontejnery | závěrů"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6e2f776b71fda9074605f072335a6e95366d2a97
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="conclusions"></a>Závěrů

-   Řešení založená na kontejneru nakonec zadejte úspory nákladů. Kontejnery jsou řešení problémů s nasazením, protože odebrat třecí nezdařila z důvodu absence závislostí v produkčním prostředí. Odebráním těchto problémů vylepšuje operace vývoje/testování, DevOps a produkční výrazně.

-   Kontejner Docker se stává stále standardní jednotka nasazení pro všechny služby nebo aplikace na serveru.

-   Pro provozní prostředí měli byste použít orchestrator (jako je Service Fabric nebo Kubernetes) na hostitele škálovatelné aplikace pracující s kontejnery Windows.

-   Virtuální počítače Azure hostování kontejnery jsou rychlý a jednoduchý způsob, jak vytvořit malých prostředích vývoje/testování v cloudu.

-   Ve výchozím nastavení se doporučuje Azure SQL Database spravované Instance, při migraci relačních databází z existujících aplikací do Azure.

-   Visual Studio 2017 a Image2Docker jsou základní nástroje spuštění modernizing existující aplikace .NET s kontejnery Windows podle urychlení získávání Začínáme křivku.

-   Při vkládání kontejnerizované aplikací v provozním prostředí vždy vytvoříte nebo přijmout jazykovou verzi DevOps a DevOps nástroje pro CI/CD kanálů, jako je Visual Studio Team Services nebo volaných.

-   Microsoft Azure poskytuje komplexní a úplné prostředí tak, aby modernizovat existující aplikace rozhraní .NET Framework s kontejnery Windows, cloudové infrastruktury a PaaS služby.

>[!div class="step-by-step"]
[Předchozí](walkthroughs-technical-get-started-overview.md)