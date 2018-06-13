---
title: 'Začínáme s Azure File storage pomocí F #'
description: Ukládejte data souborů v cloudu s Azure File storage a připojte svou cloudovou sdílenou z Azure virtuálního počítače (VM) nebo z lokální aplikace s Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: e772da5f81d2e6827295d0dfe150934a415eb3bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569340"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="56f50-103">Začínáme s Azure File storage pomocí F #</span><span class="sxs-lookup"><span data-stu-id="56f50-103">Get started with Azure File storage using F#</span></span> #

<span data-ttu-id="56f50-104">Úložiště Azure File je služba, která nabízí sdílené složky v cloudu přes standardní [zpráva bloku protokol Server (SMB)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span><span class="sxs-lookup"><span data-stu-id="56f50-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="56f50-105">Podporuje SMB 2.1 i protokol SMB 3.0.</span><span class="sxs-lookup"><span data-stu-id="56f50-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="56f50-106">S Azure File storage můžete migrovat starší aplikace, které spoléhají na sdílené složky Azure rychle a bez nákladných přepisů.</span><span class="sxs-lookup"><span data-stu-id="56f50-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="56f50-107">Aplikace běžící v cloudových službách nebo virtuálních počítačích Azure nebo z lokálních klientů můžou připojit sdílenou složku v cloudu, stejně, jako desktopová aplikace připojí typickou sdílenou složku SMB.</span><span class="sxs-lookup"><span data-stu-id="56f50-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="56f50-108">Libovolný počet součásti aplikace lze připojit a současně získat přístup ke sdílené složce úložiště.</span><span class="sxs-lookup"><span data-stu-id="56f50-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="56f50-109">Koncepční přehled úložiště file, najdete v tématu [v příručce .NET pro úložiště file](/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="56f50-109">For a conceptual overview of file storage, please see [the .NET guide for file storage](/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="56f50-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56f50-110">Prerequisites</span></span>

<span data-ttu-id="56f50-111">Chcete-li tohoto průvodce použijte, je nutné nejprve [vytvořit účet úložiště Azure](/azure/storage/storage-create-storage-account).</span><span class="sxs-lookup"><span data-stu-id="56f50-111">To use this guide, you must first [create an Azure storage account](/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="56f50-112">Budete také potřebovat přístupový klíč k úložišti pro tento účet.</span><span class="sxs-lookup"><span data-stu-id="56f50-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="56f50-113">Vytvoření F # skript a spusťte F # interaktivní</span><span class="sxs-lookup"><span data-stu-id="56f50-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="56f50-114">Ukázky v tomto článku slouží v aplikaci F # nebo skriptu F #.</span><span class="sxs-lookup"><span data-stu-id="56f50-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="56f50-115">Chcete-li vytvořit skript F #, vytvořte soubor s `.fsx` příponu, třeba `files.fsx`, ve vašem vývojovém prostředí F #.</span><span class="sxs-lookup"><span data-stu-id="56f50-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="56f50-116">Pak pomocí [Správce balíčků](package-management.md) například [Stáhnout](https://fsprojects.github.io/Paket/) nebo [NuGet](https://www.nuget.org/) k instalaci `WindowsAzure.Storage` balíčku a referenční dokumentace `WindowsAzure.Storage.dll` ve vašem skriptu, použití `#r`– direktiva.</span><span class="sxs-lookup"><span data-stu-id="56f50-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="56f50-117">Přidání deklarace oborů názvů</span><span class="sxs-lookup"><span data-stu-id="56f50-117">Add namespace declarations</span></span>

<span data-ttu-id="56f50-118">Přidejte následující `open` příkazů do horní části `files.fsx` souboru:</span><span class="sxs-lookup"><span data-stu-id="56f50-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="56f50-119">Získat připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="56f50-119">Get your connection string</span></span>

<span data-ttu-id="56f50-120">Pro účely tohoto kurzu budete potřebovat připojovací řetězec službě Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="56f50-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="56f50-121">Další informace o připojovacích řetězcích najdete v tématu [nakonfigurování připojovacích řetězců Storage](/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="56f50-121">For more information about connection strings, see [Configure Storage Connection Strings](/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="56f50-122">Pro tento kurz zadáte připojovacího řetězce ve vašem skriptu, například takto:</span><span class="sxs-lookup"><span data-stu-id="56f50-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="56f50-123">Je to ale **nedoporučuje** skutečných projekty.</span><span class="sxs-lookup"><span data-stu-id="56f50-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="56f50-124">Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="56f50-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="56f50-125">Vždycky pečlivě k ochraně klíče účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="56f50-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="56f50-126">Nedávejte ho jiným uživatelům, nezakódovávejte ho nebo ho uložit v souboru formátu prostého textu, který je přístupný ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="56f50-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="56f50-127">Můžete znovu vygenerovat klíč pomocí portálu Azure, pokud se domníváte, že by může ohrožení.</span><span class="sxs-lookup"><span data-stu-id="56f50-127">You can regenerate your key using the Azure Portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="56f50-128">Skutečných aplikace, je nejlepší způsob, jak udržovat připojovací řetězec úložiště v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="56f50-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="56f50-129">K načtení připojovacího řetězce z konfiguračního souboru, můžete to udělat:</span><span class="sxs-lookup"><span data-stu-id="56f50-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="56f50-130">Použití nástroje Azure Configuration Manager není povinné.</span><span class="sxs-lookup"><span data-stu-id="56f50-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="56f50-131">Můžete také použít API jako třeba rozhraní .NET Framework `ConfigurationManager` typu.</span><span class="sxs-lookup"><span data-stu-id="56f50-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="56f50-132">Analýza připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="56f50-132">Parse the connection string</span></span>

<span data-ttu-id="56f50-133">Chcete-li analyzovat připojovací řetězec, použijte:</span><span class="sxs-lookup"><span data-stu-id="56f50-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="56f50-134">Tato možnost vrátí `CloudStorageAccount`.</span><span class="sxs-lookup"><span data-stu-id="56f50-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="56f50-135">Vytvoření klienta služby souboru</span><span class="sxs-lookup"><span data-stu-id="56f50-135">Create the File service client</span></span>

<span data-ttu-id="56f50-136">`CloudFileClient` Typ umožňuje programu používat soubory uložené v úložišti File.</span><span class="sxs-lookup"><span data-stu-id="56f50-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="56f50-137">Tady je jeden způsob, jak vytvořit klienta služby:</span><span class="sxs-lookup"><span data-stu-id="56f50-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="56f50-138">Teď jste připravení psát kód, který načítá a zapisuje data do úložiště File.</span><span class="sxs-lookup"><span data-stu-id="56f50-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="56f50-139">Vytvoření sdílené složky</span><span class="sxs-lookup"><span data-stu-id="56f50-139">Create a file share</span></span>

<span data-ttu-id="56f50-140">Tento příklad ukazuje, jak vytvořit sdílenou složku, pokud ještě neexistuje:</span><span class="sxs-lookup"><span data-stu-id="56f50-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="56f50-141">Vytvoření kořenového adresáře a podadresáři</span><span class="sxs-lookup"><span data-stu-id="56f50-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="56f50-142">Zde můžete získat kořenový adresář a získat podadresář kořenu.</span><span class="sxs-lookup"><span data-stu-id="56f50-142">Here, you get the root directory and get a sub-directory of the root.</span></span> <span data-ttu-id="56f50-143">Můžete vytvořit i, pokud ještě neexistují.</span><span class="sxs-lookup"><span data-stu-id="56f50-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="56f50-144">Uložte text jako soubor</span><span class="sxs-lookup"><span data-stu-id="56f50-144">Upload text as a file</span></span>

<span data-ttu-id="56f50-145">Tento příklad ukazuje, jak nahrát text jako soubor.</span><span class="sxs-lookup"><span data-stu-id="56f50-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="56f50-146">Stáhněte soubor do místní kopii souboru</span><span class="sxs-lookup"><span data-stu-id="56f50-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="56f50-147">Zde si stáhnout soubor právě vytvořili, připojování obsah do místního souboru.</span><span class="sxs-lookup"><span data-stu-id="56f50-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="56f50-148">Nastavit maximální velikost sdílené složky</span><span class="sxs-lookup"><span data-stu-id="56f50-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="56f50-149">Následující příklad ukazuje, jak zkontrolovat aktuální využití sdílené složky a jak nastavit kvótu pro sdílenou složku.</span><span class="sxs-lookup"><span data-stu-id="56f50-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="56f50-150">`FetchAttributes` musí být volána k naplnění sdílené složky `Properties`, a `SetProperties` rozšíří místní změny do úložiště Azure File.</span><span class="sxs-lookup"><span data-stu-id="56f50-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="56f50-151">Vygenerování sdíleného přístupového podpisu pro soubor nebo sdílené složky</span><span class="sxs-lookup"><span data-stu-id="56f50-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="56f50-152">Můžete vygenerovat sdílený přístupový podpis (SAS) pro sdílenou složku nebo pro konkrétní soubor.</span><span class="sxs-lookup"><span data-stu-id="56f50-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="56f50-153">Můžete také vytvořit zásady sdíleného přístupu ve sdílené složce ke správě sdílených přístupových podpisů.</span><span class="sxs-lookup"><span data-stu-id="56f50-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="56f50-154">Vytvoření zásady sdíleného přístupu se doporučuje, protože tím nabízí způsob odvolání SAS, pokud by měl být dojde k ohrožení.</span><span class="sxs-lookup"><span data-stu-id="56f50-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="56f50-155">Zde vytvoříte sdílenou přístup zásad ve sdílené složce a poté tuto zásadu použít k omezení pro SAS na souboru ve sdílené složce.</span><span class="sxs-lookup"><span data-stu-id="56f50-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="56f50-156">Další informace o vytváření a použití sdílených přístupových podpisů najdete v tématu [pomocí sdíleného přístupového podpisy (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) a [vytvoření a použití SAS s úložištěm Blob](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span><span class="sxs-lookup"><span data-stu-id="56f50-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="56f50-157">Kopírování souborů</span><span class="sxs-lookup"><span data-stu-id="56f50-157">Copy files</span></span>

<span data-ttu-id="56f50-158">Soubor můžete zkopírovat do jiného souboru nebo do objektu blob, nebo objekt blob do souboru.</span><span class="sxs-lookup"><span data-stu-id="56f50-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="56f50-159">Pokud kopírujete objekt blob do souboru nebo souboru do objektu blob, můžete *musí* použít sdílený přístupový podpis (SAS) k ověření zdroje objektu, i když kopírujete v rámci stejného účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="56f50-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="56f50-160">Zkopírujte soubor do jiného souboru</span><span class="sxs-lookup"><span data-stu-id="56f50-160">Copy a file to another file</span></span>

<span data-ttu-id="56f50-161">Zde zkopírujte soubor do jiného souboru ve stejné sdílené složce.</span><span class="sxs-lookup"><span data-stu-id="56f50-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="56f50-162">Protože tato operace kopírování kopíruje soubory ve stejném účtu úložiště, můžete pro kopírování použít ověření sdíleným klíčem.</span><span class="sxs-lookup"><span data-stu-id="56f50-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="56f50-163">Zkopírujte soubor do objektu blob</span><span class="sxs-lookup"><span data-stu-id="56f50-163">Copy a file to a blob</span></span>

<span data-ttu-id="56f50-164">Zde vytvoříte soubor a zkopírujte jej do objektu BLOB ve stejném účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="56f50-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="56f50-165">Můžete vytvořit SAS pro zdrojový soubor, který služba používá k ověření přístupu ke zdrojovému souboru během operace kopírování.</span><span class="sxs-lookup"><span data-stu-id="56f50-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="56f50-166">Stejným způsobem můžete kopírovat objekt blob do souboru.</span><span class="sxs-lookup"><span data-stu-id="56f50-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="56f50-167">Pokud je zdrojový objekt blob, vytvořte SAS k ověření přístupu k tomuto objektu blob při kopírování.</span><span class="sxs-lookup"><span data-stu-id="56f50-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="56f50-168">Řešení potíží s úložištěm File pomocí metrik</span><span class="sxs-lookup"><span data-stu-id="56f50-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="56f50-169">Azure Storage Analytics podporuje metriky pro úložiště souborů.</span><span class="sxs-lookup"><span data-stu-id="56f50-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="56f50-170">S údaji z metriky můžete sledovat žádosti a diagnostikovat problémy.</span><span class="sxs-lookup"><span data-stu-id="56f50-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="56f50-171">Metriky pro úložiště File můžete povolit [portálu Azure](https://portal.azure.com), nebo můžete provést z F # takto:</span><span class="sxs-lookup"><span data-stu-id="56f50-171">You can enable metrics for File storage from the [Azure Portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](../../../samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="56f50-172">Další kroky</span><span class="sxs-lookup"><span data-stu-id="56f50-172">Next steps</span></span>

<span data-ttu-id="56f50-173">Viz tyto odkazy na další informace o Azure File storage.</span><span class="sxs-lookup"><span data-stu-id="56f50-173">See these links for more information about Azure File storage.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="56f50-174">Koncepční články a videa</span><span class="sxs-lookup"><span data-stu-id="56f50-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="56f50-175">Azure Files Storage: hladký cloudový systém souborů protokolu SMB pro Windows a Linux</span><span class="sxs-lookup"><span data-stu-id="56f50-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="56f50-176">Jak používat Azure File Storage s Linuxem</span><span class="sxs-lookup"><span data-stu-id="56f50-176">How to use Azure File Storage with Linux</span></span>](/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="56f50-177">Podpora nástrojů pro úložiště File</span><span class="sxs-lookup"><span data-stu-id="56f50-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="56f50-178">Použití Azure PowerShell s Azure Storage</span><span class="sxs-lookup"><span data-stu-id="56f50-178">Using Azure PowerShell with Azure Storage</span></span>](/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="56f50-179">Postup použití nástroje AzCopy s Microsoft Azure Storage</span><span class="sxs-lookup"><span data-stu-id="56f50-179">How to use AzCopy with Microsoft Azure Storage</span></span>](/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="56f50-180">Použití Azure CLI s Azure Storage</span><span class="sxs-lookup"><span data-stu-id="56f50-180">Using the Azure CLI with Azure Storage</span></span>](/azure/storage/storage-azure-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="56f50-181">Odkaz</span><span class="sxs-lookup"><span data-stu-id="56f50-181">Reference</span></span>

- [<span data-ttu-id="56f50-182">Klientská knihovna pro úložiště pro .NET – referenční informace</span><span class="sxs-lookup"><span data-stu-id="56f50-182">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="56f50-183">Referenční dokumentace rozhraní API služby REST souboru</span><span class="sxs-lookup"><span data-stu-id="56f50-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="56f50-184">Příspěvky blogu</span><span class="sxs-lookup"><span data-stu-id="56f50-184">Blog posts</span></span>

- [<span data-ttu-id="56f50-185">Úložiště Azure File je nyní obecně k dispozici</span><span class="sxs-lookup"><span data-stu-id="56f50-185">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="56f50-186">Uvnitř Azure File Storage</span><span class="sxs-lookup"><span data-stu-id="56f50-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/) 
- [<span data-ttu-id="56f50-187">Představujeme službu Microsoft Azure File</span><span class="sxs-lookup"><span data-stu-id="56f50-187">Introducing Microsoft Azure File Service</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/12/introducing-microsoft-azure-file-service/)
- [<span data-ttu-id="56f50-188">Nastavení trvalých připojení k Microsoft Azure Files</span><span class="sxs-lookup"><span data-stu-id="56f50-188">Persisting connections to Microsoft Azure Files</span></span>](https://blogs.msdn.microsoft.com/windowsazurestorage/2014/05/26/persisting-connections-to-microsoft-azure-files/)
