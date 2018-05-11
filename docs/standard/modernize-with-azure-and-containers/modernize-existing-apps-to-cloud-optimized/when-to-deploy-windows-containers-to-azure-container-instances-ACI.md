---
title: Při nasazení kontejnerů Windows do Azure kontejner instancí (ACI)
description: Modernizovat existující aplikace .NET s kontejnery cloudu Azure a Windows | Při nasazení kontejnerů Windows do Azure kontejner instancí (ACI)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/29/2018
ms.openlocfilehash: 3dc23c96543d9611763b571105f52b150dfec06f
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
---
# <a name="when-to-deploy-windows-containers-to-azure-container-instances-aci"></a>Při nasazení kontejnerů Windows do Azure kontejner instancí (ACI)

Azure instancí kontejnerů, které hlavní hodnotu je, že k němu můžete hned nasadit kontejnery a nemusíte spravovat prostředí, není třeba upgrade nebo opravu podkladové operační systém nebo virtuálních počítačů, všechny které je transparentní a jen nasadit kontejnery do prostředí připravené k použití.

Scénáře, kdy je vhodné použít ACI a z důvodů je podobná hlavní scénáře, když používáte virtuální počítače Azure s kontejnery, proto je v podstatě, hlavní scénáře pomocí Azure kontejner instancí jsou:

-   **Scénáře vývoje/testování**
-   **Automatizace úloh**
-   **Agenti CI/CD**
-   **Malá nebo škálování dávkové zpracování**
-   **Jednoduché webové aplikace**

Tento scénář jednoduché webové aplikace je správného scénáře pro ACI ale vezměte v úvahu, že vzhledem k tomu, že v ACI může mít pouze instance jediný kontejner pro bitovou kopii kontejneru, nebude mít vysokou dostupnost a mají omezenou škálovatelnost.

I když ACI se považuje za infrastrukturu, protože nabízí jen jediný kontejner instancí, je však obrovské výhody ve srovnání s regulární virtuálních počítačích Azure se systémem Windows Server. S ACI jen nasadit kontejnery do prostředí samoobslužné zachována a platíte jenom za těchto kontejnerech. Nemusíte spravovat/aktualizace nebo opravy virtuálních počítačů, takže je mnohem lepší platformu pro většinu scénářů, kde můžete používat virtuální počítače s kontejnery. Použití ACI je přímo dál, jen nasadit kontejner, není nutné k vytvoření prostředí virtuálních počítačů právě nasazení kontejnerů.

Hlavní výhody z Azure kontejner instancí (ACI) jsou:

-   Spustit kontejnery bez Správa serverů
-   Zvýšení flexibility s kontejnery na vyžádání
-   Kontejnery můžete nasadit do cloudu s nebývalá jednoduchost a rychlost – jedním příkazem. 
-   Zabezpečené aplikace s izolací hypervisoru

Stručně řečeno s ACI můžete vyvíjet aplikace, rychlé bez správu virtuálních počítačů, nebo máte nové nástroje. Je právě aplikace v kontejneru, běží v cloudu.

>[!div class="step-by-step"]
[Předchozí](when-to-deploy-windows-containers-to-azure-vms-iaas-cloud.md)
[další](when-to-deploy-windows-containers-to-service-fabric.md)
