---
title: Závěry
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a kontejnery Windows | závěry
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 62a9a38ccbe696c34ef799b574c0f5a95bc8f726
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628324"
---
# <a name="conclusions"></a>Závěry

- Řešení založených na kontejnerech nakonec poskytují výhod úspory nákladů. Kontejnery jsou řešení problémů s nasazením, protože odstraňují řešit zádrhele spojené s způsobené absence závislosti v produkčním prostředí. Odebráním těchto problémů výrazně zvyšuje operace pro vývoj/testování, DevOps a produkčním prostředí.

- Kontejner Dockeru se standardní jednotkou nasazení pro všechny serverové aplikace nebo služba.

- Pro produkční prostředí měli byste použít k hostování škálovatelných aplikací založených na kontejnerech Windows orchestrátoru (jako je Service Fabric nebo Kubernetes).

- Virtuální počítače Azure hostování kontejnerů jsou rychlý a jednoduchý způsob, jak vytvořit malých vývojových/testovacích prostředí v cloudu.

- Azure SQL Database Managed Instance se doporučuje ve výchozím nastavení při migraci relačních databází z existujících aplikací do Azure.

- Visual Studio 2017 a Image2Docker jsou základní nástroje pro spuštění modernizujete stávající aplikace .NET s kontejnery Windows ve urychlení získávání začít učit se.

- Při vkládání kontejnerizovaných aplikací v produkčním prostředí vždy vytvoříte nebo přijmout kulturu DevOps a nástroje DevOps pro kanály CI/CD, jako je Azure DevOps Services nebo Jenkinse.

- Microsoft Azure poskytuje komplexní a úplné prostředí tak, aby modernizovat existující aplikace rozhraní .NET Framework s kontejnery Windows, cloudové infrastruktury a služby PaaS.

>[!div class="step-by-step"]
>[Předchozí](walkthroughs-technical-get-started-overview.md)