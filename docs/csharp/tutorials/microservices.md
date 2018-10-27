---
title: Mikroslužby hostované v Dockeru –C#
description: Zjistěte, jak vytvořit základní služby, které běží v kontejnerech Dockeru technologie asp.net
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: b1f7159a222ab4d68715844e9997ca922676bc80
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49454483"
---
# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="8280f-103">Mikroslužby hostované v Dockeru</span><span class="sxs-lookup"><span data-stu-id="8280f-103">Microservices hosted in Docker</span></span>

<span data-ttu-id="8280f-104">Tento kurz podrobně popisuje úlohy plánování pro sestavování a nasazování mikroslužeb ASP.NET Core v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="8280f-104">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="8280f-105">V průběhu tohoto kurzu se dozvíte:</span><span class="sxs-lookup"><span data-stu-id="8280f-105">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="8280f-106">Jak vygenerovat aplikaci ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8280f-106">How to generate an ASP.NET Core application.</span></span>
* <span data-ttu-id="8280f-107">Jak vytvořit vývojové prostředí Dockeru.</span><span class="sxs-lookup"><span data-stu-id="8280f-107">How to create a development Docker environment.</span></span>
* <span data-ttu-id="8280f-108">Postup pro sestavení image Dockeru na základě existující image.</span><span class="sxs-lookup"><span data-stu-id="8280f-108">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="8280f-109">Postup nasazení služby do kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="8280f-109">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="8280f-110">Na cestě, uvidíte také některé C# funkcí jazyka:</span><span class="sxs-lookup"><span data-stu-id="8280f-110">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="8280f-111">Jak převést C# objekty do datové části JSON.</span><span class="sxs-lookup"><span data-stu-id="8280f-111">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="8280f-112">Postup pro sestavení neměnné datové objekty přenosu.</span><span class="sxs-lookup"><span data-stu-id="8280f-112">How to build immutable Data Transfer Objects.</span></span>
* <span data-ttu-id="8280f-113">Jak ke zpracování příchozích požadavků HTTP a generovat odpověď HTTP.</span><span class="sxs-lookup"><span data-stu-id="8280f-113">How to process incoming HTTP Requests and generate the HTTP Response.</span></span>
* <span data-ttu-id="8280f-114">Jak pracovat s typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="8280f-114">How to work with nullable value types.</span></span>

