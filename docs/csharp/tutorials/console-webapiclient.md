---
title: Vytvoření klienta REST pomocí .NET Core
description: V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 776d0ca65944e943c1c5114f95801c20d31a2b74
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75900738"
---
# <a name="rest-client"></a><span data-ttu-id="888d3-103">Klient REST</span><span class="sxs-lookup"><span data-stu-id="888d3-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="888d3-104">Úvod</span><span class="sxs-lookup"><span data-stu-id="888d3-104">Introduction</span></span>

<span data-ttu-id="888d3-105">V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce.</span><span class="sxs-lookup"><span data-stu-id="888d3-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="888d3-106">Naučíte se:</span><span class="sxs-lookup"><span data-stu-id="888d3-106">You’ll learn:</span></span>

* <span data-ttu-id="888d3-107">Základní informace o rozhraní příkazového řádku (CLI) .NET Core</span><span class="sxs-lookup"><span data-stu-id="888d3-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
* <span data-ttu-id="888d3-108">Přehled funkcí C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="888d3-108">An overview of C# Language features.</span></span>
* <span data-ttu-id="888d3-109">Správa závislostí pomocí NuGet</span><span class="sxs-lookup"><span data-stu-id="888d3-109">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="888d3-110">Komunikace HTTP</span><span class="sxs-lookup"><span data-stu-id="888d3-110">HTTP Communications</span></span>
* <span data-ttu-id="888d3-111">Zpracování informací JSON</span><span class="sxs-lookup"><span data-stu-id="888d3-111">Processing JSON information</span></span>
* <span data-ttu-id="888d3-112">Správa konfigurace s atributy.</span><span class="sxs-lookup"><span data-stu-id="888d3-112">Managing configuration with Attributes.</span></span>

<span data-ttu-id="888d3-113">Vytvoříte aplikaci, která vydává požadavky HTTP na službu REST na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="888d3-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="888d3-114">Přečtete si informace ve formátu JSON a převeďte tento paket JSON na C# objekty.</span><span class="sxs-lookup"><span data-stu-id="888d3-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="888d3-115">Nakonec uvidíte, jak pracovat s C# objekty.</span><span class="sxs-lookup"><span data-stu-id="888d3-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="888d3-116">V tomto kurzu máte spoustu funkcí.</span><span class="sxs-lookup"><span data-stu-id="888d3-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="888d3-117">Pojďme je sestavit jednou po jednom.</span><span class="sxs-lookup"><span data-stu-id="888d3-117">Let’s build them one by one.</span></span>

<span data-ttu-id="888d3-118">Pokud chcete postupovat spolu s [závěrečnou ukázkou](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) tohoto tématu, můžete si ho stáhnout.</span><span class="sxs-lookup"><span data-stu-id="888d3-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="888d3-119">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="888d3-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="888d3-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="888d3-120">Prerequisites</span></span>

<span data-ttu-id="888d3-121">Budete muset nastavit počítač tak, aby běžel .NET Core.</span><span class="sxs-lookup"><span data-stu-id="888d3-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="888d3-122">Pokyny k instalaci najdete na stránce [soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="888d3-122">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="888d3-123">Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="888d3-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="888d3-124">Budete muset nainstalovat svůj oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="888d3-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="888d3-125">Níže uvedené popisy používají [Visual Studio Code](https://code.visualstudio.com/), což je Open Source Editor pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="888d3-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="888d3-126">Můžete ale použít jakékoli nástroje, se kterými máte v pohodlí.</span><span class="sxs-lookup"><span data-stu-id="888d3-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="888d3-127">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="888d3-127">Create the Application</span></span>

<span data-ttu-id="888d3-128">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="888d3-128">The first step is to create a new application.</span></span> <span data-ttu-id="888d3-129">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="888d3-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="888d3-130">Zajistěte, aby byl aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="888d3-130">Make that the current directory.</span></span> <span data-ttu-id="888d3-131">V okně konzoly zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="888d3-131">Enter the following command in a console window:</span></span>

```console
dotnet new console --name WebApiClient
```

