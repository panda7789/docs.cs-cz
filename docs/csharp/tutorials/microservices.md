---
title: Mikroslužeb hostované v Docker - C#
description: Naučte se vytvořit základní služby, které běží v kontejnerech Docker asp.net
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: 1f4b38243beb1210b1374bd701fac66b2fa72cc5
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106347"
---
# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="e85fe-103">Mikroslužeb hostované v Docker</span><span class="sxs-lookup"><span data-stu-id="e85fe-103">Microservices hosted in Docker</span></span>

<span data-ttu-id="e85fe-104">V tomto kurzu podrobnosti o úlohách, které jsou nezbytné pro vytváření a nasazení ASP.NET Core mikroslužbu v kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="e85fe-104">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="e85fe-105">V průběhu tohoto kurzu se dozvíte:</span><span class="sxs-lookup"><span data-stu-id="e85fe-105">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="e85fe-106">Jak vygenerovat aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e85fe-106">How to generate an ASP.NET Core application.</span></span>
* <span data-ttu-id="e85fe-107">Postup vytvoření prostředí pro vývoj Docker.</span><span class="sxs-lookup"><span data-stu-id="e85fe-107">How to create a development Docker environment.</span></span>
* <span data-ttu-id="e85fe-108">Jak vytvořit bitovou kopii Docker na základě existující bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="e85fe-108">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="e85fe-109">Postup nasazení služby do kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="e85fe-109">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="e85fe-110">Cestou se dozvíte se taky, některé funkce jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="e85fe-110">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="e85fe-111">Postup převedení objektů jazyka C# do datové části JSON.</span><span class="sxs-lookup"><span data-stu-id="e85fe-111">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="e85fe-112">Jak sestavit neměnné datové objekty přenosu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-112">How to build immutable Data Transfer Objects.</span></span>
* <span data-ttu-id="e85fe-113">Postupy pro zpracování příchozích požadavků HTTP a vygenerování odpovědi HTTP.</span><span class="sxs-lookup"><span data-stu-id="e85fe-113">How to process incoming HTTP Requests and generate the HTTP Response.</span></span>
* <span data-ttu-id="e85fe-114">Jak pracovat s typy hodnot s povolenou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="e85fe-114">How to work with nullable value types.</span></span>

