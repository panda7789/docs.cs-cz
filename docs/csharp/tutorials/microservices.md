---
title: "Mikroslužeb hostované v Docker - C#"
description: "Naučte se vytvořit základní služby, které běží v kontejnerech Docker asp.net"
keywords: "Rozhraní .NET, rozhraní .NET core, Docker, C#, ASP.NET, Mikroslužbu"
author: BillWagner
ms.author: wiwagn
ms.date: 02/03/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: csharp
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: 6cdc4eb0d0fea93b5210532210ad0c928e35a7a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="8d0d2-104">Mikroslužeb hostované v Docker</span><span class="sxs-lookup"><span data-stu-id="8d0d2-104">Microservices hosted in Docker</span></span>

## <a name="introduction"></a><span data-ttu-id="8d0d2-105">Úvod</span><span class="sxs-lookup"><span data-stu-id="8d0d2-105">Introduction</span></span>

<span data-ttu-id="8d0d2-106">V tomto kurzu podrobnosti o úlohách, které jsou nezbytné pro vytváření a nasazení ASP.NET Core mikroslužbu v kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-106">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="8d0d2-107">V průběhu tohoto kurzu se dozvíte:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-107">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="8d0d2-108">Jak vygenerovat aplikace ASP.NET Core pomocí Yeoman</span><span class="sxs-lookup"><span data-stu-id="8d0d2-108">How to generate an ASP.NET Core application using Yeoman</span></span>
* <span data-ttu-id="8d0d2-109">Postup vytvoření prostředí pro vývoj Docker</span><span class="sxs-lookup"><span data-stu-id="8d0d2-109">How to create a development Docker environment</span></span>
* <span data-ttu-id="8d0d2-110">Jak vytvořit bitovou kopii Docker na základě existující bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-110">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="8d0d2-111">Postup nasazení služby do kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-111">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="8d0d2-112">Cestou se dozvíte se taky, některé funkce jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-112">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="8d0d2-113">Postup převedení objektů jazyka C# do datové části JSON.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-113">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="8d0d2-114">Jak vytvořit objekty neměnné přenosu dat</span><span class="sxs-lookup"><span data-stu-id="8d0d2-114">How to build immutable Data Transfer Objects</span></span>
* <span data-ttu-id="8d0d2-115">Postupy pro zpracování příchozích požadavků HTTP a vygenerování odpovědi HTTP</span><span class="sxs-lookup"><span data-stu-id="8d0d2-115">How to process incoming HTTP Requests and generate the HTTP Response</span></span>
* <span data-ttu-id="8d0d2-116">Jak pracovat s typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="8d0d2-116">How to work with nullable value types</span></span>

<span data-ttu-id="8d0d2-117">Můžete [zobrazení nebo stažení ukázkové aplikace](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/WeatherMicroservice) pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-117">You can [view or download the sample app](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="8d0d2-118">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="8d0d2-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

### <a name="why-docker"></a><span data-ttu-id="8d0d2-119">Proč Docker?</span><span class="sxs-lookup"><span data-stu-id="8d0d2-119">Why Docker?</span></span>

