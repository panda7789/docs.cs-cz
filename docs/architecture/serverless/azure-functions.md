---
title: Aplikace bez serveru Azure Functions
description: Azure Functions poskytuje možnosti bez serveru napříč různými jazykyC#(, JavaScript, Java) a platformami k poskytování kódu okamžitého škálování založeného na událostech.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5e8187b3752a0f0d0bcf8e15f2ce440dc5a64e45
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522877"
---
# <a name="azure-functions"></a><span data-ttu-id="9a847-103">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="9a847-103">Azure Functions</span></span>

<span data-ttu-id="9a847-104">Azure Functions poskytuje výpočetní prostředí bez serveru.</span><span class="sxs-lookup"><span data-stu-id="9a847-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="9a847-105">Funkce je vyvolána *triggerem* (například přístup ke koncovému bodu http nebo časovači) a spustí blok kódu nebo obchodní logiky.</span><span class="sxs-lookup"><span data-stu-id="9a847-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="9a847-106">Funkce také podporují specializované *vazby* , které se připojují k prostředkům, jako jsou úložiště a fronty.</span><span class="sxs-lookup"><span data-stu-id="9a847-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Logo Azure Functions](./media/azure-functions-logo.png)

<span data-ttu-id="9a847-108">Existují dvě verze rozhraní Azure Functions Framework.</span><span class="sxs-lookup"><span data-stu-id="9a847-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="9a847-109">Starší verze podporuje úplné .NET Framework a nový modul runtime podporuje aplikace .NET Core pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="9a847-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="9a847-110">Podporují se další C# jazyky kromě jazyků JavaScript F#, a Java.</span><span class="sxs-lookup"><span data-stu-id="9a847-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="9a847-111">Funkce vytvořené na portálu poskytují bohatou syntaxi skriptování.</span><span class="sxs-lookup"><span data-stu-id="9a847-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="9a847-112">Funkce vytvořené jako samostatné projekty lze nasadit s využitím plné podpory platforem a možností.</span><span class="sxs-lookup"><span data-stu-id="9a847-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="9a847-113">Další informace najdete v [dokumentaci Azure Functions](https://docs.microsoft.com/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="9a847-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="9a847-114">Funkce v1 vs. v2</span><span class="sxs-lookup"><span data-stu-id="9a847-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="9a847-115">Existují dvě verze modulu runtime Azure Functions: 1. x a 2. x.</span><span class="sxs-lookup"><span data-stu-id="9a847-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="9a847-116">Verze 1. x je všeobecně dostupná (GA).</span><span class="sxs-lookup"><span data-stu-id="9a847-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="9a847-117">Podporuje vývoj pro .NET z portálu nebo počítačů s Windows a používá .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9a847-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="9a847-118">1. x podporuje C#, JavaScript a F#, s experimentální podporou pro Python, php, TypeScript, Batch, bash a PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a847-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="9a847-119">[Verze 2. x je také všeobecně dostupná](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span><span class="sxs-lookup"><span data-stu-id="9a847-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="9a847-120">Využívá .NET Core a podporuje vývoj pro různé platformy na počítačích s Windows, macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="9a847-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="9a847-121">2. x přidává špičkovou podporu pro Java, ale ještě nepřímo nepodporuje žádný z experimentálních jazyků.</span><span class="sxs-lookup"><span data-stu-id="9a847-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="9a847-122">Verze 2. x používá nový model rozšiřitelnosti vazby, který umožňuje rozšíření jiných výrobců na platformu, nezávislé vytváření verzí vazeb a efektivnější prostředí pro provádění.</span><span class="sxs-lookup"><span data-stu-id="9a847-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="9a847-123">**Došlo k známému problému v 1. x s [podporou přesměrování vazby](https://github.com/Azure/azure-functions-host/issues/992).**</span><span class="sxs-lookup"><span data-stu-id="9a847-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="9a847-124">Tento problém je specifický pro vývoj pro .NET.</span><span class="sxs-lookup"><span data-stu-id="9a847-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="9a847-125">Budou ovlivněny projekty se závislostmi na knihovnách, které jsou odlišnou verzí z knihoven obsažených v modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="9a847-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="9a847-126">Tým Functions se zavázal, že má na problému konkrétní pokrok.</span><span class="sxs-lookup"><span data-stu-id="9a847-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="9a847-127">Tým bude adresovat přesměrování vazby v 2. x před tím, než se dostane do všeobecné dostupnosti.</span><span class="sxs-lookup"><span data-stu-id="9a847-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="9a847-128">Oficiální prohlášení týmu s navrhovanými opravami a alternativní řešení jsou k dispozici zde: [rozlišení sestavení v Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span><span class="sxs-lookup"><span data-stu-id="9a847-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="9a847-129">Další informace najdete v tématu [porovnání 1. x a 2. x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span><span class="sxs-lookup"><span data-stu-id="9a847-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="9a847-130">Podpora programovacích jazyků</span><span class="sxs-lookup"><span data-stu-id="9a847-130">Programming language support</span></span>

