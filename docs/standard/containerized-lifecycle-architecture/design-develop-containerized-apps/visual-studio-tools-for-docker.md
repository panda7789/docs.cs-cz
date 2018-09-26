---
title: Visual Studio Tools for Docker ve Windows
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/12/2018
ms.custom: vs-dotnet
ms.openlocfilehash: cd140c12ef4a0187cce096e013937d5c98cd4b39
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47170792"
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a><span data-ttu-id="765ea-103">Pomocí sady Visual Studio Tools for Docker (Visual Studio na Windows)</span><span class="sxs-lookup"><span data-stu-id="765ea-103">Using Visual Studio Tools for Docker (Visual Studio on Windows)</span></span>

<span data-ttu-id="765ea-104">Visual Studio Tools for Docker pracovní postup pro vývojáře je podobný používání Visual Studio Code a rozhraní příkazového řádku Dockeru (je založená na stejné rozhraní příkazového řádku Dockeru).</span><span class="sxs-lookup"><span data-stu-id="765ea-104">The Visual Studio Tools for Docker developer workflow is similar to using Visual Studio Code and Docker CLI (it is based on the same Docker CLI).</span></span> <span data-ttu-id="765ea-105">Visual Studio Tools pro Docker díky ještě jednodušší, abyste mohli začít, zjednodušuje a poskytuje větší produktivitu pro sestavení, spouštět a vytvořte úkoly.</span><span class="sxs-lookup"><span data-stu-id="765ea-105">Visual Studio Tools for Docker makes it even easier to get started, simplifies the process, and provides greater productivity for the build, run, and compose tasks.</span></span> <span data-ttu-id="765ea-106">Spustit a ladit své kontejnery prostřednictvím jednoduché akce, jako je **F5** a **Ctrl**+**F5**.</span><span class="sxs-lookup"><span data-stu-id="765ea-106">Execute and debug your containers via simple actions like **F5** and **Ctrl**+**F5**.</span></span>

> [!NOTE]
> <span data-ttu-id="765ea-107">Tento článek se týká sady Visual Studio ve Windows a ne Visual Studio pro Mac.</span><span class="sxs-lookup"><span data-stu-id="765ea-107">This article applies to Visual Studio on Windows, and not Visual Studio for Mac.</span></span>

## <a name="configure-your-local-environment"></a><span data-ttu-id="765ea-108">Konfigurace vašeho místního prostředí</span><span class="sxs-lookup"><span data-stu-id="765ea-108">Configure your local environment</span></span>

<span data-ttu-id="765ea-109">S nejnovější verzí Docker pro Windows ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), nastavení jednoduché usnadňuje vývoj aplikací Dockeru.</span><span class="sxs-lookup"><span data-stu-id="765ea-109">With the latest versions of Docker for Windows ([https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)), the straightforward setup makes it easy to develop Docker applications.</span></span>

