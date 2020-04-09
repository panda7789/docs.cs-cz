---
title: Kdy nasadit kontejnery Windows do služby Azure Container Service (to znamená Kubernetes)
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Kdy nasadit kontejnery Windows do služby Azure Container Service (to znamená Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 3ff51a70d4e158b831155ab4992ec32f5d98cedb
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987761"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="12c2a-103">Kdy nasadit kontejnery Windows do služby Azure Container Service (to znamená Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="12c2a-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="12c2a-104">Azure Container Service optimalizuje konfiguraci oblíbených open source nástrojů a technologií speciálně pro Azure.</span><span class="sxs-lookup"><span data-stu-id="12c2a-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="12c2a-105">Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="12c2a-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="12c2a-106">Můžete vybrat velikost, počet hostitelů a nástroje orchestrator.</span><span class="sxs-lookup"><span data-stu-id="12c2a-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="12c2a-107">Azure Container Service zpracovává infrastrukturu za vás.</span><span class="sxs-lookup"><span data-stu-id="12c2a-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="12c2a-108">Pokud už pracujete s orchestrátory s otevřeným zdrojovým kódem, jako jsou Kubernetes, Docker Swarm nebo DC/OS, nemusíte měnit stávající postupy správy, abyste přesunuli úlohy kontejnerů do cloudu.</span><span class="sxs-lookup"><span data-stu-id="12c2a-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="12c2a-109">Použijte nástroje pro správu aplikací, které už znáte, a připojte se přes standardní koncové body rozhraní API pro orchestrátorpodle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="12c2a-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="12c2a-110">Všechny tyto orchestrátory jsou vyspělá prostředí, pokud používáte kontejnery Linux Docker, ale může být pouze ve stavu Náhled pro kontejnery systému Windows.</span><span class="sxs-lookup"><span data-stu-id="12c2a-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="12c2a-111">Například v Kubernetes je podpora kontejnerů nativní (prvotřídní občan), takže použití kontejnerů Windows na Kubernetes je také efektivní (ve verzi Preview v ACS od začátku roku 2018).</span><span class="sxs-lookup"><span data-stu-id="12c2a-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="12c2a-112">Důležitá poznámka: Vyvinutá a "více PaaS" verze ACS (Azure Container Service) pro Kubernetes je AKS (Služba Azure Kubernetes), ale kontejnery Windows stále nejsou podporovány od Q2 2018, ale brzy budou podporovány.</span><span class="sxs-lookup"><span data-stu-id="12c2a-112">Important note: The evolved and "more PaaS" version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="12c2a-113">[Předchozí](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[další](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="12c2a-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
