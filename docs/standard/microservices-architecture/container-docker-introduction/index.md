---
title: "Úvod ke kontejnerům a Docker"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Úvod ke kontejnerům a Docker"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8809ae41609ff0e2d2fc969d412cb5edc8939653
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="6c0bf-104">Úvod ke kontejnerům a Docker</span><span class="sxs-lookup"><span data-stu-id="6c0bf-104">Introduction to Containers and Docker</span></span>

<span data-ttu-id="6c0bf-105">Rozdělení do kontejnerů je přístup k vývoji softwaru, ve kterém aplikace nebo služby, jeho závislosti a jeho konfigurace (abstrahované jako soubory manifestu nasazení) a instalace balíčku jako obrázek na kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6c0bf-105">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="6c0bf-106">Kontejnerizované aplikace jako jednotku otestovat a nasadit jako instance image kontejner pro hostitelský operační systém (OS).</span><span class="sxs-lookup"><span data-stu-id="6c0bf-106">The containerized application can be tested as a unit and deployed as a container image instance to the host operating system (OS).</span></span>

<span data-ttu-id="6c0bf-107">Stejně jako kontejnery přesouvání povolit přepravy lodě, train nebo vůz bez ohledu na to nákladní uvnitř zboží, kontejnery softwaru fungují jako jednotka se software, který může obsahovat různé kódu a závislosti.</span><span class="sxs-lookup"><span data-stu-id="6c0bf-107">Just as shipping containers allow goods to be transported by ship, train, or truck regardless of the cargo inside, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="6c0bf-108">Containerizing softwaru tímto způsobem umožňuje vývojářům a odborníkům nasadit v prostředí s žádné nebo téměř žádné změny.</span><span class="sxs-lookup"><span data-stu-id="6c0bf-108">Containerizing software this way enables developers and IT professionals to deploy them across environments with little or no modification.</span></span>

<span data-ttu-id="6c0bf-109">Kontejnery také izolace aplikace od sebe navzájem na sdílené operačního systému.</span><span class="sxs-lookup"><span data-stu-id="6c0bf-109">Containers also isolate applications from each other on a shared OS.</span></span> <span data-ttu-id="6c0bf-110">Kontejnerizované aplikace spustit na vrcholku kontejneru hostitele, který naopak běží na operačním systémem (Linux nebo Windows).</span><span class="sxs-lookup"><span data-stu-id="6c0bf-110">Containerized applications run on top of a container host that in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="6c0bf-111">Kontejnery tudíž výrazně menší nároky než bitové kopie virtuálních počítačů (VM).</span><span class="sxs-lookup"><span data-stu-id="6c0bf-111">Containers therefore have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="6c0bf-112">Každý kontejner můžete spustit celou webové aplikace nebo služby, jak je znázorněno v obrázku 2-1.</span><span class="sxs-lookup"><span data-stu-id="6c0bf-112">Each container can run a whole web application or a service, as shown in Figure 2-1.</span></span> <span data-ttu-id="6c0bf-113">V tomto příkladu je Docker hostitel hostitelem kontejneru a App1, počítači App2, Svc 1 a Svc 2 jsou kontejnerizované aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="6c0bf-113">In this example, Docker host is a container host, and App1, App2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

![](./media/image1.png)

<span data-ttu-id="6c0bf-114">**Obrázek 2-1**.</span><span class="sxs-lookup"><span data-stu-id="6c0bf-114">**Figure 2-1**.</span></span> <span data-ttu-id="6c0bf-115">Více kontejnerů, které jsou spuštěny v hostiteli kontejneru</span><span class="sxs-lookup"><span data-stu-id="6c0bf-115">Multiple containers running on a container host</span></span>

<span data-ttu-id="6c0bf-116">Další výhodou rozdělení do kontejnerů je škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="6c0bf-116">Another benefit of containerization is scalability.</span></span> <span data-ttu-id="6c0bf-117">Vytvořením nové kontejnery pro krátkodobé úlohy, můžete se rychle škálovat.</span><span class="sxs-lookup"><span data-stu-id="6c0bf-117">You can scale out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="6c0bf-118">Z aplikace hlediska vytváření instancí bitovou kopii (vytvoření kontejneru) je podobná vytváření instancí procesu, jako jsou služby nebo webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6c0bf-118">From an application point of view, instantiating an image (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="6c0bf-119">Pro spolehlivost ale při spuštění více instancí stejnou bitovou kopii na více serverů hostitele, obvykle je vhodné každé kontejneru (image instance) ke spuštění na serveru jiného hostitele nebo virtuálních počítačů v doménách jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="6c0bf-119">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="6c0bf-120">Stručně řečeno kontejnery nabízejí výhody izolace, přenositelnost, flexibility, škálovatelnost a řízení napříč celou aplikaci pracovního postupu životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="6c0bf-120">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the whole application lifecycle workflow.</span></span> <span data-ttu-id="6c0bf-121">Nejdůležitější výhodou je, izolaci mezi vývojářů a Ops k dispozici.</span><span class="sxs-lookup"><span data-stu-id="6c0bf-121">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="6c0bf-122">[Předchozí] (.. / index.md) [Další] (docker-defined.md)</span><span class="sxs-lookup"><span data-stu-id="6c0bf-122">[Previous] (../index.md) [Next] (docker-defined.md)</span></span>
