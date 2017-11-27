---
title: "Začínáme s Azure Blob storage pomocí F #"
description: "Ukládání nestrukturovaných dat v cloudu s Azure Blob storage."
keywords: "Visual f #, f #, funkční programování, .NET, .NET Core, Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c5b74a4f-dcd1-4849-930c-904b6c8a04e1
ms.openlocfilehash: 92e26aff605d3bed89e388dd3616a2a9a3a96081
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="f257c-104">Začínáme s Azure Blob storage pomocí F #</span><span class="sxs-lookup"><span data-stu-id="f257c-104">Get started with Azure Blob storage using F#</span></span> #

<span data-ttu-id="f257c-105">Azure Blob storage je služba, která ukládá Nestrukturovaná data v cloudu jako objekty nebo objekty BLOB.</span><span class="sxs-lookup"><span data-stu-id="f257c-105">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="f257c-106">Úložiště objektů BLOB můžete ukládat jakýkoli typ textu nebo binárních dat, jako je například dokument, soubor média nebo instalační program aplikace.</span><span class="sxs-lookup"><span data-stu-id="f257c-106">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="f257c-107">Úložiště objektů blob se také označuje jako úložiště objektů.</span><span class="sxs-lookup"><span data-stu-id="f257c-107">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="f257c-108">Tento článek ukazuje, jak provádět běžné úlohy pomocí úložiště objektů Blob.</span><span class="sxs-lookup"><span data-stu-id="f257c-108">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="f257c-109">Ukázky jsou napsané v F # pomocí klientské knihovny pro úložiště Azure pro .NET.</span><span class="sxs-lookup"><span data-stu-id="f257c-109">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="f257c-110">Úlohy popsané zahrnovat nahrát, seznam, stažení a odstranění objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="f257c-110">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="f257c-111">Koncepční přehled úložiště objektů blob, najdete v tématu [v příručce .NET pro úložiště objektů blob](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="f257c-111">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f257c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f257c-112">Prerequisites</span></span>