<span data-ttu-id="8d0d2-120">Docker usnadňuje vytvoření bitové kopie standardní počítačů pro hostování vaší služby v datovém centru, nebo veřejný cloud.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-120">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="8d0d2-121">Docker umožňuje konfiguraci bitové kopie a replikaci podle potřeby škálování k instalaci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-121">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="8d0d2-122">Všechny kód v tomto kurzu bude fungovat v jakémkoli prostředí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-122">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="8d0d2-123">Další úlohy pro instalaci Docker budou fungovat v aplikaci ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-123">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="8d0d2-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d0d2-124">Prerequisites</span></span>
<span data-ttu-id="8d0d2-125">Budete potřebovat k nastavení vašeho počítače ke spuštění .NET core.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-125">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="8d0d2-126">Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-126">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="8d0d2-127">Tuto aplikaci můžete spustit v systému Windows, Ubuntu Linux, systému macOS nebo v kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-127">You can run this application on Windows, Ubuntu Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="8d0d2-128">Budete muset nainstalovat editor vaše oblíbené kódu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-128">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="8d0d2-129">Popisy níže použijte [Visual Studio Code](https://code.visualstudio.com/) který je typu open source pro různé platformy editor.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-129">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="8d0d2-130">Můžete však použít, ať nástroje umíte pracovat s.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-130">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="8d0d2-131">Také budete potřebovat k instalaci modulu Docker.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-131">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="8d0d2-132">Najdete v článku [Docker instalační stránka](http://www.docker.com/products/docker) pokyny pro vaši platformu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-132">See the [Docker Installation page](http://www.docker.com/products/docker) for instructions for your platform.</span></span>
<span data-ttu-id="8d0d2-133">Docker lze nainstalovat v mnoha Linuxových distribucích, systému macOS nebo systému Windows.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-133">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="8d0d2-134">Tato stránka výše uvedené obsahuje oddíly pro každou instalaci k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-134">The page referenced above contains sections to each of the available installations.</span></span>

<span data-ttu-id="8d0d2-135">Většina součástí k instalaci, provádí správce balíčků.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-135">Most components to be installed are done by a package manager.</span></span> <span data-ttu-id="8d0d2-136">Pokud máte Správce balíčků na node.js `npm` nainstalované, můžete tento krok přeskočit.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-136">If you have node.js's package manager `npm` installed you can skip this step.</span></span> <span data-ttu-id="8d0d2-137">V opačném případě nainstalovat nejnovější NodeJs z [nodejs.org](https://nodejs.org) který nainstaluje Správce balíčku npm.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-137">Otherwise install the latest NodeJs from [nodejs.org](https://nodejs.org) which will install the npm package manager.</span></span> 

<span data-ttu-id="8d0d2-138">V tomto okamžiku musíte nainstalovat několik nástrojů příkazového řádku, které podporují ASP.NET core vývoj.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-138">At this point you will need to install a number of command line tools that support ASP.NET core development.</span></span> <span data-ttu-id="8d0d2-139">Šablony příkazového řádku pomocí Yeoman, Grunt, Bower a Gulp.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-139">The command line templates use Yeoman, Bower, Grunt, and Gulp.</span></span> <span data-ttu-id="8d0d2-140">Pokud máte je nainstalován, které je vhodný, v opačném případě zadejte následující do své oblíbené prostředí:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-140">If you have them installed that is good, otherwise type the following into your favorite shell:</span></span>

`npm install -g yo bower grunt-cli gulp`

<span data-ttu-id="8d0d2-141">`-g` Možnost znamená, že je globální instalace, a tyto nástroje jsou k dispozici celý systém.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-141">The `-g` option indicates that it is a global install, and those tools are available system wide.</span></span> <span data-ttu-id="8d0d2-142">(Místní instalace rozsahy balíčku, který má jeden projekt).</span><span class="sxs-lookup"><span data-stu-id="8d0d2-142">(A local install scopes the package to a single project).</span></span> <span data-ttu-id="8d0d2-143">Jakmile tyto základní nástroje jste nainstalovali, musíte nainstalovat generátory šablony yeoman asp.net:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-143">Once you've installed those core tools, you need to install the yeoman asp.net template generators:</span></span>

`npm install -g generator-aspnet`

## <a name="create-the-application"></a><span data-ttu-id="8d0d2-144">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="8d0d2-144">Create the Application</span></span>

<span data-ttu-id="8d0d2-145">Teď, když jste nainstalovali všechny nástroje, vytvořte novou aplikaci asp.net core.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-145">Now that you've installed all the tools, create a new asp.net core application.</span></span> <span data-ttu-id="8d0d2-146">Pokud chcete používat generátor příkazového řádku, spusťte následující příkaz yeoman ve své oblíbené prostředí:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-146">To use the command line generator, execute the following yeoman command in your favorite shell:</span></span>

`yo aspnet`

<span data-ttu-id="8d0d2-147">Tento příkaz zobrazí výzva k výběru jaký typ aplikace, kterou chcete vytvořit.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-147">This command prompts you to select what Type of application you want to create.</span></span> <span data-ttu-id="8d0d2-148">Pro tento mikroslužbu má možné nejjednodušším, nejvíce jednoduché webové aplikace, tak vyberte 'Prázdné webové aplikace'.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-148">For this microservice, you want the simplest, most lightweight web application possible, so select 'Empty Web Application'.</span></span> <span data-ttu-id="8d0d2-149">Šablona zobrazí výzvu k zadání názvu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-149">The template will prompt you for a name.</span></span> <span data-ttu-id="8d0d2-150">Vyberte 'WeatherMicroservice'.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-150">Select 'WeatherMicroservice'.</span></span> 

<span data-ttu-id="8d0d2-151">Šablona pro vás vytvoří osm soubory:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-151">The template creates eight files for you:</span></span>

* <span data-ttu-id="8d0d2-152">.Gitignore přizpůsobené pro aplikace asp.net core.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-152">A .gitignore, customized for asp.net core applications.</span></span>
* <span data-ttu-id="8d0d2-153">Soubor Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-153">A Startup.cs file.</span></span> <span data-ttu-id="8d0d2-154">Tato položka obsahuje základ aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-154">This contains the basis of the application.</span></span>
* <span data-ttu-id="8d0d2-155">Soubor Program.cs.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-155">A Program.cs file.</span></span> <span data-ttu-id="8d0d2-156">Tato položka obsahuje vstupní bod aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-156">This contains the entry point of the application.</span></span>
* <span data-ttu-id="8d0d2-157">Soubor WeatherMicroservice.csproj.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-157">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="8d0d2-158">Toto je soubor sestavení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-158">This is the build file for the application.</span></span>
* <span data-ttu-id="8d0d2-159">Soubor Docker.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-159">A Dockerfile.</span></span> <span data-ttu-id="8d0d2-160">Tento skript vytvoří bitovou kopii Docker pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-160">This script creates a Docker image for the application.</span></span>
* <span data-ttu-id="8d0d2-161">README.md.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-161">A README.md.</span></span> <span data-ttu-id="8d0d2-162">Tato položka obsahuje odkazy na další zdroje základní technologie asp.net.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-162">This contains links to other asp.net core resources.</span></span>
* <span data-ttu-id="8d0d2-163">Soubor web.config.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-163">A web.config file.</span></span> <span data-ttu-id="8d0d2-164">Tato položka obsahuje informace o základní konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-164">This contains basic configuration information.</span></span>
* <span data-ttu-id="8d0d2-165">Soubor runtimeconfig.template.json.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-165">A runtimeconfig.template.json file.</span></span> <span data-ttu-id="8d0d2-166">Tato položka obsahuje ladění nastavení, které používají integrovaného vývojového prostředí.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-166">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="8d0d2-167">Nyní můžete spustit aplikace vygeneruje šablony.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-167">Now you can run the template generated application.</span></span> <span data-ttu-id="8d0d2-168">Pomocí řady nástroje z příkazového řádku, které bylo dokončeno.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-168">That's done using a series of tools from the command line.</span></span> <span data-ttu-id="8d0d2-169">`dotnet` Příkaz spustí nástroje potřebné pro .NET – vývoj.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-169">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="8d0d2-170">Každý příkaz spouští jiný příkaz</span><span class="sxs-lookup"><span data-stu-id="8d0d2-170">Each verb executes a different command</span></span>

<span data-ttu-id="8d0d2-171">Prvním krokem je obnovit všechny závislosti:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-171">The first step is to restore all the dependencies:</span></span>

```console
dotnet restore
```

<span data-ttu-id="8d0d2-172">Obnovení DotNet používá Správce balíčků NuGet k instalaci nezbytných balíčků do adresáře aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-172">Dotnet restore uses the NuGet package manager to install all the necessary packages into the application directory.</span></span> <span data-ttu-id="8d0d2-173">Rovněž vygeneruje soubor project.json.lock.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-173">It also generates a project.json.lock file.</span></span> <span data-ttu-id="8d0d2-174">Tento soubor obsahuje informace o každý balíček, který se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-174">This file contains information about each package that is referenced.</span></span> <span data-ttu-id="8d0d2-175">Po obnovení všechny závislosti, sestavte aplikaci:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-175">After restoring all the dependencies, you build the application:</span></span>

```console
dotnet build
```
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="8d0d2-176">A Jakmile vytvoříte aplikaci, můžete ji spustit z příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-176">And once you build the application, you run it from the command line:</span></span>

```console
dotnet run
```

<span data-ttu-id="8d0d2-177">Výchozí konfigurace naslouchá na http://localhost: 5000.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-177">The default configuration listens to http://localhost:5000.</span></span> <span data-ttu-id="8d0d2-178">Otevřete prohlížeč, přejděte na této stránce a najdete v části "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="8d0d2-178">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="8d0d2-179">Zpráva.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-179">message.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="8d0d2-180">Anatomie aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8d0d2-180">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="8d0d2-181">Teď, když jste sestavili aplikaci, podíváme, jak je implementována tato funkce.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-181">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="8d0d2-182">Existují dva generované soubory, které jsou v tomto okamžiku zajímavé: project.json a Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-182">There are two of the generated files that are particularly interesting at this point: project.json and Startup.cs.</span></span> 

<span data-ttu-id="8d0d2-183">Project.JSON obsahuje informace o projektu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-183">Project.json contains information about the project.</span></span> <span data-ttu-id="8d0d2-184">Dva uzly, se kterými budete často pracovat jsou 'závislosti' a 'architektury'.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-184">The two nodes you'll often work with are 'dependencies' and 'frameworks'.</span></span> <span data-ttu-id="8d0d2-185">Uzel závislosti zobrazí seznam všech balíčků, které jsou potřebné pro tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-185">The dependencies node lists all the packages that are needed for this application.</span></span>
<span data-ttu-id="8d0d2-186">V tuto chvíli Toto je malé uzlu, kteří potřebují jenom balíčky, které spustí webový server.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-186">At the moment, this is a small node, needing only the packages that run the web server.</span></span>

<span data-ttu-id="8d0d2-187">Uzlu 'architektury' Určuje verze a konfigurace rozhraní .NET Framework, který se spustí tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-187">The 'frameworks' node specifies the versions and configurations of the .NET framework that will run this application.</span></span>

<span data-ttu-id="8d0d2-188">Aplikace je implementovaná v souboru Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-188">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="8d0d2-189">Tento soubor obsahuje třídu pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-189">This file contains the startup class.</span></span>

<span data-ttu-id="8d0d2-190">Tyto dvě metody jsou volány asp.net základní infrastruktury pro konfiguraci a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-190">The two methods are called by the asp.net core infrastructure to configure and run the application.</span></span> <span data-ttu-id="8d0d2-191">`ConfigureServices` Metoda popisuje služby, které jsou nutné pro tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-191">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="8d0d2-192">Kterou sestavujete štíhlého mikroslužbu, takže není nutné nakonfigurovat všechny závislosti.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-192">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="8d0d2-193">`Configure` Metoda konfiguruje obslužných rutin pro příchozí požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-193">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="8d0d2-194">Šablona generuje jednoduchá obslužná rutina, která reaguje na každou žádost s text "Hello, World!".</span><span class="sxs-lookup"><span data-stu-id="8d0d2-194">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="8d0d2-195">Sestavení mikroslužbu</span><span class="sxs-lookup"><span data-stu-id="8d0d2-195">Build a microservice</span></span>

<span data-ttu-id="8d0d2-196">Službu se chystáte vytvořit získávat zprávy o počasí odkudkoli po celém světě.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-196">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="8d0d2-197">V případě produkční aplikace by volání některé služby k načtení dat počasí.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-197">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="8d0d2-198">Pro naše ukázka budete se vygeneruje náhodné předpověď počasí.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-198">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="8d0d2-199">Existuje několik úloh, které budete muset provést kvůli implementaci naši službu náhodných počasí:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-199">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="8d0d2-200">Analyzovat příchozí požadavek na čtení zeměpisné šířky a délky.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-200">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="8d0d2-201">Generovat některé náhodná data prognózy.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-201">Generate some random forecast data.</span></span>
* <span data-ttu-id="8d0d2-202">Převeďte náhodných dat prognózy z jazyka C# objektů JSON paketů.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-202">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="8d0d2-203">Nastavte hlavičku odpovědi k označení, že vaše služba odesílá zpět JSON.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-203">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="8d0d2-204">Zápis do odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-204">Write the response.</span></span>

<span data-ttu-id="8d0d2-205">Další části vás provede procesem každý z těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-205">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="8d0d2-206">Analýza řetězec dotazu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-206">Parsing the Query String.</span></span>

<span data-ttu-id="8d0d2-207">Brzy analýzou řetězce dotazu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-207">You'll begin by parsing the query string.</span></span> <span data-ttu-id="8d0d2-208">Služba bude přijímat 'lat' a 'dlouhý' argumenty na řetězec dotazu v tomto formuláři:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-208">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

`http://localhost:5000/?lat=-35.55&long=-12.35`  

<span data-ttu-id="8d0d2-209">Všechny změny je třeba, aby se definován jako argument výraz lambda `app.Run` v třídě spuštění.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-209">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="8d0d2-210">Argument na výrazu lambda je `HttpContext` pro požadavek.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-210">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="8d0d2-211">Jedna z vlastností je `Request` objektu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-211">One of its properties is the `Request` object.</span></span> <span data-ttu-id="8d0d2-212">`Request` Objekt má `Query` vlastnost, která obsahuje slovník ze všech hodnot v řetězci dotazu pro daný požadavek.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-212">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="8d0d2-213">Pokud chcete najít hodnoty zeměpisné šířky a délky je první přidání:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-213">The first addition is to find the latitude and longitude values:</span></span>

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

<span data-ttu-id="8d0d2-214">Hodnoty slovníku dotazu jsou `StringValue` typu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-214">The Query dictionary values are `StringValue` type.</span></span> <span data-ttu-id="8d0d2-215">Tento typ může obsahovat kolekci řetězců.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-215">That type can contain a collection of strings.</span></span> <span data-ttu-id="8d0d2-216">Každá hodnota služby počasí je jeden řetězec.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-216">For your weather service, each value is a single string.</span></span> <span data-ttu-id="8d0d2-217">Proto je volání `FirstOrDefault()` ve výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-217">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="8d0d2-218">Dále musíte převést řetězce na hodnoty Double.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-218">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="8d0d2-219">Je metoda, které budete používat pro řetězec převést na dvojitou `double.TryParse()`:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-219">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="8d0d2-220">Tato metoda využívá C# výstupní parametry k označení, pokud lze vstupní řetězec převést na dvojitou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-220">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="8d0d2-221">Pokud řetězec představují znázornění platná pro datový typ double, vrátí metoda hodnotu true a `result` argument obsahuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-221">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="8d0d2-222">Pokud řetězec nepředstavuje platný datový typ double, vrátí metoda hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-222">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="8d0d2-223">Můžete přizpůsobit toto rozhraní API s použitím *metoda rozšíření* , který vrací *s možnou hodnotou Null dvojitou*.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-223">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="8d0d2-224">A *typ s možnou hodnotou Null hodnoty* je typ, který reprezentuje typ některé hodnoty a můžete také obsahovat chybějící nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-224">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="8d0d2-225">Typ s možnou hodnotou null je reprezentována připojením `?` znak na deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-225">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="8d0d2-226">Rozšiřující metody jsou metody, které jsou definovány jako statické metody, ale přidáním `this` modifikátor na prvním parametrem nelze volat, jako kdyby jsou členy této třídy.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-226">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="8d0d2-227">Rozšiřující metody, může být definována pouze statické třídy.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-227">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="8d0d2-228">Zde je definice třídy obsahující rozšiřující metodu pro analýzu:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-228">Here's the definition of the class containing the extension method for parse:</span></span>

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

<span data-ttu-id="8d0d2-229">`default(double?)` Výraz vrátí výchozí hodnota `double?` typu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-229">The `default(double?)` expression returns the default value for the `double?` type.</span></span> <span data-ttu-id="8d0d2-230">Tato výchozí hodnota je hodnota null (nebo chybějící).</span><span class="sxs-lookup"><span data-stu-id="8d0d2-230">That default value is the null (or missing) value.</span></span>

<span data-ttu-id="8d0d2-231">Tato metoda rozšíření můžete převést na typ dvojitý argumenty řetězce dotazu:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-231">You can use this extension method to convert the query string arguments into the double type:</span></span>

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

<span data-ttu-id="8d0d2-232">Snadno otestovat kód pro analýzu, aktualizujte odpověď na hodnoty argumenty, které zahrnují:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-232">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

<span data-ttu-id="8d0d2-233">V tomto okamžiku můžete spustit webové aplikace a zda analýzy kódu funguje.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-233">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="8d0d2-234">Přidání hodnoty do webové žádosti v prohlížeči a měli byste vidět aktualizované výsledky.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-234">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="8d0d2-235">Sestavení náhodných předpovědi počasí</span><span class="sxs-lookup"><span data-stu-id="8d0d2-235">Build a random weather forecast</span></span>

<span data-ttu-id="8d0d2-236">Svůj další úkol je sestavení náhodných předpověď počasí.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-236">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="8d0d2-237">Začneme kontejner dat, který obsahuje hodnoty, které je vhodnější pro předpověď počasí:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-237">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions = new string[]
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HiTemperature { get; }
    public int LoTemperature { get; }
    public int AverageWindSpeed { get; }
    public string Conditions { get; }
}
```

<span data-ttu-id="8d0d2-238">V dalším kroku sestavení konstruktor, který náhodně nastaví tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-238">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="8d0d2-239">Tento konstruktor používá hodnoty zeměpisné šířky a délky k generátor náhodných čísel.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-239">This constructor uses the values for the latitude and longitude to seed the Random number generator.</span></span> <span data-ttu-id="8d0d2-240">To znamená, že předpovědi pro stejné umístění je stejný.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-240">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="8d0d2-241">Pokud změníte argumenty pro zeměpisnou šířku a délku, získáte různých prognózy (protože se začíná s jinou počáteční hodnoty.)</span><span class="sxs-lookup"><span data-stu-id="8d0d2-241">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed.)</span></span>

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

<span data-ttu-id="8d0d2-242">Nyní můžete generovat prognózy 5 dní v odpovědi metodu:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-242">You can now generate the 5-day forecast in your response method:</span></span>

[!code-csharp[GenerateRandomReport](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#GenerateRandomReport "Generate a random weather report")]

### <a name="build-the-json-response"></a><span data-ttu-id="8d0d2-243">Vytvořte odpověď JSON.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-243">Build the JSON response.</span></span>

<span data-ttu-id="8d0d2-244">Kód poslední úlohy na serveru je převést na JSON paket WeatherReport pole a odesílat to zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-244">The final code task on the server is to convert the WeatherReport array into a JSON packet, and send that back to the client.</span></span> <span data-ttu-id="8d0d2-245">Začněme vytvořením paketu JSON.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-245">Let's start by creating the JSON packet.</span></span> <span data-ttu-id="8d0d2-246">Serializátor JSON NewtonSoft přidáte do seznamu závislosti.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-246">You'll add the NewtonSoft JSON Serializer to the list of dependencies.</span></span> <span data-ttu-id="8d0d2-247">Můžete to, že pomocí `dotnet` rozhraní příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-247">You can do that using the `dotnet` CLI:</span></span>

```
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="8d0d2-248">Pak můžete použít `JsonConvert` třída pro psaní objekt na řetězec:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-248">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

