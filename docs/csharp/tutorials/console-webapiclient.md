---
title: Vytvoření klienta REST pomocí rozhraní .NET Core
description: Tento kurz vás naučí řadu funkcí v .NET Core a jazyk C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 5796df2d2fd8c4d9aaca783d720448c90858c067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156854"
---
# <a name="rest-client"></a><span data-ttu-id="9eb1e-103">Klient REST</span><span class="sxs-lookup"><span data-stu-id="9eb1e-103">REST client</span></span>

<span data-ttu-id="9eb1e-104">Tento kurz vás naučí řadu funkcí v .NET Core a jazyk C#.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="9eb1e-105">Dozvíte se:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-105">You’ll learn:</span></span>

* <span data-ttu-id="9eb1e-106">Základy rozhraní příkazového příkazu jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-106">The basics of the .NET Core CLI.</span></span>
* <span data-ttu-id="9eb1e-107">Přehled funkcí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-107">An overview of C# Language features.</span></span>
* <span data-ttu-id="9eb1e-108">Správa závislostí pomocí NuGet</span><span class="sxs-lookup"><span data-stu-id="9eb1e-108">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="9eb1e-109">HTTP komunikace</span><span class="sxs-lookup"><span data-stu-id="9eb1e-109">HTTP Communications</span></span>
* <span data-ttu-id="9eb1e-110">Zpracování informací JSON</span><span class="sxs-lookup"><span data-stu-id="9eb1e-110">Processing JSON information</span></span>
* <span data-ttu-id="9eb1e-111">Správa konfigurace pomocí atributů.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-111">Managing configuration with Attributes.</span></span>

<span data-ttu-id="9eb1e-112">Vytvoříte aplikaci, která vydává požadavky HTTP do služby REST na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-112">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="9eb1e-113">Budete číst informace ve formátu JSON a převést, že paket JSON do C# objekty.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-113">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="9eb1e-114">Nakonec uvidíte, jak pracovat s objekty Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-114">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="9eb1e-115">V tomto kurzu je mnoho funkcí.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-115">There are many features in this tutorial.</span></span> <span data-ttu-id="9eb1e-116">Postavíme je jeden po druhém.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-116">Let’s build them one by one.</span></span>

<span data-ttu-id="9eb1e-117">Pokud dáváte přednost sledování spolu s [konečnou ukázkou](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) pro toto téma, můžete si ji stáhnout.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-117">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="9eb1e-118">Pokyny ke stažení naleznete v [tématu Ukázky a výukové programy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="9eb1e-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9eb1e-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9eb1e-119">Prerequisites</span></span>

<span data-ttu-id="9eb1e-120">Budete muset nastavit počítač pro spuštění jádra .NET.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-120">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="9eb1e-121">Pokyny k instalaci naleznete na stránce [Ke stažení jádra .NET.](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="9eb1e-121">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="9eb1e-122">Tuto aplikaci můžete spustit ve Windows, Linuxu, macOS nebo v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-122">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="9eb1e-123">Budete muset nainstalovat svůj oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-123">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="9eb1e-124">Níže uvedené popisy používají [Visual Studio Code](https://code.visualstudio.com/), což je open source editor napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-124">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="9eb1e-125">Nicméně, můžete použít bez ohledu na nástroje, které jsou pohodlné s.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-125">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="9eb1e-126">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="9eb1e-126">Create the Application</span></span>

