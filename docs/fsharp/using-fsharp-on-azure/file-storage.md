---
title: "Začínáme s Azure File storage pomocí F #"
description: "Ukládejte data souborů v cloudu s Azure File storage a připojte svou cloudovou sdílenou z Azure virtuálního počítače (VM) nebo z lokální aplikace s Windows."
keywords: "Visual f #, f #, funkční programování, .NET, .NET Core, Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 5c26a0aa-186e-476c-9f87-e0191754579e
ms.openlocfilehash: 5e1f6914acad5ae8c7148a7238e2d1d6a8ca5867
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="ec611-104">Začínáme s Azure File storage pomocí F #</span><span class="sxs-lookup"><span data-stu-id="ec611-104">Get started with Azure File storage using F#</span></span> #

<span data-ttu-id="ec611-105">Úložiště Azure File je služba, která nabízí sdílené složky v cloudu přes standardní [zpráva bloku protokol Server (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span><span class="sxs-lookup"><span data-stu-id="ec611-105">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="ec611-106">Podporuje SMB 2.1 i protokol SMB 3.0.</span><span class="sxs-lookup"><span data-stu-id="ec611-106">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="ec611-107">S Azure File storage můžete migrovat starší aplikace, které spoléhají na sdílené složky Azure rychle a bez nákladných přepisů.</span><span class="sxs-lookup"><span data-stu-id="ec611-107">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="ec611-108">Aplikace běžící v cloudových službách nebo virtuálních počítačích Azure nebo z lokálních klientů můžou připojit sdílenou složku v cloudu, stejně, jako desktopová aplikace připojí typickou sdílenou složku SMB.</span><span class="sxs-lookup"><span data-stu-id="ec611-108">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="ec611-109">Libovolný počet součásti aplikace lze připojit a současně získat přístup ke sdílené složce úložiště.</span><span class="sxs-lookup"><span data-stu-id="ec611-109">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="ec611-110">Koncepční přehled úložiště file, najdete v tématu [v příručce .NET pro úložiště file](/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="ec611-110">For a conceptual overview of file storage, please see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ec611-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ec611-111">Prerequisites</span></span>

<span data-ttu-id="ec611-112">Chcete-li tohoto průvodce použijte, je nutné nejprve [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="ec611-112">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="ec611-113">Budete také potřebovat přístupový klíč k úložišti pro tento účet.</span><span class="sxs-lookup"><span data-stu-id="ec611-113">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="ec611-114">Vytvoření F # skript a spusťte F # interaktivní</span><span class="sxs-lookup"><span data-stu-id="ec611-114">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="ec611-115">Ukázky v tomto článku slouží v aplikaci F # nebo skriptu F #.</span><span class="sxs-lookup"><span data-stu-id="ec611-115">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="ec611-116">Chcete-li vytvořit skript F #, vytvořte soubor s `.fsx` příponu, třeba `files.fsx`, ve vašem vývojovém prostředí F #.</span><span class="sxs-lookup"><span data-stu-id="ec611-116">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="ec611-117">Pak pomocí [Správce balíčků](package-management.md) například [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` balíčku a referenční dokumentace `WindowsAzure.Storage.dll` ve vašem skriptu, použití `#r`– direktiva.</span><span class="sxs-lookup"><span data-stu-id="ec611-117">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="ec611-118">Přidání deklarace oborů názvů</span><span class="sxs-lookup"><span data-stu-id="ec611-118">Add namespace declarations</span></span>

<span data-ttu-id="ec611-119">Přidejte následující `open` příkazů do horní části `files.fsx` souboru:</span><span class="sxs-lookup"><span data-stu-id="ec611-119">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="ec611-120">Získat připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="ec611-120">Get your connection string</span></span>

<span data-ttu-id="ec611-121">Pro účely tohoto kurzu budete potřebovat připojovací řetězec službě Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="ec611-121">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="ec611-122">Další informace o připojovacích řetězcích najdete v tématu [nakonfigurování připojovacích řetězců Storage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="ec611-122">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="ec611-123">Pro tento kurz zadáte připojovacího řetězce ve vašem skriptu, například takto:</span><span class="sxs-lookup"><span data-stu-id="ec611-123">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="ec611-124">Je to ale **nedoporučuje** skutečných projekty.</span><span class="sxs-lookup"><span data-stu-id="ec611-124">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="ec611-125">Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="ec611-125">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="ec611-126">Vždycky pečlivě k ochraně klíče účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="ec611-126">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="ec611-127">Nedávejte ho jiným uživatelům, nezakódovávejte ho nebo ho uložit v souboru formátu prostého textu, který je přístupný ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="ec611-127">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="ec611-128">Můžete znovu vygenerovat klíč pomocí portálu Azure, pokud se domníváte, že by může ohrožení.</span><span class="sxs-lookup"><span data-stu-id="ec611-128">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="ec611-129">Skutečných aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ec611-129">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="ec611-130">K načtení připojovacího řetězce z konfiguračního souboru, můžete to udělat:</span><span class="sxs-lookup"><span data-stu-id="ec611-130">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="ec611-131">Použití nástroje Azure Configuration Manager není povinné.</span><span class="sxs-lookup"><span data-stu-id="ec611-131">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="ec611-132">Můžete také použít API jako třeba rozhraní .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="ec611-132">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="ec611-133">Analýza připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="ec611-133">Parse the connection string</span></span>

<span data-ttu-id="ec611-134">Chcete-li analyzovat připojovací řetězec, použijte:</span><span class="sxs-lookup"><span data-stu-id="ec611-134">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="ec611-135">Tato možnost vrátí `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="ec611-135">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="ec611-136">Vytvoření klienta služby souboru</span><span class="sxs-lookup"><span data-stu-id="ec611-136">Create the File service client</span></span>

<span data-ttu-id="ec611-137">`CloudFileClient` Typ umožňuje programu používat soubory uložené v úložišti File.</span><span class="sxs-lookup"><span data-stu-id="ec611-137">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="ec611-138">Tady je jeden způsob, jak vytvořit klienta služby:</span><span class="sxs-lookup"><span data-stu-id="ec611-138">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="ec611-139">Teď jste připravení psát kód, který načítá a zapisuje data do úložiště File.</span><span class="sxs-lookup"><span data-stu-id="ec611-139">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="ec611-140">Vytvoření sdílené složky</span><span class="sxs-lookup"><span data-stu-id="ec611-140">Create a file share</span></span>

<span data-ttu-id="ec611-141">Tento příklad ukazuje, jak vytvořit sdílenou složku, pokud ještě neexistuje:</span><span class="sxs-lookup"><span data-stu-id="ec611-141">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="ec611-142">Vytvoření kořenového adresáře a podadresáři</span><span class="sxs-lookup"><span data-stu-id="ec611-142">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="ec611-143">Zde můžete získat kořenový adresář a získat podadresář kořenu.</span><span class="sxs-lookup"><span data-stu-id="ec611-143">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="ec611-144">Můžete vytvořit i, pokud ještě neexistují.</span><span class="sxs-lookup"><span data-stu-id="ec611-144">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="ec611-145">Uložte text jako soubor</span><span class="sxs-lookup"><span data-stu-id="ec611-145">Upload text as a file</span></span>

<span data-ttu-id="ec611-146">Tento příklad ukazuje, jak nahrát text jako soubor.</span><span class="sxs-lookup"><span data-stu-id="ec611-146">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="ec611-147">Stáhněte soubor do místní kopii souboru</span><span class="sxs-lookup"><span data-stu-id="ec611-147">Download a file to a local copy of the file</span></span>

<span data-ttu-id="ec611-148">Zde si stáhnout soubor právě vytvořili, připojování obsah do místního souboru.</span><span class="sxs-lookup"><span data-stu-id="ec611-148">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="ec611-149">Nastavit maximální velikost sdílené složky</span><span class="sxs-lookup"><span data-stu-id="ec611-149">Set the maximum size for a file share</span></span>

<span data-ttu-id="ec611-150">Následující příklad ukazuje, jak zkontrolovat aktuální využití sdílené složky a jak nastavit kvótu pro sdílenou složku.</span><span class="sxs-lookup"><span data-stu-id="ec611-150">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="ec611-151">`FetchAttributes` musí být volána k naplnění sdílené složky `Properties`, a `SetProperties` rozšíří místní změny do úložiště Azure File.</span><span class="sxs-lookup"><span data-stu-id="ec611-151">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="ec611-152">Vygenerování sdíleného přístupového podpisu pro soubor nebo sdílené složky</span><span class="sxs-lookup"><span data-stu-id="ec611-152">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="ec611-153">Můžete vygenerovat sdílený přístupový podpis (SAS) pro sdílenou složku nebo pro konkrétní soubor.</span><span class="sxs-lookup"><span data-stu-id="ec611-153">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="ec611-154">Můžete také vytvořit zásady sdíleného přístupu ve sdílené složce ke správě sdílených přístupových podpisů.</span><span class="sxs-lookup"><span data-stu-id="ec611-154">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="ec611-155">Vytvoření zásady sdíleného přístupu se doporučuje, protože tím nabízí způsob odvolání SAS, pokud by měl být dojde k ohrožení.</span><span class="sxs-lookup"><span data-stu-id="ec611-155">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="ec611-156">Zde vytvoříte sdílenou přístup zásad ve sdílené složce a poté tuto zásadu použít k omezení pro SAS na souboru ve sdílené složce.</span><span class="sxs-lookup"><span data-stu-id="ec611-156">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="ec611-157">Další informace o vytváření a použití sdílených přístupových podpisů najdete v tématu [pomocí sdíleného přístupového podpisy (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) a [vytvoření a použití SAS s úložištěm Blob](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span><span class="sxs-lookup"><span data-stu-id="ec611-157">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="ec611-158">Kopírování souborů</span><span class="sxs-lookup"><span data-stu-id="ec611-158">Copy files</span></span>

<span data-ttu-id="ec611-159">Soubor můžete zkopírovat do jiného souboru nebo do objektu blob, nebo objekt blob do souboru.</span><span class="sxs-lookup"><span data-stu-id="ec611-159">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="ec611-160">Pokud kopírujete objekt blob do souboru nebo souboru do objektu blob, můžete *musí* použít sdílený přístupový podpis (SAS) k ověření zdroje objektu, i když kopírujete v rámci stejného účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="ec611-160">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="ec611-161">Zkopírujte soubor do jiného souboru</span><span class="sxs-lookup"><span data-stu-id="ec611-161">Copy a file to another file</span></span>

<span data-ttu-id="ec611-162">Zde zkopírujte soubor do jiného souboru ve stejné sdílené složce.</span><span class="sxs-lookup"><span data-stu-id="ec611-162">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="ec611-163">Protože tato operace kopírování kopíruje soubory ve stejném účtu úložiště, můžete pro kopírování použít ověření sdíleným klíčem.</span><span class="sxs-lookup"><span data-stu-id="ec611-163">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="ec611-164">Zkopírujte soubor do objektu blob</span><span class="sxs-lookup"><span data-stu-id="ec611-164">Copy a file to a blob</span></span>

<span data-ttu-id="ec611-165">Zde vytvoříte soubor a zkopírujte jej do objektu BLOB ve stejném účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="ec611-165">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="ec611-166">Můžete vytvořit SAS pro zdrojový soubor, který služba používá k ověření přístupu ke zdrojovému souboru během operace kopírování.</span><span class="sxs-lookup"><span data-stu-id="ec611-166">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="ec611-167">Stejným způsobem můžete kopírovat objekt blob do souboru.</span><span class="sxs-lookup"><span data-stu-id="ec611-167">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="ec611-168">Pokud je zdrojový objekt blob, vytvořte SAS k ověření přístupu k tomuto objektu blob při kopírování.</span><span class="sxs-lookup"><span data-stu-id="ec611-168">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="ec611-169">Řešení potíží s úložištěm File pomocí metrik</span><span class="sxs-lookup"><span data-stu-id="ec611-169">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="ec611-170">Azure Storage Analytics podporuje metriky pro úložiště souborů.</span><span class="sxs-lookup"><span data-stu-id="ec611-170">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="ec611-171">S údaji z metriky můžete sledovat žádosti a diagnostikovat problémy.</span><span class="sxs-lookup"><span data-stu-id="ec611-171">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="ec611-172">Metriky pro úložiště File můžete povolit [portálu Azure](https://portal.azure.com), nebo můžete provést z F # takto:</span><span class="sxs-lookup"><span data-stu-id="ec611-172">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="ec611-173">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ec611-173">Next steps</span></span>

<span data-ttu-id="ec611-174">Viz tyto odkazy na další informace o Azure File storage.</span><span class="sxs-lookup"><span data-stu-id="ec611-174">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="ec611-175">Koncepční články a videa</span><span class="sxs-lookup"><span data-stu-id="ec611-175">Conceptual articles and videos</span></span>

- [<span data-ttu-id="ec611-176">Azure Files Storage: hladký cloudový systém souborů protokolu SMB pro Windows a Linux</span><span class="sxs-lookup"><span data-stu-id="ec611-176">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="ec611-177">Jak používat Azure File Storage s Linuxem</span><span class="sxs-lookup"><span data-stu-id="ec611-177">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="ec611-178">Podpora nástrojů pro úložiště File</span><span class="sxs-lookup"><span data-stu-id="ec611-178">Tooling support for File storage</span></span>

- [<span data-ttu-id="ec611-179">Použití Azure PowerShell s Azure Storage</span><span class="sxs-lookup"><span data-stu-id="ec611-179">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="ec611-180">Postup použití nástroje AzCopy s Microsoft Azure Storage</span><span class="sxs-lookup"><span data-stu-id="ec611-180">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="ec611-181">Použití Azure CLI s Azure Storage</span><span class="sxs-lookup"><span data-stu-id="ec611-181">Using the Azure CLI with Azure Storage</span></span>](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="ec611-182">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ec611-182">Reference</span></span>

- [<span data-ttu-id="ec611-183">Klientská knihovna pro úložiště pro .NET – referenční informace</span><span class="sxs-lookup"><span data-stu-id="ec611-183">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="ec611-184">Referenční dokumentace rozhraní API služby REST souboru</span><span class="sxs-lookup"><span data-stu-id="ec611-184">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="ec611-185">Příspěvky blogu</span><span class="sxs-lookup"><span data-stu-id="ec611-185">Blog posts</span></span>

- [<span data-ttu-id="ec611-186">Úložiště Azure File je nyní obecně k dispozici</span><span class="sxs-lookup"><span data-stu-id="ec611-186">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="ec611-187">Uvnitř Azure File Storage</span><span class="sxs-lookup"><span data-stu-id="ec611-187">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [<span data-ttu-id="ec611-188">Představujeme službu Microsoft Azure File</span><span class="sxs-lookup"><span data-stu-id="ec611-188">Introducing Microsoft Azure File Service</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [<span data-ttu-id="ec611-189">Nastavení trvalých připojení k Microsoft Azure Files</span><span class="sxs-lookup"><span data-stu-id="ec611-189">Persisting connections to Microsoft Azure Files</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
