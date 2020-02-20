---
title: Volba výpočetních platforem Azure pro aplikace založené na kontejnerech
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Výběr platforem Azure COMPUTE pro aplikace založené na kontejnerech
ms.date: 02/18/2020
ms.openlocfilehash: 52e7cf1c5dd3a5850564bdb33ac7a4ac4904f432
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503877"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Volba výpočetních platforem Azure pro aplikace založené na kontejnerech

Jakmile jste si všimli, že jste si přečetli předchozí části, je Azure otevřeným cloudem, který nabízí víc možností. Pro vaše potřeby můžete použít nejvhodnější, ale také si vyřadíme otázky týkající se produktu nebo technologie, které byste měli použít pro své aplikace v kontejneru.

V rámci *výchozího* doporučení jsou tady uvedená hlavní kritéria, která jsou doporučena v těchto pokynech:

- **Jedna aplikace monolitické:** Zvolit Azure App Service
- **N-vrstvá aplikace:** Vyberte orchestrace, jako je Azure Kubernetes Service (AKS), nebo App Service, pokud máte jednu nebo několik back-endové služeb.
- **Mikroslužby:** Výběr AKS nebo Azure Web Apps pro kontejnery
- **Funkce bez serveru & obslužné rutiny událostí:** Zvolit Azure Functions
- **Velká škála dávek:** Zvolit Azure Batch

Toto doporučení je ale potřeba vzít s gesto roztažení prstůou sůl, protože výběr produktu bude záviset na potřebách a vlastnostech konkrétní aplikace. Ne všechny aplikace jsou stejné, i když zpočátku můžou vypadat podobné typy.

Po hlubší analýze potřeb aplikace může být vybraný produkt jiný. Ale jako výchozí bod je dobré mít počáteční pokyny, ze kterých můžete začít vyhodnocovat a testovat na základě určité priority.

V následující tabulce vidíte rozpis různých druhů aplikací a jejich možné a doporučené hostitelské scénáře Azure.

| Architektura aplikace | Virtuální počítače – Azure Virtual Machines | ACI – Azure Container Instances | Azure App Service (počet kontejnerů: w-w/o) | AKS – Azure Kubernetes Services | Azure Functions | Azure Batch |
|:------------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Webové aplikace (monolitické)**         | ![Možné s virtuálními počítači](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Možné s ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Doporučuje se s App Service](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Možné s AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | |
| **N-vrstvé aplikace (služby)**        | ![Možné s virtuálními počítači](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Možné s ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Doporučuje se s App Service](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Možné s AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Možné s Azure fuctions](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | |
| **Cloud – nativní (mikroslužby)**  | | ![Možné s ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | ![Doporučuje se s AKS](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Kontejnery&nbsp;Linux)| ![Doporučuje se s Azure Functions](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Řízený&#x2011;událost) | |
| **Batch/úlohy (úlohy na pozadí)** | ![Možné s virtuálními počítači](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Možné s ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Možné s App Service](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Možné s AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Doporučuje se s Azure Functions](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Úlohy&nbsp;na pozadí) | ![Doporučuje se s Azure Batch](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Velký&#x2011;rozsah) |

**Popisek**

![Doporučená ikona](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) Doporučil
![Možná ikona](media/choosing-azure-compute-options-for-container-based-applications/possible.png) Provést

> [!div class="step-by-step"]
> [Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [Další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
