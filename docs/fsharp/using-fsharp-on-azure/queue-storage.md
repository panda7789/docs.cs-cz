---
title: 'Začínáme s Azure Queue storage pomocí F #'
description: Azure fronty poskytují spolehlivé, asynchronní zasílání zpráv mezi součástmi aplikace. Cloud zasílání zpráv umožňuje nezávisle škálovat součásti vaší aplikace.
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: bd49fd0f0e8d91449443051ab9a4ffc2d2638e11
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="get-started-with-azure-queue-storage-using-f"></a><span data-ttu-id="7c4d0-104">Začínáme s Azure Queue storage pomocí F #</span><span class="sxs-lookup"><span data-stu-id="7c4d0-104">Get started with Azure Queue storage using F#</span></span> #

<span data-ttu-id="7c4d0-105">Azure Queue storage poskytuje cloudu zasílání zpráv mezi součástmi aplikace.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-105">Azure Queue storage provides cloud messaging between application components.</span></span> <span data-ttu-id="7c4d0-106">Při navrhování aplikací pro škálování, součásti aplikace jsou často odpojené, tak, aby bylo možné škálovat nezávisle.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-106">In designing applications for scale, application components are often decoupled, so that they can scale independently.</span></span> <span data-ttu-id="7c4d0-107">Fronty úložiště poskytuje asynchronní zasílání zpráv pro komunikaci mezi součástmi aplikací, zda jsou spuštěny v cloudu, na ploše, na místním serveru nebo na mobilním zařízení.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-107">Queue storage delivers asynchronous messaging for communication between application components, whether they are running in the cloud, on the desktop, on an on-premises server, or on a mobile device.</span></span> <span data-ttu-id="7c4d0-108">Queue storage také podporuje správu asynchronních úloh a pracovní toky procesu vytváření.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-108">Queue storage also supports managing asynchronous tasks and building process work flows.</span></span>

### <a name="about-this-tutorial"></a><span data-ttu-id="7c4d0-109">O tomto kurzu</span><span class="sxs-lookup"><span data-stu-id="7c4d0-109">About this tutorial</span></span>

<span data-ttu-id="7c4d0-110">Tento kurz ukazuje, jak napsat kód F # pro některé běžné úlohy pomocí Azure Queue storage.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-110">This tutorial shows how to write F# code for some common tasks using Azure Queue storage.</span></span> <span data-ttu-id="7c4d0-111">Úlohy popsané zahrnují vytváření a odstraňování front a přidávání, čtení a odstraňování front zpráv.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-111">Tasks covered include creating and deleting queues and adding, reading, and deleting queue messages.</span></span>

<span data-ttu-id="7c4d0-112">Koncepční přehled služby queue storage, najdete v tématu [v příručce .NET pro úložiště](/azure/storage/storage-dotnet-how-to-use-queues).</span><span class="sxs-lookup"><span data-stu-id="7c4d0-112">For a conceptual overview of queue storage, please see [the .NET guide for queue storage](/azure/storage/storage-dotnet-how-to-use-queues).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7c4d0-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c4d0-113">Prerequisites</span></span>

<span data-ttu-id="7c4d0-114">Chcete-li tohoto průvodce použijte, je nutné nejprve [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="7c4d0-114">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="7c4d0-115">Budete také potřebovat přístupový klíč k úložišti pro tento účet.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-115">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="7c4d0-116">Vytvoření F # skript a spusťte F # interaktivní</span><span class="sxs-lookup"><span data-stu-id="7c4d0-116">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="7c4d0-117">Ukázky v tomto článku slouží v aplikaci F # nebo skriptu F #.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-117">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="7c4d0-118">Chcete-li vytvořit skript F #, vytvořte soubor s `.fsx` příponu, třeba `queues.fsx`, ve vašem vývojovém prostředí F #.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-118">To create an F# script, create a file with the `.fsx` extension, for example `queues.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="7c4d0-119">Pak pomocí [Správce balíčků](package-management.md) například [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` balíčku a referenční dokumentace `WindowsAzure.Storage.dll` ve vašem skriptu, použití `#r`– direktiva.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-119">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="7c4d0-120">Přidání deklarace oborů názvů</span><span class="sxs-lookup"><span data-stu-id="7c4d0-120">Add namespace declarations</span></span>

<span data-ttu-id="7c4d0-121">Přidejte následující `open` příkazů do horní části `queues.fsx` souboru:</span><span class="sxs-lookup"><span data-stu-id="7c4d0-121">Add the following `open` statements to the top of the `queues.fsx` file:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L1-L3)]

