---
title: Úvod ke kontejnerům a Dockeru
description: Získejte základní přehled o hlavní výhody použití Dockeru.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 547a76b46a319cd1b8403505ce3da618123b490e
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56218694"
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="ecca9-103">Úvod ke kontejnerům a Dockeru</span><span class="sxs-lookup"><span data-stu-id="ecca9-103">Introduction to containers and Docker</span></span>

<span data-ttu-id="ecca9-104">Kontejnerizace je přístup k vývoji softwaru, ve kterém aplikace nebo služby, jeho závislosti a jeho konfigurace (abstrahovaná jako soubory manifestu nasazení) spojených oprav jako image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ecca9-104">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="ecca9-105">Potom můžete otestovat kontejnerizovanou aplikaci jako celek a nasadit ho jako instance image kontejneru do hostitelského operačního systému.</span><span class="sxs-lookup"><span data-stu-id="ecca9-105">You then can test the containerized application as a unit and deploy it as a container image instance to the host operating system.</span></span>

<span data-ttu-id="ecca9-106">Stejně jako v oboru přesouvání standardizované kontejnery používá k přesunutí zboží příjemce, trénování nebo nákladní vůz, bez ohledu na to nákladu v nich, plnit funkci softwarové kontejnery standardní jednotkou software, který může obsahovat odlišný kód a závislosti.</span><span class="sxs-lookup"><span data-stu-id="ecca9-106">Just as the shipping industry uses standardized containers to move goods by ship, train, or truck, regardless of the cargo within them, software containers act as a standard unit of software that can contain different code and dependencies.</span></span> <span data-ttu-id="ecca9-107">Umístění softwaru do kontejnerů umožňuje vývojáři a odborníci na IT nasazování těchto kontejnerů napříč prostředími s téměř nebo vůbec žádné změny.</span><span class="sxs-lookup"><span data-stu-id="ecca9-107">Placing software into containers makes it possible for developers and IT professionals to deploy those containers across environments with little or no modification.</span></span>

<span data-ttu-id="ecca9-108">Kontejnery také izolace aplikací od sebe na sdílené operační systém (OS).</span><span class="sxs-lookup"><span data-stu-id="ecca9-108">Containers also isolate applications from one another on a shared operating system (OS).</span></span> <span data-ttu-id="ecca9-109">Kontejnerizované aplikace běží na hostiteli, který zase běží na OS (Linux nebo Windows).</span><span class="sxs-lookup"><span data-stu-id="ecca9-109">Containerized applications run on top of a container host, which in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="ecca9-110">Kontejnery tedy mít výrazně menší nároky na místo než imagí virtuálních počítačů (VM).</span><span class="sxs-lookup"><span data-stu-id="ecca9-110">Thus, containers have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="ecca9-111">Každý kontejner můžete spustit celou webovou aplikaci nebo službu, jak ukazuje obrázek 1-1.</span><span class="sxs-lookup"><span data-stu-id="ecca9-111">Each container can run an entire web application or a service, as shown in Figure 1-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="ecca9-112">Obrázek 1-1: Více kontejnerech je spuštěná na hostiteli</span><span class="sxs-lookup"><span data-stu-id="ecca9-112">Figure 1-1: Multiple containers running on a container host</span></span>

<span data-ttu-id="ecca9-113">V tomto příkladu je hostitel kontejneru hostitele Docker a aplikace 1, 2 aplikace, Svc 1 a Svc 2 jsou kontejnerizovaných aplikací nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="ecca9-113">In this example, Docker Host is a container host, and App 1, App 2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

<span data-ttu-id="ecca9-114">Další výhodou, které lze odvodit z kontejnerizace je škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="ecca9-114">Another benefit you can derive from containerization is scalability.</span></span> <span data-ttu-id="ecca9-115">Vám může horizontální navýšení kapacity rychle tak, že vytvoříte nové kontejnery pro krátkodobé úlohy.</span><span class="sxs-lookup"><span data-stu-id="ecca9-115">You can scale-out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="ecca9-116">Z aplikace hlediska *vytvoření instance bitovou kopii* (vytváření kontejneru) se podobá vytvoření instance procesu, jako je service nebo do webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="ecca9-116">From an application point of view, *instantiating an image* (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="ecca9-117">Pro spolehlivost ale při spuštění více instancí stejné image napříč více hostitelských serverů, obvykle je vhodné každý kontejner (instance image) spustit ve jiný hostitelský server nebo virtuální počítač do různých domén selhání.</span><span class="sxs-lookup"><span data-stu-id="ecca9-117">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="ecca9-118">Stručně řečeno kontejnery nabízejí výhody izolace, přenositelnost, flexibilitu, škálovatelnost a ovládací prvek v pracovním postupu životní cyklus celé aplikace.</span><span class="sxs-lookup"><span data-stu-id="ecca9-118">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the entire application life cycle workflow.</span></span> <span data-ttu-id="ecca9-119">Nejdůležitější výhoda spočívá v izolaci mezi Dev a Ops k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ecca9-119">The most important benefit is the isolation provided between Dev and Ops.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="ecca9-120">Next</span><span class="sxs-lookup"><span data-stu-id="ecca9-120">Next</span></span>](what-is-docker.md)