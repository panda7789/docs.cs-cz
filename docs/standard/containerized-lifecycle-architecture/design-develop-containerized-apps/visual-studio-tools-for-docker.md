---
title: Pomocí nástrojů Visual Studio pro Docker (Visual Studio v systému Windows)
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: facc295399a7471edfd3e59eb1cc0e90f01ef11b
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37104889"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a><span data-ttu-id="c6e9e-103">Pomocí nástrojů Visual Studio pro Docker (Visual Studio v systému Windows)</span><span class="sxs-lookup"><span data-stu-id="c6e9e-103">Using Visual Studio Tools for Docker (Visual Studio on Windows)</span></span>

<span data-ttu-id="c6e9e-104">Při použití nástroje sady Visual Studio pro Docker je pracovní postup podobně jako při použití Visual Studio Code a příkazového řádku Dockeru vývojáře pracovního postupu (ve skutečnosti pracuje na stejné příkazového řádku Dockeru), ale je snazší začít pracovat, zjednodušuje proces a poskytuje větší produktivitu pro sestavení, spustit a vytvořit úlohy.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-104">The developer workflow when using Visual Studio Tools for Docker is similar to the workflow when using Visual Studio Code and Docker CLI (in fact, it is based on the same Docker CLI), but it is easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="c6e9e-105">Je také možné ke spouštění a ladění kontejnerů prostřednictvím jednoduchého akce, jako je F5 a Ctrl + F5 ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-105">It's also able to execute and debug your containers via simple actions like F5 and Ctrl+F5 from Visual Studio.</span></span> <span data-ttu-id="c6e9e-106">I další s Visual Studio 2017, kromě toho lze spustit a ladění jediný kontejner, můžete také spustit a ladění skupinu kontejnery (celé řešení) ve stejnou dobu, pokud jsou definovány v stejný soubor docker-compose.yml na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-106">Even more, with Visual Studio 2017, in addition to being able to run and debug a single container, you also can run and debug a group of containers (a whole solution) at the same time if they are defined in the same docker-compose.yml file at the solution level.</span></span>

## <a name="configuring-your-local-environment"></a><span data-ttu-id="c6e9e-107">Konfigurace místního prostředí</span><span class="sxs-lookup"><span data-stu-id="c6e9e-107">Configuring your local environment</span></span>

<span data-ttu-id="c6e9e-108">Nejnovější verze Docker pro systém Windows je jednodušší než někdy k vývoji aplikací Docker vzhledem k tomu, že instalační program je jasné, jak je popsáno v následující odkazy.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-108">With the latest versions of Docker for Windows, it is easier than ever to develop Docker applications because the setup is straightforward, as explained in the following references.</span></span>

<span data-ttu-id="c6e9e-109">**Další informace:** Další informace o instalaci Docker pro systém Windows, přejděte na <https://docs.docker.com/docker-for-windows/>.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-109">**More info:** To learn more about installing Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>

<span data-ttu-id="c6e9e-110">Pokud používáte Visual Studio 2015, musíte mít Update 3 nebo novější verze a sady Visual Studio Tools for Docker.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-110">If you're using Visual Studio 2015, you must have Update 3 or a later version plus the Visual Studio Tools for Docker.</span></span>

