---
title: Závěry
description: Modernizace existujících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Závěry
ms.date: 10/26/2017
ms.openlocfilehash: c7c4042b224577238ae74bd786d4803e487998e7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "68677105"
---
# <a name="conclusions"></a>Závěry

- Řešení založená na kontejnerech v konečném důsledku poskytují výhody úspor nákladů. Kontejnery jsou řešením problémů s nasazením, protože odstraňují tření způsobené absencí závislostí v produkčním prostředí. Odebráním těchto problémů výrazně vylepšuje vývoj/testování, devops a produkční operace.

- Kontejner Dockeru se stává standardní jednotkou nasazení pro všechny serverové aplikace nebo služby.

- Pro produkční prostředí byste měli použít orchestrator (jako Kubernetes) k hostování škálovatelných aplikací založených na kontejnerech.

- Hostování kontejnerů virtuálních počítače Azure je rychlý a jednoduchý způsob, jak vytvořit malá prostředí pro vývoj a testování v cloudu.

- Azure SQL Database Managed Instance se doporučuje ve výchozím nastavení při migraci relačních databází z existujících aplikací do Azure.

- Visual Studio 2017 a Image2Docker jsou základní nástroje pro zahájení modernizace stávajících aplikací .NET pomocí kontejnerů windows urychlením křivky učení začínáme.

- Při umísťování kontejnerizovaných aplikací do produkčního prostředí vždy vytvoříte nebo přijmete jazykovou verzi DevOps a nástroje DevOps pro kanály CI/CD, jako jsou azure devops services nebo Jenkins.

- Microsoft Azure poskytuje nejkomplexnější a nejkomplexnější prostředí pro modernizaci stávajících aplikací rozhraní .NET Framework pomocí kontejnerů Windows, cloudové infrastruktury a služeb PaaS.

>[!div class="step-by-step"]
>[Předchozí](walkthroughs-technical-get-started-overview.md)
