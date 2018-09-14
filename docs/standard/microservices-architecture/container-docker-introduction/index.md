---
title: Úvod ke kontejnerům a Dockeru
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Úvod ke kontejnerům a Dockeru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 08/31/2018
ms.openlocfilehash: bc99bbfc3adee4cdc7008a91f42659ebcaa7a1b1
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45513335"
---
# <a name="introduction-to-containers-and-docker"></a><span data-ttu-id="2d07e-103">Úvod ke kontejnerům a Dockeru</span><span class="sxs-lookup"><span data-stu-id="2d07e-103">Introduction to Containers and Docker</span></span>

<span data-ttu-id="2d07e-104">Kontejnerizace je přístup k vývoji softwaru, ve kterém aplikace nebo služby, jeho závislosti a jeho konfigurace (abstrahovaná jako soubory manifestu nasazení) spojených oprav jako image kontejneru.</span><span class="sxs-lookup"><span data-stu-id="2d07e-104">Containerization is an approach to software development in which an application or service, its dependencies, and its configuration (abstracted as deployment manifest files) are packaged together as a container image.</span></span> <span data-ttu-id="2d07e-105">Kontejnerizovanou aplikaci jako celek otestovat a nasadit jako instance image kontejneru do hostitelského operačního systému (OS).</span><span class="sxs-lookup"><span data-stu-id="2d07e-105">The containerized application can be tested as a unit and deployed as a container image instance to the host operating system (OS).</span></span>

<span data-ttu-id="2d07e-106">Stejně jako kontejnery umožňují přepravy příjemce, trénování nebo truck bez ohledu na to nákladu uvnitř zboží, plnit funkci softwarové kontejnery standardní jednotka nasazení softwaru, který může obsahovat odlišný kód a závislosti.</span><span class="sxs-lookup"><span data-stu-id="2d07e-106">Just as shipping containers allow goods to be transported by ship, train, or truck regardless of the cargo inside, software containers act as a standard unit of software deployment that can contain different code and dependencies.</span></span> <span data-ttu-id="2d07e-107">Uzavření do kontejneru software tímto způsobem umožňuje vývojářům a IT profesionály nasazení napříč prostředími s téměř nebo vůbec žádné změny.</span><span class="sxs-lookup"><span data-stu-id="2d07e-107">Containerizing software this way enables developers and IT professionals to deploy them across environments with little or no modification.</span></span>

<span data-ttu-id="2d07e-108">Kontejnery také izolace aplikací od sebe navzájem na sdílené operačního systému.</span><span class="sxs-lookup"><span data-stu-id="2d07e-108">Containers also isolate applications from each other on a shared OS.</span></span> <span data-ttu-id="2d07e-109">Kontejnerizované aplikace běží na hostiteli, který zase běží na OS (Linux nebo Windows).</span><span class="sxs-lookup"><span data-stu-id="2d07e-109">Containerized applications run on top of a container host that in turn runs on the OS (Linux or Windows).</span></span> <span data-ttu-id="2d07e-110">Kontejnery tedy mít výrazně menší nároky na místo než imagí virtuálních počítačů (VM).</span><span class="sxs-lookup"><span data-stu-id="2d07e-110">Containers therefore have a significantly smaller footprint than virtual machine (VM) images.</span></span>

<span data-ttu-id="2d07e-111">Každý kontejner můžete spustit celou webovou aplikaci nebo službu, jak je znázorněno v obrázek 2-1.</span><span class="sxs-lookup"><span data-stu-id="2d07e-111">Each container can run a whole web application or a service, as shown in Figure 2-1.</span></span> <span data-ttu-id="2d07e-112">V tomto příkladu hostitele Docker je hostiteli a jsou App1, počítači App2, Svc 1 a Svc 2 kontejnerizovaných aplikací nebo služeb.</span><span class="sxs-lookup"><span data-stu-id="2d07e-112">In this example, Docker host is a container host, and App1, App2, Svc 1, and Svc 2 are containerized applications or services.</span></span>

![Dvě aplikace a dvě služby, které běží na operačním systému virtuálního počítače nebo fyzického serveru](./media/image1.png)

<span data-ttu-id="2d07e-114">**Obrázek 2 – 1**.</span><span class="sxs-lookup"><span data-stu-id="2d07e-114">**Figure 2-1**.</span></span> <span data-ttu-id="2d07e-115">Více kontejnerech je spuštěná na hostiteli</span><span class="sxs-lookup"><span data-stu-id="2d07e-115">Multiple containers running on a container host</span></span>

<span data-ttu-id="2d07e-116">Další výhodou kontejnerizace je škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="2d07e-116">Another benefit of containerization is scalability.</span></span> <span data-ttu-id="2d07e-117">Vytvořením nové kontejnery pro krátkodobé úlohy, můžete se rychle škálovat.</span><span class="sxs-lookup"><span data-stu-id="2d07e-117">You can scale out quickly by creating new containers for short-term tasks.</span></span> <span data-ttu-id="2d07e-118">Z aplikace hlediska vytváření instancí bitovou kopii (vytváření kontejneru) je podobné jako vytvoření instance procesu, jako je service nebo do webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="2d07e-118">From an application point of view, instantiating an image (creating a container) is similar to instantiating a process like a service or web app.</span></span> <span data-ttu-id="2d07e-119">Pro spolehlivost ale při spuštění více instancí stejné image napříč více hostitelských serverů, obvykle je vhodné každý kontejner (instance image) spustit ve jiný hostitelský server nebo virtuální počítač do různých domén selhání.</span><span class="sxs-lookup"><span data-stu-id="2d07e-119">For reliability, however, when you run multiple instances of the same image across multiple host servers, you typically want each container (image instance) to run in a different host server or VM in different fault domains.</span></span>

<span data-ttu-id="2d07e-120">Stručně řečeno kontejnery nabízejí výhody izolace, přenositelnost, flexibilitu, škálovatelnost a ovládací prvek v pracovním postupu životního cyklu celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2d07e-120">In short, containers offer the benefits of isolation, portability, agility, scalability, and control across the whole application lifecycle workflow.</span></span> <span data-ttu-id="2d07e-121">Nejdůležitější výhoda spočívá v prostředí izolace, kterou poskytuje mezi Dev a Ops.</span><span class="sxs-lookup"><span data-stu-id="2d07e-121">The most important benefit is the environment's isolation provided between Dev and Ops.</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="2d07e-122">[Předchozí](../index.md)
[další](docker-defined.md)</span><span class="sxs-lookup"><span data-stu-id="2d07e-122">[Previous](../index.md)
[Next](docker-defined.md)</span></span>
