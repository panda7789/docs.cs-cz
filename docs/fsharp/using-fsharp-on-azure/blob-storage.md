---
title: 'Začínáme s Azure Blob storage pomocí F #'
description: Ukládání nestrukturovaných dat v cloudu s Azure Blob storage.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 3ab08154bd374896fce777c7c373204c9048b65c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33576152"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="6b7bf-103">Začínáme s Azure Blob storage pomocí F #</span><span class="sxs-lookup"><span data-stu-id="6b7bf-103">Get started with Azure Blob storage using F#</span></span> #

<span data-ttu-id="6b7bf-104">Azure Blob storage je služba, která ukládá Nestrukturovaná data v cloudu jako objekty nebo objekty BLOB.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="6b7bf-105">Úložiště objektů BLOB můžete ukládat jakýkoli typ textu nebo binárních dat, jako je například dokument, soubor média nebo instalační program aplikace.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="6b7bf-106">Úložiště objektů blob se také označuje jako úložiště objektů.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="6b7bf-107">Tento článek ukazuje, jak provádět běžné úlohy pomocí úložiště objektů Blob.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="6b7bf-108">Ukázky jsou napsané v F # pomocí klientské knihovny pro úložiště Azure pro .NET.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="6b7bf-109">Úlohy popsané zahrnovat nahrát, seznam, stažení a odstranění objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="6b7bf-110">Koncepční přehled úložiště objektů blob, najdete v tématu [v příručce .NET pro úložiště objektů blob](/azure/storage/storage-dotnet-how-to-use-blobs).</span><span class="sxs-lookup"><span data-stu-id="6b7bf-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/storage-dotnet-how-to-use-blobs).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6b7bf-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6b7bf-111">Prerequisites</span></span>

