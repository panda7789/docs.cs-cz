---
title: Vytvoření klienta REST pomocí .NET Core
description: V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 09eda08f82490070c66d0b290359872c1043b0c2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737572"
---
# <a name="rest-client"></a><span data-ttu-id="6783c-103">Klient REST</span><span class="sxs-lookup"><span data-stu-id="6783c-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="6783c-104">Úvod</span><span class="sxs-lookup"><span data-stu-id="6783c-104">Introduction</span></span>

<span data-ttu-id="6783c-105">V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce.</span><span class="sxs-lookup"><span data-stu-id="6783c-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="6783c-106">Naučíte se:</span><span class="sxs-lookup"><span data-stu-id="6783c-106">You’ll learn:</span></span>

* <span data-ttu-id="6783c-107">Základní informace o rozhraní příkazového řádku (CLI) .NET Core</span><span class="sxs-lookup"><span data-stu-id="6783c-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
* <span data-ttu-id="6783c-108">Přehled funkcí C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="6783c-108">An overview of C# Language features.</span></span>
* <span data-ttu-id="6783c-109">Správa závislostí pomocí NuGet</span><span class="sxs-lookup"><span data-stu-id="6783c-109">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="6783c-110">Komunikace HTTP</span><span class="sxs-lookup"><span data-stu-id="6783c-110">HTTP Communications</span></span>
* <span data-ttu-id="6783c-111">Zpracování informací JSON</span><span class="sxs-lookup"><span data-stu-id="6783c-111">Processing JSON information</span></span>
* <span data-ttu-id="6783c-112">Správa konfigurace s atributy.</span><span class="sxs-lookup"><span data-stu-id="6783c-112">Managing configuration with Attributes.</span></span>

<span data-ttu-id="6783c-113">Vytvoříte aplikaci, která vydává požadavky HTTP na službu REST na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="6783c-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="6783c-114">Přečtete si informace ve formátu JSON a převeďte tento paket JSON na C# objekty.</span><span class="sxs-lookup"><span data-stu-id="6783c-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="6783c-115">Nakonec uvidíte, jak pracovat s C# objekty.</span><span class="sxs-lookup"><span data-stu-id="6783c-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="6783c-116">V tomto kurzu máte spoustu funkcí.</span><span class="sxs-lookup"><span data-stu-id="6783c-116">There are many features in this tutorial.</span></span> <span data-ttu-id="6783c-117">Pojďme je sestavit jednou po jednom.</span><span class="sxs-lookup"><span data-stu-id="6783c-117">Let’s build them one by one.</span></span>

<span data-ttu-id="6783c-118">Pokud chcete postupovat spolu s [závěrečnou ukázkou](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) tohoto tématu, můžete si ho stáhnout.</span><span class="sxs-lookup"><span data-stu-id="6783c-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="6783c-119">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="6783c-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6783c-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6783c-120">Prerequisites</span></span>

