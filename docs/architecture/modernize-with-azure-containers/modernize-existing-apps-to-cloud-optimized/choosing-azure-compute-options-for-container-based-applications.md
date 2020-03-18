---
title: Volba výpočetních platforem Azure pro aplikace založené na kontejnerech
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Výběr výpočetních platforem Azure pro aplikace založené na kontejnerech
ms.date: 02/18/2020
ms.openlocfilehash: 52e7cf1c5dd3a5850564bdb33ac7a4ac4904f432
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503877"
---
# <a name="choosing-azure-compute-platforms-for-container-based-applications"></a>Volba výpočetních platforem Azure pro aplikace založené na kontejnerech

Jak jste si všimli po přečtení předchozích částí, Azure je otevřený cloud, který nabízí několik možností. Můžete použít nejvhodnější pro vaše potřeby, ale také povrchy otázky o tom, co produkt / technologie, které byste měli použít pro vaše kontejnerizované aplikace.

Jako *doporučení podle výchozích hodnot* jsou hlavní kritéria doporučená v těchto pokynech následující:

- **Jedna monolitická aplikace:** Zvolte službu Azure App Service
- **N-vrstvá aplikace:** Pokud máte jednu nebo několik back-endových služeb, vyberte si orchestrátory, jako je služba Azure Kubernetes Service (AKS) nebo App Service.
- **Mikroslužeb:** Zvolte AKS nebo Azure Web Apps pro kontejnery
- **Funkce bez serveru & obslužné rutiny událostí:** Zvolte funkce Azure
- **Dávka ve velkém měřítku:** Zvolte Azure Batch

Toto doporučení by však mělo být přijato se špetkou soli, protože výběr produktu bude záviset na potřebách a vlastnostech vaší konkrétní aplikace. Ne všechny aplikace jsou stejné, i když zpočátku mohou vypadat podobné typy.

Po hlubší analýze potřeb aplikace se vybraný produkt může lišit. Ale jako výchozí bod, je dobré mít počáteční pokyny, odkud můžete začít hodnocení a testování na základě určité priority.

V následující tabulce uvidíte rozpis různých druhů aplikací a jejich možné a doporučené scénáře hostování Azure.

| Architektura aplikací | Virtuální počítače – virtuální počítače Azure | ACI – instance kontejnerů Azure | Služba Azure App Service (w-w/o kontejnery) | AKS - Služby Azure Kubernetes | Azure Functions | Azure Batch |
|:------------------------:|:--:|:--:|:--:|:--:|:--:|:--:|
| **Webové aplikace (monolitické)**         | ![Možné s virtuálními ms](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Možné s ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Doporučeno se službou App Service](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Možné s AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | |
| **N-Vrstvé aplikace (služby)**        | ![Možné s virtuálními ms](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Možné s ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Doporučeno se službou App Service](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) | ![Možné s AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Možné s Azure Fuctions](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | |
| **Nativní pro cloud (mikroslužby)**  | | ![Možné s ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | | ![Doporučeno u AKS](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Linuxové&nbsp;kontejnery)| ![Doporučeno s funkcemi Azure](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Akce&#x2011;řízena) | |
| **Dávkové/úlohy (úlohy na pozadí)** | ![Možné s virtuálními ms](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Možné s ACI](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Možné se službou App Service](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Možné s AKS](media/choosing-azure-compute-options-for-container-based-applications/possible.png) | ![Doporučeno s funkcemi Azure](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Úlohy na pozadí)&nbsp; | ![Doporučeno s Azure Batch](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) <br/> (Velké&#x2011;měřítku) |

**Legenda**

![Doporučená ikona](media/choosing-azure-compute-options-for-container-based-applications/recommended.png) Doporučeno \
![Možná ikona](media/choosing-azure-compute-options-for-container-based-applications/possible.png) Možné

> [!div class="step-by-step"]
> [Předchozí](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
> [další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)