### <a name="get-your-connection-string"></a><span data-ttu-id="7c4d0-122">Získat připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="7c4d0-122">Get your connection string</span></span>

<span data-ttu-id="7c4d0-123">Pro účely tohoto kurzu budete potřebovat připojovací řetězec službě Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-123">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="7c4d0-124">Další informace o připojovacích řetězcích najdete v tématu [nakonfigurování připojovacích řetězců Storage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="7c4d0-124">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="7c4d0-125">Pro tento kurz zadáte připojovacího řetězce ve vašem skriptu, například takto:</span><span class="sxs-lookup"><span data-stu-id="7c4d0-125">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L9-L9)]

<span data-ttu-id="7c4d0-126">Je to ale **nedoporučuje** skutečných projekty.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-126">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="7c4d0-127">Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-127">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="7c4d0-128">Vždycky pečlivě k ochraně klíče účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-128">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="7c4d0-129">Nedávejte ho jiným uživatelům, nezakódovávejte ho nebo ho uložit v souboru formátu prostého textu, který je přístupný ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-129">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="7c4d0-130">Můžete znovu vygenerovat klíč pomocí portálu Azure, pokud se domníváte, že by může ohrožení.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-130">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="7c4d0-131">Skutečných aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-131">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="7c4d0-132">K načtení připojovacího řetězce z konfiguračního souboru, můžete to udělat:</span><span class="sxs-lookup"><span data-stu-id="7c4d0-132">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L11-L13)]

<span data-ttu-id="7c4d0-133">Použití nástroje Azure Configuration Manager není povinné.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-133">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="7c4d0-134">Můžete také použít API jako třeba rozhraní .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-134">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="7c4d0-135">Analýza připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="7c4d0-135">Parse the connection string</span></span>

<span data-ttu-id="7c4d0-136">Chcete-li analyzovat připojovací řetězec, použijte:</span><span class="sxs-lookup"><span data-stu-id="7c4d0-136">To parse the connection string, use:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L19-L20)]