<span data-ttu-id="6783c-121">Budete muset nastavit počítač tak, aby běžel .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6783c-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="6783c-122">Pokyny k instalaci najdete na stránce [soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="6783c-122">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="6783c-123">Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="6783c-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="6783c-124">Budete muset nainstalovat svůj oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="6783c-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="6783c-125">Níže uvedené popisy používají [Visual Studio Code](https://code.visualstudio.com/), což je Open Source Editor pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="6783c-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="6783c-126">Můžete ale použít jakékoli nástroje, se kterými máte v pohodlí.</span><span class="sxs-lookup"><span data-stu-id="6783c-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="6783c-127">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="6783c-127">Create the Application</span></span>

<span data-ttu-id="6783c-128">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="6783c-128">The first step is to create a new application.</span></span> <span data-ttu-id="6783c-129">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6783c-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="6783c-130">Zajistěte, aby byl aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="6783c-130">Make that the current directory.</span></span> <span data-ttu-id="6783c-131">V okně konzoly zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="6783c-131">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebApiClient
```

<span data-ttu-id="6783c-132">Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="6783c-132">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="6783c-133">Název projektu je "WebApiClient".</span><span class="sxs-lookup"><span data-stu-id="6783c-133">The project name is "WebApiClient".</span></span> <span data-ttu-id="6783c-134">Vzhledem k tomu, že se jedná o nový projekt, není provedena žádná závislost.</span><span class="sxs-lookup"><span data-stu-id="6783c-134">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="6783c-135">První spuštění stáhne rozhraní .NET Core Framework, nainstaluje certifikát pro vývoj a spustí Správce balíčků NuGet pro obnovení chybějících závislostí.</span><span class="sxs-lookup"><span data-stu-id="6783c-135">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="6783c-136">Než začnete provádět úpravy, zadejte `dotnet run` ([Viz poznámku](#dotnet-restore-note)) na příkazovém řádku a spusťte tak aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6783c-136">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="6783c-137">`dotnet run` automaticky provádí `dotnet restore` v případě chybějících závislostí ve vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="6783c-137">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="6783c-138">Také provádí `dotnet build`, pokud vaše aplikace musí být znovu sestavena.</span><span class="sxs-lookup"><span data-stu-id="6783c-138">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="6783c-139">Po počáteční instalaci budete muset spustit pouze `dotnet restore` nebo `dotnet build`, pokud to pro váš projekt dává smysl.</span><span class="sxs-lookup"><span data-stu-id="6783c-139">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="6783c-140">Přidávání nových závislostí</span><span class="sxs-lookup"><span data-stu-id="6783c-140">Adding New Dependencies</span></span>

<span data-ttu-id="6783c-141">Jedním z klíčových cílů pro .NET Core je minimalizace velikosti instalace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="6783c-141">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="6783c-142">Pokud aplikace potřebuje pro některé z jejích funkcí další knihovny, přidejte tyto závislosti do souboru C# projektu (\*. csproj).</span><span class="sxs-lookup"><span data-stu-id="6783c-142">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="6783c-143">V našem příkladu budete muset přidat balíček `System.Runtime.Serialization.Json`, aby mohla aplikace zpracovat odpovědi JSON.</span><span class="sxs-lookup"><span data-stu-id="6783c-143">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="6783c-144">Pro tuto aplikaci budete potřebovat balíček `System.Runtime.Serialization.Json`.</span><span class="sxs-lookup"><span data-stu-id="6783c-144">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="6783c-145">Přidejte ho do projektu spuštěním následujícího příkazu [rozhraní .NET CLI](../../core/tools/dotnet-add-package.md) :</span><span class="sxs-lookup"><span data-stu-id="6783c-145">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```console
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="6783c-146">Vytváření webových požadavků</span><span class="sxs-lookup"><span data-stu-id="6783c-146">Making Web Requests</span></span>

<span data-ttu-id="6783c-147">Teď jste připraveni začít načítat data z webu.</span><span class="sxs-lookup"><span data-stu-id="6783c-147">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="6783c-148">V této aplikaci si přečtete informace z [rozhraní API GitHubu](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="6783c-148">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="6783c-149">Pojďme si přečíst informace o projektech v rámci [.NET Foundation](https://www.dotnetfoundation.org/) zastřešující.</span><span class="sxs-lookup"><span data-stu-id="6783c-149">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="6783c-150">Začnete tím, že si vyžádáte rozhraní API GitHubu, abyste načetli informace o projektech.</span><span class="sxs-lookup"><span data-stu-id="6783c-150">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="6783c-151">Koncový bod, který budete používat, je: <https://api.github.com/orgs/dotnet/repos>.</span><span class="sxs-lookup"><span data-stu-id="6783c-151">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="6783c-152">Chcete načíst všechny informace o těchto projektech, abyste použili požadavek HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="6783c-152">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="6783c-153">Váš prohlížeč používá také požadavky HTTP GET, takže můžete vložit tuto adresu URL do prohlížeče, abyste viděli informace, které budete dostávat a zpracovávat.</span><span class="sxs-lookup"><span data-stu-id="6783c-153">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="6783c-154">Třídu <xref:System.Net.Http.HttpClient> použijte k vytváření webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="6783c-154">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="6783c-155">Stejně jako všechna moderní rozhraní API .NET <xref:System.Net.Http.HttpClient> podporuje pouze asynchronní metody pro svá dlouhotrvající rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="6783c-155">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="6783c-156">Začněte vytvořením asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="6783c-156">Start by making an async method.</span></span> <span data-ttu-id="6783c-157">Při sestavování funkčnosti aplikace naplníte implementaci.</span><span class="sxs-lookup"><span data-stu-id="6783c-157">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="6783c-158">Začněte tím, že otevřete soubor `program.cs` v adresáři projektu a přidáte následující metodu do `Program` třídy:</span><span class="sxs-lookup"><span data-stu-id="6783c-158">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="6783c-159">V horní části metody `Main` budete muset přidat direktivu `using`, aby C# kompilátor rozpoznal typ <xref:System.Threading.Tasks.Task>:</span><span class="sxs-lookup"><span data-stu-id="6783c-159">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="6783c-160">Pokud v tomto okamžiku sestavíte projekt, zobrazí se pro tuto metodu upozornění vygenerované, protože neobsahuje žádné operátory `await` a spustí se synchronně.</span><span class="sxs-lookup"><span data-stu-id="6783c-160">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="6783c-161">Tuto chvíli ignorujte. přidáte `await` operátory při vyplňování metody.</span><span class="sxs-lookup"><span data-stu-id="6783c-161">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="6783c-162">Dále přejmenujte obor názvů definovaný v příkazu `namespace` z jeho výchozího `ConsoleApp` na `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="6783c-162">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="6783c-163">Později v tomto oboru názvů definujeme třídu `repo`.</span><span class="sxs-lookup"><span data-stu-id="6783c-163">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="6783c-164">Dále aktualizujte metodu `Main` pro volání této metody.</span><span class="sxs-lookup"><span data-stu-id="6783c-164">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="6783c-165">Metoda `ProcessRepositories` vrátí úlohu a neukončí program před dokončením této úlohy.</span><span class="sxs-lookup"><span data-stu-id="6783c-165">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="6783c-166">Proto je nutné změnit signaturu `Main`.</span><span class="sxs-lookup"><span data-stu-id="6783c-166">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="6783c-167">Přidejte modifikátor `async` a změňte návratový typ na `Task`.</span><span class="sxs-lookup"><span data-stu-id="6783c-167">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="6783c-168">Pak v těle metody přidejte volání `ProcessRepositories`.</span><span class="sxs-lookup"><span data-stu-id="6783c-168">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="6783c-169">Do tohoto volání metody přidejte klíčové slovo `await`:</span><span class="sxs-lookup"><span data-stu-id="6783c-169">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="6783c-170">Nyní máte program, který nic nedělá, ale asynchronně ho provede.</span><span class="sxs-lookup"><span data-stu-id="6783c-170">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="6783c-171">Pojďme to vylepšit.</span><span class="sxs-lookup"><span data-stu-id="6783c-171">Let's improve it.</span></span>

<span data-ttu-id="6783c-172">Nejprve potřebujete objekt, který je schopný načíst data z webu. k tomu můžete použít <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="6783c-172">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="6783c-173">Tento objekt zpracovává požadavek a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="6783c-173">This object handles the request and the responses.</span></span> <span data-ttu-id="6783c-174">Vytvořte instanci jedné instance daného typu ve třídě `Program` v souboru *program.cs* .</span><span class="sxs-lookup"><span data-stu-id="6783c-174">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static async Task Main(string[] args)
        {
            //...
        }
    }
}
```

<span data-ttu-id="6783c-175">Pojďme se zpátky do metody `ProcessRepositories` a vyplnit první verzi IT:</span><span class="sxs-lookup"><span data-stu-id="6783c-175">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="6783c-176">V horní části souboru budete muset přidat také dvě nové direktivy `using`, aby se tato kompilace mohla kompilovat:</span><span class="sxs-lookup"><span data-stu-id="6783c-176">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="6783c-177">Tato první verze vytvoří webový požadavek na načtení seznamu všech úložišť v rámci organizace dotnet Foundation.</span><span class="sxs-lookup"><span data-stu-id="6783c-177">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="6783c-178">(ID gitHubu pro .NET Foundation je "dotnet").</span><span class="sxs-lookup"><span data-stu-id="6783c-178">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="6783c-179">První pár řádků nastavil <xref:System.Net.Http.HttpClient> pro tuto žádost.</span><span class="sxs-lookup"><span data-stu-id="6783c-179">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="6783c-180">Nejdřív je nakonfigurovaný tak, aby přijímal odpovědi na adresu JSON pro GitHub.</span><span class="sxs-lookup"><span data-stu-id="6783c-180">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="6783c-181">Tento formát je jednoduše JSON.</span><span class="sxs-lookup"><span data-stu-id="6783c-181">This format is simply JSON.</span></span> <span data-ttu-id="6783c-182">Další řádek přidá hlavičku uživatelského agenta do všech požadavků od tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="6783c-182">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="6783c-183">Tato dvě záhlaví jsou kontrolována kódem serveru GitHub a jsou nutná k načtení informací z GitHubu.</span><span class="sxs-lookup"><span data-stu-id="6783c-183">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="6783c-184">Po dokončení konfigurace <xref:System.Net.Http.HttpClient>vytvoříte webový požadavek a načtete odpověď.</span><span class="sxs-lookup"><span data-stu-id="6783c-184">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="6783c-185">V této první verzi použijete metodu <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> pohodlí.</span><span class="sxs-lookup"><span data-stu-id="6783c-185">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="6783c-186">Tato pohodlná metoda spustí úlohu, která provede webový požadavek, a poté, co požadavek vrátí, načte datový proud odpovědi a extrahuje obsah z datového proudu.</span><span class="sxs-lookup"><span data-stu-id="6783c-186">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="6783c-187">Tělo odpovědi je vráceno jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="6783c-187">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="6783c-188">Řetězec je k dispozici po dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="6783c-188">The string is available when the task completes.</span></span>

<span data-ttu-id="6783c-189">Poslední dva řádky této metody čekají na daný úkol a pak vytiskněte odpověď do konzoly.</span><span class="sxs-lookup"><span data-stu-id="6783c-189">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="6783c-190">Sestavte aplikaci a spusťte ji.</span><span class="sxs-lookup"><span data-stu-id="6783c-190">Build the app, and run it.</span></span> <span data-ttu-id="6783c-191">Upozornění na sestavení je teď pryč, protože `ProcessRepositories` nyní obsahuje operátor `await`.</span><span class="sxs-lookup"><span data-stu-id="6783c-191">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="6783c-192">Zobrazí se dlouhé zobrazení textu ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="6783c-192">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="6783c-193">Zpracování výsledku JSON</span><span class="sxs-lookup"><span data-stu-id="6783c-193">Processing the JSON Result</span></span>

<span data-ttu-id="6783c-194">V tuto chvíli jste napsali kód, který načte odpověď z webového serveru, a zobrazí text obsažený v této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="6783c-194">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="6783c-195">Nyní převedeme tuto odpověď JSON na C# objekty.</span><span class="sxs-lookup"><span data-stu-id="6783c-195">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="6783c-196">Třída <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> serializace objektů do formátu JSON a deserializace JSON do objektů.</span><span class="sxs-lookup"><span data-stu-id="6783c-196">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="6783c-197">Začněte definováním třídy představující `repo` objekt JSON vrácený z rozhraní API GitHubu:</span><span class="sxs-lookup"><span data-stu-id="6783c-197">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

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

<span data-ttu-id="6783c-198">Výše uvedený kód vložte do nového souboru s názvem "úložiště. cs".</span><span class="sxs-lookup"><span data-stu-id="6783c-198">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="6783c-199">Tato verze třídy představuje nejjednodušší cestu pro zpracování dat JSON.</span><span class="sxs-lookup"><span data-stu-id="6783c-199">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="6783c-200">Název třídy a název členu odpovídají názvům použitým v paketu JSON namísto následujících C# konvencí.</span><span class="sxs-lookup"><span data-stu-id="6783c-200">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="6783c-201">Opravte to tak, že později poskytnete nějaké konfigurační atributy.</span><span class="sxs-lookup"><span data-stu-id="6783c-201">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="6783c-202">Tato třída ukazuje další důležitou funkci serializace a deserializace JSON: Ne všechna pole v paketu JSON jsou součástí této třídy.</span><span class="sxs-lookup"><span data-stu-id="6783c-202">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="6783c-203">Serializátor JSON bude ignorovat informace, které nejsou zahrnuté do používaného typu třídy.</span><span class="sxs-lookup"><span data-stu-id="6783c-203">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="6783c-204">Tato funkce usnadňuje vytváření typů, které pracují pouze s podmnožinou polí v paketu JSON.</span><span class="sxs-lookup"><span data-stu-id="6783c-204">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="6783c-205">Teď, když jste vytvořili typ, Pojďme ho deserializovat.</span><span class="sxs-lookup"><span data-stu-id="6783c-205">Now that you've created the type, let's deserialize it.</span></span> 

<span data-ttu-id="6783c-206">V dalším kroku použijete serializátor k převedení JSON na C# objekty.</span><span class="sxs-lookup"><span data-stu-id="6783c-206">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="6783c-207">Nahraďte volání <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> v metodě `ProcessRepositories` následující tři řádky:</span><span class="sxs-lookup"><span data-stu-id="6783c-207">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following three lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="6783c-208">Používáte nový obor názvů, takže ho budete muset přidat i na začátek souboru:</span><span class="sxs-lookup"><span data-stu-id="6783c-208">You're using a new namespace, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Text.Json;
```

<span data-ttu-id="6783c-209">Všimněte si, že teď místo <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>používáte <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)>.</span><span class="sxs-lookup"><span data-stu-id="6783c-209">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="6783c-210">Serializátor používá jako svůj zdroj datový proud místo řetězce.</span><span class="sxs-lookup"><span data-stu-id="6783c-210">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="6783c-211">Pojďme Vysvětleme několik funkcí C# jazyka, které se používají v druhém řádku předchozího fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="6783c-211">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="6783c-212">Prvním argumentem, který je <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType>, je výraz `await`.</span><span class="sxs-lookup"><span data-stu-id="6783c-212">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="6783c-213">(Ostatní dva parametry jsou volitelné a jsou vynechány ve fragmentu kódu.) Výrazy await se můžou vyskytovat skoro kdekoli v kódu, a to i v případě, že jste je teď udělali jenom jako součást příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="6783c-213">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="6783c-214">Metoda `Deserialize` je *Obecná*, což znamená, že je nutné zadat argumenty typu pro typ objektu, který by měl být vytvořen z textu JSON.</span><span class="sxs-lookup"><span data-stu-id="6783c-214">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="6783c-215">V tomto příkladu provádíte deserializaci do `List<Repository>`, což je jiný obecný objekt, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6783c-215">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6783c-216">Třída `List<>` ukládá kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="6783c-216">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="6783c-217">Argument typu deklaruje typ objektů uložených v `List<>`.</span><span class="sxs-lookup"><span data-stu-id="6783c-217">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="6783c-218">Text JSON představuje kolekci objektů úložiště, takže je argument typu `Repository`.</span><span class="sxs-lookup"><span data-stu-id="6783c-218">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="6783c-219">V této části už skoro jste hotovi.</span><span class="sxs-lookup"><span data-stu-id="6783c-219">You're almost done with this section.</span></span> <span data-ttu-id="6783c-220">Teď, když jste převedli JSON C# na objekty, pojďme zobrazit název každého úložiště.</span><span class="sxs-lookup"><span data-stu-id="6783c-220">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="6783c-221">Nahraďte řádky, které se čtou:</span><span class="sxs-lookup"><span data-stu-id="6783c-221">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="6783c-222">s následujícím:</span><span class="sxs-lookup"><span data-stu-id="6783c-222">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="6783c-223">Zkompilujte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6783c-223">Compile and run the application.</span></span> <span data-ttu-id="6783c-224">Vypíše názvy úložišť, která jsou součástí .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="6783c-224">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="6783c-225">Řízení serializace</span><span class="sxs-lookup"><span data-stu-id="6783c-225">Controlling Serialization</span></span>

<span data-ttu-id="6783c-226">Než přidáte další funkce, předejte adresu `name` vlastnosti pomocí atributu `[JsonPropertyName]`.</span><span class="sxs-lookup"><span data-stu-id="6783c-226">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="6783c-227">Proveďte následující změny v deklaraci pole `name` v repo.cs:</span><span class="sxs-lookup"><span data-stu-id="6783c-227">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="6783c-228">Chcete-li použít atribut `[JsonPropertyName]`, budete muset přidat <xref:System.Text.Json.Serialization> oboru názvů do direktiv `using`:</span><span class="sxs-lookup"><span data-stu-id="6783c-228">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="6783c-229">Tato změna znamená, že potřebujete změnit kód, který zapisuje název každého úložiště v program.cs:</span><span class="sxs-lookup"><span data-stu-id="6783c-229">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="6783c-230">Spusťte `dotnet run`, abyste se ujistili, že jsou mapování správná.</span><span class="sxs-lookup"><span data-stu-id="6783c-230">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="6783c-231">Měl by se zobrazit stejný výstup jako předtím.</span><span class="sxs-lookup"><span data-stu-id="6783c-231">You should see the same output as before.</span></span>

<span data-ttu-id="6783c-232">Pojďme ještě před přidáním nových funkcí udělat nějakou další změnu.</span><span class="sxs-lookup"><span data-stu-id="6783c-232">Let's make one more change before adding new features.</span></span> <span data-ttu-id="6783c-233">Metoda `ProcessRepositories` může provádět asynchronní práci a vracet kolekci úložišť.</span><span class="sxs-lookup"><span data-stu-id="6783c-233">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="6783c-234">Pojďme z této metody vracet `List<Repository>` a přesunete kód, který zapisuje informace do metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="6783c-234">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="6783c-235">Změňte podpis `ProcessRepositories` a vraťte úkol, jehož výsledkem je seznam objektů `Repository`:</span><span class="sxs-lookup"><span data-stu-id="6783c-235">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="6783c-236">Pak jednoduše vraťte úložiště po zpracování odpovědi JSON:</span><span class="sxs-lookup"><span data-stu-id="6783c-236">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="6783c-237">Kompilátor vygeneruje objekt `Task<T>` pro návrat, protože jste tuto metodu označili jako `async`.</span><span class="sxs-lookup"><span data-stu-id="6783c-237">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="6783c-238">Pak upravíte metodu `Main` tak, aby zachytit tyto výsledky a zapsala jednotlivé názvy úložišť do konzoly.</span><span class="sxs-lookup"><span data-stu-id="6783c-238">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="6783c-239">Vaše metoda `Main` nyní vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="6783c-239">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="6783c-240">Přečtěte si další informace</span><span class="sxs-lookup"><span data-stu-id="6783c-240">Reading More Information</span></span>

<span data-ttu-id="6783c-241">Pojďme to dokončit zpracováním několika dalších vlastností v paketu JSON, které se odesílají z rozhraní API GitHubu.</span><span class="sxs-lookup"><span data-stu-id="6783c-241">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="6783c-242">Nebudete chtít všechno přidat, ale přidáním několika vlastností se ukáže několik dalších funkcí tohoto C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="6783c-242">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="6783c-243">Pojďme začít přidáním několika jednoduchých typů do definice `Repository` třídy.</span><span class="sxs-lookup"><span data-stu-id="6783c-243">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="6783c-244">Přidejte tyto vlastnosti do této třídy:</span><span class="sxs-lookup"><span data-stu-id="6783c-244">Add these properties to that class:</span></span>

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

<span data-ttu-id="6783c-245">Tyto vlastnosti mají předdefinované převody z typu řetězce (což je to, co pakety JSON obsahují) k cílovému typu.</span><span class="sxs-lookup"><span data-stu-id="6783c-245">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="6783c-246">Typ <xref:System.Uri> může být pro vás nový.</span><span class="sxs-lookup"><span data-stu-id="6783c-246">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="6783c-247">Představuje identifikátor URI, nebo v tomto případě adresu URL.</span><span class="sxs-lookup"><span data-stu-id="6783c-247">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="6783c-248">V případě `Uri` a `int`ch typů platí, že pokud paket JSON obsahuje data, která nejsou převedena na cílový typ, akce serializace vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="6783c-248">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="6783c-249">Jakmile je přidáte, aktualizujte metodu `Main`, aby zobrazovala tyto prvky:</span><span class="sxs-lookup"><span data-stu-id="6783c-249">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="6783c-250">Jako poslední krok Pojďme přidat informace pro poslední operaci Push.</span><span class="sxs-lookup"><span data-stu-id="6783c-250">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="6783c-251">Tyto informace jsou v odpovědi JSON formátované tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="6783c-251">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="6783c-252">Tento formát nedodržuje žádné standardní <xref:System.DateTime> formáty .NET.</span><span class="sxs-lookup"><span data-stu-id="6783c-252">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="6783c-253">Z tohoto důvodu budete muset napsat vlastní metodu převodu.</span><span class="sxs-lookup"><span data-stu-id="6783c-253">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="6783c-254">Pravděpodobně nebudete chtít, aby Nezpracovaný řetězec byl vystaven uživatelům třídy `Repository`.</span><span class="sxs-lookup"><span data-stu-id="6783c-254">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="6783c-255">Atributy mohou také určovat.</span><span class="sxs-lookup"><span data-stu-id="6783c-255">Attributes can help control that as well.</span></span> <span data-ttu-id="6783c-256">Nejprve definujte vlastnost `public`, která bude obsahovat řetězcové vyjádření data a času ve vaší třídě `Repository` a vlastnost `LastPush` `readonly`, která vrací formátovaný řetězec, který představuje vrácené datum:</span><span class="sxs-lookup"><span data-stu-id="6783c-256">First, define a `public` property that will hold the string representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns a formatted string that represents the returned date:</span></span>

```csharp
[JsonPropertyName(Name="pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

<span data-ttu-id="6783c-257">Pojďme přecházet na nové konstrukce, které jsme právě definovali.</span><span class="sxs-lookup"><span data-stu-id="6783c-257">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="6783c-258">Vlastnost `LastPush` je definována pomocí *člena Expression-těle* pro přistupující objekt `get`.</span><span class="sxs-lookup"><span data-stu-id="6783c-258">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="6783c-259">Neexistuje žádný přistupující objekt `set`.</span><span class="sxs-lookup"><span data-stu-id="6783c-259">There is no `set` accessor.</span></span> <span data-ttu-id="6783c-260">Vynechání přístupového objektu `set` je způsob, jakým definujete vlastnost C# *jen pro čtení* v.</span><span class="sxs-lookup"><span data-stu-id="6783c-260">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="6783c-261">(Ano, můžete vytvořit vlastnosti *pouze pro zápis* v C#, ale jejich hodnota je omezená.) Metoda <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analyzuje řetězec a vytvoří objekt <xref:System.DateTime> pomocí poskytnutého formátu data a přidá další metadata do `DateTime` pomocí objektu `CultureInfo`.</span><span class="sxs-lookup"><span data-stu-id="6783c-261">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="6783c-262">Pokud operace analýzy není úspěšná, přistupující objekt vlastnosti vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="6783c-262">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="6783c-263">Chcete-li použít <xref:System.Globalization.CultureInfo.InvariantCulture>, bude nutné přidat obor názvů <xref:System.Globalization> do direktiv `using` v `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="6783c-263">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` directives in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="6783c-264">Nakonec přidejte do konzoly další příkaz Output a teď budete připraveni tuto aplikaci sestavit a spustit:</span><span class="sxs-lookup"><span data-stu-id="6783c-264">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="6783c-265">Verze by měla nyní odpovídat [ukázce dokončeno](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="6783c-265">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="6783c-266">Závěr</span><span class="sxs-lookup"><span data-stu-id="6783c-266">Conclusion</span></span>

<span data-ttu-id="6783c-267">V tomto kurzu jste si ukázali, jak vytvářet webové požadavky, analyzovat výsledek a zobrazovat vlastnosti těchto výsledků.</span><span class="sxs-lookup"><span data-stu-id="6783c-267">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="6783c-268">Přidali jste také nové balíčky jako závislosti ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="6783c-268">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="6783c-269">Seznámili jste se s některými funkcemi C# jazyka, který podporuje objektově orientované techniky.</span><span class="sxs-lookup"><span data-stu-id="6783c-269">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