<span data-ttu-id="9eb1e-127">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-127">The first step is to create a new application.</span></span> <span data-ttu-id="9eb1e-128">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-128">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="9eb1e-129">Ať je to aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-129">Make that the current directory.</span></span> <span data-ttu-id="9eb1e-130">V okně konzoly zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-130">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebApiClient
```

<span data-ttu-id="9eb1e-131">Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="9eb1e-131">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="9eb1e-132">Název projektu je "WebApiClient".</span><span class="sxs-lookup"><span data-stu-id="9eb1e-132">The project name is "WebApiClient".</span></span> <span data-ttu-id="9eb1e-133">Vzhledem k tomu, že se jedná o nový projekt, žádná ze závislostí není na místě.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-133">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="9eb1e-134">První spuštění stáhne rozhraní .NET Core framework, nainstaluje vývojový certifikát a spustí správce balíčků NuGet a obnoví chybějící závislosti.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-134">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="9eb1e-135">Než začnete provádět změny, zadejte `dotnet run` na příkazovém řádku příkaz[(viz poznámka)](#dotnet-restore-note)a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="9eb1e-136">`dotnet run`automaticky `dotnet restore` provádí, pokud ve vašem prostředí chybí závislosti.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="9eb1e-137">Také provádí, `dotnet build` pokud je potřeba znovu sestavit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="9eb1e-138">Po počátečním nastavení budete muset `dotnet restore` spustit `dotnet build` nebo pouze tehdy, když to dává smysl pro váš projekt.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="9eb1e-139">Přidání nových závislostí</span><span class="sxs-lookup"><span data-stu-id="9eb1e-139">Adding New Dependencies</span></span>

<span data-ttu-id="9eb1e-140">Jedním z klíčových cílů návrhu pro .NET Core je minimalizovat velikost instalace .NET.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="9eb1e-141">Pokud aplikace potřebuje další knihovny pro některé z jeho funkcí, přidáte\*tyto závislosti do souboru projektu C# ( .csproj).</span><span class="sxs-lookup"><span data-stu-id="9eb1e-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="9eb1e-142">Pro náš příklad budete muset přidat `System.Runtime.Serialization.Json` balíček, takže vaše aplikace může zpracovávat odpovědi JSON.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="9eb1e-143">Budete potřebovat balíček `System.Runtime.Serialization.Json` pro tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="9eb1e-144">Přidejte jej do projektu spuštěním následujícího příkazu [rozhraní PŘÍKAZU .NET:](../../core/tools/dotnet-add-package.md)</span><span class="sxs-lookup"><span data-stu-id="9eb1e-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="9eb1e-145">Vytváření webových požadavků</span><span class="sxs-lookup"><span data-stu-id="9eb1e-145">Making Web Requests</span></span>

<span data-ttu-id="9eb1e-146">Nyní můžete začít načítat data z webu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="9eb1e-147">V této aplikaci budete číst informace z [GitHub API](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="9eb1e-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="9eb1e-148">Přečtěme si informace o projektech pod zastřešujícím programem [.NET Foundation.](https://www.dotnetfoundation.org/)</span><span class="sxs-lookup"><span data-stu-id="9eb1e-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="9eb1e-149">Začnete tím, že žádost github api načíst informace o projektech.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="9eb1e-150">Koncový bod, který budete <https://api.github.com/orgs/dotnet/repos>používat, je: .</span><span class="sxs-lookup"><span data-stu-id="9eb1e-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="9eb1e-151">Chcete načíst všechny informace o těchto projektech, takže budete používat požadavek HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="9eb1e-152">Váš prohlížeč také používá požadavky HTTP GET, takže můžete tuto adresu URL vložit do prohlížeče a zjistit, jaké informace budete dostávat a zpracovávat.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="9eb1e-153">Třídu <xref:System.Net.Http.HttpClient> používáte k výrobě webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="9eb1e-154">Stejně jako všechna moderní <xref:System.Net.Http.HttpClient> rozhraní API .NET podporuje pouze asynchronní metody pro dlouhotrvající rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="9eb1e-155">Začněte tím, že asynchronní metodu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-155">Start by making an async method.</span></span> <span data-ttu-id="9eb1e-156">Budete vyplnit implementaci při vytváření funkce aplikace.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="9eb1e-157">Začněte otevřením souboru `program.cs` v adresáři projektu `Program` a přidáním následující metody do třídy:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="9eb1e-158">Budete muset přidat direktivu `using` v `Main` horní části metody tak, aby <xref:System.Threading.Tasks.Task> kompilátor Jazyka C# rozpozná typ:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-158">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="9eb1e-159">Pokud vytvoříte projekt v tomto okamžiku, zobrazí se upozornění generované pro tuto metodu, protože neobsahuje žádné `await` operátory a bude spuštěnsynchronně.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="9eb1e-160">Prozatím to ignorujte; při vyplňování `await` metody přidáte operátory.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="9eb1e-161">Dále přejmenujte obor názvů `namespace` definovaný v příkazu z jeho výchozí ho `ConsoleApp` `WebAPIClient`na .</span><span class="sxs-lookup"><span data-stu-id="9eb1e-161">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="9eb1e-162">Později definujeme `repo` třídu v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-162">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="9eb1e-163">Dále aktualizujte `Main` metodu pro volání této metody.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-163">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="9eb1e-164">Metoda `ProcessRepositories` vrátí úkol a neměli byste ukončit program před dokončením této úlohy.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-164">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="9eb1e-165">Proto je nutné změnit `Main`podpis .</span><span class="sxs-lookup"><span data-stu-id="9eb1e-165">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="9eb1e-166">Přidejte `async` modifikátor a změňte návratový typ na `Task`.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-166">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="9eb1e-167">Potom v těle metody přidejte volání `ProcessRepositories`.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-167">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="9eb1e-168">Přidejte `await` klíčové slovo do volání této metody:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-168">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="9eb1e-169">Nyní máte program, který nedělá nic, ale dělá to asynchronně.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-169">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="9eb1e-170">Pojďme to zlepšit.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-170">Let's improve it.</span></span>

<span data-ttu-id="9eb1e-171">Nejprve potřebujete objekt, který je schopen načíst data z webu; můžete použít <xref:System.Net.Http.HttpClient> k tomu, že.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-171">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="9eb1e-172">Tento objekt zpracovává požadavek a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-172">This object handles the request and the responses.</span></span> <span data-ttu-id="9eb1e-173">Vytvořte instanci tohoto typu ve `Program` třídě uvnitř *Program.cs* souboru.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-173">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

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

<span data-ttu-id="9eb1e-174">Vraťme se k `ProcessRepositories` metodě a vyplňte její první verzi:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-174">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="9eb1e-175">Budete také muset přidat dvě `using` nové direktivy v horní části souboru pro tento kompilovat:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-175">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="9eb1e-176">Tato první verze vytvoří webový požadavek na čtení seznamu všech úložišť v rámci organizace dotnet foundation.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-176">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="9eb1e-177">(GitHub ID pro .NET Foundation je 'dotnet').</span><span class="sxs-lookup"><span data-stu-id="9eb1e-177">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="9eb1e-178">Prvních několik řádků nastavit <xref:System.Net.Http.HttpClient> pro tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-178">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="9eb1e-179">Nejprve je nakonfigurován tak, aby přijímal odpovědi GitHub JSON.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-179">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="9eb1e-180">Tento formát je jednoduše JSON.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-180">This format is simply JSON.</span></span> <span data-ttu-id="9eb1e-181">Další řádek přidá hlavičku uživatelského agenta ke všem požadavkům z tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-181">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="9eb1e-182">Tyto dvě hlavičky jsou kontrolovány kódem serveru GitHub a jsou nezbytné k načtení informací z GitHubu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-182">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="9eb1e-183">Po konfiguraci <xref:System.Net.Http.HttpClient>aplikace provedete webový požadavek a načtete odpověď.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-183">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="9eb1e-184">V této první verzi <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> použijete metodu pohodlí.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-184">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="9eb1e-185">Tato metoda pohodlí spustí úlohu, která vytvoří webový požadavek a potom, když se požadavek vrátí, přečte datový proud odpovědi a extrahuje obsah z datového proudu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-185">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="9eb1e-186">Tělo odpovědi je vrácena <xref:System.String>jako .</span><span class="sxs-lookup"><span data-stu-id="9eb1e-186">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="9eb1e-187">Řetězec je k dispozici po dokončení úlohy.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-187">The string is available when the task completes.</span></span>

<span data-ttu-id="9eb1e-188">Poslední dva řádky této metody čekají na tuto úlohu a vytisknout odpověď na konzolu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-188">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="9eb1e-189">Vytvořte aplikaci a spusťte ji.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-189">Build the app, and run it.</span></span> <span data-ttu-id="9eb1e-190">Upozornění sestavení je nyní pryč, protože `ProcessRepositories` `await` nyní obsahuje operátor.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-190">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="9eb1e-191">Zobrazí se dlouhé zobrazení textu ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-191">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="9eb1e-192">Zpracování výsledku JSON</span><span class="sxs-lookup"><span data-stu-id="9eb1e-192">Processing the JSON Result</span></span>

<span data-ttu-id="9eb1e-193">V tomto okamžiku jste napsali kód pro načtení odpovědi z webového serveru a zobrazení textu, který je obsažen v této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-193">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="9eb1e-194">Dále převeďte odpověď JSON na objekty Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-194">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="9eb1e-195">Třída <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> serializuje objekty do JSON a reserializuje JSON do objektů.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-195">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="9eb1e-196">Začněte definováním třídy `repo` představující objekt JSON vrácený z rozhraní API GitHub:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-196">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; }
    }
}
```