<span data-ttu-id="8d0d2-249">Výše uvedený kód převede objekt prognózy (seznam `WeatherForecast` objekty) do formátu JSON paketu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-249">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON packet.</span></span> <span data-ttu-id="8d0d2-250">Po způsob konstrukce paket odpovědi, nastavíte typ obsahu na `application/json`a zápis řetězec.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-250">After you've constructed the response packet, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="8d0d2-251">Aplikace se teď spustí a vrátí náhodné prognózy.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-251">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="8d0d2-252">Vytvořit bitovou kopii Docker</span><span class="sxs-lookup"><span data-stu-id="8d0d2-252">Build a Docker image</span></span>

<span data-ttu-id="8d0d2-253">Naše poslední je spuštění aplikace v nástroji Docker.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-253">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="8d0d2-254">Vytvoříme kontejner Docker, který spouští Docker obrázku, který představuje naší aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-254">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="8d0d2-255">A ***Docker Image*** je soubor, který definuje prostředí pro spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-255">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="8d0d2-256">A ***kontejner Docker*** představuje spuštěné instance Docker bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-256">A ***Docker Container*** represents a running instance of a Docker image.</span></span>

<span data-ttu-id="8d0d2-257">Obdobně, si můžete představit *Docker Image* jako *třída*a *kontejner Docker* jako objekt nebo instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-257">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="8d0d2-258">Soubor Docker vytvořených šablonou asp.net bude sloužit pro naše účely.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-258">The Dockerfile created by the asp.net template will serve for our purposes.</span></span> <span data-ttu-id="8d0d2-259">Vraťme se přes jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-259">Let's go over its contents.</span></span>

