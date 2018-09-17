---
title: Pomocí sady Visual Studio Tools for Docker (Visual Studio na Windows)
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: af14c92ab27885deec878dc33e7b94035f43e65b
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45743823"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a><span data-ttu-id="7b0d0-103">Pomocí sady Visual Studio Tools for Docker (Visual Studio na Windows)</span><span class="sxs-lookup"><span data-stu-id="7b0d0-103">Using Visual Studio Tools for Docker (Visual Studio on Windows)</span></span>

<span data-ttu-id="7b0d0-104">Pracovní postup vývoje při použití Visual Studio Tools for Docker je podobný pracovní postup při používání Visual Studio Code a rozhraní příkazového řádku Dockeru.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-104">The development workflow when using Visual Studio Tools for Docker is similar to the workflow when using Visual Studio Code and Docker CLI.</span></span> <span data-ttu-id="7b0d0-105">Ve skutečnosti je založen na stejné rozhraní příkazového řádku Dockeru, ale je snadné začít, zjednodušuje a poskytuje větší produktivitu pro sestavení, spouštět a vytvořit úkolů.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-105">In fact, it's based on the same Docker CLI, but it's easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="7b0d0-106">Je také možné spouštět a ladit své kontejnery prostřednictvím jednoduché akce, jako je F5 a Ctrl + F5 v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-106">It's also able to execute and debug your containers via simple actions like F5 and Ctrl+F5 from Visual Studio.</span></span> <span data-ttu-id="7b0d0-107">Díky podpoře Orchestrace volitelný kontejner, kromě možnosti spuštění a ladění jednoho kontejneru můžete spustit a ladit skupinu kontejnerů (celé řešení) ve stejnou dobu.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-107">With the optional container orchestration support, in addition to being able to run and debug a single container, you can run and debug a group of containers (a whole solution) at the same time.</span></span> <span data-ttu-id="7b0d0-108">Pouze definuje kontejnery ve stejném *docker-compose.yml* souboru na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-108">Just define the containers in the same *docker-compose.yml* file at the solution level.</span></span>

## <a name="configuring-your-local-environment"></a><span data-ttu-id="7b0d0-109">Konfigurace vašeho místního prostředí</span><span class="sxs-lookup"><span data-stu-id="7b0d0-109">Configuring your local environment</span></span>

<span data-ttu-id="7b0d0-110">Podporu dockeru je zahrnuta v sadě Visual Studio 2017 s žádným z nainstalovaných úlohách .NET a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-110">Docker support is included in Visual Studio 2017 with any of the .NET and .NET Core workloads installed.</span></span> <span data-ttu-id="7b0d0-111">Docker pro Windows instalovat samostatně.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-111">Install Docker for Windows separately.</span></span>

<span data-ttu-id="7b0d0-112">S nejnovější verzí Docker pro Windows je jednodušší než někdy k vývoji aplikací Dockeru vzhledem k tomu, že instalační program je jasné, jak je vysvětleno v následující odkazy.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-112">With the latest versions of Docker for Windows, it is easier than ever to develop Docker applications because the setup is straightforward, as explained in the following references.</span></span>

<span data-ttu-id="7b0d0-113">**Další informace:** Další informace o instalaci Dockeru pro Windows, přejděte na <https://docs.docker.com/docker-for-windows/>.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-113">**More info:** To learn more about installing Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>

