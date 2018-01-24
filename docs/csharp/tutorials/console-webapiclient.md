---
title: "Vytvoření klienta REST pomocí .NET Core"
description: "V tomto kurzu se dozvíte, jaké celou řadu funkcí v .NET Core a jazyka C#."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 6b0f3acc3a6dbed4f44497d92d3c518ee5a5d2a7
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2018
---
# <a name="rest-client"></a><span data-ttu-id="356e5-104">Klienta REST</span><span class="sxs-lookup"><span data-stu-id="356e5-104">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="356e5-105">Úvod</span><span class="sxs-lookup"><span data-stu-id="356e5-105">Introduction</span></span>
<span data-ttu-id="356e5-106">V tomto kurzu se dozvíte, jaké celou řadu funkcí v .NET Core a jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="356e5-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="356e5-107">Naučíte:</span><span class="sxs-lookup"><span data-stu-id="356e5-107">You’ll learn:</span></span>
*   <span data-ttu-id="356e5-108">Základy .NET Core rozhraní příkazového řádku (CLI).</span><span class="sxs-lookup"><span data-stu-id="356e5-108">The basics of the .NET Core Command Line Interface (CLI).</span></span>
*   <span data-ttu-id="356e5-109">Přehled funkcí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="356e5-109">An overview of C# Language features.</span></span>
*   <span data-ttu-id="356e5-110">Správa závislostí s NuGet</span><span class="sxs-lookup"><span data-stu-id="356e5-110">Managing dependencies with NuGet</span></span>
*   <span data-ttu-id="356e5-111">Komunikace HTTP</span><span class="sxs-lookup"><span data-stu-id="356e5-111">HTTP Communications</span></span>
*   <span data-ttu-id="356e5-112">Informace o zpracování JSON</span><span class="sxs-lookup"><span data-stu-id="356e5-112">Processing JSON information</span></span>
*   <span data-ttu-id="356e5-113">Správa konfigurací s atributy.</span><span class="sxs-lookup"><span data-stu-id="356e5-113">Managing configuration with Attributes.</span></span> 

<span data-ttu-id="356e5-114">Budete sestavit aplikaci, která vydává požadavků HTTP pro službu REST na Githubu.</span><span class="sxs-lookup"><span data-stu-id="356e5-114">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="356e5-115">Budete přečtěte si informace ve formátu JSON a převést paketu JSON na objekty C#.</span><span class="sxs-lookup"><span data-stu-id="356e5-115">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="356e5-116">Nakonec uvidíte, jak pracovat s objekty jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="356e5-116">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="356e5-117">V tomto kurzu je celá řada funkcí.</span><span class="sxs-lookup"><span data-stu-id="356e5-117">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="356e5-118">Umožňuje vytvořit, je po jednom.</span><span class="sxs-lookup"><span data-stu-id="356e5-118">Let’s build them one by one.</span></span>