<span data-ttu-id="8d0d2-260">První řádek určuje zdrojové bitové kopie:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-260">The first line specifies the source image:</span></span>

```
FROM microsoft/dotnet:1.1-sdk-msbuild
```

<span data-ttu-id="8d0d2-261">Docker umožňuje nakonfigurovat bitové kopie počítače na základě šablony zdroje.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-261">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="8d0d2-262">Znamená, že nemáte k zadání všech parametrů počítač při spuštění, stačí zadat všechny změny.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-262">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="8d0d2-263">Změny tady bude zahrnovat naší aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-263">The changes here will be to include our application.</span></span>

<span data-ttu-id="8d0d2-264">V této ukázce první použijeme `1.1-sdk-msbuild` verze bitové kopie dotnet.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-264">In this first sample, we'll use the `1.1-sdk-msbuild` version of the dotnet image.</span></span> <span data-ttu-id="8d0d2-265">Toto je nejjednodušší způsob, jak vytvořit funkční Docker prostředí.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-265">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="8d0d2-266">Tento image zahrnovat na dotnet core runtime a dotnet SDK.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-266">This image include the dotnet core runtime, and the dotnet SDK.</span></span> <span data-ttu-id="8d0d2-267">Který usnadňuje začít a sestavení, ale vytvoření bitové kopie větší.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-267">That makes it easier to get started and build, but does create a larger image.</span></span>

