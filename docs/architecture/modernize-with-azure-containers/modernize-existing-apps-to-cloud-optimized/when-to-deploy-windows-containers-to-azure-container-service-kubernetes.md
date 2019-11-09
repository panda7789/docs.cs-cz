---
title: Kdy nasadit kontejnery Windows do Azure Container Service (tj. Kubernetes)
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Kdy nasadit kontejnery Windows do Azure Container Service (tj. Kubernetes)
ms.date: 04/30/2018
ms.openlocfilehash: 903082deba635dd0dfc22d0186fbc589f8d05b92
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676910"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="97b2f-103">Kdy nasadit kontejnery Windows do Azure Container Service (tj. Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="97b2f-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="97b2f-104">Azure Container Service optimalizuje konfiguraci oblíbených open source nástrojů a technologií konkrétně pro Azure.</span><span class="sxs-lookup"><span data-stu-id="97b2f-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="97b2f-105">Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="97b2f-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="97b2f-106">Vyberte velikost, počet hostitelů a nástroje Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="97b2f-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="97b2f-107">Azure Container Service zpracovává infrastrukturu za vás.</span><span class="sxs-lookup"><span data-stu-id="97b2f-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="97b2f-108">Pokud už pracujete s open source orchestrací, jako je Kubernetes, Docker Swarm nebo DC/OS, nemusíte měnit stávající postupy správy, aby bylo možné přesunout úlohy kontejneru do cloudu.</span><span class="sxs-lookup"><span data-stu-id="97b2f-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="97b2f-109">Použijte nástroje pro správu aplikací, které už znáte, a připojte se přes standardní koncové body rozhraní API pro Orchestrator podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="97b2f-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="97b2f-110">Všechny tyto orchestrace jsou vyspělá prostředí, pokud používáte kontejnery Docker pro Linux, ale můžou být jenom ve verzi Preview pro kontejnery Windows.</span><span class="sxs-lookup"><span data-stu-id="97b2f-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="97b2f-111">Například v Kubernetes je podpora pro kontejnery nativní (občan první třídy), takže použití kontejnerů Windows v Kubernetes je také účinné (ve verzi Preview ve službě ACS k začátku 2018).</span><span class="sxs-lookup"><span data-stu-id="97b2f-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="97b2f-112">Důležité upozornění: vývojová a další PaaS verze ACS (Azure Container Service) pro Kubernetes je AKS (služba Azure Kubernetes), ale kontejnery Windows se ještě nepodporují od Q2 2018, ale budou se brzy podporovat.</span><span class="sxs-lookup"><span data-stu-id="97b2f-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="97b2f-113">[Předchozí](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
>[Další](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="97b2f-113">[Previous](when-to-deploy-windows-containers-to-azure-container-instances-ACI.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
