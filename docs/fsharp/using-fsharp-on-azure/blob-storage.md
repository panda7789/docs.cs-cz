---
title: Začínáme se službou Azure Blob Storage s využitím F#
description: Ukládejte nestrukturovaná data v cloudu pomocí služby Azure Blob Storage.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 79f6a559ac603b0544916764126a988d3f3f43d7
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092626"
---
# <a name="get-started-with-azure-blob-storage-using-f"></a><span data-ttu-id="264e7-103">Začínáme s Azure Blob Storage s využitím F\#</span><span class="sxs-lookup"><span data-stu-id="264e7-103">Get started with Azure Blob storage using F\#</span></span>

<span data-ttu-id="264e7-104">Úložiště objektů blob v Azure je služba, která ukládá nestrukturovaná data v cloudu jako objekty nebo objekty blob.</span><span class="sxs-lookup"><span data-stu-id="264e7-104">Azure Blob storage is a service that stores unstructured data in the cloud as objects/blobs.</span></span> <span data-ttu-id="264e7-105">Do Blob storage se dá ukládat jakýkoli druh textu nebo binárních dat, jako je dokument, soubor médií nebo instalátor aplikace.</span><span class="sxs-lookup"><span data-stu-id="264e7-105">Blob storage can store any type of text or binary data, such as a document, media file, or application installer.</span></span> <span data-ttu-id="264e7-106">Blob storage se také nazývá úložiště objektů.</span><span class="sxs-lookup"><span data-stu-id="264e7-106">Blob storage is also referred to as object storage.</span></span>

<span data-ttu-id="264e7-107">V tomto článku se dozvíte, jak provádět běžné úlohy pomocí služby Blob Storage.</span><span class="sxs-lookup"><span data-stu-id="264e7-107">This article shows you how to perform common tasks using Blob storage.</span></span> <span data-ttu-id="264e7-108">Ukázky se napíší pomocí F# Azure Storage klientské knihovny pro .NET.</span><span class="sxs-lookup"><span data-stu-id="264e7-108">The samples are written using F# using the Azure Storage Client Library for .NET.</span></span> <span data-ttu-id="264e7-109">Mezi zahrnuté úlohy patří postup při nahrávání, vypsání, stahování a odstraňování objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="264e7-109">The tasks covered include how to upload, list, download, and delete blobs.</span></span>