<span data-ttu-id="7c4d0-137">Tato možnost vrátí `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-137">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-queue-service-client"></a><span data-ttu-id="7c4d0-138">Vytvoření klienta služby front</span><span class="sxs-lookup"><span data-stu-id="7c4d0-138">Create the Queue service client</span></span>

<span data-ttu-id="7c4d0-139">`CloudQueueClient` Vám umožňuje načíst fronty uložené v rámci Queue storage.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-139">The `CloudQueueClient` class enables you to retrieve queues stored in Queue storage.</span></span> <span data-ttu-id="7c4d0-140">Tady je jeden způsob, jak vytvořit klienta služby:</span><span class="sxs-lookup"><span data-stu-id="7c4d0-140">Here's one way to create the service client:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L26-L26)]

<span data-ttu-id="7c4d0-141">Teď jste připravení psát kód, který načítá a zapisuje data do fronty úložiště.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-141">Now you are ready to write code that reads data from and writes data to Queue storage.</span></span>

## <a name="create-a-queue"></a><span data-ttu-id="7c4d0-142">Vytvoření fronty</span><span class="sxs-lookup"><span data-stu-id="7c4d0-142">Create a queue</span></span>

<span data-ttu-id="7c4d0-143">Tento příklad ukazuje, jak vytvořit frontu, pokud ještě neexistuje:</span><span class="sxs-lookup"><span data-stu-id="7c4d0-143">This example shows how to create a queue if it doesn't already exist:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L32-L36)]

## <a name="insert-a-message-into-a-queue"></a><span data-ttu-id="7c4d0-144">Vložit zprávu do fronty</span><span class="sxs-lookup"><span data-stu-id="7c4d0-144">Insert a message into a queue</span></span>

<span data-ttu-id="7c4d0-145">Pokud chcete vložit zprávu do existující fronty, vytvořte nejdříve novou `CloudQueueMessage`.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-145">To insert a message into an existing queue, first create a new `CloudQueueMessage`.</span></span> <span data-ttu-id="7c4d0-146">Pak zavolejte `AddMessage` metoda.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-146">Next, call the `AddMessage` method.</span></span> <span data-ttu-id="7c4d0-147">A `CloudQueueMessage` můžete vytvořit buď z řetězce (ve formátu UTF-8) nebo `byte` pole takto:</span><span class="sxs-lookup"><span data-stu-id="7c4d0-147">A `CloudQueueMessage` can be created from either a string (in UTF-8 format) or a `byte` array, like this:</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L42-L44)]

## <a name="peek-at-the-next-message"></a><span data-ttu-id="7c4d0-148">Zobrazení náhledu další zprávy</span><span class="sxs-lookup"><span data-stu-id="7c4d0-148">Peek at the next message</span></span>

<span data-ttu-id="7c4d0-149">Můžete prohlížet zprávy ve frontě, bez odebere ji z fronty voláním `PeekMessage` metoda.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-149">You can peek at the message in the front of a queue, without removing it from the queue, by calling the `PeekMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L50-L52)]

## <a name="get-the-next-message-for-processing"></a><span data-ttu-id="7c4d0-150">Získat další zprávy pro zpracování</span><span class="sxs-lookup"><span data-stu-id="7c4d0-150">Get the next message for processing</span></span>

<span data-ttu-id="7c4d0-151">Můžete načíst zprávu na popředí fronty pro zpracování voláním `GetMessage` metoda.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-151">You can retrieve the message at the front of a queue for processing by calling the `GetMessage` method.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L58-L59)]

