---
title: Vytvoření klienta REST s využitím .NET Core
description: V tomto kurzu se naučíte mnoho funkcí v jazyce C# a .NET Core.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 13466b717d0676c2db5edf4c98a4ead3e673b96c
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47397917"
---
# <a name="rest-client"></a><span data-ttu-id="cdf8e-103">Klient REST</span><span class="sxs-lookup"><span data-stu-id="cdf8e-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="cdf8e-104">Úvod</span><span class="sxs-lookup"><span data-stu-id="cdf8e-104">Introduction</span></span>
<span data-ttu-id="cdf8e-105">V tomto kurzu se naučíte mnoho funkcí v jazyce C# a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="cdf8e-106">Získáte informace:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-106">You’ll learn:</span></span>
*   <span data-ttu-id="cdf8e-107">Základní informace o .NET Core rozhraní příkazového řádku (CLI).</span><span class="sxs-lookup"><span data-stu-id="cdf8e-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
*   <span data-ttu-id="cdf8e-108">Přehled funkcí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-108">An overview of C# Language features.</span></span>
*   <span data-ttu-id="cdf8e-109">Správa závislostí nuget</span><span class="sxs-lookup"><span data-stu-id="cdf8e-109">Managing dependencies with NuGet</span></span>
*   <span data-ttu-id="cdf8e-110">Komunikace protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="cdf8e-110">HTTP Communications</span></span>
*   <span data-ttu-id="cdf8e-111">Informace o zpracování JSON</span><span class="sxs-lookup"><span data-stu-id="cdf8e-111">Processing JSON information</span></span>
*   <span data-ttu-id="cdf8e-112">Správa konfigurace s atributy.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-112">Managing configuration with Attributes.</span></span> 

<span data-ttu-id="cdf8e-113">Vytvoříte aplikaci, která vydává požadavků HTTP pro službu REST na Githubu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="cdf8e-114">Budete číst informace ve formátu JSON a převést paketu JSON na objekty jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="cdf8e-115">Nakonec uvidíte, jak pracovat s objekty jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="cdf8e-116">Existuje mnoho funkcí v tomto kurzu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="cdf8e-117">Vytvořme je jeden po druhém.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-117">Let’s build them one by one.</span></span>

