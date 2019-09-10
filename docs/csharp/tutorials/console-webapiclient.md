---
title: Vytvoření klienta REST pomocí .NET Core
description: V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce.
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 001a9cbaae1cdb57b6451bc42ce326864f8dcf7b
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850975"
---
# <a name="rest-client"></a><span data-ttu-id="7f17f-103">Klient REST</span><span class="sxs-lookup"><span data-stu-id="7f17f-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="7f17f-104">Úvod</span><span class="sxs-lookup"><span data-stu-id="7f17f-104">Introduction</span></span>

<span data-ttu-id="7f17f-105">V tomto kurzu se naučíte řadou funkcí v .NET Core a v C# jazyce.</span><span class="sxs-lookup"><span data-stu-id="7f17f-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="7f17f-106">Naučíte se:</span><span class="sxs-lookup"><span data-stu-id="7f17f-106">You’ll learn:</span></span>

* <span data-ttu-id="7f17f-107">Základní informace o rozhraní příkazového řádku (CLI) .NET Core</span><span class="sxs-lookup"><span data-stu-id="7f17f-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
* <span data-ttu-id="7f17f-108">Přehled funkcí C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="7f17f-108">An overview of C# Language features.</span></span>
* <span data-ttu-id="7f17f-109">Správa závislostí pomocí NuGet</span><span class="sxs-lookup"><span data-stu-id="7f17f-109">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="7f17f-110">Komunikace HTTP</span><span class="sxs-lookup"><span data-stu-id="7f17f-110">HTTP Communications</span></span>
* <span data-ttu-id="7f17f-111">Zpracování informací JSON</span><span class="sxs-lookup"><span data-stu-id="7f17f-111">Processing JSON information</span></span>
* <span data-ttu-id="7f17f-112">Správa konfigurace s atributy.</span><span class="sxs-lookup"><span data-stu-id="7f17f-112">Managing configuration with Attributes.</span></span>

<span data-ttu-id="7f17f-113">Vytvoříte aplikaci, která vydává požadavky HTTP na službu REST na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="7f17f-114">Přečtete si informace ve formátu JSON a převeďte tento paket JSON na C# objekty.</span><span class="sxs-lookup"><span data-stu-id="7f17f-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="7f17f-115">Nakonec uvidíte, jak pracovat s C# objekty.</span><span class="sxs-lookup"><span data-stu-id="7f17f-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="7f17f-116">V tomto kurzu máte spoustu funkcí.</span><span class="sxs-lookup"><span data-stu-id="7f17f-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="7f17f-117">Pojďme je sestavit jednou po jednom.</span><span class="sxs-lookup"><span data-stu-id="7f17f-117">Let’s build them one by one.</span></span>

<span data-ttu-id="7f17f-118">Pokud chcete postupovat spolu s [závěrečnou ukázkou](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) tohoto tématu, můžete si ho stáhnout.</span><span class="sxs-lookup"><span data-stu-id="7f17f-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="7f17f-119">Pokyny ke stažení najdete v tématu [ukázky a kurzy](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="7f17f-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7f17f-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f17f-120">Prerequisites</span></span>