<span data-ttu-id="6b7bf-112">Chcete-li tohoto průvodce použijte, je nutné nejprve [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="6b7bf-112">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span> <span data-ttu-id="6b7bf-113">Pro tento účet je také nutné přístupový klíč k úložišti.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="6b7bf-114">Vytvoření F # skript a spusťte F # interaktivní</span><span class="sxs-lookup"><span data-stu-id="6b7bf-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="6b7bf-115">Ukázky v tomto článku slouží v aplikaci F # nebo skriptu F #.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="6b7bf-116">Chcete-li vytvořit skript F #, vytvořte soubor s `.fsx` příponu, třeba `blobs.fsx`, ve vašem vývojovém prostředí F #.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="6b7bf-117">Pak pomocí [Správce balíčků](package-management.md) například [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` a `Microsoft.WindowsAzure.ConfigurationManager` balíčky a reference `WindowsAzure.Storage.dll` a `Microsoft.WindowsAzure.Configuration.dll` v pomocí skriptu `#r` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="6b7bf-118">Přidání deklarace oborů názvů</span><span class="sxs-lookup"><span data-stu-id="6b7bf-118">Add namespace declarations</span></span>

<span data-ttu-id="6b7bf-119">Přidejte následující `open` příkazů do horní části `blobs.fsx` souboru:</span><span class="sxs-lookup"><span data-stu-id="6b7bf-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="6b7bf-120">Získat připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="6b7bf-120">Get your connection string</span></span>

<span data-ttu-id="6b7bf-121">Pro účely tohoto kurzu potřebujete připojovací řetězec službě Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="6b7bf-122">Další informace o připojovacích řetězcích najdete v tématu [nakonfigurování připojovacích řetězců Storage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="6b7bf-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="6b7bf-123">Pro tento kurz zadejte připojovací řetězec ve vašem skriptu, například takto:</span><span class="sxs-lookup"><span data-stu-id="6b7bf-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="6b7bf-124">Je to ale **nedoporučuje** skutečných projekty.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="6b7bf-125">Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="6b7bf-126">Vždycky pečlivě k ochraně klíče účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="6b7bf-127">Nedávejte ho jiným uživatelům, nezakódovávejte ho nebo ho uložit v souboru formátu prostého textu, který je přístupný ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="6b7bf-128">Můžete znovu vygenerovat klíč pomocí portálu Azure, pokud se domníváte, že by může ohrožení.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="6b7bf-129">Skutečných aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="6b7bf-130">K načtení připojovacího řetězce z konfiguračního souboru, můžete to udělat:</span><span class="sxs-lookup"><span data-stu-id="6b7bf-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="6b7bf-131">Použití nástroje Azure Configuration Manager není povinné.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="6b7bf-132">Můžete také použít API jako třeba rozhraní .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="6b7bf-133">Analýza připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="6b7bf-133">Parse the connection string</span></span>

<span data-ttu-id="6b7bf-134">Chcete-li analyzovat připojovací řetězec, použijte:</span><span class="sxs-lookup"><span data-stu-id="6b7bf-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="6b7bf-135">Tento příkaz vrátí `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="6b7bf-136">Vytvořit některé místní fiktivní data</span><span class="sxs-lookup"><span data-stu-id="6b7bf-136">Create some local dummy data</span></span>

<span data-ttu-id="6b7bf-137">Než začnete, vytvořte některé fiktivní místní data v adresáři naše skriptu.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="6b7bf-138">Později nahrajete tato data.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="6b7bf-139">Vytvoření klienta služby objektů Blob</span><span class="sxs-lookup"><span data-stu-id="6b7bf-139">Create the Blob service client</span></span>

<span data-ttu-id="6b7bf-140">`CloudBlobClient` Typ umožňuje načíst kontejnery a objekty BLOB uložené v úložišti objektů Blob.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="6b7bf-141">Tady je jeden způsob, jak vytvořit klienta služby:</span><span class="sxs-lookup"><span data-stu-id="6b7bf-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="6b7bf-142">Teď jste připravení psát kód, který načítá a zapisuje data do úložiště objektů Blob.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="6b7bf-143">Vytvoření kontejneru</span><span class="sxs-lookup"><span data-stu-id="6b7bf-143">Create a container</span></span>

<span data-ttu-id="6b7bf-144">Tento příklad ukazuje, jak vytvořit kontejner, pokud ještě neexistuje:</span><span class="sxs-lookup"><span data-stu-id="6b7bf-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="6b7bf-145">Ve výchozím nastavení je nový kontejner privátní, což znamená, že musíte zadat přístupový klíč k úložišti ke stažení z tohoto kontejneru objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="6b7bf-146">Pokud chcete, aby soubory v kontejneru dostupné pro všechny uživatele, můžete nastavit kontejner, aby se veřejné, pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="6b7bf-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="6b7bf-147">Kdokoli na Internetu může vidět objekty BLOB ve veřejném kontejneru, ale můžete upravit nebo odstranit pouze v případě, že máte přístupový klíč odpovídající účtu nebo sdílený přístupový podpis.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="6b7bf-148">Nahrát objekt blob do kontejneru</span><span class="sxs-lookup"><span data-stu-id="6b7bf-148">Upload a blob into a container</span></span>

<span data-ttu-id="6b7bf-149">Úložiště objektů Blob Azure podporuje objekty BLOB bloku a objekty BLOB stránky.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="6b7bf-150">Ve většině případů je objekt blob bloku typ k použití doporučuje.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="6b7bf-151">Chcete-li nahrát soubor do objektu blob bloku, získejte odkaz na kontejner a umožňuje vám získat odkaz na objekt blob bloku.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="6b7bf-152">Až budete mít odkaz na objekt blob, můžete nahrát jakýkoli proud dat k němu voláním `UploadFromFile` metoda.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="6b7bf-153">Tato operace vytvoří objekt blob, pokud nebyla dříve neexistuje, nebo ho přepíše, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="6b7bf-154">Seznam objektů BLOB v kontejneru</span><span class="sxs-lookup"><span data-stu-id="6b7bf-154">List the blobs in a container</span></span>

<span data-ttu-id="6b7bf-155">Pro zobrazení seznamu objektů BLOB v kontejneru, nejdřív získejte odkaz na kontejner.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="6b7bf-156">Pak můžete použít kontejneru `ListBlobs` metoda pro načtení objektů BLOB a/nebo obsažené adresáře.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="6b7bf-157">Pro přístup k bohaté sadě vlastností a metod vrácené `IListBlobItem`, musíte vysílat na `CloudBlockBlob`, `CloudPageBlob`, nebo `CloudBlobDirectory` objektu.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="6b7bf-158">Pokud je typ neznámý, můžete použít kontrolu typu zjistíte, které vysílat.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="6b7bf-159">Následující kód ukazuje, jak načíst a získat výstup URI pro každou položku v `mydata` kontejneru:</span><span class="sxs-lookup"><span data-stu-id="6b7bf-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="6b7bf-160">Můžete také objekty BLOB název informace o cestě jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="6b7bf-161">Tím se vytvoří struktura virtuálního adresáře, který můžete uspořádat a procházení, stejně jako u tradičních systémů souborů.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="6b7bf-162">Všimněte si, že strukturu adresáře je pouze virtuální – jenom prostředky, které jsou k dispozici v úložišti objektů Blob jsou kontejnery a objekty BLOB.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-162">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="6b7bf-163">Však nabízí Klientská knihovna pro úložiště `CloudBlobDirectory` objekt, který má odkazovat na virtuální adresář a zjednodušit tak práci s objekty BLOB, které jsou tímto způsobem uspořádány.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="6b7bf-164">Zvažte například následující sadu objektů BLOB bloku v kontejneru nazvaném `photos`:</span><span class="sxs-lookup"><span data-stu-id="6b7bf-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="6b7bf-165">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span><span class="sxs-lookup"><span data-stu-id="6b7bf-165">*photo1.jpg*
*2015/architecture/description.txt*
*2015/architecture/photo3.jpg*
*2015/architecture/photo4.jpg*
*2016/architecture/photo5.jpg*
*2016/architecture/photo6.jpg*
*2016/architecture/description.txt*
*2016/photo7.jpg*</span></span>

<span data-ttu-id="6b7bf-166">Při volání `ListBlobs` do kontejneru (viz ukázka výše) se vrátí hierarchický výpis.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-166">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="6b7bf-167">Pokud obsahuje oba `CloudBlobDirectory` a `CloudBlockBlob` objekty, které představují adresáře a objekty BLOB v kontejneru, v uvedeném pořadí, pak výsledný výstup vypadá podobně jako tento:</span><span class="sxs-lookup"><span data-stu-id="6b7bf-167">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="6b7bf-168">Volitelně můžete nastavit `UseFlatBlobListing` parametr `ListBlobs` metodu `true`.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-168">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="6b7bf-169">V takovém případě je každý objekt blob v kontejneru vrácen jako `CloudBlockBlob` objektu.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-169">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="6b7bf-170">Volání `ListBlobs` vrátit plochým výpisem vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="6b7bf-170">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="6b7bf-171">a v závislosti na aktuální obsah vašeho kontejneru, výsledky vypadat například takto:</span><span class="sxs-lookup"><span data-stu-id="6b7bf-171">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="6b7bf-172">Stáhnout objekty BLOB</span><span class="sxs-lookup"><span data-stu-id="6b7bf-172">Download blobs</span></span>

<span data-ttu-id="6b7bf-173">Pokud chcete stáhnout objekty BLOB, nejdřív načtěte odkaz na objekt blob a potom zavolejte `DownloadToStream` metoda.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-173">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="6b7bf-174">Následující příklad používá `DownloadToStream` způsob přenosu obsahu objektu blob na objekt proudu, který potom můžete zachovat do místního souboru.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-174">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="6b7bf-175">Můžete také `DownloadToStream` metoda pro stažení obsahu objektu blob jako textový řetězec.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-175">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="6b7bf-176">Odstranění objektů BLOB</span><span class="sxs-lookup"><span data-stu-id="6b7bf-176">Delete blobs</span></span>

<span data-ttu-id="6b7bf-177">Chcete-li odstranit objekt blob, nejdřív získejte odkaz na objekt blob a potom volejte `Delete` metoda na něm.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-177">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="6b7bf-178">Seznam objektů blob na stránkách asynchronně</span><span class="sxs-lookup"><span data-stu-id="6b7bf-178">List blobs in pages asynchronously</span></span>

<span data-ttu-id="6b7bf-179">Pokud provádíte výpis velkého počtu objektů BLOB nebo chcete řídit počet výsledků, které vrátíte v rámci jedné operace výpisu, můžete vytvořit seznam objektů blob na stránkách s výsledky.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-179">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="6b7bf-180">Tento příklad ukazuje, jak vracet výsledky na stránkách asynchronně, tak, aby čekání na vrácení velké sady výsledků neblokovalo provádění.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-180">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="6b7bf-181">Tento příklad ukazuje výpis plochého objektu blob, ale můžete také provést hierarchický výpis nastavením `useFlatBlobListing` parametr `ListBlobsSegmentedAsync` metodu `false`.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-181">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="6b7bf-182">Ukázka definuje asynchronní metodu, pomocí `async` bloku.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-182">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="6b7bf-183">``let!`` – Klíčové slovo pozastaví spuštění metody ukázky až do dokončení úlohy vytváření seznamu.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-183">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="6b7bf-184">Tato rutina asynchronní jsme teď můžete použít takto.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-184">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="6b7bf-185">Nejprve nahrát fiktivní data (pomocí místního souboru v tomto kurzu vytvořili).</span><span class="sxs-lookup"><span data-stu-id="6b7bf-185">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="6b7bf-186">Nyní volání rutiny.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-186">Now, call the routine.</span></span> <span data-ttu-id="6b7bf-187">Používáte ``Async.RunSynchronously`` vynutit provedení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-187">You use ``Async.RunSynchronously`` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="6b7bf-188">Zápis do doplňovacího objektu BLOB</span><span class="sxs-lookup"><span data-stu-id="6b7bf-188">Writing to an append blob</span></span>

<span data-ttu-id="6b7bf-189">Doplňovací objekt blob je optimalizován pro operace připojení, například protokolování.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-189">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="6b7bf-190">Podobně jako objekt blob bloku doplňovací objekt blob se skládá z bloků, ale při přidání nového bloku pro doplňovací objekt blob, je připojen vždy na konec objektu blob.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-190">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="6b7bf-191">Nelze aktualizovat nebo odstranit existující blok v doplňovacím objektu blob.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-191">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="6b7bf-192">ID bloku pro doplňovací objekt blob nejsou vystavená, protože jsou pro objekt blob bloku.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-192">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="6b7bf-193">Každý blok v doplňovacím objektu blob může mít různou velikost, až do maximálního počtu 4 MB volného místa, a doplňovací objekt blob může obsahovat maximálně 50 000 bloků.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-193">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="6b7bf-194">Maximální velikost doplňovacího objektu BLOB je proto něco větší než 195 GB (4 MB × 50 000 bloků).</span><span class="sxs-lookup"><span data-stu-id="6b7bf-194">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="6b7bf-195">Následující příklad vytvoří nový doplňovací objekt blob a připojí některá data, simulaci jednoduché operace protokolování.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-195">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](../../../samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="6b7bf-196">V tématu [objekty BLOB bloku pochopení, objekty BLOB stránky a doplňovacích objektů blob](https://msdn.microsoft.com/library/azure/ee691964.aspx) Další informace o rozdílech mezi třemi typy objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-196">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="6b7bf-197">Souběžný přístup</span><span class="sxs-lookup"><span data-stu-id="6b7bf-197">Concurrent access</span></span>

<span data-ttu-id="6b7bf-198">Chcete-li podporovat souběžný přístup do objektu blob z více klientů nebo více instancí procesu, můžete použít **značky etag binárním rozsáhlým** nebo **zapůjčení**.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-198">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

* <span data-ttu-id="6b7bf-199">**Značka Etag** -poskytuje způsob, jak zjistit, že objektu blob nebo kontejneru byl změněn jiným procesem</span><span class="sxs-lookup"><span data-stu-id="6b7bf-199">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

* <span data-ttu-id="6b7bf-200">**Zapůjčení** -poskytuje způsob, jak získat exkluzivní, obnovitelné, zápisu nebo odstranit přístupu do objektu blob pro v časovém intervalu</span><span class="sxs-lookup"><span data-stu-id="6b7bf-200">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="6b7bf-201">Další informace najdete v tématu [Správa souběžnost v Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="6b7bf-201">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="6b7bf-202">Názvy kontejnerů</span><span class="sxs-lookup"><span data-stu-id="6b7bf-202">Naming containers</span></span>

<span data-ttu-id="6b7bf-203">Každý objekt blob v úložišti Azure se musí nacházet v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-203">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="6b7bf-204">Kontejner je součástí názvu objektu blob.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-204">The container forms part of the blob name.</span></span> <span data-ttu-id="6b7bf-205">Například `mydata` je název kontejneru v těchto ukázkových objektů blob identifikátory URI:</span><span class="sxs-lookup"><span data-stu-id="6b7bf-205">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

    https://storagesample.blob.core.windows.net/mydata/blob1.txt
    https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg

<span data-ttu-id="6b7bf-206">Název kontejneru musí být platný název DNS, který odpovídá následujícím pravidlům pro pojmenování:</span><span class="sxs-lookup"><span data-stu-id="6b7bf-206">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="6b7bf-207">Názvy kontejnerů musí začínat písmenem nebo číslicí a může obsahovat pouze písmena, číslice a pomlčky (-) znaků.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-207">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="6b7bf-208">Každý znak pomlčka (-) musí být okamžitě a následnou písmenem nebo číslicí; po sobě jdoucí pomlčky nejsou povolené v názvech kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-208">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="6b7bf-209">Všechna písmena název kontejneru musí být malé.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-209">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="6b7bf-210">Názvy kontejnerů musí mít délku 3 až 63 znaků.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-210">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="6b7bf-211">Všimněte si, že název kontejneru musí být vždy malá písmena.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-211">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="6b7bf-212">Pokud název kontejneru zahrnout velké písmeno nebo jinak porušíte pravidla po pojmenování kontejnerů, může se zobrazit chyba 400 (Chybný požadavek).</span><span class="sxs-lookup"><span data-stu-id="6b7bf-212">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="6b7bf-213">Správa zabezpečení pro objekty BLOB</span><span class="sxs-lookup"><span data-stu-id="6b7bf-213">Managing security for blobs</span></span>

<span data-ttu-id="6b7bf-214">Ve výchozím nastavení Azure Storage zajišťuje ochranu dat omezením přístupu k majiteli účtu, který je vlastníkem přístupové klíče účtu.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-214">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="6b7bf-215">Když potřebujete sdílet data objektu blob ve vašem účtu úložiště, je důležité, aby nedošlo k ohrožení zabezpečení klíče pro přístup k účtu.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-215">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="6b7bf-216">Navíc můžete šifrovat data objektů blob k zajištění, že se jedná o zabezpečený přenos přes síť nebo ve službě Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-216">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="6b7bf-217">Řízení přístupu k datům objektu blob</span><span class="sxs-lookup"><span data-stu-id="6b7bf-217">Controlling access to blob data</span></span>

<span data-ttu-id="6b7bf-218">Ve výchozím nastavení jsou data objektu blob ve vašem účtu úložiště je dostupné pouze majiteli účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-218">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="6b7bf-219">Ve výchozím nastavení ověřování požadavků na úložiště objektů Blob vyžaduje přístupový klíč účtu.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-219">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="6b7bf-220">Můžete však určitá data objektu blob zpřístupnit ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-220">However, you might want to make certain blob data available to other users.</span></span>

<span data-ttu-id="6b7bf-221">Podrobnosti o tom, jak řídit přístup do úložiště objektů blob najdete v tématu [v příručce .NET pro oddíl úložiště objektů blob na řízení přístupu](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span><span class="sxs-lookup"><span data-stu-id="6b7bf-221">For details on how to control access to blob storage, see [the .NET guide for blob storage section on access control](/azure/storage/storage-dotnet-how-to-use-blobs#controlling-access-to-blob-data).</span></span>


### <a name="encrypting-blob-data"></a><span data-ttu-id="6b7bf-222">Šifrování dat objektů blob</span><span class="sxs-lookup"><span data-stu-id="6b7bf-222">Encrypting blob data</span></span>

<span data-ttu-id="6b7bf-223">Úložiště Azure podporuje šifrování dat objektů blob na straně klienta i na serveru.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-223">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

<span data-ttu-id="6b7bf-224">Podrobnosti na šifrování dat objektů blob najdete v tématu [v příručce .NET pro oddíl úložiště objektů blob v šifrování](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span><span class="sxs-lookup"><span data-stu-id="6b7bf-224">For details on encrypting blob data, see [the .NET guide for blob storage section on encryption](/azure/storage/storage-dotnet-how-to-use-blobs#encrypting-blob-data).</span></span>

## <a name="next-steps"></a><span data-ttu-id="6b7bf-225">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6b7bf-225">Next steps</span></span>

<span data-ttu-id="6b7bf-226">Teď, když jste se naučili základy používání Blob storage, postupujte podle následujících odkazech na další informace.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-226">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="6b7bf-227">Nástroje</span><span class="sxs-lookup"><span data-stu-id="6b7bf-227">Tools</span></span>
- <span data-ttu-id="6b7bf-228">[F # AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) F # – zprostředkovatel typu používanou prozkoumat prostředky Blob, tabulky a fronty Azure Storage a snadno použít operace CRUD s nimi.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-228">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/) An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>
- <span data-ttu-id="6b7bf-229">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) k F # rozhraní API pro používání služby Microsoft Azure Table Storage</span><span class="sxs-lookup"><span data-stu-id="6b7bf-229">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage) An F# API for using Microsoft Azure Table Storage service</span></span>
- <span data-ttu-id="6b7bf-230">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) je samostatná aplikace, volná, od společnosti Microsoft, který umožňuje vizuálně pracovat s daty Azure Storage ve Windows, OS X a Linux.</span><span class="sxs-lookup"><span data-stu-id="6b7bf-230">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer) is a free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="6b7bf-231">Odkaz na objekt BLOB úložiště</span><span class="sxs-lookup"><span data-stu-id="6b7bf-231">Blob storage reference</span></span>

- [<span data-ttu-id="6b7bf-232">Rozhraní API úložiště Azure pro .NET</span><span class="sxs-lookup"><span data-stu-id="6b7bf-232">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="6b7bf-233">Referenční dokumentace rozhraní API REST služby Azure Storage</span><span class="sxs-lookup"><span data-stu-id="6b7bf-233">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/Azure-Storage-Services-REST-API-Reference)

### <a name="related-guides"></a><span data-ttu-id="6b7bf-234">Související příručky</span><span class="sxs-lookup"><span data-stu-id="6b7bf-234">Related guides</span></span>

- [<span data-ttu-id="6b7bf-235">Začínáme s Azure Blob Storage v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6b7bf-235">Getting Started with Azure Blob Storage in C#</span></span>](https://azure.microsoft.com/resources/samples/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="6b7bf-236">Přenos dat pomocí nástroje příkazového řádku azcopy v systému Windows</span><span class="sxs-lookup"><span data-stu-id="6b7bf-236">Transfer data with the AzCopy command-line utility on Windows</span></span>](/azure/storage/common/storage-use-azcopy)
- [<span data-ttu-id="6b7bf-237">Přenos dat pomocí nástroje příkazového řádku azcopy v systému Linux</span><span class="sxs-lookup"><span data-stu-id="6b7bf-237">Transfer data with the AzCopy command-line utility on Linux</span></span>](/azure/storage/common/storage-use-azcopy-linux)
- [<span data-ttu-id="6b7bf-238">Konfigurace připojovacích řetězců Azure Storage</span><span class="sxs-lookup"><span data-stu-id="6b7bf-238">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="6b7bf-239">Blog týmu Azure Storage</span><span class="sxs-lookup"><span data-stu-id="6b7bf-239">Azure Storage Team Blog</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/)