<span data-ttu-id="9eb1e-197">Vložte výše uvedený kód do nového souboru s názvem 'repo.cs'.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-197">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="9eb1e-198">Tato verze třídy představuje nejjednodušší cestu ke zpracování dat JSON.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-198">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="9eb1e-199">Název třídy a název člena odpovídají názvům použitým v paketu JSON namísto následujících konvencí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-199">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="9eb1e-200">Opravíte to tím, že později poskytnete některé atributy konfigurace.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-200">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="9eb1e-201">Tato třída ukazuje další důležitou funkci serializace json a deserializace: Ne všechna pole v paketu JSON jsou součástí této třídy.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-201">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="9eb1e-202">Serializátor JSON bude ignorovat informace, které nejsou zahrnuty v typu třídy, který se používá.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-202">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="9eb1e-203">Tato funkce usnadňuje vytváření typů, které pracují pouze s podmnožinou polí v paketu JSON.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-203">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="9eb1e-204">Teď, když jste vytvořili typ, pojďme ho rekonstruovat.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-204">Now that you've created the type, let's deserialize it.</span></span>

<span data-ttu-id="9eb1e-205">Dále použijete serializátor k převodu JSON na objekty Jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-205">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="9eb1e-206">Nahraďte <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> volání `ProcessRepositories` v metodě následujícími třemi řádky:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-206">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following three lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