<span data-ttu-id="264e7-110">Koncepční přehled služby Blob Storage najdete v [průvodci .NET pro úložiště objektů BLOB](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span><span class="sxs-lookup"><span data-stu-id="264e7-110">For a conceptual overview of blob storage, see [the .NET guide for blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="264e7-111">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="264e7-111">Prerequisites</span></span>

<span data-ttu-id="264e7-112">Pokud chcete použít tuto příručku, musíte nejdřív [vytvořit účet úložiště Azure](/azure/storage/common/storage-account-create).</span><span class="sxs-lookup"><span data-stu-id="264e7-112">To use this guide, you must first [create an Azure storage account](/azure/storage/common/storage-account-create).</span></span> <span data-ttu-id="264e7-113">Pro tento účet budete potřebovat taky přístupový klíč k úložišti.</span><span class="sxs-lookup"><span data-stu-id="264e7-113">You also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="264e7-114">Vytvoření F# skriptu a spuštění F# Interactive</span><span class="sxs-lookup"><span data-stu-id="264e7-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="264e7-115">Ukázky v tomto článku se dají použít buď v F# aplikaci, nebo ve F# skriptu.</span><span class="sxs-lookup"><span data-stu-id="264e7-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="264e7-116">Chcete-li F# vytvořit skript, vytvořte soubor s příponou `.fsx`, například `blobs.fsx`ve vašem F# vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="264e7-116">To create an F# script, create a file with the `.fsx` extension, for example `blobs.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="264e7-117">Dále použijte [Správce balíčků](package-management.md) , jako je [paket](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) , k instalaci balíčků `WindowsAzure.Storage` a `Microsoft.WindowsAzure.ConfigurationManager` a odkazování `WindowsAzure.Storage.dll` a `Microsoft.WindowsAzure.Configuration.dll` ve vašem skriptu pomocí direktivy `#r`.</span><span class="sxs-lookup"><span data-stu-id="264e7-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` and `Microsoft.WindowsAzure.ConfigurationManager` packages and reference `WindowsAzure.Storage.dll` and `Microsoft.WindowsAzure.Configuration.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="264e7-118">Přidání deklarací oboru názvů</span><span class="sxs-lookup"><span data-stu-id="264e7-118">Add namespace declarations</span></span>

<span data-ttu-id="264e7-119">Přidejte do horní části souboru `open` následující příkazy `blobs.fsx`:</span><span class="sxs-lookup"><span data-stu-id="264e7-119">Add the following `open` statements to the top of the `blobs.fsx` file:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="264e7-120">Získání připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="264e7-120">Get your connection string</span></span>

<span data-ttu-id="264e7-121">Pro tento kurz potřebujete připojovací řetězec Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="264e7-121">You need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="264e7-122">Další informace o připojovacích řetězcích najdete v tématu [Konfigurace připojovacích řetězců úložiště](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="264e7-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="264e7-123">V tomto kurzu do skriptu zadáte připojovací řetězec, například:</span><span class="sxs-lookup"><span data-stu-id="264e7-123">For the tutorial, you enter your connection string in your script, like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L11-L11)]

<span data-ttu-id="264e7-124">To však **nedoporučujeme** pro skutečné projekty.</span><span class="sxs-lookup"><span data-stu-id="264e7-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="264e7-125">Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="264e7-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="264e7-126">Vždy klíč účtu úložiště pečlivě chraňte.</span><span class="sxs-lookup"><span data-stu-id="264e7-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="264e7-127">Nedávejte ho jiným uživatelům, nezakódovávejte ho ani ho neukládejte do souboru ve formátu prostého textu, který je přístupný ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="264e7-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="264e7-128">Klíč můžete znovu vygenerovat pomocí webu Azure Portal, pokud se domníváte, že je možné, že došlo k ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="264e7-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="264e7-129">Pro reálné aplikace je nejlepší způsob, jak udržovat připojovací řetězec úložiště, v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="264e7-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="264e7-130">Chcete-li načíst připojovací řetězec z konfiguračního souboru, můžete to provést:</span><span class="sxs-lookup"><span data-stu-id="264e7-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L13-L15)]

<span data-ttu-id="264e7-131">Použití nástroje Azure Configuration Manager není povinné.</span><span class="sxs-lookup"><span data-stu-id="264e7-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="264e7-132">Můžete také použít rozhraní API, jako je například typ `ConfigurationManager` .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="264e7-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="264e7-133">Analýza připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="264e7-133">Parse the connection string</span></span>

<span data-ttu-id="264e7-134">K analýze připojovacího řetězce použijte:</span><span class="sxs-lookup"><span data-stu-id="264e7-134">To parse the connection string, use:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L21-L22)]

<span data-ttu-id="264e7-135">Vrátí `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="264e7-135">This returns a `CloudStorageAccount`.</span></span>

### <a name="create-some-local-dummy-data"></a><span data-ttu-id="264e7-136">Vytvoření některých místních fiktivních dat</span><span class="sxs-lookup"><span data-stu-id="264e7-136">Create some local dummy data</span></span>

<span data-ttu-id="264e7-137">Než začnete, vytvořte v adresáři našeho skriptu nějaké fiktivní místní údaje.</span><span class="sxs-lookup"><span data-stu-id="264e7-137">Before you begin, create some dummy local data in the directory of our script.</span></span> <span data-ttu-id="264e7-138">Později tato data nahrajete.</span><span class="sxs-lookup"><span data-stu-id="264e7-138">Later you upload this data.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L28-L30)]

### <a name="create-the-blob-service-client"></a><span data-ttu-id="264e7-139">Vytvoření klienta služby Blob service</span><span class="sxs-lookup"><span data-stu-id="264e7-139">Create the Blob service client</span></span>

<span data-ttu-id="264e7-140">Typ `CloudBlobClient` umožňuje načíst kontejnery a objekty blob uložené v úložišti objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="264e7-140">The `CloudBlobClient` type enables you to retrieve containers and blobs stored in Blob storage.</span></span> <span data-ttu-id="264e7-141">Tady je jeden ze způsobů, jak vytvořit klienta služby:</span><span class="sxs-lookup"><span data-stu-id="264e7-141">Here's one way to create the service client:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L36-L36)]

<span data-ttu-id="264e7-142">Teď můžete napsat kód, který bude číst data z Blob storage a bude je tam také zapisovat.</span><span class="sxs-lookup"><span data-stu-id="264e7-142">Now you are ready to write code that reads data from and writes data to Blob storage.</span></span>

## <a name="create-a-container"></a><span data-ttu-id="264e7-143">Vytvoření kontejneru</span><span class="sxs-lookup"><span data-stu-id="264e7-143">Create a container</span></span>

<span data-ttu-id="264e7-144">Tento příklad ukazuje, jak vytvořit kontejner, pokud ještě neexistuje:</span><span class="sxs-lookup"><span data-stu-id="264e7-144">This example shows how to create a container if it does not already exist:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L42-L46)]

<span data-ttu-id="264e7-145">Ve výchozím nastavení je nový kontejner privátní, což znamená, že ke stažení objektů blob z tohoto kontejneru musíte zadat přístupový klíč úložiště.</span><span class="sxs-lookup"><span data-stu-id="264e7-145">By default, the new container is private, meaning that you must specify your storage access key to download blobs from this container.</span></span> <span data-ttu-id="264e7-146">Když chcete, aby soubory v kontejneru byly k dispozici všem uživatelům, můžete jej pomocí následujícího kódu nastavit jako veřejný:</span><span class="sxs-lookup"><span data-stu-id="264e7-146">If you want to make the files within the container available to everyone, you can set the container to be public using the following code:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L48-L49)]

<span data-ttu-id="264e7-147">Kdokoli na Internetu může vidět objekty blob ve veřejném kontejneru, upravit nebo odstranit je ale můžete jenom v případě, že máte příslušný přístupový klíč k účtu nebo sdílený přístupový podpis.</span><span class="sxs-lookup"><span data-stu-id="264e7-147">Anyone on the Internet can see blobs in a public container, but you can modify or delete them only if you have the appropriate account access key or a shared access signature.</span></span>

## <a name="upload-a-blob-into-a-container"></a><span data-ttu-id="264e7-148">Nahrání objektu blob do kontejneru</span><span class="sxs-lookup"><span data-stu-id="264e7-148">Upload a blob into a container</span></span>

<span data-ttu-id="264e7-149">Úložiště objektů blob v Azure podporuje objekty blob bloku a objekty blob stránky.</span><span class="sxs-lookup"><span data-stu-id="264e7-149">Azure Blob Storage supports block blobs and page blobs.</span></span> <span data-ttu-id="264e7-150">Ve většině případů je objekt blob bloku doporučeným typem, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="264e7-150">In most cases, a block blob is the recommended type to use.</span></span>

<span data-ttu-id="264e7-151">Když chcete nahrát soubor do objektu blob bloku, získejte odkaz na kontejner a použijte ho k získání odkazu objektu blob bloku.</span><span class="sxs-lookup"><span data-stu-id="264e7-151">To upload a file to a block blob, get a container reference and use it to get a block blob reference.</span></span> <span data-ttu-id="264e7-152">Jakmile budete mít odkaz na objekt blob, můžete do něj nahrát libovolný datový proud zavoláním metody `UploadFromFile`.</span><span class="sxs-lookup"><span data-stu-id="264e7-152">Once you have a blob reference, you can upload any stream of data to it by calling the `UploadFromFile` method.</span></span> <span data-ttu-id="264e7-153">Tato operace vytvoří objekt blob, pokud předtím neexistoval, nebo ho přepíše, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="264e7-153">This operation creates the blob if it didn't previously exist, or overwrite it if it does exist.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L55-L59)]

## <a name="list-the-blobs-in-a-container"></a><span data-ttu-id="264e7-154">Zobrazí seznam objektů blob v kontejneru</span><span class="sxs-lookup"><span data-stu-id="264e7-154">List the blobs in a container</span></span>

<span data-ttu-id="264e7-155">Pokud chcete mít seznam objektů blob v kontejneru, nejdřív získejte odkaz na kontejner.</span><span class="sxs-lookup"><span data-stu-id="264e7-155">To list the blobs in a container, first get a container reference.</span></span> <span data-ttu-id="264e7-156">Pak můžete použít metodu `ListBlobs` kontejneru k načtení objektů BLOB a adresářů v ní.</span><span class="sxs-lookup"><span data-stu-id="264e7-156">You can then use the container's `ListBlobs` method to retrieve the blobs and/or directories within it.</span></span> <span data-ttu-id="264e7-157">Chcete-li získat přístup k bohatě se sadou vlastností a metod vrácených `IListBlobItem`, je nutné ji přetypovat na objekt `CloudBlockBlob`, `CloudPageBlob`nebo `CloudBlobDirectory`.</span><span class="sxs-lookup"><span data-stu-id="264e7-157">To access the rich set of properties and methods for a returned `IListBlobItem`, you must cast it to a `CloudBlockBlob`, `CloudPageBlob`, or `CloudBlobDirectory` object.</span></span> <span data-ttu-id="264e7-158">Pokud je typ neznámý, můžete použít kontrolu typu a zjistit, na který typ vysílat.</span><span class="sxs-lookup"><span data-stu-id="264e7-158">If the type is unknown, you can use a type check to determine which to cast it to.</span></span> <span data-ttu-id="264e7-159">Následující kód ukazuje, jak načíst a získat výstup URI pro každou položku v `mydata` kontejneru:</span><span class="sxs-lookup"><span data-stu-id="264e7-159">The following code demonstrates how to retrieve and output the URI of each item in the `mydata` container:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L67-L80)]

<span data-ttu-id="264e7-160">Můžete také pojmenovat objekty BLOB s informacemi o cestě v jejich názvech.</span><span class="sxs-lookup"><span data-stu-id="264e7-160">You can also name blobs with path information in their names.</span></span> <span data-ttu-id="264e7-161">Tím se vytvoří struktura virtuálního adresáře, kterou můžete organizovat a měnit podle potřeby jako u tradičních systémů souborů.</span><span class="sxs-lookup"><span data-stu-id="264e7-161">This creates a virtual directory structure that you can organize and traverse as you would a traditional file system.</span></span> <span data-ttu-id="264e7-162">Všimněte si, že struktura adresářů je jenom virtuální - jediné prostředky, které jsou dostupné v úložišti objektů Blob,  jsou kontejnery a objekty blob.</span><span class="sxs-lookup"><span data-stu-id="264e7-162">Note that the directory structure is virtual only - the only resources available in Blob storage are containers and blobs.</span></span> <span data-ttu-id="264e7-163">Klientská knihovna pro úložiště ale nabízí objekt `CloudBlobDirectory`, který odkazuje na virtuální adresář a zjednodušuje proces práce s objekty blob, které jsou tímto způsobem uspořádány.</span><span class="sxs-lookup"><span data-stu-id="264e7-163">However, the storage client library offers a `CloudBlobDirectory` object to refer to a virtual directory and simplify the process of working with blobs that are organized in this way.</span></span>

<span data-ttu-id="264e7-164">Můžete zvolit například následující sadu objektů blob bloku v kontejneru nazvaném `photos`:</span><span class="sxs-lookup"><span data-stu-id="264e7-164">For example, consider the following set of block blobs in a container named `photos`:</span></span>

<span data-ttu-id="264e7-165">*photo1. jpg*</span><span class="sxs-lookup"><span data-stu-id="264e7-165">*photo1.jpg*</span></span>\
<span data-ttu-id="264e7-166">*2015/architektura/Description. txt*</span><span class="sxs-lookup"><span data-stu-id="264e7-166">*2015/architecture/description.txt*</span></span>\
<span data-ttu-id="264e7-167">\ *2015/architektury/photo3. jpg*</span><span class="sxs-lookup"><span data-stu-id="264e7-167">*2015/architecture/photo3.jpg*\</span></span>
<span data-ttu-id="264e7-168">\ *2015/architektury/photo4. jpg*</span><span class="sxs-lookup"><span data-stu-id="264e7-168">*2015/architecture/photo4.jpg*\</span></span>
<span data-ttu-id="264e7-169">*2016/architektura/photo5. jpg*</span><span class="sxs-lookup"><span data-stu-id="264e7-169">*2016/architecture/photo5.jpg*</span></span>\
<span data-ttu-id="264e7-170">*2016/architektura/photo6. jpg*</span><span class="sxs-lookup"><span data-stu-id="264e7-170">*2016/architecture/photo6.jpg*</span></span>\
<span data-ttu-id="264e7-171">*2016/architektura/Description. txt*</span><span class="sxs-lookup"><span data-stu-id="264e7-171">*2016/architecture/description.txt*</span></span>\
<span data-ttu-id="264e7-172">\ *2016/photo7. jpg*</span><span class="sxs-lookup"><span data-stu-id="264e7-172">*2016/photo7.jpg*\</span></span>

<span data-ttu-id="264e7-173">Při volání `ListBlobs` na kontejneru (jako ve výše uvedené ukázce) se vrátí hierarchický výpis.</span><span class="sxs-lookup"><span data-stu-id="264e7-173">When you call `ListBlobs` on a container (as in the above sample), a hierarchical listing is returned.</span></span> <span data-ttu-id="264e7-174">Pokud obsahuje `CloudBlobDirectory` i `CloudBlockBlob` objektů, které představují adresáře a objekty BLOB v kontejneru, pak výsledný výstup vypadá podobně jako tento:</span><span class="sxs-lookup"><span data-stu-id="264e7-174">If it contains both `CloudBlobDirectory` and `CloudBlockBlob` objects, representing the directories and blobs in the container, respectively, then the resulting output looks similar to this:</span></span>

```console
Directory: https://<accountname>.blob.core.windows.net/photos/2015/
Directory: https://<accountname>.blob.core.windows.net/photos/2016/
Block blob of length 505623: https://<accountname>.blob.core.windows.net/photos/photo1.jpg
```

<span data-ttu-id="264e7-175">Volitelně můžete nastavit parametr `UseFlatBlobListing` metody `ListBlobs` na `true`.</span><span class="sxs-lookup"><span data-stu-id="264e7-175">Optionally, you can set the `UseFlatBlobListing` parameter of the `ListBlobs` method to `true`.</span></span> <span data-ttu-id="264e7-176">V takovém případě se každý objekt BLOB v kontejneru vrátí jako objekt `CloudBlockBlob`.</span><span class="sxs-lookup"><span data-stu-id="264e7-176">In this case, every blob in the container is returned as a `CloudBlockBlob` object.</span></span> <span data-ttu-id="264e7-177">Volání `ListBlobs` k vrácení nestrukturovaného seznamu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="264e7-177">The call to `ListBlobs` to return a flat listing looks like this:</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L82-L89)]

<span data-ttu-id="264e7-178">a v závislosti na aktuálním obsahu vašeho kontejneru vypadá výsledek takto:</span><span class="sxs-lookup"><span data-stu-id="264e7-178">and, depending on the current contents of your container, the results look like this:</span></span>

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

## <a name="download-blobs"></a><span data-ttu-id="264e7-179">Stáhnout objekty blob</span><span class="sxs-lookup"><span data-stu-id="264e7-179">Download blobs</span></span>

<span data-ttu-id="264e7-180">Chcete-li stáhnout objekty blob, načtěte nejprve odkaz na objekt BLOB a potom zavolejte metodu `DownloadToStream`.</span><span class="sxs-lookup"><span data-stu-id="264e7-180">To download blobs, first retrieve a blob reference and then call the `DownloadToStream` method.</span></span> <span data-ttu-id="264e7-181">Následující příklad používá metodu `DownloadToStream` k přenosu obsahu objektu blob do objektu streamu, který pak můžete zachovat do místního souboru.</span><span class="sxs-lookup"><span data-stu-id="264e7-181">The following example uses the `DownloadToStream` method to transfer the blob contents to a stream object that you can then persist to a local file.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L95-L101)]

<span data-ttu-id="264e7-182">Pomocí metody `DownloadToStream` můžete také stáhnout obsah objektu BLOB jako textový řetězec.</span><span class="sxs-lookup"><span data-stu-id="264e7-182">You can also use the `DownloadToStream` method to download the contents of a blob as a text string.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L103-L106)]

## <a name="delete-blobs"></a><span data-ttu-id="264e7-183">Odstranění objektů blob</span><span class="sxs-lookup"><span data-stu-id="264e7-183">Delete blobs</span></span>

<span data-ttu-id="264e7-184">Pokud chcete odstranit objekt blob, nejdřív Získejte odkaz na objekt BLOB a pak na něj volejte metodu `Delete`.</span><span class="sxs-lookup"><span data-stu-id="264e7-184">To delete a blob, first get a blob reference and then call the `Delete` method on it.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L112-L116)]

## <a name="list-blobs-in-pages-asynchronously"></a><span data-ttu-id="264e7-185">Asynchronní zobrazení seznamu objektů blob na stránkách</span><span class="sxs-lookup"><span data-stu-id="264e7-185">List blobs in pages asynchronously</span></span>

<span data-ttu-id="264e7-186">Když provádíte výpis velkého počtu objektů blob nebo chcete mít přehled o počtu výsledků, které vrátíte v rámci jedné operace výpisu, můžete vytvořit seznam objektů blob na stránkách s výsledky.</span><span class="sxs-lookup"><span data-stu-id="264e7-186">If you are listing a large number of blobs, or you want to control the number of results you return in one listing operation, you can list blobs in pages of results.</span></span> <span data-ttu-id="264e7-187">Tento příklad ukazuje, jak vracet výsledky na stránkách asynchronně tak, aby čekání na vrácení velké sady výsledků neblokovalo provádění.</span><span class="sxs-lookup"><span data-stu-id="264e7-187">This example shows how to return results in pages asynchronously, so that execution is not blocked while waiting to return a large set of results.</span></span>

<span data-ttu-id="264e7-188">Tento příklad ukazuje výpis plochého objektu blob, ale můžete také provést hierarchický výpis nastavením parametru `useFlatBlobListing` `ListBlobsSegmentedAsync` metody na `false`.</span><span class="sxs-lookup"><span data-stu-id="264e7-188">This example shows a flat blob listing, but you can also perform a hierarchical listing, by setting the `useFlatBlobListing` parameter of the `ListBlobsSegmentedAsync` method to `false`.</span></span>

<span data-ttu-id="264e7-189">Ukázka definuje asynchronní metodu pomocí `async`ho bloku.</span><span class="sxs-lookup"><span data-stu-id="264e7-189">The sample defines an asynchronous method, using an `async` block.</span></span> <span data-ttu-id="264e7-190">Klíčové slovo ``let!`` pozastaví provádění ukázkové metody, dokud není dokončena úloha výpisu.</span><span class="sxs-lookup"><span data-stu-id="264e7-190">The ``let!`` keyword suspends execution of the sample method until the listing task completes.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L122-L160)]

<span data-ttu-id="264e7-191">Tuto asynchronní rutinu teď můžeme použít následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="264e7-191">We can now use this asynchronous routine as follows.</span></span> <span data-ttu-id="264e7-192">Nejdřív nahrajete některá fiktivní data (pomocí místního souboru vytvořeného dříve v tomto kurzu).</span><span class="sxs-lookup"><span data-stu-id="264e7-192">First you upload some dummy data (using the local file created earlier in this tutorial).</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L162-L166)]

<span data-ttu-id="264e7-193">Nyní zavolejte rutinu.</span><span class="sxs-lookup"><span data-stu-id="264e7-193">Now, call the routine.</span></span> <span data-ttu-id="264e7-194">Použijete `Async.RunSynchronously` k vynucení provedení asynchronní operace.</span><span class="sxs-lookup"><span data-stu-id="264e7-194">You use `Async.RunSynchronously` to force the execution of the asynchronous operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L168-L168)]

## <a name="writing-to-an-append-blob"></a><span data-ttu-id="264e7-195">Zápis do doplňovacího objektu blob</span><span class="sxs-lookup"><span data-stu-id="264e7-195">Writing to an append blob</span></span>

<span data-ttu-id="264e7-196">Doplňovací objekt blob je optimalizován pro operace připojení, například protokolování.</span><span class="sxs-lookup"><span data-stu-id="264e7-196">An append blob is optimized for append operations, such as logging.</span></span> <span data-ttu-id="264e7-197">Podobně jako objekt blob bloku se doplňovací objekt blob skládá z bloků, ale když chcete do doplňovacího objektu blob připojit nový blok, je připojen vždy na konec objektu blob.</span><span class="sxs-lookup"><span data-stu-id="264e7-197">Like a block blob, an append blob is comprised of blocks, but when you add a new block to an append blob, it is always appended to the end of the blob.</span></span> <span data-ttu-id="264e7-198">Existující blok v doplňovacím objektu blob se nedá aktualizovat ani odstranit.</span><span class="sxs-lookup"><span data-stu-id="264e7-198">You cannot update or delete an existing block in an append blob.</span></span> <span data-ttu-id="264e7-199">ID bloku pro doplňovací objekt blob nejsou vystavená, protože jsou určená pro objekt blob bloku.</span><span class="sxs-lookup"><span data-stu-id="264e7-199">The block IDs for an append blob are not exposed as they are for a block blob.</span></span>

<span data-ttu-id="264e7-200">Každý blok v doplňovacím objektu blob může mít různou velikost až do 4 MB, každý doplňovací objekt blob může obsahovat maximálně 50 000 bloků.</span><span class="sxs-lookup"><span data-stu-id="264e7-200">Each block in an append blob can be a different size, up to a maximum of 4 MB, and an append blob can include a maximum of 50,000 blocks.</span></span> <span data-ttu-id="264e7-201">Maximální velikost doplňovacího objektu blob je proto o něco větší než 195 GB (4 MB × 50 000 bloků).</span><span class="sxs-lookup"><span data-stu-id="264e7-201">The maximum size of an append blob is therefore slightly more than 195 GB (4 MB X 50,000 blocks).</span></span>

<span data-ttu-id="264e7-202">Následující příklad vytvoří nový doplňovací objekt BLOB a připojí k němu nějaká data a simuluje jednoduchou operaci protokolování.</span><span class="sxs-lookup"><span data-stu-id="264e7-202">The following example creates a new append blob and appends some data to it, simulating a simple logging operation.</span></span>

[!code-fsharp[BlobStorage](~/samples/snippets/fsharp/azure/blob-storage.fsx#L174-L203)]

<span data-ttu-id="264e7-203">Další informace o rozdílech mezi třemi typy objektů blob získáte v části [ Vysvětlení objektů blob bloku, objektů blob stránky a doplňovacích objektů blob](https://msdn.microsoft.com/library/azure/ee691964.aspx).</span><span class="sxs-lookup"><span data-stu-id="264e7-203">See [Understanding Block Blobs, Page Blobs, and Append Blobs](https://msdn.microsoft.com/library/azure/ee691964.aspx) for more information about the differences between the three types of blobs.</span></span>

## <a name="concurrent-access"></a><span data-ttu-id="264e7-204">Souběžný přístup</span><span class="sxs-lookup"><span data-stu-id="264e7-204">Concurrent access</span></span>

<span data-ttu-id="264e7-205">Aby bylo možné podporovat souběžný přístup k objektu BLOB z více klientů nebo instancí více procesů, můžete použít **značky ETag** nebo **zapůjčení**.</span><span class="sxs-lookup"><span data-stu-id="264e7-205">To support concurrent access to a blob from multiple clients or multiple process instances, you can use **ETags** or **leases**.</span></span>

- <span data-ttu-id="264e7-206">**Značka ETag** – poskytuje způsob, jak zjistit, že objekt BLOB nebo kontejner byl upraven jiným procesem.</span><span class="sxs-lookup"><span data-stu-id="264e7-206">**Etag** - provides a way to detect that the blob or container has been modified by another process</span></span>

- <span data-ttu-id="264e7-207">**Zapůjčení** – poskytuje způsob, jak získat přístup výhradního, obnovitelného, zápisu nebo odstranění objektu BLOB po určitou dobu.</span><span class="sxs-lookup"><span data-stu-id="264e7-207">**Lease** - provides a way to obtain exclusive, renewable, write or delete access to a blob for a period of time</span></span>

<span data-ttu-id="264e7-208">Další informace najdete v tématu [Správa souběžnosti v Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span><span class="sxs-lookup"><span data-stu-id="264e7-208">For more information, see [Managing Concurrency in Microsoft Azure Storage](https://azure.microsoft.com/blog/managing-concurrency-in-microsoft-azure-storage-2/).</span></span>

## <a name="naming-containers"></a><span data-ttu-id="264e7-209">Pojmenování kontejnerů</span><span class="sxs-lookup"><span data-stu-id="264e7-209">Naming containers</span></span>

<span data-ttu-id="264e7-210">Každý objekt blob v úložišti Azure se musí nacházet v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="264e7-210">Every blob in Azure storage must reside in a container.</span></span> <span data-ttu-id="264e7-211">Kontejner je součástí názvu objektu blob.</span><span class="sxs-lookup"><span data-stu-id="264e7-211">The container forms part of the blob name.</span></span> <span data-ttu-id="264e7-212">Třeba `mydata` je název kontejneru v těchto identifikátorech URI ukázkových objektů blob:</span><span class="sxs-lookup"><span data-stu-id="264e7-212">For example, `mydata` is the name of the container in these sample blob URIs:</span></span>

- `https://storagesample.blob.core.windows.net/mydata/blob1.txt`
- `https://storagesample.blob.core.windows.net/mydata/photos/myphoto.jpg`

<span data-ttu-id="264e7-213">Název kontejneru musí být platný název DNS, který odpovídá následujícím pravidlům pro pojmenování:</span><span class="sxs-lookup"><span data-stu-id="264e7-213">A container name must be a valid DNS name, conforming to the following naming rules:</span></span>

1. <span data-ttu-id="264e7-214">Názvy kontejnerů musí začínat písmenem nebo číslicí a smí obsahovat jenom písmena, číslice a pomlčky (-).</span><span class="sxs-lookup"><span data-stu-id="264e7-214">Container names must start with a letter or number, and can contain only letters, numbers, and the dash (-) character.</span></span>
1. <span data-ttu-id="264e7-215">Bezprostředně před a za každým znakem pomlčky (-) se musí nacházet písmeno nebo číslice. Názvy kontejnerů nesmí obsahovat po sobě jdoucí pomlčky.</span><span class="sxs-lookup"><span data-stu-id="264e7-215">Every dash (-) character must be immediately preceded and followed by a letter or number; consecutive dashes are not permitted in container names.</span></span>
1. <span data-ttu-id="264e7-216">Název kontejneru musí být psaný malými písmeny.</span><span class="sxs-lookup"><span data-stu-id="264e7-216">All letters in a container name must be lowercase.</span></span>
1. <span data-ttu-id="264e7-217">Názvy kontejnerů musí mít délku 3 až 63 znaků.</span><span class="sxs-lookup"><span data-stu-id="264e7-217">Container names must be from 3 through 63 characters long.</span></span>

<span data-ttu-id="264e7-218">Upozorňujeme, že název kontejneru musí být psaný malými písmeny.</span><span class="sxs-lookup"><span data-stu-id="264e7-218">Note that the name of a container must always be lowercase.</span></span> <span data-ttu-id="264e7-219">Pokud v názvu kontejneru napíšete velké písmeno nebo jinak porušíte pravidla po pojmenování kontejnerů, může se zobrazit chyba 400 (Chybný požadavek).</span><span class="sxs-lookup"><span data-stu-id="264e7-219">If you include an upper-case letter in a container name, or otherwise violate the container naming rules, you may receive a 400 error (Bad Request).</span></span>

## <a name="managing-security-for-blobs"></a><span data-ttu-id="264e7-220">Správa zabezpečení pro objekty blob</span><span class="sxs-lookup"><span data-stu-id="264e7-220">Managing security for blobs</span></span>

<span data-ttu-id="264e7-221">Úložiště Azure ve výchozím nastavení zajišťuje ochranu dat omezením přístupu k majiteli účtu, který vlastní klíče pro přístup k účtu.</span><span class="sxs-lookup"><span data-stu-id="264e7-221">By default, Azure Storage keeps your data secure by limiting access to the account owner, who is in possession of the account access keys.</span></span> <span data-ttu-id="264e7-222">Když budete chtít sdílet data objektu blob na svém účtu úložiště, je důležité zajistit, aby nedošlo k ohrožení zabezpečení vašich klíčů pro přístup k účtu.</span><span class="sxs-lookup"><span data-stu-id="264e7-222">When you need to share blob data in your storage account, it is important to do so without compromising the security of your account access keys.</span></span> <span data-ttu-id="264e7-223">Navíc můžete šifrovat data objektů blob tak, aby byl zaručen jejich zabezpečený přenos přes síť nebo úložiště Azure.</span><span class="sxs-lookup"><span data-stu-id="264e7-223">Additionally, you can encrypt blob data to ensure that it is secure going over the wire and in Azure Storage.</span></span>

### <a name="controlling-access-to-blob-data"></a><span data-ttu-id="264e7-224">Kontrola přístupu k datům objektu blob</span><span class="sxs-lookup"><span data-stu-id="264e7-224">Controlling access to blob data</span></span>

<span data-ttu-id="264e7-225">Ve výchozím nastavení jsou data objektu blob ve vašem účtu úložiště dostupná pouze majiteli účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="264e7-225">By default, the blob data in your storage account is accessible only to storage account owner.</span></span> <span data-ttu-id="264e7-226">Ve výchozím nastavení vyžaduje ověřování požadavků na Blob storage přístupový klíč účtu.</span><span class="sxs-lookup"><span data-stu-id="264e7-226">Authenticating requests against Blob storage requires the account access key by default.</span></span> <span data-ttu-id="264e7-227">Můžete však chtít zpřístupnit určitá data objektů BLOB ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="264e7-227">However, you might want to make certain blob data available to other users.</span></span>

### <a name="encrypting-blob-data"></a><span data-ttu-id="264e7-228">Šifrování dat objektů blob</span><span class="sxs-lookup"><span data-stu-id="264e7-228">Encrypting blob data</span></span>

<span data-ttu-id="264e7-229">Azure Storage podporuje šifrování dat objektů BLOB v klientovi i na serveru.</span><span class="sxs-lookup"><span data-stu-id="264e7-229">Azure Storage supports encrypting blob data both at the client and on the server.</span></span>

## <a name="next-steps"></a><span data-ttu-id="264e7-230">Další kroky</span><span class="sxs-lookup"><span data-stu-id="264e7-230">Next steps</span></span>

<span data-ttu-id="264e7-231">Teď, když jste se naučili základy používání Blob storage, podívejte se na následující odkazy a získejte další informace.</span><span class="sxs-lookup"><span data-stu-id="264e7-231">Now that you've learned the basics of Blob storage, follow these links to learn more.</span></span>

### <a name="tools"></a><span data-ttu-id="264e7-232">Nástroje</span><span class="sxs-lookup"><span data-stu-id="264e7-232">Tools</span></span>

- <span data-ttu-id="264e7-233">[ F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span><span class="sxs-lookup"><span data-stu-id="264e7-233">[F# AzureStorageTypeProvider](https://fsprojects.github.io/AzureStorageTypeProvider/)</span></span>\
<span data-ttu-id="264e7-234">Poskytovatel F# typu, který se dá použít k prozkoumání prostředků blob, Table a Queue Azure Storage a snadné použití operací CRUD na nich.</span><span class="sxs-lookup"><span data-stu-id="264e7-234">An F# Type Provider which can be used to explore Blob, Table and Queue Azure Storage assets and easily apply CRUD operations on them.</span></span>

- <span data-ttu-id="264e7-235">[FSharp. Azure. Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span><span class="sxs-lookup"><span data-stu-id="264e7-235">[FSharp.Azure.Storage](https://github.com/fsprojects/FSharp.Azure.Storage)</span></span>\
<span data-ttu-id="264e7-236">F# Rozhraní API pro používání služby Microsoft Azure Table Storage</span><span class="sxs-lookup"><span data-stu-id="264e7-236">An F# API for using Microsoft Azure Table Storage service</span></span>

- <span data-ttu-id="264e7-237">[Průzkumník služby Microsoft Azure Storage (mase)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span><span class="sxs-lookup"><span data-stu-id="264e7-237">[Microsoft Azure Storage Explorer (MASE)](/azure/vs-azure-tools-storage-manage-with-storage-explorer)</span></span>\
<span data-ttu-id="264e7-238">Bezplatná samostatná aplikace od Microsoftu, která umožňuje vizuálně pracovat s Azure Storagemi daty ve Windows, OS X a Linux.</span><span class="sxs-lookup"><span data-stu-id="264e7-238">A free, standalone app from Microsoft that enables you to work visually with Azure Storage data on Windows, OS X, and Linux.</span></span>

### <a name="blob-storage-reference"></a><span data-ttu-id="264e7-239">Odkazy Blob storage</span><span class="sxs-lookup"><span data-stu-id="264e7-239">Blob storage reference</span></span>

- [<span data-ttu-id="264e7-240">Rozhraní API pro Azure Storage pro .NET</span><span class="sxs-lookup"><span data-stu-id="264e7-240">Azure Storage APIs for .NET</span></span>](/dotnet/api/overview/azure/storage)
- [<span data-ttu-id="264e7-241">Referenční informace o rozhraní REST API pro služby Azure Storage</span><span class="sxs-lookup"><span data-stu-id="264e7-241">Azure Storage Services REST API Reference</span></span>](/rest/api/storageservices/)

### <a name="related-guides"></a><span data-ttu-id="264e7-242">Související příručky</span><span class="sxs-lookup"><span data-stu-id="264e7-242">Related guides</span></span>

- [<span data-ttu-id="264e7-243">Ukázky pro Azure Blob Storage pro .NET</span><span class="sxs-lookup"><span data-stu-id="264e7-243">Azure Blob Storage Samples for .NET</span></span>](https://docs.microsoft.com/samples/azure-samples/storage-blob-dotnet-getting-started/storage-blob-dotnet-getting-started/)
- [<span data-ttu-id="264e7-244">Začínáme s AzCopy</span><span class="sxs-lookup"><span data-stu-id="264e7-244">Get started with AzCopy</span></span>](/azure/storage/common/storage-use-azcopy-v10)
- [<span data-ttu-id="264e7-245">Nakonfigurování připojovacích řetězců Azure Storage</span><span class="sxs-lookup"><span data-stu-id="264e7-245">Configure Azure Storage connection strings</span></span>](/azure/storage/common/storage-configure-connection-string)
- [<span data-ttu-id="264e7-246">Blog týmu Azure Storage</span><span class="sxs-lookup"><span data-stu-id="264e7-246">Azure Storage Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/windowsazurestorage/)
- [<span data-ttu-id="264e7-247">Rychlý Start: použití .NET k vytvoření objektu BLOB v úložišti objektů</span><span class="sxs-lookup"><span data-stu-id="264e7-247">Quickstart: Use .NET to create a blob in object storage</span></span>](/azure/storage/blobs/storage-quickstart-blobs-dotnet)
