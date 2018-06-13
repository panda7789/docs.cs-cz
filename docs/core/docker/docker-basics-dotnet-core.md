---
title: Další základní informace o Docker s .NET Core
description: Základní kurz .NET Core a Docker
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: 02b6b3fc9e149f5d1d5d78e310c7df257be983c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218541"
---
# <a name="learn-docker-basics-with-net-core"></a><span data-ttu-id="9c595-103">Další základní informace o Docker s .NET Core</span><span class="sxs-lookup"><span data-stu-id="9c595-103">Learn Docker Basics with .NET Core</span></span>

<span data-ttu-id="9c595-104">V tomto kurzu se dozvíte, jaké Docker kontejneru sestavení a nasazení úlohy pro aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c595-104">This tutorial teaches the Docker container build and deploy tasks for a .NET Core application.</span></span> <span data-ttu-id="9c595-105">V průběhu tohoto kurzu se seznámíte:</span><span class="sxs-lookup"><span data-stu-id="9c595-105">During the course of this tutorial, you learn:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="9c595-106">Jak vytvořit soubor Docker</span><span class="sxs-lookup"><span data-stu-id="9c595-106">How to create a Dockerfile</span></span>
> * <span data-ttu-id="9c595-107">Jak vytvořit aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c595-107">How to create a .NET Core app.</span></span>
> * <span data-ttu-id="9c595-108">Postup nasazení aplikace do kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="9c595-108">How to deploy your app into a Docker container.</span></span>

