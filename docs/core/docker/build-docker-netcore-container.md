---
title: Kontejnerizace aplikace pomocí Docker kurz
description: V tomto kurzu se dozvíte, jak kontejnerizovat aplikace .NET Core s Dockerem.
ms.date: 03/20/2019
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: 81dbcd5e0fd15048a0fc59bfeeef64bedbfeb769
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481129"
---
# <a name="tutorial-containerize-a-net-core-app"></a><span data-ttu-id="a5e06-103">Kurz: Kontejnerizace .NET Core aplikace</span><span class="sxs-lookup"><span data-stu-id="a5e06-103">Tutorial: Containerize a .NET Core app</span></span>

<span data-ttu-id="a5e06-104">V tomto kurzu se naučíte, jak sestavit image Dockeru obsahující aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5e06-104">This tutorial teaches you how to build a Docker image that contains your .NET Core application.</span></span> <span data-ttu-id="a5e06-105">Na obrázku slouží k vytvoření kontejnerů pro vaše místní vývojové prostředí, privátního cloudu nebo veřejného cloudu.</span><span class="sxs-lookup"><span data-stu-id="a5e06-105">The image can be used to create containers for your local development environment, private cloud, or public cloud.</span></span>

<span data-ttu-id="a5e06-106">V tomto kurzu se dozvíte, jak:</span><span class="sxs-lookup"><span data-stu-id="a5e06-106">In this tutorial you will learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="a5e06-107">Vytvoření souboru Dockerfile</span><span class="sxs-lookup"><span data-stu-id="a5e06-107">Create a Dockerfile</span></span>
> * <span data-ttu-id="a5e06-108">Stáhněte si základní image Dockeru rozhraní Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="a5e06-108">Pull a Microsoft .NET Core Docker base image</span></span>
> * <span data-ttu-id="a5e06-109">Přizpůsobení a nasazení vaší aplikace do bitové kopie</span><span class="sxs-lookup"><span data-stu-id="a5e06-109">Customize and deploy your app to the image</span></span>
> * <span data-ttu-id="a5e06-110">Vytvoření a spuštění kontejneru</span><span class="sxs-lookup"><span data-stu-id="a5e06-110">Create and run a container</span></span>
> * <span data-ttu-id="a5e06-111">Nasazení do Azure</span><span class="sxs-lookup"><span data-stu-id="a5e06-111">Deploy to Azure</span></span>