<span data-ttu-id="7c4d0-152">Později označuje úspěšné zpracování zprávy pomocí `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-152">You later indicate successful processing of the message by using `DeleteMessage`.</span></span>

## <a name="change-the-contents-of-a-queued-message"></a><span data-ttu-id="7c4d0-153">Změna obsahu zpráv zařazených ve frontě</span><span class="sxs-lookup"><span data-stu-id="7c4d0-153">Change the contents of a queued message</span></span>

<span data-ttu-id="7c4d0-154">Můžete změnit obsah načtené zprávy přímo ve frontě.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-154">You can change the contents of a retrieved message in-place in the queue.</span></span> <span data-ttu-id="7c4d0-155">Pokud zpráva představuje pracovní úlohu, můžete tuto funkci použít k aktualizaci stavu pracovních úloh.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-155">If the message represents a work task, you could use this feature to update the status of the work task.</span></span> <span data-ttu-id="7c4d0-156">Následující kód aktualizuje zprávy ve frontě o nový obsah a nastaví limit viditelnosti na jiné 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-156">The following code updates the queue message with new contents, and sets the visibility timeout to extend another 60 seconds.</span></span> <span data-ttu-id="7c4d0-157">Uloží stav práce spojený se zprávou a klient získá další minutu, aby pokračovat v práci na zprávě.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-157">This saves the state of work associated with the message, and gives the client another minute to continue working on the message.</span></span> <span data-ttu-id="7c4d0-158">Tímto způsobem může sledovat vícekrokového pracovní postupy pro zprávy ve frontě, aniž by bylo nutné začít znovu od začátku, pokud se nezdaří krok zpracování z důvodu selhání hardwaru nebo softwaru.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-158">You could use this technique to track multi-step workflows on queue messages, without having to start over from the beginning if a processing step fails due to hardware or software failure.</span></span> <span data-ttu-id="7c4d0-159">Obvykle byste udržovali také počet opakování, a pokud zpráva je více než některé počet opakovat, odstranili byste ji.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-159">Typically, you would keep a retry count as well, and if the message is retried more than some number of times, you would delete it.</span></span> <span data-ttu-id="7c4d0-160">Je to ochrana proti zprávu, která nevyvolala chyby aplikace pokaždé, když je zpracován.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-160">This protects against a message that triggers an application error each time it is processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L65-L69)]

## <a name="de-queue-the-next-message"></a><span data-ttu-id="7c4d0-161">Zrušte další zprávy z fronty</span><span class="sxs-lookup"><span data-stu-id="7c4d0-161">De-queue the next message</span></span>

<span data-ttu-id="7c4d0-162">Váš kód vyřazuje z fronty zpráv z fronty ve dvou krocích.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-162">Your code de-queues a message from a queue in two steps.</span></span> <span data-ttu-id="7c4d0-163">Při volání `GetMessage`, získáte další zprávu ve frontě.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-163">When you call `GetMessage`, you get the next message in a queue.</span></span> <span data-ttu-id="7c4d0-164">Zpráva vrácená metodou `GetMessage` stane neviditelnou pro jakýkoli jiný kód čtení zpráv z této fronty.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-164">A message returned from `GetMessage` becomes invisible to any other code reading messages from this queue.</span></span> <span data-ttu-id="7c4d0-165">Ve výchozím nastavení tato zpráva zůstává neviditelná po dobu 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-165">By default, this message stays invisible for 30 seconds.</span></span> <span data-ttu-id="7c4d0-166">K dokončení odebrání zprávy z fronty, musíte také zavolat `DeleteMessage`.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-166">To finish removing the message from the queue, you must also call `DeleteMessage`.</span></span> <span data-ttu-id="7c4d0-167">Tento dvoukrokový proces odebrání zprávy zaručuje, pokud se váš kód se nepodaří zpracovat zprávu z důvodu selhání hardwaru nebo softwaru, jiná instance vašeho kódu můžete stejnou zprávu získat a zkuste to znovu.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-167">This two-step process of removing a message assures that if your code fails to process a message due to hardware or software failure, another instance of your code can get the same message and try again.</span></span> <span data-ttu-id="7c4d0-168">Váš kód zavolá metodu `DeleteMessage` pravým po zpracování zprávy.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-168">Your code calls `DeleteMessage` right after the message has been processed.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L75-L76)]

## <a name="use-async-workflows-with-common-queue-storage-apis"></a><span data-ttu-id="7c4d0-169">Asynchronní pracovní postupy použít s běžnými rozhraním API Queue storage</span><span class="sxs-lookup"><span data-stu-id="7c4d0-169">Use Async workflows with common Queue storage APIs</span></span>

<span data-ttu-id="7c4d0-170">Tento příklad ukazuje způsob použití pracovním postupu asynchronní s běžnými rozhraním API Queue storage.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-170">This example shows how to use an async workflow with common Queue storage APIs.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L82-L91)]

## <a name="additional-options-for-de-queuing-messages"></a><span data-ttu-id="7c4d0-171">Další možností pro vyřazování zpráv z fronty</span><span class="sxs-lookup"><span data-stu-id="7c4d0-171">Additional options for de-queuing messages</span></span>

<span data-ttu-id="7c4d0-172">Existují dva způsoby, jak můžete přizpůsobit načítání zpráv z fronty.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-172">There are two ways you can customize message retrieval from a queue.</span></span>
<span data-ttu-id="7c4d0-173">Nejprve můžete načíst dávku zpráv (až 32).</span><span class="sxs-lookup"><span data-stu-id="7c4d0-173">First, you can get a batch of messages (up to 32).</span></span> <span data-ttu-id="7c4d0-174">Druhý můžete nastavit časový limit neviditelnosti delší nebo kratší, aby měl váš kód více nebo méně času na úplné zpracování jednotlivých zpráv.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-174">Second, you can set a longer or shorter invisibility timeout, allowing your code more or less time to fully process each message.</span></span> <span data-ttu-id="7c4d0-175">Následující příklad kódu používá `GetMessages` získat 20 zpráv v jednom volání a poté je zpracovává každou zprávu.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-175">The following code example uses `GetMessages` to get 20 messages in one call and then processes each message.</span></span> <span data-ttu-id="7c4d0-176">Také nastaví časový limit neviditelnosti 5 minut pro každou zprávu.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-176">It also sets the invisibility timeout to five minutes for each message.</span></span> <span data-ttu-id="7c4d0-177">Všimněte si, že 5 minut začíná pro všechny zprávy ve stejnou dobu, takže po 5 minutách mít předán od volání `GetMessages`, všechny zprávy, které nebyly odstraněny, opět viditelné.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-177">Note that the 5 minutes starts for all messages at the same time, so after 5 minutes have passed since the call to `GetMessages`, any messages which have not been deleted will become visible again.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L97-L99)]

## <a name="get-the-queue-length"></a><span data-ttu-id="7c4d0-178">Získání délky fronty</span><span class="sxs-lookup"><span data-stu-id="7c4d0-178">Get the queue length</span></span>

<span data-ttu-id="7c4d0-179">Můžete získat odhadovaný počet zpráv ve frontě.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-179">You can get an estimate of the number of messages in a queue.</span></span> <span data-ttu-id="7c4d0-180">`FetchAttributes` Metoda požádá službu front o načtení atributů fronty, včetně počtu zpráv.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-180">The `FetchAttributes` method asks the Queue service to retrieve the queue attributes, including the message count.</span></span> <span data-ttu-id="7c4d0-181">`ApproximateMessageCount` Vlastnost vrací poslední hodnotu načtenou `FetchAttributes` metoda bez volání služby front.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-181">The `ApproximateMessageCount` property returns the last value retrieved by the `FetchAttributes` method, without calling the Queue service.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L105-L106)]

## <a name="delete-a-queue"></a><span data-ttu-id="7c4d0-182">Odstranění fronty</span><span class="sxs-lookup"><span data-stu-id="7c4d0-182">Delete a queue</span></span>

<span data-ttu-id="7c4d0-183">Chcete-li odstranit frontu se všemi zprávami, které v ní, zavolejte `Delete` metoda pro objekt fronty.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-183">To delete a queue and all the messages contained in it, call the `Delete` method on the queue object.</span></span>

[!code-fsharp[QueueStorage](../../../samples/snippets/fsharp/azure/queue-storage.fsx#L112-L113)]

## <a name="next-steps"></a><span data-ttu-id="7c4d0-184">Další kroky</span><span class="sxs-lookup"><span data-stu-id="7c4d0-184">Next steps</span></span>

<span data-ttu-id="7c4d0-185">Teď, když jste se naučili základy používání služby Queue storage, postupujte podle následujících odkazech na další informace o složitějších úlohách úložiště.</span><span class="sxs-lookup"><span data-stu-id="7c4d0-185">Now that you've learned the basics of Queue storage, follow these links to learn about more complex storage tasks.</span></span>

- [<span data-ttu-id="7c4d0-186">Rozhraní API úložiště Azure pro .NET</span><span class="sxs-lookup"><span data-stu-id="7c4d0-186">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="7c4d0-187">Typ zprostředkovatele úložiště Azure</span><span class="sxs-lookup"><span data-stu-id="7c4d0-187">Azure Storage Type Provider</span></span>](https://github.com/fsprojects/AzureStorageTypeProvider)
- [<span data-ttu-id="7c4d0-188">Blog týmu Azure Storage</span><span class="sxs-lookup"><span data-stu-id="7c4d0-188">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="7c4d0-189">Konfigurace připojovacích řetězců Azure Storage</span><span class="sxs-lookup"><span data-stu-id="7c4d0-189">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="7c4d0-190">Referenční dokumentace rozhraní API REST služby Azure Storage</span><span class="sxs-lookup"><span data-stu-id="7c4d0-190">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)
