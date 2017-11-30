---
title: "Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: f5ba7aa2cf14e7ca9f3a1f3eb12bbe236dca7e97
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="eb8cb-103">Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="eb8cb-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="eb8cb-104">Azure Container Service optimalizuje konfigurace oblíbených open-source nástrojů a technologií speciálně pro Azure.</span><span class="sxs-lookup"><span data-stu-id="eb8cb-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="eb8cb-105">Získat otevřete řešení, která nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="eb8cb-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="eb8cb-106">Můžete vybrat, velikost, počtu hostitelů a nástroje orchestrator.</span><span class="sxs-lookup"><span data-stu-id="eb8cb-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="eb8cb-107">Azure Container Service zpracovává infrastruktury pro vás.</span><span class="sxs-lookup"><span data-stu-id="eb8cb-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="eb8cb-108">Pokud již pracujete s otevřeným zdrojem orchestrators jako Kubernetes, Docker Swarm nebo DC/OS, nemusíte měnit vaše stávající postupy správy pro přesun kontejneru úloh do cloudu.</span><span class="sxs-lookup"><span data-stu-id="eb8cb-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="eb8cb-109">Pomocí nástrojů pro správu aplikaci jste již obeznámeni s a připojení přes standardní koncové body rozhraní API pro nástroj orchestrator podle svého výběru.</span><span class="sxs-lookup"><span data-stu-id="eb8cb-109">Use the application management tools that you're already familiar with, and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="eb8cb-110">Pokud používáte Linux Docker kontejnery, ale jejich také podporu Windows kontejnery jako z 2017 (některé dříve, některé nedávno, v závislosti na orchestrator), jsou všechny tyto orchestrators vyspělá prostředí.</span><span class="sxs-lookup"><span data-stu-id="eb8cb-110">All these orchestrators are mature environments if you are using Linux Docker containers, but they also support Windows Containers as of 2017 (some earlier, some more recently, depending on the orchestrator).</span></span>

<span data-ttu-id="eb8cb-111">Například v Kubernetes, podporu pro kontejnery je nativní (prvotřídní občan), takže použití Windows kontejnerů na Kubernetes je také velmi efektivní a spolehlivý (ve verzi preview, dokud již v rané fázi spadají 2017).</span><span class="sxs-lookup"><span data-stu-id="eb8cb-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also very effective and reliable (in preview until early fall 2017).</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="eb8cb-112">[Předchozí](when-to-deploy-windows-containers-to-service-fabric.md)
[další](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span><span class="sxs-lookup"><span data-stu-id="eb8cb-112">[Previous](when-to-deploy-windows-containers-to-service-fabric.md)
[Next](build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud.md)</span></span>