<span data-ttu-id="9eb1e-207">Používáte nový obor názvů, takže ho budete muset přidat také v horní části souboru:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-207">You're using a new namespace, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Text.Json;
```

<span data-ttu-id="9eb1e-208">Všimněte si, že <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> nyní <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>používáte místo .</span><span class="sxs-lookup"><span data-stu-id="9eb1e-208">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="9eb1e-209">Serializátor používá datový proud namísto řetězce jako jeho zdroj.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-209">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="9eb1e-210">Vysvětlíme několik funkcí jazyka C#, které se používají ve druhém řádku předchozího fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-210">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="9eb1e-211">Prvním argumentem <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> je `await` výraz.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-211">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="9eb1e-212">(Další dva parametry jsou volitelné a jsou vynechány ve fragmentu kódu.) Await výrazy se mohou zobrazit téměř kdekoli ve vašem kódu, i když až do teď, jste je viděli pouze jako součást příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-212">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="9eb1e-213">Metoda `Deserialize` je *obecná*, což znamená, že je nutné zadat argumenty typu pro jaký druh objektů by měl být vytvořen z textu JSON.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-213">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="9eb1e-214">V tomto příkladu reserializujete `List<Repository>`na , což je <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>jiný obecný objekt, .</span><span class="sxs-lookup"><span data-stu-id="9eb1e-214">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9eb1e-215">Třída `List<>` ukládá kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-215">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="9eb1e-216">Argument typu deklaruje typ `List<>`objektů uložených v .</span><span class="sxs-lookup"><span data-stu-id="9eb1e-216">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="9eb1e-217">Text JSON představuje kolekci objektů repo, takže `Repository`argument typu je .</span><span class="sxs-lookup"><span data-stu-id="9eb1e-217">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="9eb1e-218">S touhle sekcí jsi skoro skončil.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-218">You're almost done with this section.</span></span> <span data-ttu-id="9eb1e-219">Teď, když jste převedli JSON na objekty Jazyka C#, zobrazme název každého úložiště.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-219">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="9eb1e-220">Nahraďte řádky s přečtenými řádky:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-220">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="9eb1e-221">s následujícími:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-221">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="9eb1e-222">Zkompilujte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-222">Compile and run the application.</span></span> <span data-ttu-id="9eb1e-223">Vytiskne názvy úložišť, které jsou součástí .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-223">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="9eb1e-224">Řízení serializace</span><span class="sxs-lookup"><span data-stu-id="9eb1e-224">Controlling Serialization</span></span>

<span data-ttu-id="9eb1e-225">Než přidáte další funkce, pojďme `name` adresu vlastnost `[JsonPropertyName]` pomocí atributu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-225">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="9eb1e-226">Proveďte následující změny v `name` deklaraci pole v repo.cs:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-226">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="9eb1e-227">Chcete-li použít `[JsonPropertyName]` atribut, budete <xref:System.Text.Json.Serialization> muset přidat `using` obor názvů do směrnic:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-227">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="9eb1e-228">Tato změna znamená, že je třeba změnit kód, který zapisuje název každého úložiště v program.cs:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-228">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="9eb1e-229">Proveďte, `dotnet run` abyste se ujistili, že máte správné mapování.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-229">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="9eb1e-230">Měli byste vidět stejný výstup jako předtím.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-230">You should see the same output as before.</span></span>

<span data-ttu-id="9eb1e-231">Před přidáním nových funkcí proveďte ještě jednu změnu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-231">Let's make one more change before adding new features.</span></span> <span data-ttu-id="9eb1e-232">Metoda `ProcessRepositories` může provést asynchronní práci a vrátit kolekci úložišť.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-232">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="9eb1e-233">Vraťme z `List<Repository>` této metody a přesuňte kód, který `Main` zapisuje informace do metody.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-233">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="9eb1e-234">Změňte podpis `ProcessRepositories` funkce a vraťte úkol, `Repository` jehož výsledkem je seznam objektů:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-234">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="9eb1e-235">Potom vraťte úložiště po zpracování odpovědi JSON:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-235">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="9eb1e-236">Kompilátor generuje `Task<T>` objekt pro návrat, protože jste tuto `async`metodu označili jako .</span><span class="sxs-lookup"><span data-stu-id="9eb1e-236">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="9eb1e-237">Potom pojďme upravit `Main` metodu tak, aby zachytí tyto výsledky a zapíše každý název úložiště do konzoly.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-237">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="9eb1e-238">Vaše `Main` metoda nyní vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-238">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="9eb1e-239">Čtení více informací</span><span class="sxs-lookup"><span data-stu-id="9eb1e-239">Reading More Information</span></span>

<span data-ttu-id="9eb1e-240">Dokončení tohoto zpracování zpracováním několik dalších vlastností v paketu JSON, který se odesílá z rozhraní API GitHub.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-240">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="9eb1e-241">Nebudete chtít uchopit všechno, ale přidání několika vlastností bude demonstrovat několik dalších funkcí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-241">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="9eb1e-242">Začněme přidáním několika dalších jednoduchých typů do definice třídy. `Repository`</span><span class="sxs-lookup"><span data-stu-id="9eb1e-242">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="9eb1e-243">Přidejte tyto vlastnosti do této třídy:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-243">Add these properties to that class:</span></span>

```csharp
[JsonPropertyName("description")]
public string Description { get; set; }

