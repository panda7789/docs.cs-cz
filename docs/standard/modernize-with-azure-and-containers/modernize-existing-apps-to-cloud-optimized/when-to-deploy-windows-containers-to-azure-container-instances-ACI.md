---
title: Kdy nasadit kontejnery Windows do Azure Container Instances (ACI)
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Kdy nasadit kontejnery Windows do Azure Container Instances (ACI)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 03ee7c8b65e1a92dcc7fd40b44e9ba081f571487
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674403"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Kdy nasadit kontejnery Windows do Azure Container Instances (ACI)

Služba Azure Container Instances, hlavní hodnotové je, můžete okamžitě nasazení kontejnerů do ní a není nutné udržovat prostředí, není nutné upgradování, opravování základní operační systém nebo virtuálních počítačů, všechny, které je transparentní a jen nasadit kontejnery do prostředí připravené k použití.

Z důvodů a scénáře, kdy je vhodné použít ACI jsou podobné hlavní scénáře, pokud používáte virtuální počítače Azure s kontejnery, tedy v podstatě, jsou hlavní scénáře pomocí služby Azure Container Instances:

- **Scénáře vývoje/testování**
- **Automatizace úloh**
- **Agenti CI/CD**
- **Dávkové zpracování (krátkodobé používání) nebo exponent**
- **Jednoduché webové aplikace**

Scénář jednoduché webové aplikace je veletrh scénářem ACI, ale vezměte v úvahu, že vzhledem k tomu, že v ACI může mít pouze jeden kontejner instance za image kontejneru, nebudou mít vysokou dostupnost a pouze omezená škálovatelnost.

Nicméně i v případě, že ACI je považován za infrastrukturu, protože poskytuje právě jeden kontejner instancí, je obrovská výhoda ve srovnání s běžnými virtuálními počítači Azure s Windows serverem. Pomocí ACI jen nasadit kontejnery do prostředí s místním udržované a platíte jenom za těchto kontejnerů. Není nutné udržovat/aktualizací a oprav virtuálních počítačů, tak, aby byl mnohem lepší platformu pro většinu scénářů, kde je možné, že používáte virtuální počítače s kontejnery. Pomocí ACI je snadná, stačí nasadit kontejner, není nutné k vytvoření virtuálního počítače prostředí jen nasadit kontejnery.

Hlavní výhody služby Azure Container Instances (ACI) jsou:

- Spouštění kontejnerů bez správy serverů
- Zvýšení agility s kontejnery na vyžádání
- Nasazení kontejnerů do cloudu mimořádně rychle a snadno – pomocí jediného příkazu.
- Zabezpečené aplikace s izolací hypervisoru

Stručně řečeno s ACI můžete vyvíjet aplikace rychle bez správu virtuálních počítačů a nemusíte se učit nové nástroje. Je to jenom vaše aplikace v kontejneru spuštěná v cloudu.

> [!div class="step-by-step"]
> [Předchozí](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
> [další](when-to-deploy-windows-containers-to-service-fabric.md)
