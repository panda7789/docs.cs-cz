---
title: Spuštění, Správa a monitorování produkčních prostředí Dockeru
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 9c24a87fd691723b8f91077288478d26e5123265
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219123"
---
# <a name="run-manage-and-monitor-docker-production-environments"></a><span data-ttu-id="c5b74-103">Spuštění, Správa a monitorování produkčních prostředí Dockeru</span><span class="sxs-lookup"><span data-stu-id="c5b74-103">Run, manage, and monitor Docker production environments</span></span>

<span data-ttu-id="c5b74-104">Pro zpracování obrazu: Podnikové aplikace je potřeba spustit s vysokou dostupností a vysokou škálovatelnost; IT oddělení musí mít možnost spravovat a monitorovat prostředí a samotnými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="c5b74-104">Vision: Enterprise applications need to run with high availability and high scalability; IT operations need to be able to manage and monitor the environments and the applications themselves.</span></span>

<span data-ttu-id="c5b74-105">Tento poslední pilíř v životní cyklus kontejnerizované aplikace Dockeru se jedná o jak můžete spouštět, spravovat a monitorujte své aplikace v produkčním prostředí škálovatelné, vysokou dostupnost (HA).</span><span class="sxs-lookup"><span data-stu-id="c5b74-105">This last pillar in the containerized Docker applications life cycle is centered on how you can run, manage, and monitor your applications in scalable, high availability (HA) production environments.</span></span>

<span data-ttu-id="c5b74-106">Spouštění kontejnerizovaných aplikací v produkčním prostředí (architektury a platformy technologií infrastruktury) je také velmi související a zcela založená na zvolené pro architekturu a vývoj platforem, které jsme se podívali na v kapitole 1 tohoto objektu e kniha.</span><span class="sxs-lookup"><span data-stu-id="c5b74-106">How you run your containerized applications in production (infrastructure architecture and platform technologies) is also very much related and completely founded on the chosen architecture and development platforms that we looked at in the Chapter 1 of this e-book.</span></span> <span data-ttu-id="c5b74-107">Tato kapitola zkontroluje konkrétní produkty a technologiemi od Microsoftu a jiných dodavatelů, které můžete efektivně provozovat vysoce škálovatelné, vysokou dostupnost distribuované aplikace a jak můžete spravovat a monitorovat z hlediska oddělení IT.</span><span class="sxs-lookup"><span data-stu-id="c5b74-107">This chapter examines specific products and technologies from Microsoft and other vendors that you can use to effectively run highly scalable, HA distributed applications plus how you can manage and monitor them from the IT perspective.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c5b74-108">[Předchozí](../docker-devops-workflow/create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
>[další](run-microservices-based-applications-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="c5b74-108">[Previous](../docker-devops-workflow/create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
[Next](run-microservices-based-applications-in-production.md)</span></span>