[JsonPropertyName("html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName("homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName("watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="9eb1e-244">Tyto vlastnosti mají předdefinované převody z typu řetězce (což je co obsahují pakety JSON) na cílový typ.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-244">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="9eb1e-245">Typ <xref:System.Uri> může být pro vás nový.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-245">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="9eb1e-246">Představuje identifikátor URI nebo v tomto případě adresu URL.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-246">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="9eb1e-247">V případě `Uri` a `int` typy, pokud paket JSON obsahuje data, která nepřevádí na cílový typ, akce serializace vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-247">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="9eb1e-248">Po přidání těchto aktualizací aktualizujte metodu `Main` tak, aby se tyto prvky zobrazily:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-248">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="9eb1e-249">Jako poslední krok přidáme informace pro poslední operaci push.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-249">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="9eb1e-250">Tyto informace jsou formátovány tímto způsobem v odpovědi JSON:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-250">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="9eb1e-251">Tento formát nedodržuje žádný ze <xref:System.DateTime> standardních formátů .NET.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-251">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="9eb1e-252">Z tohoto důvodu budete muset napsat vlastní metodu převodu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-252">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="9eb1e-253">Také pravděpodobně nechcete, aby byl nezpracovaný `Repository` řetězec vystaven uživatelům třídy.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-253">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="9eb1e-254">Atributy mohou pomoci řídit, že také.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-254">Attributes can help control that as well.</span></span> <span data-ttu-id="9eb1e-255">Nejprve `public` definujte vlastnost, která bude obsahovat řetězcovou `Repository` reprezentaci data a času ve vaší třídě a `LastPush` `readonly` vlastnost, která vrací formátovaný řetězec, který představuje vrácené datum:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-255">First, define a `public` property that will hold the string representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns a formatted string that represents the returned date:</span></span>

```csharp
[JsonPropertyName("pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

<span data-ttu-id="9eb1e-256">Projděme si nové konstrukce, které jsme právě definovali.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-256">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="9eb1e-257">Vlastnost `LastPush` je definována pomocí člena s `get` *výrazem pro* přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-257">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="9eb1e-258">Neexistuje žádný `set` přistupující odkaz.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-258">There is no `set` accessor.</span></span> <span data-ttu-id="9eb1e-259">Vynechání přistupujícího objektu `set` je způsob, jakým definujete vlastnost jen pro *čtení* v c#.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-259">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="9eb1e-260">(Ano, můžete vytvořit vlastnosti *pouze pro zápis* v c#, ale jejich hodnota je omezená.) Metoda <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> analyzuje řetězec a vytvoří <xref:System.DateTime> objekt pomocí zadaný formát data a přidá `DateTime` další `CultureInfo` metadata k použití objektu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-260">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="9eb1e-261">Pokud se operace analýzy nezdaří, přistupující objekt vlastnosti vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-261">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="9eb1e-262">Chcete-li <xref:System.Globalization.CultureInfo.InvariantCulture>použít , budete <xref:System.Globalization> muset přidat `using` obor `repo.cs`názvů do direktiv v :</span><span class="sxs-lookup"><span data-stu-id="9eb1e-262">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` directives in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="9eb1e-263">Nakonec přidejte ještě jeden výstupní příkaz do konzoly a jste připraveni vytvořit a spustit tuto aplikaci znovu:</span><span class="sxs-lookup"><span data-stu-id="9eb1e-263">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="9eb1e-264">Vaše verze by nyní měla odpovídat [dokončené ukázce](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="9eb1e-264">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="9eb1e-265">Závěr</span><span class="sxs-lookup"><span data-stu-id="9eb1e-265">Conclusion</span></span>

<span data-ttu-id="9eb1e-266">Tento kurz vám ukázal, jak vytvořit webové požadavky, analyzovat výsledek a zobrazit vlastnosti těchto výsledků.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-266">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="9eb1e-267">Také jste přidali nové balíčky jako závislosti v projektu.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-267">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="9eb1e-268">Viděli jste některé funkce jazyka C#, které podporují objektově orientované techniky.</span><span class="sxs-lookup"><span data-stu-id="9eb1e-268">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