<span data-ttu-id="8280f-115">Je možné [zobrazení nebo stažení ukázkové aplikace](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) pro toto téma.</span><span class="sxs-lookup"><span data-stu-id="8280f-115">You can [view or download the sample app](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="8280f-116">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="8280f-116">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="why-docker"></a><span data-ttu-id="8280f-117">Proč Docker?</span><span class="sxs-lookup"><span data-stu-id="8280f-117">Why Docker?</span></span>

<span data-ttu-id="8280f-118">Docker usnadňuje vytváření imagí standardní počítač pro hostování vašich služeb v datovém centru nebo veřejného cloudu.</span><span class="sxs-lookup"><span data-stu-id="8280f-118">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="8280f-119">Docker umožňuje nakonfigurujte image a replikaci podle potřeby škálování instalaci vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="8280f-119">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="8280f-120">Veškerý kód v tomto kurzu bude fungovat v jakémkoli prostředí .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8280f-120">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="8280f-121">Další úkoly pro instalaci Dockeru bude fungovat pro aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8280f-121">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="8280f-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8280f-122">Prerequisites</span></span>

<span data-ttu-id="8280f-123">Budete potřebovat k nastavení vašeho počítače ke spuštění .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8280f-123">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="8280f-124">Můžete najít pokyny k instalaci na [.NET Core](https://www.microsoft.com/net/core) stránky.</span><span class="sxs-lookup"><span data-stu-id="8280f-124">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="8280f-125">Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="8280f-125">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="8280f-126">Bude potřeba nainstalovat váš oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="8280f-126">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="8280f-127">Popisy níže použití [Visual Studio Code](https://code.visualstudio.com/) což je open source pro různé platformy editoru.</span><span class="sxs-lookup"><span data-stu-id="8280f-127">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="8280f-128">Ale můžete použít jakýkoli nástroje jste obeznámeni.</span><span class="sxs-lookup"><span data-stu-id="8280f-128">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="8280f-129">Musíte také nainstalovat modul Docker.</span><span class="sxs-lookup"><span data-stu-id="8280f-129">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="8280f-130">Zobrazit [stránky instalace Dockeru](https://docs.docker.com/install/overview/) pokyny pro vaši platformu.</span><span class="sxs-lookup"><span data-stu-id="8280f-130">See the [Docker Installation page](https://docs.docker.com/install/overview/) for instructions for your platform.</span></span>
<span data-ttu-id="8280f-131">Docker je možné nainstalovat v mnoha distribucí systému Linux, macOS a Windows.</span><span class="sxs-lookup"><span data-stu-id="8280f-131">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="8280f-132">Na stránce výše uvedenými obsahuje oddíly pro každý z dostupné instalace.</span><span class="sxs-lookup"><span data-stu-id="8280f-132">The page referenced above contains sections to each of the available installations.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="8280f-133">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="8280f-133">Create the Application</span></span>

<span data-ttu-id="8280f-134">Teď, když si nainstalujete všechny nástroje, vytvořte novou aplikaci ASP.NET Core v adresáři s názvem "WeatherMicroservice" spuštěním následujícího příkazu v oblíbeném prostředí:</span><span class="sxs-lookup"><span data-stu-id="8280f-134">Now that you've installed all the tools, create a new ASP.NET Core application in a directory called "WeatherMicroservice" by executing the following command in your favorite shell:</span></span>

```console
dotnet new web -o WeatherMicroservice
```

<span data-ttu-id="8280f-135">`dotnet` Příkaz spustí nástroje potřebné pro vývoj na platformě .NET.</span><span class="sxs-lookup"><span data-stu-id="8280f-135">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="8280f-136">Každý příkaz spouští k jinému příkazu.</span><span class="sxs-lookup"><span data-stu-id="8280f-136">Each verb executes a different command.</span></span>

<span data-ttu-id="8280f-137">`dotnet new` Příkaz slouží k vytvoření.Net Core projekty.</span><span class="sxs-lookup"><span data-stu-id="8280f-137">The `dotnet new` command is used to create .Net Core projects.</span></span>

<span data-ttu-id="8280f-138">`-o WeatherMicroservice` Za parametr `dotnet new` příkaz slouží k zadejte umístění pro vytvoření aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8280f-138">The `-o WeatherMicroservice` option after the `dotnet new` command is used to give the location to create the ASP.NET Core application.</span></span>

<span data-ttu-id="8280f-139">Pro mikroslužby, chceme nejjednodušší a největší jednoduché webové aplikace je to možné, takže jsme použili "ASP.NET Core prázdnou" šablonu tak, že zadáte jeho krátký název `web`.</span><span class="sxs-lookup"><span data-stu-id="8280f-139">For this microservice, we want the simplest, most lightweight web application possible, so we used the "ASP.NET Core Empty" template, by specifying its short name, `web`.</span></span>

<span data-ttu-id="8280f-140">Šablona pro vás vytvoří čtyři soubory:</span><span class="sxs-lookup"><span data-stu-id="8280f-140">The template creates four files for you:</span></span>

* <span data-ttu-id="8280f-141">Souboru Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="8280f-141">A Startup.cs file.</span></span> <span data-ttu-id="8280f-142">Tato položka obsahuje základ aplikace.</span><span class="sxs-lookup"><span data-stu-id="8280f-142">This contains the basis of the application.</span></span>
* <span data-ttu-id="8280f-143">Soubor Program.cs.</span><span class="sxs-lookup"><span data-stu-id="8280f-143">A Program.cs file.</span></span> <span data-ttu-id="8280f-144">Tato položka obsahuje vstupní bod aplikace.</span><span class="sxs-lookup"><span data-stu-id="8280f-144">This contains the entry point of the application.</span></span>
* <span data-ttu-id="8280f-145">WeatherMicroservice.csproj souboru.</span><span class="sxs-lookup"><span data-stu-id="8280f-145">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="8280f-146">Toto je soubor sestavení pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8280f-146">This is the build file for the application.</span></span>
* <span data-ttu-id="8280f-147">Properties/launchSettings.json souboru.</span><span class="sxs-lookup"><span data-stu-id="8280f-147">A Properties/launchSettings.json file.</span></span> <span data-ttu-id="8280f-148">Tato položka obsahuje ladění nastavení, které používají integrovaného vývojového prostředí.</span><span class="sxs-lookup"><span data-stu-id="8280f-148">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="8280f-149">Nyní můžete spustit aplikaci vygenerovanou šablonu:</span><span class="sxs-lookup"><span data-stu-id="8280f-149">Now you can run the template generated application:</span></span>

```console
dotnet run
```

<span data-ttu-id="8280f-150">Tento příkaz obnoví nejprve závislosti, které vyžaduje k sestavení aplikace a potom ho sestavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8280f-150">This command will first restore dependencies required to build the application and then it will build the application.</span></span>

<span data-ttu-id="8280f-151">Výchozí konfigurace naslouchá `http://localhost:5000`.</span><span class="sxs-lookup"><span data-stu-id="8280f-151">The default configuration listens to `http://localhost:5000`.</span></span> <span data-ttu-id="8280f-152">Otevřete prohlížeč, přejděte na tuto stránku a naleznete v tématu "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="8280f-152">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="8280f-153">zpráva.</span><span class="sxs-lookup"><span data-stu-id="8280f-153">message.</span></span>

<span data-ttu-id="8280f-154">Jakmile budete hotovi, můžete vypnout aplikaci stisknutím klávesy <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8280f-154">When you're done, you can shut down the application by pressing <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="8280f-155">Anatomie aplikace ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8280f-155">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="8280f-156">Teď, když jste vytvořili aplikaci, Podívejme se na tom, jak je implementována tato funkce.</span><span class="sxs-lookup"><span data-stu-id="8280f-156">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="8280f-157">Existují dva soubory, které jsou v tuto chvíli zvlášť zajímavý: WeatherMicroservice.csproj a Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="8280f-157">There are two of the generated files that are particularly interesting at this point: WeatherMicroservice.csproj and Startup.cs.</span></span> 

<span data-ttu-id="8280f-158">Soubor .csproj obsahuje informace o projektu.</span><span class="sxs-lookup"><span data-stu-id="8280f-158">The .csproj file contains information about the project.</span></span>
<span data-ttu-id="8280f-159">Jsou dva uzly, které jsou nejzajímavější `<TargetFramework>` a `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="8280f-159">The two nodes that are most interesting are `<TargetFramework>` and `<PackageReference>`.</span></span>

<span data-ttu-id="8280f-160">`<TargetFramework>` Uzlu Určuje verzi rozhraní .NET, který se spustí tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8280f-160">The `<TargetFramework>` node specifies the version of .NET that will run this application.</span></span>

<span data-ttu-id="8280f-161">Každý `<PackageReference>` uzlu se používá k určení balíčku, který je nezbytný pro tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8280f-161">Each `<PackageReference>` node is used to specify a package that is needed for this application.</span></span>

<span data-ttu-id="8280f-162">Aplikace je implementováno v souboru Startup.cs.</span><span class="sxs-lookup"><span data-stu-id="8280f-162">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="8280f-163">Tento soubor obsahuje třídu pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="8280f-163">This file contains the startup class.</span></span>

<span data-ttu-id="8280f-164">Tyto dvě metody jsou volány ASP.NET Core infrastrukturu pro konfiguraci a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="8280f-164">The two methods are called by the ASP.NET Core infrastructure to configure and run the application.</span></span> <span data-ttu-id="8280f-165">`ConfigureServices` Metody jsou popsány služby, které jsou potřebné pro tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8280f-165">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="8280f-166">Vytváříte Štíhlá mikroslužeb, takže není nutné nakonfigurovat všechny závislosti.</span><span class="sxs-lookup"><span data-stu-id="8280f-166">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="8280f-167">`Configure` Metoda nakonfiguruje obslužné rutiny pro příchozí požadavky HTTP.</span><span class="sxs-lookup"><span data-stu-id="8280f-167">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="8280f-168">Tato šablona vygeneruje jednoduchou obslužnou rutinu, která bude reagovat na každou žádost s textem "Hello World!".</span><span class="sxs-lookup"><span data-stu-id="8280f-168">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="8280f-169">Vytvářet mikroslužby</span><span class="sxs-lookup"><span data-stu-id="8280f-169">Build a microservice</span></span>

<span data-ttu-id="8280f-170">Služba se chystáte vytvořit doručí doručování předpovědí počasí odkudkoli na světě.</span><span class="sxs-lookup"><span data-stu-id="8280f-170">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="8280f-171">V produkční aplikace by volání některé služby se načíst data o počasí.</span><span class="sxs-lookup"><span data-stu-id="8280f-171">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="8280f-172">Naše ukázka vygenerujeme náhodné předpověď počasí.</span><span class="sxs-lookup"><span data-stu-id="8280f-172">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="8280f-173">Existuje mnoho úloh, které budete muset provést, abyste mohli implementovat naše služby náhodné weather:</span><span class="sxs-lookup"><span data-stu-id="8280f-173">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="8280f-174">Parsovat příchozí požadavek na čtení zeměpisné šířky a délky.</span><span class="sxs-lookup"><span data-stu-id="8280f-174">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="8280f-175">Generovat náhodná data prognózy.</span><span class="sxs-lookup"><span data-stu-id="8280f-175">Generate some random forecast data.</span></span>
* <span data-ttu-id="8280f-176">Převést tento náhodných dat prognózy z C# objekty do formátu JSON paketů.</span><span class="sxs-lookup"><span data-stu-id="8280f-176">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="8280f-177">Nastavte hlavičku odpovědi k označení, že vaše služba odešle zpět JSON.</span><span class="sxs-lookup"><span data-stu-id="8280f-177">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="8280f-178">Zápis odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8280f-178">Write the response.</span></span>

<span data-ttu-id="8280f-179">Následující části vás provede jednotlivé kroky.</span><span class="sxs-lookup"><span data-stu-id="8280f-179">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="8280f-180">Analýza řetězce dotazu</span><span class="sxs-lookup"><span data-stu-id="8280f-180">Parsing the Query String</span></span>

<span data-ttu-id="8280f-181">Zobrazí za přibližně analýzou řetězce dotazu.</span><span class="sxs-lookup"><span data-stu-id="8280f-181">You'll begin by parsing the query string.</span></span> <span data-ttu-id="8280f-182">Služba bude přijímat "lat" a "dlouhý" argumenty řetězce dotazu v tomto formuláři:</span><span class="sxs-lookup"><span data-stu-id="8280f-182">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

<span data-ttu-id="8280f-183">Všechny změny, je třeba, aby se ve výrazu lambda, který je definován jako argument `app.Run` ve své třídě spuštění.</span><span class="sxs-lookup"><span data-stu-id="8280f-183">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="8280f-184">Argument výrazu lambda je `HttpContext` pro daný požadavek.</span><span class="sxs-lookup"><span data-stu-id="8280f-184">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="8280f-185">Jedna z jeho vlastností je `Request` objektu.</span><span class="sxs-lookup"><span data-stu-id="8280f-185">One of its properties is the `Request` object.</span></span> <span data-ttu-id="8280f-186">`Request` Má objekt `Query` vlastnost, která obsahuje slovník ze všech hodnot v řetězci dotazu požadavku.</span><span class="sxs-lookup"><span data-stu-id="8280f-186">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="8280f-187">Pokud chcete najít hodnoty zeměpisné šířky a délky je prvního přidání:</span><span class="sxs-lookup"><span data-stu-id="8280f-187">The first addition is to find the latitude and longitude values:</span></span>

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

<span data-ttu-id="8280f-188">`Query` Hodnoty slovníku jsou `StringValue` typu.</span><span class="sxs-lookup"><span data-stu-id="8280f-188">The `Query` dictionary values are `StringValue` type.</span></span> <span data-ttu-id="8280f-189">Tento typ mohou obsahovat kolekce řetězců.</span><span class="sxs-lookup"><span data-stu-id="8280f-189">That type can contain a collection of strings.</span></span> <span data-ttu-id="8280f-190">Pro vaši službu počasí každá hodnota je jeden řetězec.</span><span class="sxs-lookup"><span data-stu-id="8280f-190">For your weather service, each value is a single string.</span></span> <span data-ttu-id="8280f-191">To je důvod, proč je volání `FirstOrDefault()` ve výše uvedeném kódu.</span><span class="sxs-lookup"><span data-stu-id="8280f-191">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="8280f-192">Dále je třeba převést řetězce čísly typu Double.</span><span class="sxs-lookup"><span data-stu-id="8280f-192">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="8280f-193">Metoda použijete tak řetězec převést na typ double je `double.TryParse()`:</span><span class="sxs-lookup"><span data-stu-id="8280f-193">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="8280f-194">Tato metoda využívá C# výstupní parametry k označení, pokud je možné vstupní řetězec převést na hodnotu double.</span><span class="sxs-lookup"><span data-stu-id="8280f-194">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="8280f-195">Pokud řetězec představuje platný reprezentaci pro typ double, metoda vrátí hodnotu true a `result` argument obsahuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8280f-195">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="8280f-196">Pokud řetězec nepředstavuje platný typ double, vrátí metoda hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="8280f-196">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="8280f-197">Můžete upravit toto rozhraní API s použitím *– metoda rozšíření* , která vrací *s možnou hodnotou Null double*.</span><span class="sxs-lookup"><span data-stu-id="8280f-197">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="8280f-198">A *typ s možnou hodnotou Null* je typ, který představuje typ některé hodnoty a může také obsahovat chybějící nebo hodnota null.</span><span class="sxs-lookup"><span data-stu-id="8280f-198">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="8280f-199">Typ připouštějící hodnotu Null, je reprezentována přidáním `?` znakem k deklaraci typu.</span><span class="sxs-lookup"><span data-stu-id="8280f-199">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="8280f-200">Rozšiřující metody jsou metody, které jsou definovány jako statické metody, ale tak, že přidáte `this` modifikátor první parametr, lze volat, jakoby jsou členy této třídy.</span><span class="sxs-lookup"><span data-stu-id="8280f-200">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="8280f-201">Metody rozšíření lze definovat pouze ve statické třídy.</span><span class="sxs-lookup"><span data-stu-id="8280f-201">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="8280f-202">Tady je definice třídy obsahující metodu rozšíření pro analýzu:</span><span class="sxs-lookup"><span data-stu-id="8280f-202">Here's the definition of the class containing the extension method for parse:</span></span>

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

<span data-ttu-id="8280f-203">Před voláním metody rozšíření, změňte na invariantní aktuální jazykové verze:</span><span class="sxs-lookup"><span data-stu-id="8280f-203">Before calling the extension method, change the current culture to invariant:</span></span>

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

<span data-ttu-id="8280f-204">Tím se zajistí, že vaše aplikace analyzuje stejná čísla na libovolném serveru, bez ohledu na jeho výchozí jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="8280f-204">This ensures that your application parses numbers the same on any server, regardless of its default culture.</span></span>

<span data-ttu-id="8280f-205">Teď můžete použít metodu rozšíření můžete převést na typ double argumenty řetězce dotazu:</span><span class="sxs-lookup"><span data-stu-id="8280f-205">Now you can use the extension method to convert the query string arguments into the double type:</span></span>

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

<span data-ttu-id="8280f-206">Chcete-li snadno testujte analýzy kódu, aktualizujte odpovědi zahrnout hodnoty argumentů:</span><span class="sxs-lookup"><span data-stu-id="8280f-206">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

<span data-ttu-id="8280f-207">V tomto okamžiku můžete spustit webové aplikace a zda je analýza kódu funguje.</span><span class="sxs-lookup"><span data-stu-id="8280f-207">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="8280f-208">Přidejte hodnoty webové žádosti v prohlížeči a měli byste vidět aktualizované výsledky.</span><span class="sxs-lookup"><span data-stu-id="8280f-208">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="8280f-209">Vytvářet náhodné předpovědí počasí</span><span class="sxs-lookup"><span data-stu-id="8280f-209">Build a random weather forecast</span></span>

<span data-ttu-id="8280f-210">Dalším úkolem je vytvářet náhodné předpověď počasí.</span><span class="sxs-lookup"><span data-stu-id="8280f-210">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="8280f-211">Začněme datový kontejner, který obsahuje hodnoty, které je vhodné pro předpověď počasí:</span><span class="sxs-lookup"><span data-stu-id="8280f-211">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

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

<span data-ttu-id="8280f-212">V dalším kroku sestavení konstruktor, který náhodně nastaví tyto hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8280f-212">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="8280f-213">Tento konstruktor používá hodnoty pro zeměpisnou šířku a zeměpisnou délku na počáteční hodnotu `Random` generátor čísel.</span><span class="sxs-lookup"><span data-stu-id="8280f-213">This constructor uses the values for the latitude and longitude to seed the `Random` number generator.</span></span> <span data-ttu-id="8280f-214">To znamená, že předpovědi na stejném umístění je stejný.</span><span class="sxs-lookup"><span data-stu-id="8280f-214">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="8280f-215">Pokud změníte argumenty pro zeměpisnou šířku a zeměpisnou délku, získáte různých předpovědi (protože začínat různé základní hodnota).</span><span class="sxs-lookup"><span data-stu-id="8280f-215">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed).</span></span>

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

<span data-ttu-id="8280f-216">Teď můžete vygenerovat 5 dní předpovědi ve své metodě odpovědi:</span><span class="sxs-lookup"><span data-stu-id="8280f-216">You can now generate the 5-day forecast in your response method:</span></span>

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

### <a name="build-the-json-response"></a><span data-ttu-id="8280f-217">Sestavení odpověď JSON</span><span class="sxs-lookup"><span data-stu-id="8280f-217">Build the JSON response</span></span>

<span data-ttu-id="8280f-218">Konečný kód úkol na serveru je převést `WeatherReport` seznamu do dokumentu JSON a odešlete zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="8280f-218">The final code task on the server is to convert the `WeatherReport` list into JSON document, and send that back to the client.</span></span> <span data-ttu-id="8280f-219">Začněme vytvořením dokumentu JSON.</span><span class="sxs-lookup"><span data-stu-id="8280f-219">Let's start by creating the JSON document.</span></span> <span data-ttu-id="8280f-220">Serializátor Newtonsoft JSON přidáte na seznam závislostí.</span><span class="sxs-lookup"><span data-stu-id="8280f-220">You'll add the Newtonsoft JSON serializer to the list of dependencies.</span></span> <span data-ttu-id="8280f-221">Můžete to udělat pomocí následujících `dotnet` příkaz:</span><span class="sxs-lookup"><span data-stu-id="8280f-221">You can do that using the following `dotnet` command:</span></span>

```console
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="8280f-222">Potom můžete použít `JsonConvert` třídu pro zápis na objekt na řetězec:</span><span class="sxs-lookup"><span data-stu-id="8280f-222">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

<span data-ttu-id="8280f-223">Výše uvedený kód převede objekt prognózy (seznam `WeatherForecast` objekty) do dokumentu JSON.</span><span class="sxs-lookup"><span data-stu-id="8280f-223">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON document.</span></span> <span data-ttu-id="8280f-224">Poté, co jste vytvořen odpověď dokumentu, nastavte typ obsahu `application/json`a zápisu řetězce.</span><span class="sxs-lookup"><span data-stu-id="8280f-224">After you've constructed the response document, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="8280f-225">Aplikace se teď spustí a vrátí náhodné prognózy.</span><span class="sxs-lookup"><span data-stu-id="8280f-225">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="8280f-226">Sestavíte image Dockeru</span><span class="sxs-lookup"><span data-stu-id="8280f-226">Build a Docker image</span></span>

<span data-ttu-id="8280f-227">Naše poslední úkol je ke spuštění aplikace v Dockeru.</span><span class="sxs-lookup"><span data-stu-id="8280f-227">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="8280f-228">Vytvoříme kontejner Dockeru, na kterém běží image Dockeru, který představuje naši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8280f-228">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="8280f-229">A ***Image Dockeru*** je soubor, který definuje prostředí pro spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="8280f-229">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="8280f-230">A ***kontejneru Dockeru*** představuje běžící instance Image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="8280f-230">A ***Docker Container*** represents a running instance of a Docker Image.</span></span>

<span data-ttu-id="8280f-231">Obdobně, si můžete představit *Image Dockeru* jako *třídy*a *kontejneru Dockeru* jako objekt nebo instance této třídy.</span><span class="sxs-lookup"><span data-stu-id="8280f-231">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="8280f-232">Následující soubor Dockerfile bude sloužit pro naše účely:</span><span class="sxs-lookup"><span data-stu-id="8280f-232">The following Dockerfile will serve for our purposes:</span></span>

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

<span data-ttu-id="8280f-233">Probereme si jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="8280f-233">Let's go over its contents.</span></span>

<span data-ttu-id="8280f-234">První řádek určuje zdroj obrázku použita k sestavení aplikace:</span><span class="sxs-lookup"><span data-stu-id="8280f-234">The first line specifies the source image used for building the application:</span></span>

```
FROM microsoft/dotnet:2.1-sdk AS build
```

<span data-ttu-id="8280f-235">Docker umožňuje nakonfigurovat image počítače, na základě zdroje šablony.</span><span class="sxs-lookup"><span data-stu-id="8280f-235">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="8280f-236">To znamená, není nutné zadat všechny parametry počítače při spuštění, stačí zadat všechny změny.</span><span class="sxs-lookup"><span data-stu-id="8280f-236">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="8280f-237">Změny zde bude zahrnovat naši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8280f-237">The changes here will be to include our application.</span></span>

<span data-ttu-id="8280f-238">V této ukázce použijeme `2.1-sdk` verzi `dotnet` bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="8280f-238">In this sample, we'll use the `2.1-sdk` version of the `dotnet` image.</span></span> <span data-ttu-id="8280f-239">Toto je nejjednodušší způsob, jak vytvořit pracovní prostředí Dockeru.</span><span class="sxs-lookup"><span data-stu-id="8280f-239">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="8280f-240">Tato image obsahuje modul runtime .NET Core a .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="8280f-240">This image includes the .NET Core runtime, and the .NET Core SDK.</span></span>
<span data-ttu-id="8280f-241">Zjednodušuje tím chcete začít pracovat a sestavení, ale vytvořit větší obrázek, takže použijeme tuto image pro vytváření aplikací a jiný obrázek k jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="8280f-241">That makes it easier to get started and build, but does create a larger image, so we'll use this image for building the application and a different image to run it.</span></span>

<span data-ttu-id="8280f-242">Další řádky nastavení a sestavit aplikaci:</span><span class="sxs-lookup"><span data-stu-id="8280f-242">The next lines setup and build your application:</span></span>

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="8280f-243">To zkopíruje soubor projektu z aktuálního adresáře na virtuální počítač Docker a obnovte všechny balíčky.</span><span class="sxs-lookup"><span data-stu-id="8280f-243">This will copy the project file from the  current directory to the Docker VM, and restore all the packages.</span></span> <span data-ttu-id="8280f-244">Pomocí rozhraní příkazového řádku dotnet znamená, že image Dockeru musí obsahovat sadu .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="8280f-244">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="8280f-245">Potom se zkopíruje zbývající části aplikace a `dotnet
publish` příkaz sestaví a zabalí aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8280f-245">After that, the rest of your application gets copied, and the `dotnet
publish` command builds and packages your application.</span></span>

<span data-ttu-id="8280f-246">Nakonec vytvoříme druhý image Dockeru, na kterém běží aplikace:</span><span class="sxs-lookup"><span data-stu-id="8280f-246">Finally, we create a second Docker image that runs the application:</span></span>

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

<span data-ttu-id="8280f-247">Tuto image používá `2.1-aspnetcore-runtime` verzi `dotnet` image, která obsahuje vše potřebné ke spouštění aplikací ASP.NET Core, ale nezahrnuje .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="8280f-247">This image uses the `2.1-aspnetcore-runtime` version of the `dotnet` image, which contains everything necessary to run ASP.NET Core applications, but does not include the .NET Core SDK.</span></span> <span data-ttu-id="8280f-248">To znamená, že tento obrázek nelze použít k sestavování aplikací .NET Core, ale také umožní konečném obrazu menší.</span><span class="sxs-lookup"><span data-stu-id="8280f-248">This means this image can't be used to build .NET Core applications, but it also makes the final image smaller.</span></span>

<span data-ttu-id="8280f-249">Chcete-li tuto práci, jsme zkopírujte sestavené aplikace z první image na druhou.</span><span class="sxs-lookup"><span data-stu-id="8280f-249">To make this work, we copy the built application from the first image to the second one.</span></span>

<span data-ttu-id="8280f-250">`ENTRYPOINT` Příkaz informuje Docker, jaké příkazu spustí službu.</span><span class="sxs-lookup"><span data-stu-id="8280f-250">The `ENTRYPOINT` command informs Docker what command starts the service.</span></span>

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="8280f-251">Vytváření a spouštění image v kontejneru</span><span class="sxs-lookup"><span data-stu-id="8280f-251">Building and running the image in a container</span></span>

<span data-ttu-id="8280f-252">Pojďme vytvořit bitovou kopii a spuštění služby uvnitř kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="8280f-252">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="8280f-253">Nechcete, aby všechny soubory z místního adresáře zkopírován do bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="8280f-253">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="8280f-254">Místo toho budete vytvářet aplikace v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8280f-254">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="8280f-255">Vytvoříte `.dockerignore` souboru k zadání adresáře, které nejsou zkopírovány do bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="8280f-255">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="8280f-256">Nechcete některou prostředků sestavení zkopírovat.</span><span class="sxs-lookup"><span data-stu-id="8280f-256">You don't want any of the build assets copied.</span></span> <span data-ttu-id="8280f-257">Zadejte sestavení a publikování adresáře `.dockerignore` souboru:</span><span class="sxs-lookup"><span data-stu-id="8280f-257">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="8280f-258">Sestavení image pomocí `docker build` příkazu.</span><span class="sxs-lookup"><span data-stu-id="8280f-258">You build the image using the `docker build` command.</span></span> <span data-ttu-id="8280f-259">Spusťte následující příkaz z adresáře, který obsahuje váš kód.</span><span class="sxs-lookup"><span data-stu-id="8280f-259">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="8280f-260">Tento příkaz sestaví image kontejneru, na základě informací o ve vašem souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="8280f-260">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="8280f-261">`-t` Argument obsahuje značku nebo název pro tuto bitovou kopii kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8280f-261">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="8280f-262">Na příkazovém řádku výše, značky použité pro kontejner Dockeru se `weather-microservice`.</span><span class="sxs-lookup"><span data-stu-id="8280f-262">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="8280f-263">Po dokončení tohoto příkazu máte kontejner připraven ke spuštění nové služby.</span><span class="sxs-lookup"><span data-stu-id="8280f-263">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="8280f-264">Spusťte následující příkaz pro spuštění kontejneru a spuštění služby:</span><span class="sxs-lookup"><span data-stu-id="8280f-264">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

<span data-ttu-id="8280f-265">`-d` Možnost znamená, že ke spuštění kontejneru odpojena od aktuální terminálu.</span><span class="sxs-lookup"><span data-stu-id="8280f-265">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="8280f-266">To znamená, že neuvidíte výstupu příkazu v terminálu.</span><span class="sxs-lookup"><span data-stu-id="8280f-266">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="8280f-267">`-p` Možnost označuje mapování portů mezi službou a hostitele.</span><span class="sxs-lookup"><span data-stu-id="8280f-267">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="8280f-268">Tady říká, že jakékoli příchozí žádosti na portu 80 se mají předávat na port 80 v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8280f-268">Here it says that any incoming request on port 80 should be forwarded to port 80 on the container.</span></span> <span data-ttu-id="8280f-269">Pomocí 80 odpovídá portu, které vaše služba naslouchá na, což je výchozí port pro aplikace v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="8280f-269">Using 80 matches the port your service is listening on, which is the default port for production applications.</span></span> <span data-ttu-id="8280f-270">`--name` Argument názvy spuštěný kontejner.</span><span class="sxs-lookup"><span data-stu-id="8280f-270">The `--name` argument names your running container.</span></span> <span data-ttu-id="8280f-271">Je vhodné název, který můžete použít pro práci s tohoto kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8280f-271">It's a convenient name you can use to work with that container.</span></span>

<span data-ttu-id="8280f-272">Můžete zobrazit, zda obrázek běží tak, že zkontrolujete příkazu:</span><span class="sxs-lookup"><span data-stu-id="8280f-272">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="8280f-273">Pokud je váš kontejner spuštěný, zobrazí se vám řádek, který obsahuje spuštěné procesy.</span><span class="sxs-lookup"><span data-stu-id="8280f-273">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="8280f-274">(Může být jenom jeden.)</span><span class="sxs-lookup"><span data-stu-id="8280f-274">(It may be the only one.)</span></span>

<span data-ttu-id="8280f-275">Otevřete prohlížeč a přejděte na místního hostitele a určující zeměpisnou šířku a délku můžete otestovat vaši službu:</span><span class="sxs-lookup"><span data-stu-id="8280f-275">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="8280f-276">Připojení ke spuštěnému kontejneru</span><span class="sxs-lookup"><span data-stu-id="8280f-276">Attaching to a running container</span></span>

<span data-ttu-id="8280f-277">Při spuštění služby v příkazovém okně zobrazí diagnostické informace, které jsou zobrazeny pro každý požadavek.</span><span class="sxs-lookup"><span data-stu-id="8280f-277">When you ran your service in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="8280f-278">Tyto informace nevidíte, když je váš kontejner spuštěný v režimu odpojení.</span><span class="sxs-lookup"><span data-stu-id="8280f-278">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="8280f-279">Příkaz připojit Dockeru umožňuje připojení k spuštěný kontejner, kde můžete zobrazit informace protokolu.</span><span class="sxs-lookup"><span data-stu-id="8280f-279">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="8280f-280">Spuštěním tohoto příkazu z příkazového okna:</span><span class="sxs-lookup"><span data-stu-id="8280f-280">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="8280f-281">`--sig-proxy=false` Argument znamená, že <kbd>Ctrl</kbd>+<kbd>C</kbd> příkazy získat neodesílají se do kontejneru procesu, ale spíše Zastavit `docker attach` příkazu.</span><span class="sxs-lookup"><span data-stu-id="8280f-281">The `--sig-proxy=false` argument means that <kbd>Ctrl</kbd>+<kbd>C</kbd> commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="8280f-282">Konečný argument je daný název kontejneru v `docker run` příkazu.</span><span class="sxs-lookup"><span data-stu-id="8280f-282">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="8280f-283">Přiřazené ID kontejneru Dockeru můžete použít také k odkazování na kterýkoli kontejner.</span><span class="sxs-lookup"><span data-stu-id="8280f-283">You can also use the Docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="8280f-284">Pokud jste nezadali název kontejneru v `docker run` je nutné použít ID kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8280f-284">If you didn't specify a name for your container in `docker run` you must use the container ID.</span></span>

<span data-ttu-id="8280f-285">Otevřete prohlížeč a přejděte k vaší službě.</span><span class="sxs-lookup"><span data-stu-id="8280f-285">Open a browser and navigate to your service.</span></span> <span data-ttu-id="8280f-286">Zobrazí se vám diagnostické zprávy v okně příkazového řádku z připojených spuštěný kontejner.</span><span class="sxs-lookup"><span data-stu-id="8280f-286">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="8280f-287">Stisknutím klávesy <kbd>Ctrl</kbd>+<kbd>C</kbd> zastavte sledovací proces připojení.</span><span class="sxs-lookup"><span data-stu-id="8280f-287">Press <kbd>Ctrl</kbd>+<kbd>C</kbd> to stop the attach process.</span></span>

<span data-ttu-id="8280f-288">Po dokončení práce s kontejneru, můžete ho zastavit:</span><span class="sxs-lookup"><span data-stu-id="8280f-288">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="8280f-289">Kontejner a image je stále k dispozici pro restartování.</span><span class="sxs-lookup"><span data-stu-id="8280f-289">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="8280f-290">Pokud chcete odebrat kontejner ze svého počítače, použijte tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="8280f-290">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="8280f-291">Pokud chcete odebrat z počítače nepoužívané Image, použijte tento příkaz:</span><span class="sxs-lookup"><span data-stu-id="8280f-291">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="8280f-292">Závěr</span><span class="sxs-lookup"><span data-stu-id="8280f-292">Conclusion</span></span> 

<span data-ttu-id="8280f-293">V tomto kurzu založená mikroslužbách ASP.NET Core a přidá několik jednoduchých funkcí.</span><span class="sxs-lookup"><span data-stu-id="8280f-293">In this tutorial, you built an ASP.NET Core microservice, and added a few simple features.</span></span>

<span data-ttu-id="8280f-294">Sestavili image kontejneru pro tuto službu Docker a spuštění kontejneru na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="8280f-294">You built a Docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="8280f-295">Okno terminálu připojen ke službě a viděli diagnostické zprávy z vaší služby.</span><span class="sxs-lookup"><span data-stu-id="8280f-295">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="8280f-296">Na cestě jste viděli některé funkce služby C# jazyk v akci.</span><span class="sxs-lookup"><span data-stu-id="8280f-296">Along the way, you saw several features of the C# language in action.</span></span>
