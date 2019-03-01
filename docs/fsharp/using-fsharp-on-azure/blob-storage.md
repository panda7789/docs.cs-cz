---
title: Začínáme s využitím úložiště objektů Blob v AzureF#
description: Store nestrukturovaných dat v cloudu s využitím úložiště objektů Blob v Azure.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: e38f58fefa63f922bcb1a78254249a3626bfac43
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981904"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="473e1-103">Začínáme s Azure Blob storage s využitím F\#</span><span class="sxs-lookup"><span data-stu-id="473e1-103">Get started with Azure Blob storage using F\#</span></span>

<span data-ttu-id="473e1-104">Azure Blob storage je služba, která ukládá Nestrukturovaná data v cloudu jako objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="473e1-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="473e1-105">BLOB storage dokáže ukládat jakýkoli druh textu nebo binárních dat, jako je například dokument, soubor médií nebo instalační program aplikace.</span><span class="sxs-lookup"><span data-stu-id="473e1-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="473e1-106">Úložiště objektů blob se taky označuje jako úložiště objektů.</span><span class="sxs-lookup"><span data-stu-id="473e1-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="473e1-107">V tomto článku se dozvíte, jak provádět běžné úlohy pomocí úložiště objektů Blob.</span><span class="sxs-lookup"><span data-stu-id="473e1-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="473e1-108">Ukázky jsou napsané s využitím F# pomocí klientské knihovny Azure Storage pro .NET.</span><span class="sxs-lookup"><span data-stu-id="473e1-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="473e1-109">Popsané úkoly popsané v nahrání, výpisu, stahování a odstraňování objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="473e1-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="473e1-110">Koncepční přehled služby blob storage, najdete v části [v příručce .NET pro úložiště objektů blob](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="473e1-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="473e1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="473e1-111">Prerequisites</span></span>