<span data-ttu-id="f257c-113">Chcete-li tohoto průvodce použijte, je nutné nejprve [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="f257c-113">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="f257c-114">Pro tento účet je také nutné přístupový klíč k úložišti.</span><span class="sxs-lookup"><span data-stu-id="f257c-114">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="f257c-115">Vytvoření F # skript a spusťte F # interaktivní</span><span class="sxs-lookup"><span data-stu-id="f257c-115">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="f257c-116">Ukázky v tomto článku slouží v aplikaci F # nebo skriptu F #.</span><span class="sxs-lookup"><span data-stu-id="f257c-116">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="f257c-117">Chcete-li vytvořit skript F #, vytvořte soubor s `.fsx` příponu, třeba `blobs.fsx`, ve vašem vývojovém prostředí F #.</span><span class="sxs-lookup"><span data-stu-id="f257c-117">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="f257c-118">Pak pomocí [Správce balíčků](package-management.md) například [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` a `Microsoft.WindowsAzure.ConfigurationManager` balíčky a reference `WindowsAzure.Storage.dll` a `Microsoft.WindowsAzure.Configuration.dll` v pomocí skriptu `#r` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="f257c-118">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="f257c-119">Přidání deklarace oborů názvů</span><span class="sxs-lookup"><span data-stu-id="f257c-119">Add namespace declarations</span></span>

<span data-ttu-id="f257c-120">Přidejte následující `open` příkazů do horní části `blobs.fsx` souboru:</span><span class="sxs-lookup"><span data-stu-id="f257c-120">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="f257c-121">Získat připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="f257c-121">Get your connection string</span></span>

<span data-ttu-id="f257c-122">Pro účely tohoto kurzu potřebujete připojovací řetězec službě Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="f257c-122">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="f257c-123">Další informace o připojovacích řetězcích najdete v tématu [nakonfigurování připojovacích řetězců Storage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="f257c-123">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="f257c-124">Pro tento kurz zadejte připojovací řetězec ve vašem skriptu, například takto:</span><span class="sxs-lookup"><span data-stu-id="f257c-124">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="f257c-125">Je to ale **nedoporučuje** skutečných projekty.</span><span class="sxs-lookup"><span data-stu-id="f257c-125">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="f257c-126">Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="f257c-126">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="f257c-127">Vždycky pečlivě k ochraně klíče účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="f257c-127">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="f257c-128">Nedávejte ho jiným uživatelům, nezakódovávejte ho nebo ho uložit v souboru formátu prostého textu, který je přístupný ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="f257c-128">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="f257c-129">Můžete znovu vygenerovat klíč pomocí portálu Azure, pokud se domníváte, že by může ohrožení.</span><span class="sxs-lookup"><span data-stu-id="f257c-129">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="f257c-130">Skutečných aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="f257c-130">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="f257c-131">K načtení připojovacího řetězce z konfiguračního souboru, můžete to udělat:</span><span class="sxs-lookup"><span data-stu-id="f257c-131">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="f257c-132">Použití nástroje Azure Configuration Manager není povinné.</span><span class="sxs-lookup"><span data-stu-id="f257c-132">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="f257c-133">Můžete také použít API jako třeba rozhraní .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="f257c-133">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="f257c-134">Analýza připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="f257c-134">Parse the connection string</span></span>

<span data-ttu-id="f257c-135">Chcete-li analyzovat připojovací řetězec, použijte:</span><span class="sxs-lookup"><span data-stu-id="f257c-135">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="f257c-136">Tento příkaz vrátí `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="f257c-136">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="f257c-137">Vytvořit některé místní fiktivní data</span><span class="sxs-lookup"><span data-stu-id="f257c-137">Create some local dummy data</span></span>

<span data-ttu-id="f257c-138">Než začnete, vytvořte některé fiktivní místní data v adresáři naše skriptu.</span><span class="sxs-lookup"><span data-stu-id="f257c-138">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="f257c-139">Později nahrajete tato data.</span><span class="sxs-lookup"><span data-stu-id="f257c-139">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="f257c-140">Vytvoření klienta služby objektů Blob</span><span class="sxs-lookup"><span data-stu-id="f257c-140">Create the Blob service client</span></span>

<span data-ttu-id="f257c-141">`CloudBlobClient` Typ umožňuje načíst kontejnery a objekty BLOB uložené v úložišti objektů Blob.</span><span class="sxs-lookup"><span data-stu-id="f257c-141">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="f257c-142">Tady je jeden způsob, jak vytvořit klienta služby:</span><span class="sxs-lookup"><span data-stu-id="f257c-142">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="f257c-143">Teď jste připravení psát kód, který načítá a zapisuje data do úložiště objektů Blob.</span><span class="sxs-lookup"><span data-stu-id="f257c-143">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="f257c-144">Vytvoření kontejneru</span><span class="sxs-lookup"><span data-stu-id="f257c-144">Create a container</span></span>

<span data-ttu-id="f257c-145">Tento příklad ukazuje, jak vytvořit kontejner, pokud ještě neexistuje:</span><span class="sxs-lookup"><span data-stu-id="f257c-145">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="f257c-146">Ve výchozím nastavení je nový kontejner privátní, což znamená, že musíte zadat přístupový klíč k úložišti ke stažení z tohoto kontejneru objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="f257c-146">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="f257c-147">Pokud chcete, aby soubory v kontejneru dostupné pro všechny uživatele, můžete nastavit kontejner, aby se veřejné, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="f257c-147">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="f257c-148">Kdokoli na Internetu může vidět objekty BLOB ve veřejném kontejneru, ale můžete upravit nebo odstranit pouze v případě, že máte přístupový klíč odpovídající účtu nebo sdílený přístupový podpis.</span><span class="sxs-lookup"><span data-stu-id="f257c-148">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="f257c-149">Nahrát objekt blob do kontejneru</span><span class="sxs-lookup"><span data-stu-id="f257c-149">Upload a blob into a container</span></span>

<span data-ttu-id="f257c-150">Úložiště objektů Blob Azure podporuje objekty BLOB bloku a objekty BLOB stránky.</span><span class="sxs-lookup"><span data-stu-id="f257c-150">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="f257c-151">Ve většině případů je objekt blob bloku typ k použití doporučuje.</span><span class="sxs-lookup"><span data-stu-id="f257c-151">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="f257c-152">Chcete-li nahrát soubor do objektu blob bloku, získejte odkaz na kontejner a umožňuje vám získat odkaz na objekt blob bloku.</span><span class="sxs-lookup"><span data-stu-id="f257c-152">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="f257c-153">Až budete mít odkaz na objekt blob, můžete nahrát jakýkoli proud dat k němu voláním `UploadFromFile` metoda.</span><span class="sxs-lookup"><span data-stu-id="f257c-153">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="f257c-154">Tato operace vytvoří objekt blob, pokud nebyla dříve neexistuje, nebo ho přepíše, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="f257c-154">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="f257c-155">Seznam objektů BLOB v kontejneru</span><span class="sxs-lookup"><span data-stu-id="f257c-155">List the blobs in a container</span></span>

<span data-ttu-id="f257c-156">Pro zobrazení seznamu objektů BLOB v kontejneru, nejdřív získejte odkaz na kontejner.</span><span class="sxs-lookup"><span data-stu-id="f257c-156">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="f257c-157">Pak můžete použít kontejneru `ListBlobs` metoda pro načtení objektů BLOB a/nebo obsažené adresáře.</span><span class="sxs-lookup"><span data-stu-id="f257c-157">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="f257c-158">Pro přístup k bohaté sadě vlastností a metod vrácené `IListBlobItem`, musíte vysílat na `CloudBlockBlob`, `CloudPageBlob`, nebo `CloudBlobDirectory` objektu.</span><span class="sxs-lookup"><span data-stu-id="f257c-158">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="f257c-159">Pokud je typ neznámý, můžete použít kontrolu typu zjistíte, které vysílat.</span><span class="sxs-lookup"><span data-stu-id="f257c-159">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="f257c-160">Následující kód ukazuje, jak načíst a získat výstup URI pro každou položku v `mydata` kontejneru:</span><span class="sxs-lookup"><span data-stu-id="f257c-160">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="f257c-161">Můžete také objekty BLOB název informace o cestě jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="f257c-161">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="f257c-162">Tím se vytvoří struktura virtuálního adresáře, který můžete uspořádat a procházení, stejně jako u tradičních systémů souborů.</span><span class="sxs-lookup"><span data-stu-id="f257c-162">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="f257c-163">Všimněte si, že strukturu adresáře je pouze virtuální – jenom prostředky, které jsou k dispozici v úložišti objektů Blob jsou kontejnery a objekty BLOB.</span><span class="sxs-lookup"><span data-stu-id="f257c-163">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="f257c-164">Však nabízí Klientská knihovna pro úložiště `CloudBlobDirectory` objekt, který má odkazovat na virtuální adresář a zjednodušit tak práci s objekty BLOB, které jsou tímto způsobem uspořádány.</span><span class="sxs-lookup"><span data-stu-id="f257c-164">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="f257c-165">Zvažte například následující sadu objektů BLOB bloku v kontejneru nazvaném `photos`:</span><span class="sxs-lookup"><span data-stu-id="f257c-165">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="f257c-166">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015 nebo Architektura/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg* 
 *2016/architecture/description.txt*
*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="f257c-166">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span></span>

<span data-ttu-id="f257c-167">Při volání `ListBlobs` do kontejneru (viz ukázka výše) se vrátí hierarchický výpis.</span><span class="sxs-lookup"><span data-stu-id="f257c-167">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="f257c-168">Pokud obsahuje oba `CloudBlobDirectory` a `CloudBlockBlob` objekty, které představují adresáře a objekty BLOB v kontejneru, v uvedeném pořadí, pak výsledný výstup vypadá podobně jako tento:</span><span class="sxs-lookup"><span data-stu-id="f257c-168">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="f257c-169">Volitelně můžete nastavit `UseFlatBlobListing` parametr `ListBlobs` metodu `true`.</span><span class="sxs-lookup"><span data-stu-id="f257c-169">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="f257c-170">V takovém případě je každý objekt blob v kontejneru vrácen jako `CloudBlockBlob` objektu.</span><span class="sxs-lookup"><span data-stu-id="f257c-170">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="f257c-171">Volání `ListBlobs` vrátit plochým výpisem vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="f257c-171">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="f257c-172">a v závislosti na aktuální obsah vašeho kontejneru, výsledky vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="f257c-172">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="f257c-173">Stáhnout objekty BLOB</span><span class="sxs-lookup"><span data-stu-id="f257c-173">Download blobs</span></span>

<span data-ttu-id="f257c-174">Pokud chcete stáhnout objekty BLOB, nejdřív načtěte odkaz na objekt blob a potom zavolejte `DownloadToStream` metoda.</span><span class="sxs-lookup"><span data-stu-id="f257c-174">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="f257c-175">Následující příklad používá `DownloadToStream` způsob přenosu obsahu objektu blob na objekt proudu, který potom můžete zachovat do místního souboru.</span><span class="sxs-lookup"><span data-stu-id="f257c-175">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="f257c-176">Můžete také `DownloadToStream` metoda pro stažení obsahu objektu blob jako textový řetězec.</span><span class="sxs-lookup"><span data-stu-id="f257c-176">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="f257c-177">Odstranění objektů BLOB</span><span class="sxs-lookup"><span data-stu-id="f257c-177">Delete blobs</span></span>

<span data-ttu-id="f257c-178">Chcete-li odstranit objekt blob, nejdřív získejte odkaz na objekt blob a potom volejte `Delete` metoda na něm.</span><span class="sxs-lookup"><span data-stu-id="f257c-178">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="f257c-179">Seznam objektů blob na stránkách asynchronně</span><span class="sxs-lookup"><span data-stu-id="f257c-179">List blobs in pages asynchronously</span></span>

<span data-ttu-id="f257c-180">Pokud provádíte výpis velkého počtu objektů BLOB nebo chcete řídit počet výsledků, které vrátíte v rámci jedné operace výpisu, můžete vytvořit seznam objektů blob na stránkách s výsledky.</span><span class="sxs-lookup"><span data-stu-id="f257c-180">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="f257c-181">Tento příklad ukazuje, jak vracet výsledky na stránkách asynchronně, tak, aby čekání na vrácení velké sady výsledků neblokovalo provádění.</span><span class="sxs-lookup"><span data-stu-id="f257c-181">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="f257c-182">Tento příklad ukazuje výpis plochého objektu blob, ale můžete také provést hierarchický výpis nastavením `useFlatBlobListing` parametr `ListBlobsSegmentedAsync` metodu `false`.</span><span class="sxs-lookup"><span data-stu-id="f257c-182">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="f257c-183">Ukázka definuje asynchronní metodu, pomocí `async` bloku.</span><span class="sxs-lookup"><span data-stu-id="f257c-183">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="f257c-184">``let!`` – Klíčové slovo pozastaví spuštění metody ukázky až do dokončení úlohy vytváření seznamu.</span><span class="sxs-lookup"><span data-stu-id="f257c-184">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="f257c-185">Tato rutina asynchronní jsme teď můžete použít takto.</span><span class="sxs-lookup"><span data-stu-id="f257c-185">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="f257c-186">Nejprve nahrát fiktivní data (pomocí místního souboru v tomto kurzu vytvořili).</span><span class="sxs-lookup"><span data-stu-id="f257c-186">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="f257c-187">Nyní volání rutiny.</span><span class="sxs-lookup"><span data-stu-id="f257c-187">Now, call the routine.</span></span> <span data-ttu-id="f257c-188">Používáte ``Async.RunSynchronously`` vynutit provedení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="f257c-188">You use ``Async.RunSynchronously`` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="f257c-189">Zápis do doplňovacího objektu BLOB</span><span class="sxs-lookup"><span data-stu-id="f257c-189">Writing to an append blob</span></span>

<span data-ttu-id="f257c-190">Doplňovací objekt blob je optimalizován pro operace připojení, například protokolování.</span><span class="sxs-lookup"><span data-stu-id="f257c-190">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="f257c-191">Podobně jako objekt blob bloku doplňovací objekt blob se skládá z bloků, ale při přidání nového bloku pro doplňovací objekt blob, je připojen vždy na konec objektu blob.</span><span class="sxs-lookup"><span data-stu-id="f257c-191">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="f257c-192">Nelze aktualizovat nebo odstranit existující blok v doplňovacím objektu blob.</span><span class="sxs-lookup"><span data-stu-id="f257c-192">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="f257c-193">ID bloku pro doplňovací objekt blob nejsou vystavená, protože jsou pro objekt blob bloku.</span><span class="sxs-lookup"><span data-stu-id="f257c-193">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="f257c-194">Každý blok v doplňovacím objektu blob může mít různou velikost, až do maximálního počtu 4 MB volného místa, a doplňovací objekt blob může obsahovat maximálně 50 000 bloků.</span><span class="sxs-lookup"><span data-stu-id="f257c-194">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="f257c-195">Maximální velikost doplňovacího objektu BLOB je proto něco větší než 195 GB (4 MB × 50 000 bloků).</span><span class="sxs-lookup"><span data-stu-id="f257c-195">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="f257c-196">Následující příklad vytvoří nový doplňovací objekt blob a připojí některá data, simulaci jednoduché operace protokolování.</span><span class="sxs-lookup"><span data-stu-id="f257c-196">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="f257c-197">V tématu [objekty BLOB bloku pochopení, objekty BLOB stránky a doplňovacích objektů blob](https://msdn.microsoft.com/library/azure/ee691964.aspx) Další informace o rozdílech mezi třemi typy objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="f257c-197">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="f257c-198">Souběžný přístup</span><span class="sxs-lookup"><span data-stu-id="f257c-198">Concurrent access</span></span>

<span data-ttu-id="f257c-199">Chcete-li podporovat souběžný přístup do objektu blob z více klientů nebo více instancí procesu, můžete použít **značky etag binárním rozsáhlým** nebo **zapůjčení**.</span><span class="sxs-lookup"><span data-stu-id="f257c-199">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="f257c-200">**Značka Etag** -poskytuje způsob, jak zjistit, že objektu blob nebo kontejneru byl změněn jiným procesem</span><span class="sxs-lookup"><span data-stu-id="f257c-200">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="f257c-201">**Zapůjčení** -poskytuje způsob, jak získat exkluzivní, obnovitelné, zápisu nebo odstranit přístupu do objektu blob pro v časovém intervalu</span><span class="sxs-lookup"><span data-stu-id="f257c-201">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="f257c-202">Další informace najdete v tématu [Správa souběžnost v Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="f257c-202">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="f257c-203">Názvy kontejnerů</span><span class="sxs-lookup"><span data-stu-id="f257c-203">Naming containers</span></span>

<span data-ttu-id="f257c-204">Každý objekt blob v úložišti Azure se musí nacházet v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="f257c-204">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="f257c-205">Kontejner je součástí názvu objektu blob.</span><span class="sxs-lookup"><span data-stu-id="f257c-205">The container forms part of the blob name.</span></span> <span data-ttu-id="f257c-206">Například `mydata` je název kontejneru v těchto ukázkových objektů blob identifikátory URI:</span><span class="sxs-lookup"><span data-stu-id="f257c-206">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="f257c-207">Název kontejneru musí být platný název DNS, který odpovídá následujícím pravidlům pro pojmenování:</span><span class="sxs-lookup"><span data-stu-id="f257c-207">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="f257c-208">Názvy kontejnerů musí začínat písmenem nebo číslicí a může obsahovat pouze písmena, číslice a pomlčky (-) znaků.</span><span class="sxs-lookup"><span data-stu-id="f257c-208">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="f257c-209">Každý znak pomlčka (-) musí být okamžitě a následnou písmenem nebo číslicí; po sobě jdoucí pomlčky nejsou povolené v názvech kontejneru.</span><span class="sxs-lookup"><span data-stu-id="f257c-209">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="f257c-210">Všechna písmena název kontejneru musí být malé.</span><span class="sxs-lookup"><span data-stu-id="f257c-210">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="f257c-211">Názvy kontejnerů musí mít délku 3 až 63 znaků.</span><span class="sxs-lookup"><span data-stu-id="f257c-211">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="f257c-212">Všimněte si, že název kontejneru musí být vždy malá písmena.</span><span class="sxs-lookup"><span data-stu-id="f257c-212">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="f257c-213">Pokud název kontejneru zahrnout velké písmeno nebo jinak porušíte pravidla po pojmenování kontejnerů, může se zobrazit chyba 400 (Chybný požadavek).</span><span class="sxs-lookup"><span data-stu-id="f257c-213">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="f257c-214">Správa zabezpečení pro objekty BLOB</span><span class="sxs-lookup"><span data-stu-id="f257c-214">Managing security for blobs</span></span>

<span data-ttu-id="f257c-215">Ve výchozím nastavení Azure Storage zajišťuje ochranu dat omezením přístupu k majiteli účtu, který je vlastníkem přístupové klíče účtu.</span><span class="sxs-lookup"><span data-stu-id="f257c-215">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="f257c-216">Když potřebujete sdílet data objektu blob ve vašem účtu úložiště, je důležité, aby nedošlo k ohrožení zabezpečení klíče pro přístup k účtu.</span><span class="sxs-lookup"><span data-stu-id="f257c-216">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="f257c-217">Navíc můžete šifrovat data objektů blob k zajištění, že se jedná o zabezpečený přenos přes síť nebo ve službě Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="f257c-217">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="f257c-218">Řízení přístupu k datům objektu blob</span><span class="sxs-lookup"><span data-stu-id="f257c-218">Controlling access to blob data</span></span>

<span data-ttu-id="f257c-219">Ve výchozím nastavení jsou data objektu blob ve vašem účtu úložiště je dostupné pouze majiteli účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="f257c-219">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="f257c-220">Ve výchozím nastavení ověřování požadavků na úložiště objektů Blob vyžaduje přístupový klíč účtu.</span><span class="sxs-lookup"><span data-stu-id="f257c-220">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="f257c-221">Můžete však určitá data objektu blob zpřístupnit ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="f257c-221">However, you might want to make certain blob data available to other users.</span></span>

<span data-ttu-id="f257c-222">Podrobnosti o tom, jak řídit přístup do úložiště objektů blob najdete v tématu [v příručce .NET pro oddíl úložiště objektů blob na řízení přístupu](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span><span class="sxs-lookup"><span data-stu-id="f257c-222">For details on how to control access to blob storage, see [the .NET guide for blob storage section on access control](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span></span>


### <a name="encrypting-blob-data"></a><span data-ttu-id="f257c-223">Šifrování dat objektů blob</span><span class="sxs-lookup"><span data-stu-id="f257c-223">Encrypting blob data</span></span>

<span data-ttu-id="f257c-224">Úložiště Azure podporuje šifrování dat objektů blob na straně klienta i na serveru.</span><span class="sxs-lookup"><span data-stu-id="f257c-224">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

<span data-ttu-id="f257c-225">Podrobnosti na šifrování dat objektů blob najdete v tématu [v příručce .NET pro oddíl úložiště objektů blob v šifrování](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span><span class="sxs-lookup"><span data-stu-id="f257c-225">For details on encrypting blob data, see [the .NET guide for blob storage section on encryption](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f257c-226">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f257c-226">Next steps</span></span>

<span data-ttu-id="f257c-227">Teď, když jste se naučili základy používání Blob storage, postupujte podle následujících odkazech na další informace.</span><span class="sxs-lookup"><span data-stu-id="f257c-227">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="f257c-228">Nástroje</span><span class="sxs-lookup"><span data-stu-id="f257c-228">Tools</span></span>
- <span data-ttu-id="f257c-229">[F # AzureStorageTypeProvider](http://fsprojects.github.io/AzureStorageTypeProvider/) F # – zprostředkovatel typu používanou prozkoumat prostředky Blob, tabulky a fronty Azure Storage a snadno použít operace CRUD s nimi.</span><span class="sxs-lookup"><span data-stu-id="f257c-229">[F# AzureStorageTypeProvider](http://fsprojects.github.io/AzureStorageTypeProvider/) An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>
- <span data-ttu-id="f257c-230">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) k F # rozhraní API pro používání služby Microsoft Azure Table Storage</span><span class="sxs-lookup"><span data-stu-id="f257c-230">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) An F# API for using Microsoft Azure Table Storage service</span></span>
- <span data-ttu-id="f257c-231">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) je samostatná aplikace, volná, od společnosti Microsoft, který umožňuje vizuálně pracovat s daty Azure Storage ve Windows, OS X a Linux.</span><span class="sxs-lookup"><span data-stu-id="f257c-231">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) is a free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="f257c-232">Odkaz na objekt BLOB úložiště</span><span class="sxs-lookup"><span data-stu-id="f257c-232">Blob storage reference</span></span>

- [<span data-ttu-id="f257c-233">Klientská knihovna pro úložiště pro .NET – referenční informace</span><span class="sxs-lookup"><span data-stu-id="f257c-233">Storage Client Library for .NET reference</span></span>](http://go.microsoft.com/fwlink/?LinkID=390731&clcid=0x409)
- [<span data-ttu-id="f257c-234">Referenční dokumentace rozhraní API REST</span><span class="sxs-lookup"><span data-stu-id="f257c-234">REST API reference</span></span>](http://msdn.microsoft.com/library/azure/dd179355)

### <a name="related-guides"></a><span data-ttu-id="f257c-235">Související příručky</span><span class="sxs-lookup"><span data-stu-id="f257c-235">Related guides</span></span>

- [<span data-ttu-id="f257c-236">Začínáme s Azure Blob Storage v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f257c-236">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/documentation/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="f257c-237">Přenos dat pomocí nástroje příkazového řádku azcopy</span><span class="sxs-lookup"><span data-stu-id="f257c-237">Transfer data with the AzCopy command-line utility</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="f257c-238">Konfigurace připojovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="f257c-238">Configuring Connection Strings</span></span>](http://msdn.microsoft.com/library/azure/ee758697.aspx)
- [<span data-ttu-id="f257c-239">Blog týmu Azure Storage</span><span class="sxs-lookup"><span data-stu-id="f257c-239">Azure Storage Team Blog</span></span>](http://blogs.msdn.com/b/windowsazurestorage/)
