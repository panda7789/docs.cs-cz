---
title: Vytvoření klienta REST pomocí .NET Core
description: V tomto kurzu se naučíte řadou funkcí v .NET Core a v jazyce C#.
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 1d1d1bec8c6602e4fe34fa3ce243423290412736
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004852"
---
# <a name="rest-client"></a><span data-ttu-id="cbfc2-103">Klient REST</span><span class="sxs-lookup"><span data-stu-id="cbfc2-103">REST client</span></span>

<span data-ttu-id="cbfc2-104">V tomto kurzu se naučíte řadou funkcí v .NET Core a v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="cbfc2-105">Naučíte se:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-105">You’ll learn:</span></span>

* <span data-ttu-id="cbfc2-106">Základy .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-106">The basics of the .NET Core CLI.</span></span>
* <span data-ttu-id="cbfc2-107">Přehled funkcí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-107">An overview of C# Language features.</span></span>
* <span data-ttu-id="cbfc2-108">Správa závislostí pomocí NuGet</span><span class="sxs-lookup"><span data-stu-id="cbfc2-108">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="cbfc2-109">Komunikace HTTP</span><span class="sxs-lookup"><span data-stu-id="cbfc2-109">HTTP Communications</span></span>
* <span data-ttu-id="cbfc2-110">Zpracování informací JSON</span><span class="sxs-lookup"><span data-stu-id="cbfc2-110">Processing JSON information</span></span>
* <span data-ttu-id="cbfc2-111">Správa konfigurace s atributy.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-111">Managing configuration with Attributes.</span></span>

<span data-ttu-id="cbfc2-112">Vytvoříte aplikaci, která vydává požadavky HTTP na službu REST na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-112">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="cbfc2-113">Přečtete si informace ve formátu JSON a převeďte tento paket JSON na objekty C#.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-113">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="cbfc2-114">Nakonec uvidíte, jak pracovat s objekty C#.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-114">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="cbfc2-115">V tomto kurzu máte spoustu funkcí.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-115">There are many features in this tutorial.</span></span> <span data-ttu-id="cbfc2-116">Pojďme je sestavit jednou po jednom.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-116">Let’s build them one by one.</span></span>

<span data-ttu-id="cbfc2-117">Pokud chcete postupovat spolu s [závěrečnou ukázkou](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) tohoto tématu, můžete si ho stáhnout.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-117">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="cbfc2-118">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="cbfc2-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cbfc2-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cbfc2-119">Prerequisites</span></span>

<span data-ttu-id="cbfc2-120">Budete muset nastavit počítač tak, aby běžel .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-120">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="cbfc2-121">Pokyny k instalaci najdete na stránce [soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="cbfc2-121">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="cbfc2-122">Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-122">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="cbfc2-123">Budete muset nainstalovat svůj oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-123">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="cbfc2-124">Níže uvedené popisy používají [Visual Studio Code](https://code.visualstudio.com/), což je Open Source Editor pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-124">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="cbfc2-125">Můžete ale použít jakékoli nástroje, se kterými máte v pohodlí.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-125">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="cbfc2-126">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="cbfc2-126">Create the Application</span></span>