<span data-ttu-id="7f17f-121">Budete muset nastavit počítač tak, aby běžel .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7f17f-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="7f17f-122">Pokyny k instalaci najdete na stránce [soubory ke stažení pro .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="7f17f-122">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="7f17f-123">Tuto aplikaci můžete spustit na Windows, Linux, macOS nebo v kontejneru Docker.</span><span class="sxs-lookup"><span data-stu-id="7f17f-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="7f17f-124">Budete muset nainstalovat svůj oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="7f17f-125">Níže uvedené popisy používají [Visual Studio Code](https://code.visualstudio.com/), což je Open Source Editor pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="7f17f-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="7f17f-126">Můžete ale použít jakékoli nástroje, se kterými máte v pohodlí.</span><span class="sxs-lookup"><span data-stu-id="7f17f-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="7f17f-127">Vytvoření aplikace</span><span class="sxs-lookup"><span data-stu-id="7f17f-127">Create the Application</span></span>

<span data-ttu-id="7f17f-128">Prvním krokem je vytvoření nové aplikace.</span><span class="sxs-lookup"><span data-stu-id="7f17f-128">The first step is to create a new application.</span></span> <span data-ttu-id="7f17f-129">Otevřete příkazový řádek a vytvořte nový adresář pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7f17f-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="7f17f-130">Zajistěte, aby byl aktuální adresář.</span><span class="sxs-lookup"><span data-stu-id="7f17f-130">Make that the current directory.</span></span> <span data-ttu-id="7f17f-131">Zadejte příkaz `dotnet new console` na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="7f17f-131">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="7f17f-132">Tím se vytvoří počáteční soubory pro základní aplikaci "Hello World".</span><span class="sxs-lookup"><span data-stu-id="7f17f-132">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="7f17f-133">Vzhledem k tomu, že se jedná o nový projekt, není zavedena žádná závislost, takže první spuštění stáhne rozhraní .NET Core Framework, nainstaluje certifikát pro vývoj a spustí Správce balíčků NuGet pro obnovení chybějících závislostí.</span><span class="sxs-lookup"><span data-stu-id="7f17f-133">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework, install a development certificate and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="7f17f-134">Než začnete provádět úpravy, zadejte `dotnet run` ([Viz poznámku](#dotnet-restore-note)) na příkazovém řádku a spusťte tak aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7f17f-134">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="7f17f-135">`dotnet run`provede `dotnet restore` automaticky v případě chybějících závislostí ve vašem prostředí.</span><span class="sxs-lookup"><span data-stu-id="7f17f-135">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="7f17f-136">Provádí `dotnet build` se také v případě, že vaše aplikace musí být znovu sestavena.</span><span class="sxs-lookup"><span data-stu-id="7f17f-136">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="7f17f-137">Po počáteční instalaci budete muset spustit `dotnet restore` pouze nebo `dotnet build` , když to pro váš projekt dává smysl.</span><span class="sxs-lookup"><span data-stu-id="7f17f-137">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="7f17f-138">Přidávání nových závislostí</span><span class="sxs-lookup"><span data-stu-id="7f17f-138">Adding New Dependencies</span></span>

<span data-ttu-id="7f17f-139">Jedním z klíčových cílů pro .NET Core je minimalizace velikosti instalace rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="7f17f-139">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="7f17f-140">Pokud aplikace potřebuje pro některé z jejích funkcí další knihovny, přidejte tyto závislosti do souboru C# projektu (\*. csproj).</span><span class="sxs-lookup"><span data-stu-id="7f17f-140">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="7f17f-141">V našem příkladu budete muset přidat `System.Runtime.Serialization.Json` balíček, aby aplikace mohla zpracovávat odpovědi JSON.</span><span class="sxs-lookup"><span data-stu-id="7f17f-141">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="7f17f-142">Otevřete soubor `csproj` projektu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-142">Open your `csproj` project file.</span></span> <span data-ttu-id="7f17f-143">První řádek souboru by měl vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="7f17f-143">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="7f17f-144">Hned za tento řádek přidejte následující:</span><span class="sxs-lookup"><span data-stu-id="7f17f-144">Add the following immediately after this line:</span></span>

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup>
```

<span data-ttu-id="7f17f-145">Většina editorů kódu bude poskytovat dokončování pro různé verze těchto knihoven.</span><span class="sxs-lookup"><span data-stu-id="7f17f-145">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="7f17f-146">Obvykle budete chtít použít nejnovější verzi balíčku, který přidáte.</span><span class="sxs-lookup"><span data-stu-id="7f17f-146">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="7f17f-147">Je však důležité se ujistit, že verze všech balíčků odpovídají a že také odpovídají verzi rozhraní .NET Core Application Framework.</span><span class="sxs-lookup"><span data-stu-id="7f17f-147">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="7f17f-148">Po provedení těchto změn proveďte `dotnet restore` příkaz ([Viz poznámku](#dotnet-restore-note)), aby se balíček nainstaloval do vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="7f17f-148">After you've made these changes, execute `dotnet restore` ([see note](#dotnet-restore-note)) so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="7f17f-149">Vytváření webových požadavků</span><span class="sxs-lookup"><span data-stu-id="7f17f-149">Making Web Requests</span></span>

<span data-ttu-id="7f17f-150">Teď jste připraveni začít načítat data z webu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-150">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="7f17f-151">V této aplikaci si přečtete informace z [rozhraní API GitHubu](https://developer.github.com/v3/).</span><span class="sxs-lookup"><span data-stu-id="7f17f-151">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="7f17f-152">Pojďme si přečíst informace o projektech v rámci [.NET Foundation](https://www.dotnetfoundation.org/) zastřešující.</span><span class="sxs-lookup"><span data-stu-id="7f17f-152">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="7f17f-153">Začnete tím, že si vyžádáte rozhraní API GitHubu, abyste načetli informace o projektech.</span><span class="sxs-lookup"><span data-stu-id="7f17f-153">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="7f17f-154">Koncový bod, který budete používat, <https://api.github.com/orgs/dotnet/repos>je:.</span><span class="sxs-lookup"><span data-stu-id="7f17f-154">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="7f17f-155">Chcete načíst všechny informace o těchto projektech, abyste použili požadavek HTTP GET.</span><span class="sxs-lookup"><span data-stu-id="7f17f-155">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="7f17f-156">Váš prohlížeč používá také požadavky HTTP GET, takže můžete vložit tuto adresu URL do prohlížeče, abyste viděli informace, které budete dostávat a zpracovávat.</span><span class="sxs-lookup"><span data-stu-id="7f17f-156">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="7f17f-157"><xref:System.Net.Http.HttpClient> Třídu můžete použít k vytváření webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="7f17f-157">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="7f17f-158">Stejně jako všechna moderní rozhraní API <xref:System.Net.Http.HttpClient> .NET podporuje pouze asynchronní metody pro svá dlouhotrvající rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="7f17f-158">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="7f17f-159">Začněte vytvořením asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="7f17f-159">Start by making an async method.</span></span> <span data-ttu-id="7f17f-160">Při sestavování funkčnosti aplikace naplníte implementaci.</span><span class="sxs-lookup"><span data-stu-id="7f17f-160">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="7f17f-161">Začněte otevřením `program.cs` souboru v adresáři projektu a přidáním následující metody `Program` do třídy:</span><span class="sxs-lookup"><span data-stu-id="7f17f-161">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="7f17f-162">Je nutné přidat `using` příkaz na začátek `Main` metody C# <xref:System.Threading.Tasks.Task> , aby kompilátor rozpoznal typ:</span><span class="sxs-lookup"><span data-stu-id="7f17f-162">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="7f17f-163">Pokud v tomto okamžiku sestavíte projekt, zobrazí se pro tuto metodu upozornění vygenerované, protože neobsahuje žádné `await` operátory a spustí se synchronně.</span><span class="sxs-lookup"><span data-stu-id="7f17f-163">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="7f17f-164">Tuto chvíli ignorujte. operátory přidáte `await` při vyplňování metody.</span><span class="sxs-lookup"><span data-stu-id="7f17f-164">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="7f17f-165">Dále přejmenujte obor názvů definovaný v `namespace` příkazu z jeho výchozí hodnoty `ConsoleApp` na `WebAPIClient`.</span><span class="sxs-lookup"><span data-stu-id="7f17f-165">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="7f17f-166">Později v tomto oboru názvů `repo` definujeme třídu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-166">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="7f17f-167">Dále aktualizujte `Main` metodu pro volání této metody.</span><span class="sxs-lookup"><span data-stu-id="7f17f-167">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="7f17f-168">`ProcessRepositories` Metoda vrátí úlohu a neukončí program před dokončením této úlohy.</span><span class="sxs-lookup"><span data-stu-id="7f17f-168">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="7f17f-169">Proto je nutné použít `Wait` metodu k blokování a čekání na dokončení úlohy:</span><span class="sxs-lookup"><span data-stu-id="7f17f-169">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="7f17f-170">Nyní máte program, který nic nedělá, ale asynchronně ho provede.</span><span class="sxs-lookup"><span data-stu-id="7f17f-170">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="7f17f-171">Pojďme to vylepšit.</span><span class="sxs-lookup"><span data-stu-id="7f17f-171">Let's improve it.</span></span>

<span data-ttu-id="7f17f-172">Nejprve potřebujete objekt, který je schopný načíst data z webu. <xref:System.Net.Http.HttpClient> k tomu můžete použít.</span><span class="sxs-lookup"><span data-stu-id="7f17f-172">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="7f17f-173">Tento objekt zpracovává požadavek a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="7f17f-173">This object handles the request and the responses.</span></span> <span data-ttu-id="7f17f-174">Vytvořte instanci jedné instance daného typu ve `Program` třídě uvnitř souboru program.cs.</span><span class="sxs-lookup"><span data-stu-id="7f17f-174">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

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

<span data-ttu-id="7f17f-175">Pojďme se zpátky k `ProcessRepositories` metodě a vyplnit první verzi IT:</span><span class="sxs-lookup"><span data-stu-id="7f17f-175">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="7f17f-176">V horní části souboru budete muset přidat také dvě nové příkazy using, aby se mohla kompilovat:</span><span class="sxs-lookup"><span data-stu-id="7f17f-176">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="7f17f-177">Tato první verze vytvoří webový požadavek na načtení seznamu všech úložišť v rámci organizace dotnet Foundation.</span><span class="sxs-lookup"><span data-stu-id="7f17f-177">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="7f17f-178">(ID gitHubu pro .NET Foundation je "dotnet").</span><span class="sxs-lookup"><span data-stu-id="7f17f-178">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="7f17f-179">Prvních pár řádků, které jsou <xref:System.Net.Http.HttpClient> pro tento požadavek nastaveny.</span><span class="sxs-lookup"><span data-stu-id="7f17f-179">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="7f17f-180">Nejdřív je nakonfigurovaný tak, aby přijímal odpovědi na adresu JSON pro GitHub.</span><span class="sxs-lookup"><span data-stu-id="7f17f-180">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="7f17f-181">Tento formát je jednoduše JSON.</span><span class="sxs-lookup"><span data-stu-id="7f17f-181">This format is simply JSON.</span></span> <span data-ttu-id="7f17f-182">Další řádek přidá hlavičku uživatelského agenta do všech požadavků od tohoto objektu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-182">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="7f17f-183">Tato dvě záhlaví jsou kontrolována kódem serveru GitHub a jsou nutná k načtení informací z GitHubu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-183">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="7f17f-184">Po dokončení konfigurace <xref:System.Net.Http.HttpClient>aplikace vytvoříte webový požadavek a načtete odpověď.</span><span class="sxs-lookup"><span data-stu-id="7f17f-184">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="7f17f-185">V této první verzi použijete <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> metodu usnadnění.</span><span class="sxs-lookup"><span data-stu-id="7f17f-185">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="7f17f-186">Tato pohodlná metoda spustí úlohu, která provede webový požadavek, a poté, co požadavek vrátí, načte datový proud odpovědi a extrahuje obsah z datového proudu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-186">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="7f17f-187">Tělo odpovědi je vráceno jako <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="7f17f-187">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="7f17f-188">Řetězec je k dispozici po dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-188">The string is available when the task completes.</span></span>

<span data-ttu-id="7f17f-189">Poslední dva řádky této metody čekají na daný úkol a pak vytiskněte odpověď do konzoly.</span><span class="sxs-lookup"><span data-stu-id="7f17f-189">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="7f17f-190">Sestavte aplikaci a spusťte ji.</span><span class="sxs-lookup"><span data-stu-id="7f17f-190">Build the app, and run it.</span></span> <span data-ttu-id="7f17f-191">Upozornění na sestavení je nyní pryč, protože `ProcessRepositories` nyní `await` obsahuje operátor.</span><span class="sxs-lookup"><span data-stu-id="7f17f-191">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="7f17f-192">Zobrazí se dlouhé zobrazení textu ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="7f17f-192">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="7f17f-193">Zpracování výsledku JSON</span><span class="sxs-lookup"><span data-stu-id="7f17f-193">Processing the JSON Result</span></span>

<span data-ttu-id="7f17f-194">V tuto chvíli jste napsali kód, který načte odpověď z webového serveru, a zobrazí text obsažený v této odpovědi.</span><span class="sxs-lookup"><span data-stu-id="7f17f-194">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="7f17f-195">Nyní převedeme tuto odpověď JSON na C# objekty.</span><span class="sxs-lookup"><span data-stu-id="7f17f-195">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="7f17f-196">Serializátor JSON převede data JSON na C# objekty.</span><span class="sxs-lookup"><span data-stu-id="7f17f-196">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="7f17f-197">Prvním úkolem je definovat typ C# třídy, který bude obsahovat informace, které z této odpovědi použijete.</span><span class="sxs-lookup"><span data-stu-id="7f17f-197">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="7f17f-198">Pojďme to sestavit pomalu, takže začněte jednoduchým C# typem, který obsahuje název úložiště:</span><span class="sxs-lookup"><span data-stu-id="7f17f-198">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

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

<span data-ttu-id="7f17f-199">Výše uvedený kód vložte do nového souboru s názvem "úložiště. cs".</span><span class="sxs-lookup"><span data-stu-id="7f17f-199">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="7f17f-200">Tato verze třídy představuje nejjednodušší cestu pro zpracování dat JSON.</span><span class="sxs-lookup"><span data-stu-id="7f17f-200">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="7f17f-201">Název třídy a název členu odpovídají názvům použitým v paketu JSON namísto následujících C# konvencí.</span><span class="sxs-lookup"><span data-stu-id="7f17f-201">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="7f17f-202">Opravte to tak, že později poskytnete nějaké konfigurační atributy.</span><span class="sxs-lookup"><span data-stu-id="7f17f-202">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="7f17f-203">Tato třída ukazuje další důležitou funkci serializace a deserializace JSON: Ne všechna pole v paketu JSON jsou součástí této třídy.</span><span class="sxs-lookup"><span data-stu-id="7f17f-203">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="7f17f-204">Serializátor JSON bude ignorovat informace, které nejsou zahrnuté do používaného typu třídy.</span><span class="sxs-lookup"><span data-stu-id="7f17f-204">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="7f17f-205">Tato funkce usnadňuje vytváření typů, které pracují pouze s podmnožinou polí v paketu JSON.</span><span class="sxs-lookup"><span data-stu-id="7f17f-205">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="7f17f-206">Teď, když jste vytvořili typ, Pojďme ho deserializovat.</span><span class="sxs-lookup"><span data-stu-id="7f17f-206">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="7f17f-207">Budete muset vytvořit <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> objekt.</span><span class="sxs-lookup"><span data-stu-id="7f17f-207">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="7f17f-208">Tento objekt musí znát typ CLR očekávaný pro načtený paket JSON.</span><span class="sxs-lookup"><span data-stu-id="7f17f-208">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="7f17f-209">Paket z GitHubu obsahuje sekvenci úložišť, takže `List<repo>` je to správný typ.</span><span class="sxs-lookup"><span data-stu-id="7f17f-209">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="7f17f-210">Do `ProcessRepositories` metody přidejte následující řádek:</span><span class="sxs-lookup"><span data-stu-id="7f17f-210">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="7f17f-211">Používáte dva nové obory názvů, takže je budete muset přidat také:</span><span class="sxs-lookup"><span data-stu-id="7f17f-211">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="7f17f-212">V dalším kroku použijete serializátor k převedení JSON na C# objekty.</span><span class="sxs-lookup"><span data-stu-id="7f17f-212">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="7f17f-213">Nahraďte volání <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> `ProcessRepositories` v metodě následujícími dvěma řádky:</span><span class="sxs-lookup"><span data-stu-id="7f17f-213">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="7f17f-214">Všimněte si, že nyní používáte <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>místo.</span><span class="sxs-lookup"><span data-stu-id="7f17f-214">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="7f17f-215">Serializátor používá jako svůj zdroj datový proud místo řetězce.</span><span class="sxs-lookup"><span data-stu-id="7f17f-215">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="7f17f-216">Pojďme vysvětlit několik funkcí C# jazyka, které se používají ve druhém řádku výše.</span><span class="sxs-lookup"><span data-stu-id="7f17f-216">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="7f17f-217">Argumentem <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> `await` výrazu je výraz.</span><span class="sxs-lookup"><span data-stu-id="7f17f-217">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="7f17f-218">Výrazy await se můžou vyskytovat skoro kdekoli v kódu, a to i v případě, že jste je teď udělali jenom jako součást příkazu přiřazení.</span><span class="sxs-lookup"><span data-stu-id="7f17f-218">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="7f17f-219">Následně se `as` operátor převede z `object` typu doby kompilace na `List<repo>`.</span><span class="sxs-lookup"><span data-stu-id="7f17f-219">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span>
<span data-ttu-id="7f17f-220">Deklarace <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> deklaruje, že vrací objekt typu <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7f17f-220">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7f17f-221"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)>Vrátí typ, který jste zadali při jeho sestavení (`List<repo>` v tomto kurzu).</span><span class="sxs-lookup"><span data-stu-id="7f17f-221"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="7f17f-222">Pokud převod není úspěšný, `as` operátor vyhodnotí `null`, namísto vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="7f17f-222">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="7f17f-223">V této části už skoro jste hotovi.</span><span class="sxs-lookup"><span data-stu-id="7f17f-223">You're almost done with this section.</span></span> <span data-ttu-id="7f17f-224">Teď, když jste převedli JSON C# na objekty, pojďme zobrazit název každého úložiště.</span><span class="sxs-lookup"><span data-stu-id="7f17f-224">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="7f17f-225">Nahraďte řádky, které se čtou:</span><span class="sxs-lookup"><span data-stu-id="7f17f-225">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="7f17f-226">s následujícím:</span><span class="sxs-lookup"><span data-stu-id="7f17f-226">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="7f17f-227">Zkompilujte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7f17f-227">Compile and run the application.</span></span> <span data-ttu-id="7f17f-228">Vypíše názvy úložišť, která jsou součástí .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="7f17f-228">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="7f17f-229">Řízení serializace</span><span class="sxs-lookup"><span data-stu-id="7f17f-229">Controlling Serialization</span></span>

<span data-ttu-id="7f17f-230">Než přidáte více funkcí, pojďme tento `repo` typ adresovat a postupovat podle standardních C# konvencí.</span><span class="sxs-lookup"><span data-stu-id="7f17f-230">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="7f17f-231">Provedete to tak, že použijete anotaci `repo` typu s *atributy* , které řídí způsob fungování serializátoru JSON.</span><span class="sxs-lookup"><span data-stu-id="7f17f-231">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="7f17f-232">V takovém případě použijete tyto atributy k definování mapování mezi názvy klíčů JSON a názvy C# tříd a členů.</span><span class="sxs-lookup"><span data-stu-id="7f17f-232">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="7f17f-233">Používají <xref:System.Runtime.Serialization.DataContractAttribute> se dva atributy a <xref:System.Runtime.Serialization.DataMemberAttribute> .</span><span class="sxs-lookup"><span data-stu-id="7f17f-233">The two attributes used are the <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes.</span></span> <span data-ttu-id="7f17f-234">Podle konvence všechny třídy atributů končí v příponě `Attribute`.</span><span class="sxs-lookup"><span data-stu-id="7f17f-234">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="7f17f-235">Tuto příponu však nemusíte používat při použití atributu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-235">However, you do not need to use that suffix when you apply an attribute.</span></span>

<span data-ttu-id="7f17f-236">Atributy <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> jsou v jiné knihovně, takže je nutné přidat tuto knihovnu do souboru C# projektu jako závislost.</span><span class="sxs-lookup"><span data-stu-id="7f17f-236">The <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="7f17f-237">Přidejte následující řádek do `<ItemGroup>` části souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="7f17f-237">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="7f17f-238">Po uložení souboru spusťte `dotnet restore` příkaz ([Viz poznámku](#dotnet-restore-note)) pro načtení tohoto balíčku.</span><span class="sxs-lookup"><span data-stu-id="7f17f-238">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="7f17f-239">Pak otevřete `repo.cs` soubor.</span><span class="sxs-lookup"><span data-stu-id="7f17f-239">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="7f17f-240">Pojďme změnit název tak, aby používal velká písmena jazyka Pascal, a plně hláskovat název `Repository`</span><span class="sxs-lookup"><span data-stu-id="7f17f-240">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="7f17f-241">Pořád chceme mapovat uzly úložiště JSON na tento typ, takže budete muset přidat <xref:System.Runtime.Serialization.DataContractAttribute> atribut do deklarace třídy.</span><span class="sxs-lookup"><span data-stu-id="7f17f-241">We still want to map JSON 'repo' nodes to this type, so you'll need to add the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the class declaration.</span></span> <span data-ttu-id="7f17f-242">Nastavíte `Name` vlastnost atributu na název uzlů JSON, které jsou namapovány na tento typ:</span><span class="sxs-lookup"><span data-stu-id="7f17f-242">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="7f17f-243">Je členem <xref:System.Runtime.Serialization> oboru názvů, takže budete muset přidat příslušný `using` příkaz na začátek souboru: <xref:System.Runtime.Serialization.DataContractAttribute></span><span class="sxs-lookup"><span data-stu-id="7f17f-243">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="7f17f-244">Změnili jste název `repo` třídy na `Repository`, takže budete muset v program.cs udělat stejnou změnu názvu (některé editory můžou podporovat Refaktoring přejmenování, který tuto změnu provede automaticky:).</span><span class="sxs-lookup"><span data-stu-id="7f17f-244">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="7f17f-245">Nyní provedeme stejnou změnu s `name` polem <xref:System.Runtime.Serialization.DataMemberAttribute> pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="7f17f-245">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="7f17f-246">Proveďte následující změny v deklaraci `name` pole v repo.cs:</span><span class="sxs-lookup"><span data-stu-id="7f17f-246">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="7f17f-247">Tato změna znamená, že potřebujete změnit kód, který zapisuje název každého úložiště v program.cs:</span><span class="sxs-lookup"><span data-stu-id="7f17f-247">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="7f17f-248">Po následování a `dotnet run` se ujistěte, že jsou mapování správná. `dotnet build`</span><span class="sxs-lookup"><span data-stu-id="7f17f-248">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="7f17f-249">Měl by se zobrazit stejný výstup jako předtím.</span><span class="sxs-lookup"><span data-stu-id="7f17f-249">You should see the same output as before.</span></span> <span data-ttu-id="7f17f-250">Než my zpracujeme další vlastnosti z webového serveru, Pojďme udělat ještě jednu změnu `Repository` třídy.</span><span class="sxs-lookup"><span data-stu-id="7f17f-250">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="7f17f-251">`Name` Člen je veřejně přístupný pole.</span><span class="sxs-lookup"><span data-stu-id="7f17f-251">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="7f17f-252">To není dobrý postup orientovaný na objekt, takže ho můžeme změnit na vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7f17f-252">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="7f17f-253">Pro naše účely nepotřebujeme, aby při získávání nebo nastavování vlastnosti běžel žádný konkrétní kód, ale změna na vlastnost usnadňuje přidávání těchto změn později, aniž by došlo k `Repository` porušení kódu, který používá třídu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-253">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="7f17f-254">Odeberte definici pole a nahraďte ji pomocí [automaticky implementované vlastnosti](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span><span class="sxs-lookup"><span data-stu-id="7f17f-254">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="7f17f-255">Kompilátor generuje tělo `get` a přistupující objekty a `set` také soukromé pole pro uložení názvu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-255">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="7f17f-256">Je podobný následujícímu kódu, který jste mohli zadat ručně:</span><span class="sxs-lookup"><span data-stu-id="7f17f-256">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name
{
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="7f17f-257">Pojďme ještě před přidáním nových funkcí udělat nějakou další změnu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-257">Let's make one more change before adding new features.</span></span> <span data-ttu-id="7f17f-258">`ProcessRepositories` Metoda může provádět asynchronní práci a vracet kolekci úložišť.</span><span class="sxs-lookup"><span data-stu-id="7f17f-258">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="7f17f-259">Pojďme `List<Repository>` z této metody vracet a přesunete kód, který zapisuje informace `Main` do metody.</span><span class="sxs-lookup"><span data-stu-id="7f17f-259">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="7f17f-260">Změnou signatury `ProcessRepositories` vrátíte úkol, jehož výsledkem je `Repository` seznam objektů:</span><span class="sxs-lookup"><span data-stu-id="7f17f-260">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="7f17f-261">Pak jednoduše vraťte úložiště po zpracování odpovědi JSON:</span><span class="sxs-lookup"><span data-stu-id="7f17f-261">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="7f17f-262">Kompilátor vygeneruje `Task<T>` objekt pro návrat, protože jste označili tuto metodu jako `async`.</span><span class="sxs-lookup"><span data-stu-id="7f17f-262">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="7f17f-263">Pak Pojďme `Main` metodu upravit tak, aby zachytit tyto výsledky a zapsala všechny názvy úložišť do konzoly.</span><span class="sxs-lookup"><span data-stu-id="7f17f-263">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="7f17f-264">Vaše `Main` metoda teď vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="7f17f-264">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="7f17f-265">Přístup k `Result` vlastnosti bloků úkolu, dokud se úloha nedokončí.</span><span class="sxs-lookup"><span data-stu-id="7f17f-265">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="7f17f-266">Normálně byste měli preferovat `await` dokončení úlohy, jako `ProcessRepositories` v metodě, ale `Main` které nejsou v metodě povoleny.</span><span class="sxs-lookup"><span data-stu-id="7f17f-266">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="7f17f-267">Přečtěte si další informace</span><span class="sxs-lookup"><span data-stu-id="7f17f-267">Reading More Information</span></span>

<span data-ttu-id="7f17f-268">Pojďme to dokončit zpracováním několika dalších vlastností v paketu JSON, které se odesílají z rozhraní API GitHubu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-268">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="7f17f-269">Nebudete chtít všechno přidat, ale přidáním několika vlastností se ukáže několik dalších funkcí tohoto C# jazyka.</span><span class="sxs-lookup"><span data-stu-id="7f17f-269">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="7f17f-270">Pojďme začít přidáním několika jednoduchých typů do `Repository` definice třídy.</span><span class="sxs-lookup"><span data-stu-id="7f17f-270">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="7f17f-271">Přidejte tyto vlastnosti do této třídy:</span><span class="sxs-lookup"><span data-stu-id="7f17f-271">Add these properties to that class:</span></span>

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

<span data-ttu-id="7f17f-272">Tyto vlastnosti mají předdefinované převody z typu řetězce (což je to, co pakety JSON obsahují) k cílovému typu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-272">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="7f17f-273"><xref:System.Uri> Typ může být pro vás nový.</span><span class="sxs-lookup"><span data-stu-id="7f17f-273">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="7f17f-274">Představuje identifikátor URI, nebo v tomto případě adresu URL.</span><span class="sxs-lookup"><span data-stu-id="7f17f-274">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="7f17f-275">V případě `Uri` typů a `int` platí, že pokud paket JSON obsahuje data, která nejsou převedena na cílový typ, akce serializace vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="7f17f-275">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="7f17f-276">Jakmile je přidáte, aktualizujte `Main` metodu tak, aby zobrazovala tyto prvky:</span><span class="sxs-lookup"><span data-stu-id="7f17f-276">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="7f17f-277">Jako poslední krok Pojďme přidat informace pro poslední operaci Push.</span><span class="sxs-lookup"><span data-stu-id="7f17f-277">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="7f17f-278">Tyto informace jsou v odpovědi JSON formátované tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="7f17f-278">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="7f17f-279">Tento formát nedodržuje žádné standardní formáty .NET <xref:System.DateTime> .</span><span class="sxs-lookup"><span data-stu-id="7f17f-279">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="7f17f-280">Z tohoto důvodu budete muset napsat vlastní metodu převodu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-280">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="7f17f-281">Pravděpodobně nebudete chtít, aby Nezpracovaný řetězec byl vystaven uživatelům `Repository` třídy.</span><span class="sxs-lookup"><span data-stu-id="7f17f-281">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="7f17f-282">Atributy mohou také určovat.</span><span class="sxs-lookup"><span data-stu-id="7f17f-282">Attributes can help control that as well.</span></span> <span data-ttu-id="7f17f-283">Nejprve definujte `private` vlastnost, která bude obsahovat řetězcové vyjádření data a času ve vaší `Repository` třídě:</span><span class="sxs-lookup"><span data-stu-id="7f17f-283">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="7f17f-284"><xref:System.Runtime.Serialization.DataMemberAttribute> Atribut informuje serializátor, který by měl být zpracován, i když se nejedná o veřejný člen.</span><span class="sxs-lookup"><span data-stu-id="7f17f-284">The <xref:System.Runtime.Serialization.DataMemberAttribute> attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="7f17f-285">Dále musíte napsat veřejnou vlastnost jen pro čtení, která převede řetězec na platný <xref:System.DateTime> objekt a vrátí to: <xref:System.DateTime></span><span class="sxs-lookup"><span data-stu-id="7f17f-285">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

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

<span data-ttu-id="7f17f-286">Pojďme přejít na výše uvedené nové konstrukce.</span><span class="sxs-lookup"><span data-stu-id="7f17f-286">Let's go over the new constructs above.</span></span> <span data-ttu-id="7f17f-287">`IgnoreDataMember` Atribut instruuje serializátor, že tento typ by neměl být čten nebo napsán z libovolného objektu JSON.</span><span class="sxs-lookup"><span data-stu-id="7f17f-287">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="7f17f-288">Tato vlastnost obsahuje pouze `get` přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="7f17f-288">This property contains only a `get` accessor.</span></span> <span data-ttu-id="7f17f-289">K dispozici `set` není žádný přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="7f17f-289">There is no `set` accessor.</span></span> <span data-ttu-id="7f17f-290">To je způsob, jak definovat vlastnost *jen pro čtení* v C#.</span><span class="sxs-lookup"><span data-stu-id="7f17f-290">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="7f17f-291">(Ano, můžete vytvořit vlastnosti *pouze pro zápis* v C#, ale jejich hodnota je omezená.) Metoda analyzuje řetězec a <xref:System.DateTime> vytvoří objekt pomocí poskytnutého formátu data a `DateTime` přidá další `CultureInfo` metadata do objektu pomocí objektu. <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)></span><span class="sxs-lookup"><span data-stu-id="7f17f-291">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="7f17f-292">Pokud operace analýzy není úspěšná, přistupující objekt vlastnosti vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="7f17f-292">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="7f17f-293">Chcete- <xref:System.Globalization.CultureInfo.InvariantCulture>li použít, budete muset <xref:System.Globalization> přidat obor názvů do `using` příkazů v `repo.cs`:</span><span class="sxs-lookup"><span data-stu-id="7f17f-293">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="7f17f-294">Nakonec přidejte do konzoly další příkaz Output a teď budete připraveni tuto aplikaci sestavit a spustit:</span><span class="sxs-lookup"><span data-stu-id="7f17f-294">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="7f17f-295">Verze by měla nyní odpovídat [ukázce dokončeno](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span><span class="sxs-lookup"><span data-stu-id="7f17f-295">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="7f17f-296">Závěr</span><span class="sxs-lookup"><span data-stu-id="7f17f-296">Conclusion</span></span>

<span data-ttu-id="7f17f-297">V tomto kurzu jste si ukázali, jak vytvářet webové požadavky, analyzovat výsledek a zobrazovat vlastnosti těchto výsledků.</span><span class="sxs-lookup"><span data-stu-id="7f17f-297">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="7f17f-298">Přidali jste také nové balíčky jako závislosti ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="7f17f-298">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="7f17f-299">Seznámili jste se s některými funkcemi C# jazyka, který podporuje objektově orientované techniky.</span><span class="sxs-lookup"><span data-stu-id="7f17f-299">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