<span data-ttu-id="8d0d2-268">Následujících pět řádků instalační program a sestavit aplikaci:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-268">The next five lines setup and build your application:</span></span>

```
WORKDIR /app

# copy csproj and restore as distinct layers

COPY WeatherMicroservice.csproj .
RUN dotnet restore 

# copy and build everything else

COPY . .

# RUN dotnet restore
RUN dotnet publish -c Release -o out
```

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="8d0d2-269">To bude zkopírujte soubor projektu do docker virtuálních počítačů z aktuálního adresáře a obnovte všechny balíčky.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-269">This will copy the project file from the  current directory to the docker VM, and restore all the packages.</span></span> <span data-ttu-id="8d0d2-270">Pomocí rozhraní příkazového řádku dotnet znamená, že Docker image musí obsahovat .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-270">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="8d0d2-271">Poté se zkopírují zbytek vaší aplikace a dotnet publikování příkaz sestavení a balíčky aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-271">After that, the rest of your application gets copied, and the dotnet publish command builds and packages your application.</span></span>

<span data-ttu-id="8d0d2-272">Poslední řádek souboru spustí aplikaci:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-272">The final line of the file runs the application:</span></span>

```
ENTRYPOINT ["dotnet", "out/WeatherMicroservice.dll", "--server.urls", "http://0.0.0.0:5000"]
```