<span data-ttu-id="cbfc2-127">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-127">The first step is to create a new application.</span></span> <span data-ttu-id="cbfc2-128">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-128">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="cbfc2-129">Zajistěte, aby byl aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-129">Make that the current directory.</span></span> <span data-ttu-id="cbfc2-130">V okně konzoly zadejte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-130">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebAPIClient
```

<span data-ttu-id="cbfc2-131">Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="cbfc2-131">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="cbfc2-132">Název projektu je "WebAPIClient".</span><span class="sxs-lookup"><span data-stu-id="cbfc2-132">The project name is "WebAPIClient".</span></span> <span data-ttu-id="cbfc2-133">Vzhledem k tomu, že se jedná o nový projekt, není provedena žádná závislost.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-133">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="cbfc2-134">První spuštění stáhne rozhraní .NET Core Framework, nainstaluje certifikát pro vývoj a spustí Správce balíčků NuGet pro obnovení chybějících závislostí.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-134">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="cbfc2-135">Než začnete provádět úpravy, zadejte `dotnet run` ([Viz poznámku](#dotnet-restore-note)) na příkazovém řádku a spusťte tak aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="cbfc2-136">`dotnet run`provede automaticky `dotnet restore` v případě chybějících závislostí ve vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="cbfc2-137">Provádí se také `dotnet build` v případě, že vaše aplikace musí být znovu sestavena.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="cbfc2-138">Po počáteční instalaci budete muset spustit pouze `dotnet restore` nebo, `dotnet build` když to pro váš projekt dává smysl.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="cbfc2-139">Přidávání nových závislostí</span><span class="sxs-lookup"><span data-stu-id="cbfc2-139">Adding New Dependencies</span></span>

<span data-ttu-id="cbfc2-140">Jedním z klíčových cílů pro .NET Core je minimalizace velikosti instalace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="cbfc2-141">Pokud aplikace potřebuje další knihovny pro některé z jejích funkcí, přidejte tyto závislosti do souboru projektu C# ( \* . csproj).</span><span class="sxs-lookup"><span data-stu-id="cbfc2-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="cbfc2-142">V našem příkladu budete muset `System.Runtime.Serialization.Json` balíček přidat, aby mohla aplikace zpracovat odpovědi JSON.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="cbfc2-143">`System.Runtime.Serialization.Json`Pro tuto aplikaci budete potřebovat balíček.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="cbfc2-144">Přidejte ho do projektu spuštěním následujícího příkazu [rozhraní .NET CLI](../../core/tools/dotnet-add-package.md) :</span><span class="sxs-lookup"><span data-stu-id="cbfc2-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="cbfc2-145">Vytváření webových požadavků</span><span class="sxs-lookup"><span data-stu-id="cbfc2-145">Making Web Requests</span></span>

<span data-ttu-id="cbfc2-146">Teď jste připraveni začít načítat data z webu.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="cbfc2-147">V této aplikaci si přečtete informace z [rozhraní API GitHubu](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="cbfc2-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="cbfc2-148">Pojďme si přečíst informace o projektech v rámci [.NET Foundation](https://www.dotnetfoundation.org/) zastřešující.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="cbfc2-149">Začnete tím, že si vyžádáte rozhraní API GitHubu, abyste načetli informace o projektech.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="cbfc2-150">Koncový bod, který budete používat, je: <https://api.github.com/orgs/dotnet/repos> .</span><span class="sxs-lookup"><span data-stu-id="cbfc2-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="cbfc2-151">Chcete načíst všechny informace o těchto projektech, abyste použili požadavek HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="cbfc2-152">Váš prohlížeč používá také požadavky HTTP GET, takže můžete vložit tuto adresu URL do prohlížeče, abyste viděli informace, které budete dostávat a zpracovávat.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="cbfc2-153">Třídu můžete použít <xref:System.Net.Http.HttpClient> k vytváření webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="cbfc2-154">Stejně jako všechna moderní rozhraní API .NET <xref:System.Net.Http.HttpClient> podporuje pouze asynchronní metody pro svá dlouhotrvající rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="cbfc2-155">Začněte vytvořením asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-155">Start by making an async method.</span></span> <span data-ttu-id="cbfc2-156">Při sestavování funkčnosti aplikace naplníte implementaci.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="cbfc2-157">Začněte otevřením `program.cs` souboru v adresáři projektu a přidáním následující metody do `Program` třídy:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="cbfc2-158">V horní části metody bude nutné přidat `using` direktivu `Main` , aby kompilátor jazyka C# rozpoznal <xref:System.Threading.Tasks.Task> Typ:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-158">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="cbfc2-159">Pokud v tomto okamžiku sestavíte projekt, zobrazí se pro tuto metodu upozornění vygenerované, protože neobsahuje žádné `await` operátory a spustí se synchronně.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="cbfc2-160">Tuto chvíli ignorujte. operátory přidáte při `await` vyplňování metody.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="cbfc2-161">Dále aktualizujte `Main` metodu pro volání `ProcessRepositories` metody.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-161">Next, update the `Main` method to call the `ProcessRepositories` method.</span></span> <span data-ttu-id="cbfc2-162">`ProcessRepositories`Metoda vrátí úlohu a neukončí program před dokončením této úlohy.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-162">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="cbfc2-163">Proto je nutné změnit signaturu `Main` .</span><span class="sxs-lookup"><span data-stu-id="cbfc2-163">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="cbfc2-164">Přidejte `async` modifikátor a změňte návratový typ na `Task` .</span><span class="sxs-lookup"><span data-stu-id="cbfc2-164">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="cbfc2-165">Pak v těle metody přidejte volání do `ProcessRepositories` .</span><span class="sxs-lookup"><span data-stu-id="cbfc2-165">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="cbfc2-166">Přidejte `await` klíčové slovo do tohoto volání metody:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-166">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="cbfc2-167">Nyní máte program, který nic nedělá, ale asynchronně ho provede.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-167">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="cbfc2-168">Pojďme to vylepšit.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-168">Let's improve it.</span></span>

<span data-ttu-id="cbfc2-169">Nejprve potřebujete objekt, který je schopný načíst data z webu. k tomu můžete použít <xref:System.Net.Http.HttpClient> .</span><span class="sxs-lookup"><span data-stu-id="cbfc2-169">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="cbfc2-170">Tento objekt zpracovává požadavek a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-170">This object handles the request and the responses.</span></span> <span data-ttu-id="cbfc2-171">Vytvořte instanci jedné instance daného typu ve `Program` třídě uvnitř souboru *program.cs* .</span><span class="sxs-lookup"><span data-stu-id="cbfc2-171">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

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

<span data-ttu-id="cbfc2-172">Pojďme se zpátky k `ProcessRepositories` metodě a vyplnit první verzi IT:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-172">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="cbfc2-173">V horní části souboru budete muset přidat také dvě nové `using` direktivy, aby se mohla kompilovat:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-173">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="cbfc2-174">Tato první verze vytvoří webový požadavek na načtení seznamu všech úložišť v rámci organizace dotnet Foundation.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-174">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="cbfc2-175">(ID gitHubu pro .NET Foundation je "dotnet").</span><span class="sxs-lookup"><span data-stu-id="cbfc2-175">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="cbfc2-176">Prvních pár řádků, které jsou <xref:System.Net.Http.HttpClient> pro tento požadavek nastaveny.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-176">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="cbfc2-177">Nejdřív je nakonfigurovaný tak, aby přijímal odpovědi na adresu JSON pro GitHub.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-177">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="cbfc2-178">Tento formát je jednoduše JSON.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-178">This format is simply JSON.</span></span> <span data-ttu-id="cbfc2-179">Další řádek přidá hlavičku uživatelského agenta do všech požadavků od tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-179">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="cbfc2-180">Tato dvě záhlaví jsou kontrolována kódem serveru GitHub a jsou nutná k načtení informací z GitHubu.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-180">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="cbfc2-181">Po dokončení konfigurace aplikace vytvoříte <xref:System.Net.Http.HttpClient> webový požadavek a načtete odpověď.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-181">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="cbfc2-182">V této první verzi použijete <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> metodu usnadnění.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-182">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="cbfc2-183">Tato pohodlná metoda spustí úlohu, která provede webový požadavek, a poté, co požadavek vrátí, načte datový proud odpovědi a extrahuje obsah z datového proudu.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-183">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="cbfc2-184">Tělo odpovědi je vráceno jako <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="cbfc2-184">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="cbfc2-185">Řetězec je k dispozici po dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-185">The string is available when the task completes.</span></span>

<span data-ttu-id="cbfc2-186">Poslední dva řádky této metody čekají na daný úkol a pak vytiskněte odpověď do konzoly.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-186">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="cbfc2-187">Sestavte aplikaci a spusťte ji.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-187">Build the app, and run it.</span></span> <span data-ttu-id="cbfc2-188">Upozornění na sestavení je nyní pryč, protože `ProcessRepositories` nyní obsahuje `await` operátor.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-188">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="cbfc2-189">Zobrazí se dlouhé zobrazení textu ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-189">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="cbfc2-190">Zpracování výsledku JSON</span><span class="sxs-lookup"><span data-stu-id="cbfc2-190">Processing the JSON Result</span></span>

<span data-ttu-id="cbfc2-191">V tuto chvíli jste napsali kód, který načte odpověď z webového serveru, a zobrazí text obsažený v této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-191">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="cbfc2-192">Nyní převedeme tuto odpověď JSON na objekty jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-192">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="cbfc2-193"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType>Třída serializace objektů do formátu JSON a deserializace JSON do objektů.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-193">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="cbfc2-194">Začněte tím, že definujete třídu, která představuje `repo` objekt JSON vrácený z rozhraní API GitHubu:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-194">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

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

<span data-ttu-id="cbfc2-195">Výše uvedený kód vložte do nového souboru s názvem "úložiště. cs".</span><span class="sxs-lookup"><span data-stu-id="cbfc2-195">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="cbfc2-196">Tato verze třídy představuje nejjednodušší cestu pro zpracování dat JSON.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-196">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="cbfc2-197">Název třídy a název členu odpovídají názvům použitým v paketu JSON namísto následujících konvencí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-197">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="cbfc2-198">Opravte to tak, že později poskytnete nějaké konfigurační atributy.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-198">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="cbfc2-199">Tato třída ukazuje další důležitou funkci serializace a deserializace JSON: Ne všechna pole v paketu JSON jsou součástí této třídy.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-199">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="cbfc2-200">Serializátor JSON bude ignorovat informace, které nejsou zahrnuté do používaného typu třídy.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-200">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="cbfc2-201">Tato funkce usnadňuje vytváření typů, které pracují pouze s podmnožinou polí v paketu JSON.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-201">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="cbfc2-202">Teď, když jste vytvořili typ, Pojďme ho deserializovat.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-202">Now that you've created the type, let's deserialize it.</span></span>

<span data-ttu-id="cbfc2-203">V dalším kroku použijete serializátor k převedení formátu JSON na objekty jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-203">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="cbfc2-204">Nahraďte volání <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> v `ProcessRepositories` metodě následujícími řádky:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-204">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

<span data-ttu-id="cbfc2-205">Používáte nové obory názvů, takže ho budete muset přidat i na začátek souboru:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-205">You're using new namespaces, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Text.Json;
```

