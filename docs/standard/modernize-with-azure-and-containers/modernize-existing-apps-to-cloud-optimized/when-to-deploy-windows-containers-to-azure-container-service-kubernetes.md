---
title: Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)
description: Modernizovat existující aplikace .NET s kontejnery cloudu Azure a Windows | Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/30/2018
ms.openlocfilehash: b7f106e2b79a2c6bb24733debf7f4828505d66a6
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
ms.locfileid: "33958290"
---
# <a name="when-to-deploy-windows-containers-to-azure-container-service-that-is-kubernetes"></a><span data-ttu-id="b4938-103">Když k nasazení Windows kontejnerů Azure Container Service (Kubernetes)</span><span class="sxs-lookup"><span data-stu-id="b4938-103">When to deploy Windows Containers to Azure Container Service (that is, Kubernetes)</span></span>

<span data-ttu-id="b4938-104">Azure Container Service optimalizuje konfigurace oblíbených open-source nástrojů a technologií speciálně pro Azure.</span><span class="sxs-lookup"><span data-stu-id="b4938-104">Azure Container Service optimizes the configuration of popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="b4938-105">Získat otevřete řešení, která nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4938-105">You get an open solution that offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="b4938-106">Můžete vybrat, velikost, počtu hostitelů a nástroje orchestrator.</span><span class="sxs-lookup"><span data-stu-id="b4938-106">You select the size, the number of hosts, and the orchestrator tools.</span></span> <span data-ttu-id="b4938-107">Azure Container Service zpracovává infrastruktury pro vás.</span><span class="sxs-lookup"><span data-stu-id="b4938-107">Azure Container Service handles the infrastructure for you.</span></span>

<span data-ttu-id="b4938-108">Pokud již pracujete s otevřeným zdrojem orchestrators jako Kubernetes, Docker Swarm nebo DC/OS, nemusíte měnit vaše stávající postupy správy pro přesun kontejneru úloh do cloudu.</span><span class="sxs-lookup"><span data-stu-id="b4938-108">If you are already working with open-source orchestrators like Kubernetes, Docker Swarm, or DC/OS, you don't need to change your existing management practices to move container workloads to the cloud.</span></span> <span data-ttu-id="b4938-109">Pomocí nástroje pro správu aplikací, které jste již obeznámeni s a připojení přes standardní koncové body rozhraní API pro nástroj orchestrator podle svého výběru.</span><span class="sxs-lookup"><span data-stu-id="b4938-109">Use the application management tools that you're already familiar with and connect via the standard API endpoints for the orchestrator of your choice.</span></span>

<span data-ttu-id="b4938-110">Všechny tyto orchestrators jsou vyspělá prostředí, pokud používáte Linux Docker kontejnery, ale může být pouze ve verzi Preview stavu pro kontejnery systému Windows.</span><span class="sxs-lookup"><span data-stu-id="b4938-110">All these orchestrators are mature environments if you are using Linux Docker containers, but might only be in Preview state for Windows Containers.</span></span>

<span data-ttu-id="b4938-111">Například v Kubernetes, podporu pro kontejnery je nativní (prvotřídní občan), takže použití Windows kontejnerů na Kubernetes je také efektivní (ve verzi preview v rámci služby ACS od časná 2018).</span><span class="sxs-lookup"><span data-stu-id="b4938-111">For example, in Kubernetes, support for containers is native (first-class citizen), so using Windows Containers on Kubernetes is also effective (in preview in ACS as of early 2018).</span></span>

<span data-ttu-id="b4938-112">Důležité upozornění: evolved a "Další PaaS" je verze služby ACS (Azure Container Service) pro Kubernetes AKS (Azure Kubernetes Service), Windows kontejnery nepodporují stále od 2018 Dotaz č. 2, ale budou brzy podporované.</span><span class="sxs-lookup"><span data-stu-id="b4938-112">Important note: The evolved and “more PaaS” version of ACS (Azure Container Service) for Kubernetes is AKS (Azure Kubernetes Service), however, Windows Containers are still not supported as of Q2 2018, but it will be supported soon.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="b4938-113">[Předchozí](when-to-deploy-windows-containers-to-service-fabric.md)
[další](choosing-azure-compute-options-for-container-based-applications.md)</span><span class="sxs-lookup"><span data-stu-id="b4938-113">[Previous](when-to-deploy-windows-containers-to-service-fabric.md)
[Next](choosing-azure-compute-options-for-container-based-applications.md)</span></span>