<span data-ttu-id="cdf8e-118">Pokud chcete postupovat podle [konečný vzorek](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) pro toto téma, můžete ji stáhnout.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="cdf8e-119">Pokyny ke stažení najdete v tématu [ukázek a kurzů](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="cdf8e-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cdf8e-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cdf8e-120">Prerequisites</span></span>
<span data-ttu-id="cdf8e-121">Budete muset nastavit počítač pro spuštění .NET core.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="cdf8e-122">Můžete najít pokyny k instalaci na [.NET Core](https://www.microsoft.com/net/core) stránky.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-122">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="cdf8e-123">Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="cdf8e-124">Bude potřeba nainstalovat váš oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="cdf8e-125">Popisy níže použití [Visual Studio Code](https://code.visualstudio.com/), což je open source pro různé platformy editoru.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="cdf8e-126">Ale můžete použít jakýkoli nástroje jste obeznámeni.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-126">However, you can use whatever tools you are comfortable with.</span></span>
## <a name="create-the-application"></a><span data-ttu-id="cdf8e-127">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="cdf8e-127">Create the Application</span></span>
<span data-ttu-id="cdf8e-128">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-128">The first step is to create a new application.</span></span> <span data-ttu-id="cdf8e-129">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="cdf8e-130">Ujistěte se, že do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-130">Make that the current directory.</span></span> <span data-ttu-id="cdf8e-131">Zadejte příkaz `dotnet new console` příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="cdf8e-132">Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".</span><span class="sxs-lookup"><span data-stu-id="cdf8e-132">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="cdf8e-133">Než začnete, úpravy, Podívejme se kroky ke spuštění jednoduché aplikace Hello World.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-133">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="cdf8e-134">Po vytvoření aplikace, zadejte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-134">After creating the application, type `dotnet restore` ([see note](#dotnet-restore-note)) at the command prompt.</span></span> <span data-ttu-id="cdf8e-135">Tento příkaz spustí proces obnovení balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-135">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="cdf8e-136">Správce balíčků NuGet je Správce balíčků .NET.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-136">NuGet is a .NET package manager.</span></span> <span data-ttu-id="cdf8e-137">Tento příkaz načte všechny chybějící závislosti pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-137">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="cdf8e-138">Toto je nový projekt, závislosti nejsou v místě, tak při prvním spuštění se stáhnout .NET Core framework.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-138">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="cdf8e-139">Po provedení tohoto kroku počáteční je pouze potřeba spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) při přidání nové závislé balíčky nebo aktualizace verze závislosti.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-139">After this initial step, you will only need to run `dotnet restore` ([see note](#dotnet-restore-note)) when you add new dependent packages, or update the versions of any of your dependencies.</span></span>  

<span data-ttu-id="cdf8e-140">Po obnovení balíčků, spustíte `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-140">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="cdf8e-141">To spustí modul sestavení a vytvoří vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-141">This executes the build engine and creates your application.</span></span> <span data-ttu-id="cdf8e-142">Nakonec spuštěním `dotnet run` ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-142">Finally, you execute `dotnet run` to run your application.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="cdf8e-143">Přidání nové závislosti</span><span class="sxs-lookup"><span data-stu-id="cdf8e-143">Adding New Dependencies</span></span>
<span data-ttu-id="cdf8e-144">Jedním z hlavních cílů pro .NET Core je minimální velikost instalace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-144">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="cdf8e-145">Pokud aplikace potřebuje další knihovny pro některé z jejích funkcí, přidejte tyto závislosti do projektu C# (\*.csproj) souboru.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-145">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="cdf8e-146">V našem příkladu bude potřeba přidat `System.Runtime.Serialization.Json` balíček, vaše aplikace dokáže zpracovat odpověďmi ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-146">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="cdf8e-147">Otevřete váš `csproj` souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-147">Open your `csproj` project file.</span></span> <span data-ttu-id="cdf8e-148">První řádek souboru by měl vypadat jako:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-148">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="cdf8e-149">Přidejte následující ihned po tomto řádku:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-149">Add the following immediately after this line:</span></span> 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
<span data-ttu-id="cdf8e-150">Většina editory kódu bude poskytovat dokončování pro různé verze knihoven.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-150">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="cdf8e-151">Obvykle budete chtít používat nejnovější verzi balíčku, který přidáte.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-151">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="cdf8e-152">Je důležité, abyste měli jistotu, že odpovídají verze všechny balíčky a aby splňovaly verzi rozhraní framework aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-152">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="cdf8e-153">Po provedení těchto změn, měli byste spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) znovu tak, aby se balíček nainstaluje do systému.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-153">After you've made these changes, you should run `dotnet restore` ([see note](#dotnet-restore-note)) again so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="cdf8e-154">Vytváření webových požadavků</span><span class="sxs-lookup"><span data-stu-id="cdf8e-154">Making Web Requests</span></span>
<span data-ttu-id="cdf8e-155">Teď jste připravení začít, načítání dat z webu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-155">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="cdf8e-156">V této aplikaci, nemusíte se věnovat čtení informací z [rozhraní API Githubu](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="cdf8e-156">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="cdf8e-157">Načteme informace o projektech v rámci [.NET Foundation](http://www.dotnetfoundation.org/) zastřešující.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-157">Let's read information about the projects under the [.NET Foundation](http://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="cdf8e-158">Začnete tím, že požadavek na rozhraní API Githubu k načtení informací o projektech.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-158">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="cdf8e-159">Koncový bod, který budete používat: [ https://api.github.com/orgs/dotnet/repos ](https://api.github.com/orgs/dotnet/repos).</span><span class="sxs-lookup"><span data-stu-id="cdf8e-159">The endpoint you'll use is: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos).</span></span> <span data-ttu-id="cdf8e-160">Budete chtít získat všechny informace o těchto projektů, takže budete používat požadavek HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-160">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="cdf8e-161">Váš prohlížeč také používá HTTP GET požadavky, takže vložíte je, že adresy URL do prohlížeče informací vám bude přijímat a zpracování.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-161">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="cdf8e-162">Můžete použít <xref:System.Net.Http.HttpClient> třídy k vytvoření webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-162">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="cdf8e-163">Všechny moderní rozhraní .NET API, jako jsou <xref:System.Net.Http.HttpClient> podporuje pouze asynchronní metody pro jeho dlouho běžící rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-163">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="cdf8e-164">Začněte tím, že asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-164">Start by making an async method.</span></span> <span data-ttu-id="cdf8e-165">Implementace budete vyplňte během vytváření funkce aplikace.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-165">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="cdf8e-166">Začněte otevřením `program.cs` souborů v adresáři projektu a přidáním následující metodu do `Program` třídy:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-166">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    
}
```

<span data-ttu-id="cdf8e-167">Budete muset přidat `using` příkazu v horní části vaší `Main` metoda tak, aby kompilátor jazyka C# rozpozná <xref:System.Threading.Tasks.Task> typu:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-167">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="cdf8e-168">V tomto okamžiku sestavení projektu získáte upozornění vygenerované pro tuto metodu, protože neobsahuje žádný `await` operátory a spustí se synchronně.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-168">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="cdf8e-169">Ignorovat, který teď; přidáte `await` operátory při vyplňte metodu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-169">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="cdf8e-170">V dalším kroku přejmenujte obor názvů definovaný v `namespace` příkaz z výchozí hodnoty `ConsoleApp` k `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-170">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="cdf8e-171">Budeme dále definovat `repo` třídy v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-171">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="cdf8e-172">Dále, aktualizujte `Main` metoda k volání této metody.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-172">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="cdf8e-173">`ProcessRepositories` Metoda vrátí úkol a by neměl ukončete program před dokončením tohoto úkolu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-173">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="cdf8e-174">Proto je nutné použít `Wait` metoda blokovat a počkejte na dokončení úlohy:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-174">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="cdf8e-175">Teď máte program, který nemá žádný účinek, ale nemá asynchronně.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-175">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="cdf8e-176">Ho můžeme vylepšit.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-176">Let's improve it.</span></span>

<span data-ttu-id="cdf8e-177">Nejdřív je potřeba objekt, který je schopen načíst data z webu; můžete použít <xref:System.Net.Http.HttpClient> to udělat.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-177">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="cdf8e-178">Tento objekt zpracovává žádosti a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-178">This object handles the request and the responses.</span></span> <span data-ttu-id="cdf8e-179">Vytvořte instanci jedné instance daného typu v `Program` třída v souboru Program.cs.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-179">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static void Main(string[] args)
        {
            //...
        }
    }
}
```

 <span data-ttu-id="cdf8e-180">Vraťme se k `ProcessRepositories` metoda a vyplňte první verzi:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-180">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

<span data-ttu-id="cdf8e-181">Musíte také přidejte dva nové příkazy using v horní části souboru pro tuto kompilace:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-181">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="cdf8e-182">Tato první verze díky webový požadavek na čtení seznamu všechna úložiště v rámci organizace foundation dotnet.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-182">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="cdf8e-183">(ID Githubu pro .NET Foundation je "dotnet").</span><span class="sxs-lookup"><span data-stu-id="cdf8e-183">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="cdf8e-184">Nastavit několik prvních řádků <xref:System.Net.Http.HttpClient> pro tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-184">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="cdf8e-185">Nejprve je nakonfigurován tak, aby přijímal odpověďmi ve formátu JSON Githubu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-185">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="cdf8e-186">Tento formát je jednoduše JSON.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-186">This format is simply JSON.</span></span> <span data-ttu-id="cdf8e-187">Další řádek přidá hlavičku uživatelského agenta na všechny požadavky z tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-187">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="cdf8e-188">Tyto dvě záhlaví jsou kontrolovány v kódu serveru Githubu a jsou nezbytné k načtení informací z Githubu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-188">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="cdf8e-189">Po dokončení konfigurace <xref:System.Net.Http.HttpClient>, provedete webové žádosti a načíst odpovědi.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-189">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="cdf8e-190">V této první verzi, můžete použít <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> metoda pohodlí.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-190">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="cdf8e-191">Tato metoda pohodlí spustí úlohu, která provádí na webový požadavek, a potom po návratu požadavek načte datový proud odpovědí a extrahuje obsah z datového proudu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-191">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="cdf8e-192">Text odpovědi se vrátí jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-192">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="cdf8e-193">Řetězec je k dispozici po dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-193">The string is available when the task completes.</span></span> 

<span data-ttu-id="cdf8e-194">Poslední dva řádky této metody await tento úkol a pak vytiskněte odpovědi do konzoly.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-194">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="cdf8e-195">Sestavení aplikace a spustíme ji.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-195">Build the app, and run it.</span></span> <span data-ttu-id="cdf8e-196">Upozornění sestavení je pryč nyní, protože `ProcessRepositories` teď obsahují `await` operátor.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-196">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="cdf8e-197">Uvidíte, že se že jedná o dlouho zobrazení JSON formátovaného textu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-197">You'll see a long display of JSON formatted text.</span></span>   

## <a name="processing-the-json-result"></a><span data-ttu-id="cdf8e-198">Zpracování výsledku JSON</span><span class="sxs-lookup"><span data-stu-id="cdf8e-198">Processing the JSON Result</span></span>

<span data-ttu-id="cdf8e-199">V tomto okamžiku jste napsali kód k načtení odpověď z webového serveru a zobrazení text, který je obsažen v této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-199">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="cdf8e-200">V dalším kroku můžeme převést tuto odpověď JSON na objekty jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-200">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="cdf8e-201">Serializátor JSON převádí JSON data na objekty jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-201">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="cdf8e-202">První úloha je definice typu třídy C# obsahuje informace, které můžete použít z této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-202">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="cdf8e-203">Vytvořme tomto pomalu, takže začínat jednoduchý typ jazyka C#, který obsahuje název úložiště:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-203">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class repo
    {
        public string name;
    }
}
``` 

<span data-ttu-id="cdf8e-204">Výše uvedený kód umístěte do nového souboru s názvem "repo.cs".</span><span class="sxs-lookup"><span data-stu-id="cdf8e-204">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="cdf8e-205">Tato verze třídy představuje nejjednodušší způsob zpracování dat JSON.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-205">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="cdf8e-206">Název třídy a název člena shodovat s názvy používanými v paketu JSON, namísto následující převody C#.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-206">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="cdf8e-207">Opravíte to tím, že poskytuje některé atributy konfigurace později.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-207">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="cdf8e-208">Tato třída ukazuje další důležitou funkcí JSON serializace a deserializace: všechna pole v paketu JSON jsou součástí této třídy.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-208">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="cdf8e-209">Serializátor JSON bude ignorovat informace, které není součástí typu třídy se používají.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-209">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="cdf8e-210">Tato funkce usnadňuje vytváření typů, které pracují s pouze podmnožinu polí v paketu JSON.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-210">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="cdf8e-211">Teď, když jste vytvořili typ, Pojďme deserializovat.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-211">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="cdf8e-212">Budete muset vytvořit <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> objektu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-212">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="cdf8e-213">Tento objekt musíte znát očekávaný typ CLR pro paket JSON ho načte.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-213">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="cdf8e-214">Paket z Githubu obsahuje posloupnost úložiště, takže `List<repo>` je nesprávného typu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-214">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="cdf8e-215">Přidejte následující řádek, který vaše `ProcessRepositories` metody:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-215">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="cdf8e-216">Používáte dva nové obory názvů, takže budete muset přidat ty také:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-216">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="cdf8e-217">V dalším kroku použijete serializátoru, který můžete převést JSON na objekty jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-217">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="cdf8e-218">Nahraďte volání <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> ve vašich `ProcessRepositories` metoda s následujícími dvěma řádky:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-218">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="cdf8e-219">Všimněte si, že teď používáte <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> místo <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-219">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="cdf8e-220">Serializátoru, který používá jako zdroj datového proudu namísto řetězce.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-220">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="cdf8e-221">Pojďme vysvětlují několik funkcí jazyka C#, která se používají v druhý řádek výše.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-221">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="cdf8e-222">Argument <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> je `await` výrazu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-222">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="cdf8e-223">Operátor await výrazy se mohou objevit skoro kdekoli v kódu, i když až doteď jste viděli pouze jejich jako součást příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-223">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="cdf8e-224">Za druhé `as` operátor převede typ času kompilace `object` k `List<repo>`.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-224">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span> <span data-ttu-id="cdf8e-225">Deklarace <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> deklaruje, že vrátí objekt typu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-225">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cdf8e-226"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> Vrátí typ, který jste zadali při jeho vytvořený (`List<repo>` v tomto kurzu).</span><span class="sxs-lookup"><span data-stu-id="cdf8e-226"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="cdf8e-227">Pokud převod selže, `as` vyhodnotí jako operátor `null`, namísto vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-227">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="cdf8e-228">Téměř dokončení této části.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-228">You're almost done with this section.</span></span> <span data-ttu-id="cdf8e-229">Teď, když jste převést JSON na objekty jazyka C#, Pojďme zobrazovaný název každého úložiště.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-229">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="cdf8e-230">Nahraďte řádky, které čtou:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-230">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="cdf8e-231">následující:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-231">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="cdf8e-232">Kompilace a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-232">Compile and run the application.</span></span> <span data-ttu-id="cdf8e-233">Vytiskne názvy úložišť, které jsou součástí .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-233">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="cdf8e-234">Řízení serializace</span><span class="sxs-lookup"><span data-stu-id="cdf8e-234">Controlling Serialization</span></span>

<span data-ttu-id="cdf8e-235">Předtím, než přidáte další funkce, Pojďme adres `repo` typ a nastavte ji více standard jazyka C# pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-235">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="cdf8e-236">Provedete to anotací `repo` typ s *atributy* , které řídí, jak funguje serializátor JSON.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-236">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="cdf8e-237">Ve vašem případě použijete tyto atributy definovat mapování mezi názvy klíčů JSON a C# názvy tříd a členů.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-237">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="cdf8e-238">Jsou dva atributy použité `DataContract` atribut a `DataMember` atribut.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-238">The two attributes used are the `DataContract` attribute and the `DataMember` attribute.</span></span> <span data-ttu-id="cdf8e-239">Podle konvence, všechny třídy atributu končit příponou `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-239">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="cdf8e-240">Ale není potřeba použít tuto příponu při použití atributu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-240">However, you do not need to use that suffix when you apply an attribute.</span></span> 

<span data-ttu-id="cdf8e-241">`DataContract` a `DataMember` atributy jsou v jiné knihovny, takže budete muset přidat tuto knihovnu do souboru projektu C# jako závislost.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-241">The `DataContract` and `DataMember` attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="cdf8e-242">Přidejte následující řádek, který `<ItemGroup>` část souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-242">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="cdf8e-243">Až soubor uložíte, spusťte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) pro načtení tohoto balíčku.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-243">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="cdf8e-244">Dále otevřete `repo.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-244">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="cdf8e-245">Umožňuje změnit název Pascalcase a plně pravopisu jméno `Repository`.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-245">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="cdf8e-246">Chceme mapují JSON "úložiště" uzly k tomuto typu, takže budete muset přidat `DataContract` atribut deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-246">We still want to map JSON 'repo' nodes to this type, so you'll need to add the `DataContract` attribute to the class declaration.</span></span> <span data-ttu-id="cdf8e-247">Nastavíte `Name` vlastnost atributu název JSON uzly, které se mapují k tomuto typu:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-247">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="cdf8e-248"><xref:System.Runtime.Serialization.DataContractAttribute> Je členem skupiny <xref:System.Runtime.Serialization> obor názvů, takže budete muset přidat příslušné `using` příkazu v horní části souboru:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-248">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="cdf8e-249">Změnili jste název `repo` třídu `Repository`, takže budete muset vytvořit stejný název změnit v souboru Program.cs (Některé editory mohou podporovat refaktoring pro přejmenování, která bude tuto změnu provést automaticky:)</span><span class="sxs-lookup"><span data-stu-id="cdf8e-249">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="cdf8e-250">V dalším kroku vytvoříme stejnou změnu s `name` pole, a to pomocí <xref:System.Runtime.Serialization.DataMemberAttribute> třídy.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-250">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="cdf8e-251">Proveďte následující změny k deklaraci `name` repo.cs pole:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-251">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="cdf8e-252">Tato změna znamená, že budete muset změnit kód, který zapíše název každého úložiště v souboru program.cs:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-252">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="cdf8e-253">Proveďte `dotnet build` následovaný `dotnet run` k Ujistěte se, že máte mapování správné.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-253">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="cdf8e-254">Měli byste vidět stejný výstup jako před.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-254">You should see the same output as before.</span></span> <span data-ttu-id="cdf8e-255">Předtím, než zpracujeme více vlastností z webového serveru, vytvoříme jednu další změnu `Repository` třídy.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-255">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="cdf8e-256">`Name` Člen je veřejně dostupná pole.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-256">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="cdf8e-257">Není vhodné objektově orientované, můžeme ho změnit na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-257">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="cdf8e-258">Pro naše účely nepotřebujeme žádné konkrétní spuštění kódu při načtení nebo nastavení vlastnosti, ale změna vlastnosti usnadňuje později přidat tyto změny bez narušení veškerý kód, který se používá `Repository` třídy.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-258">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="cdf8e-259">Odebrat definici pole a nahraďte ho hodnotou [automaticky implementované vlastnosti](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span><span class="sxs-lookup"><span data-stu-id="cdf8e-259">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="cdf8e-260">Kompilátor generuje text `get` a `set` přístupové objekty, stejně jako soukromé pole pro uložení názvu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-260">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="cdf8e-261">By měl vypadat přibližně následující kód, který můžete ručně zadat:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-261">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="cdf8e-262">Vytvoříme jednu další změnu před přidáním nových funkcí.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-262">Let's make one more change before adding new features.</span></span> <span data-ttu-id="cdf8e-263">`ProcessRepositories` Metoda umí asynchronní práce a vrátí kolekci úložišť.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-263">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="cdf8e-264">Vraťme `List<Repository>` z této metody a přesuňte kód, který zapisuje informace do `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-264">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="cdf8e-265">Změna podpisu `ProcessRepositories` vrátit úlohu, jehož výsledkem je seznam z `Repository` objekty:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-265">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="cdf8e-266">Pak se jenom vrátit úložiště po zpracování odpověď JSON:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-266">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="cdf8e-267">Kompilátor vygeneruje `Task<T>` objektu pro vrácení, protože jste označili jako tato metoda `async`.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-267">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="cdf8e-268">Potom Pojďme upravit `Main` metoda tak se zaznamená ty výsledky a název každého úložiště zapisuje do konzoly.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-268">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="cdf8e-269">Vaše `Main` metoda nyní vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-269">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="cdf8e-270">Přístup k `Result` vlastnost úlohy blokuje, dokud není úloha dokončena.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-270">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="cdf8e-271">Za normálních okolností si přejete `await` úlohy, jako v `ProcessRepositories` metody, ale to není povoleno v `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-271">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="cdf8e-272">Další informace pro čtení</span><span class="sxs-lookup"><span data-stu-id="cdf8e-272">Reading More Information</span></span>

<span data-ttu-id="cdf8e-273">Pojďme to dokončete tak, že zpracování několik dalších vlastností v JSON paket načte odeslaný z rozhraní API Githubu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-273">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="cdf8e-274">Si nebudete chtít získejte všechno, ale přidává několik vlastností vám předvede několik více funkcí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-274">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="cdf8e-275">Začněme přidáním další pár jednoduchých typů k `Repository` definici třídy.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-275">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="cdf8e-276">Přidejte tyto vlastnosti třídy:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-276">Add these properties to that class:</span></span>

```csharp
[DataMember(Name="description")]
public string Description { get; set; }

[DataMember(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[DataMember(Name="homepage")]
public Uri Homepage { get; set; }

[DataMember(Name="watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="cdf8e-277">Tyto vlastnosti mají integrovanou převody z typu řetězec (což je, co obsahují pakety JSON) do cílového typu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-277">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="cdf8e-278"><xref:System.Uri> Typ může být pro vás nová.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-278">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="cdf8e-279">Představuje identifikátor URI, nebo v tomto případě adresy URL.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-279">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="cdf8e-280">V případě třídy `Uri` a `int` typy, pokud je paket JSON obsahuje data, která nejde převést na cílový typ., Serializační akce vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-280">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="cdf8e-281">Jakmile přidáte tyto aktualizace `Main` metodu pro zobrazení těchto prvků:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-281">Once you've added these, update the `Main` method to display those elements:</span></span>

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```
<span data-ttu-id="cdf8e-282">V posledním kroku Pojďme přidat informace o poslední operaci push.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-282">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="cdf8e-283">Tyto informace je ve formátu tímto způsobem v odpovědi JSON:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-283">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="cdf8e-284">Tento formát nedodržuje některé standardní .NET <xref:System.DateTime> formátů.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-284">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="cdf8e-285">Proto musíte napsat vlastní převod metodu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-285">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="cdf8e-286">Nejspíš taky budete nechcete nezpracovaného řetězce vystavené pro uživatele `Repository` třídy.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-286">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="cdf8e-287">Ovládací prvek, který také může pomoct atributy.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-287">Attributes can help control that as well.</span></span> <span data-ttu-id="cdf8e-288">Nejprve definujte `private` vlastnost, která bude obsahovat řetězcovou reprezentaci data času ve vaší `Repository` třídy:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-288">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="cdf8e-289">`DataMember` Atribut informuje serializátoru, který je, že to má být zpracován, i když není veřejný člen.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-289">The `DataMember` attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="cdf8e-290">Dále je třeba napsat veřejnou vlastnost jen pro čtení, která převede řetězec na platnou <xref:System.DateTime> objekt a vrátí ji <xref:System.DateTime>:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-290">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

```csharp
[IgnoreDataMember]
public DateTime LastPush
{
    get
    {
        return DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
    }
}
```

<span data-ttu-id="cdf8e-291">Probereme si nové konstruktory výše.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-291">Let's go over the new constructs above.</span></span> <span data-ttu-id="cdf8e-292">`IgnoreDataMember` Atribut nastaví serializátor, že tento typ by neměly být ke čtení nebo zapisovat z libovolného objektu JSON.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-292">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="cdf8e-293">Tato vlastnost obsahuje pouze `get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-293">This property contains only a `get` accessor.</span></span> <span data-ttu-id="cdf8e-294">Neexistuje žádná `set` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-294">There is no `set` accessor.</span></span> <span data-ttu-id="cdf8e-295">To je, jak definovat *jen pro čtení* vlastností v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-295">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="cdf8e-296">(Ano, můžete vytvořit *jen pro zápis* vlastností v jazyce C#, ale jejich hodnota je omezený.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Metoda analyzuje řetězec a vytvoří <xref:System.DateTime> pomocí formátu zadané datum a přidá další metadata, aby `DateTime` pomocí `CultureInfo` objektu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-296">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="cdf8e-297">Přistupující objekt vlastnosti vyvolá výjimku, pokud se nezdaří operace analýzy.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-297">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="cdf8e-298">Použití <xref:System.Globalization.CultureInfo.InvariantCulture>, budete muset přidat <xref:System.Globalization> obor názvů, aby `using` příkazů v `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-298">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="cdf8e-299">Nakonec přidejte jednu výstupní více příkazu v konzole, a budete připraveni k sestavení a znovu spusťte tuto aplikaci:</span><span class="sxs-lookup"><span data-stu-id="cdf8e-299">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="cdf8e-300">Vaše verze by měla odpovídat nyní [dokončení ukázkové](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="cdf8e-300">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>
 
## <a name="conclusion"></a><span data-ttu-id="cdf8e-301">Závěr</span><span class="sxs-lookup"><span data-stu-id="cdf8e-301">Conclusion</span></span>

<span data-ttu-id="cdf8e-302">Tento kurz vám ukázal vytvoření webových požadavků, výsledek analyzovat a zobrazovat vlastnosti těchto výsledků.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-302">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="cdf8e-303">Jste také přidali nové balíčky jako závislosti ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-303">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="cdf8e-304">Jste viděli některé z funkcí jazyka C# podporující objektově orientované techniky.</span><span class="sxs-lookup"><span data-stu-id="cdf8e-304">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
