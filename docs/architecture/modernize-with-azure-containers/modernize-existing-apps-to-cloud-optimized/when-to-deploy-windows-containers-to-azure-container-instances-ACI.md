---
title: Kdy nasadit kontejnery Windows do Azure Container Instances (ACI)
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Kdy nasadit kontejnery Windows do Azure Container Instances (ACI)
ms.date: 04/29/2018
ms.openlocfilehash: 3b6ae1ced9c4e01f5ab400e2575947a396064ebd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676907"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Kdy nasadit kontejnery Windows do Azure Container Instances (ACI)

Azure Container Instances hlavní pozice hodnoty znamená, že můžete do ní hned nasadit kontejnery a nemusíte ho udržovat, nemusíte upgradovat/opravovat základní operační systémy nebo virtuální počítače, které jsou transparentní a stačí nasadit kontejnery do prostředí, které je připraveno k použití.

Důvody a scénáře, kdy byste chtěli použít ACI, jsou podobné hlavním scénářům při použití virtuálních počítačů Azure s kontejnery, a to v podstatě hlavní scénáře použití Azure Container Instances:

- **Scénáře pro vývoj a testování**
- **Automatizace úloh**
- **Agenti CI/CD**
- **Dávkové zpracování malých nebo škálovatelných**
- **Jednoduché webové aplikace**

Scénář jednoduché webové aplikace je spravedlivý scénář pro ACI, ale vezme v úvahu, že protože v ACI máte jenom jednu instanci kontejneru na Image kontejneru, nebudete mít vysokou dostupnost a máte jenom omezené škálovatelnost.

I když se ACI považuje za infrastrukturu, protože poskytuje jenom jednu instanci kontejneru, je ve srovnání s běžnými virtuálními počítači Azure s Windows serverem velký přínos. V ACI stačí nasadit kontejnery do samostatného prostředí a Vy jenom platíte za tyto kontejnery. Nemusíte spravovat/aktualizovat/opravovat virtuální počítače, takže je to mnohem lepší platforma pro většinu scénářů, ve kterých můžete používat virtuální počítače s kontejnery. Použití ACI je rovné, stačí pouze nasadit kontejner, takže nemusíte vytvářet prostředí virtuálních počítačů, které pouze nasazujete kontejnery.

Hlavní výhody Azure Container Instances (ACI) jsou:

- Spouštění kontejnerů bez správy serverů
- Zvýšení flexibility pomocí kontejnerů na vyžádání
- Pomocí jediného příkazu můžete nasadit kontejnery do cloudu s nepředchůdci a rychlostí.
- Zabezpečení aplikací s izolací hypervisoru

V krátkém ACI můžete rychle vyvíjet aplikace bez nutnosti spravovat virtuální počítače nebo se seznámit s novými nástroji. Je to jenom vaše aplikace v kontejneru spuštěná v cloudu.

> [!div class="step-by-step"]
> [Předchozí](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)Další
> [](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