<span data-ttu-id="7b0d0-114">**Další informace:** pokyny k instalaci sady Visual Studio, přejděte na [ https://visualstudio.microsoft.com/downloads/ ](https://visualstudio.microsoft.com/downloads/).</span><span class="sxs-lookup"><span data-stu-id="7b0d0-114">**More info:** For instructions on installing Visual Studio, go to [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/).</span></span>

<span data-ttu-id="7b0d0-115">Pokud chcete zobrazit informace o instalaci Visual Studio Tools for Docker, přejděte na <http://aka.ms/vstoolsfordocker> a <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-115">To see more about installing Visual Studio Tools for Docker, go to <http://aka.ms/vstoolsfordocker> and <https://docs.microsoft.com/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker>.</span></span>

## <a name="using-docker-tools-in-visual-studio-2017"></a><span data-ttu-id="7b0d0-116">S použitím nástrojů Docker v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7b0d0-116">Using Docker Tools in Visual Studio 2017</span></span>

<span data-ttu-id="7b0d0-117">Při přidávání podpory Docker do projektu (viz obrázek 4 – 26), sada Visual Studio přidá *soubor Dockerfile* do kořenového adresáře projektu.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-117">When adding Docker support to a project (see Figure 4-26), Visual Studio adds a *Dockerfile* to the project root.</span></span>

![Zapnutí podpory řešení Dockeru v projektu sady Visual Studio 2017](./media/image32.png)

<span data-ttu-id="7b0d0-119">Obrázek 4 – 26: zapnutí podpory řešení Dockeru v projektu sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="7b0d0-119">Figure 4-26: Turning on Docker Solution support in a Visual Studio 2017 project</span></span>

 <span data-ttu-id="7b0d0-120">Podpora Orchestrace kontejnerů pomocí Docker Compose, se přidá ve výchozím nastavení v sadě Visual Studio 2017 verze 15.7 nebo starší.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-120">Container orchestration support, via Docker Compose, is added by default in Visual Studio 2017 versions 15.7 or earlier.</span></span> <span data-ttu-id="7b0d0-121">Podpora Orchestrace kontejnerů je přihlašovaná funkce v sadě Visual Studio 2017 verze 15.8 nebo později, v takovém případě Docker Compose a Service Fabric se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-121">Container orchestration support is an opt-in feature in Visual Studio 2017 versions 15.8 or later, in which case Docker Compose and Service Fabric are supported.</span></span>

<span data-ttu-id="7b0d0-122">Pomocí sady Visual Studio verze 15,8 a novější můžete přidat podporu pro více projektů v řešení, že mají přiřazeným kontejnerem.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-122">With Visual Studio version 15.8 and later, you can add support for multiple projects in a solution that each have an associated container.</span></span> <span data-ttu-id="7b0d0-123">Klikněte pravým tlačítkem na uzel řešení nebo projektu v **Průzkumníka řešení**a zvolte **přidat** > **podpora Orchestrace kontejnerů**.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-123">Right-click on the solution or project node in **Solution Explorer**, and choose **Add** > **Container Orchestration Support**.</span></span>  <span data-ttu-id="7b0d0-124">Klikněte na tlačítko **Docker Compose** nebo **Service Fabric** Spravovat kontejnery.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-124">Then choose **Docker Compose** or **Service Fabric** to manage the containers.</span></span>

<span data-ttu-id="7b0d0-125">Pokud zvolíte **Docker Compose**, sada Visual Studio přidá oddíl služby ve vašem řešení *docker-compose.yml* soubory (nebo vytvoří soubory, pokud nebyla neexistují).</span><span class="sxs-lookup"><span data-stu-id="7b0d0-125">When you choose **Docker Compose**, Visual Studio adds a service section in your solution's *docker-compose.yml* files (or creates the files if they didn't exist).</span></span> <span data-ttu-id="7b0d0-126">Je snadný způsob, jak začít vytváření řešení více kontejnerů; pak můžete otevřít *docker-compose.yml* soubory a provede jejich aktualizaci rozšířených o další funkce.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-126">It's an easy way to begin composing your multi-container solution; you then can open the *docker-compose.yml* files and update them with additional features.</span></span>

<span data-ttu-id="7b0d0-127">Tato akce přidá požadované konfigurace řádky kódu *docker-compose.yml* nastavená na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-127">This action adds the required configuration lines of code to a *docker-compose.yml* set at the solution level.</span></span>