<span data-ttu-id="a5e06-112">V tomto kurzu se dozvíte, jaké Docker, kontejner sestavení a nasazení úlohy pro aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5e06-112">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="a5e06-113">[Platforma Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) používá [modul Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) k rychlému sestavování a balíčky aplikací jako [imagí Dockeru](https://docs.docker.com/glossary/?term=image).</span><span class="sxs-lookup"><span data-stu-id="a5e06-113">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="a5e06-114">Tyto Image jsou napsané v [soubor Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) formátu k nasazení a spouštění [vrstvy kontejneru](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="a5e06-114">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="a5e06-115">.NET Core: Nejjednodušší způsob, jak začít</span><span class="sxs-lookup"><span data-stu-id="a5e06-115">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="a5e06-116">Před vytvořením image Dockeru, musíte aplikaci kontejnerizace.</span><span class="sxs-lookup"><span data-stu-id="a5e06-116">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="a5e06-117">Můžete jej vytvořit v Linuxu, MacOS nebo Windows.</span><span class="sxs-lookup"><span data-stu-id="a5e06-117">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="a5e06-118">Nejrychlejší a nejjednodušší způsob, jak to udělat, je použití .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5e06-118">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="a5e06-119">Pokud nejste obeznámeni s sada nástrojů .NET Core CLI, přečtěte si [.NET Core SDK přehled](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="a5e06-119">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="a5e06-120">Můžete vytvářet kontejnery Windows i Linuxu pomocí [více arch na základě značky](https://github.com/dotnet/announcements/issues/14).</span><span class="sxs-lookup"><span data-stu-id="a5e06-120">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="a5e06-121">Svou první aplikaci .NET Core Dockeru</span><span class="sxs-lookup"><span data-stu-id="a5e06-121">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="a5e06-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5e06-122">Prerequisites</span></span>

<span data-ttu-id="a5e06-123">K provedení kroků v tomto kurzu je potřeba:</span><span class="sxs-lookup"><span data-stu-id="a5e06-123">To complete this tutorial:</span></span>

#### <a name="net-core-sdk"></a><span data-ttu-id="a5e06-124">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="a5e06-124">.NET Core SDK</span></span>

* <span data-ttu-id="a5e06-125">Nainstalujte [sady SDK .NET Core 2.1](https://www.microsoft.com/net/download) nebo novější.</span><span class="sxs-lookup"><span data-stu-id="a5e06-125">Install [.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later.</span></span>

<span data-ttu-id="a5e06-126">Zobrazit [podporované verze operačního systému .NET Core 2.1](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) pro úplný seznam .NET Core 2.1 podporované operační systémy, z verze podporu operačního systému a propojení zásad životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="a5e06-126">See [.NET Core 2.1 Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md) for the complete list of .NET Core 2.1 supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="a5e06-127">Pokud jste tak dosud neučinili, nainstalujte váš oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="a5e06-127">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="a5e06-128">Je potřeba nainstalovat editor kódu?</span><span class="sxs-lookup"><span data-stu-id="a5e06-128">Need to install a code editor?</span></span> <span data-ttu-id="a5e06-129">Try [Visual Studio Code](https://code.visualstudio.com/download)!</span><span class="sxs-lookup"><span data-stu-id="a5e06-129">Try [Visual Studio Code](https://code.visualstudio.com/download)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="a5e06-130">Instalace klienta Dockeru</span><span class="sxs-lookup"><span data-stu-id="a5e06-130">Installing Docker Client</span></span>

<span data-ttu-id="a5e06-131">Nainstalujte [Docker 18.06](https://docs.docker.com/release-notes/docker-ce/) nebo novější klienta Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a5e06-131">Install [Docker 18.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="a5e06-132">Klienta Dockeru se dá nainstalovat ve:</span><span class="sxs-lookup"><span data-stu-id="a5e06-132">The Docker client can be installed in:</span></span>

* <span data-ttu-id="a5e06-133">Linuxové distribuce</span><span class="sxs-lookup"><span data-stu-id="a5e06-133">Linux distributions</span></span>

  * [<span data-ttu-id="a5e06-134">CentOS</span><span class="sxs-lookup"><span data-stu-id="a5e06-134">CentOS</span></span>](https://docs.docker.com/install/linux/docker-ce/centos/)

  * [<span data-ttu-id="a5e06-135">Debian</span><span class="sxs-lookup"><span data-stu-id="a5e06-135">Debian</span></span>](https://docs.docker.com/install/linux/docker-ce/debian/)

  * [<span data-ttu-id="a5e06-136">Fedora</span><span class="sxs-lookup"><span data-stu-id="a5e06-136">Fedora</span></span>](https://docs.docker.com/install/linux/docker-ce/fedora/)

  * [<span data-ttu-id="a5e06-137">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="a5e06-137">Ubuntu</span></span>](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [<span data-ttu-id="a5e06-138">macOS</span><span class="sxs-lookup"><span data-stu-id="a5e06-138">macOS</span></span>](https://docs.docker.com/docker-for-mac/install/)

* <span data-ttu-id="a5e06-139">[Windows](https://docs.docker.com/docker-for-windows/install/).</span><span class="sxs-lookup"><span data-stu-id="a5e06-139">[Windows](https://docs.docker.com/docker-for-windows/install/).</span></span>

### <a name="create-a-net-core-21-console-app-for-dockerization"></a><span data-ttu-id="a5e06-140">Vytvoření konzolové aplikace .NET Core 2.1 pro Dockerization</span><span class="sxs-lookup"><span data-stu-id="a5e06-140">Create a .NET Core 2.1 console app for Dockerization</span></span>

<span data-ttu-id="a5e06-141">Otevřete příkazový řádek a vytvořte složku s názvem *Hello*.</span><span class="sxs-lookup"><span data-stu-id="a5e06-141">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="a5e06-142">Přejděte do složky, kterou jste vytvořili a zadejte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="a5e06-142">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="a5e06-143">Pojďme si rychlý návod:</span><span class="sxs-lookup"><span data-stu-id="a5e06-143">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="a5e06-144">[`dotnet new`](../tools/dotnet-new.md) Vytvoří aktuální `Hello.csproj` soubor projektu se závislostmi, které jsou potřebné k sestavení aplikace konzoly.</span><span class="sxs-lookup"><span data-stu-id="a5e06-144">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="a5e06-145">Vytvoří se také `Program.cs`, základní soubor, který obsahuje vstupní bod pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a5e06-145">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>

   `Hello.csproj`<span data-ttu-id="a5e06-146">:</span><span class="sxs-lookup"><span data-stu-id="a5e06-146">:</span></span>

   <span data-ttu-id="a5e06-147">Soubor projektu určuje vše, co je potřeba k obnovení závislostí a sestavit program.</span><span class="sxs-lookup"><span data-stu-id="a5e06-147">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="a5e06-148">`OutputType` Značka Určuje, že vytváříme spustitelný soubor, jinými slovy konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5e06-148">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="a5e06-149">`TargetFramework` Značky Určuje, jaké implementace .NET jsme cílíte.</span><span class="sxs-lookup"><span data-stu-id="a5e06-149">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="a5e06-150">V pokročilém scénáři můžete zadat více cílových platforem a od sestavení k architekturami zadanými v rámci jedné operace.</span><span class="sxs-lookup"><span data-stu-id="a5e06-150">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="a5e06-151">V tomto kurzu jsme integrovali pro .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="a5e06-151">In this tutorial, we build for .NET Core 2.1.</span></span>

   `Program.cs`<span data-ttu-id="a5e06-152">:</span><span class="sxs-lookup"><span data-stu-id="a5e06-152">:</span></span>

   <span data-ttu-id="a5e06-153">Spuštění programu pomocí `using System`.</span><span class="sxs-lookup"><span data-stu-id="a5e06-153">The program starts by `using System`.</span></span> <span data-ttu-id="a5e06-154">Toto prohlášení znamená, "umožňuje přinést si všechno, co `System` oboru názvů do oboru tohoto souboru."</span><span class="sxs-lookup"><span data-stu-id="a5e06-154">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="a5e06-155">`System` Obor názvů obsahuje základní konstrukce, jako `string`, nebo číselné typy.</span><span class="sxs-lookup"><span data-stu-id="a5e06-155">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="a5e06-156">My pak definovat obor názvů s názvem `Hello`.</span><span class="sxs-lookup"><span data-stu-id="a5e06-156">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="a5e06-157">Obor názvů můžete změnit na všechno, co chcete.</span><span class="sxs-lookup"><span data-stu-id="a5e06-157">You can change namespace to anything you want.</span></span> <span data-ttu-id="a5e06-158">Třída s názvem `Program` je definována v daném oboru názvů s `Main` metodu, která přijímá pole řetězců jako svůj argument.</span><span class="sxs-lookup"><span data-stu-id="a5e06-158">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="a5e06-159">Toto pole se seznamem argumentů předaných v při volání zkompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="a5e06-159">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="a5e06-160">V našem příkladu program zapíše pouze "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="a5e06-160">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="a5e06-161">do konzoly.</span><span class="sxs-lookup"><span data-stu-id="a5e06-161">to the console.</span></span>

   <span data-ttu-id="a5e06-162">**DotNet nové** běží [ `dotnet restore` ](../tools/dotnet-restore.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="a5e06-162">**dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="a5e06-163">**DotNet restore** strom závislostí se obnoví [NuGet](https://www.nuget.org/)volání (Správce balíčků .NET).</span><span class="sxs-lookup"><span data-stu-id="a5e06-163">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="a5e06-164">NuGet provádí následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="a5e06-164">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="a5e06-165">analyzuje *Hello.csproj* souboru.</span><span class="sxs-lookup"><span data-stu-id="a5e06-165">analyzes the *Hello.csproj* file.</span></span>
   * <span data-ttu-id="a5e06-166">stáhne soubor závislosti (nebo získá z mezipaměti počítače).</span><span class="sxs-lookup"><span data-stu-id="a5e06-166">downloads the file dependencies (or grabs from your machine cache).</span></span>
   * <span data-ttu-id="a5e06-167">zapíše *obj/project.assets.json* souboru.</span><span class="sxs-lookup"><span data-stu-id="a5e06-167">writes the *obj/project.assets.json* file.</span></span>

   <span data-ttu-id="a5e06-168">*Project.assets.json* soubor je kompletní sadu grafu závislostí NuGet, řešení vazby a další metadata aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5e06-168">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="a5e06-169">To vyžaduje soubor je používán jiné nástroje, jako například [ `dotnet build` ](../tools/dotnet-build.md) a [ `dotnet run` ](../tools/dotnet-run.md), správně zpracovat zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="a5e06-169">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>

2. `$ dotnet run`

   <span data-ttu-id="a5e06-170">[`dotnet run`](../tools/dotnet-run.md) volání [ `dotnet build` ](../tools/dotnet-build.md) potvrďte úspěšné sestavení a volání `dotnet <assembly.dll>` ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5e06-170">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>

    ```console
    $ dotnet run

    Hello World!
    ```

    <span data-ttu-id="a5e06-171">Pokročilé scénáře, naleznete v tématu [nasazení aplikace .NET Core](../deploying/index.md) podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="a5e06-171">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="a5e06-172">Dockerizace aplikací .NET Core</span><span class="sxs-lookup"><span data-stu-id="a5e06-172">Dockerize the .NET Core application</span></span>

<span data-ttu-id="a5e06-173">Konzolovou aplikaci Hello .NET Core úspěšně běží místně.</span><span class="sxs-lookup"><span data-stu-id="a5e06-173">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="a5e06-174">Nyní Pojďme jít o krok dál a sestavit a spustit aplikaci v Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a5e06-174">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="a5e06-175">Vaše první soubor Dockerfile</span><span class="sxs-lookup"><span data-stu-id="a5e06-175">Your first Dockerfile</span></span>

<span data-ttu-id="a5e06-176">Otevřete textový editor a můžeme začít!</span><span class="sxs-lookup"><span data-stu-id="a5e06-176">Open your text editor and let's get started!</span></span> <span data-ttu-id="a5e06-177">Z adresáře Hello, kterou jsme vytvořili aplikaci v pořád pracujeme.</span><span class="sxs-lookup"><span data-stu-id="a5e06-177">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="a5e06-178">Přidejte následující pokyny Dockeru pro buď Linux nebo [kontejnery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/) do nového souboru.</span><span class="sxs-lookup"><span data-stu-id="a5e06-178">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="a5e06-179">Až budete hotovi, uložte ho v kořenovém adresáři Hello jako **soubor Dockerfile**, bez přípony (budete muset nastavit vašemu typu souboru `All types (*.*)` nebo něco podobného).</span><span class="sxs-lookup"><span data-stu-id="a5e06-179">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="a5e06-180">Soubor Dockerfile obsahuje pokyny pro sestavení Dockeru, které se spouští sekvenčně.</span><span class="sxs-lookup"><span data-stu-id="a5e06-180">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="a5e06-181">Musí být první instrukce [ **FROM**](https://docs.docker.com/engine/reference/builder/#from).</span><span class="sxs-lookup"><span data-stu-id="a5e06-181">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="a5e06-182">Tento pokyn inicializuje nové fázi sestavení a nastaví základní Image pro pokynů.</span><span class="sxs-lookup"><span data-stu-id="a5e06-182">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="a5e06-183">Více architektury značky kontejnery Windows nebo Linuxem v závislosti na Docker pro Windows o přijetí změn [režimu kontejneru](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span><span class="sxs-lookup"><span data-stu-id="a5e06-183">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="a5e06-184">Základní Image pro naše ukázka je 2.1 sdk image z úložiště microsoft/dotnet</span><span class="sxs-lookup"><span data-stu-id="a5e06-184">The Base Image for our sample is the 2.1-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.1-sdk
```

<span data-ttu-id="a5e06-185">[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) instrukce nastaví pracovní adresář pro všechny zbývající spuštění, CMD, ENTRYPOINT, kopírování a souboru Dockerfile přidat pokyny.</span><span class="sxs-lookup"><span data-stu-id="a5e06-185">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="a5e06-186">Pokud adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="a5e06-186">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="a5e06-187">V takovém případě WORKDIR nastavena na adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5e06-187">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="a5e06-188">[ **Kopírování** ](https://docs.docker.com/engine/reference/builder/#copy) instrukce zkopíruje nové soubory nebo adresáře z cesty zdrojových a přidá je do cílového systému souborů kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a5e06-188">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="a5e06-189">S tuto instrukci jsme kopírujete soubor projektu C# do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a5e06-189">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="a5e06-190">[ **Spustit** ](https://docs.docker.com/engine/reference/builder/#run) instrukce spustí všechny příkazy v nové vrstvě nad aktuální imagí a potvrďte výsledky.</span><span class="sxs-lookup"><span data-stu-id="a5e06-190">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="a5e06-191">Výsledná potvrzená image se používá k dalšímu kroku v souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a5e06-191">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="a5e06-192">Spouštíme **dotnet restore** získat potřebné závislosti soubor projektu C#.</span><span class="sxs-lookup"><span data-stu-id="a5e06-192">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span>

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="a5e06-193">To **kopírování** instrukce zkopíruje zbývající soubory do našich kontejneru do nové [vrstvy](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span><span class="sxs-lookup"><span data-stu-id="a5e06-193">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="a5e06-194">Publikujeme aplikaci s tímto **spustit** instrukce.</span><span class="sxs-lookup"><span data-stu-id="a5e06-194">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="a5e06-195">[ **Dotnet publikovat** ](../tools/dotnet-publish.md) příkaz zkompiluje aplikaci, přečte prostřednictvím jeho závislosti v souboru projektu zadána a publikuje výslednou sadu souborů do adresáře.</span><span class="sxs-lookup"><span data-stu-id="a5e06-195">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="a5e06-196">Naše aplikace je publikována s **vydání** konfigurace a výstup do výchozí adresář.</span><span class="sxs-lookup"><span data-stu-id="a5e06-196">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="a5e06-197">[ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint) instrukce umožňuje kontejner pro spuštění jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="a5e06-197">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="a5e06-198">Nyní je třeba soubor Dockerfile, který:</span><span class="sxs-lookup"><span data-stu-id="a5e06-198">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="a5e06-199">zkopíruje vaší aplikace do bitové kopie</span><span class="sxs-lookup"><span data-stu-id="a5e06-199">copies your app to the image</span></span>
* <span data-ttu-id="a5e06-200">závislostí vaší aplikace do bitové kopie</span><span class="sxs-lookup"><span data-stu-id="a5e06-200">your app's dependencies to the image</span></span>
* <span data-ttu-id="a5e06-201">spuštění jako spustitelný soubor aplikace sestavení</span><span class="sxs-lookup"><span data-stu-id="a5e06-201">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-app"></a><span data-ttu-id="a5e06-202">Sestavíte a spustíte aplikaci Hello .NET Core</span><span class="sxs-lookup"><span data-stu-id="a5e06-202">Build and run the Hello .NET Core app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="a5e06-203">Základní příkazy Dockeru</span><span class="sxs-lookup"><span data-stu-id="a5e06-203">Essential Docker commands</span></span>

<span data-ttu-id="a5e06-204">Jsou nezbytné tyto příkazy Dockeru:</span><span class="sxs-lookup"><span data-stu-id="a5e06-204">These Docker commands are essential:</span></span>

* [<span data-ttu-id="a5e06-205">sestavení dockeru</span><span class="sxs-lookup"><span data-stu-id="a5e06-205">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="a5e06-206">docker, spusťte</span><span class="sxs-lookup"><span data-stu-id="a5e06-206">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="a5e06-207">docker ps</span><span class="sxs-lookup"><span data-stu-id="a5e06-207">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="a5e06-208">docker stop</span><span class="sxs-lookup"><span data-stu-id="a5e06-208">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="a5e06-209">docker rm</span><span class="sxs-lookup"><span data-stu-id="a5e06-209">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="a5e06-210">rmi dockeru</span><span class="sxs-lookup"><span data-stu-id="a5e06-210">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="a5e06-211">image dockeru</span><span class="sxs-lookup"><span data-stu-id="a5e06-211">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="a5e06-212">Sestavit a spustit</span><span class="sxs-lookup"><span data-stu-id="a5e06-212">Build and run</span></span>

<span data-ttu-id="a5e06-213">Jste napsali soubor dockerfile; Docker teď sestavení vaší aplikace a pak spustí kontejner.</span><span class="sxs-lookup"><span data-stu-id="a5e06-213">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="a5e06-214">Výstup `docker build` příkaz by měl být podobný výstup konzoly následující:</span><span class="sxs-lookup"><span data-stu-id="a5e06-214">The output from the `docker build` command should be similar to the following console output:</span></span>

```console
Sending build context to Docker daemon   173.1kB
Step 1/7 : FROM microsoft/dotnet:2.1-sdk
 ---> 288f8c45f7c2
Step 2/7 : WORKDIR /app
 ---> Using cache
 ---> 9af1fbdc7972
Step 3/7 : COPY *.csproj ./
 ---> Using cache
 ---> 86c8c332d4b3
Step 4/7 : RUN dotnet restore
 ---> Using cache
 ---> 86fcd7dd0ea4
Step 5/7 : COPY . ./
 ---> Using cache
 ---> 6faf0a53607f
Step 6/7 : RUN dotnet publish -c Release -o out
 ---> Using cache
 ---> f972328318c8
Step 7/7 : ENTRYPOINT dotnet out/Hello.dll
 ---> Using cache
 ---> 53c337887e18
Successfully built 46db075bd98d
Successfully tagged dotnetapp-dev:latest
```

<span data-ttu-id="a5e06-215">Jak je vidět z výstupu modulu Docker použít soubor Dockerfile k sestavení náš kontejner.</span><span class="sxs-lookup"><span data-stu-id="a5e06-215">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="a5e06-216">Výstup `docker run` příkaz by měl být podobný výstup konzoly následující:</span><span class="sxs-lookup"><span data-stu-id="a5e06-216">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="a5e06-217">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="a5e06-217">Congratulations!</span></span> <span data-ttu-id="a5e06-218">máte jen:</span><span class="sxs-lookup"><span data-stu-id="a5e06-218">You have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="a5e06-219">Vytvoření místní aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="a5e06-219">Created a local .NET Core app</span></span>
> * <span data-ttu-id="a5e06-220">Vytvoření souboru Dockerfile k vytvoření prvního kontejneru služby</span><span class="sxs-lookup"><span data-stu-id="a5e06-220">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="a5e06-221">Vytvořené a spustili aplikaci Dockerized</span><span class="sxs-lookup"><span data-stu-id="a5e06-221">Built and ran your Dockerized app</span></span>

## <a name="next-steps"></a><span data-ttu-id="a5e06-222">Další kroky</span><span class="sxs-lookup"><span data-stu-id="a5e06-222">Next steps</span></span>

<span data-ttu-id="a5e06-223">Tady jsou některé další kroky, které si můžete:</span><span class="sxs-lookup"><span data-stu-id="a5e06-223">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="a5e06-224">Úvod do Video Image .NET Dockeru</span><span class="sxs-lookup"><span data-stu-id="a5e06-224">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="a5e06-225">Visual Studio, Docker a Azure Container Instances společně to jde líp!</span><span class="sxs-lookup"><span data-stu-id="a5e06-225">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://medium.com/@AliMazaheri/visual-studio-docker-azure-container-instances-better-together-bf8c2f0419ae)
* [<span data-ttu-id="a5e06-226">Docker for rychlí průvodci Azure</span><span class="sxs-lookup"><span data-stu-id="a5e06-226">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="a5e06-227">Nasazení vaší aplikace v Dockeru pro Azure</span><span class="sxs-lookup"><span data-stu-id="a5e06-227">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!NOTE]
> <span data-ttu-id="a5e06-228">Pokud nemáte předplatné Azure, [zaregistrujte se ještě dnes](https://azure.microsoft.com/free/?b=16.48) pro bezplatný účet 30 dní a získat 200 USD v kreditech Azure pro vyzkoušení jakékoli kombinace služeb Azure.</span><span class="sxs-lookup"><span data-stu-id="a5e06-228">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="a5e06-229">Používané v tomto příkladu Imagí dockeru</span><span class="sxs-lookup"><span data-stu-id="a5e06-229">Docker Images used in this sample</span></span>

<span data-ttu-id="a5e06-230">V této ukázce se používají následující Image Dockeru</span><span class="sxs-lookup"><span data-stu-id="a5e06-230">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.1-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="a5e06-231">Související prostředky</span><span class="sxs-lookup"><span data-stu-id="a5e06-231">Related resources</span></span>

* [<span data-ttu-id="a5e06-232">Ukázky Dockeru .NET core</span><span class="sxs-lookup"><span data-stu-id="a5e06-232">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker/tree/master/samples)
* [<span data-ttu-id="a5e06-233">Soubor Docker na kontejnery Windows</span><span class="sxs-lookup"><span data-stu-id="a5e06-233">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="a5e06-234">Ukázky Dockeru rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="a5e06-234">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="a5e06-235">ASP.NET Core na Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="a5e06-235">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="a5e06-236">Dockerizace aplikací .NET Core – kurz Dockeru</span><span class="sxs-lookup"><span data-stu-id="a5e06-236">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="a5e06-237">Práce s nástroji Dockeru pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a5e06-237">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="a5e06-238">Nasazování Imagí Dockeru ze služby Azure Container Registry do služby Azure Container Instances</span><span class="sxs-lookup"><span data-stu-id="a5e06-238">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
