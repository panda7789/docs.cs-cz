---
title: Úvod ke kontejnerům a Docker
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: 8d1062aaea85cf810fa07b36252974eceb227c43
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="1cc0a-103">Úvod ke kontejnerům a Docker</span><span class="sxs-lookup"><span data-stu-id="1cc0a-103">Introduction to containers and Docker</span></span>

<span data-ttu-id="1cc0a-104">Rozdělení do kontejnerů je přístup k vývoji softwaru, ve kterém aplikace nebo služby, jeho závislosti a jeho konfigurace (abstrahované jako soubory manifestu nasazení) a instalace balíčku jako obrázek na kontejneru.</span><span class="sxs-lookup"><span data-stu-id="1cc0a-104">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="1cc0a-105">Potom můžete otestovat kontejnerizované aplikaci jako celek a nasaďte ho jako instanci kontejneru bitové kopie pro hostitelský operační systém.</span><span class="sxs-lookup"><span data-stu-id="1cc0a-105">You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system.</span></span>

<span data-ttu-id="1cc0a-106">Stejně jako v odvětví přesouvání používá standardizované kontejnery přesunout zboží lodě, train nebo vůz, bez ohledu na to nákladní v nich, kontejnery softwaru fungují jako jednotka se software, který může obsahovat různé kódu a závislosti.</span><span class="sxs-lookup"><span data-stu-id="1cc0a-106">Just as the shipping industry uses standardized containers to move goods by ship, train, or truck, regardless of the cargo within them, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="1cc0a-107">Umístění softwaru do kontejnerů umožňuje pro vývojáře a IT odborníky nasazení těchto kontejnerů v rámci prostředí s žádné nebo téměř žádné změny.</span><span class="sxs-lookup"><span data-stu-id="1cc0a-107">Placing software into containers makes it possible for developers and IT professionals to deploy those containers across environments with little or no modification.</span></span>

<span data-ttu-id="1cc0a-108">Kontejnery také izolace aplikace od sebe navzájem na sdílené operační systém (OS).</span><span class="sxs-lookup"><span data-stu-id="1cc0a-108">Containers also isolate applications from one another on a shared operating system (OS).</span></span> <span data-ttu-id="1cc0a-109">Kontejnerizované aplikace spustit na vrcholku kontejneru hostitele, který naopak běží na operačním systémem (Linux nebo Windows).</span><span class="sxs-lookup"><span data-stu-id="1cc0a-109">Containerized applications run on top of a container host, which in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="1cc0a-110">Kontejnery tedy mít výrazně menší nároky než bitové kopie virtuálních počítačů (VM).</span><span class="sxs-lookup"><span data-stu-id="1cc0a-110">Thus, containers have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="1cc0a-111">Každý kontejner můžete spustit celou webovou aplikaci nebo službu, jak ukazuje obrázek 1-1.</span><span class="sxs-lookup"><span data-stu-id="1cc0a-111">Each container can run an entire web application or a service, as shown in Figure 1-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="1cc0a-112">Obrázek 1-1: několika kontejnerů spuštěny v hostiteli kontejneru</span><span class="sxs-lookup"><span data-stu-id="1cc0a-112">Figure 1-1: Multiple containers running on a container host</span></span>

<span data-ttu-id="1cc0a-113">V tomto příkladu je Docker hostitel hostitelem kontejneru a aplikace 1, 2 aplikace, Svc 1 a Svc 2 jsou kontejnerizované aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="1cc0a-113">In this example, Docker Host is a container host, and App 1, App 2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

<span data-ttu-id="1cc0a-114">Mezi další výhody, které může být odvozen z rozdělení do kontejnerů je škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="1cc0a-114">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="1cc0a-115">Vám může Škálováním na více systémů rychle vytvořit nové kontejnery pro krátkodobé úlohy.</span><span class="sxs-lookup"><span data-stu-id="1cc0a-115">You can scale-out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="1cc0a-116">Z aplikace hlediska *vytváření instancí bitovou kopii* (vytvoření kontejneru) je podobná vytváření instancí procesu, jako jsou služby nebo webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1cc0a-116">From an application point of view, *instantiating an image* (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="1cc0a-117">Pro spolehlivost ale při spuštění více instancí stejnou bitovou kopii na více serverů hostitele, obvykle je vhodné každé kontejneru (image instance) ke spuštění na serveru jiného hostitele nebo virtuálních počítačů v doménách jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="1cc0a-117">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="1cc0a-118">Stručně řečeno kontejnery nabízejí výhody izolace, přenositelnost, flexibility, škálovatelnost a řízení napříč pracovního postupu životní cyklus celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1cc0a-118">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application life cycle workflow.</span></span> <span data-ttu-id="1cc0a-119">Nejdůležitější výhodou je, izolaci mezi vývojářů a Ops k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1cc0a-119">The most important benefit is the isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="1cc0a-120">[Další] (what-is-docker.md)</span><span class="sxs-lookup"><span data-stu-id="1cc0a-120">[Next] (what-is-docker.md)</span></span>