<span data-ttu-id="e85fe-115">Můžete [zobrazení nebo stažení ukázkové aplikace](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="e85fe-115">You can [view or download the sample app](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="e85fe-116">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="e85fe-116">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="why-docker"></a><span data-ttu-id="e85fe-117">Proč Docker?</span><span class="sxs-lookup"><span data-stu-id="e85fe-117">Why Docker?</span></span>

<span data-ttu-id="e85fe-118">Docker usnadňuje vytvoření bitové kopie standardní počítačů pro hostování vaší služby v datovém centru, nebo veřejný cloud.</span><span class="sxs-lookup"><span data-stu-id="e85fe-118">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="e85fe-119">Docker umožňuje konfiguraci bitové kopie a replikaci podle potřeby škálování k instalaci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e85fe-119">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="e85fe-120">Všechny kód v tomto kurzu bude fungovat v jakémkoli prostředí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e85fe-120">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="e85fe-121">Další úlohy pro instalaci Docker budou fungovat v aplikaci ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e85fe-121">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="e85fe-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e85fe-122">Prerequisites</span></span>

<span data-ttu-id="e85fe-123">Budete potřebovat k nastavení vašeho počítače ke spuštění .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e85fe-123">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="e85fe-124">Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky.</span><span class="sxs-lookup"><span data-stu-id="e85fe-124">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="e85fe-125">Tuto aplikaci můžete spustit v systému Windows, Linux, systému macOS nebo v kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="e85fe-125">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="e85fe-126">Budete muset nainstalovat editor vaše oblíbené kódu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-126">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="e85fe-127">Popisy níže použijte [Visual Studio Code](https://code.visualstudio.com/) který je typu open source pro různé platformy editor.</span><span class="sxs-lookup"><span data-stu-id="e85fe-127">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="e85fe-128">Můžete však použít, ať nástroje umíte pracovat s.</span><span class="sxs-lookup"><span data-stu-id="e85fe-128">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="e85fe-129">Také budete potřebovat k instalaci modulu Docker.</span><span class="sxs-lookup"><span data-stu-id="e85fe-129">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="e85fe-130">Najdete v článku [Docker instalační stránka](http://www.docker.com/products/docker) pokyny pro vaši platformu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-130">See the [Docker Installation page](http://www.docker.com/products/docker) for instructions for your platform.</span></span>
<span data-ttu-id="e85fe-131">Docker lze nainstalovat v mnoha Linuxových distribucích, systému macOS nebo systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e85fe-131">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="e85fe-132">Tato stránka výše uvedené obsahuje oddíly pro každou instalaci k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e85fe-132">The page referenced above contains sections to each of the available installations.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="e85fe-133">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="e85fe-133">Create the Application</span></span>

<span data-ttu-id="e85fe-134">Teď, když jste nainstalovali všechny nástroje, vytvořte novou aplikaci ASP.NET Core v adresář s názvem "WeatherMicroservice" spuštěním následujícího příkazu v své oblíbené prostředí:</span><span class="sxs-lookup"><span data-stu-id="e85fe-134">Now that you've installed all the tools, create a new ASP.NET Core application in a directory called "WeatherMicroservice" by executing the following command in your favorite shell:</span></span>

```console
dotnet new web -o WeatherMicroservice
```

<span data-ttu-id="e85fe-135">`dotnet` Příkaz spustí nástroje potřebné pro .NET – vývoj.</span><span class="sxs-lookup"><span data-stu-id="e85fe-135">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="e85fe-136">Každý příkaz spouští jiný příkaz.</span><span class="sxs-lookup"><span data-stu-id="e85fe-136">Each verb executes a different command.</span></span>

<span data-ttu-id="e85fe-137">`dotnet new` Příkaz se používá k vytvoření .net základní projekty.</span><span class="sxs-lookup"><span data-stu-id="e85fe-137">The `dotnet new` command is used to create .Net Core projects.</span></span>

<span data-ttu-id="e85fe-138">`-o WeatherMicroservice` Možnost po `dotnet new` příkaz umožňuje poskytnout umístění pro vytvoření aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e85fe-138">The `-o WeatherMicroservice` option after the `dotnet new` command is used to give the location to create the ASP.NET Core application.</span></span>

<span data-ttu-id="e85fe-139">Pro tento mikroslužby chceme nejjednodušším, nejvíce jednoduché webové aplikace to možné, takže jsme použili šabloně "ASP.NET Core prázdný" zadáním jeho krátký název `web`.</span><span class="sxs-lookup"><span data-stu-id="e85fe-139">For this microservice, we want the simplest, most lightweight web application possible, so we used the "ASP.NET Core Empty" template, by specifying its short name, `web`.</span></span>

<span data-ttu-id="e85fe-140">Šablona pro vás vytvoří čtyři soubory:</span><span class="sxs-lookup"><span data-stu-id="e85fe-140">The template creates four files for you:</span></span>

* <span data-ttu-id="e85fe-141">Soubor Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="e85fe-141">A Startup.cs file.</span></span> <span data-ttu-id="e85fe-142">Tato položka obsahuje základ aplikace.</span><span class="sxs-lookup"><span data-stu-id="e85fe-142">This contains the basis of the application.</span></span>
* <span data-ttu-id="e85fe-143">Soubor Program.cs.</span><span class="sxs-lookup"><span data-stu-id="e85fe-143">A Program.cs file.</span></span> <span data-ttu-id="e85fe-144">Tato položka obsahuje vstupní bod aplikace.</span><span class="sxs-lookup"><span data-stu-id="e85fe-144">This contains the entry point of the application.</span></span>
* <span data-ttu-id="e85fe-145">Soubor WeatherMicroservice.csproj.</span><span class="sxs-lookup"><span data-stu-id="e85fe-145">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="e85fe-146">Toto je soubor sestavení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e85fe-146">This is the build file for the application.</span></span>
* <span data-ttu-id="e85fe-147">Soubor Properties/launchSettings.json.</span><span class="sxs-lookup"><span data-stu-id="e85fe-147">A Properties/launchSettings.json file.</span></span> <span data-ttu-id="e85fe-148">Tato položka obsahuje ladění nastavení, které používají integrovaného vývojového prostředí.</span><span class="sxs-lookup"><span data-stu-id="e85fe-148">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="e85fe-149">Nyní můžete spustit aplikace vygeneruje šablony:</span><span class="sxs-lookup"><span data-stu-id="e85fe-149">Now you can run the template generated application:</span></span>

```console
dotnet run
```

<span data-ttu-id="e85fe-150">Tento příkaz obnoví nejprve závislosti požadované aplikace se sestaví a potom ho sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e85fe-150">This command will first restore dependencies required to build the application and then it will build the application.</span></span>

<span data-ttu-id="e85fe-151">Výchozí konfigurace naslouchá `http://localhost:5000`.</span><span class="sxs-lookup"><span data-stu-id="e85fe-151">The default configuration listens to `http://localhost:5000`.</span></span> <span data-ttu-id="e85fe-152">Otevřete prohlížeč, přejděte na této stránce a najdete v části "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="e85fe-152">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="e85fe-153">Zpráva.</span><span class="sxs-lookup"><span data-stu-id="e85fe-153">message.</span></span>

<span data-ttu-id="e85fe-154">Když jste hotovi, můžete vypnout aplikaci stisknutím <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="e85fe-154">When you're done, you can shut down the application by pressing <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="e85fe-155">Anatomie aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e85fe-155">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="e85fe-156">Teď, když jste sestavili aplikaci, podíváme, jak je implementována tato funkce.</span><span class="sxs-lookup"><span data-stu-id="e85fe-156">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="e85fe-157">Existují dva generované soubory, které jsou v tomto okamžiku zajímavé: WeatherMicroservice.csproj a Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="e85fe-157">There are two of the generated files that are particularly interesting at this point: WeatherMicroservice.csproj and Startup.cs.</span></span> 

<span data-ttu-id="e85fe-158">Souboru .csproj obsahuje informace o projektu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-158">The .csproj file contains information about the project.</span></span>
<span data-ttu-id="e85fe-159">Jsou dva uzly, které jsou nejvíce zajímavé `<TargetFramework>` a `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="e85fe-159">The two nodes that are most interesting are `<TargetFramework>` and `<PackageReference>`.</span></span>

<span data-ttu-id="e85fe-160">`<TargetFramework>` Uzlu Určuje verzi rozhraní .NET, který se spustí tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e85fe-160">The `<TargetFramework>` node specifies the version of .NET that will run this application.</span></span>

<span data-ttu-id="e85fe-161">Každý `<PackageReference>` uzlu se používá k určení balíčku, který je potřebný pro tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e85fe-161">Each `<PackageReference>` node is used to specify a package that is needed for this application.</span></span>

<span data-ttu-id="e85fe-162">Aplikace je implementovaná v souboru Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="e85fe-162">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="e85fe-163">Tento soubor obsahuje třídu pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="e85fe-163">This file contains the startup class.</span></span>

<span data-ttu-id="e85fe-164">Tyto dvě metody jsou volány ASP.NET základní infrastruktury pro konfiguraci a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e85fe-164">The two methods are called by the ASP.NET Core infrastructure to configure and run the application.</span></span> <span data-ttu-id="e85fe-165">`ConfigureServices` Metoda popisuje služby, které jsou nutné pro tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e85fe-165">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="e85fe-166">Kterou sestavujete štíhlého mikroslužbu, takže není nutné nakonfigurovat všechny závislosti.</span><span class="sxs-lookup"><span data-stu-id="e85fe-166">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="e85fe-167">`Configure` Metoda konfiguruje obslužných rutin pro příchozí požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="e85fe-167">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="e85fe-168">Šablona generuje jednoduchá obslužná rutina, která reaguje na každou žádost s text "Hello, World!".</span><span class="sxs-lookup"><span data-stu-id="e85fe-168">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="e85fe-169">Sestavení mikroslužbu</span><span class="sxs-lookup"><span data-stu-id="e85fe-169">Build a microservice</span></span>

<span data-ttu-id="e85fe-170">Službu se chystáte vytvořit získávat zprávy o počasí odkudkoli po celém světě.</span><span class="sxs-lookup"><span data-stu-id="e85fe-170">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="e85fe-171">V případě produkční aplikace by volání některé služby k načtení dat počasí.</span><span class="sxs-lookup"><span data-stu-id="e85fe-171">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="e85fe-172">Pro naše ukázka budete se vygeneruje náhodné předpověď počasí.</span><span class="sxs-lookup"><span data-stu-id="e85fe-172">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="e85fe-173">Existuje několik úloh, které budete muset provést kvůli implementaci naši službu náhodných počasí:</span><span class="sxs-lookup"><span data-stu-id="e85fe-173">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="e85fe-174">Analyzovat příchozí požadavek na čtení zeměpisné šířky a délky.</span><span class="sxs-lookup"><span data-stu-id="e85fe-174">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="e85fe-175">Generovat některé náhodná data prognózy.</span><span class="sxs-lookup"><span data-stu-id="e85fe-175">Generate some random forecast data.</span></span>
* <span data-ttu-id="e85fe-176">Převeďte náhodných dat prognózy z jazyka C# objektů JSON paketů.</span><span class="sxs-lookup"><span data-stu-id="e85fe-176">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="e85fe-177">Nastavte hlavičku odpovědi k označení, že vaše služba odesílá zpět JSON.</span><span class="sxs-lookup"><span data-stu-id="e85fe-177">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="e85fe-178">Zápis do odpovědi.</span><span class="sxs-lookup"><span data-stu-id="e85fe-178">Write the response.</span></span>

<span data-ttu-id="e85fe-179">Další části vás provede procesem každý z těchto kroků.</span><span class="sxs-lookup"><span data-stu-id="e85fe-179">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="e85fe-180">Analýza řetězec dotazu</span><span class="sxs-lookup"><span data-stu-id="e85fe-180">Parsing the Query String</span></span>

<span data-ttu-id="e85fe-181">Brzy analýzou řetězce dotazu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-181">You'll begin by parsing the query string.</span></span> <span data-ttu-id="e85fe-182">Služba bude přijímat 'lat' a 'dlouhý' argumenty na řetězec dotazu v tomto formuláři:</span><span class="sxs-lookup"><span data-stu-id="e85fe-182">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

<span data-ttu-id="e85fe-183">Všechny změny je třeba, aby se definován jako argument výraz lambda `app.Run` v třídě spuštění.</span><span class="sxs-lookup"><span data-stu-id="e85fe-183">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="e85fe-184">Argument na výrazu lambda je `HttpContext` pro požadavek.</span><span class="sxs-lookup"><span data-stu-id="e85fe-184">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="e85fe-185">Jedna z vlastností je `Request` objektu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-185">One of its properties is the `Request` object.</span></span> <span data-ttu-id="e85fe-186">`Request` Objekt má `Query` vlastnost, která obsahuje slovník ze všech hodnot v řetězci dotazu pro daný požadavek.</span><span class="sxs-lookup"><span data-stu-id="e85fe-186">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="e85fe-187">Pokud chcete najít hodnoty zeměpisné šířky a délky je první přidání:</span><span class="sxs-lookup"><span data-stu-id="e85fe-187">The first addition is to find the latitude and longitude values:</span></span>

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

<span data-ttu-id="e85fe-188">`Query` Hodnoty slovníku jsou `StringValue` typu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-188">The `Query` dictionary values are `StringValue` type.</span></span> <span data-ttu-id="e85fe-189">Tento typ může obsahovat kolekci řetězců.</span><span class="sxs-lookup"><span data-stu-id="e85fe-189">That type can contain a collection of strings.</span></span> <span data-ttu-id="e85fe-190">Každá hodnota služby počasí je jeden řetězec.</span><span class="sxs-lookup"><span data-stu-id="e85fe-190">For your weather service, each value is a single string.</span></span> <span data-ttu-id="e85fe-191">Proto je volání `FirstOrDefault()` ve výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-191">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="e85fe-192">Dále musíte převést řetězce na hodnoty Double.</span><span class="sxs-lookup"><span data-stu-id="e85fe-192">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="e85fe-193">Je metoda, které budete používat pro řetězec převést na dvojitou `double.TryParse()`:</span><span class="sxs-lookup"><span data-stu-id="e85fe-193">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="e85fe-194">Tato metoda využívá C# výstupní parametry k označení, pokud lze vstupní řetězec převést na dvojitou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-194">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="e85fe-195">Pokud řetězec představují znázornění platná pro datový typ double, vrátí metoda hodnotu true a `result` argument obsahuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-195">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="e85fe-196">Pokud řetězec nepředstavuje platný datový typ double, vrátí metoda hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="e85fe-196">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="e85fe-197">Můžete přizpůsobit toto rozhraní API s použitím *metoda rozšíření* , který vrací *s možnou hodnotou Null dvojitou*.</span><span class="sxs-lookup"><span data-stu-id="e85fe-197">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="e85fe-198">A *typ s možnou hodnotou Null hodnoty* je typ, který reprezentuje typ některé hodnoty a můžete také obsahovat chybějící nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="e85fe-198">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="e85fe-199">Typ s možnou hodnotou null je reprezentována připojením `?` znak na deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-199">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="e85fe-200">Rozšiřující metody jsou metody, které jsou definovány jako statické metody, ale přidáním `this` modifikátor na prvním parametrem nelze volat, jako kdyby jsou členy této třídy.</span><span class="sxs-lookup"><span data-stu-id="e85fe-200">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="e85fe-201">Rozšiřující metody, může být definována pouze statické třídy.</span><span class="sxs-lookup"><span data-stu-id="e85fe-201">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="e85fe-202">Zde je definice třídy obsahující rozšiřující metodu pro analýzu:</span><span class="sxs-lookup"><span data-stu-id="e85fe-202">Here's the definition of the class containing the extension method for parse:</span></span>

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

<span data-ttu-id="e85fe-203">Před voláním metody rozšíření, změňte výchozí jazykové verze aktuálního:</span><span class="sxs-lookup"><span data-stu-id="e85fe-203">Before calling the extension method, change the current culture to invariant:</span></span>

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

<span data-ttu-id="e85fe-204">Tím se zajistí, že vaše aplikace analyzuje stejná čísla na libovolném serveru, bez ohledu na jeho výchozí jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="e85fe-204">This ensures that your application parses numbers the same on any server, regardless of its default culture.</span></span>

<span data-ttu-id="e85fe-205">Teď můžete použít metodu rozšíření převést na typ dvojitý argumenty řetězce dotazu:</span><span class="sxs-lookup"><span data-stu-id="e85fe-205">Now you can use the extension method to convert the query string arguments into the double type:</span></span>

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

<span data-ttu-id="e85fe-206">Snadno otestovat kód pro analýzu, aktualizujte odpověď na hodnoty argumenty, které zahrnují:</span><span class="sxs-lookup"><span data-stu-id="e85fe-206">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

<span data-ttu-id="e85fe-207">V tomto okamžiku můžete spustit webové aplikace a zda analýzy kódu funguje.</span><span class="sxs-lookup"><span data-stu-id="e85fe-207">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="e85fe-208">Přidání hodnoty do webové žádosti v prohlížeči a měli byste vidět aktualizované výsledky.</span><span class="sxs-lookup"><span data-stu-id="e85fe-208">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="e85fe-209">Sestavení náhodných předpovědi počasí</span><span class="sxs-lookup"><span data-stu-id="e85fe-209">Build a random weather forecast</span></span>

<span data-ttu-id="e85fe-210">Svůj další úkol je sestavení náhodných předpověď počasí.</span><span class="sxs-lookup"><span data-stu-id="e85fe-210">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="e85fe-211">Začneme kontejner dat, který obsahuje hodnoty, které je vhodnější pro předpověď počasí:</span><span class="sxs-lookup"><span data-stu-id="e85fe-211">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions =
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HighTemperatureFahrenheit { get; }
    public int LowTemperatureFahrenheit { get; }
    public int AverageWindSpeedMph { get; }
    public string Condition { get; }
}
```

<span data-ttu-id="e85fe-212">V dalším kroku sestavení konstruktor, který náhodně nastaví tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e85fe-212">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="e85fe-213">Tento konstruktor používá hodnoty pro zeměpisnou šířku a zeměpisnou délku na počáteční hodnoty `Random` generátoru čísel.</span><span class="sxs-lookup"><span data-stu-id="e85fe-213">This constructor uses the values for the latitude and longitude to seed the `Random` number generator.</span></span> <span data-ttu-id="e85fe-214">To znamená, že předpovědi pro stejné umístění je stejný.</span><span class="sxs-lookup"><span data-stu-id="e85fe-214">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="e85fe-215">Pokud změníte argumenty pro zeměpisnou šířku a délku, získáte různých prognózy (protože začínat různých počáteční hodnoty).</span><span class="sxs-lookup"><span data-stu-id="e85fe-215">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed).</span></span>

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

<span data-ttu-id="e85fe-216">Nyní můžete generovat prognózy 5 dní v odpovědi metodu:</span><span class="sxs-lookup"><span data-stu-id="e85fe-216">You can now generate the 5-day forecast in your response method:</span></span>

```csharp
if (latitude.HasValue && longitude.HasValue)
{
    var forecast = new List<WeatherReport>();
    for (var days = 1; days <= 5; days++)
    {
        forecast.Add(new WeatherReport(latitude.Value, longitude.Value, days));
    }
}
```

### <a name="build-the-json-response"></a><span data-ttu-id="e85fe-217">Sestavení odpověď JSON</span><span class="sxs-lookup"><span data-stu-id="e85fe-217">Build the JSON response</span></span>

<span data-ttu-id="e85fe-218">Kód poslední úlohy na serveru je převést `WeatherReport` seznamu do dokumentu JSON a odesílání, která zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="e85fe-218">The final code task on the server is to convert the `WeatherReport` list into JSON document, and send that back to the client.</span></span> <span data-ttu-id="e85fe-219">Začněme vytvořením dokumentu JSON.</span><span class="sxs-lookup"><span data-stu-id="e85fe-219">Let's start by creating the JSON document.</span></span> <span data-ttu-id="e85fe-220">Serializátor Newtonsoft JSON přidáte do seznamu závislosti.</span><span class="sxs-lookup"><span data-stu-id="e85fe-220">You'll add the Newtonsoft JSON serializer to the list of dependencies.</span></span> <span data-ttu-id="e85fe-221">Můžete to udělat pomocí následujících `dotnet` příkaz:</span><span class="sxs-lookup"><span data-stu-id="e85fe-221">You can do that using the following `dotnet` command:</span></span>

```console
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="e85fe-222">Pak můžete použít `JsonConvert` třída pro psaní objekt na řetězec:</span><span class="sxs-lookup"><span data-stu-id="e85fe-222">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

<span data-ttu-id="e85fe-223">Výše uvedený kód převede objekt prognózy (seznam `WeatherForecast` objekty) do dokumentu JSON.</span><span class="sxs-lookup"><span data-stu-id="e85fe-223">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON document.</span></span> <span data-ttu-id="e85fe-224">Po způsob konstrukce odpovědi dokument, typ obsahu, který nastavíte na `application/json`a zápis řetězec.</span><span class="sxs-lookup"><span data-stu-id="e85fe-224">After you've constructed the response document, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="e85fe-225">Aplikace se teď spustí a vrátí náhodné prognózy.</span><span class="sxs-lookup"><span data-stu-id="e85fe-225">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="e85fe-226">Vytvořit bitovou kopii Docker</span><span class="sxs-lookup"><span data-stu-id="e85fe-226">Build a Docker image</span></span>

<span data-ttu-id="e85fe-227">Naše poslední je spuštění aplikace v nástroji Docker.</span><span class="sxs-lookup"><span data-stu-id="e85fe-227">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="e85fe-228">Vytvoříme kontejner Docker, který spouští Docker obrázku, který představuje naší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e85fe-228">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="e85fe-229">A ***Docker Image*** je soubor, který definuje prostředí pro spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="e85fe-229">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="e85fe-230">A ***kontejner Docker*** představuje spuštěné instance Docker bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="e85fe-230">A ***Docker Container*** represents a running instance of a Docker Image.</span></span>

<span data-ttu-id="e85fe-231">Obdobně, si můžete představit *Docker Image* jako *třída*a *kontejner Docker* jako objekt nebo instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="e85fe-231">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="e85fe-232">Následující soubor Docker bude sloužit pro naše účely:</span><span class="sxs-lookup"><span data-stu-id="e85fe-232">The following Dockerfile will serve for our purposes:</span></span>

```
FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

<span data-ttu-id="e85fe-233">Vraťme se přes jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="e85fe-233">Let's go over its contents.</span></span>

<span data-ttu-id="e85fe-234">První řádek určuje zdrojové bitové kopie, použít pro vytvoření aplikace:</span><span class="sxs-lookup"><span data-stu-id="e85fe-234">The first line specifies the source image used for building the application:</span></span>

```
FROM microsoft/dotnet:2.1-sdk AS build
```

<span data-ttu-id="e85fe-235">Docker umožňuje nakonfigurovat bitové kopie počítače na základě šablony zdroje.</span><span class="sxs-lookup"><span data-stu-id="e85fe-235">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="e85fe-236">Znamená, že nemáte k zadání všech parametrů počítač při spuštění, stačí zadat všechny změny.</span><span class="sxs-lookup"><span data-stu-id="e85fe-236">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="e85fe-237">Změny tady bude zahrnovat naší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e85fe-237">The changes here will be to include our application.</span></span>

<span data-ttu-id="e85fe-238">V této ukázce, použijeme `2.1-sdk` verzi `dotnet` bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="e85fe-238">In this sample, we'll use the `2.1-sdk` version of the `dotnet` image.</span></span> <span data-ttu-id="e85fe-239">Toto je nejjednodušší způsob, jak vytvořit funkční Docker prostředí.</span><span class="sxs-lookup"><span data-stu-id="e85fe-239">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="e85fe-240">Tento image obsahuje na .NET Core runtime a .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e85fe-240">This image includes the .NET Core runtime, and the .NET Core SDK.</span></span>
<span data-ttu-id="e85fe-241">Který usnadňuje začít a sestavení, ale vytvoření bitové kopie větší, proto použijeme tuto bitovou kopii pro vytváření aplikace a jinou bitovou kopii ji spustit.</span><span class="sxs-lookup"><span data-stu-id="e85fe-241">That makes it easier to get started and build, but does create a larger image, so we'll use this image for building the application and a different image to run it.</span></span>

<span data-ttu-id="e85fe-242">Další řádky instalační program a sestavit aplikaci:</span><span class="sxs-lookup"><span data-stu-id="e85fe-242">The next lines setup and build your application:</span></span>

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="e85fe-243">To se zkopírovat soubor projektu z aktuálního adresáře na virtuální počítač Docker a obnovit všechny balíčky.</span><span class="sxs-lookup"><span data-stu-id="e85fe-243">This will copy the project file from the  current directory to the Docker VM, and restore all the packages.</span></span> <span data-ttu-id="e85fe-244">Pomocí rozhraní příkazového řádku dotnet znamená, že Docker image musí obsahovat .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e85fe-244">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="e85fe-245">Potom získá zbývající aplikace zkopírovali a `dotnet
publish` příkaz vytvoří a balíčky aplikace.</span><span class="sxs-lookup"><span data-stu-id="e85fe-245">After that, the rest of your application gets copied, and the `dotnet
publish` command builds and packages your application.</span></span>

<span data-ttu-id="e85fe-246">Nakonec jsme vytvořit bitovou kopii druhý Docker, který spouští aplikaci:</span><span class="sxs-lookup"><span data-stu-id="e85fe-246">Finally, we create a second Docker image that runs the application:</span></span>

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

<span data-ttu-id="e85fe-247">Používá tuto bitovou kopii `2.1-aspnetcore-runtime` verzi `dotnet` bitovou kopii, kterou obsahuje všechno potřebné ke spouštění aplikací ASP.NET Core, ale nezahrnuje .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="e85fe-247">This image uses the `2.1-aspnetcore-runtime` version of the `dotnet` image, which contains everything necessary to run ASP.NET Core applications, but does not include the .NET Core SDK.</span></span> <span data-ttu-id="e85fe-248">To znamená, že tento obrázek nelze použít k vytváření aplikací .NET Core, ale také umožňuje finální image menší.</span><span class="sxs-lookup"><span data-stu-id="e85fe-248">This means this image can't be used to build .NET Core applications, but it also makes the final image smaller.</span></span>

<span data-ttu-id="e85fe-249">Aby byla zajištěna, jsme zkopírujte integrované aplikace z první bitové kopie na druhou.</span><span class="sxs-lookup"><span data-stu-id="e85fe-249">To make this work, we copy the built application from the first image to the second one.</span></span>

<span data-ttu-id="e85fe-250">`ENTRYPOINT` Příkaz informuje Docker jaké příkazu spustí službu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-250">The `ENTRYPOINT` command informs Docker what command starts the service.</span></span>

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="e85fe-251">Vytváření a spouštění bitovou kopii v kontejneru</span><span class="sxs-lookup"><span data-stu-id="e85fe-251">Building and running the image in a container</span></span>

<span data-ttu-id="e85fe-252">Umožňuje vytvořit bitovou kopii a spustit službu uvnitř kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="e85fe-252">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="e85fe-253">Nechcete, aby všechny soubory z vašeho místního adresáře zkopírován do bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="e85fe-253">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="e85fe-254">Místo toho budete vytvoříte aplikaci v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e85fe-254">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="e85fe-255">Vytvoříte `.dockerignore` souboru k zadání adresáře, které nejsou zkopírovány do bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="e85fe-255">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="e85fe-256">Nechcete, aby všechny prostředky sestavení zkopírovali.</span><span class="sxs-lookup"><span data-stu-id="e85fe-256">You don't want any of the build assets copied.</span></span> <span data-ttu-id="e85fe-257">Zadejte sestavení a publikování adresářů v `.dockerignore` souboru:</span><span class="sxs-lookup"><span data-stu-id="e85fe-257">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="e85fe-258">Sestavování pomocí bitové kopie `docker build` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e85fe-258">You build the image using the `docker build` command.</span></span> <span data-ttu-id="e85fe-259">Spusťte následující příkaz z adresáře, která obsahuje váš kód.</span><span class="sxs-lookup"><span data-stu-id="e85fe-259">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="e85fe-260">Tento příkaz vytvoří bitovou kopii kontejneru na základě všech informací v váš soubor Docker.</span><span class="sxs-lookup"><span data-stu-id="e85fe-260">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="e85fe-261">`-t` Argument poskytuje značka nebo název pro tuto bitovou kopii kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e85fe-261">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="e85fe-262">V příkazovém řádku výše, je použít pro kontejner Docker značky `weather-microservice`.</span><span class="sxs-lookup"><span data-stu-id="e85fe-262">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="e85fe-263">Po dokončení tohoto příkazu máte připraven ke spuštění služby nový kontejner.</span><span class="sxs-lookup"><span data-stu-id="e85fe-263">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="e85fe-264">Spusťte následující příkaz spusťte kontejner a spusťte služby:</span><span class="sxs-lookup"><span data-stu-id="e85fe-264">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

<span data-ttu-id="e85fe-265">`-d` Možnost znamená, že spusťte kontejner odpojený od aktuální terminálu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-265">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="e85fe-266">To znamená, že neuvidíte výstupu příkazu v terminálu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-266">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="e85fe-267">`-p` Možnost označuje mapování portů mezi službou a hostitele.</span><span class="sxs-lookup"><span data-stu-id="e85fe-267">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="e85fe-268">Zde říká, že port 80 na kontejneru mají předávat všechny příchozí požadavek na portu 80.</span><span class="sxs-lookup"><span data-stu-id="e85fe-268">Here it says that any incoming request on port 80 should be forwarded to port 80 on the container.</span></span> <span data-ttu-id="e85fe-269">Pomocí 80 odpovídá portu, které vaše služba naslouchá na, což je výchozí port pro výrobní aplikace.</span><span class="sxs-lookup"><span data-stu-id="e85fe-269">Using 80 matches the port your service is listening on, which is the default port for production applications.</span></span> <span data-ttu-id="e85fe-270">`--name` Argument názvy vaší spuštěné kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e85fe-270">The `--name` argument names your running container.</span></span> <span data-ttu-id="e85fe-271">Je vhodné názvem, který můžete použít pro práci s tohoto kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e85fe-271">It's a convenient name you can use to work with that container.</span></span>

<span data-ttu-id="e85fe-272">Můžete zjistit, zda bitovou kopii je spuštěn kontrolou příkaz:</span><span class="sxs-lookup"><span data-stu-id="e85fe-272">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="e85fe-273">Pokud vaše kontejneru běží, uvidíte řádek, který uvádí v spuštěných procesů.</span><span class="sxs-lookup"><span data-stu-id="e85fe-273">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="e85fe-274">(To může být pouze.)</span><span class="sxs-lookup"><span data-stu-id="e85fe-274">(It may be the only one.)</span></span>

<span data-ttu-id="e85fe-275">Otevřením prohlížeče a přejdete na místního hostitele a určující zeměpisnou šířku a délku můžete otestovat služby:</span><span class="sxs-lookup"><span data-stu-id="e85fe-275">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="e85fe-276">Připojení ke spuštěné kontejneru</span><span class="sxs-lookup"><span data-stu-id="e85fe-276">Attaching to a running container</span></span>

<span data-ttu-id="e85fe-277">Chcete-li v příkazovém okně služby, by mohli zobrazit diagnostické informace vytisknout pro každý požadavek.</span><span class="sxs-lookup"><span data-stu-id="e85fe-277">When you ran your service in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="e85fe-278">Tyto informace nevidíte, pokud je v odpojeném režimu vašeho kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e85fe-278">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="e85fe-279">Docker připojit příkaz umožňuje připojit ke kontejneru spuštěné, aby mohli zobrazit informace o protokolu.</span><span class="sxs-lookup"><span data-stu-id="e85fe-279">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="e85fe-280">Tento příkaz spusťte z příkazového okna:</span><span class="sxs-lookup"><span data-stu-id="e85fe-280">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="e85fe-281">`--sig-proxy=false` Argument znamená, že <kbd>Ctrl</kbd>+<kbd>C</kbd> příkazy get neodešle do procesu kontejneru, ale spíš Zastavit `docker attach` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e85fe-281">The `--sig-proxy=false` argument means that <kbd>Ctrl</kbd>+<kbd>C</kbd> commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="e85fe-282">Konečný argument je daný název kontejneru v `docker run` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e85fe-282">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="e85fe-283">Můžete taky Docker přiřazeno ID kontejneru odkazovat na žádné kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e85fe-283">You can also use the Docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="e85fe-284">Pokud jste nezadali název vašeho kontejneru v `docker run` je nutné použít ID kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e85fe-284">If you didn't specify a name for your container in `docker run` you must use the container ID.</span></span>

<span data-ttu-id="e85fe-285">Otevřete prohlížeč a přejděte do služby.</span><span class="sxs-lookup"><span data-stu-id="e85fe-285">Open a browser and navigate to your service.</span></span> <span data-ttu-id="e85fe-286">Uvidíte diagnostické zprávy v systému windows příkaz z připojených spuštěné kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e85fe-286">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="e85fe-287">Stiskněte klávesu <kbd>Ctrl</kbd>+<kbd>C</kbd> zastavit proces připojení.</span><span class="sxs-lookup"><span data-stu-id="e85fe-287">Press <kbd>Ctrl</kbd>+<kbd>C</kbd> to stop the attach process.</span></span>

<span data-ttu-id="e85fe-288">Po dokončení práce s vaší kontejneru, můžete ho zastavit:</span><span class="sxs-lookup"><span data-stu-id="e85fe-288">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="e85fe-289">Kontejner a bitové kopie je stále k dispozici pro restartování.</span><span class="sxs-lookup"><span data-stu-id="e85fe-289">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="e85fe-290">Pokud chcete odebrat kontejner z počítače, můžete pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="e85fe-290">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="e85fe-291">Pokud chcete odebrat nepoužité bitové kopie z počítače, můžete pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="e85fe-291">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="e85fe-292">Závěr</span><span class="sxs-lookup"><span data-stu-id="e85fe-292">Conclusion</span></span> 

<span data-ttu-id="e85fe-293">V tomto kurzu vytvořené mikroslužbu ASP.NET Core a přidat několik jednoduchých funkce.</span><span class="sxs-lookup"><span data-stu-id="e85fe-293">In this tutorial, you built an ASP.NET Core microservice, and added a few simple features.</span></span>

<span data-ttu-id="e85fe-294">Vytvořené Docker kontejneru bitovou kopii pro tuto službu a byl spuštěn kontejneru na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="e85fe-294">You built a Docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="e85fe-295">Připojit ke službě okno terminálu a viděli diagnostické zprávy z vaší služby.</span><span class="sxs-lookup"><span data-stu-id="e85fe-295">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="e85fe-296">Přitom jste viděli několik funkcí jazyka C# v akci.</span><span class="sxs-lookup"><span data-stu-id="e85fe-296">Along the way, you saw several features of the C# language in action.</span></span>
