---
title: Ukázkové obchodní scénáře a případy použití pro aplikace bez serveru
description: Přístup k ukázkám, které jsou v rozsahu od zpracování obrazu až po mobilní kanály a kanály ETL, se naučíte bez serveru s praktickým přístupem.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/17/2020
ms.openlocfilehash: 3cb3b73325fccc327ccf17f7298048f2eeb3577a
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158447"
---
# <a name="serverless-business-scenarios-and-use-cases"></a><span data-ttu-id="ee64a-103">Obchodní scénáře aplikací bez serveru a případy použití</span><span class="sxs-lookup"><span data-stu-id="ee64a-103">Serverless business scenarios and use cases</span></span>

<span data-ttu-id="ee64a-104">K dispozici je mnoho případů použití a scénářů pro aplikace bez serveru.</span><span class="sxs-lookup"><span data-stu-id="ee64a-104">There are many use cases and scenarios for serverless applications.</span></span> <span data-ttu-id="ee64a-105">Tato kapitola obsahuje ukázky, které ilustrují různé scénáře.</span><span class="sxs-lookup"><span data-stu-id="ee64a-105">This chapter includes samples that illustrate the different scenarios.</span></span> <span data-ttu-id="ee64a-106">Scénáře obsahují odkazy na související dokumentaci a veřejné úložiště zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="ee64a-106">The scenarios include links to related documentation and public source code repositories.</span></span> <span data-ttu-id="ee64a-107">Ukázky v této kapitole vám umožní začít pracovat s vlastními vytvářením a implementací řešení bez serveru.</span><span class="sxs-lookup"><span data-stu-id="ee64a-107">The samples in this chapter enable you to get started on your own building and implementing serverless solutions.</span></span>

## <a name="big-data-processing"></a><span data-ttu-id="ee64a-108">Zpracování velkých objemů dat</span><span class="sxs-lookup"><span data-stu-id="ee64a-108">Big data processing</span></span>

![Mapování/zmenšení diagramu](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/media/mapreducearchitecture.png)

<span data-ttu-id="ee64a-110">V tomto příkladu se používá bez serveru k provedení operace mapování/zmenšování pro sadu velkých objemů dat.</span><span class="sxs-lookup"><span data-stu-id="ee64a-110">This example uses serverless to do a map/reduce operation on a big data set.</span></span> <span data-ttu-id="ee64a-111">Určuje průměrnou rychlost New York Yellow taxislužby TRIPS za den v 2017.</span><span class="sxs-lookup"><span data-stu-id="ee64a-111">It determines the average speed of New York Yellow taxi trips per day in 2017.</span></span>

[<span data-ttu-id="ee64a-112">Zpracování velkých objemů dat: MapReduce bez serveru v Azure</span><span class="sxs-lookup"><span data-stu-id="ee64a-112">Big Data Processing: Serverless MapReduce on Azure</span></span>](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)

## <a name="create-serverless-applications-hands-on-lab"></a><span data-ttu-id="ee64a-113">Vytváření aplikací bez serveru: praktická cvičení</span><span class="sxs-lookup"><span data-stu-id="ee64a-113">Create serverless applications: hands-on lab</span></span>

<span data-ttu-id="ee64a-114">Naučte se používat funkce pro spouštění logiky na straně serveru a vytváření architektur bez serveru.</span><span class="sxs-lookup"><span data-stu-id="ee64a-114">Learn how to use functions to execute server-side logic and build serverless architectures.</span></span>

- <span data-ttu-id="ee64a-115">Výběr nejlepší služby Azure pro vaši firmu</span><span class="sxs-lookup"><span data-stu-id="ee64a-115">Choosing the best Azure service for your business</span></span>
- <span data-ttu-id="ee64a-116">Vytváření Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ee64a-116">Creating Azure Functions</span></span>
- <span data-ttu-id="ee64a-117">Používání triggerů</span><span class="sxs-lookup"><span data-stu-id="ee64a-117">Using triggers</span></span>
- <span data-ttu-id="ee64a-118">Funkce zřetězení</span><span class="sxs-lookup"><span data-stu-id="ee64a-118">Chaining functions</span></span>
- <span data-ttu-id="ee64a-119">Dlouhotrvající pracovní postupy</span><span class="sxs-lookup"><span data-stu-id="ee64a-119">Long-running workflows</span></span>
- <span data-ttu-id="ee64a-120">Monitorování</span><span class="sxs-lookup"><span data-stu-id="ee64a-120">Monitoring</span></span>
- <span data-ttu-id="ee64a-121">Vývoj, testování a nasazení</span><span class="sxs-lookup"><span data-stu-id="ee64a-121">Development, testing, and deployment</span></span>