<span data-ttu-id="473e1-112">K použití tohoto průvodce, musíte nejdřív [vytvoření účtu služby Azure storage](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="473e1-112">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="473e1-113">Pro tento účet také potřebovat přístupový klíč k úložišti.</span><span class="sxs-lookup"><span data-stu-id="473e1-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="473e1-114">Vytvoření F# skript a spustit F# interaktivní</span><span class="sxs-lookup"><span data-stu-id="473e1-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="473e1-115">Ukázky v tomto článku můžete použít buď F# aplikace nebo F# skriptu.</span><span class="sxs-lookup"><span data-stu-id="473e1-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="473e1-116">Vytvoření F# skript, vytvořte soubor s `.fsx` příponu, třeba `blobs.fsx`v vaše F# vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="473e1-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="473e1-117">Dále používat [Správce balíčků](package-management.md) například [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` a `Microsoft.WindowsAzure.ConfigurationManager` balíčky a reference `WindowsAzure.Storage.dll` a `Microsoft.WindowsAzure.Configuration.dll` v pomocí skriptu `#r` směrnice.</span><span class="sxs-lookup"><span data-stu-id="473e1-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="473e1-118">Přidání deklarací oboru názvů</span><span class="sxs-lookup"><span data-stu-id="473e1-118">Add namespace declarations</span></span>

<span data-ttu-id="473e1-119">Přidejte následující `open` příkazy k hornímu okraji `blobs.fsx` souboru:</span><span class="sxs-lookup"><span data-stu-id="473e1-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="473e1-120">Získání připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="473e1-120">Get your connection string</span></span>

<span data-ttu-id="473e1-121">Pro účely tohoto kurzu potřebujete připojovací řetězec služby Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="473e1-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="473e1-122">Další informace o připojovacích řetězcích najdete v tématu [nakonfigurovat připojovací řetězce úložiště](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="473e1-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="473e1-123">Pro tento kurz můžete zadat připojovací řetězec ve vašem skriptu, například takto:</span><span class="sxs-lookup"><span data-stu-id="473e1-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="473e1-124">Je to ale **ale nedoporučený krok** skutečných projekty.</span><span class="sxs-lookup"><span data-stu-id="473e1-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="473e1-125">Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="473e1-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="473e1-126">Vždy klíč účtu úložiště pečlivě chraňte.</span><span class="sxs-lookup"><span data-stu-id="473e1-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="473e1-127">Nedávejte ho jiným uživatelům, nezakódovávejte ho ani ho neukládejte do souboru ve formátu prostého textu, který je přístupný ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="473e1-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="473e1-128">Můžete znovu vygenerovat klíč pomocí webu Azure Portal, pokud se domníváte, že je možná ohrožené.</span><span class="sxs-lookup"><span data-stu-id="473e1-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="473e1-129">Pro skutečné aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="473e1-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="473e1-130">K načtení připojovacího řetězce z konfiguračního souboru, můžete udělat toto:</span><span class="sxs-lookup"><span data-stu-id="473e1-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="473e1-131">Použití nástroje Azure Configuration Manager není povinné.</span><span class="sxs-lookup"><span data-stu-id="473e1-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="473e1-132">Můžete také použít rozhraní API, jako je například rozhraní .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="473e1-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="473e1-133">Analýza připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="473e1-133">Parse the connection string</span></span>

<span data-ttu-id="473e1-134">K analýze připojovacího řetězce, použijte:</span><span class="sxs-lookup"><span data-stu-id="473e1-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="473e1-135">Tím se vrátí `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="473e1-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="473e1-136">Vytvořit místní fiktivní data</span><span class="sxs-lookup"><span data-stu-id="473e1-136">Create some local dummy data</span></span>

<span data-ttu-id="473e1-137">Než začnete, vytvořte nějaká fiktivní místní data v adresáři skriptu.</span><span class="sxs-lookup"><span data-stu-id="473e1-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="473e1-138">Později můžete tato data nahrát.</span><span class="sxs-lookup"><span data-stu-id="473e1-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="473e1-139">Vytvoření klienta služby Blob service</span><span class="sxs-lookup"><span data-stu-id="473e1-139">Create the Blob service client</span></span>

<span data-ttu-id="473e1-140">`CloudBlobClient` Typ umožňuje načíst kontejnery a objekty BLOB uložené v úložišti objektů Blob.</span><span class="sxs-lookup"><span data-stu-id="473e1-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="473e1-141">Tady je jeden způsob, jak vytvořit klienta služby:</span><span class="sxs-lookup"><span data-stu-id="473e1-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="473e1-142">Nyní jste připraveni napsat kód, který čte data z a zapisuje data do úložiště objektů Blob.</span><span class="sxs-lookup"><span data-stu-id="473e1-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="473e1-143">Vytvoření kontejneru</span><span class="sxs-lookup"><span data-stu-id="473e1-143">Create a container</span></span>

<span data-ttu-id="473e1-144">Tento příklad ukazuje, jak vytvořit kontejner, pokud ještě neexistuje:</span><span class="sxs-lookup"><span data-stu-id="473e1-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="473e1-145">Ve výchozím nastavení je nový kontejner privátní, což znamená, že je nutné zadat přístupový klíč úložiště pro objekty BLOB můžete stáhnout z tohoto kontejneru.</span><span class="sxs-lookup"><span data-stu-id="473e1-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="473e1-146">Pokud chcete zpřístupnit soubory v kontejneru pro všechny uživatele, můžete nastavit kontejner, aby se veřejné, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="473e1-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="473e1-147">Kdokoli na Internetu může vidět objekty BLOB ve veřejném kontejneru, ale můžete upravit nebo odstranit jenom v případě, že máte příslušný přístup klíč k účtu nebo sdílený přístupový podpis.</span><span class="sxs-lookup"><span data-stu-id="473e1-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="473e1-148">Nahrání objektu blob do kontejneru</span><span class="sxs-lookup"><span data-stu-id="473e1-148">Upload a blob into a container</span></span>

<span data-ttu-id="473e1-149">Azure Blob Storage podporuje objekty BLOB bloku a objekty BLOB stránky.</span><span class="sxs-lookup"><span data-stu-id="473e1-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="473e1-150">Ve většině případů je objekt blob bloku typ k použití doporučuje.</span><span class="sxs-lookup"><span data-stu-id="473e1-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="473e1-151">Chcete-li nahrát soubor do objektu blob bloku, získejte odkaz na kontejner a použijte ho k získání odkazu objektu blob bloku.</span><span class="sxs-lookup"><span data-stu-id="473e1-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="473e1-152">Jakmile budete mít odkaz na objekt blob, můžete nahrát jakýkoli proud dat k němu voláním `UploadFromFile` metody.</span><span class="sxs-lookup"><span data-stu-id="473e1-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="473e1-153">Tato operace vytvoří objekt blob, pokud nebyla dříve neexistuje, nebo ho přepíše, pokud už existoval.</span><span class="sxs-lookup"><span data-stu-id="473e1-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="473e1-154">Výpis objektů BLOB v kontejneru</span><span class="sxs-lookup"><span data-stu-id="473e1-154">List the blobs in a container</span></span>

<span data-ttu-id="473e1-155">Seznam objektů BLOB v kontejneru, nejdřív získejte odkaz na kontejner.</span><span class="sxs-lookup"><span data-stu-id="473e1-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="473e1-156">Pak můžete použít kontejneru `ListBlobs` metodu pro načtení objektů BLOB a/nebo obsažené adresáře.</span><span class="sxs-lookup"><span data-stu-id="473e1-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="473e1-157">Pro přístup k bohaté sadě vlastností a metod vrácené `IListBlobItem`, musíte vysílat na `CloudBlockBlob`, `CloudPageBlob`, nebo `CloudBlobDirectory` objektu.</span><span class="sxs-lookup"><span data-stu-id="473e1-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="473e1-158">Pokud je typ neznámý, můžete určit, který typ vysílat kontrolu typu.</span><span class="sxs-lookup"><span data-stu-id="473e1-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="473e1-159">Následující kód ukazuje, jak načíst a výstup URI pro každou položku v `mydata` kontejneru:</span><span class="sxs-lookup"><span data-stu-id="473e1-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="473e1-160">Můžete také název objektů BLOB pomocí informací o cestě v jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="473e1-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="473e1-161">Tím se vytvoří struktura virtuálního adresáře, kterou můžete organizovat a procházet podle potřeby jako u tradičních systémů souborů.</span><span class="sxs-lookup"><span data-stu-id="473e1-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="473e1-162">Všimněte si, že struktura adresářů je jenom virtuální - jediné prostředky, které jsou k dispozici v úložišti objektů Blob, jsou kontejnery a objekty BLOB.</span><span class="sxs-lookup"><span data-stu-id="473e1-162">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="473e1-163">Však nabízí klientskou knihovnu pro úložiště `CloudBlobDirectory` objektu, který chcete odkazovat na virtuální adresář a zjednodušit tak práci s objekty BLOB, které jsou tímto způsobem uspořádány.</span><span class="sxs-lookup"><span data-stu-id="473e1-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="473e1-164">Zvažte například následující sadu objektů BLOB bloku v kontejneru nazvaném `photos`:</span><span class="sxs-lookup"><span data-stu-id="473e1-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="473e1-165">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="473e1-165">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span></span>

<span data-ttu-id="473e1-166">Při volání `ListBlobs` kontejneru (viz ukázka výše) se vrátí hierarchický výpis.</span><span class="sxs-lookup"><span data-stu-id="473e1-166">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="473e1-167">Pokud obsahuje `CloudBlobDirectory` a `CloudBlockBlob` objekty, které představují adresáře a objekty BLOB v kontejneru, v uvedeném pořadí, pak výsledný výstup by měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="473e1-167">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="473e1-168">Volitelně můžete nastavit `UseFlatBlobListing` parametr `ListBlobs` metodu `true`.</span><span class="sxs-lookup"><span data-stu-id="473e1-168">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="473e1-169">V takovém případě je každý objekt blob v kontejneru vrácen jako `CloudBlockBlob` objektu.</span><span class="sxs-lookup"><span data-stu-id="473e1-169">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="473e1-170">Volání `ListBlobs` vrátit plochým výpisem vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="473e1-170">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="473e1-171">a v závislosti na aktuální obsah vašeho kontejneru, výsledek vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="473e1-171">and, depending on the current contents of your container, the results look like this:</span></span>

```console
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2015/architecture/description.txt
Block blob of length 314618: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo3.jpg
Block blob of length 522713: https://<accountname>.blob.core.windows.net/photos/2015/architecture/photo4.jpg
Block blob of length 4: https://<accountname>.blob.core.windows.net/photos/2016/architecture/description.txt
Block blob of length 419048: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo5.jpg
Block blob of length 506388: https://<accountname>.blob.core.windows.net/photos/2016/architecture/photo6.jpg
Block blob of length 399751: https://<accountname>.blob.core.windows.net/photos/2016/photo7.jpg
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

## <a name="download-blobs"></a><span data-ttu-id="473e1-172">Stažení objektů BLOB</span><span class="sxs-lookup"><span data-stu-id="473e1-172">Download blobs</span></span>

<span data-ttu-id="473e1-173">Pokud chcete stáhnout objekty BLOB, nejdřív načtěte odkaz objektu blob a pak zavolat `DownloadToStream` metody.</span><span class="sxs-lookup"><span data-stu-id="473e1-173">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="473e1-174">V následujícím příkladu `DownloadToStream` způsob přenosu obsahu objektu blob na objekt datového proudu, který je pak možné zachovat do místního souboru.</span><span class="sxs-lookup"><span data-stu-id="473e1-174">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="473e1-175">Můžete také použít `DownloadToStream` metody ke stahování obsahu objektu blob jako textový řetězec.</span><span class="sxs-lookup"><span data-stu-id="473e1-175">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="473e1-176">Odstranění objektů BLOB</span><span class="sxs-lookup"><span data-stu-id="473e1-176">Delete blobs</span></span>

<span data-ttu-id="473e1-177">Chcete-li odstranit objekt blob, nejdřív získejte odkaz na objekt blob a poté zavolejte `Delete` metoda na něm.</span><span class="sxs-lookup"><span data-stu-id="473e1-177">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="473e1-178">Seznam objektů blob na stránkách asynchronně</span><span class="sxs-lookup"><span data-stu-id="473e1-178">List blobs in pages asynchronously</span></span>

<span data-ttu-id="473e1-179">Pokud jsou výpis velkého počtu objektů BLOB nebo chcete řídit počet výsledků, které vrátíte v rámci jedné operace výpisu, můžete vytvořit seznam objektů blob na stránkách s výsledky.</span><span class="sxs-lookup"><span data-stu-id="473e1-179">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="473e1-180">Tento příklad ukazuje, jak vracet výsledky na stránkách asynchronně, takže provádění není blokována během čekání na vrácení velké sady výsledků.</span><span class="sxs-lookup"><span data-stu-id="473e1-180">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="473e1-181">Tento příklad ukazuje plochý výpis objektu blob, ale můžete také provést hierarchický výpis nastavením `useFlatBlobListing` parametr `ListBlobsSegmentedAsync` metodu `false`.</span><span class="sxs-lookup"><span data-stu-id="473e1-181">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="473e1-182">Ukázka definuje metodu, pomocí `async` bloku.</span><span class="sxs-lookup"><span data-stu-id="473e1-182">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="473e1-183">``let!`` – Klíčové slovo pozastaví spuštění metody ukázky až do dokončení úlohy vytváření seznamu.</span><span class="sxs-lookup"><span data-stu-id="473e1-183">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="473e1-184">Tato rutina asynchronní jsme teď můžete použít následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="473e1-184">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="473e1-185">Nejprve nahrát fiktivní data (s použitím místní soubor vytvořený dříve v tomto kurzu).</span><span class="sxs-lookup"><span data-stu-id="473e1-185">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="473e1-186">Nyní volání rutiny.</span><span class="sxs-lookup"><span data-stu-id="473e1-186">Now, call the routine.</span></span> <span data-ttu-id="473e1-187">Použijete `Async.RunSynchronously` k vynucení provedení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="473e1-187">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="473e1-188">Zápis do doplňovacího objektu BLOB</span><span class="sxs-lookup"><span data-stu-id="473e1-188">Writing to an append blob</span></span>

<span data-ttu-id="473e1-189">Doplňovací objekt blob je optimalizován pro operace připojení, jako je například protokolování.</span><span class="sxs-lookup"><span data-stu-id="473e1-189">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="473e1-190">Podobně jako objekt blob bloku doplňovací objekt blob se skládá z bloků, ale při přidání nového bloku pro doplňovací objekt blob se vždy připojí na konec objektu blob.</span><span class="sxs-lookup"><span data-stu-id="473e1-190">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="473e1-191">Nelze aktualizovat nebo odstranit existující blok v doplňovacím objektu blob.</span><span class="sxs-lookup"><span data-stu-id="473e1-191">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="473e1-192">ID bloku pro doplňovací objekt blob nejsou vystavená, protože jsou pro objekt blob bloku.</span><span class="sxs-lookup"><span data-stu-id="473e1-192">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="473e1-193">Každý blok v doplňovacím objektu blob může mít různou velikost až 4 MB, a doplňovací objekt blob může obsahovat maximálně 50 000 bloků.</span><span class="sxs-lookup"><span data-stu-id="473e1-193">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="473e1-194">Maximální velikost doplňovacího objektu blob je proto o něco větší než 195 GB (4 MB × 50 000 bloků).</span><span class="sxs-lookup"><span data-stu-id="473e1-194">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="473e1-195">Následující příklad vytvoří nový doplňovací objekt blob a připojí některá data, simulaci jednoduché operace protokolování.</span><span class="sxs-lookup"><span data-stu-id="473e1-195">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="473e1-196">Zobrazit [vysvětlení objektů BLOB bloku, objekty BLOB stránky a doplňovací objekty BLOB](https://msdn.microsoft.com/library/azure/ee691964.aspx) Další informace o rozdílech mezi třemi typy objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="473e1-196">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="473e1-197">Souběžný přístup</span><span class="sxs-lookup"><span data-stu-id="473e1-197">Concurrent access</span></span>

<span data-ttu-id="473e1-198">Pro podporu souběžný přístup z více klientům nebo více instancí procesu do objektu blob, můžete použít **značek etag** nebo **zapůjčení**.</span><span class="sxs-lookup"><span data-stu-id="473e1-198">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="473e1-199">**Značka Etag** – poskytuje způsob, jak zjistit, že objekt blob nebo kontejner byl změněn jiným procesem</span><span class="sxs-lookup"><span data-stu-id="473e1-199">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="473e1-200">**Zapůjčení** – poskytuje způsob, jak získat exkluzivní, obnovitelné, zapsat nebo odstranit pro určitou dobu přístup k objektu blob</span><span class="sxs-lookup"><span data-stu-id="473e1-200">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="473e1-201">Další informace najdete v tématu [Správa souběžnosti v Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="473e1-201">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="473e1-202">Pojmenování kontejnerů</span><span class="sxs-lookup"><span data-stu-id="473e1-202">Naming containers</span></span>

<span data-ttu-id="473e1-203">Každý objekt blob ve službě Azure storage se musí nacházet v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="473e1-203">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="473e1-204">Kontejner je součástí názvu objektu blob.</span><span class="sxs-lookup"><span data-stu-id="473e1-204">The container forms part of the blob name.</span></span> <span data-ttu-id="473e1-205">Například `mydata` je název kontejneru v těchto ukázkových objektů blob identifikátorů URI:</span><span class="sxs-lookup"><span data-stu-id="473e1-205">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="473e1-206">Název kontejneru musí být platný název DNS, který odpovídá následujícím pravidlům pro pojmenování:</span><span class="sxs-lookup"><span data-stu-id="473e1-206">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="473e1-207">Názvy kontejnerů musí začínat písmenem nebo číslicí a může obsahovat jenom písmena, číslice a znak spojovníku (-).</span><span class="sxs-lookup"><span data-stu-id="473e1-207">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="473e1-208">Každému znaku pomlčky (-) musí být bezprostředně před a následované písmenem nebo číslicí; po sobě jdoucí pomlčky nejsou povolené v názvu kontejneru.</span><span class="sxs-lookup"><span data-stu-id="473e1-208">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="473e1-209">Všechna písmena v názvu kontejneru musí obsahovat malá písmena.</span><span class="sxs-lookup"><span data-stu-id="473e1-209">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="473e1-210">Názvy kontejnerů musí mít délku 3 až 63 znaků.</span><span class="sxs-lookup"><span data-stu-id="473e1-210">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="473e1-211">Všimněte si, že název kontejneru musí vždy obsahovat malá písmena.</span><span class="sxs-lookup"><span data-stu-id="473e1-211">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="473e1-212">Pokud zahrnují písmena velká písmena v názvu kontejneru nebo jinak porušíte pravidla po pojmenování kontejnerů, může se zobrazit chyba 400 (Chybný požadavek).</span><span class="sxs-lookup"><span data-stu-id="473e1-212">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="473e1-213">Správa zabezpečení pro objekty BLOB</span><span class="sxs-lookup"><span data-stu-id="473e1-213">Managing security for blobs</span></span>

<span data-ttu-id="473e1-214">Ve výchozím nastavení služby Azure Storage zachovává zabezpečení dat omezením přístupu k majiteli účtu, který je ve vlastnictví přístupové klíče účtu.</span><span class="sxs-lookup"><span data-stu-id="473e1-214">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="473e1-215">Když budete potřebovat ke sdílení dat objektů blob v účtu úložiště, je potřeba udělat bez narušení zabezpečení přístupové klíče vašeho účtu.</span><span class="sxs-lookup"><span data-stu-id="473e1-215">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="473e1-216">Navíc můžete šifrovat data objektů blob abychom měli jistotu, že se jedná o zabezpečený přenos přenosu i ve službě Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="473e1-216">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="473e1-217">Řízení přístupu k datům objektu blob</span><span class="sxs-lookup"><span data-stu-id="473e1-217">Controlling access to blob data</span></span>

<span data-ttu-id="473e1-218">Ve výchozím nastavení je přístupný pouze vlastník účtu úložiště dat objektů blob v účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="473e1-218">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="473e1-219">Ve výchozím nastavení ověřování požadavků na úložiště objektů Blob vyžaduje přístupový klíč účtu.</span><span class="sxs-lookup"><span data-stu-id="473e1-219">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="473e1-220">Můžete však chtít určitá data objektu blob zpřístupnit ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="473e1-220">However, you might want to make certain blob data available to other users.</span></span>

### <a name="encrypting-blob-data"></a><span data-ttu-id="473e1-221">Šifrování dat objektů blob</span><span class="sxs-lookup"><span data-stu-id="473e1-221">Encrypting blob data</span></span>

<span data-ttu-id="473e1-222">Azure Storage podporuje šifrování dat objektů blob na straně klienta i na serveru.</span><span class="sxs-lookup"><span data-stu-id="473e1-222">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

## <a name="next-steps"></a><span data-ttu-id="473e1-223">Další kroky</span><span class="sxs-lookup"><span data-stu-id="473e1-223">Next steps</span></span>

<span data-ttu-id="473e1-224">Teď, když jste se naučili základy používání Blob storage, použijte tyto odkazy na další informace.</span><span class="sxs-lookup"><span data-stu-id="473e1-224">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="473e1-225">Nástroje</span><span class="sxs-lookup"><span data-stu-id="473e1-225">Tools</span></span>

- <span data-ttu-id="473e1-226">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\\</span><span class="sxs-lookup"><span data-stu-id="473e1-226">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)\\</span></span>
<span data-ttu-id="473e1-227">F# Typu poskytovatele, který slouží k prozkoumání objektů Blob, tabulky a fronty Azure Storage prostředky a snadno použít operace CRUD s nimi.</span><span class="sxs-lookup"><span data-stu-id="473e1-227">An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>

- <span data-ttu-id="473e1-228">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\\</span><span class="sxs-lookup"><span data-stu-id="473e1-228">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)\\</span></span>
<span data-ttu-id="473e1-229">F# Rozhraní API za používání služby Microsoft Azure Table Storage</span><span class="sxs-lookup"><span data-stu-id="473e1-229">An F# API for using Microsoft Azure Table Storage service</span></span>

- <span data-ttu-id="473e1-230">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\\</span><span class="sxs-lookup"><span data-stu-id="473e1-230">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)\\</span></span>
<span data-ttu-id="473e1-231">Bezplatná samostatná aplikace od Microsoftu, která umožňuje vizuálně pracovat s daty Azure Storage ve Windows, OS X a Linux.</span><span class="sxs-lookup"><span data-stu-id="473e1-231">A free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="473e1-232">Odkaz na objekt BLOB úložiště</span><span class="sxs-lookup"><span data-stu-id="473e1-232">Blob storage reference</span></span>

- [<span data-ttu-id="473e1-233">Rozhraní API služby Azure Storage pro .NET</span><span class="sxs-lookup"><span data-stu-id="473e1-233">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="473e1-234">Reference k rozhraní REST API služby Azure Storage</span><span class="sxs-lookup"><span data-stu-id="473e1-234">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="473e1-235">Související vodítka</span><span class="sxs-lookup"><span data-stu-id="473e1-235">Related guides</span></span>

- [<span data-ttu-id="473e1-236">Začínáme se službou Azure Blob Storage v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="473e1-236">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="473e1-237">Přenos dat pomocí nástroje příkazového řádku azcopy ve Windows</span><span class="sxs-lookup"><span data-stu-id="473e1-237">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="473e1-238">Přenos dat pomocí nástroje příkazového řádku azcopy v Linuxu</span><span class="sxs-lookup"><span data-stu-id="473e1-238">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="473e1-239">Nakonfigurování připojovacích řetězců Azure Storage</span><span class="sxs-lookup"><span data-stu-id="473e1-239">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="473e1-240">Blog týmu Azure Storage</span><span class="sxs-lookup"><span data-stu-id="473e1-240">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
- [<span data-ttu-id="473e1-241">Rychlý start: Vytvoření objektu blob v úložišti objektů pomocí .NET</span><span class="sxs-lookup"><span data-stu-id="473e1-241">Quickstart: Use .NET to create a blob in object storage</span></span>](/azure/storage/blobs/storage-quickstart-blobs-dotnet)