<span data-ttu-id="765ea-110">Podporu dockeru je zahrnuta v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="765ea-110">Docker support is included in Visual Studio 2017.</span></span> <span data-ttu-id="765ea-111">Stáhnete Visual Studio 2017: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span><span class="sxs-lookup"><span data-stu-id="765ea-111">Download Visual Studio 2017 here: [https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span></span>

## <a name="use-docker-tools-in-visual-studio-2017"></a><span data-ttu-id="765ea-112">Použití nástrojů Dockeru v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="765ea-112">Use Docker Tools in Visual Studio 2017</span></span>

<span data-ttu-id="765ea-113">Existují dvě úrovně podpory Dockeru, které můžete přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="765ea-113">There are two levels of Docker support you can add to a project.</span></span> <span data-ttu-id="765ea-114">V projektech webových aplikací .NET Core, lze přidat *soubor Dockerfile* soubor do projektu povolení podpory Dockeru.</span><span class="sxs-lookup"><span data-stu-id="765ea-114">In .NET Core web app projects, you can just add a *Dockerfile* file to the project by enabling Docker support.</span></span> <span data-ttu-id="765ea-115">Další úrovní je podpora orchestrátoru kontejnerů, které přidává *soubor Dockerfile* do projektu (pokud ještě neexistuje) a *docker-compose.yml* souboru na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="765ea-115">The next level is container orchestrator support, which adds a *Dockerfile* to the project (if it doesn't already exist) and a *docker-compose.yml* file at the solution level.</span></span>

<span data-ttu-id="765ea-116">**Přidat** > **podporu Dockeru** a **přidat** > **podporu Orchestrátoru kontejnerů** jsou příkazy umístěné v místní nabídce (nebo kontextovou nabídku) uzel projektu pro projekt webové aplikace v **Průzkumníka řešení**, jak ukazuje obrázek 4 – 26:</span><span class="sxs-lookup"><span data-stu-id="765ea-116">The **Add** > **Docker Support** and **Add** > **Container Orchestrator Support** commands are located on the right-click menu (or context menu) of the project node for a web app project in **Solution Explorer**, as shown in Figure 4-26:</span></span>

![Přidejte podporu Dockeru nabídky v sadě Visual Studio](media/add-docker-support-menu.png)

<span data-ttu-id="765ea-118">Obrázek 4 – 26: Přidání podpory Dockeru do projektu sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="765ea-118">Figure 4-26: Adding Docker support to a Visual Studio 2017 project</span></span>

### <a name="add-docker-support"></a><span data-ttu-id="765ea-119">Přidání podpory Dockeru</span><span class="sxs-lookup"><span data-stu-id="765ea-119">Add Docker support</span></span>

<span data-ttu-id="765ea-120">Můžete přidat podporu Dockeru do existujícího projektu webové aplikace .NET Core tak, že vyberete **přidat** > **podporu Dockeru** v **Průzkumníka řešení**.</span><span class="sxs-lookup"><span data-stu-id="765ea-120">You can add Docker support to an existing .NET Core web app project by selecting **Add** > **Docker Support** in **Solution Explorer**.</span></span> <span data-ttu-id="765ea-121">Můžete také povolit podporu Dockeru během vytváření projektu tak, že vyberete **povolit podporu Dockeru** v **nová webová aplikace ASP.NET Core** dialogové okno, které se otevře po kliknutí na **OK** v **nový projekt** dialogové okno, jak ukazuje obrázek 4 – 27.</span><span class="sxs-lookup"><span data-stu-id="765ea-121">You can also enable Docker support during project creation by selecting **Enable Docker Support** in the **New ASP.NET Core Web Application** dialog box that opens after you click **OK** in the **New Project** dialog box, as shown in Figure 4-27.</span></span>

![Povolit podporu Dockeru pro novou webovou aplikaci ASP.NET Core v sadě Visual Studio](./media/enable-docker-support-visual-studio.png)

<span data-ttu-id="765ea-123">Obrázek 4 – 27: povolte podporu Dockeru během vytváření projektu v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="765ea-123">Figure 4-27: Enable Docker support during project creation in Visual Studio 2017</span></span>

<span data-ttu-id="765ea-124">Když přidáváte nebo povolit podporu Dockeru, sada Visual Studio přidá *soubor Dockerfile* soubor do projektu.</span><span class="sxs-lookup"><span data-stu-id="765ea-124">When you add or enable Docker support, Visual Studio adds a *Dockerfile* file to the project.</span></span>

> [!NOTE]
> <span data-ttu-id="765ea-125">Když povolíte podporu Docker Compose během vytváření projektu pro projekt webové aplikace .NET Framework (nikoli projekt .NET Core webové aplikace), jak ukazuje obrázek 4 – 28, přidá se také podpora orchestrátoru kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="765ea-125">When you enable Docker Compose support during project creation for a .NET Framework web app project (not a .NET Core web app project) as shown in Figure 4-28, container orchestrator support is also added.</span></span>
>
> ![Povolit Docker compose podpory pro rozhraní .NET Framework projektu webové aplikace](media/enable-docker-compose-support.png)

> <span data-ttu-id="765ea-127">Obrázek 4 – 28: Povolení podpory Docker Compose v projektu webové aplikace .NET Framework v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="765ea-127">Figure 4-28: Enabling Docker Compose support on a .NET Framework web app project in Visual Studio 2017</span></span>

### <a name="add-container-orchestrator-support"></a><span data-ttu-id="765ea-128">Přidat podporu orchestrátoru kontejnerů</span><span class="sxs-lookup"><span data-stu-id="765ea-128">Add container orchestrator support</span></span>

<span data-ttu-id="765ea-129">Pokud chcete vytvořit vícekontejnerových řešení, přidáte podporu orchestrátoru kontejnerů do vašich projektů.</span><span class="sxs-lookup"><span data-stu-id="765ea-129">When you want to compose a multicontainer solution, add container orchestrator support to your projects.</span></span> <span data-ttu-id="765ea-130">Když chcete přidat podporu orchestrátoru kontejnerů, Visual Studio přidá *soubor Dockerfile* projektu (pokud ještě neexistuje) a globální *docker-compose.yml* souboru na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="765ea-130">When you add container orchestrator support, Visual Studio adds a *Dockerfile* to the project (if it doesn't already exist) and a global *docker-compose.yml* file at the solution level.</span></span> <span data-ttu-id="765ea-131">To vám umožní spouštět a ladit skupinu kontejnerů (celé řešení) ve stejnou dobu, pokud jsou definovány ve stejném *docker-compose.yml* souboru.</span><span class="sxs-lookup"><span data-stu-id="765ea-131">This lets you run and debug a group of containers (a whole solution) at the same time if they're defined in the same *docker-compose.yml* file.</span></span> <span data-ttu-id="765ea-132">Pokud *docker-compose.yml* již existuje, požadovaných řádků kódu, konfigurace sady Visual Studio právě přidá k němu.</span><span class="sxs-lookup"><span data-stu-id="765ea-132">If *docker-compose.yml* already exists, Visual Studio just adds the required lines of configuration code to it.</span></span>

<span data-ttu-id="765ea-133">Poté, co přidáte do projektu podporu Orchestrace kontejnerů, se zobrazí soubor Dockerfile přidat do projektu a **docker-compose** přidán do řešení ve složce **Průzkumníka řešení**, jak ukazuje obrázek 4 – 29:</span><span class="sxs-lookup"><span data-stu-id="765ea-133">After you add container orchestration support to your project, you see a Dockerfile added to the project and a **docker-compose** folder added to the solution in **Solution Explorer**, as shown in Figure 4-29:</span></span>

![Soubory docker v Průzkumníku řešení v sadě Visual Studio](media/docker-support-solution-explorer.png)

<span data-ttu-id="765ea-135">Obrázek 4 – 29: Docker soubory v Průzkumníku řešení v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="765ea-135">Figure 4-29: Docker files in Solution Explorer in Visual Studio 2017</span></span>

<span data-ttu-id="765ea-136">**Další informace:** další podrobnosti o implementaci služby a použití sady Visual Studio Tools for Docker v následujících článcích:</span><span class="sxs-lookup"><span data-stu-id="765ea-136">**More information:** For further details on the services implementation and use of Visual Studio Tools for Docker, read the following articles:</span></span>

<span data-ttu-id="765ea-137">Vytváření, ladění, aktualizovat a aktualizovat aplikace v místním kontejneru Dockeru: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="765ea-137">Build, debug, update, and refresh apps in a local Docker container: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

<span data-ttu-id="765ea-138">Nasazení kontejneru ASP.NET Core Dockeru do registru kontejneru: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="765ea-138">Deploy an ASP.NET Core Docker container to a container registry: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="765ea-139">[Předchozí](docker-apps-inner-loop-workflow.md)
[další](set-up-windows-containers-with-powershell.md)</span><span class="sxs-lookup"><span data-stu-id="765ea-139">[Previous](docker-apps-inner-loop-workflow.md)
[Next](set-up-windows-containers-with-powershell.md)</span></span>