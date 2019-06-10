---
title: Kdy nasadit kontejnery Windows do Azure Container Service (Kubernetes)
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Kdy nasadit kontejnery Windows do Azure Container Service (Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758564"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="19669-103">Kdy nasadit kontejnery Windows do Azure Container Service (Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="19669-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="19669-104">Služba Azure Container Service optimalizuje konfiguraci oblíbených opensourcových nástrojů a technologií konkrétně pro Azure.</span><span class="sxs-lookup"><span data-stu-id="19669-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="19669-105">Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i Konfigurace aplikací.</span><span class="sxs-lookup"><span data-stu-id="19669-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="19669-106">Vyberete velikost, počet hostitelů a nástroje orchestrator.</span><span class="sxs-lookup"><span data-stu-id="19669-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="19669-107">Služba Azure Container Service obstarává infrastrukturu za vás.</span><span class="sxs-lookup"><span data-stu-id="19669-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="19669-108">Pokud již pracujete s open source orchestrátorů, jako je Kubernetes, Docker Swarm nebo DC/OS, nemusíte měnit svoje dosavadní postupy správy chcete přesunout úlohy kontejnerů do cloudu.</span><span class="sxs-lookup"><span data-stu-id="19669-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="19669-109">Pomocí nástroje pro správu aplikací, které jste již obeznámeni s a připojte se pomocí standardních koncových bodů rozhraní API k orchestrátoru podle vaší volby.</span><span class="sxs-lookup"><span data-stu-id="19669-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="19669-110">Všechny tyto orchestrátorů jsou až po zralé prostředí, pokud používáte kontejnery linuxového Dockeru, ale může být pouze ve verzi Preview pro kontejnery Windows.</span><span class="sxs-lookup"><span data-stu-id="19669-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="19669-111">Například v Kubernetes, podpora kontejnerů je nativní (prvotřídní občany), takže pomocí kontejnerů Windows v Kubernetes platí také (ve verzi preview ve službě ACS od začátkem roku 2018).</span><span class="sxs-lookup"><span data-stu-id="19669-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="19669-112">Důležitá poznámka: Evolved a "Další PaaS" verze služby ACS (Azure Container Service) pro Kubernetes je AKS (služby Azure Kubernetes Service), ale kontejnerů Windows se ještě nepodporují od 2. čtvrtletí 2018, ale bude brzy podporovat.</span><span class="sxs-lookup"><span data-stu-id="19669-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="19669-113">[Předchozí](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[další](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="19669-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