<span data-ttu-id="8d0d2-273">Tento port nakonfigurovaný odkazuje `--server.urls` argument `dotnet` na posledním řádku soubor Docker.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-273">This configured port is referenced in the `--server.urls` argument to `dotnet` on the last  line of the Dockerfile.</span></span> <span data-ttu-id="8d0d2-274">`ENTRYPOINT` Příkaz informuje Docker, jaké možnosti příkazu a příkazového řádku spusťte službu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-274">The `ENTRYPOINT` command informs Docker  what command and command line options start the service.</span></span> 

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="8d0d2-275">Vytváření a spouštění bitovou kopii v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-275">Building and running the image in a container.</span></span>

<span data-ttu-id="8d0d2-276">Umožňuje vytvořit bitovou kopii a spustit službu uvnitř kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-276">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="8d0d2-277">Nechcete, aby všechny soubory z vašeho místního adresáře zkopírován do bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-277">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="8d0d2-278">Místo toho budete vytvoříte aplikaci v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-278">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="8d0d2-279">Vytvoříte `.dockerignore` souboru k zadání adresáře, které nejsou zkopírovány do bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-279">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="8d0d2-280">Nechcete, aby všechny prostředky sestavení zkopírovali.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-280">You don't want any of the build assets copied.</span></span> <span data-ttu-id="8d0d2-281">Zadejte sestavení a publikování adresářů v `.dockerignore` souboru:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-281">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="8d0d2-282">Můžete vytvořit bitovou kopii pomocí příkazu docker sestavení.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-282">You build the image using the docker build command.</span></span> <span data-ttu-id="8d0d2-283">Spusťte následující příkaz z adresáře, která obsahuje váš kód.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-283">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="8d0d2-284">Tento příkaz vytvoří bitovou kopii kontejneru na základě všech informací v váš soubor Docker.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-284">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="8d0d2-285">`-t` Argument poskytuje značka nebo název pro tuto bitovou kopii kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-285">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="8d0d2-286">V příkazovém řádku výše, je použít pro kontejner Docker značky `weather-microservice`.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-286">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="8d0d2-287">Po dokončení tohoto příkazu máte připraven ke spuštění služby nový kontejner.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-287">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="8d0d2-288">Spusťte následující příkaz spusťte kontejner a spusťte služby:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-288">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:5000 --name hello-docker weather-microservice
```

<span data-ttu-id="8d0d2-289">`-d` Možnost znamená, že spusťte kontejner odpojený od aktuální terminálu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-289">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="8d0d2-290">To znamená, že neuvidíte výstupu příkazu v terminálu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-290">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="8d0d2-291">`-p` Možnost označuje mapování portů mezi službou a hostitele.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-291">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="8d0d2-292">Zde říká, že port 5000 na kontejneru mají předávat všechny příchozí požadavek na portu 80.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-292">Here it says that any incoming request on port 80 should be forwarded to port 5000 on the container.</span></span> <span data-ttu-id="8d0d2-293">Pomocí 5000 odpovídá vaší služby z argumentů příkazového řádku zadaný v výše soubor Docker naslouchá na portu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-293">Using 5000 matches the port your service is listening on from the command line arguments specified in the Dockerfile above.</span></span> <span data-ttu-id="8d0d2-294">`--name` Argument názvy vaší spuštěné kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-294">The `--name` argument names your running container.</span></span> <span data-ttu-id="8d0d2-295">Je vhodné názvem, který můžete použít pro práci s tohoto kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-295">It's a convenient name you can use to work with that container.</span></span> 

<span data-ttu-id="8d0d2-296">Můžete zjistit, zda bitovou kopii je spuštěn kontrolou příkaz:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-296">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="8d0d2-297">Pokud vaše kontejneru běží, uvidíte řádek, který uvádí v spuštěných procesů.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-297">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="8d0d2-298">(To může být pouze).</span><span class="sxs-lookup"><span data-stu-id="8d0d2-298">(It may be the only one).</span></span>

<span data-ttu-id="8d0d2-299">Otevřením prohlížeče a přejdete na místního hostitele a určující zeměpisnou šířku a délku můžete otestovat služby:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-299">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="8d0d2-300">Připojení ke spuštěné kontejneru</span><span class="sxs-lookup"><span data-stu-id="8d0d2-300">Attaching to a running container</span></span>

<span data-ttu-id="8d0d2-301">Chcete-li v příkazovém okně vaší adresářové, by mohli zobrazit diagnostické informace vytisknout pro každý požadavek.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-301">When you ran your sevice in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="8d0d2-302">Tyto informace nevidíte, pokud je v odpojeném režimu vašeho kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-302">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="8d0d2-303">Docker připojit příkaz umožňuje připojit ke kontejneru spuštěné, aby mohli zobrazit informace o protokolu.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-303">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="8d0d2-304">Tento příkaz spusťte z příkazového okna:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-304">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="8d0d2-305">`--sig-proxy=false` Argument znamená, že `Ctrl-C` příkazy get neodešle do procesu kontejneru, ale spíš Zastavit `docker attach` příkaz.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-305">The `--sig-proxy=false` argument means that `Ctrl-C` commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="8d0d2-306">Konečný argument je daný název kontejneru v `docker run` příkaz.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-306">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="8d0d2-307">Můžete taky docker přiřazeno ID kontejneru odkazovat na žádné kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-307">You can also use the docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="8d0d2-308">Pokud jste nezadali název vašeho kontejneru v `docker run` musíte použít id kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-308">If you didn't specify a name for your container in `docker run` you must use the container id.</span></span>

<span data-ttu-id="8d0d2-309">Otevřete prohlížeč a přejděte do služby.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-309">Open a browser and navigate to your service.</span></span> <span data-ttu-id="8d0d2-310">Uvidíte diagnostické zprávy v systému windows příkaz z připojených spuštěné kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-310">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="8d0d2-311">Stiskněte klávesu `Ctrl-C` zastavit proces připojení.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-311">Press `Ctrl-C` to stop the attach process.</span></span>

<span data-ttu-id="8d0d2-312">Po dokončení práce s vaší kontejneru, můžete ho zastavit:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-312">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="8d0d2-313">Kontejner a bitové kopie je stále k dispozici pro restartování.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-313">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="8d0d2-314">Pokud chcete odebrat kontejner z počítače, můžete pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-314">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="8d0d2-315">Pokud chcete odebrat nepoužité bitové kopie z počítače, můžete pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="8d0d2-315">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="8d0d2-316">Závěr</span><span class="sxs-lookup"><span data-stu-id="8d0d2-316">Conclusion</span></span> 

<span data-ttu-id="8d0d2-317">V tomto kurzu vytvořené mikroslužbu jádro asp.net a přidat několik jednoduchých funkce.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-317">In this tutorial, you built an asp.net core microservice, and added a few simple features.</span></span>

<span data-ttu-id="8d0d2-318">Vytvořené docker kontejneru bitovou kopii pro tuto službu a byl spuštěn kontejneru na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-318">You built a docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="8d0d2-319">Připojit ke službě okno terminálu a viděli diagnostické zprávy z vaší služby.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-319">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="8d0d2-320">Přitom jste viděli několik funkcí jazyka C# v akci.</span><span class="sxs-lookup"><span data-stu-id="8d0d2-320">Along the way, you saw several features of the C# language in action.</span></span>