<span data-ttu-id="9a847-131">Následující jazyky jsou podporovány buď v obecné dostupnosti (GA), ve verzi Preview, nebo experimentální.</span><span class="sxs-lookup"><span data-stu-id="9a847-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="9a847-132">Jazyk</span><span class="sxs-lookup"><span data-stu-id="9a847-132">Language</span></span>      |<span data-ttu-id="9a847-133">verze</span><span class="sxs-lookup"><span data-stu-id="9a847-133">1.x</span></span>         |<span data-ttu-id="9a847-134">2.x</span><span class="sxs-lookup"><span data-stu-id="9a847-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="9a847-135">**C#**</span><span class="sxs-lookup"><span data-stu-id="9a847-135">**C#**</span></span>        |<span data-ttu-id="9a847-136">GA</span><span class="sxs-lookup"><span data-stu-id="9a847-136">GA</span></span>          |<span data-ttu-id="9a847-137">Preview</span><span class="sxs-lookup"><span data-stu-id="9a847-137">Preview</span></span>  |
|<span data-ttu-id="9a847-138">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="9a847-138">**JavaScript**</span></span>|<span data-ttu-id="9a847-139">GA</span><span class="sxs-lookup"><span data-stu-id="9a847-139">GA</span></span>          |<span data-ttu-id="9a847-140">Preview</span><span class="sxs-lookup"><span data-stu-id="9a847-140">Preview</span></span>  |
|<span data-ttu-id="9a847-141">**F#**</span><span class="sxs-lookup"><span data-stu-id="9a847-141">**F#**</span></span>        |<span data-ttu-id="9a847-142">GA</span><span class="sxs-lookup"><span data-stu-id="9a847-142">GA</span></span>          |         |
|<span data-ttu-id="9a847-143">**Java**</span><span class="sxs-lookup"><span data-stu-id="9a847-143">**Java**</span></span>      |            |<span data-ttu-id="9a847-144">Preview</span><span class="sxs-lookup"><span data-stu-id="9a847-144">Preview</span></span>  |
|<span data-ttu-id="9a847-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="9a847-145">**Python**</span></span>    |<span data-ttu-id="9a847-146">Experimentální</span><span class="sxs-lookup"><span data-stu-id="9a847-146">Experimental</span></span>|         |
|<span data-ttu-id="9a847-147">**PHP**</span><span class="sxs-lookup"><span data-stu-id="9a847-147">**PHP**</span></span>       |<span data-ttu-id="9a847-148">Experimentální</span><span class="sxs-lookup"><span data-stu-id="9a847-148">Experimental</span></span>|         |
|<span data-ttu-id="9a847-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="9a847-149">**TypeScript**</span></span>|<span data-ttu-id="9a847-150">Experimentální</span><span class="sxs-lookup"><span data-stu-id="9a847-150">Experimental</span></span>|         |
|<span data-ttu-id="9a847-151">**Partie**</span><span class="sxs-lookup"><span data-stu-id="9a847-151">**Batch**</span></span>     |<span data-ttu-id="9a847-152">Experimentální</span><span class="sxs-lookup"><span data-stu-id="9a847-152">Experimental</span></span>|         |
|<span data-ttu-id="9a847-153">**Bash**</span><span class="sxs-lookup"><span data-stu-id="9a847-153">**Bash**</span></span>      |<span data-ttu-id="9a847-154">Experimentální</span><span class="sxs-lookup"><span data-stu-id="9a847-154">Experimental</span></span>|         |
|<span data-ttu-id="9a847-155">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="9a847-155">**PowerShell**</span></span>|<span data-ttu-id="9a847-156">Experimentální</span><span class="sxs-lookup"><span data-stu-id="9a847-156">Experimental</span></span>|         |

