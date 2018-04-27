---
title: Spouštět, spravovat a monitorovat Docker produkční prostředí
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 41c170b5e58d92c6e669de48c1f41caf5b2aa6e8
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="run-manage-and-monitor-docker-production-environments"></a><span data-ttu-id="c7a42-103">Spouštět, spravovat a monitorovat Docker produkční prostředí</span><span class="sxs-lookup"><span data-stu-id="c7a42-103">Run, manage, and monitor Docker production environments</span></span>

<span data-ttu-id="c7a42-104">Vizi: Podnikové aplikace, které musí spustit s vysokou dostupnost a škálovatelnost vysoké; IT oddělení musí být schopné spravovat a monitorovat prostředí a aplikace samotné.</span><span class="sxs-lookup"><span data-stu-id="c7a42-104">Vision: Enterprise applications need to run with high availability and high scalability; IT operations need to be able to manage and monitor the environments and the applications themselves.</span></span>

<span data-ttu-id="c7a42-105">Tento poslední pilíře kontejnerizované životního cyklu aplikací Docker se jedná o tom, jak můžete spouštět, spravovat a monitorujte své aplikace v produkčním prostředí, škálovatelnou a vysoké dostupnosti (HA).</span><span class="sxs-lookup"><span data-stu-id="c7a42-105">This last pillar in the containerized Docker applications life cycle is centered on how you can run, manage, and monitor your applications in scalable, high availability (HA) production environments.</span></span>

<span data-ttu-id="c7a42-106">Jak spouštět kontejnerizované aplikace v produkčním prostředí (platformu a architektura technologie infrastruktury) je také velmi dobře související a úplně založená na zvolené architektury a vývoj platformy, které jsme se podívali na v kapitole 1 tohoto objektu elektronická kniha.</span><span class="sxs-lookup"><span data-stu-id="c7a42-106">How you run your containerized applications in production (infrastructure architecture and platform technologies) is also very much related and completely founded on the chosen architecture and development platforms that we looked at in the Chapter 1 of this e-book.</span></span> <span data-ttu-id="c7a42-107">Tato kapitola prozkoumá konkrétní produkty a technologie společnosti Microsoft a jiných dodavatelů, které můžete efektivně provozovat vysoce škálovatelné, HA distribuované aplikace a jak můžete spravovat a monitorovat je z hlediska oddělení IT.</span><span class="sxs-lookup"><span data-stu-id="c7a42-107">This chapter examines specific products and technologies from Microsoft and other vendors that you can use to effectively run highly scalable, HA distributed applications plus how you can manage and monitor them from the IT perspective.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="c7a42-108">[Předchozí] (.. / docker-devops-workflow/docker-application-outer-loop-devops-workflow.md) [Další] (run-microservices-based-applications-in-production.md)</span><span class="sxs-lookup"><span data-stu-id="c7a42-108">[Previous] (../docker-devops-workflow/docker-application-outer-loop-devops-workflow.md) [Next] (run-microservices-based-applications-in-production.md)</span></span>
