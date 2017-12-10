---
title: "Spouštění aplikací konzoly v Docker"
description: "Zjistěte, jak využít stávající aplikace konzoly .NET Framework a spustíte ho v kontejner Windows Docker."
author: spboyer
keywords: ".NET – aplikace typu kontejner, konzoly,"
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: 037d94452dd62c06fe6d8ac7aea1143f52b96d32
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="running-console-applications-in-windows-containers"></a><span data-ttu-id="6139c-104">Konzolové aplikace spuštěna v kontejnerech Windows</span><span class="sxs-lookup"><span data-stu-id="6139c-104">Running console applications in Windows containers</span></span>

<span data-ttu-id="6139c-105">Konzolové aplikace se používají pro mnoho účely; z jednoduchý dotaz na stav pro dlouhotrvající obrázek dokumentu zpracování úlohy.</span><span class="sxs-lookup"><span data-stu-id="6139c-105">Console applications are used for many purposes; from simple querying of a status to long running document image processing tasks.</span></span> <span data-ttu-id="6139c-106">Možnost spuštění a škálování tyto aplikace se v žádném případě splnění s omezeními akvizicích hardwaru, časy spuštění nebo spuštěním několika instancí.</span><span class="sxs-lookup"><span data-stu-id="6139c-106">In any case, the ability to start up and scale these applications are met with limitations of hardware acquisitions, startup times or running multiple instances.</span></span>

<span data-ttu-id="6139c-107">Přesunutí aplikace konzoly používat Docker a Windows Server kontejnery umožňuje od těchto aplikací do čistého stavu tím jim umožníte provádět operace a pak vypnutí ještě jednou.</span><span class="sxs-lookup"><span data-stu-id="6139c-107">Moving your console applications to use Docker and Windows Server containers allows for starting these applications from a clean state, enabling them to perform the operation and then shutdown cleanly.</span></span> <span data-ttu-id="6139c-108">Toto téma se zobrazí na základě kontejneru kroky potřebné k přesunutí konzolové aplikace pro Windows a spusťte ji pomocí skriptu prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6139c-108">This topic will show the steps needed to move a console application to a Windows based container and start it using a PowerShell script.</span></span>

<span data-ttu-id="6139c-109">Ukázkovou aplikaci konzoly je jednoduchý příklad, která přebírá argument, dotaz v tomto případě a vrací náhodné odpovědí.</span><span class="sxs-lookup"><span data-stu-id="6139c-109">The sample console application is a simple example which takes an argument, a question in this case, and returns a random answer.</span></span> <span data-ttu-id="6139c-110">To může trvat `customer_id` a zpracovat jejich daně, nebo vytvořte miniaturu `image_url` argument.</span><span class="sxs-lookup"><span data-stu-id="6139c-110">This could take a `customer_id` and process their taxes, or create a thumbnail for an `image_url` argument.</span></span>

<span data-ttu-id="6139c-111">Kromě odpověď `Environment.MachineName` byla přidána do odpovědi na tento rozdíl mezi systémem aplikace místně a v kontejneru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="6139c-111">In addition to the answer, the `Environment.MachineName` has been added to the response to show the difference between running the application locally and in a Windows container.</span></span> <span data-ttu-id="6139c-112">Při spuštění aplikace místně, má být vrácen název místního počítače a při spuštění v systému Windows kontejneru; je vrácen kontejner id relace.</span><span class="sxs-lookup"><span data-stu-id="6139c-112">When running the application locally, your local machine name should be returned and when running in a Windows Container; the container session id is returned.</span></span>