<span data-ttu-id="cbfc2-206">Všimněte si, že nyní používáte <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> místo <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> .</span><span class="sxs-lookup"><span data-stu-id="cbfc2-206">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="cbfc2-207">Serializátor používá jako svůj zdroj datový proud místo řetězce.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-207">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="cbfc2-208">Pojďme Vysvětleme několik funkcí jazyka C#, které jsou používány v druhém řádku předchozího fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-208">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="cbfc2-209">První argument pro <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> je `await` výraz.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-209">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="cbfc2-210">(Ostatní dva parametry jsou volitelné a jsou vynechány ve fragmentu kódu.) Výrazy await se můžou vyskytovat skoro kdekoli v kódu, a to i v případě, že jste je teď udělali jenom jako součást příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-210">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="cbfc2-211">`Deserialize`Metoda je *Obecná*, což znamená, že je nutné zadat argumenty typu pro typ objektu, který by měl být VYTVOŘEN z textu JSON.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-211">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="cbfc2-212">V tomto příkladu provádíte deserializaci do `List<Repository>` , což je jiný obecný objekt, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="cbfc2-212">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cbfc2-213">`List<>`Třída ukládá kolekci objektů.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-213">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="cbfc2-214">Argument typu deklaruje typ objektů uložených v `List<>` .</span><span class="sxs-lookup"><span data-stu-id="cbfc2-214">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="cbfc2-215">Text JSON představuje kolekci objektů úložiště, takže je argument typu `Repository` .</span><span class="sxs-lookup"><span data-stu-id="cbfc2-215">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="cbfc2-216">V této části už skoro jste hotovi.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-216">You're almost done with this section.</span></span> <span data-ttu-id="cbfc2-217">Teď, když jste převedli JSON na objekty C#, pojďme zobrazit název každého úložiště.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-217">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="cbfc2-218">Nahraďte řádky, které se čtou:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-218">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="cbfc2-219">s následujícím:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-219">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="cbfc2-220">Zkompilujte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-220">Compile and run the application.</span></span> <span data-ttu-id="cbfc2-221">Vypíše názvy úložišť, která jsou součástí .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-221">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="cbfc2-222">Řízení serializace</span><span class="sxs-lookup"><span data-stu-id="cbfc2-222">Controlling Serialization</span></span>