<span data-ttu-id="c6e9e-111">**Další informace:** pokyny k instalaci sady Visual Studio, přejděte na [ https://visualstudio.microsoft.com/\ produkty/vs-2015produktu edice](https://visualstudio.microsoft.com/products/vs-2015-product-editions).</span><span class="sxs-lookup"><span data-stu-id="c6e9e-111">**More info:** For instructions on installing Visual Studio, go to [https://visualstudio.microsoft.com/\ products/vs-2015-product-editions](https://visualstudio.microsoft.com/products/vs-2015-product-editions).</span></span>

<span data-ttu-id="c6e9e-112">Chcete-li zobrazit další informace o instalaci Visual Studio Tools for Docker, přejděte na <http://aka.ms/vstoolsfordocker> a <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-112">To see more about installing Visual Studio Tools for Docker, go to <http://aka.ms/vstoolsfordocker> and <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.</span></span>

<span data-ttu-id="c6e9e-113">Pokud používáte Visual Studio 2017, je už součástí sady Docker podpory.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-113">If you're using Visual Studio 2017, Docker support is already included.</span></span>

## <a name="using-docker-tools-in-visual-studio-2015"></a><span data-ttu-id="c6e9e-114">Pomocí nástroje Docker v sadě Visual Studio 2015</span><span class="sxs-lookup"><span data-stu-id="c6e9e-114">Using Docker Tools in Visual Studio 2015</span></span>

<span data-ttu-id="c6e9e-115">Visual Studio Tools for Docker zajišťuje konzistentní způsob pro vývoj a ověření místně kontejnerů Docker pro Linux v rámci Linux Docker hostitele nebo virtuálního počítače nebo kontejnerů Windows přímo v systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-115">The Visual Studio Tools for Docker provides a consistent way to develop and validate locally your Docker containers for Linux in a Linux Docker host or VM, or your Windows Containers directly on Windows.</span></span>

<span data-ttu-id="c6e9e-116">Pokud používáte jediný kontejner, je první věcí, které potřebujete k zahájení zapnout podporu Docker do projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-116">If you're using a single container, the first thing you need to begin is to turn on Docker support into your .NET Core project.</span></span> <span data-ttu-id="c6e9e-117">K tomu, klikněte pravým tlačítkem na soubor projektu, jak ukazuje obrázek 4 – 25.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-117">To do this, right-click your project file, as shown in Figure 4-25.</span></span>

![https://i1.visualstudiogallery.msdn.s-msft.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4/image/file/205468/1/add-docker-support.png](./media/image31.png)

<span data-ttu-id="c6e9e-118">Obrázek 4 – 25: zapnutí Docker podporu pro svůj projekt sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c6e9e-118">Figure 4-25: Turning on Docker support for your Visual Studio project</span></span>

## <a name="using-docker-tools-in-visual-studio-2017"></a><span data-ttu-id="c6e9e-119">Pomocí nástroje Docker v Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c6e9e-119">Using Docker Tools in Visual Studio 2017</span></span>

<span data-ttu-id="c6e9e-120">Když přidáte podporu Docker do projektu služby ve vašem řešení (viz obrázek 4-26) a Visual Studio není soubor soubor Docker jen přidat do projektu, ho také je přidání oddílu služby vaše řešení docker-compose.yml soubory (nebo vytváření souborů, pokud jejich nebyla existují).</span><span class="sxs-lookup"><span data-stu-id="c6e9e-120">When you add Docker support to a service project in your solution (see Figure 4-26), Visual Studio is not just adding a DockerFile file to your project, it also is adding a service section in your solution's docker-compose.yml files (or creating the files if they didn't exist).</span></span> <span data-ttu-id="c6e9e-121">Je snadný způsob, jak začít sestavování řešení multicontainer; pak můžete otevřít soubory docker-compose.yml a provede jejich aktualizaci s další funkce.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-121">It's an easy way to begin composing your multicontainer solution; you then can open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image32.png)

<span data-ttu-id="c6e9e-122">Obrázek 4-26: zapnutí podpory Docker řešení v projektu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="c6e9e-122">Figure 4-26: Turning on Docker Solution support in a Visual Studio 2017 project</span></span>

<span data-ttu-id="c6e9e-123">Tato akce přidá do projektu není jenom soubor Docker, přidá také požadovanou konfiguraci řádky kódu do globální docker-compose.yml nastavit na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-123">This action not only adds the DockerFile to your project, it also adds the required configuration lines of code to a global docker-compose.yml set at the solution level.</span></span>

<span data-ttu-id="c6e9e-124">Také můžete zapnout podporu Docker při vytváření projektu ASP.NET Core v Visual Studio 2017, jak ukazuje obrázek 4-27.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-124">You also can turn on Docker support when creating an ASP.NET Core project in Visual Studio 2017, as shown in Figure 4-27.</span></span>

![](./media/image33.png)

<span data-ttu-id="c6e9e-125">Obrázek 4-27: zapnutí podpory Docker při vytváření projektu</span><span class="sxs-lookup"><span data-stu-id="c6e9e-125">Figure 4-27: Turning on Docker support when creating a project</span></span>

<span data-ttu-id="c6e9e-126">Po přidání podpory Docker do řešení v sadě Visual Studio, taky uvidíte novou větev uzlu v Průzkumníku řešení se soubory přidané docker-compose.yml znázorněný v obrázek 4-28.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-126">After you add Docker support to your solution in Visual Studio, you also will see a new node tree in Solution Explorer with the added docker-compose.yml files, as depicted in Figure 4-28.</span></span>

![](./media/image34.PNG)

<span data-ttu-id="c6e9e-127">Obrázek 4-28: docker-compose.yml soubory nyní zobrazit v Průzkumníku řešení</span><span class="sxs-lookup"><span data-stu-id="c6e9e-127">Figure 4-28: docker-compose.yml files now display in Solution Explorer</span></span>

<span data-ttu-id="c6e9e-128">Můžete nasadit multicontainer aplikace pomocí jednoho docker-compose.yml souboru při spuštění docker tvoří; však sady Visual Studio přidá skupinu z nich, takže můžete přepsat hodnoty v závislosti na prostředí (vývoj a produkční) a provádění typu (vydání a ladění).</span><span class="sxs-lookup"><span data-stu-id="c6e9e-128">You could deploy a multicontainer application by using a single docker-compose.yml file when you run docker-compose up; however, Visual Studio adds a group of them, so you can override values depending on the environment (development versus production) and the execution type (release versus debug).</span></span> <span data-ttu-id="c6e9e-129">Tato funkce bude lépe popsané v dalších kapitolách.</span><span class="sxs-lookup"><span data-stu-id="c6e9e-129">This capability will be better explained in later chapters.</span></span>

<span data-ttu-id="c6e9e-130">**Další informace:** další podrobnosti o implementaci služby a použití nástroje sady Visual Studio pro Docker přečíst v následujících článcích:</span><span class="sxs-lookup"><span data-stu-id="c6e9e-130">**More info:** For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>

<span data-ttu-id="c6e9e-131">Vytvoření, ladění, aktualizace a aktualizace aplikace v místním kontejner Docker: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="c6e9e-131">Build, debug, update, and refresh apps in a local Docker container: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

<span data-ttu-id="c6e9e-132">Nasaďte kontejner ASP.NET se vzdáleným hostitelem Docker: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="c6e9e-132">Deploy an ASP.NET container to a remote Docker host: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="c6e9e-133">[Předchozí](docker-apps-inner-loop-workflow.md)
[další](set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="c6e9e-133">[Previous](docker-apps-inner-loop-workflow.md)
[Next](set-up-windows-containers-with-powershell.md)</span></span>