<span data-ttu-id="6139c-113">[Kompletní příklad](https://github.com/dotnet/docs/tree/master/samples/framework/docker/ConsoleRandomAnswerGenerator) je k dispozici v úložišti dotnet/docs na Githubu.</span><span class="sxs-lookup"><span data-stu-id="6139c-113">The [complete example](https://github.com/dotnet/docs/tree/master/samples/framework/docker/ConsoleRandomAnswerGenerator) is available in the dotnet/docs repository on GitHub.</span></span> <span data-ttu-id="6139c-114">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="6139c-114">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="6139c-115">Musíte se seznámit s některé Docker podmínky před zahájením práce na přesunutí aplikace do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6139c-115">You need to be familiar with some Docker terms before you begin working on moving your application to a container.</span></span>

> <span data-ttu-id="6139c-116">A *Docker image* je jen pro čtení šablonu, která definuje prostředí pro spuštěné kontejneru, včetně operační systém (OS), součástí systému a aplikacím.</span><span class="sxs-lookup"><span data-stu-id="6139c-116">A *Docker image* is a read-only template that defines the environment for a running container, including the operating system (OS), system components, and application(s).</span></span>

<span data-ttu-id="6139c-117">Důležitou součást imagí Dockeru je, že bitové kopie se skládají ze základní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="6139c-117">One important feature of Docker images is that images are composed from a base image.</span></span> <span data-ttu-id="6139c-118">Každé nové bitové kopie malých sadu funkcí, přidá do stávající image.</span><span class="sxs-lookup"><span data-stu-id="6139c-118">Each new image adds a small set of features to an existing image.</span></span> 

> <span data-ttu-id="6139c-119">A *kontejner Docker* je spuštěné instance bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="6139c-119">A *Docker container* is a running instance of an image.</span></span> 

<span data-ttu-id="6139c-120">Aplikace je škálovat tak, že spustíte stejnou bitovou kopii do mnoho kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="6139c-120">You scale an application by running the same image in many containers.</span></span>
<span data-ttu-id="6139c-121">Toto je koncepčně, podobná stejná aplikace spuštěna v několika hostitelích.</span><span class="sxs-lookup"><span data-stu-id="6139c-121">Conceptually, this is similar to running the same application in multiple hosts.</span></span>

<span data-ttu-id="6139c-122">Další informace o architektuře Docker načtením [Docker přehled](https://docs.docker.com/engine/understanding-docker/) na webu Docker.</span><span class="sxs-lookup"><span data-stu-id="6139c-122">You can learn more about the Docker architecture by reading the [Docker Overview](https://docs.docker.com/engine/understanding-docker/) on the Docker site.</span></span> 

<span data-ttu-id="6139c-123">Přesunutí aplikace konzoly se několik kroků.</span><span class="sxs-lookup"><span data-stu-id="6139c-123">Moving your console application is a matter of a few steps.</span></span>

1. [<span data-ttu-id="6139c-124">Sestavení aplikace</span><span class="sxs-lookup"><span data-stu-id="6139c-124">Build the application</span></span>](#building-the-application)
1. [<span data-ttu-id="6139c-125">Vytváření soubor Docker bitové kopie</span><span class="sxs-lookup"><span data-stu-id="6139c-125">Creating a Dockerfile for the image</span></span>](#creating-the-dockerfile)
1. [<span data-ttu-id="6139c-126">Proces sestavení a spuštění kontejner Docker</span><span class="sxs-lookup"><span data-stu-id="6139c-126">Process to build and run the Docker container</span></span>](#creating-the-image)

## <a name="prerequisites"></a><span data-ttu-id="6139c-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6139c-127">Prerequisites</span></span>
<span data-ttu-id="6139c-128">Kontejnery Windows jsou podporovány v [Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) nebo [systému Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).</span><span class="sxs-lookup"><span data-stu-id="6139c-128">Windows containers are supported on [Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) or [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).</span></span>

> [!NOTE]
><span data-ttu-id="6139c-129">Pokud používáte systém Windows Server 2016, je nutné kontejnery ručně povolit, protože instalační program Docker pro systém Windows nebude povolení této funkce.</span><span class="sxs-lookup"><span data-stu-id="6139c-129">If you are using Windows Server 2016, you must enable containers manually since the Docker for Windows installer will not enable the feature.</span></span> <span data-ttu-id="6139c-130">Zkontrolujte, že všechny aktualizace spustili pro operační systém a potom postupujte podle pokynů v tématu [nasazení hostitele kontejneru](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) článku nainstalujte kontejnery a Docker funkce.</span><span class="sxs-lookup"><span data-stu-id="6139c-130">Make sure all updates have run for the OS and then follow the instructions from the [Container Host Deployment](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) article to install the containers and Docker features.</span></span>

<span data-ttu-id="6139c-131">Je potřeba mít Docker pro systém Windows, verze 1.12 Beta 26 nebo vyšší pro podporu Windows kontejnery.</span><span class="sxs-lookup"><span data-stu-id="6139c-131">You need to have Docker for Windows, version 1.12 Beta 26 or higher to support Windows containers.</span></span> <span data-ttu-id="6139c-132">Ve výchozím nastavení povoluje Docker založenými na systému Linux kontejnery; Přepněte do Windows kontejnery kliknutím pravým tlačítkem na ikonu Docker na hlavním panelu a vyberte **přepnout do kontejnerů Windows**.</span><span class="sxs-lookup"><span data-stu-id="6139c-132">By default, Docker enables Linux based containers; switch to Windows containers by right clicking the Docker icon in the system tray and select **Switch to Windows containers**.</span></span> <span data-ttu-id="6139c-133">Docker spustí proces změny a může být nutný restart.</span><span class="sxs-lookup"><span data-stu-id="6139c-133">Docker will run the process to change and a restart may be required.</span></span>

![Windows – kontejnery](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a><span data-ttu-id="6139c-135">Vytváření aplikace</span><span class="sxs-lookup"><span data-stu-id="6139c-135">Building the application</span></span>
<span data-ttu-id="6139c-136">Obvykle jsou konzolových aplikací distribuovaných přes instalačního programu, FTP nebo sdílené složky nasazení.</span><span class="sxs-lookup"><span data-stu-id="6139c-136">Typically console applications are distributed through an installer, FTP, or File Share deployment.</span></span> <span data-ttu-id="6139c-137">Pokud nasazujete do kontejneru, prostředky nutné zkompilovat a dvoufázové instalace do umístění, které lze použít při vytváření bitové kopie Docker.</span><span class="sxs-lookup"><span data-stu-id="6139c-137">When deploying to a container, the assets need to be compiled and staged to a location that can be used when the Docker image is created.</span></span>

<span data-ttu-id="6139c-138">V *build.ps1*, tento skript využívá [MSBuild](/visualstudio/msbuild/msbuild) zkompilovat aplikace k dokončení úlohy vytváření prostředků.</span><span class="sxs-lookup"><span data-stu-id="6139c-138">In *build.ps1*, the script uses [MSBuild](/visualstudio/msbuild/msbuild) to compile the application to complete the task of building the assets.</span></span> <span data-ttu-id="6139c-139">Existuje několik parametrů předaný MSBuild finalizace potřebné prostředky.</span><span class="sxs-lookup"><span data-stu-id="6139c-139">There are a few parameters passed to MSBuild to finalize the needed assets.</span></span> <span data-ttu-id="6139c-140">Název souboru projektu nebo řešení, které mají být zkompilovány, do, umístění pro výstup a nakonec konfigurace (verze nebo verze pro ladění).</span><span class="sxs-lookup"><span data-stu-id="6139c-140">The name of the project file or solution to be compiled, the location for the output and finally the configuration (Release or Debug).</span></span>

<span data-ttu-id="6139c-141">Ve volání `Invoke-MSBuild` `OutputPath` je nastaven na **publikování** a `Configuration` nastavena na **verze**.</span><span class="sxs-lookup"><span data-stu-id="6139c-141">In the call to `Invoke-MSBuild` the `OutputPath` is set to **publish** and  `Configuration` set to **Release**.</span></span> 

```
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj /p:OutputPath=.\publish /p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a><span data-ttu-id="6139c-142">Vytváření soubor Docker</span><span class="sxs-lookup"><span data-stu-id="6139c-142">Creating the Dockerfile</span></span>
<span data-ttu-id="6139c-143">Základní image použitá pro konzolu aplikace rozhraní .NET Framework je `microsoft/windowsservercore`, veřejně dostupné v [úložiště Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/).</span><span class="sxs-lookup"><span data-stu-id="6139c-143">The base image used for a console .NET Framework application is `microsoft/windowsservercore`, publicly available on [Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/).</span></span> <span data-ttu-id="6139c-144">Bitová kopie obsahuje minimální instalaci systému Windows Server 2016, rozhraní .NET Framework 4.6.2 a slouží jako základní bitovou kopii operačního systému Windows kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="6139c-144">The base image contains a minimal installation of Windows Server 2016, .NET Framework 4.6.2 and serves as the base OS image for Windows Containers.</span></span>

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
<span data-ttu-id="6139c-145">V prvním řádku soubor Docker označí základní bitovou kopii pomocí [ `FROM` ](https://docs.docker.com/engine/reference/builder/#/from) instrukcí.</span><span class="sxs-lookup"><span data-stu-id="6139c-145">The first line in the Dockerfile designates the base image using the [`FROM`](https://docs.docker.com/engine/reference/builder/#/from) instruction.</span></span> <span data-ttu-id="6139c-146">Dále [ `ADD` ](https://docs.docker.com/engine/reference/builder/#/add) v souboru zkopíruje prostředky aplikace z **publikování** složky do kořenové složky kontejneru a poslední; nastavení [ `ENTRYPOINT` ](https://docs.docker.com/engine/reference/builder/#/entrypoint) z bitové kopie stavů že toto je příkaz nebo aplikaci, která se spustí při spuštění kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6139c-146">Next, [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) in the file copies the application assets from the **publish** folder to root folder of the container and last; setting the [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint) of the image states that this is the command or application that will run when the container starts.</span></span> 

## <a name="creating-the-image"></a><span data-ttu-id="6139c-147">Vytváření bitové kopie</span><span class="sxs-lookup"><span data-stu-id="6139c-147">Creating the image</span></span>
<span data-ttu-id="6139c-148">Chcete-li vytvořit bitovou kopii Docker, následující kód je přidán do *build.ps1* skriptu.</span><span class="sxs-lookup"><span data-stu-id="6139c-148">In order to create the Docker image, the following code is added to the *build.ps1* script.</span></span> <span data-ttu-id="6139c-149">Při spuštění skriptu `console-random-answer-generator` bitové kopie je vytvořený pomocí prostředky kompilují ze MSBuild definované v [vytváření aplikace](#building-the-application) části.</span><span class="sxs-lookup"><span data-stu-id="6139c-149">When the script is run, the `console-random-answer-generator` image is created using the assets compiled from MSBuild defined in the [Building the application](#building-the-application) section.</span></span>

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

<span data-ttu-id="6139c-150">Spuštění skriptu pomocí `.\build.ps1` z příkazového řádku prostředí PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6139c-150">Run the script using `.\build.ps1` from the PowerShell command prompt.</span></span>

<span data-ttu-id="6139c-151">Po dokončení sestavení pomocí `docker images` příkazu z příkazového řádku nebo příkazovém řádku prostředí PowerShell; uvidíte, že obrázek je vytvořená a připravená ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="6139c-151">When the build is complete, using the `docker images` command from a command line or PowerShell prompt; you'll see that the image is created and ready to be run.</span></span>

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a><span data-ttu-id="6139c-152">Spuštění kontejneru</span><span class="sxs-lookup"><span data-stu-id="6139c-152">Running the container</span></span>
<span data-ttu-id="6139c-153">Kontejner můžete spustit z příkazového řádku pomocí Docker příkazy.</span><span class="sxs-lookup"><span data-stu-id="6139c-153">You can start the container from the command line using the Docker commands.</span></span>

```
docker run console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="6139c-154">Výstup</span><span class="sxs-lookup"><span data-stu-id="6139c-154">The output is</span></span>

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

<span data-ttu-id="6139c-155">Pokud spustíte `docker ps -a` příkazu z prostředí PowerShell, uvidíte, že kontejner stále existuje.</span><span class="sxs-lookup"><span data-stu-id="6139c-155">If you run the `docker ps -a` command from PowerShell, you can see that the container still exists.</span></span>

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

<span data-ttu-id="6139c-156">Ve sloupci Stav ukazuje na "přibližně před minutou", aplikace je úplná a může být vypnuté.</span><span class="sxs-lookup"><span data-stu-id="6139c-156">The STATUS column shows at "About a minute ago", the application was complete and could be shut down.</span></span> <span data-ttu-id="6139c-157">Pokud tohoto příkazu Set časy, by sto levém statické kontejnery s žádnou činnost.</span><span class="sxs-lookup"><span data-stu-id="6139c-157">If the command was run a hundred times, there would be a hundred containers left static with no work to do.</span></span> <span data-ttu-id="6139c-158">V případě začátku ideální operace byla práci a vypnutí nebo čištění.</span><span class="sxs-lookup"><span data-stu-id="6139c-158">In the beginning scenario the ideal operation was to do the work and shutdown or cleanup.</span></span> <span data-ttu-id="6139c-159">K provedení pracovního postupu, přidání `--rm` možnost k `docker run` příkaz odebere kontejneru co nejrychleji `Exited` přijetí signál.</span><span class="sxs-lookup"><span data-stu-id="6139c-159">To accomplish that workflow, adding the `--rm` option to the `docker run` command will remove the container as soon as the `Exited` signal is received.</span></span>

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="6139c-160">Pomocí této možnosti spustíte příkaz a podívat se na výstup `docker ps -a` příkaz; Všimněte si, že id kontejneru ( `Environment.MachineName`) není v seznamu.</span><span class="sxs-lookup"><span data-stu-id="6139c-160">Running the command with this option and then looking at the output of `docker ps -a` command; notice that the container id (the `Environment.MachineName`) is not in the list.</span></span>

### <a name="running-the-container-using-powershell"></a><span data-ttu-id="6139c-161">Spuštění kontejneru pomocí prostředí PowerShell</span><span class="sxs-lookup"><span data-stu-id="6139c-161">Running the container using PowerShell</span></span>
<span data-ttu-id="6139c-162">V ukázkových souborů projektu je také *run.ps1* což je příklad toho, jak pomocí prostředí PowerShell a spusťte aplikaci přijímá argumenty.</span><span class="sxs-lookup"><span data-stu-id="6139c-162">In the sample project files there is also a *run.ps1* which is an example of how to use PowerShell to run the application accepting the arguments.</span></span>

<span data-ttu-id="6139c-163">Pokud chcete spustit, otevřete prostředí PowerShell a použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="6139c-163">To run, open PowerShell and use the following command:</span></span>

```
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a><span data-ttu-id="6139c-164">Souhrn</span><span class="sxs-lookup"><span data-stu-id="6139c-164">Summary</span></span>
<span data-ttu-id="6139c-165">Stejně tak, že přidání soubor Docker a publikování aplikace, můžete containerize vaší konzolové aplikace .NET Framework a nyní využít výhod spuštění více instancí, čisté spuštění a zastavení a další funkce systému Windows Server 2016 bez provedení žádné změny kódu aplikace vůbec.</span><span class="sxs-lookup"><span data-stu-id="6139c-165">Just by adding a Dockerfile and publishing the application, you can containerize your .NET Framework console applications and now take the advantage of running multiple instances, clean start and stop and more Windows Server 2016 capabilities without making any changes to the application code at all.</span></span>