<span data-ttu-id="888d3-132">Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="888d3-132">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="888d3-133">Název projektu je "WebApiClient".</span><span class="sxs-lookup"><span data-stu-id="888d3-133">The project name is "WebApiClient".</span></span> <span data-ttu-id="888d3-134">Vzhledem k tomu, že se jedná o nový projekt, není zavedena žádná závislost, takže první spuštění stáhne rozhraní .NET Core Framework, nainstaluje certifikát pro vývoj a spustí Správce balíčků NuGet pro obnovení chybějících závislostí.</span><span class="sxs-lookup"><span data-stu-id="888d3-134">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework, install a development certificate and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="888d3-135">Než začnete provádět úpravy, zadejte `dotnet run` ([Viz poznámku](#dotnet-restore-note)) na příkazovém řádku a spusťte tak aplikaci.</span><span class="sxs-lookup"><span data-stu-id="888d3-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="888d3-136">`dotnet run` automaticky provádí `dotnet restore` v případě chybějících závislostí ve vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="888d3-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="888d3-137">Také provádí `dotnet build`, pokud vaše aplikace musí být znovu sestavena.</span><span class="sxs-lookup"><span data-stu-id="888d3-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="888d3-138">Po počáteční instalaci budete muset spustit pouze `dotnet restore` nebo `dotnet build`, pokud to pro váš projekt dává smysl.</span><span class="sxs-lookup"><span data-stu-id="888d3-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="888d3-139">Přidávání nových závislostí</span><span class="sxs-lookup"><span data-stu-id="888d3-139">Adding New Dependencies</span></span>

<span data-ttu-id="888d3-140">Jedním z klíčových cílů pro .NET Core je minimalizace velikosti instalace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="888d3-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="888d3-141">Pokud aplikace potřebuje pro některé z jejích funkcí další knihovny, přidejte tyto závislosti do souboru C# projektu (\*. csproj).</span><span class="sxs-lookup"><span data-stu-id="888d3-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="888d3-142">V našem příkladu budete muset přidat balíček `System.Runtime.Serialization.Json`, aby mohla aplikace zpracovat odpovědi JSON.</span><span class="sxs-lookup"><span data-stu-id="888d3-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="888d3-143">Pro tuto aplikaci budete potřebovat balíček `System.Runtime.Serialization.Json`.</span><span class="sxs-lookup"><span data-stu-id="888d3-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="888d3-144">Přidejte ho do projektu spuštěním následujícího příkazu [rozhraní .NET CLI](../../core/tools/dotnet-add-package.md) :</span><span class="sxs-lookup"><span data-stu-id="888d3-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```console
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="888d3-145">Vytváření webových požadavků</span><span class="sxs-lookup"><span data-stu-id="888d3-145">Making Web Requests</span></span>

<span data-ttu-id="888d3-146">Teď jste připraveni začít načítat data z webu.</span><span class="sxs-lookup"><span data-stu-id="888d3-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="888d3-147">V této aplikaci si přečtete informace z [rozhraní API GitHubu](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="888d3-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="888d3-148">Pojďme si přečíst informace o projektech v rámci [.NET Foundation](https://www.dotnetfoundation.org/) zastřešující.</span><span class="sxs-lookup"><span data-stu-id="888d3-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="888d3-149">Začnete tím, že si vyžádáte rozhraní API GitHubu, abyste načetli informace o projektech.</span><span class="sxs-lookup"><span data-stu-id="888d3-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="888d3-150">Koncový bod, který budete používat, je: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="888d3-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="888d3-151">Chcete načíst všechny informace o těchto projektech, abyste použili požadavek HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="888d3-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="888d3-152">Váš prohlížeč používá také požadavky HTTP GET, takže můžete vložit tuto adresu URL do prohlížeče, abyste viděli informace, které budete dostávat a zpracovávat.</span><span class="sxs-lookup"><span data-stu-id="888d3-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="888d3-153">Třídu <xref:System.Net.Http.HttpClient> použijte k vytváření webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="888d3-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="888d3-154">Stejně jako všechna moderní rozhraní API .NET <xref:System.Net.Http.HttpClient> podporuje pouze asynchronní metody pro svá dlouhotrvající rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="888d3-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="888d3-155">Začněte vytvořením asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="888d3-155">Start by making an async method.</span></span> <span data-ttu-id="888d3-156">Při sestavování funkčnosti aplikace naplníte implementaci.</span><span class="sxs-lookup"><span data-stu-id="888d3-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="888d3-157">Začněte tím, že otevřete soubor `program.cs` v adresáři projektu a přidáte následující metodu do `Program` třídy:</span><span class="sxs-lookup"><span data-stu-id="888d3-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="888d3-158">V horní části metody `Main` budete muset přidat příkaz `using`, aby C# kompilátor rozpoznal typ <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="888d3-158">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="888d3-159">Pokud v tomto okamžiku sestavíte projekt, zobrazí se pro tuto metodu upozornění vygenerované, protože neobsahuje žádné operátory `await` a spustí se synchronně.</span><span class="sxs-lookup"><span data-stu-id="888d3-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="888d3-160">Tuto chvíli ignorujte. přidáte `await` operátory při vyplňování metody.</span><span class="sxs-lookup"><span data-stu-id="888d3-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="888d3-161">Dále přejmenujte obor názvů definovaný v příkazu `namespace` z jeho výchozího `ConsoleApp` na `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="888d3-161">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="888d3-162">Později v tomto oboru názvů definujeme třídu `repo`.</span><span class="sxs-lookup"><span data-stu-id="888d3-162">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="888d3-163">Dále aktualizujte metodu `Main` pro volání této metody.</span><span class="sxs-lookup"><span data-stu-id="888d3-163">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="888d3-164">Metoda `ProcessRepositories` vrátí úlohu a neukončí program před dokončením této úlohy.</span><span class="sxs-lookup"><span data-stu-id="888d3-164">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="888d3-165">Proto je nutné změnit signaturu `Main`.</span><span class="sxs-lookup"><span data-stu-id="888d3-165">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="888d3-166">Přidejte modifikátor `async` a změňte návratový typ na `Task`.</span><span class="sxs-lookup"><span data-stu-id="888d3-166">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="888d3-167">Pak v těle metody přidejte volání `ProcessRepositories`.</span><span class="sxs-lookup"><span data-stu-id="888d3-167">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="888d3-168">Přidejte klíčové slovo `await` při volání této metody:</span><span class="sxs-lookup"><span data-stu-id="888d3-168">Add the `await` keyword when to that method call:</span></span>

```csharp
static Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="888d3-169">Nyní máte program, který nic nedělá, ale asynchronně ho provede.</span><span class="sxs-lookup"><span data-stu-id="888d3-169">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="888d3-170">Pojďme to vylepšit.</span><span class="sxs-lookup"><span data-stu-id="888d3-170">Let's improve it.</span></span>

<span data-ttu-id="888d3-171">Nejprve potřebujete objekt, který je schopný načíst data z webu. k tomu můžete použít <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="888d3-171">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="888d3-172">Tento objekt zpracovává požadavek a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="888d3-172">This object handles the request and the responses.</span></span> <span data-ttu-id="888d3-173">Vytvořte instanci jedné instance daného typu ve třídě `Program` v souboru Program.cs.</span><span class="sxs-lookup"><span data-stu-id="888d3-173">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static Task Main(string[] args)
        {
            //...
        }
    }
}
```

<span data-ttu-id="888d3-174">Pojďme se zpátky do metody `ProcessRepositories` a vyplnit první verzi IT:</span><span class="sxs-lookup"><span data-stu-id="888d3-174">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="888d3-175">V horní části souboru budete muset přidat také dvě nové příkazy using, aby se mohla kompilovat:</span><span class="sxs-lookup"><span data-stu-id="888d3-175">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="888d3-176">Tato první verze vytvoří webový požadavek na načtení seznamu všech úložišť v rámci organizace dotnet Foundation.</span><span class="sxs-lookup"><span data-stu-id="888d3-176">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="888d3-177">(ID gitHubu pro .NET Foundation je "dotnet").</span><span class="sxs-lookup"><span data-stu-id="888d3-177">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="888d3-178">První pár řádků nastavil <xref:System.Net.Http.HttpClient> pro tuto žádost.</span><span class="sxs-lookup"><span data-stu-id="888d3-178">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="888d3-179">Nejdřív je nakonfigurovaný tak, aby přijímal odpovědi na adresu JSON pro GitHub.</span><span class="sxs-lookup"><span data-stu-id="888d3-179">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="888d3-180">Tento formát je jednoduše JSON.</span><span class="sxs-lookup"><span data-stu-id="888d3-180">This format is simply JSON.</span></span> <span data-ttu-id="888d3-181">Další řádek přidá hlavičku uživatelského agenta do všech požadavků od tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="888d3-181">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="888d3-182">Tato dvě záhlaví jsou kontrolována kódem serveru GitHub a jsou nutná k načtení informací z GitHubu.</span><span class="sxs-lookup"><span data-stu-id="888d3-182">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="888d3-183">Po dokončení konfigurace <xref:System.Net.Http.HttpClient>vytvoříte webový požadavek a načtete odpověď.</span><span class="sxs-lookup"><span data-stu-id="888d3-183">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="888d3-184">V této první verzi použijete metodu <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> pohodlí.</span><span class="sxs-lookup"><span data-stu-id="888d3-184">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="888d3-185">Tato pohodlná metoda spustí úlohu, která provede webový požadavek, a poté, co požadavek vrátí, načte datový proud odpovědi a extrahuje obsah z datového proudu.</span><span class="sxs-lookup"><span data-stu-id="888d3-185">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="888d3-186">Tělo odpovědi je vráceno jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="888d3-186">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="888d3-187">Řetězec je k dispozici po dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="888d3-187">The string is available when the task completes.</span></span>

<span data-ttu-id="888d3-188">Poslední dva řádky této metody čekají na daný úkol a pak vytiskněte odpověď do konzoly.</span><span class="sxs-lookup"><span data-stu-id="888d3-188">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="888d3-189">Sestavte aplikaci a spusťte ji.</span><span class="sxs-lookup"><span data-stu-id="888d3-189">Build the app, and run it.</span></span> <span data-ttu-id="888d3-190">Upozornění na sestavení je teď pryč, protože `ProcessRepositories` nyní obsahuje operátor `await`.</span><span class="sxs-lookup"><span data-stu-id="888d3-190">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="888d3-191">Zobrazí se dlouhé zobrazení textu ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="888d3-191">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="888d3-192">Zpracování výsledku JSON</span><span class="sxs-lookup"><span data-stu-id="888d3-192">Processing the JSON Result</span></span>

<span data-ttu-id="888d3-193">V tuto chvíli jste napsali kód, který načte odpověď z webového serveru, a zobrazí text obsažený v této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="888d3-193">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="888d3-194">Nyní převedeme tuto odpověď JSON na C# objekty.</span><span class="sxs-lookup"><span data-stu-id="888d3-194">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="888d3-195">Třída <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> serializace objektů do formátu JSON a deserializace JSON do objektů.</span><span class="sxs-lookup"><span data-stu-id="888d3-195">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="888d3-196">Začněte definováním třídy představující `repo` objekt JSON vrácený z rozhraní API GitHubu:</span><span class="sxs-lookup"><span data-stu-id="888d3-196">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; };
    }
}
```

<span data-ttu-id="888d3-197">Výše uvedený kód vložte do nového souboru s názvem "úložiště. cs".</span><span class="sxs-lookup"><span data-stu-id="888d3-197">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="888d3-198">Tato verze třídy představuje nejjednodušší cestu pro zpracování dat JSON.</span><span class="sxs-lookup"><span data-stu-id="888d3-198">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="888d3-199">Název třídy a název členu odpovídají názvům použitým v paketu JSON namísto následujících C# konvencí.</span><span class="sxs-lookup"><span data-stu-id="888d3-199">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="888d3-200">Opravte to tak, že později poskytnete nějaké konfigurační atributy.</span><span class="sxs-lookup"><span data-stu-id="888d3-200">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="888d3-201">Tato třída ukazuje další důležitou funkci serializace a deserializace JSON: Ne všechna pole v paketu JSON jsou součástí této třídy.</span><span class="sxs-lookup"><span data-stu-id="888d3-201">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="888d3-202">Serializátor JSON bude ignorovat informace, které nejsou zahrnuté do používaného typu třídy.</span><span class="sxs-lookup"><span data-stu-id="888d3-202">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="888d3-203">Tato funkce usnadňuje vytváření typů, které pracují pouze s podmnožinou polí v paketu JSON.</span><span class="sxs-lookup"><span data-stu-id="888d3-203">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="888d3-204">Teď, když jste vytvořili typ, Pojďme ho deserializovat.</span><span class="sxs-lookup"><span data-stu-id="888d3-204">Now that you've created the type, let's deserialize it.</span></span> 

<span data-ttu-id="888d3-205">V dalším kroku použijete serializátor k převedení JSON na C# objekty.</span><span class="sxs-lookup"><span data-stu-id="888d3-205">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="888d3-206">Nahraďte volání <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> v metodě `ProcessRepositories` následující tři řádky:</span><span class="sxs-lookup"><span data-stu-id="888d3-206">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following three lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="888d3-207">Používáte nový obor názvů, takže ho budete muset přidat i na začátek souboru:</span><span class="sxs-lookup"><span data-stu-id="888d3-207">You're using a new namespace, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Text.Json;
```

<span data-ttu-id="888d3-208">Všimněte si, že teď místo <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>používáte <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="888d3-208">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="888d3-209">Serializátor používá jako svůj zdroj datový proud místo řetězce.</span><span class="sxs-lookup"><span data-stu-id="888d3-209">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="888d3-210">Pojďme Vysvětleme několik funkcí C# jazyka, které se používají v druhém řádku předchozího fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="888d3-210">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="888d3-211">Prvním argumentem, který je <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType>, je výraz `await`.</span><span class="sxs-lookup"><span data-stu-id="888d3-211">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="888d3-212">(Ostatní dva parametry jsou volitelné a jsou vynechány ve fragmentu kódu.) Výrazy await se můžou vyskytovat skoro kdekoli v kódu, a to i v případě, že jste je teď udělali jenom jako součást příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="888d3-212">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="888d3-213">Metoda `Deserialize` je *Obecná*, což znamená, že je nutné zadat argumenty typu pro typ objektu, který by měl být vytvořen z textu JSON.</span><span class="sxs-lookup"><span data-stu-id="888d3-213">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="888d3-214">V tomto příkladu provádíte deserializaci do `List<Repository>`, což je jiný obecný objekt, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="888d3-214">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="888d3-215">Třída `List<>` ukládá kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="888d3-215">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="888d3-216">Argument typu deklaruje typ objektů uložených v `List<>`.</span><span class="sxs-lookup"><span data-stu-id="888d3-216">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="888d3-217">Text JSON představuje kolekci objektů úložiště, takže je argument typu `Repository`.</span><span class="sxs-lookup"><span data-stu-id="888d3-217">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="888d3-218">V této části už skoro jste hotovi.</span><span class="sxs-lookup"><span data-stu-id="888d3-218">You're almost done with this section.</span></span> <span data-ttu-id="888d3-219">Teď, když jste převedli JSON C# na objekty, pojďme zobrazit název každého úložiště.</span><span class="sxs-lookup"><span data-stu-id="888d3-219">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="888d3-220">Nahraďte řádky, které se čtou:</span><span class="sxs-lookup"><span data-stu-id="888d3-220">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="888d3-221">s následujícím:</span><span class="sxs-lookup"><span data-stu-id="888d3-221">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="888d3-222">Zkompilujte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="888d3-222">Compile and run the application.</span></span> <span data-ttu-id="888d3-223">Vypíše názvy úložišť, která jsou součástí .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="888d3-223">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="888d3-224">Řízení serializace</span><span class="sxs-lookup"><span data-stu-id="888d3-224">Controlling Serialization</span></span>

<span data-ttu-id="888d3-225">Než přidáte další funkce, předejte adresu `name` vlastnosti pomocí atributu `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="888d3-225">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="888d3-226">Proveďte následující změny v deklaraci pole `name` v repo.cs:</span><span class="sxs-lookup"><span data-stu-id="888d3-226">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="888d3-227">Tato změna znamená, že potřebujete změnit kód, který zapisuje název každého úložiště v program.cs:</span><span class="sxs-lookup"><span data-stu-id="888d3-227">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="888d3-228">Spusťte `dotnet run`, abyste se ujistili, že jsou mapování správná.</span><span class="sxs-lookup"><span data-stu-id="888d3-228">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="888d3-229">Měl by se zobrazit stejný výstup jako předtím.</span><span class="sxs-lookup"><span data-stu-id="888d3-229">You should see the same output as before.</span></span>

<span data-ttu-id="888d3-230">Pojďme ještě před přidáním nových funkcí udělat nějakou další změnu.</span><span class="sxs-lookup"><span data-stu-id="888d3-230">Let's make one more change before adding new features.</span></span> <span data-ttu-id="888d3-231">Metoda `ProcessRepositories` může provádět asynchronní práci a vracet kolekci úložišť.</span><span class="sxs-lookup"><span data-stu-id="888d3-231">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="888d3-232">Pojďme z této metody vracet `List<Repository>` a přesunete kód, který zapisuje informace do metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="888d3-232">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="888d3-233">Změňte podpis `ProcessRepositories` a vraťte úkol, jehož výsledkem je seznam objektů `Repository`:</span><span class="sxs-lookup"><span data-stu-id="888d3-233">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="888d3-234">Pak jednoduše vraťte úložiště po zpracování odpovědi JSON:</span><span class="sxs-lookup"><span data-stu-id="888d3-234">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="888d3-235">Kompilátor vygeneruje objekt `Task<T>` pro návrat, protože jste tuto metodu označili jako `async`.</span><span class="sxs-lookup"><span data-stu-id="888d3-235">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="888d3-236">Pak upravíte metodu `Main` tak, aby zachytit tyto výsledky a zapsala jednotlivé názvy úložišť do konzoly.</span><span class="sxs-lookup"><span data-stu-id="888d3-236">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="888d3-237">Vaše metoda `Main` nyní vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="888d3-237">Your `Main` method now looks like this:</span></span>

```csharp
public static Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="888d3-238">Přečtěte si další informace</span><span class="sxs-lookup"><span data-stu-id="888d3-238">Reading More Information</span></span>

<span data-ttu-id="888d3-239">Pojďme to dokončit zpracováním několika dalších vlastností v paketu JSON, které se odesílají z rozhraní API GitHubu.</span><span class="sxs-lookup"><span data-stu-id="888d3-239">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="888d3-240">Nebudete chtít všechno přidat, ale přidáním několika vlastností se ukáže několik dalších funkcí tohoto C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="888d3-240">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="888d3-241">Pojďme začít přidáním několika jednoduchých typů do definice `Repository` třídy.</span><span class="sxs-lookup"><span data-stu-id="888d3-241">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="888d3-242">Přidejte tyto vlastnosti do této třídy:</span><span class="sxs-lookup"><span data-stu-id="888d3-242">Add these properties to that class:</span></span>

```csharp
[JsonPropertyName(Name="description")]
public string Description { get; set; }

[JsonPropertyName(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName(Name="homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName(Name="watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="888d3-243">Tyto vlastnosti mají předdefinované převody z typu řetězce (což je to, co pakety JSON obsahují) k cílovému typu.</span><span class="sxs-lookup"><span data-stu-id="888d3-243">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="888d3-244">Typ <xref:System.Uri> může být pro vás nový.</span><span class="sxs-lookup"><span data-stu-id="888d3-244">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="888d3-245">Představuje identifikátor URI, nebo v tomto případě adresu URL.</span><span class="sxs-lookup"><span data-stu-id="888d3-245">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="888d3-246">V případě `Uri` a `int`ch typů platí, že pokud paket JSON obsahuje data, která nejsou převedena na cílový typ, akce serializace vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="888d3-246">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="888d3-247">Jakmile je přidáte, aktualizujte metodu `Main`, aby zobrazovala tyto prvky:</span><span class="sxs-lookup"><span data-stu-id="888d3-247">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="888d3-248">Jako poslední krok Pojďme přidat informace pro poslední operaci Push.</span><span class="sxs-lookup"><span data-stu-id="888d3-248">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="888d3-249">Tyto informace jsou v odpovědi JSON formátované tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="888d3-249">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="888d3-250">Tento formát nedodržuje žádné standardní <xref:System.DateTime> formáty .NET.</span><span class="sxs-lookup"><span data-stu-id="888d3-250">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="888d3-251">Z tohoto důvodu budete muset napsat vlastní metodu převodu.</span><span class="sxs-lookup"><span data-stu-id="888d3-251">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="888d3-252">Pravděpodobně nebudete chtít, aby Nezpracovaný řetězec byl vystaven uživatelům třídy `Repository`.</span><span class="sxs-lookup"><span data-stu-id="888d3-252">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="888d3-253">Atributy mohou také určovat.</span><span class="sxs-lookup"><span data-stu-id="888d3-253">Attributes can help control that as well.</span></span> <span data-ttu-id="888d3-254">Nejprve definujte vlastnost `public`, která bude obsahovat řetězcové vyjádření data a času ve vaší třídě `Repository` a vlastnost `LastPush` `readonly`, která vrací formátovaný řetězec, který představuje vrácené datum:</span><span class="sxs-lookup"><span data-stu-id="888d3-254">First, define a `public` property that will hold the string representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns a formatted string that represents the returned date:</span></span>

```csharp
[JsonPropertyName(Name="pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

<span data-ttu-id="888d3-255">Pojďme přecházet na nové konstrukce, které jsme právě definovali.</span><span class="sxs-lookup"><span data-stu-id="888d3-255">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="888d3-256">Vlastnost `LastPush` je definována pomocí *člena Expression-těle* pro přistupující objekt `get`.</span><span class="sxs-lookup"><span data-stu-id="888d3-256">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="888d3-257">Neexistuje žádný přistupující objekt `set`.</span><span class="sxs-lookup"><span data-stu-id="888d3-257">There is no `set` accessor.</span></span> <span data-ttu-id="888d3-258">Vynechání přístupového objektu `set` je způsob, jakým definujete vlastnost C# *jen pro čtení* v.</span><span class="sxs-lookup"><span data-stu-id="888d3-258">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="888d3-259">(Ano, můžete vytvořit vlastnosti *pouze pro zápis* v C#, ale jejich hodnota je omezená.) Metoda <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analyzuje řetězec a vytvoří objekt <xref:System.DateTime> pomocí poskytnutého formátu data a přidá další metadata do `DateTime` pomocí objektu `CultureInfo`.</span><span class="sxs-lookup"><span data-stu-id="888d3-259">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="888d3-260">Pokud operace analýzy není úspěšná, přistupující objekt vlastnosti vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="888d3-260">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="888d3-261">Chcete-li použít <xref:System.Globalization.CultureInfo.InvariantCulture>, bude nutné přidat <xref:System.Globalization> oboru názvů do příkazů `using` v `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="888d3-261">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="888d3-262">Nakonec přidejte do konzoly další příkaz Output a teď budete připraveni tuto aplikaci sestavit a spustit:</span><span class="sxs-lookup"><span data-stu-id="888d3-262">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="888d3-263">Verze by měla nyní odpovídat [ukázce dokončeno](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="888d3-263">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="888d3-264">Závěr</span><span class="sxs-lookup"><span data-stu-id="888d3-264">Conclusion</span></span>

<span data-ttu-id="888d3-265">V tomto kurzu jste si ukázali, jak vytvářet webové požadavky, analyzovat výsledek a zobrazovat vlastnosti těchto výsledků.</span><span class="sxs-lookup"><span data-stu-id="888d3-265">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="888d3-266">Přidali jste také nové balíčky jako závislosti ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="888d3-266">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="888d3-267">Seznámili jste se s některými funkcemi C# jazyka, který podporuje objektově orientované techniky.</span><span class="sxs-lookup"><span data-stu-id="888d3-267">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
