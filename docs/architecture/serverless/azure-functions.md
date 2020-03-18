---
title: Funkce Azure – aplikace bez serveru
description: Funkce Azure poskytují funkce bez serveru ve více jazycích (C#, JavaScript, Java) a platformách, které poskytují okamžitý škálovací kód řízený událostmi.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401611"
---
# <a name="azure-functions"></a><span data-ttu-id="41131-103">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="41131-103">Azure Functions</span></span>

<span data-ttu-id="41131-104">Funkce Azure poskytují výpočetní prostředí bez serveru.</span><span class="sxs-lookup"><span data-stu-id="41131-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="41131-105">Funkce je vyvolána *aktivační událostí* (například přístup ke koncovému bodu HTTP nebo časovači) a spustí blok kódu nebo obchodní logiky.</span><span class="sxs-lookup"><span data-stu-id="41131-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="41131-106">Funkce také podporují specializované *vazby,* které se připojují k prostředkům, jako je úložiště a fronty.</span><span class="sxs-lookup"><span data-stu-id="41131-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Logo funkcí Azure](./media/azure-functions-logo.png)

<span data-ttu-id="41131-108">Existují dvě verze architektury Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="41131-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="41131-109">Starší verze podporuje úplnou architekturu .NET Framework a nový runtime podporuje aplikace .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="41131-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="41131-110">Další jazyky kromě Jazyka C#, například JavaScript, F# a Java, jsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="41131-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="41131-111">Funkce vytvořené na portálu poskytují bohatou syntaxi skriptování.</span><span class="sxs-lookup"><span data-stu-id="41131-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="41131-112">Funkce vytvořené jako samostatné projekty lze nasadit s plnou podporou platformy a možnostmi.</span><span class="sxs-lookup"><span data-stu-id="41131-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="41131-113">Další informace naleznete v [dokumentaci k funkcím Azure](https://docs.microsoft.com/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="41131-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="41131-114">Funkce v1 vs. v2</span><span class="sxs-lookup"><span data-stu-id="41131-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="41131-115">Existují dvě verze runtime Funkce Azure: 1.x a 2.x.</span><span class="sxs-lookup"><span data-stu-id="41131-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="41131-116">Verze 1.x je obecně dostupná (GA).</span><span class="sxs-lookup"><span data-stu-id="41131-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="41131-117">Podporuje vývoj rozhraní .NET z portálu nebo počítačů se systémem Windows a používá rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41131-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="41131-118">1.x podporuje C#, JavaScript a F#, s experimentální podporou Pythonu, PHP, TypeScriptu, Batch, Bash a PowerShellu.</span><span class="sxs-lookup"><span data-stu-id="41131-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="41131-119">[Verze 2.x je také obecně k dispozici nyní](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span><span class="sxs-lookup"><span data-stu-id="41131-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="41131-120">Využívá rozhraní .NET Core a podporuje vývoj napříč platformami na počítačích se systémem Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="41131-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="41131-121">2.x přidává prvotřídní podporu pro Javu, ale zatím přímo nepodporuje žádný z experimentálních jazyků.</span><span class="sxs-lookup"><span data-stu-id="41131-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="41131-122">Verze 2.x používá nový model rozšiřitelnosti vazby, který umožňuje rozšíření třetích stran na platformu, nezávislé správy verzí vazeb a efektivnější spuštění prostředí.</span><span class="sxs-lookup"><span data-stu-id="41131-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="41131-123">**Je známý problém v 1.x s [podporou přesměrování vazby](https://github.com/Azure/azure-functions-host/issues/992).**</span><span class="sxs-lookup"><span data-stu-id="41131-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="41131-124">Problém je specifický pro vývoj rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="41131-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="41131-125">Projekty se závislostmi na knihovnách, které jsou jinou verzí než knihovny zahrnuté v běhu, jsou ovlivněny.</span><span class="sxs-lookup"><span data-stu-id="41131-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="41131-126">Tým funkcí se zavázal k dosažení konkrétního pokroku v řešení problému.</span><span class="sxs-lookup"><span data-stu-id="41131-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="41131-127">Tým bude řešit vazby přesměrování v 2.x před přejde do obecné dostupnosti.</span><span class="sxs-lookup"><span data-stu-id="41131-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="41131-128">Oficiální prohlášení týmu s navrhovanými opravami a řešeními je k dispozici zde: [Řešení sestavení ve funkcích Azure](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span><span class="sxs-lookup"><span data-stu-id="41131-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="41131-129">Další informace naleznete [v tématech Porovnání 1.x a 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span><span class="sxs-lookup"><span data-stu-id="41131-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="41131-130">Podpora programovacích jazyků</span><span class="sxs-lookup"><span data-stu-id="41131-130">Programming language support</span></span>

<span data-ttu-id="41131-131">Následující jazyky jsou podporovány buď v obecné dostupnosti (GA), náhledu nebo experimentální.</span><span class="sxs-lookup"><span data-stu-id="41131-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="41131-132">Jazyk</span><span class="sxs-lookup"><span data-stu-id="41131-132">Language</span></span>      |<span data-ttu-id="41131-133">1.x</span><span class="sxs-lookup"><span data-stu-id="41131-133">1.x</span></span>         |<span data-ttu-id="41131-134">2.x</span><span class="sxs-lookup"><span data-stu-id="41131-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="41131-135">**C #**</span><span class="sxs-lookup"><span data-stu-id="41131-135">**C#**</span></span>        |<span data-ttu-id="41131-136">GA</span><span class="sxs-lookup"><span data-stu-id="41131-136">GA</span></span>          |<span data-ttu-id="41131-137">Preview</span><span class="sxs-lookup"><span data-stu-id="41131-137">Preview</span></span>  |
|<span data-ttu-id="41131-138">**Javascript**</span><span class="sxs-lookup"><span data-stu-id="41131-138">**JavaScript**</span></span>|<span data-ttu-id="41131-139">GA</span><span class="sxs-lookup"><span data-stu-id="41131-139">GA</span></span>          |<span data-ttu-id="41131-140">Preview</span><span class="sxs-lookup"><span data-stu-id="41131-140">Preview</span></span>  |
|<span data-ttu-id="41131-141">**F #**</span><span class="sxs-lookup"><span data-stu-id="41131-141">**F#**</span></span>        |<span data-ttu-id="41131-142">GA</span><span class="sxs-lookup"><span data-stu-id="41131-142">GA</span></span>          |         |
|<span data-ttu-id="41131-143">**Java**</span><span class="sxs-lookup"><span data-stu-id="41131-143">**Java**</span></span>      |            |<span data-ttu-id="41131-144">Preview</span><span class="sxs-lookup"><span data-stu-id="41131-144">Preview</span></span>  |
|<span data-ttu-id="41131-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="41131-145">**Python**</span></span>    |<span data-ttu-id="41131-146">Experimentální</span><span class="sxs-lookup"><span data-stu-id="41131-146">Experimental</span></span>|         |
|<span data-ttu-id="41131-147">**PHP**</span><span class="sxs-lookup"><span data-stu-id="41131-147">**PHP**</span></span>       |<span data-ttu-id="41131-148">Experimentální</span><span class="sxs-lookup"><span data-stu-id="41131-148">Experimental</span></span>|         |
|<span data-ttu-id="41131-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="41131-149">**TypeScript**</span></span>|<span data-ttu-id="41131-150">Experimentální</span><span class="sxs-lookup"><span data-stu-id="41131-150">Experimental</span></span>|         |
|<span data-ttu-id="41131-151">**Batch**</span><span class="sxs-lookup"><span data-stu-id="41131-151">**Batch**</span></span>     |<span data-ttu-id="41131-152">Experimentální</span><span class="sxs-lookup"><span data-stu-id="41131-152">Experimental</span></span>|         |
|<span data-ttu-id="41131-153">**Bash**</span><span class="sxs-lookup"><span data-stu-id="41131-153">**Bash**</span></span>      |<span data-ttu-id="41131-154">Experimentální</span><span class="sxs-lookup"><span data-stu-id="41131-154">Experimental</span></span>|         |
|<span data-ttu-id="41131-155">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="41131-155">**PowerShell**</span></span>|<span data-ttu-id="41131-156">Experimentální</span><span class="sxs-lookup"><span data-stu-id="41131-156">Experimental</span></span>|         |

<span data-ttu-id="41131-157">Další informace najdete v tématu [Podporované jazyky](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="41131-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="41131-158">Plány služeb aplikace</span><span class="sxs-lookup"><span data-stu-id="41131-158">App service plans</span></span>

<span data-ttu-id="41131-159">Funkce jsou zálohovány *plánem služby App Service*.</span><span class="sxs-lookup"><span data-stu-id="41131-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="41131-160">Plán definuje prostředky používané aplikací funkce.</span><span class="sxs-lookup"><span data-stu-id="41131-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="41131-161">Můžete přiřadit plány k oblasti, určit velikost a počet virtuálních počítačů, které budou použity, a vyberte cenovou úroveň.</span><span class="sxs-lookup"><span data-stu-id="41131-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="41131-162">Pro skutečný přístup bez serveru aplikace funkce můžete použít plán **spotřeby.**</span><span class="sxs-lookup"><span data-stu-id="41131-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="41131-163">Plán spotřeby automaticky změní velikost back-endu na základě zatížení.</span><span class="sxs-lookup"><span data-stu-id="41131-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="41131-164">Další informace naleznete v tématu [Plány služeb aplikace](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="41131-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="41131-165">Vytvoření první funkce</span><span class="sxs-lookup"><span data-stu-id="41131-165">Create your first function</span></span>

<span data-ttu-id="41131-166">Existují tři běžné způsoby, jak můžete vytvářet aplikace funkcí.</span><span class="sxs-lookup"><span data-stu-id="41131-166">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="41131-167">Skript funguje na portálu.</span><span class="sxs-lookup"><span data-stu-id="41131-167">Script functions in the portal.</span></span>
- <span data-ttu-id="41131-168">Vytvořte potřebné prostředky pomocí azure cli.</span><span class="sxs-lookup"><span data-stu-id="41131-168">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="41131-169">Vytvářejte funkce místně pomocí oblíbeného prostředí IDE a publikujte je do Azure.</span><span class="sxs-lookup"><span data-stu-id="41131-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="41131-170">Další informace o vytvoření skriptované funkce na portálu najdete v [tématu Vytvoření první funkce na webu Azure Portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span><span class="sxs-lookup"><span data-stu-id="41131-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="41131-171">Pokud chcete vytvořit z azure cli, najdete [v tématu vytvoření první funkce pomocí příkazového příkazu k onomu azure](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="41131-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="41131-172">Pokud chcete vytvořit funkci z Visual Studia, [přečtěte si](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)informace o vytvoření první funkce pomocí sady Visual Studio .</span><span class="sxs-lookup"><span data-stu-id="41131-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="41131-173">Principy aktivačních událostí a vazeb</span><span class="sxs-lookup"><span data-stu-id="41131-173">Understand triggers and bindings</span></span>

<span data-ttu-id="41131-174">Funkce jsou vyvolány *aktivační událostí* a mohou mít přesně jednu.</span><span class="sxs-lookup"><span data-stu-id="41131-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="41131-175">Kromě vyvolání funkce, některé aktivační události slouží také jako vazby.</span><span class="sxs-lookup"><span data-stu-id="41131-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="41131-176">Můžete také definovat více vazeb kromě aktivační události.</span><span class="sxs-lookup"><span data-stu-id="41131-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="41131-177">*Vazby* poskytují deklarativní způsob připojení dat k kódu.</span><span class="sxs-lookup"><span data-stu-id="41131-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="41131-178">Mohou být předány (vstup) nebo přijímat data (výstup).</span><span class="sxs-lookup"><span data-stu-id="41131-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="41131-179">Spouštěaaa a vazby usnadňují práci s funkcemi.</span><span class="sxs-lookup"><span data-stu-id="41131-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="41131-180">Vazby odeberou režii ručního vytváření připojení databáze nebo systému souborů.</span><span class="sxs-lookup"><span data-stu-id="41131-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="41131-181">Všechny informace potřebné pro vazby je obsažena ve speciálním souboru *functions.json* pro skripty nebo deklarované s atributy v kódu.</span><span class="sxs-lookup"><span data-stu-id="41131-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="41131-182">Některé běžné aktivační události zahrnují:</span><span class="sxs-lookup"><span data-stu-id="41131-182">Some common triggers include:</span></span>

- <span data-ttu-id="41131-183">Úložiště objektů blob: vyvolá funkci při nahrání nebo změně souboru nebo složky v úložišti.</span><span class="sxs-lookup"><span data-stu-id="41131-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="41131-184">HTTP: vyvolat funkci jako rozhraní REST API.</span><span class="sxs-lookup"><span data-stu-id="41131-184">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="41131-185">Fronta: vyvolá funkci, pokud položky existují ve frontě.</span><span class="sxs-lookup"><span data-stu-id="41131-185">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="41131-186">Časovač: vyvolat svou funkci na pravidelné kadence.</span><span class="sxs-lookup"><span data-stu-id="41131-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="41131-187">Příklady vazeb:</span><span class="sxs-lookup"><span data-stu-id="41131-187">Examples of bindings include:</span></span>

- <span data-ttu-id="41131-188">CosmosDB: snadno se připojit k databázi načíst nebo uložit soubory.</span><span class="sxs-lookup"><span data-stu-id="41131-188">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="41131-189">Table Storage: práce s úložištěm klíč/hodnota z vaší aplikace funkce.</span><span class="sxs-lookup"><span data-stu-id="41131-189">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="41131-190">Skladování front: snadno načíst položky z fronty nebo umístit nové položky do fronty.</span><span class="sxs-lookup"><span data-stu-id="41131-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="41131-191">Následující příklad *souboru functions.json* definuje aktivační událost a vazbu:</span><span class="sxs-lookup"><span data-stu-id="41131-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

<span data-ttu-id="41131-192">V tomto příkladu je funkce spuštěna změnou `images` úložiště objektů blob v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="41131-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="41131-193">Informace pro soubor je předán, takže aktivační událost také funguje jako vazba.</span><span class="sxs-lookup"><span data-stu-id="41131-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="41131-194">Existuje jiná vazba pro zařazení informací `images`do fronty s názvem .</span><span class="sxs-lookup"><span data-stu-id="41131-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="41131-195">Zde je skript C# pro funkci:</span><span class="sxs-lookup"><span data-stu-id="41131-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="41131-196">Příkladem je jednoduchá funkce, která přebírá název souboru, který byl upraven nebo odeslán do úložiště objektů blob, a umístí jej do fronty pro pozdější zpracování.</span><span class="sxs-lookup"><span data-stu-id="41131-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="41131-197">Úplný seznam aktivačních událostí a vazeb najdete v [tématu Azure Functions aktivační události a koncepty vazby](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="41131-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="41131-198">Proxy</span><span class="sxs-lookup"><span data-stu-id="41131-198">Proxies</span></span>

<span data-ttu-id="41131-199">Servery proxy poskytují funkce přesměrování pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="41131-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="41131-200">Proxy servery vystavit koncový bod a mapování tohoto koncového bodu na jiný prostředek.</span><span class="sxs-lookup"><span data-stu-id="41131-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="41131-201">S proxy servery můžete:</span><span class="sxs-lookup"><span data-stu-id="41131-201">With proxies, you can:</span></span>

- <span data-ttu-id="41131-202">Přesměrovat příchozí požadavek do jiného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="41131-202">Reroute an incoming request to another endpoint.</span></span>
- <span data-ttu-id="41131-203">Upravte příchozí požadavek před jeho předáním.</span><span class="sxs-lookup"><span data-stu-id="41131-203">Modify the incoming request before it's passed along.</span></span>
- <span data-ttu-id="41131-204">Upravte nebo poskytněte odpověď.</span><span class="sxs-lookup"><span data-stu-id="41131-204">Modify or provide a response.</span></span>

<span data-ttu-id="41131-205">Proxy servery se používají pro scénáře, jako jsou:</span><span class="sxs-lookup"><span data-stu-id="41131-205">Proxies are used for scenarios such as:</span></span>

- <span data-ttu-id="41131-206">Zjednodušení, zkrácení nebo změna adresy URL.</span><span class="sxs-lookup"><span data-stu-id="41131-206">Simplifying, shortening, or changing the URL.</span></span>
- <span data-ttu-id="41131-207">Poskytuje konzistentní předponu rozhraní API pro více back-endových služeb.</span><span class="sxs-lookup"><span data-stu-id="41131-207">Providing a consistent API prefix to multiple back-end services.</span></span>
- <span data-ttu-id="41131-208">Zesměšňování odpověď na koncový bod vyvíjené.</span><span class="sxs-lookup"><span data-stu-id="41131-208">Mocking a response to an endpoint being developed.</span></span>
- <span data-ttu-id="41131-209">Poskytuje statickou odpověď na známý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="41131-209">Providing a static response to a well-known endpoint.</span></span>
- <span data-ttu-id="41131-210">Udržování koncového bodu rozhraní API konzistentní při přesunutí nebo migraci back-endu.</span><span class="sxs-lookup"><span data-stu-id="41131-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="41131-211">Proxy servery jsou uloženy jako definice JSON.</span><span class="sxs-lookup"><span data-stu-id="41131-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="41131-212">Zde naleznete příklad:</span><span class="sxs-lookup"><span data-stu-id="41131-212">Here is an example:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "Domain Redirect": {
      "matchCondition": {
        "route": "/{shortUrl}"
      },
      "backendUri": "http://%WEBSITE_HOSTNAME%/api/UrlRedirect/{shortUrl}"
    },
    "Root": {
      "matchCondition": {
        "route": "/"
      },
      "responseOverrides": {
        "response.statusCode": "301",
        "response.statusReason": "Moved Permanently",
        "response.headers.location": "https://docs.microsoft.com/"
      }
    }
  }
}
```

<span data-ttu-id="41131-213">Proxy `Domain Redirect` server provede zkrácenou trasu a mapuje ji na prostředek delší funkce.</span><span class="sxs-lookup"><span data-stu-id="41131-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="41131-214">Transformace vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="41131-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="41131-215">Proxy `Root` server přenese vše`https://--shorturl--/`odeslané na kořenovou adresu URL ( ) a přesměruje ji na dokumentační web.</span><span class="sxs-lookup"><span data-stu-id="41131-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="41131-216">Příklad použití proxy serverů se zobrazí ve videu [Azure: Přeneste svou aplikaci do cloudu s funkcemi Azure bez serveru](https://channel9.msdn.com/events/Connect/2017/E102).</span><span class="sxs-lookup"><span data-stu-id="41131-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="41131-217">V reálném čase se do Cloudu Azure cloudu migruje ASP.NET základní aplikace spuštěná na místním SQL Serveru.</span><span class="sxs-lookup"><span data-stu-id="41131-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="41131-218">Proxy servery se používají k refaktoringu tradiční hostoje webAPI projekt používat funkce.</span><span class="sxs-lookup"><span data-stu-id="41131-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="41131-219">Další informace o proxy serverech najdete v [tématu Práce s azure functions proxy](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span><span class="sxs-lookup"><span data-stu-id="41131-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="41131-220">[Předchozí](azure-serverless-platform.md)
>[další](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="41131-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