[<span data-ttu-id="ee64a-122">Vytváření bezserverových aplikací</span><span class="sxs-lookup"><span data-stu-id="ee64a-122">Create serverless applications</span></span>](https://docs.microsoft.com/learn/paths/create-serverless-applications/)

## <a name="customer-reviews"></a><span data-ttu-id="ee64a-123">Recenze zákazníků</span><span class="sxs-lookup"><span data-stu-id="ee64a-123">Customer reviews</span></span>

<span data-ttu-id="ee64a-124">Tato ukázka předvádí nové nástroje Azure Functions pro knihovny tříd jazyka C# v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ee64a-124">This sample showcases the new Azure Functions tooling for C# Class Libraries in Visual Studio.</span></span> <span data-ttu-id="ee64a-125">Vytvořte web, kde zákazníci odesílají recenze produktů uložené v Azure Storage BLOBs a CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="ee64a-125">Create a website where customers submit product reviews that are stored in Azure storage blobs and CosmosDB.</span></span> <span data-ttu-id="ee64a-126">Přidejte funkci Azure, která umožňuje automatizované moderování revizí zákazníka pomocí Cognitive Services Azure.</span><span class="sxs-lookup"><span data-stu-id="ee64a-126">Add an Azure Function to perform automated moderation of the customer reviews using Azure Cognitive Services.</span></span> <span data-ttu-id="ee64a-127">Použijte frontu úložiště Azure k oddělení webu od funkce.</span><span class="sxs-lookup"><span data-stu-id="ee64a-127">Use an Azure storage queue to decouple the website from the function.</span></span>

[<span data-ttu-id="ee64a-128">Aplikace pro revize zákazníků pomocí Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="ee64a-128">Customer Reviews App with Cognitive Services</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)

## <a name="docker-linux-image-support"></a><span data-ttu-id="ee64a-129">Podpora imagí Docker Linux</span><span class="sxs-lookup"><span data-stu-id="ee64a-129">Docker Linux image support</span></span>

<span data-ttu-id="ee64a-130">Tato ukázka demonstruje, jak `Dockerfile` vytvořit a spustit Azure Functions v kontejneru Linux Docker.</span><span class="sxs-lookup"><span data-stu-id="ee64a-130">This sample demonstrates how to create a `Dockerfile` to build and run Azure Functions on a Linux Docker container.</span></span>

[<span data-ttu-id="ee64a-131">Azure Functions v systému Linux</span><span class="sxs-lookup"><span data-stu-id="ee64a-131">Azure Functions on Linux</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)

## <a name="file-processing-and-validation"></a><span data-ttu-id="ee64a-132">Zpracování a ověřování souborů</span><span class="sxs-lookup"><span data-stu-id="ee64a-132">File processing and validation</span></span>

<span data-ttu-id="ee64a-133">Tento příklad analyzuje sadu souborů CSV od hypotetických zákazníků.</span><span class="sxs-lookup"><span data-stu-id="ee64a-133">This example parses a set of CSV files from hypothetical customers.</span></span> <span data-ttu-id="ee64a-134">Zajišťuje připravenost všech souborů požadovaných pro zákazníka "Batch" a potom ověří strukturu každého souboru.</span><span class="sxs-lookup"><span data-stu-id="ee64a-134">It ensures that all files required for a customer "batch" are ready, then validates the structure of each file.</span></span> <span data-ttu-id="ee64a-135">Různá řešení se zobrazují pomocí Azure Functions, Logic Apps a Durable Functions.</span><span class="sxs-lookup"><span data-stu-id="ee64a-135">Different solutions are presented using Azure Functions, Logic Apps, and Durable Functions.</span></span>

[<span data-ttu-id="ee64a-136">Zpracování a ověřování souborů pomocí Azure Functions, Logic Apps a Durable Functions</span><span class="sxs-lookup"><span data-stu-id="ee64a-136">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)

## <a name="game-data-visualization"></a><span data-ttu-id="ee64a-137">Vizualizace herních dat</span><span class="sxs-lookup"><span data-stu-id="ee64a-137">Game data visualization</span></span>

![Telemetrie her](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/media/points.png)

<span data-ttu-id="ee64a-139">Příklad, jak vývojář může implementovat řešení vizualizace dat v editoru pro svou hru.</span><span class="sxs-lookup"><span data-stu-id="ee64a-139">An example of how a developer could implement an in-editor data visualization solution for their game.</span></span> <span data-ttu-id="ee64a-140">Ve skutečnosti se modul plug-in a modul plug-in Unreal Engine vyvinul pomocí této ukázky jako jeho back-end.</span><span class="sxs-lookup"><span data-stu-id="ee64a-140">In fact, an Unreal Engine 4 Plugin and Unity Plugin were developed using this sample as its backend.</span></span> <span data-ttu-id="ee64a-141">Součást služby je nezávislá herního stroje.</span><span class="sxs-lookup"><span data-stu-id="ee64a-141">The service component is game engine agnostic.</span></span>

[<span data-ttu-id="ee64a-142">Vizualizace telemetrie her v editoru</span><span class="sxs-lookup"><span data-stu-id="ee64a-142">In-editor game telemetry visualization</span></span>](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)

## <a name="graphql"></a><span data-ttu-id="ee64a-143">GraphQL</span><span class="sxs-lookup"><span data-stu-id="ee64a-143">GraphQL</span></span>

<span data-ttu-id="ee64a-144">Vytvořte funkci bez serveru, která zpřístupňuje rozhraní GraphQL API.</span><span class="sxs-lookup"><span data-stu-id="ee64a-144">Create a serverless function that exposes a GraphQL API.</span></span>

[<span data-ttu-id="ee64a-145">Funkce bez serveru pro GraphQL</span><span class="sxs-lookup"><span data-stu-id="ee64a-145">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)

## <a name="internet-of-things-iot-reliable-edge-relay"></a><span data-ttu-id="ee64a-146">Spolehlivý hraniční přenos Internet věcí (IoT)</span><span class="sxs-lookup"><span data-stu-id="ee64a-146">Internet of Things (IoT) reliable edge relay</span></span>

![Architektura IoT](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/media/architecture.png)

<span data-ttu-id="ee64a-148">Tato ukázka implementuje nový komunikační protokol, který umožňuje spolehlivou komunikaci ze zařízení IoT.</span><span class="sxs-lookup"><span data-stu-id="ee64a-148">This sample implements a new communication protocol to enable reliable upstream communication from IoT devices.</span></span> <span data-ttu-id="ee64a-149">Automatizuje detekci a zpětnou výplň datových mezer.</span><span class="sxs-lookup"><span data-stu-id="ee64a-149">It automates data gap detection and backfill.</span></span>

[<span data-ttu-id="ee64a-150">IoT Reliable Edge Relay</span><span class="sxs-lookup"><span data-stu-id="ee64a-150">IoT Reliable Edge Relay</span></span>](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)

## <a name="microservices-reference-architecture"></a><span data-ttu-id="ee64a-151">Referenční architektura mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="ee64a-151">Microservices reference architecture</span></span>

![Referenční architektura](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/media/macro-architecture.png)

<span data-ttu-id="ee64a-153">Referenční architektura, která vás provede procesem rozhodování, který se zabývá návrhem, vývojem a poskytováním RideShare aplikací Relecloud (fiktivní společnost).</span><span class="sxs-lookup"><span data-stu-id="ee64a-153">A reference architecture that walks you through the decision-making process involved in designing, developing, and delivering the Rideshare by Relecloud application (a fictitious company).</span></span> <span data-ttu-id="ee64a-154">Obsahuje praktické pokyny ke konfiguraci a nasazení všech komponent architektury.</span><span class="sxs-lookup"><span data-stu-id="ee64a-154">It includes hands-on instructions for configuring and deploying all of the architecture's components.</span></span>

[<span data-ttu-id="ee64a-155">Referenční architektura mikroslužeb bez serveru</span><span class="sxs-lookup"><span data-stu-id="ee64a-155">Serverless Microservices reference architecture</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

## <a name="migrate-console-apps-to-serverless"></a><span data-ttu-id="ee64a-156">Migrace konzolových aplikací na bez serveru</span><span class="sxs-lookup"><span data-stu-id="ee64a-156">Migrate console apps to serverless</span></span>

<span data-ttu-id="ee64a-157">Tato ukázka je obecná funkce (`.csx` soubor), která se dá použít k převedení jakékoli konzolové aplikace na webovou službu HTTP v Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="ee64a-157">This sample is a generic function (`.csx` file) that can be used to convert any console application to an HTTP web service in Azure Functions.</span></span> <span data-ttu-id="ee64a-158">Vše, co musíte udělat, je upravit konfigurační soubor a určit, jaké vstupní parametry se budou předávat jako argumenty `.exe`do.</span><span class="sxs-lookup"><span data-stu-id="ee64a-158">All you have to do is edit a configuration file and specify what input parameters will be passed as arguments to the `.exe`.</span></span>

[<span data-ttu-id="ee64a-159">Spouštění konzolových aplikací v Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ee64a-159">Run Console Apps on Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)

## <a name="serverless-for-mobile"></a><span data-ttu-id="ee64a-160">Bez serveru pro mobilní zařízení</span><span class="sxs-lookup"><span data-stu-id="ee64a-160">Serverless for mobile</span></span>

<span data-ttu-id="ee64a-161">Azure Functions lze snadno implementovat a udržovat a přistupovat prostřednictvím protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="ee64a-161">Azure Functions are easy to implement and maintain, and accessible through HTTP.</span></span> <span data-ttu-id="ee64a-162">Jsou skvělým způsobem, jak implementovat rozhraní API pro mobilní aplikace.</span><span class="sxs-lookup"><span data-stu-id="ee64a-162">They are a great way to implement an API for a mobile application.</span></span> <span data-ttu-id="ee64a-163">Microsoft nabízí skvělé nástroje pro více platforem pro iOS, Android a Windows s využitím Xamarin.</span><span class="sxs-lookup"><span data-stu-id="ee64a-163">Microsoft offers great cross-platform tools for iOS, Android, and Windows with Xamarin.</span></span> <span data-ttu-id="ee64a-164">V takovém případě Xamarin a Azure Functions fungují skvěle společně.</span><span class="sxs-lookup"><span data-stu-id="ee64a-164">As such, Xamarin and Azure Functions are working great together.</span></span> <span data-ttu-id="ee64a-165">Tento článek ukazuje, jak implementovat funkci Azure Functions v Azure Portal nebo v aplikaci Visual Studio poprvé a vytvořit klienta pro různé platformy pomocí Xamarin. Forms běžící v Androidu, iOS a Windows.</span><span class="sxs-lookup"><span data-stu-id="ee64a-165">This article shows how to implement an Azure Function in the Azure portal or in Visual Studio at first, and build a cross-platform client with Xamarin.Forms running on Android, iOS, and Windows.</span></span>

[<span data-ttu-id="ee64a-166">Implementace jednoduché funkce Azure Functions s klientem Xamarin. Forms</span><span class="sxs-lookup"><span data-stu-id="ee64a-166">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)

## <a name="serverless-messaging"></a><span data-ttu-id="ee64a-167">Zasílání zpráv bez serveru</span><span class="sxs-lookup"><span data-stu-id="ee64a-167">Serverless messaging</span></span>

<span data-ttu-id="ee64a-168">V této ukázce se dozvíte, jak použít Durable Functions vzorek ventilátoru pro načtení libovolného počtu zpráv v rámci libovolného počtu relací nebo oddílů.</span><span class="sxs-lookup"><span data-stu-id="ee64a-168">This sample shows how to utilize Durable Functions' fan-out pattern to load an arbitrary number of messages across any number of sessions/partitions.</span></span> <span data-ttu-id="ee64a-169">Cílí na Service Bus, Event Hubs nebo fronty úložiště.</span><span class="sxs-lookup"><span data-stu-id="ee64a-169">It targets Service Bus, Event Hubs, or Storage Queues.</span></span> <span data-ttu-id="ee64a-170">Ukázka také přidává možnost využít tyto zprávy s jinou funkcí Azure a načíst výsledná časová data do jiného centra událostí.</span><span class="sxs-lookup"><span data-stu-id="ee64a-170">The sample also adds the ability to consume those messages with another Azure Function and load the resulting timing data in to another Event Hub.</span></span> <span data-ttu-id="ee64a-171">Data se pak ingestují do analytických služeb, jako je Azure Průzkumník dat.</span><span class="sxs-lookup"><span data-stu-id="ee64a-171">The data is then ingested into analytics services like Azure Data Explorer.</span></span>

[<span data-ttu-id="ee64a-172">Vytváření a využívání zpráv prostřednictvím Service Bus, Event Hubs a front úložiště s Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ee64a-172">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)

## <a name="recommended-resources"></a><span data-ttu-id="ee64a-173">Doporučené prostředky</span><span class="sxs-lookup"><span data-stu-id="ee64a-173">Recommended resources</span></span>

- [<span data-ttu-id="ee64a-174">Azure Functions v systému Linux</span><span class="sxs-lookup"><span data-stu-id="ee64a-174">Azure Functions on Linux</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)
- [<span data-ttu-id="ee64a-175">Zpracování velkých objemů dat: MapReduce bez serveru v Azure</span><span class="sxs-lookup"><span data-stu-id="ee64a-175">Big Data Processing: Serverless MapReduce on Azure</span></span>](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)
- [<span data-ttu-id="ee64a-176">Vytváření bezserverových aplikací</span><span class="sxs-lookup"><span data-stu-id="ee64a-176">Create serverless applications</span></span>](https://docs.microsoft.com/learn/paths/create-serverless-applications/)
- [<span data-ttu-id="ee64a-177">Aplikace pro revize zákazníků pomocí Cognitive Services</span><span class="sxs-lookup"><span data-stu-id="ee64a-177">Customer Reviews App with Cognitive Services</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)
- [<span data-ttu-id="ee64a-178">Zpracování a ověřování souborů pomocí Azure Functions, Logic Apps a Durable Functions</span><span class="sxs-lookup"><span data-stu-id="ee64a-178">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)
- [<span data-ttu-id="ee64a-179">Implementace jednoduché funkce Azure Functions s klientem Xamarin. Forms</span><span class="sxs-lookup"><span data-stu-id="ee64a-179">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [<span data-ttu-id="ee64a-180">Vizualizace telemetrie her v editoru</span><span class="sxs-lookup"><span data-stu-id="ee64a-180">In-editor game telemetry visualization</span></span>](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)
- [<span data-ttu-id="ee64a-181">IoT Reliable Edge Relay</span><span class="sxs-lookup"><span data-stu-id="ee64a-181">IoT Reliable Edge Relay</span></span>](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)
- [<span data-ttu-id="ee64a-182">Vytváření a využívání zpráv prostřednictvím Service Bus, Event Hubs a front úložiště s Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ee64a-182">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)
- [<span data-ttu-id="ee64a-183">Spouštění konzolových aplikací v Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ee64a-183">Run Console Apps on Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)
- [<span data-ttu-id="ee64a-184">Funkce bez serveru pro GraphQL</span><span class="sxs-lookup"><span data-stu-id="ee64a-184">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)
- [<span data-ttu-id="ee64a-185">Referenční architektura mikroslužeb bez serveru</span><span class="sxs-lookup"><span data-stu-id="ee64a-185">Serverless Microservices reference architecture</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

>[!div class="step-by-step"]
><span data-ttu-id="ee64a-186">[Předchozí](orchestration-patterns.md)
>[Další](serverless-conclusion.md)</span><span class="sxs-lookup"><span data-stu-id="ee64a-186">[Previous](orchestration-patterns.md)
[Next](serverless-conclusion.md)</span></span>