<span data-ttu-id="9c595-109">[Docker platformy](https://docs.docker.com/engine/docker-overview/#the-docker-platform) používá [modulu Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) rychle vytvářet a balíček aplikace jako [imagí Dockeru](https://docs.docker.com/glossary/?term=image).</span><span class="sxs-lookup"><span data-stu-id="9c595-109">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image).</span></span> <span data-ttu-id="9c595-110">Tyto Image jsou zapsány v [soubor Docker](https://docs.docker.com/glossary/?term=Dockerfile) formát, který se nasadit a spustit [vrstvený kontejneru](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="9c595-110">These images are written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format to be deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

## <a name="net-core-easiest-way-to-get-started"></a><span data-ttu-id="9c595-111">.NET core: Nejjednodušším způsobem Začínáme</span><span class="sxs-lookup"><span data-stu-id="9c595-111">.NET Core: Easiest way to get started</span></span>

<span data-ttu-id="9c595-112">Před vytvořením bitové kopie Docker, musíte aplikaci containerize.</span><span class="sxs-lookup"><span data-stu-id="9c595-112">Before creating the Docker image, you need an application to containerize.</span></span> <span data-ttu-id="9c595-113">Můžete ho vytvořit v systému Linux, systému MacOS nebo systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9c595-113">You can create it on Linux, MacOS, or Windows.</span></span> <span data-ttu-id="9c595-114">Nejrychlejší a nejjednodušší způsob, jak to udělat, je použití .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9c595-114">The quickest and easiest way to do that is to use .NET Core.</span></span>

<span data-ttu-id="9c595-115">Pokud jste obeznámeni s .NET Core rozhraní příkazového řádku sady nástrojů, přečtěte si [.NET Core SDK přehled](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="9c595-115">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

<span data-ttu-id="9c595-116">Můžete vytvořit kontejnery Windows a Linux s [architektura více na základě značek](https://github.com/dotnet/announcements/issues/14).</span><span class="sxs-lookup"><span data-stu-id="9c595-116">You can build both Windows and Linux containers with [multi-arch based tags](https://github.com/dotnet/announcements/issues/14).</span></span>

## <a name="your-first-net-core-docker-app"></a><span data-ttu-id="9c595-117">První aplikace .NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="9c595-117">Your first .NET Core Docker app</span></span>

### <a name="prerequisites"></a><span data-ttu-id="9c595-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9c595-118">Prerequisites</span></span>

<span data-ttu-id="9c595-119">K dokončení tohoto kurzu:</span><span class="sxs-lookup"><span data-stu-id="9c595-119">To complete this tutorial:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="9c595-120">Základní rozhraní .NET 2.0 SDK</span><span class="sxs-lookup"><span data-stu-id="9c595-120">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="9c595-121">Nainstalujte [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="9c595-121">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

<span data-ttu-id="9c595-122">V tématu [2.x .NET Core, podporované verze operačního systému](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) pro úplný seznam .NET Core 2.x podporované operační systémy, mimo verze podporu operačního systému a odkazy na zásady životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="9c595-122">See [.NET Core 2.x Supported OS Versions](https://github.com/dotnet/core/blob/master/release-notes/2.0/2.0-supported-os.md) for the complete list of .NET Core 2.x supported operating systems, out of support OS versions, and lifecycle policy links.</span></span>

* <span data-ttu-id="9c595-123">Pokud jste to ještě neudělali, nainstalujte editor vaše oblíbené kódu.</span><span class="sxs-lookup"><span data-stu-id="9c595-123">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="9c595-124">Je potřeba nainstalovat editor kódu?</span><span class="sxs-lookup"><span data-stu-id="9c595-124">Need to install a code editor?</span></span> <span data-ttu-id="9c595-125">Zkuste [sady Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="9c595-125">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="9c595-126">Instalace klienta Docker</span><span class="sxs-lookup"><span data-stu-id="9c595-126">Installing Docker Client</span></span>

<span data-ttu-id="9c595-127">Nainstalujte [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) nebo novější Docker klienta.</span><span class="sxs-lookup"><span data-stu-id="9c595-127">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="9c595-128">Klient Docker může být nainstalován v:</span><span class="sxs-lookup"><span data-stu-id="9c595-128">The Docker client can be installed in:</span></span>

* <span data-ttu-id="9c595-129">Distribuce systému Linux</span><span class="sxs-lookup"><span data-stu-id="9c595-129">Linux distributions</span></span>

   * [<span data-ttu-id="9c595-130">CentOS</span><span class="sxs-lookup"><span data-stu-id="9c595-130">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="9c595-131">Debian</span><span class="sxs-lookup"><span data-stu-id="9c595-131">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="9c595-132">Fedora</span><span class="sxs-lookup"><span data-stu-id="9c595-132">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="9c595-133">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="9c595-133">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="9c595-134">macOS</span><span class="sxs-lookup"><span data-stu-id="9c595-134">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="9c595-135">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="9c595-135">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

### <a name="create-a-net-core-20-console-app-for-dockerization"></a><span data-ttu-id="9c595-136">Vytvoření aplikace konzoly .NET Core 2.0 pro Dockerization</span><span class="sxs-lookup"><span data-stu-id="9c595-136">Create a .NET Core 2.0 console app for Dockerization</span></span>

<span data-ttu-id="9c595-137">Otevřete příkazový řádek a vytvořte složku s názvem *Hello*.</span><span class="sxs-lookup"><span data-stu-id="9c595-137">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="9c595-138">Přejděte do složky, kterou jste vytvořili a zadejte následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="9c595-138">Navigate to the folder you created and type the following commands:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="9c595-139">Umožňuje provést rychlé názorný postup:</span><span class="sxs-lookup"><span data-stu-id="9c595-139">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="9c595-140">[`dotnet new`](../tools/dotnet-new.md) Vytvoří aktuální `Hello.csproj` souboru projektu se závislostmi, které jsou potřebné k vytvoření konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c595-140">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="9c595-141">Vytvoří také `Program.cs`, základní souboru, který obsahuje vstupní bod pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9c595-141">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="9c595-142">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="9c595-142">`Hello.csproj`:</span></span>

   <span data-ttu-id="9c595-143">Soubor projektu určuje vše, co je potřeba k obnovení závislosti a sestavte program.</span><span class="sxs-lookup"><span data-stu-id="9c595-143">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="9c595-144">`OutputType` Značky Určuje, že vytváříme spustitelný soubor, jinými slovy konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c595-144">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="9c595-145">`TargetFramework` Značky Určuje, jaké implementace rozhraní .NET jsme se cílení na.</span><span class="sxs-lookup"><span data-stu-id="9c595-145">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="9c595-146">V pokročilém scénáři můžete zadat několik cílové architektury a sestavení k zadané architektury v rámci jedné operace.</span><span class="sxs-lookup"><span data-stu-id="9c595-146">In an advanced scenario, you can specify multiple target frameworks and build to the specified frameworks in a single operation.</span></span> <span data-ttu-id="9c595-147">V tomto kurzu jsme sestavení pro rozhraní .NET 2.0 jádra.</span><span class="sxs-lookup"><span data-stu-id="9c595-147">In this tutorial, we build for .NET Core 2.0.</span></span>

   <span data-ttu-id="9c595-148">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="9c595-148">`Program.cs`:</span></span>

   <span data-ttu-id="9c595-149">Program se spustí `using System`.</span><span class="sxs-lookup"><span data-stu-id="9c595-149">The program starts by `using System`.</span></span> <span data-ttu-id="9c595-150">Toto prohlášení znamená, "předány všechno, co `System` oboru názvů do oboru pro tento soubor."</span><span class="sxs-lookup"><span data-stu-id="9c595-150">This statement means, "Bring everything in the `System` namespace into scope for this file."</span></span> <span data-ttu-id="9c595-151">`System` Obor názvů obsahuje základní konstrukce, jako `string`, nebo číselnými typy.</span><span class="sxs-lookup"><span data-stu-id="9c595-151">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="9c595-152">Potom jsme definovali obor názvů s názvem `Hello`.</span><span class="sxs-lookup"><span data-stu-id="9c595-152">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="9c595-153">Obor názvů, můžete změnit na nic, co chcete.</span><span class="sxs-lookup"><span data-stu-id="9c595-153">You can change namespace to anything you want.</span></span> <span data-ttu-id="9c595-154">Třída s názvem `Program` je definována v daném oboru názvů pomocí `Main` metody, která přijímá pole řetězců jako její argument.</span><span class="sxs-lookup"><span data-stu-id="9c595-154">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="9c595-155">Toto pole obsahuje seznam argumentů předaná při volání zkompilovaný program.</span><span class="sxs-lookup"><span data-stu-id="9c595-155">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="9c595-156">V našem příkladu program pouze zapíše "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="9c595-156">In our example, the program only writes "Hello World!"</span></span> <span data-ttu-id="9c595-157">ke konzole.</span><span class="sxs-lookup"><span data-stu-id="9c595-157">to the console.</span></span>

2. `$ dotnet restore`

   <span data-ttu-id="9c595-158">V .NET Core 2.x, **dotnet nové** běží [ `dotnet restore` ](../tools/dotnet-restore.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="9c595-158">In .NET Core 2.x, **dotnet new** runs the [`dotnet restore`](../tools/dotnet-restore.md) command.</span></span> <span data-ttu-id="9c595-159">**Obnovení DotNet** obnoví stromu závislosti s [NuGet](https://www.nuget.org/)volání (Správce balíčků .NET).</span><span class="sxs-lookup"><span data-stu-id="9c595-159">**Dotnet restore** restores the tree of dependencies with a [NuGet](https://www.nuget.org/)(.NET package manager) call.</span></span>
   <span data-ttu-id="9c595-160">NuGet provede následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="9c595-160">NuGet performs the following tasks:</span></span>
   * <span data-ttu-id="9c595-161">analyzuje *Hello.csproj* souboru</span><span class="sxs-lookup"><span data-stu-id="9c595-161">analyzes the *Hello.csproj* file</span></span> 
   * <span data-ttu-id="9c595-162">Načtení souboru závislosti (nebo získá z vašeho počítače mezipaměti)</span><span class="sxs-lookup"><span data-stu-id="9c595-162">downloads the file dependencies (or grabs from your machine cache)</span></span>
   * <span data-ttu-id="9c595-163">zapíše *obj/project.assets.json* souboru</span><span class="sxs-lookup"><span data-stu-id="9c595-163">writes the *obj/project.assets.json* file</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
   
   <span data-ttu-id="9c595-164">*Project.assets.json* soubor je kompletní sada grafu závislostí NuGet, řešení vazby a další metadata aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c595-164">The *project.assets.json* file is a complete set of the NuGet dependencies graph, binding resolutions, and other app metadata.</span></span> <span data-ttu-id="9c595-165">To vyžadováno, soubor je používán jiných nástrojů, jako například [ `dotnet build` ](../tools/dotnet-build.md) a [ `dotnet run` ](../tools/dotnet-run.md), správně zpracovat zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="9c595-165">This required file is used by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), to correctly process the source code.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="9c595-166">[`dotnet run`](../tools/dotnet-run.md) volání [ `dotnet build` ](../tools/dotnet-build.md) potvrďte úspěšném sestavení a poté zavolá `dotnet <assembly.dll>` ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c595-166">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to confirm a successful build, and then calls `dotnet <assembly.dll>` to run the application.</span></span>
   
    ```console
    $ dotnet run
    
    Hello World!
    ```

    <span data-ttu-id="9c595-167">Složitější scénáře, najdete v části [nasazení aplikace .NET Core](../deploying/index.md) podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="9c595-167">For advanced scenarios,  see [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

## <a name="dockerize-the-net-core-application"></a><span data-ttu-id="9c595-168">Dockerize aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="9c595-168">Dockerize the .NET Core application</span></span>

<span data-ttu-id="9c595-169">Konzolové aplikace Hello .NET Core úspěšně běží místně.</span><span class="sxs-lookup"><span data-stu-id="9c595-169">The Hello .NET Core console app successfully runs locally.</span></span> <span data-ttu-id="9c595-170">Teď umožňuje provádět ho další krok a sestavení a spuštění aplikace v nástroji Docker.</span><span class="sxs-lookup"><span data-stu-id="9c595-170">Now let's take it a step further and build and run the app in Docker.</span></span>

### <a name="your-first-dockerfile"></a><span data-ttu-id="9c595-171">Vaše první soubor Docker</span><span class="sxs-lookup"><span data-stu-id="9c595-171">Your first Dockerfile</span></span>

<span data-ttu-id="9c595-172">Otevřete textový editor a můžeme začít!</span><span class="sxs-lookup"><span data-stu-id="9c595-172">Open your text editor and let's get started!</span></span> <span data-ttu-id="9c595-173">Z Hello adresáře, které jsme vytvořili aplikaci v stále pracujeme.</span><span class="sxs-lookup"><span data-stu-id="9c595-173">We're still working from the Hello directory we built the app in.</span></span>

<span data-ttu-id="9c595-174">Přidejte následující pokyny Docker buď Linux nebo [Windows kontejnery](https://docs.microsoft.com/virtualization/windowscontainers/about/) do nového souboru.</span><span class="sxs-lookup"><span data-stu-id="9c595-174">Add the following Docker instructions for either Linux or [Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/) to a new file.</span></span> <span data-ttu-id="9c595-175">Po dokončení uložte jej v kořenovém adresáři Hello jako **soubor Docker**, bez přípony (budete muset nastavit vašeho typu souboru `All types (*.*)` nebo něco podobné).</span><span class="sxs-lookup"><span data-stu-id="9c595-175">When finished, save it in the root of your Hello directory as **Dockerfile**, with no extension (You may need to set your file type to `All types (*.*)` or something similar).</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
WORKDIR /app

# copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# copy and build everything else
COPY . ./
RUN dotnet publish -c Release -o out
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="9c595-176">Soubor Docker obsahuje pokyny Docker sestavení, které spouští sekvenčně.</span><span class="sxs-lookup"><span data-stu-id="9c595-176">The Dockerfile contains Docker build instructions that run sequentially.</span></span>

<span data-ttu-id="9c595-177">Musí být první pokyn [ **FROM**](https://docs.docker.com/engine/reference/builder/#from).</span><span class="sxs-lookup"><span data-stu-id="9c595-177">The first instruction must be [**FROM**](https://docs.docker.com/engine/reference/builder/#from).</span></span> <span data-ttu-id="9c595-178">Tento pokyn inicializuje nové fáze sestavení a nastaví pro základní bitovou kopii podle zbývajících pokynů.</span><span class="sxs-lookup"><span data-stu-id="9c595-178">This instruction initializes a new build stage and sets the Base Image for the remaining instructions.</span></span> <span data-ttu-id="9c595-179">Více architektury značky pro vyžádání obsahu systému Windows nebo Linux kontejnery v závislosti na Docker pro systém Windows [režim kontejneru](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span><span class="sxs-lookup"><span data-stu-id="9c595-179">The multi-arch tags pull either Windows or Linux containers depending on the Docker for Windows [container mode](https://docs.docker.com/docker-for-windows/#switch-between-windows-and-linux-containers).</span></span> <span data-ttu-id="9c595-180">Pro základní bitovou kopii naše ukázka je 2.0 sdk image z úložiště microsoft/dotnet.</span><span class="sxs-lookup"><span data-stu-id="9c595-180">The Base Image for our sample is the 2.0-sdk image from the microsoft/dotnet repository,</span></span>

```Dockerfile
FROM microsoft/dotnet:2.0-sdk
```

<span data-ttu-id="9c595-181">[ **WORKDIR** ](https://docs.docker.com/engine/reference/builder/#workdir) instrukce nastaví pracovní adresář pro všechny zbývající spustit, CMD, vstupní bod, kopírování a přidat soubor Docker pokyny.</span><span class="sxs-lookup"><span data-stu-id="9c595-181">The [**WORKDIR**](https://docs.docker.com/engine/reference/builder/#workdir) instruction sets the working directory for any remaining RUN, CMD, ENTRYPOINT, COPY, and ADD Dockerfile instructions.</span></span> <span data-ttu-id="9c595-182">Pokud adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="9c595-182">If the directory doesn't exist, it's created.</span></span> <span data-ttu-id="9c595-183">V takovém případě WORKDIR nastavena na adresář aplikace.</span><span class="sxs-lookup"><span data-stu-id="9c595-183">In this case, WORKDIR is set to the app directory.</span></span>

```Dockerfile
WORKDIR /app
```

<span data-ttu-id="9c595-184">[ **Kopie** ](https://docs.docker.com/engine/reference/builder/#copy) instrukce zkopíruje nových souborů nebo adresářů z cesty zdrojových a přidá je do systému cílový kontejner souborů.</span><span class="sxs-lookup"><span data-stu-id="9c595-184">The [**COPY**](https://docs.docker.com/engine/reference/builder/#copy) instruction copies new files or directories from the source path and adds them to the destination container filesystem.</span></span> <span data-ttu-id="9c595-185">S Tento pokyn jsme se kopírování souboru projektu C# do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="9c595-185">With this instruction, we are copying the C# project file to the container.</span></span>

```Dockerfile
COPY *.csproj ./
```

<span data-ttu-id="9c595-186">[ **Spustit** ](https://docs.docker.com/engine/reference/builder/#run) instrukce spustí všechny příkazy v novou vrstvu nad aktuální image a potvrďte výsledky.</span><span class="sxs-lookup"><span data-stu-id="9c595-186">The [**RUN**](https://docs.docker.com/engine/reference/builder/#run) instruction executes any commands in a new layer on top of the current image and commit the results.</span></span> <span data-ttu-id="9c595-187">Výsledný potvrdit bitovou kopii se používá pro další krok v soubor Docker.</span><span class="sxs-lookup"><span data-stu-id="9c595-187">The resulting committed image is used for the next step in the Dockerfile.</span></span> <span data-ttu-id="9c595-188">Používáme **dotnet obnovení** získat potřebné závislosti souboru projektu C#.</span><span class="sxs-lookup"><span data-stu-id="9c595-188">We are running **dotnet restore** to get the needed dependencies of the C# project file.</span></span> 

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="9c595-189">To **kopie** instrukce zkopíruje zbytek soubory do našich kontejneru do nové [vrstvy](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span><span class="sxs-lookup"><span data-stu-id="9c595-189">This **COPY** instruction copies the rest of the files into our container into new [layers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers).</span></span>

```Dockerfile
COPY . ./
```

<span data-ttu-id="9c595-190">Jsme publikují aplikace s tímto **spustit** instrukcí.</span><span class="sxs-lookup"><span data-stu-id="9c595-190">We are publishing the app with this **RUN** instruction.</span></span> <span data-ttu-id="9c595-191">[ **Dotnet publikování** ](../tools/dotnet-publish.md) příkaz kompilaci aplikace, čte prostřednictvím jeho závislé součásti, zadaný v souboru projektu a publikuje výslednou sadu soubory do adresáře.</span><span class="sxs-lookup"><span data-stu-id="9c595-191">The [**dotnet publish**](../tools/dotnet-publish.md) command compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="9c595-192">Naše aplikace je publikována s **verze** konfigurace a výstup do výchozí adresář.</span><span class="sxs-lookup"><span data-stu-id="9c595-192">Our app is published with a **Release** configuration and output to the default directory.</span></span>

```Dockerfile
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="9c595-193">[ **ENTRYPOINT** ](https://docs.docker.com/engine/reference/builder/#entrypoint) instrukce umožňuje kontejneru spustit jako spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="9c595-193">The [**ENTRYPOINT**](https://docs.docker.com/engine/reference/builder/#entrypoint) instruction allows the container to run as an executable.</span></span>

```Dockerfile
ENTRYPOINT ["dotnet", "out/Hello.dll"]
```

<span data-ttu-id="9c595-194">Nyní máte soubor Docker který:</span><span class="sxs-lookup"><span data-stu-id="9c595-194">Now you have a Dockerfile that:</span></span>

* <span data-ttu-id="9c595-195">zkopíruje vaší aplikace do bitové kopie</span><span class="sxs-lookup"><span data-stu-id="9c595-195">copies your app to the image</span></span>
* <span data-ttu-id="9c595-196">závislosti vaší aplikace do bitové kopie</span><span class="sxs-lookup"><span data-stu-id="9c595-196">your app's dependencies to the image</span></span>
* <span data-ttu-id="9c595-197">sestavení v aplikaci spustit jako spustitelný soubor</span><span class="sxs-lookup"><span data-stu-id="9c595-197">builds the app to run as an executable</span></span>

### <a name="build-and-run-the-hello-net-core-20-app"></a><span data-ttu-id="9c595-198">Sestavení a spuštění aplikace Hello .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="9c595-198">Build and run the Hello .NET Core 2.0 app</span></span>

#### <a name="essential-docker-commands"></a><span data-ttu-id="9c595-199">Základní příkazy Docker</span><span class="sxs-lookup"><span data-stu-id="9c595-199">Essential Docker commands</span></span>

<span data-ttu-id="9c595-200">Tyto příkazy Docker je nezbytné:</span><span class="sxs-lookup"><span data-stu-id="9c595-200">These Docker commands are essential:</span></span>

* [<span data-ttu-id="9c595-201">docker sestavení</span><span class="sxs-lookup"><span data-stu-id="9c595-201">docker build</span></span>](https://docs.docker.com/engine/reference/commandline/build/)
* [<span data-ttu-id="9c595-202">Spustit docker</span><span class="sxs-lookup"><span data-stu-id="9c595-202">docker run</span></span>](https://docs.docker.com/engine/reference/commandline/run/)
* [<span data-ttu-id="9c595-203">docker ps</span><span class="sxs-lookup"><span data-stu-id="9c595-203">docker ps</span></span>](https://docs.docker.com/engine/reference/commandline/ps/)
* [<span data-ttu-id="9c595-204">zastavení docker</span><span class="sxs-lookup"><span data-stu-id="9c595-204">docker stop</span></span>](https://docs.docker.com/engine/reference/commandline/stop/)
* [<span data-ttu-id="9c595-205">docker rm</span><span class="sxs-lookup"><span data-stu-id="9c595-205">docker rm</span></span>](https://docs.docker.com/engine/reference/commandline/rm/)
* [<span data-ttu-id="9c595-206">docker rmi</span><span class="sxs-lookup"><span data-stu-id="9c595-206">docker rmi</span></span>](https://docs.docker.com/engine/reference/commandline/rmi/)
* [<span data-ttu-id="9c595-207">Obrázek docker</span><span class="sxs-lookup"><span data-stu-id="9c595-207">docker image</span></span>](https://docs.docker.com/engine/reference/commandline/image/)

#### <a name="build-and-run"></a><span data-ttu-id="9c595-208">Sestavení a spuštění</span><span class="sxs-lookup"><span data-stu-id="9c595-208">Build and run</span></span>

<span data-ttu-id="9c595-209">Jste napsali soubor docker; Teď Docker sestavení vaší aplikace a pak spustí kontejneru.</span><span class="sxs-lookup"><span data-stu-id="9c595-209">You wrote the dockerfile; now Docker builds your app and then runs the container.</span></span>

```console
docker build -t dotnetapp-dev .
docker run --rm dotnetapp-dev Hello from Docker
```

<span data-ttu-id="9c595-210">Výstup `docker build` příkaz by mělo být podobné výstupu v následujícím konzoly:</span><span class="sxs-lookup"><span data-stu-id="9c595-210">The output from the `docker build` command should be similar to the following console output:</span></span>

```console
Sending build context to Docker daemon   72.7kB
Step 1/7 : FROM microsoft/dotnet:2.0-sdk
 ---> d84f64b126a6
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
Successfully built 53c337887e18
Successfully tagged dotnetapp-dev:latest
```

<span data-ttu-id="9c595-211">Jak je vidět z výstupu modulu Docker soubor Docker použita k vytvoření naše kontejneru.</span><span class="sxs-lookup"><span data-stu-id="9c595-211">As you can see from the output, the Docker Engine used the Dockerfile to build our container.</span></span>

<span data-ttu-id="9c595-212">Výstup `docker run` příkaz by mělo být podobné výstupu v následujícím konzoly:</span><span class="sxs-lookup"><span data-stu-id="9c595-212">The output from the `docker run` command should be similar to the following console output:</span></span>

```console
Hello World!
```

<span data-ttu-id="9c595-213">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="9c595-213">Congratulations!</span></span> <span data-ttu-id="9c595-214">máte právě:</span><span class="sxs-lookup"><span data-stu-id="9c595-214">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="9c595-215">Vytvořit místní aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="9c595-215">Created a local .NET Core app</span></span>
> * <span data-ttu-id="9c595-216">Vytvořit soubor Docker k vytvoření vaší první kontejneru</span><span class="sxs-lookup"><span data-stu-id="9c595-216">Created a Dockerfile to build your first container</span></span>
> * <span data-ttu-id="9c595-217">Vytvořené a spustil aplikaci Dockerized</span><span class="sxs-lookup"><span data-stu-id="9c595-217">Built and ran your Dockerized app</span></span>



## <a name="next-steps"></a><span data-ttu-id="9c595-218">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9c595-218">Next Steps</span></span>

<span data-ttu-id="9c595-219">Zde jsou některé další kroky, které můžete provést:</span><span class="sxs-lookup"><span data-stu-id="9c595-219">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="9c595-220">Úvod do rozhraní .NET Docker bitové kopie Video</span><span class="sxs-lookup"><span data-stu-id="9c595-220">Introduction to .NET Docker Images Video</span></span>](https://channel9.msdn.com/Shows/Code-Conversations/Introduction-to-NET-Docker-Images-with-Kendra-Havens?term=docker)
* [<span data-ttu-id="9c595-221">Visual Studio, Docker & instancí kontejnerů Azure lepší společně!</span><span class="sxs-lookup"><span data-stu-id="9c595-221">Visual Studio, Docker & Azure Container Instances better together!</span></span>](https://blogs.msdn.microsoft.com/alimaz/2017/08/17/visual-studio-docker-azure-container-instances-better-together/)
* [<span data-ttu-id="9c595-222">Docker pro Azure – elementy QuickStart</span><span class="sxs-lookup"><span data-stu-id="9c595-222">Docker for Azure Quickstarts</span></span>](https://docs.docker.com/docker-for-azure/#docker-community-edition-ce-for-azure)
* [<span data-ttu-id="9c595-223">Nasazení aplikace na Docker pro Azure.</span><span class="sxs-lookup"><span data-stu-id="9c595-223">Deploy your app on Docker for Azure</span></span>](https://docs.docker.com/docker-for-azure/deploy/)

> [!Note]
> <span data-ttu-id="9c595-224">Pokud nemáte předplatné Azure, [Přihlaste se ještě dnes](https://azure.microsoft.com/free/?b=16.48) bezplatný účet 30 dnů a 200 USD get v kredity Azure můžete vyzkoušet na libovolnou kombinaci služby Azure.</span><span class="sxs-lookup"><span data-stu-id="9c595-224">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

## <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="9c595-225">Docker obrázků použitých v této ukázce</span><span class="sxs-lookup"><span data-stu-id="9c595-225">Docker Images used in this sample</span></span>

<span data-ttu-id="9c595-226">V této ukázce se používají na následujících obrázcích Docker</span><span class="sxs-lookup"><span data-stu-id="9c595-226">The following Docker images are used in this sample</span></span>

* [`microsoft/dotnet:2.0-sdk`](https://hub.docker.com/r/microsoft/dotnet)

## <a name="related-resources"></a><span data-ttu-id="9c595-227">Související informační zdroje</span><span class="sxs-lookup"><span data-stu-id="9c595-227">Related Resources</span></span>

* [<span data-ttu-id="9c595-228">Ukázky rozhraní .NET core Docker</span><span class="sxs-lookup"><span data-stu-id="9c595-228">.NET Core Docker samples</span></span>](https://github.com/dotnet/dotnet-docker-samples/README.md)
* [<span data-ttu-id="9c595-229">Soubor Docker kontejnerům Windows</span><span class="sxs-lookup"><span data-stu-id="9c595-229">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="9c595-230">Ukázky rozhraní .NET framework Docker</span><span class="sxs-lookup"><span data-stu-id="9c595-230">.NET Framework Docker samples</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples)
* [<span data-ttu-id="9c595-231">Jádro ASP.NET na DockerHub</span><span class="sxs-lookup"><span data-stu-id="9c595-231">ASP.NET Core on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore/)
* [<span data-ttu-id="9c595-232">Dockerize aplikace .NET Core – kurz Docker</span><span class="sxs-lookup"><span data-stu-id="9c595-232">Dockerize a .NET Core application - Docker Tutorial</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)
* [<span data-ttu-id="9c595-233">Práce s nástroji Visual Studio Docker</span><span class="sxs-lookup"><span data-stu-id="9c595-233">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="9c595-234">Nasazení bitových kopií Docker z registru kontejner Azure do Azure kontejner instancí</span><span class="sxs-lookup"><span data-stu-id="9c595-234">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)