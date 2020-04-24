---
title: Aplikace bez serveru Azure Functions
description: Azure Functions poskytuje možnosti bez serveru v různých jazycích (C#, JavaScript, Java) a platformy pro poskytování kódu okamžitého škálování založeného na událostech.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 2dee60e3635be94a55ee26a7f04942bc59cb8dec
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135721"
---
# <a name="azure-functions"></a><span data-ttu-id="801a8-103">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="801a8-103">Azure Functions</span></span>

<span data-ttu-id="801a8-104">Azure Functions poskytuje výpočetní prostředí bez serveru.</span><span class="sxs-lookup"><span data-stu-id="801a8-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="801a8-105">Funkce je vyvolána *triggerem* (například přístup ke koncovému bodu http nebo časovači) a spustí blok kódu nebo obchodní logiky.</span><span class="sxs-lookup"><span data-stu-id="801a8-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="801a8-106">Funkce také podporují specializované *vazby* , které se připojují k prostředkům, jako jsou úložiště a fronty.</span><span class="sxs-lookup"><span data-stu-id="801a8-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Logo Azure Functions](./media/azure-functions-logo.png)

<span data-ttu-id="801a8-108">Aktuální verze modulu runtime 3,0 podporuje aplikace .NET Core 3,1 pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="801a8-108">The current runtime version 3.0 supports cross-platform .NET Core 3.1 applications.</span></span> <span data-ttu-id="801a8-109">Podporují se další jazyky kromě C#, jako je JavaScript, F # a Java.</span><span class="sxs-lookup"><span data-stu-id="801a8-109">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="801a8-110">Funkce vytvořené na portálu poskytují bohatou syntaxi skriptování.</span><span class="sxs-lookup"><span data-stu-id="801a8-110">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="801a8-111">Funkce vytvořené jako samostatné projekty lze nasadit s využitím plné podpory platforem a možností.</span><span class="sxs-lookup"><span data-stu-id="801a8-111">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="801a8-112">Další informace najdete v [dokumentaci Azure Functions](https://docs.microsoft.com/azure/azure-functions).</span><span class="sxs-lookup"><span data-stu-id="801a8-112">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="801a8-113">Podpora programovacích jazyků</span><span class="sxs-lookup"><span data-stu-id="801a8-113">Programming language support</span></span>

<span data-ttu-id="801a8-114">V rámci všeobecné dostupnosti (GA) jsou podporovány následující jazyky.</span><span class="sxs-lookup"><span data-stu-id="801a8-114">The following languages are all supported in general availability (GA).</span></span>

|<span data-ttu-id="801a8-115">Jazyk</span><span class="sxs-lookup"><span data-stu-id="801a8-115">Language</span></span>      |<span data-ttu-id="801a8-116">Podporované moduly runtime</span><span class="sxs-lookup"><span data-stu-id="801a8-116">Supported runtimes</span></span>|
|--------------|------------------|
|<span data-ttu-id="801a8-117">**R #**</span><span class="sxs-lookup"><span data-stu-id="801a8-117">**C#**</span></span>        |<span data-ttu-id="801a8-118">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="801a8-118">.NET Core 3.1</span></span>     |
|<span data-ttu-id="801a8-119">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="801a8-119">**JavaScript**</span></span>|<span data-ttu-id="801a8-120">Uzel 10 & 12</span><span class="sxs-lookup"><span data-stu-id="801a8-120">Node 10 & 12</span></span>      |
|<span data-ttu-id="801a8-121">**F#**</span><span class="sxs-lookup"><span data-stu-id="801a8-121">**F#**</span></span>        |<span data-ttu-id="801a8-122">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="801a8-122">.NET Core 3.1</span></span>     |
|<span data-ttu-id="801a8-123">**Java**</span><span class="sxs-lookup"><span data-stu-id="801a8-123">**Java**</span></span>      |<span data-ttu-id="801a8-124">Java 8</span><span class="sxs-lookup"><span data-stu-id="801a8-124">Java 8</span></span>            |
|<span data-ttu-id="801a8-125">**Python**</span><span class="sxs-lookup"><span data-stu-id="801a8-125">**Python**</span></span>    |<span data-ttu-id="801a8-126">Python 3,6, 3,7, & 3,8</span><span class="sxs-lookup"><span data-stu-id="801a8-126">Python 3.6, 3.7, & 3.8</span></span>|
|<span data-ttu-id="801a8-127">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="801a8-127">**TypeScript**</span></span>|<span data-ttu-id="801a8-128">Uzel 10 & 12 (přes JavaScript)</span><span class="sxs-lookup"><span data-stu-id="801a8-128">Node 10 & 12 (via JavaScript)</span></span>|
|<span data-ttu-id="801a8-129">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="801a8-129">**PowerShell**</span></span>|<span data-ttu-id="801a8-130">PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="801a8-130">PowerShell Core 6</span></span>|

<span data-ttu-id="801a8-131">Další informace najdete v tématu [Podporované jazyky](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span><span class="sxs-lookup"><span data-stu-id="801a8-131">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="801a8-132">Plány služby App Service</span><span class="sxs-lookup"><span data-stu-id="801a8-132">App service plans</span></span>

<span data-ttu-id="801a8-133">Služba Functions se zálohuje podle *plánu služby App Service*.</span><span class="sxs-lookup"><span data-stu-id="801a8-133">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="801a8-134">Plán definuje prostředky používané aplikací Functions.</span><span class="sxs-lookup"><span data-stu-id="801a8-134">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="801a8-135">Můžete přiřadit plány k oblasti, určit velikost a počet virtuálních počítačů, které se budou používat, a vybrat cenovou úroveň.</span><span class="sxs-lookup"><span data-stu-id="801a8-135">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="801a8-136">Pro skutečný přístup bez serveru můžou aplikace Function App používat plán **spotřeby** .</span><span class="sxs-lookup"><span data-stu-id="801a8-136">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="801a8-137">Plán spotřeby bude automaticky škálovat back-end na základě zatížení.</span><span class="sxs-lookup"><span data-stu-id="801a8-137">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="801a8-138">Dalším parametrem hostování pro aplikace Function App je [Plán Premium](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan).</span><span class="sxs-lookup"><span data-stu-id="801a8-138">Another hosting option for function apps is the [Premium plan](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan).</span></span> <span data-ttu-id="801a8-139">Tento plán poskytuje instanci "Always On", aby se zabránilo studenému startu, podporuje pokročilé funkce, jako je připojení k virtuální síti, a běží na hardwaru Premium.</span><span class="sxs-lookup"><span data-stu-id="801a8-139">This plan provides an "always on" instance to avoid cold start, supports advanced features like VNet connectivity, and runs on premium hardware.</span></span>

<span data-ttu-id="801a8-140">Další informace najdete v tématu [plány služby App Service](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span><span class="sxs-lookup"><span data-stu-id="801a8-140">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="801a8-141">Vytvoření první funkce</span><span class="sxs-lookup"><span data-stu-id="801a8-141">Create your first function</span></span>

<span data-ttu-id="801a8-142">Existují tři běžné způsoby, jak můžete vytvářet aplikace Function App.</span><span class="sxs-lookup"><span data-stu-id="801a8-142">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="801a8-143">Funkce skriptu na portálu.</span><span class="sxs-lookup"><span data-stu-id="801a8-143">Script functions in the portal.</span></span>
- <span data-ttu-id="801a8-144">Vytvořte potřebné prostředky pomocí Azure CLI.</span><span class="sxs-lookup"><span data-stu-id="801a8-144">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="801a8-145">Vytvářejte funkce místně pomocí svého oblíbeného integrovaného vývojového prostředí a publikujte je do Azure.</span><span class="sxs-lookup"><span data-stu-id="801a8-145">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="801a8-146">Další informace o vytvoření skriptované funkce na portálu najdete v tématu [Vytvoření první funkce v Azure Portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span><span class="sxs-lookup"><span data-stu-id="801a8-146">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="801a8-147">Informace o tom, jak vytvořit z Azure CLI, najdete v tématu [Vytvoření první funkce pomocí Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span><span class="sxs-lookup"><span data-stu-id="801a8-147">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="801a8-148">Chcete-li vytvořit funkci ze sady Visual Studio, přečtěte si téma [Vytvoření první funkce pomocí sady Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="801a8-148">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="801a8-149">Principy aktivačních událostí a vazeb</span><span class="sxs-lookup"><span data-stu-id="801a8-149">Understand triggers and bindings</span></span>

<span data-ttu-id="801a8-150">Funkce jsou vyvolány *triggerem* a mohou mít právě jednu.</span><span class="sxs-lookup"><span data-stu-id="801a8-150">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="801a8-151">Kromě vyvolání funkce určité triggery slouží také jako vazby.</span><span class="sxs-lookup"><span data-stu-id="801a8-151">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="801a8-152">Kromě triggeru můžete také definovat více vazeb.</span><span class="sxs-lookup"><span data-stu-id="801a8-152">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="801a8-153">*Vazby* poskytují deklarativní způsob, jak připojit data k vašemu kódu.</span><span class="sxs-lookup"><span data-stu-id="801a8-153">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="801a8-154">Můžou se předávat (zadávat) nebo přijímat data (výstup).</span><span class="sxs-lookup"><span data-stu-id="801a8-154">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="801a8-155">Aktivační události a vazby usnadňují práci s funkcemi.</span><span class="sxs-lookup"><span data-stu-id="801a8-155">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="801a8-156">Vazby odstraňují režii při ručním vytváření připojení databáze nebo systému souborů.</span><span class="sxs-lookup"><span data-stu-id="801a8-156">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="801a8-157">Všechny informace potřebné pro vazby jsou obsaženy ve speciálním souboru *Functions. JSON* pro skripty nebo deklarované pomocí atributů v kódu.</span><span class="sxs-lookup"><span data-stu-id="801a8-157">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="801a8-158">Mezi běžné triggery patří:</span><span class="sxs-lookup"><span data-stu-id="801a8-158">Some common triggers include:</span></span>

- <span data-ttu-id="801a8-159">Blob Storage: vyvolejte funkci, když se v úložišti nahraje nebo změní soubor nebo složka.</span><span class="sxs-lookup"><span data-stu-id="801a8-159">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="801a8-160">HTTP: vyvolání funkce jako REST API.</span><span class="sxs-lookup"><span data-stu-id="801a8-160">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="801a8-161">Queue: vyvolá funkci, když položky ve frontě existují.</span><span class="sxs-lookup"><span data-stu-id="801a8-161">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="801a8-162">Timer: vyvolejte funkci v normálním tempo.</span><span class="sxs-lookup"><span data-stu-id="801a8-162">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="801a8-163">Mezi příklady vazeb patří:</span><span class="sxs-lookup"><span data-stu-id="801a8-163">Examples of bindings include:</span></span>

- <span data-ttu-id="801a8-164">CosmosDB: snadno se připojte k databázi a načíst nebo uložit soubory.</span><span class="sxs-lookup"><span data-stu-id="801a8-164">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="801a8-165">Table Storage: Pracujte s úložištěm klíč/hodnota z aplikace Function App.</span><span class="sxs-lookup"><span data-stu-id="801a8-165">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="801a8-166">Queue Storage: snadno načíst položky z fronty nebo umístit nové položky do fronty.</span><span class="sxs-lookup"><span data-stu-id="801a8-166">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="801a8-167">Následující příklad souboru *Functions. JSON* definuje Trigger a vazbu:</span><span class="sxs-lookup"><span data-stu-id="801a8-167">The following example *functions.json* file defines a trigger and a binding:</span></span>

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

<span data-ttu-id="801a8-168">V tomto příkladu je funkce aktivována změnou v úložišti objektů BLOB v `images` kontejneru.</span><span class="sxs-lookup"><span data-stu-id="801a8-168">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="801a8-169">Informace pro soubor jsou předány, takže Trigger funguje také jako vazba.</span><span class="sxs-lookup"><span data-stu-id="801a8-169">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="801a8-170">Existuje další vazba pro vložení informací do fronty s názvem `images`.</span><span class="sxs-lookup"><span data-stu-id="801a8-170">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="801a8-171">Zde je skript jazyka C# pro funkci:</span><span class="sxs-lookup"><span data-stu-id="801a8-171">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="801a8-172">Příkladem je jednoduchá funkce, která přebírá název souboru, který se změnil nebo nahrál do úložiště objektů blob, a umístí ho do fronty pro pozdější zpracování.</span><span class="sxs-lookup"><span data-stu-id="801a8-172">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="801a8-173">Úplný seznam triggerů a vazeb najdete v tématu [Azure Functions triggery a koncepty vazeb](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span><span class="sxs-lookup"><span data-stu-id="801a8-173">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="801a8-174">[Předchozí](azure-serverless-platform.md)
>[Další](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="801a8-174">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
