---
title: Začínáme se službou Azure Queue Storage s využitím F#
description: Fronty Azure poskytují spolehlivé a asynchronní zasílání zpráv mezi součástmi aplikace. Cloudové zasílání zpráv umožňuje nezávisle škálovat komponenty vaší aplikace.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: a09cbdd4b995e34177c110ce91b02162bb19dfa8
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73423849"
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="7454f-104">Začínáme s úložištěm Azure Queue pomocí jazyka F\#</span><span class="sxs-lookup"><span data-stu-id="7454f-104">Get started with Azure Queue storage using F\#</span></span>

<span data-ttu-id="7454f-105">Azure Queue Storage poskytuje cloudové zprávy mezi součástmi aplikace.</span><span class="sxs-lookup"><span data-stu-id="7454f-105">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="7454f-106">V navrhování aplikací pro škálování jsou součásti aplikace často odděleny, takže je lze škálovat nezávisle.</span><span class="sxs-lookup"><span data-stu-id="7454f-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="7454f-107">Queue Storage zajišťuje asynchronní zasílání zpráv pro komunikaci mezi součástmi aplikace, ať už jsou spuštěné v cloudu, v desktopovém prostředí, na místním serveru nebo na mobilním zařízení.</span><span class="sxs-lookup"><span data-stu-id="7454f-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="7454f-108">Queue Storage také podporuje správu asynchronních úloh a vytváření pracovních toků procesů.</span><span class="sxs-lookup"><span data-stu-id="7454f-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="7454f-109">O tomto kurzu</span><span class="sxs-lookup"><span data-stu-id="7454f-109">About this tutorial</span></span>

<span data-ttu-id="7454f-110">V tomto kurzu se dozvíte F# , jak napsat kód pro některé běžné úlohy pomocí služby Azure Queue Storage.</span><span class="sxs-lookup"><span data-stu-id="7454f-110">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="7454f-111">Mezi zahrnuté úlohy patří vytváření a odstraňování front a přidávání, čtení a odstraňování zpráv fronty.</span><span class="sxs-lookup"><span data-stu-id="7454f-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="7454f-112">Koncepční přehled služby Queue Storage najdete v [příručce .NET pro úložiště Queue](/azure/storage/storage-dotnet-how-to-use-queues).</span><span class="sxs-lookup"><span data-stu-id="7454f-112">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7454f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7454f-113">Prerequisites</span></span>