<span data-ttu-id="cbfc2-223">Než přidáte více funkcí, pojďme tuto `name` vlastnost adresovat pomocí `[JsonPropertyName]` atributu.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-223">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="cbfc2-224">Proveďte následující změny v deklaraci `name` pole v repo.cs:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-224">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="cbfc2-225">Chcete-li použít `[JsonPropertyName]` atribut, budete muset přidat <xref:System.Text.Json.Serialization> obor názvů do `using` direktiv:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-225">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="cbfc2-226">Tato změna znamená, že potřebujete změnit kód, který zapisuje název každého úložiště v program.cs:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-226">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="cbfc2-227">Spusťte `dotnet run` , abyste se ujistili, že jsou mapování správná.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-227">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="cbfc2-228">Měl by se zobrazit stejný výstup jako předtím.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-228">You should see the same output as before.</span></span>

<span data-ttu-id="cbfc2-229">Pojďme ještě před přidáním nových funkcí udělat nějakou další změnu.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-229">Let's make one more change before adding new features.</span></span> <span data-ttu-id="cbfc2-230">`ProcessRepositories`Metoda může provádět asynchronní práci a vracet kolekci úložišť.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-230">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="cbfc2-231">Pojďme `List<Repository>` z této metody vracet a přesunete kód, který zapisuje informace do `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-231">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="cbfc2-232">Změnou signatury `ProcessRepositories` vrátíte úkol, jehož výsledkem je seznam `Repository` objektů:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-232">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="cbfc2-233">Pak jednoduše vraťte úložiště po zpracování odpovědi JSON:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-233">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="cbfc2-234">Kompilátor vygeneruje `Task<T>` objekt pro návrat, protože jste označili tuto metodu jako `async` .</span><span class="sxs-lookup"><span data-stu-id="cbfc2-234">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="cbfc2-235">Pak Pojďme `Main` metodu upravit tak, aby zachytit tyto výsledky a zapsala všechny názvy úložišť do konzoly.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-235">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="cbfc2-236">Vaše `Main` Metoda teď vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-236">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="cbfc2-237">Přečtěte si další informace</span><span class="sxs-lookup"><span data-stu-id="cbfc2-237">Reading More Information</span></span>

<span data-ttu-id="cbfc2-238">Pojďme to dokončit zpracováním několika dalších vlastností v paketu JSON, které se odesílají z rozhraní API GitHubu.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-238">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="cbfc2-239">Nebudete chtít všechno přidat, ale přidáním několika vlastností se ukáže několik dalších funkcí jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-239">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="cbfc2-240">Pojďme začít přidáním několika jednoduchých typů do `Repository` definice třídy.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-240">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="cbfc2-241">Přidejte tyto vlastnosti do této třídy:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-241">Add these properties to that class:</span></span>

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

<span data-ttu-id="cbfc2-242">Tyto vlastnosti mají předdefinované převody z typu řetězce (což je to, co pakety JSON obsahují) k cílovému typu.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-242">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="cbfc2-243"><xref:System.Uri>Typ může být pro vás nový.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-243">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="cbfc2-244">Představuje identifikátor URI, nebo v tomto případě adresu URL.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-244">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="cbfc2-245">V případě `Uri` typů a platí `int` , že pokud paket JSON obsahuje data, která nejsou převedena na cílový typ, akce serializace vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-245">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="cbfc2-246">Jakmile je přidáte, aktualizujte `Main` metodu tak, aby zobrazovala tyto prvky:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-246">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="cbfc2-247">Jako poslední krok Pojďme přidat informace pro poslední operaci Push.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-247">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="cbfc2-248">Tyto informace jsou v odpovědi JSON formátované tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-248">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="cbfc2-249">Tento formát je koordinovaný světový čas (UTC), takže získáte <xref:System.DateTime> hodnotu, jejíž <xref:System.DateTime.Kind%2A> vlastnost je <xref:System.DateTimeKind.Utc> .</span><span class="sxs-lookup"><span data-stu-id="cbfc2-249">That format is in Coordinated Universal Time (UTC) so you'll get a <xref:System.DateTime> value whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Utc>.</span></span> <span data-ttu-id="cbfc2-250">Pokud upřednostňujete datum reprezentované ve vašem časovém pásmu, budete muset napsat vlastní metodu převodu.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-250">If you prefer a date represented in your time zone, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="cbfc2-251">Nejprve definujte `public` vlastnost, která bude obsahovat reprezentaci UTC pro datum a čas ve vaší `Repository` třídě a `LastPush` `readonly` vlastnost, která vrátí datum převedené na místní čas:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-251">First, define a `public` property that will hold the UTC representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns the date converted to local time:</span></span>

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

<span data-ttu-id="cbfc2-252">Pojďme přecházet na nové konstrukce, které jsme právě definovali.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-252">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="cbfc2-253">`LastPush`Vlastnost je definována pomocí *člena Expression-těle* pro `get` přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-253">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="cbfc2-254">K dispozici není žádný `set` přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-254">There is no `set` accessor.</span></span> <span data-ttu-id="cbfc2-255">Vynechání `set` přístupového objektu je způsob, jakým definujete vlastnost *jen pro čtení* v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-255">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="cbfc2-256">(Ano, v jazyce C# můžete vytvořit vlastnosti *jen pro zápis* , ale jejich hodnota je omezená.)</span><span class="sxs-lookup"><span data-stu-id="cbfc2-256">(Yes, you can create *write-only* properties in C#, but their value is limited.)</span></span>

<span data-ttu-id="cbfc2-257">Nakonec přidejte do konzoly další příkaz Output a teď budete připraveni tuto aplikaci sestavit a spustit:</span><span class="sxs-lookup"><span data-stu-id="cbfc2-257">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="cbfc2-258">Verze by měla nyní odpovídat [ukázce dokončeno](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="cbfc2-258">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="cbfc2-259">Závěr</span><span class="sxs-lookup"><span data-stu-id="cbfc2-259">Conclusion</span></span>

<span data-ttu-id="cbfc2-260">V tomto kurzu jste si ukázali, jak vytvářet webové požadavky, analyzovat výsledek a zobrazovat vlastnosti těchto výsledků.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-260">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="cbfc2-261">Přidali jste také nové balíčky jako závislosti ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-261">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="cbfc2-262">Viděli jste některé z funkcí jazyka C#, které podporují objektově orientované techniky.</span><span class="sxs-lookup"><span data-stu-id="cbfc2-262">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