<span data-ttu-id="356e5-119">Pokud dáváte přednost použijte spolu s [konečný vzorek](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient) pro toto téma, můžete ho stáhnout.</span><span class="sxs-lookup"><span data-stu-id="356e5-119">If you prefer to follow along with the [final sample](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="356e5-120">Pokyny ke stažení najdete v tématu [ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="356e5-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="356e5-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="356e5-121">Prerequisites</span></span>
<span data-ttu-id="356e5-122">Budete muset nastavit svůj počítač ke spuštění .NET core.</span><span class="sxs-lookup"><span data-stu-id="356e5-122">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="356e5-123">Pokyny k instalaci najdete na [.NET Core](https://www.microsoft.com/net/core) stránky.</span><span class="sxs-lookup"><span data-stu-id="356e5-123">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="356e5-124">Tuto aplikaci můžete spustit v systému Windows, Linux, systému macOS nebo v kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="356e5-124">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="356e5-125">Budete muset nainstalovat editor vaše oblíbené kódu.</span><span class="sxs-lookup"><span data-stu-id="356e5-125">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="356e5-126">Popisy níže použijte [Visual Studio Code](https://code.visualstudio.com/), který je typu open source pro různé platformy editor.</span><span class="sxs-lookup"><span data-stu-id="356e5-126">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="356e5-127">Můžete však použít, ať nástroje umíte pracovat s.</span><span class="sxs-lookup"><span data-stu-id="356e5-127">However, you can use whatever tools you are comfortable with.</span></span>
## <a name="create-the-application"></a><span data-ttu-id="356e5-128">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="356e5-128">Create the Application</span></span>
<span data-ttu-id="356e5-129">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="356e5-129">The first step is to create a new application.</span></span> <span data-ttu-id="356e5-130">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="356e5-130">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="356e5-131">Nastavit aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="356e5-131">Make that the current directory.</span></span> <span data-ttu-id="356e5-132">Zadejte příkaz `dotnet new console` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="356e5-132">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="356e5-133">Tím se vytvoří počáteční soubory pro základní aplikace "Hello World".</span><span class="sxs-lookup"><span data-stu-id="356e5-133">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="356e5-134">Než začnete, provádění změn, přejděte přes kroky a spusťte tak jednoduchou aplikaci Hello World.</span><span class="sxs-lookup"><span data-stu-id="356e5-134">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="356e5-135">Po vytvoření aplikace, zadejte `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="356e5-135">After creating the application, type `dotnet restore` ([see note](#dotnet-restore-note)) at the command prompt.</span></span> <span data-ttu-id="356e5-136">Tento příkaz spustí proces obnovení balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="356e5-136">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="356e5-137">NuGet je Správce balíčků .NET.</span><span class="sxs-lookup"><span data-stu-id="356e5-137">NuGet is a .NET package manager.</span></span> <span data-ttu-id="356e5-138">Tento příkaz stáhne všechny chybějící závislosti pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="356e5-138">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="356e5-139">Toto je nový projekt, žádné závislosti na místě, se tak během prvního spuštění stáhnou rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="356e5-139">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="356e5-140">Po provedení tohoto kroku počáteční se jenom musíte spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) při přidání nové závislé balíčky nebo aktualizace verze všechny svoje závislosti.</span><span class="sxs-lookup"><span data-stu-id="356e5-140">After this initial step, you will only need to run `dotnet restore` ([see note](#dotnet-restore-note)) when you add new dependent packages, or update the versions of any of your dependencies.</span></span>  

<span data-ttu-id="356e5-141">Po obnovení balíčků, můžete spustit `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="356e5-141">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="356e5-142">To provede modul sestavení a vytvoří vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="356e5-142">This executes the build engine and creates your application.</span></span> <span data-ttu-id="356e5-143">Nakonec spuštěním `dotnet run` spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="356e5-143">Finally, you execute `dotnet run` to run your application.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="356e5-144">Přidání nové závislosti</span><span class="sxs-lookup"><span data-stu-id="356e5-144">Adding New Dependencies</span></span>
<span data-ttu-id="356e5-145">Jedním z hlavních cílů aplikace .NET Core je minimální velikost instalace rozhraní .NET framework.</span><span class="sxs-lookup"><span data-stu-id="356e5-145">One of the key design goals for .NET Core is to minimize the size of the .NET framework installation.</span></span> <span data-ttu-id="356e5-146">Rozhraní .NET Core obsahuje pouze běžných prvků úplné rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="356e5-146">The .NET Core Application framework contains only the most common elements of the .NET full framework.</span></span> <span data-ttu-id="356e5-147">Pokud aplikace potřebuje další knihovny pro některé jeho funkce, přidejte tyto závislosti do projektu C# (\*.csproj) souboru.</span><span class="sxs-lookup"><span data-stu-id="356e5-147">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="356e5-148">Pro náš příklad, budete muset přidat `System.Runtime.Serialization.Json` balíčku, vaše aplikace může zpracovat odpovědi JSON.</span><span class="sxs-lookup"><span data-stu-id="356e5-148">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="356e5-149">Otevřete váš `csproj` souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="356e5-149">Open your `csproj` project file.</span></span> <span data-ttu-id="356e5-150">První řádek souboru by měla vypadat jako:</span><span class="sxs-lookup"><span data-stu-id="356e5-150">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="356e5-151">Přidejte následující okamžitě po tomto řádku:</span><span class="sxs-lookup"><span data-stu-id="356e5-151">Add the following immediately after this line:</span></span> 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
<span data-ttu-id="356e5-152">Většinu kódu editory poskytne dokončení pro různé verze tyto knihovny.</span><span class="sxs-lookup"><span data-stu-id="356e5-152">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="356e5-153">Obvykle budete chtít použít nejnovější verzi balíčku, která přidáte.</span><span class="sxs-lookup"><span data-stu-id="356e5-153">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="356e5-154">Je však potřeba se ujistit, že verze všech balíčků odpovídá, a aby splňovaly verzi rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="356e5-154">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="356e5-155">Po provedení těchto změn, byste měli spustit `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) znovu, aby balíček nainstalován ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="356e5-155">After you've made these changes, you should run `dotnet restore` ([see note](#dotnet-restore-note)) again so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="356e5-156">Provádění webových požadavků</span><span class="sxs-lookup"><span data-stu-id="356e5-156">Making Web Requests</span></span>
<span data-ttu-id="356e5-157">Teď jste připravení zahájit načítání dat z webu.</span><span class="sxs-lookup"><span data-stu-id="356e5-157">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="356e5-158">V této aplikaci, budete pro čtení informací z [Githubu API](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="356e5-158">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="356e5-159">Umožňuje načíst informace o projekty v části [.NET Foundation](http://www.dotnetfoundation.org/) zastřešující.</span><span class="sxs-lookup"><span data-stu-id="356e5-159">Let's read information about the projects under the [.NET Foundation](http://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="356e5-160">Ukázku zahájíte tím, že žádost na rozhraní API Githubu k načtení informací o projektech.</span><span class="sxs-lookup"><span data-stu-id="356e5-160">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="356e5-161">Koncový bod, které budete používat: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos).</span><span class="sxs-lookup"><span data-stu-id="356e5-161">The endpoint you'll use is: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos).</span></span> <span data-ttu-id="356e5-162">Chcete načíst všechny informace o těchto projekty, takže budete používat požadavek HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="356e5-162">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="356e5-163">Váš prohlížeč používá také HTTP GET požadavků a vložit, adresu URL do prohlížeče jaké informace můžete budete být přijímání a zpracování.</span><span class="sxs-lookup"><span data-stu-id="356e5-163">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="356e5-164">Můžete použít <xref:System.Net.Http.HttpClient> třída k vytvoření webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="356e5-164">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="356e5-165">Všechny moderní API technologie .NET, například <xref:System.Net.Http.HttpClient> podporuje pouze asynchronní metody pro jeho dlouho běžící rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="356e5-165">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="356e5-166">Spustit tím, že asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="356e5-166">Start by making an async method.</span></span> <span data-ttu-id="356e5-167">Při sestavování funkce aplikace, budete implementace vyplnit.</span><span class="sxs-lookup"><span data-stu-id="356e5-167">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="356e5-168">Začněte otevřením `program.cs` soubor v adresáři projektu a přidání metodu `Program` třídy:</span><span class="sxs-lookup"><span data-stu-id="356e5-168">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    
}
```

<span data-ttu-id="356e5-169">Budete muset přidat `using` příkaz v horní části vaší `Main` metoda tak, aby rozpozná kompilátor jazyka C# <xref:System.Threading.Tasks.Task> typu:</span><span class="sxs-lookup"><span data-stu-id="356e5-169">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="356e5-170">Pokud nyní vytvoříte projekt, protože neobsahuje žádné získáte upozornění generovaná pro tato metoda `await` operátory a spustí synchronně.</span><span class="sxs-lookup"><span data-stu-id="356e5-170">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="356e5-171">Ignorovat, teď; přidáte `await` operátory jako můžete vyplnit metodu.</span><span class="sxs-lookup"><span data-stu-id="356e5-171">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="356e5-172">V dalším kroku přejmenovat definovaný v oboru názvů `namespace` příkaz z výchozí hodnoty `ConsoleApp` k `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="356e5-172">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="356e5-173">Budeme později definovat `repo` třídy v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="356e5-173">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="356e5-174">Potom aktualizujte `Main` metoda mohli volat tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="356e5-174">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="356e5-175">`ProcessRepositories` Metoda vrátí úlohu, a neměly by se ukončovat program, než dokončení této úlohy.</span><span class="sxs-lookup"><span data-stu-id="356e5-175">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="356e5-176">Proto je nutné použít `Wait` metoda blokovat a počkejte na dokončení úlohy:</span><span class="sxs-lookup"><span data-stu-id="356e5-176">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
public static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="356e5-177">Nyní máte program, který nic neprovádí, ale dělá asynchronně.</span><span class="sxs-lookup"><span data-stu-id="356e5-177">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="356e5-178">Umožňuje zvýšit.</span><span class="sxs-lookup"><span data-stu-id="356e5-178">Let's improve it.</span></span>

<span data-ttu-id="356e5-179">Je třeba nejprve objekt, který je schopen načíst data z webu; můžete použít <xref:System.Net.Http.HttpClient> to provést.</span><span class="sxs-lookup"><span data-stu-id="356e5-179">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="356e5-180">Tento objekt zpracovává žádosti a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="356e5-180">This object handles the request and the responses.</span></span> <span data-ttu-id="356e5-181">Vytvořit jednu instanci daného typu v `Program` – třída v souboru Program.cs.</span><span class="sxs-lookup"><span data-stu-id="356e5-181">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

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

 <span data-ttu-id="356e5-182">Přejděte zpět do `ProcessRepositories` metoda a vyplňte v první verzi:</span><span class="sxs-lookup"><span data-stu-id="356e5-182">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="356e5-183">Budete muset přidat také dva nové kompilace pomocí příkazů v horní části souboru pro tento:</span><span class="sxs-lookup"><span data-stu-id="356e5-183">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="356e5-184">Tato první verze vytvoří žádost webové číst seznam všech úložiště v rámci organizace foundation dotnet.</span><span class="sxs-lookup"><span data-stu-id="356e5-184">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="356e5-185">(ID Githubu .NET Foundation je 'dotnet.).</span><span class="sxs-lookup"><span data-stu-id="356e5-185">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="356e5-186">Nastavit několik prvních řádků <xref:System.Net.Http.HttpClient> pro tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="356e5-186">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="356e5-187">Nejprve je nakonfigurován tak, aby přijímal odpovědi JSON Githubu.</span><span class="sxs-lookup"><span data-stu-id="356e5-187">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="356e5-188">Tento formát je jednoduše JSON.</span><span class="sxs-lookup"><span data-stu-id="356e5-188">This format is simply JSON.</span></span> <span data-ttu-id="356e5-189">Na další řádek přidá hlavičku uživatelského agenta na všechny požadavky z tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="356e5-189">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="356e5-190">Tyto dvě hlavičky se ověří pomocí kódu serveru Githubu a jsou nezbytné k načtení informací z Githubu.</span><span class="sxs-lookup"><span data-stu-id="356e5-190">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="356e5-191">Po dokončení konfigurace <xref:System.Net.Http.HttpClient>, provedete webové žádosti a načíst odpověď.</span><span class="sxs-lookup"><span data-stu-id="356e5-191">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="356e5-192">V této verzi první použijete <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> metoda pohodlí.</span><span class="sxs-lookup"><span data-stu-id="356e5-192">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="356e5-193">Tato metoda pohodlí spustí úlohu, která provede webový požadavek, a pak po dokončení žádosti, čtení datového proudu odpovědi a extrahuje obsah z datového proudu.</span><span class="sxs-lookup"><span data-stu-id="356e5-193">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="356e5-194">Text odpovědi se vrátí jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="356e5-194">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="356e5-195">Řetězec je k dispozici po dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="356e5-195">The string is available when the task completes.</span></span> 

<span data-ttu-id="356e5-196">Poslední dva řádky této metody await této úlohy a poté vytiskněte odpověď na konzole.</span><span class="sxs-lookup"><span data-stu-id="356e5-196">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="356e5-197">Sestavte aplikaci a spusťte ho.</span><span class="sxs-lookup"><span data-stu-id="356e5-197">Build the app, and run it.</span></span> <span data-ttu-id="356e5-198">Upozornění sestavení je pryč nyní, protože `ProcessRepositories` nyní neobsahuje `await` operátor.</span><span class="sxs-lookup"><span data-stu-id="356e5-198">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="356e5-199">Uvidíte, že se že jedná o dlouho zobrazení JSON formátovaného textu.</span><span class="sxs-lookup"><span data-stu-id="356e5-199">You'll see a long display of JSON formatted text.</span></span>   

## <a name="processing-the-json-result"></a><span data-ttu-id="356e5-200">Zpracování výsledku JSON</span><span class="sxs-lookup"><span data-stu-id="356e5-200">Processing the JSON Result</span></span>

<span data-ttu-id="356e5-201">V tomto okamžiku jste zapisují kód načíst odpověď z webového serveru, a zobrazit text, který je obsažený v této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="356e5-201">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="356e5-202">Dále umožňuje převést tuto odpověď JSON na objekty C#.</span><span class="sxs-lookup"><span data-stu-id="356e5-202">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="356e5-203">Serializátor JSON převede JSON data na objekty C#.</span><span class="sxs-lookup"><span data-stu-id="356e5-203">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="356e5-204">První úlohou je definice typu třídy jazyka C# obsahuje informace, které můžete použít z této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="356e5-204">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="356e5-205">Vytvořme tomto pomalu, takže začněte s jednoduché C# typu, který obsahuje název úložiště:</span><span class="sxs-lookup"><span data-stu-id="356e5-205">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

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

<span data-ttu-id="356e5-206">Uveďte ve výše uvedeném kódu v nový soubor s názvem 'repo.cs'.</span><span class="sxs-lookup"><span data-stu-id="356e5-206">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="356e5-207">Tato verze třídy představuje nejjednodušší cestu ke zpracování dat JSON.</span><span class="sxs-lookup"><span data-stu-id="356e5-207">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="356e5-208">Název třídy a člen název odpovídat názvů používaných v paketu JSON, místo následující konvence C#.</span><span class="sxs-lookup"><span data-stu-id="356e5-208">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="356e5-209">Budete to opravíme tím, že poskytuje některé konfigurační atributy později.</span><span class="sxs-lookup"><span data-stu-id="356e5-209">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="356e5-210">Tato třída představuje další důležité funkcí JSON serializace a deserializace: Ne všechna pole v paketu JSON jsou součástí této třídy.</span><span class="sxs-lookup"><span data-stu-id="356e5-210">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="356e5-211">Serializátor JSON bude ignorovat informace, které nejsou součástí typu třídy, který je používán.</span><span class="sxs-lookup"><span data-stu-id="356e5-211">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="356e5-212">Tato funkce usnadňuje vytvoření typů, které pracují se jenom podmnožinu pole v paketu JSON.</span><span class="sxs-lookup"><span data-stu-id="356e5-212">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="356e5-213">Teď, když jste vytvořili typ, můžeme deserializaci.</span><span class="sxs-lookup"><span data-stu-id="356e5-213">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="356e5-214">Budete muset vytvořit <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> objektu.</span><span class="sxs-lookup"><span data-stu-id="356e5-214">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="356e5-215">Tento objekt musíte znát typ CLR očekávala paketu JSON načte.</span><span class="sxs-lookup"><span data-stu-id="356e5-215">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="356e5-216">Paket z Githubu obsahuje posloupnost úložiště, takže `List<repo>` není správného typu.</span><span class="sxs-lookup"><span data-stu-id="356e5-216">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="356e5-217">Přidejte následující řádek na vaše `ProcessRepositories` metoda:</span><span class="sxs-lookup"><span data-stu-id="356e5-217">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="356e5-218">Používáte dva nové obory názvů, takže budete muset přidat ty také:</span><span class="sxs-lookup"><span data-stu-id="356e5-218">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="356e5-219">V dalším kroku použijete serializátor JSON převést na objekty C#.</span><span class="sxs-lookup"><span data-stu-id="356e5-219">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="356e5-220">Nahraďte volání <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> ve vaší `ProcessRepositories` metoda s následující dva řádky:</span><span class="sxs-lookup"><span data-stu-id="356e5-220">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="356e5-221">Všimněte si, že teď používáte <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> místo <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="356e5-221">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="356e5-222">Serializátor používá jako zdroj datového proudu místo řetězec.</span><span class="sxs-lookup"><span data-stu-id="356e5-222">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="356e5-223">Pojďme vysvětlují několik funkcí jazyka C#, které jsou používány ve druhém řádku výše.</span><span class="sxs-lookup"><span data-stu-id="356e5-223">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="356e5-224">Argument <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> je `await` výrazu.</span><span class="sxs-lookup"><span data-stu-id="356e5-224">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="356e5-225">Await výrazy může vyskytovat téměř kdekoli v kódu, i když až zatím Seznámili jste se pouze jejich v rámci příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="356e5-225">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="356e5-226">Za druhé `as` operátor převede z typu čas kompilace `object` k `List<repo>`.</span><span class="sxs-lookup"><span data-stu-id="356e5-226">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span> <span data-ttu-id="356e5-227">Prohlášení o <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> deklaruje, že vrací objekt typu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="356e5-227">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="356e5-228"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)>Vrátí typ, který jste zadali, když se vám ho (`List<repo>` v tomto kurzu).</span><span class="sxs-lookup"><span data-stu-id="356e5-228"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="356e5-229">Pokud převod neproběhne úspěšně, `as` vyhodnocen jako operátor `null`, místo došlo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="356e5-229">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="356e5-230">Téměř jste hotovi s v této části.</span><span class="sxs-lookup"><span data-stu-id="356e5-230">You're almost done with this section.</span></span> <span data-ttu-id="356e5-231">Teď, když jste převést JSON na objekty C#, můžeme zobrazí název každé úložiště.</span><span class="sxs-lookup"><span data-stu-id="356e5-231">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="356e5-232">Nahraďte řádky, které čtou:</span><span class="sxs-lookup"><span data-stu-id="356e5-232">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="356e5-233">pomocí následující:</span><span class="sxs-lookup"><span data-stu-id="356e5-233">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="356e5-234">Zkompilování a spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="356e5-234">Compile and run the application.</span></span> <span data-ttu-id="356e5-235">Vytiskne názvy úložiště, které jsou součástí služby .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="356e5-235">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="356e5-236">Řízení serializace</span><span class="sxs-lookup"><span data-stu-id="356e5-236">Controlling Serialization</span></span>

<span data-ttu-id="356e5-237">Než přidáte další funkce, budeme adres `repo` zadejte a nastavit jej konvencemi více standardní C#.</span><span class="sxs-lookup"><span data-stu-id="356e5-237">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="356e5-238">Můžete to udělat pomocí zadávání poznámek k `repo` zadejte s *atributy* které řídí, jak funguje serializátor JSON.</span><span class="sxs-lookup"><span data-stu-id="356e5-238">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="356e5-239">V případě použijete tyto atributy definovat mapování mezi názvy klíčů JSON a C# třídy a člen názvy.</span><span class="sxs-lookup"><span data-stu-id="356e5-239">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="356e5-240">Jsou dva atributy používané `DataContract` atribut a `DataMember` atribut.</span><span class="sxs-lookup"><span data-stu-id="356e5-240">The two attributes used are the `DataContract` attribute and the `DataMember` attribute.</span></span> <span data-ttu-id="356e5-241">Podle konvence všechny třídy atributů končit příponou `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="356e5-241">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="356e5-242">Však není potřeba použít tuto příponu, když použijete atribut.</span><span class="sxs-lookup"><span data-stu-id="356e5-242">However, you do not need to use that suffix when you apply an attribute.</span></span> 

<span data-ttu-id="356e5-243">`DataContract` a `DataMember` atributy jsou různé knihovny, takže budete muset přidat této knihovny do souboru projektu C# jako závislost.</span><span class="sxs-lookup"><span data-stu-id="356e5-243">The `DataContract` and `DataMember` attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="356e5-244">Přidejte následující řádek na `<ItemGroup>` části souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="356e5-244">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="356e5-245">Po uložení souboru spouštět `dotnet restore` ([viz Poznámka](#dotnet-restore-note)) pro načtení tohoto balíčku.</span><span class="sxs-lookup"><span data-stu-id="356e5-245">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="356e5-246">Dále otevřete `repo.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="356e5-246">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="356e5-247">Umožňuje změnit název Pascalcase a plně pravopisu název `Repository`.</span><span class="sxs-lookup"><span data-stu-id="356e5-247">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="356e5-248">Chceme mapování JSON, úložiště, uzly na tento typ, takže budete muset přidat `DataContract` atribut deklaraci třídy.</span><span class="sxs-lookup"><span data-stu-id="356e5-248">We still want to map JSON 'repo' nodes to this type, so you'll need to add the `DataContract` attribute to the class declaration.</span></span> <span data-ttu-id="356e5-249">Budete nastavíte `Name` vlastnost na název JSON uzlů, které jsou mapovány na tento typ atributu:</span><span class="sxs-lookup"><span data-stu-id="356e5-249">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="356e5-250"><xref:System.Runtime.Serialization.DataContractAttribute> Je členem skupiny <xref:System.Runtime.Serialization> obor názvů, takže budete muset přidat odpovídající `using` příkaz v horní části souboru:</span><span class="sxs-lookup"><span data-stu-id="356e5-250">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="356e5-251">Změnit název `repo` třídy k `Repository`, takže budete potřebovat, aby se stejným názvem změnit v souboru Program.cs (Některé editory můžou podporovat přejmenování refaktoring, která bude tuto změnu provést automaticky:)</span><span class="sxs-lookup"><span data-stu-id="356e5-251">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="356e5-252">V dalším kroku provedeme stejné změny s `name` pole pomocí <xref:System.Runtime.Serialization.DataMemberAttribute> – třída.</span><span class="sxs-lookup"><span data-stu-id="356e5-252">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="356e5-253">Proveďte následující změny k prohlášení o `name` pole repo.cs:</span><span class="sxs-lookup"><span data-stu-id="356e5-253">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="356e5-254">Tato změna znamená, že budete muset změnit kód, který zapisuje do souboru program.cs název každé úložiště:</span><span class="sxs-lookup"><span data-stu-id="356e5-254">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="356e5-255">Proveďte `dotnet build` následuje `dotnet run` a ujistěte se, máte k dispozici mapování správný.</span><span class="sxs-lookup"><span data-stu-id="356e5-255">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="356e5-256">Měli byste vidět stejný výstup jako před.</span><span class="sxs-lookup"><span data-stu-id="356e5-256">You should see the same output as before.</span></span> <span data-ttu-id="356e5-257">Před jsme zpracovat další vlastnosti z webového serveru, můžeme provést jeden další změny pro `Repository` třídy.</span><span class="sxs-lookup"><span data-stu-id="356e5-257">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="356e5-258">`Name` Člen je veřejně dostupná pole.</span><span class="sxs-lookup"><span data-stu-id="356e5-258">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="356e5-259">Není vhodné objektově orientované, takže můžeme ho změnit na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="356e5-259">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="356e5-260">Pro naše účely jsme nepotřebují žádné konkrétní spuštění kódu při získání nebo nastavení vlastnosti, ale změna na vlastnost usnadňuje přidat tyto změny později, aniž by vás kód, který používá `Repository` třídy.</span><span class="sxs-lookup"><span data-stu-id="356e5-260">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="356e5-261">Odebrat definici pole a nahraďte ho [automaticky implementované vlastnosti](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span><span class="sxs-lookup"><span data-stu-id="356e5-261">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="356e5-262">Kompilátor generuje text `get` a `set` přístupové objekty a také soukromé pole k uložení názvu.</span><span class="sxs-lookup"><span data-stu-id="356e5-262">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="356e5-263">Je podobná následující kód, který můžete ručně zadat:</span><span class="sxs-lookup"><span data-stu-id="356e5-263">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="356e5-264">Umožňuje provést jeden další změnu před přidáním nové funkce.</span><span class="sxs-lookup"><span data-stu-id="356e5-264">Let's make one more change before adding new features.</span></span> <span data-ttu-id="356e5-265">`ProcessRepositories` Metoda můžete práci asynchronní a vracet kolekci úložišť.</span><span class="sxs-lookup"><span data-stu-id="356e5-265">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="356e5-266">Umožňuje vrátit `List<Repository>` z této metody a přesuňte kód, který zapisuje informace do `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="356e5-266">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="356e5-267">Změnit podpis `ProcessRepositories` vrátit úlohy, jejichž výsledkem je seznam z `Repository` objekty:</span><span class="sxs-lookup"><span data-stu-id="356e5-267">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="356e5-268">Pak se právě vraťte úložiště po zpracování odpovědi JSON:</span><span class="sxs-lookup"><span data-stu-id="356e5-268">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="356e5-269">Kompilátor vygeneruje `Task<T>` objekt pro návrat, protože jste označili jako tuto metodu `async`.</span><span class="sxs-lookup"><span data-stu-id="356e5-269">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="356e5-270">Potom Pojďme upravit `Main` metoda tak to zaznamená ty výsledků a zapíše každý název úložiště do konzoly.</span><span class="sxs-lookup"><span data-stu-id="356e5-270">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="356e5-271">Vaše `Main` metoda nyní vypadat třeba takto:</span><span class="sxs-lookup"><span data-stu-id="356e5-271">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="356e5-272">Přístup k `Result` vlastnosti úlohy blokuje až po dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="356e5-272">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="356e5-273">Za normálních okolností raději `await` dokončení této úlohy, jako v `ProcessRepositories` metoda, ale není povolen v `Main` metoda.</span><span class="sxs-lookup"><span data-stu-id="356e5-273">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="356e5-274">Další informace pro čtení</span><span class="sxs-lookup"><span data-stu-id="356e5-274">Reading More Information</span></span>

<span data-ttu-id="356e5-275">Umožňuje to dokončit zpracováním několik dalších vlastností v paketu JSON, která se odešlou z rozhraní API Githubu.</span><span class="sxs-lookup"><span data-stu-id="356e5-275">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="356e5-276">Nebudete chtít získat všechno, ale přidání několik vlastností ukážeme pár více funkcí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="356e5-276">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="356e5-277">Začněme přidáním další pár jednoduchých typů k `Repository` definici třídy.</span><span class="sxs-lookup"><span data-stu-id="356e5-277">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="356e5-278">Přidejte tyto vlastnosti třídy:</span><span class="sxs-lookup"><span data-stu-id="356e5-278">Add these properties to that class:</span></span>

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

<span data-ttu-id="356e5-279">Tyto vlastnosti mají integrované převody z typu řetězec (což je co obsahovat pakety JSON) na typ cíle.</span><span class="sxs-lookup"><span data-stu-id="356e5-279">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="356e5-280"><xref:System.Uri> Typ může být pro vás nový.</span><span class="sxs-lookup"><span data-stu-id="356e5-280">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="356e5-281">Reprezentuje identifikátor URI, nebo v tomto případě adresy URL.</span><span class="sxs-lookup"><span data-stu-id="356e5-281">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="356e5-282">U `Uri` a `int` typy, pokud paketu JSON obsahuje data, která není převést na typ cíle, akce serializace vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="356e5-282">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="356e5-283">Jakmile přidáte tyto aktualizace `Main` metodu pro zobrazení tyto prvky:</span><span class="sxs-lookup"><span data-stu-id="356e5-283">Once you've added these, update the `Main` method to display those elements:</span></span>

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
<span data-ttu-id="356e5-284">V posledním kroku Pojďme přidat informace o poslední operace push.</span><span class="sxs-lookup"><span data-stu-id="356e5-284">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="356e5-285">Tyto informace formátována tímto způsobem v odpovědi JSON:</span><span class="sxs-lookup"><span data-stu-id="356e5-285">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="356e5-286">Tento formát není postupovat podle některého z standardní .NET <xref:System.DateTime> formáty.</span><span class="sxs-lookup"><span data-stu-id="356e5-286">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="356e5-287">Z tohoto důvodu budete muset napíše metoda, vlastní převod.</span><span class="sxs-lookup"><span data-stu-id="356e5-287">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="356e5-288">Nezpracovaný řetězec vystavené uživatelům taky pravděpodobně nebudete chtít `Repository` třídy.</span><span class="sxs-lookup"><span data-stu-id="356e5-288">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="356e5-289">Atributy může pomoct to také ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="356e5-289">Attributes can help control that as well.</span></span> <span data-ttu-id="356e5-290">Nejprve definovat `private` vlastnost, která bude obsahovat řetězcovou reprezentaci času ve vaší `Repository` třídy:</span><span class="sxs-lookup"><span data-stu-id="356e5-290">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="356e5-291">`DataMember` Atribut informuje serializátor, měla by to být zpracována, i když není členem veřejné.</span><span class="sxs-lookup"><span data-stu-id="356e5-291">The `DataMember` attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="356e5-292">Potom budete muset napsat veřejné vlastnosti jen pro čtení, která převede řetězec na platnou <xref:System.DateTime> objektu a vrátí který <xref:System.DateTime>:</span><span class="sxs-lookup"><span data-stu-id="356e5-292">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

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

<span data-ttu-id="356e5-293">Vraťme se přes nové konstrukce výše.</span><span class="sxs-lookup"><span data-stu-id="356e5-293">Let's go over the new constructs above.</span></span> <span data-ttu-id="356e5-294">`IgnoreDataMember` Atribut nastaví serializátor, že tento typ by neměly být pro čtení nebo zapisovat z libovolného objektu JSON.</span><span class="sxs-lookup"><span data-stu-id="356e5-294">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="356e5-295">Tato vlastnost obsahuje pouze `get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="356e5-295">This property contains only a `get` accessor.</span></span> <span data-ttu-id="356e5-296">Neexistuje žádné `set` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="356e5-296">There is no `set` accessor.</span></span> <span data-ttu-id="356e5-297">To je, jak definovat *jen pro čtení* vlastnost v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="356e5-297">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="356e5-298">(Ano, můžete vytvořit *jen pro zápis* vlastnosti v C#, ale jeho hodnota je omezená.) <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> Metoda analyzuje řetězec a vytvoří <xref:System.DateTime> objektu formátu zadané datum a přidá další metadata, aby `DateTime` pomocí `CultureInfo` objektu.</span><span class="sxs-lookup"><span data-stu-id="356e5-298">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="356e5-299">Pokud se nezdaří operace analýzy, přistupující objekt vlastnosti vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="356e5-299">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="356e5-300">Použít <xref:System.Globalization.CultureInfo.InvariantCulture>, budete muset přidat <xref:System.Globalization> názvů `using` příkazy v `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="356e5-300">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="356e5-301">Nakonec přidejte jednu výstupní více příkaz v konzole a jste připraveni k sestavení a spuštění této aplikace znovu:</span><span class="sxs-lookup"><span data-stu-id="356e5-301">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="356e5-302">Teď má shodovat s vaší verzí [dokončení ukázkové](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="356e5-302">Your version should now match the [finished sample](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient).</span></span>
 
## <a name="conclusion"></a><span data-ttu-id="356e5-303">Závěr</span><span class="sxs-lookup"><span data-stu-id="356e5-303">Conclusion</span></span>

<span data-ttu-id="356e5-304">Tento kurz vám ukázal jak webové požadavky, analyzovat výsledek a zobrazit vlastnosti výsledků.</span><span class="sxs-lookup"><span data-stu-id="356e5-304">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="356e5-305">Jste také přidali nové balíčky jako závislé položky ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="356e5-305">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="356e5-306">Seznámili jste některé z funkcí jazyka C#, které podporují objektově orientované techniky.</span><span class="sxs-lookup"><span data-stu-id="356e5-306">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