<span data-ttu-id="7454f-114">Pokud chcete použít tuto příručku, musíte nejdřív [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="7454f-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="7454f-115">Pro tento účet budete taky potřebovat přístupový klíč k úložišti.</span><span class="sxs-lookup"><span data-stu-id="7454f-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="7454f-116">Vytvoření F# skriptu a spuštění F# Interactive</span><span class="sxs-lookup"><span data-stu-id="7454f-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="7454f-117">Ukázky v tomto článku se dají použít buď v F# aplikaci, nebo ve F# skriptu.</span><span class="sxs-lookup"><span data-stu-id="7454f-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="7454f-118">Chcete-li F# vytvořit skript, vytvořte soubor s příponou `.fsx`, například `queues.fsx`ve vašem F# vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="7454f-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="7454f-119">V dalším kroku pomocí [Správce balíčků](package-management.md) , jako je [paket](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) , nainstalujte balíček `WindowsAzure.Storage` a odkaz `WindowsAzure.Storage.dll` ve svém skriptu pomocí direktivy `#r`.</span><span class="sxs-lookup"><span data-stu-id="7454f-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="7454f-120">Přidat deklarace oboru názvů</span><span class="sxs-lookup"><span data-stu-id="7454f-120">Add namespace declarations</span></span>

<span data-ttu-id="7454f-121">Do horní části `queues.fsx` souboru přidejte následující příkazy `open`:</span><span class="sxs-lookup"><span data-stu-id="7454f-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="7454f-122">Získání připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="7454f-122">Get your connection string</span></span>

<span data-ttu-id="7454f-123">Pro tento kurz budete potřebovat připojovací řetězec Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="7454f-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="7454f-124">Další informace o připojovacích řetězcích najdete v tématu [Konfigurace připojovacích řetězců úložiště](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="7454f-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="7454f-125">V tomto kurzu do skriptu zadáte svůj připojovací řetězec, například:</span><span class="sxs-lookup"><span data-stu-id="7454f-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="7454f-126">To však **nedoporučujeme** pro skutečné projekty.</span><span class="sxs-lookup"><span data-stu-id="7454f-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="7454f-127">Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="7454f-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="7454f-128">Vždy buďte opatrní, abyste chránili klíč účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="7454f-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="7454f-129">Vyhněte se distribuci jiným uživatelům, pevným kódováním nebo uložením v souboru ve formátu prostého textu, který je přístupný ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="7454f-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="7454f-130">Klíč můžete znovu vygenerovat pomocí webu Azure Portal, pokud se domníváte, že je možné, že došlo k ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7454f-130">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="7454f-131">Pro reálné aplikace je nejlepší způsob, jak udržovat připojovací řetězec úložiště, v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="7454f-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="7454f-132">Chcete-li načíst připojovací řetězec z konfiguračního souboru, můžete to provést:</span><span class="sxs-lookup"><span data-stu-id="7454f-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="7454f-133">Použití Azure Configuration Manager je volitelné.</span><span class="sxs-lookup"><span data-stu-id="7454f-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="7454f-134">Můžete také použít rozhraní API, jako je .NET Framework typ `ConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="7454f-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="7454f-135">Analyzovat připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="7454f-135">Parse the connection string</span></span>

<span data-ttu-id="7454f-136">K analýze připojovacího řetězce použijte:</span><span class="sxs-lookup"><span data-stu-id="7454f-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="7454f-137">Tato akce vrátí `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="7454f-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="7454f-138">Vytvoření klienta Služba front</span><span class="sxs-lookup"><span data-stu-id="7454f-138">Create the Queue service client</span></span>

<span data-ttu-id="7454f-139">Třída `CloudQueueClient` umožňuje načítat fronty uložené v úložišti front.</span><span class="sxs-lookup"><span data-stu-id="7454f-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="7454f-140">Tady je jeden ze způsobů, jak vytvořit klienta služby:</span><span class="sxs-lookup"><span data-stu-id="7454f-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="7454f-141">Nyní jste připraveni napsat kód, který čte data z a zapisuje data do fronty úložiště.</span><span class="sxs-lookup"><span data-stu-id="7454f-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="7454f-142">Vytvoření fronty</span><span class="sxs-lookup"><span data-stu-id="7454f-142">Create a queue</span></span>

<span data-ttu-id="7454f-143">Tento příklad ukazuje, jak vytvořit frontu, pokud ještě neexistuje:</span><span class="sxs-lookup"><span data-stu-id="7454f-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="7454f-144">Vložení zprávy do fronty</span><span class="sxs-lookup"><span data-stu-id="7454f-144">Insert a message into a queue</span></span>

<span data-ttu-id="7454f-145">Chcete-li vložit zprávu do existující fronty, vytvořte nejprve novou `CloudQueueMessage`.</span><span class="sxs-lookup"><span data-stu-id="7454f-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="7454f-146">Dále zavolejte metodu `AddMessage`.</span><span class="sxs-lookup"><span data-stu-id="7454f-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="7454f-147">`CloudQueueMessage` lze vytvořit buď pomocí řetězce (ve formátu UTF-8), nebo pole `byte`, například takto:</span><span class="sxs-lookup"><span data-stu-id="7454f-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="7454f-148">Prohlížet další zprávu</span><span class="sxs-lookup"><span data-stu-id="7454f-148">Peek at the next message</span></span>

<span data-ttu-id="7454f-149">Můžete prohlížet zprávy před frontou, aniž byste je odebrali z fronty, voláním metody `PeekMessage`.</span><span class="sxs-lookup"><span data-stu-id="7454f-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="7454f-150">Získat další zprávu ke zpracování</span><span class="sxs-lookup"><span data-stu-id="7454f-150">Get the next message for processing</span></span>

<span data-ttu-id="7454f-151">Zprávu můžete načíst na začátku fronty ke zpracování voláním metody `GetMessage`.</span><span class="sxs-lookup"><span data-stu-id="7454f-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="7454f-152">Později označíte úspěšné zpracování zprávy pomocí `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="7454f-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="7454f-153">Změna obsahu zprávy ve frontě</span><span class="sxs-lookup"><span data-stu-id="7454f-153">Change the contents of a queued message</span></span>

<span data-ttu-id="7454f-154">Obsah načtené zprávy můžete změnit na místě ve frontě.</span><span class="sxs-lookup"><span data-stu-id="7454f-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="7454f-155">Pokud zpráva představuje pracovní úlohu, můžete tuto funkci použít k aktualizaci stavu pracovní úlohy.</span><span class="sxs-lookup"><span data-stu-id="7454f-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="7454f-156">Následující kód aktualizuje zprávu fronty novými obsahem a nastaví časový limit viditelnosti na prodloužení dalších 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="7454f-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="7454f-157">Tím se uloží stav práce, která je přidružená ke zprávě, a poskytne klientovi další minutu, aby pokračoval v práci na této zprávě.</span><span class="sxs-lookup"><span data-stu-id="7454f-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="7454f-158">Pomocí této techniky můžete sledovat víceúrovňové pracovní postupy u zpráv ve frontě, aniž byste museli začít od začátku, pokud krok zpracování selže kvůli selhání hardwaru nebo softwaru.</span><span class="sxs-lookup"><span data-stu-id="7454f-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="7454f-159">Obvykle byste zachovali počet opakování i v případě, že se zpráva znovu pokusí o více než pár časů, takže byste ji odstranili.</span><span class="sxs-lookup"><span data-stu-id="7454f-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="7454f-160">To je chráněno proti zprávě, která při každém zpracování vyvolá chybu aplikace.</span><span class="sxs-lookup"><span data-stu-id="7454f-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="7454f-161">Zruší zařazení další zprávy do fronty.</span><span class="sxs-lookup"><span data-stu-id="7454f-161">De-queue the next message</span></span>

<span data-ttu-id="7454f-162">Kód z fronty odřadí zprávu z fronty ve dvou krocích.</span><span class="sxs-lookup"><span data-stu-id="7454f-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="7454f-163">Když zavoláte `GetMessage`, dostanete další zprávu ve frontě.</span><span class="sxs-lookup"><span data-stu-id="7454f-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="7454f-164">Zpráva vrácená z `GetMessage` bude neviditelná pro jakýkoliv jiný kód, který čte zprávy z této fronty.</span><span class="sxs-lookup"><span data-stu-id="7454f-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="7454f-165">Ve výchozím nastavení tato zpráva zůstane po dobu 30 sekund neviditelná.</span><span class="sxs-lookup"><span data-stu-id="7454f-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="7454f-166">Chcete-li dokončit odebrání zprávy z fronty, je nutné také volat `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="7454f-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="7454f-167">Tento dvoustupňový proces odebrání zprávy zaručuje, že pokud váš kód nedokáže zpracovat zprávu z důvodu selhání hardwaru nebo softwaru, může jiná instance kódu získat stejnou zprávu a zkusit to znovu.</span><span class="sxs-lookup"><span data-stu-id="7454f-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="7454f-168">Váš kód volá `DeleteMessage` hned po zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="7454f-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="7454f-169">Použití asynchronních pracovních postupů s rozhraními API služby Common Queue Storage</span><span class="sxs-lookup"><span data-stu-id="7454f-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="7454f-170">Tento příklad ukazuje, jak použít asynchronní pracovní postup s běžnými rozhraními API služby Queue Storage.</span><span class="sxs-lookup"><span data-stu-id="7454f-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="7454f-171">Další možnosti pro zprávy o zrušení fronty</span><span class="sxs-lookup"><span data-stu-id="7454f-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="7454f-172">Existují dva způsoby, jak můžete přizpůsobit načítání zpráv z fronty.</span><span class="sxs-lookup"><span data-stu-id="7454f-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="7454f-173">Nejprve můžete získat dávku zpráv (až do 32).</span><span class="sxs-lookup"><span data-stu-id="7454f-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="7454f-174">Za druhé můžete nastavit delší nebo kratší časový limit neviditelnosti, což umožňuje, aby váš kód měl více nebo méně času na úplné zpracování každé zprávy.</span><span class="sxs-lookup"><span data-stu-id="7454f-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="7454f-175">Následující příklad kódu používá `GetMessages` k získání 20 zpráv v jednom volání a pak zpracovává každou zprávu.</span><span class="sxs-lookup"><span data-stu-id="7454f-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="7454f-176">Nastaví také časový limit neviditelnosti na pět minut pro každou zprávu.</span><span class="sxs-lookup"><span data-stu-id="7454f-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="7454f-177">Všimněte si, že 5 minut začne u všech zpráv současně, takže po uplynutí 5 minut od volání `GetMessages`se všechny zprávy, které nebyly odstraněny, opět zobrazí.</span><span class="sxs-lookup"><span data-stu-id="7454f-177">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="7454f-178">Získat délku fronty</span><span class="sxs-lookup"><span data-stu-id="7454f-178">Get the queue length</span></span>

<span data-ttu-id="7454f-179">Můžete získat odhad počtu zpráv ve frontě.</span><span class="sxs-lookup"><span data-stu-id="7454f-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="7454f-180">Metoda `FetchAttributes` požádá Služba front o načtení atributů fronty, včetně počtu zpráv.</span><span class="sxs-lookup"><span data-stu-id="7454f-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="7454f-181">Vlastnost `ApproximateMessageCount` vrací poslední hodnotu získanou metodou `FetchAttributes` bez volání Služba front.</span><span class="sxs-lookup"><span data-stu-id="7454f-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="7454f-182">Odstranění fronty</span><span class="sxs-lookup"><span data-stu-id="7454f-182">Delete a queue</span></span>

<span data-ttu-id="7454f-183">Pokud chcete odstranit frontu a všechny zprávy, které jsou v ní obsažené, zavolejte metodu `Delete` u objektu Queue.</span><span class="sxs-lookup"><span data-stu-id="7454f-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](~/samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="7454f-184">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7454f-184">Next steps</span></span>

<span data-ttu-id="7454f-185">Teď, když jste se naučili základní informace o službě Queue Storage, získáte další informace o složitějších úlohách úložiště pomocí těchto odkazů.</span><span class="sxs-lookup"><span data-stu-id="7454f-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="7454f-186">Rozhraní API pro Azure Storage pro .NET</span><span class="sxs-lookup"><span data-stu-id="7454f-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="7454f-187">Poskytovatel typu Azure Storage</span><span class="sxs-lookup"><span data-stu-id="7454f-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="7454f-188">Blog týmu Azure Storage</span><span class="sxs-lookup"><span data-stu-id="7454f-188">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="7454f-189">Konfigurace připojovacích řetězců Azure Storage</span><span class="sxs-lookup"><span data-stu-id="7454f-189">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="7454f-190">Referenční informace pro službu Azure Storage Services REST API</span><span class="sxs-lookup"><span data-stu-id="7454f-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