<span data-ttu-id="9a847-157">Další informace najdete v tématu [podporované jazyky](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="9a847-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="9a847-158">Plány služby App Service</span><span class="sxs-lookup"><span data-stu-id="9a847-158">App service plans</span></span>

<span data-ttu-id="9a847-159">Služba Functions se zálohuje podle *plánu služby App Service*.</span><span class="sxs-lookup"><span data-stu-id="9a847-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="9a847-160">Plán definuje prostředky používané aplikací Functions.</span><span class="sxs-lookup"><span data-stu-id="9a847-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="9a847-161">Můžete přiřadit plány k oblasti, určit velikost a počet virtuálních počítačů, které se budou používat, a vybrat cenovou úroveň.</span><span class="sxs-lookup"><span data-stu-id="9a847-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="9a847-162">Pro skutečný přístup bez serveru můžou aplikace Function App používat plán **spotřeby** .</span><span class="sxs-lookup"><span data-stu-id="9a847-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="9a847-163">Plán spotřeby bude automaticky škálovat back-end na základě zatížení.</span><span class="sxs-lookup"><span data-stu-id="9a847-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="9a847-164">Další informace najdete v tématu [plány služby App Service](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="9a847-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="9a847-165">Vytvoření první funkce</span><span class="sxs-lookup"><span data-stu-id="9a847-165">Create your first function</span></span>

<span data-ttu-id="9a847-166">Existují tři běžné způsoby, jak můžete vytvářet aplikace Function App.</span><span class="sxs-lookup"><span data-stu-id="9a847-166">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="9a847-167">Funkce skriptu na portálu.</span><span class="sxs-lookup"><span data-stu-id="9a847-167">Script functions in the portal.</span></span>
- <span data-ttu-id="9a847-168">Vytvořte potřebné prostředky pomocí rozhraní příkazového řádku Azure (CLI).</span><span class="sxs-lookup"><span data-stu-id="9a847-168">Create the necessary resources using the Azure Command Line Interface (CLI).</span></span>
- <span data-ttu-id="9a847-169">Vytvářejte funkce místně pomocí svého oblíbeného integrovaného vývojového prostředí a publikujte je do Azure.</span><span class="sxs-lookup"><span data-stu-id="9a847-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="9a847-170">Další informace o vytvoření skriptované funkce na portálu najdete v tématu [Vytvoření první funkce v Azure Portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span><span class="sxs-lookup"><span data-stu-id="9a847-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="9a847-171">Informace o tom, jak vytvořit z Azure CLI, najdete v tématu [Vytvoření první funkce pomocí Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="9a847-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="9a847-172">Chcete-li vytvořit funkci ze sady Visual Studio, přečtěte si téma [Vytvoření první funkce pomocí sady Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="9a847-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="9a847-173">Principy aktivačních událostí a vazeb</span><span class="sxs-lookup"><span data-stu-id="9a847-173">Understand triggers and bindings</span></span>

<span data-ttu-id="9a847-174">Funkce jsou vyvolány *triggerem* a mohou mít právě jednu.</span><span class="sxs-lookup"><span data-stu-id="9a847-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="9a847-175">Kromě vyvolání funkce určité triggery slouží také jako vazby.</span><span class="sxs-lookup"><span data-stu-id="9a847-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="9a847-176">Kromě triggeru můžete také definovat více vazeb.</span><span class="sxs-lookup"><span data-stu-id="9a847-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="9a847-177">*Vazby* poskytují deklarativní způsob, jak připojit data k vašemu kódu.</span><span class="sxs-lookup"><span data-stu-id="9a847-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="9a847-178">Můžou se předávat (zadávat) nebo přijímat data (výstup).</span><span class="sxs-lookup"><span data-stu-id="9a847-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="9a847-179">Aktivační události a vazby usnadňují práci s funkcemi.</span><span class="sxs-lookup"><span data-stu-id="9a847-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="9a847-180">Vazby odstraňují režii při ručním vytváření připojení databáze nebo systému souborů.</span><span class="sxs-lookup"><span data-stu-id="9a847-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="9a847-181">Všechny informace potřebné pro vazby jsou obsaženy ve speciálním souboru *Functions. JSON* pro skripty nebo deklarované pomocí atributů v kódu.</span><span class="sxs-lookup"><span data-stu-id="9a847-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="9a847-182">Mezi běžné triggery patří:</span><span class="sxs-lookup"><span data-stu-id="9a847-182">Some common triggers include:</span></span>

- <span data-ttu-id="9a847-183">Blob Storage: vyvolejte funkci, když se v úložišti nahraje nebo změní soubor nebo složka.</span><span class="sxs-lookup"><span data-stu-id="9a847-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="9a847-184">HTTP: vyvolání funkce jako REST API.</span><span class="sxs-lookup"><span data-stu-id="9a847-184">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="9a847-185">Queue: vyvolá funkci, když položky ve frontě existují.</span><span class="sxs-lookup"><span data-stu-id="9a847-185">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="9a847-186">Timer: vyvolejte funkci v normálním tempo.</span><span class="sxs-lookup"><span data-stu-id="9a847-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="9a847-187">Mezi příklady vazeb patří:</span><span class="sxs-lookup"><span data-stu-id="9a847-187">Examples of bindings include:</span></span>

- <span data-ttu-id="9a847-188">CosmosDB: snadno se připojte k databázi a načíst nebo uložit soubory.</span><span class="sxs-lookup"><span data-stu-id="9a847-188">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="9a847-189">Table Storage: Pracujte s úložištěm klíč/hodnota z aplikace Function App.</span><span class="sxs-lookup"><span data-stu-id="9a847-189">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="9a847-190">Queue Storage: snadno načíst položky z fronty nebo umístit nové položky do fronty.</span><span class="sxs-lookup"><span data-stu-id="9a847-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="9a847-191">Následující příklad souboru *Functions. JSON* definuje Trigger a vazbu:</span><span class="sxs-lookup"><span data-stu-id="9a847-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

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

<span data-ttu-id="9a847-192">V tomto příkladu je funkce aktivována změnou v úložišti objektů BLOB v kontejneru `images`.</span><span class="sxs-lookup"><span data-stu-id="9a847-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="9a847-193">Informace pro soubor jsou předány, takže Trigger funguje také jako vazba.</span><span class="sxs-lookup"><span data-stu-id="9a847-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="9a847-194">Pro vložení informací do fronty s názvem `images`existuje jiná vazba.</span><span class="sxs-lookup"><span data-stu-id="9a847-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="9a847-195">Tady je C# skript pro funkci:</span><span class="sxs-lookup"><span data-stu-id="9a847-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="9a847-196">Příkladem je jednoduchá funkce, která přebírá název souboru, který se změnil nebo nahrál do úložiště objektů blob, a umístí ho do fronty pro pozdější zpracování.</span><span class="sxs-lookup"><span data-stu-id="9a847-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="9a847-197">Úplný seznam triggerů a vazeb najdete v tématu [Azure Functions triggery a koncepty vazeb](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="9a847-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="9a847-198">Proxy</span><span class="sxs-lookup"><span data-stu-id="9a847-198">Proxies</span></span>

<span data-ttu-id="9a847-199">Proxy poskytují funkce přesměrování vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="9a847-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="9a847-200">Proxy zpřístupňují koncový bod a mapují tento koncový bod na jiný prostředek.</span><span class="sxs-lookup"><span data-stu-id="9a847-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="9a847-201">U proxy serverů můžete provádět následující akce:</span><span class="sxs-lookup"><span data-stu-id="9a847-201">With proxies, you can:</span></span>

- <span data-ttu-id="9a847-202">Přesměrovat příchozí požadavek do jiného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="9a847-202">Reroute an incoming request to another endpoint.</span></span>
- <span data-ttu-id="9a847-203">Upravte příchozí požadavek předtím, než se předáte společně.</span><span class="sxs-lookup"><span data-stu-id="9a847-203">Modify the incoming request before it's passed along.</span></span>
- <span data-ttu-id="9a847-204">Upravte nebo poskytněte odpověď.</span><span class="sxs-lookup"><span data-stu-id="9a847-204">Modify or provide a response.</span></span>

<span data-ttu-id="9a847-205">Proxy servery se používají pro scénáře, jako například:</span><span class="sxs-lookup"><span data-stu-id="9a847-205">Proxies are used for scenarios such as:</span></span>

- <span data-ttu-id="9a847-206">Zjednodušení, zkrácení nebo změna adresy URL.</span><span class="sxs-lookup"><span data-stu-id="9a847-206">Simplifying, shortening, or changing the URL.</span></span>
- <span data-ttu-id="9a847-207">Poskytování konzistentní předpony rozhraní API pro více back-endové služby.</span><span class="sxs-lookup"><span data-stu-id="9a847-207">Providing a consistent API prefix to multiple back-end services.</span></span>
- <span data-ttu-id="9a847-208">Napodobování odezvy na vyvíjený koncový bod.</span><span class="sxs-lookup"><span data-stu-id="9a847-208">Mocking a response to an endpoint being developed.</span></span>
- <span data-ttu-id="9a847-209">Poskytnutí statické odezvy na známý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="9a847-209">Providing a static response to a well-known endpoint.</span></span>
- <span data-ttu-id="9a847-210">Udržování konzistentního koncového bodu rozhraní API v době, kdy je back-end přesunut nebo migrován.</span><span class="sxs-lookup"><span data-stu-id="9a847-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="9a847-211">Proxy servery jsou uloženy jako definice JSON.</span><span class="sxs-lookup"><span data-stu-id="9a847-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="9a847-212">Tady je příklad:</span><span class="sxs-lookup"><span data-stu-id="9a847-212">Here is an example:</span></span>

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

<span data-ttu-id="9a847-213">Proxy `Domain Redirect` má zkrácenou trasu a mapuje ji na delší prostředek funkce.</span><span class="sxs-lookup"><span data-stu-id="9a847-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="9a847-214">Transformace vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="9a847-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="9a847-215">Proxy serveru `Root` přebírá cokoli odeslané na kořenovou adresu URL (`https://--shorturl--/`) a přesměruje je na web dokumentace.</span><span class="sxs-lookup"><span data-stu-id="9a847-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="9a847-216">Příklad použití proxy serverů je zobrazený ve videu [Azure: přeneste svou aplikaci do cloudu pomocí Azure Functions bez serveru](https://channel9.msdn.com/events/Connect/2017/E102).</span><span class="sxs-lookup"><span data-stu-id="9a847-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="9a847-217">V reálném čase je ASP.NET Core aplikace běžící v místním SQL Server migrována do cloudu Azure.</span><span class="sxs-lookup"><span data-stu-id="9a847-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="9a847-218">Proxy servery slouží k refaktorování tradičního projektu webového rozhraní API, aby mohli používat funkce.</span><span class="sxs-lookup"><span data-stu-id="9a847-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="9a847-219">Další informace o proxy serverech najdete v tématu věnovaném [práci s proxy služby Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span><span class="sxs-lookup"><span data-stu-id="9a847-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9a847-220">[Předchozí](azure-serverless-platform.md)
>[Další](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="9a847-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