<span data-ttu-id="7b0d0-128">Také můžete zapnout podporu Dockeru při vytváření projektu aplikace ASP.NET Core v sadě Visual Studio 2017, jak ukazuje obrázek 4 – 27.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-128">You also can turn on Docker support when creating an ASP.NET Core project in Visual Studio 2017, as shown in Figure 4-27.</span></span>

![Zapnutí podpory Dockeru při vytváření projektu](./media/image33.png)

<span data-ttu-id="7b0d0-130">Obrázek 4 – 27: zapnutí podpory Dockeru při vytváření projektu</span><span class="sxs-lookup"><span data-stu-id="7b0d0-130">Figure 4-27: Turning on Docker support when creating a project</span></span>

<span data-ttu-id="7b0d0-131">Po přidání podpory Dockeru do svého řešení v sadě Visual Studio, také uvidíte nový uzel stromu **Průzkumníka řešení** s přidaného *docker-compose.yml* soubory, jak je znázorněno v obrázek 4 – 28.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-131">After you add Docker support to your solution in Visual Studio, you also will see a new node tree in **Solution Explorer** with the added *docker-compose.yml* files, as depicted in Figure 4-28.</span></span>

![soubory docker-compose.yml nyní zobrazit v Průzkumníku řešení](./media/image34.PNG)

<span data-ttu-id="7b0d0-133">Obrázek 4 – 28: soubory docker-compose.yml nově zobrazují v **Průzkumníka řešení**</span><span class="sxs-lookup"><span data-stu-id="7b0d0-133">Figure 4-28: docker-compose.yml files now display in **Solution Explorer**</span></span>

<span data-ttu-id="7b0d0-134">Můžete nasadit aplikace s více kontejnerů pomocí jediného *docker-compose.yml* souboru při spuštění `docker-compose up`, nicméně sady Visual Studio přidá skupinu z nich, takže mohou přepsat hodnoty v závislosti na prostředí (vývojové a produkční) a provedení příkazu zadejte (vydání a ladění).</span><span class="sxs-lookup"><span data-stu-id="7b0d0-134">You could deploy a multi-container app by using a single *docker-compose.yml* file when you run `docker-compose up`; however, Visual Studio adds a group of them, so you can override values depending on the environment (development versus production) and the execution type (release versus debug).</span></span> <span data-ttu-id="7b0d0-135">Tato funkce je lepší vysvětlení najdete v dalších kapitolách.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-135">This capability is better explained in later chapters.</span></span>

<span data-ttu-id="7b0d0-136">Service Fabric místo Docker Compose můžete také použít ke správě několika kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="7b0d0-136">You can also use Service Fabric instead of Docker Compose to manage multiple containers.</span></span> <span data-ttu-id="7b0d0-137">Zobrazit [kurz: nasazení aplikace .NET v kontejneru Windows do Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-host-app-in-a-container).</span><span class="sxs-lookup"><span data-stu-id="7b0d0-137">See [Tutorial: Deploy a .NET application in a Windows container to Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-host-app-in-a-container).</span></span>

<span data-ttu-id="7b0d0-138">**Další informace:** další podrobnosti o implementaci služby a použití sady Visual Studio Tools for Docker v následujících článcích:</span><span class="sxs-lookup"><span data-stu-id="7b0d0-138">**More info:** For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>

<span data-ttu-id="7b0d0-139">Vytváření, ladění, aktualizovat a aktualizovat aplikace v místním kontejneru Dockeru: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="7b0d0-139">Build, debug, update, and refresh apps in a local Docker container: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

<span data-ttu-id="7b0d0-140">Nasazení kontejneru ASP.NET Core Dockeru do registru kontejneru: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="7b0d0-140">Deploy an ASP.NET Core Docker container to a container registry: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="7b0d0-141">[Předchozí](docker-apps-inner-loop-workflow.md)
[další](set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="7b0d0-141">[Previous](docker-apps-inner-loop-workflow.md)
[Next](set-up-windows-containers-with-powershell.md)</span></span>
