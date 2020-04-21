---
title: Začínáme se službou Azure File Storage s využitím F#
description: Ukládejte data souborů do cloudu pomocí Azure File Storage a připojte svou cloudovou sdílenou složku z virtuálního počítače Azure nebo z lokální aplikace s Windows.
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: 1b38ee53f2f73f7b7f4ee12f712f487cb726d41e
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739589"
---
# <a name="get-started-with-azure-file-storage-using-f"></a><span data-ttu-id="ef6fe-103">Začínáme s úložištěm souborů Azure pomocí F\#</span><span class="sxs-lookup"><span data-stu-id="ef6fe-103">Get started with Azure File storage using F\#</span></span>

<span data-ttu-id="ef6fe-104">Úložiště Azure File je služba, která nabízí sdílené složky v cloudu přes standardní [protokol SMB (Server Message Block)](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span><span class="sxs-lookup"><span data-stu-id="ef6fe-104">Azure File storage is a service that offers file shares in the cloud using the standard [Server Message Block (SMB) Protocol](https://msdn.microsoft.com/library/windows/desktop/aa365233.aspx).</span></span> <span data-ttu-id="ef6fe-105">Podporují se SMB 2.1 i SMB 3.0.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-105">Both SMB 2.1 and SMB 3.0 are supported.</span></span> <span data-ttu-id="ef6fe-106">S Azure File Storage můžete rychle a bez nákladných přepisů migrovat starší aplikace, které spoléhají na sdílené složky, do Azure.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-106">With Azure File storage, you can migrate legacy applications that rely on file shares to Azure quickly and without costly rewrites.</span></span> <span data-ttu-id="ef6fe-107">Aplikace běžící v cloudových službách nebo virtuálních počítačích Azure nebo spuštěné z lokálních klientů můžou připojit sdílenou složku v cloudu stejným způsobem, jako desktopová aplikace připojí typickou sdílenou složku SMB.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-107">Applications running in Azure virtual machines or cloud services or from on-premises clients can mount a file share in the cloud, just as a desktop application mounts a typical SMB share.</span></span> <span data-ttu-id="ef6fe-108">Potom může sdílenou složku File Storage připojit a používat libovolný počet aplikací.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-108">Any number of application components can then mount and access the File storage share simultaneously.</span></span>

<span data-ttu-id="ef6fe-109">Koncepční přehled úložiště souborů naleznete [v průvodci .NET pro ukládání souborů](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-files).</span><span class="sxs-lookup"><span data-stu-id="ef6fe-109">For a conceptual overview of file storage, see [the .NET guide for file storage](https://docs.microsoft.com/azure/storage/storage-dotnet-how-to-use-files).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ef6fe-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ef6fe-110">Prerequisites</span></span>

<span data-ttu-id="ef6fe-111">Chcete-li použít tuto [příručku,](https://docs.microsoft.com/azure/storage/storage-create-storage-account)musíte nejprve vytvořit účet úložiště Azure .</span><span class="sxs-lookup"><span data-stu-id="ef6fe-111">To use this guide, you must first [create an Azure storage account](https://docs.microsoft.com/azure/storage/storage-create-storage-account).</span></span>
<span data-ttu-id="ef6fe-112">Budete také potřebovat přístupový klíč úložiště pro tento účet.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-112">You'll also need your storage access key for this account.</span></span>

## <a name="create-an-f-script-and-start-f-interactive"></a><span data-ttu-id="ef6fe-113">Vytvoření skriptu Jazyka F# a interaktivního spuštění jazyka F#</span><span class="sxs-lookup"><span data-stu-id="ef6fe-113">Create an F# Script and Start F# Interactive</span></span>

<span data-ttu-id="ef6fe-114">Ukázky v tomto článku lze použít v aplikaci F# nebo skript F#.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-114">The samples in this article can be used in either an F# application or an F# script.</span></span> <span data-ttu-id="ef6fe-115">Chcete-li vytvořit skript F#, `.fsx` vytvořte soubor `files.fsx`s příponou, například ve vývojovém prostředí F#.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-115">To create an F# script, create a file with the `.fsx` extension, for example `files.fsx`, in your F# development environment.</span></span>

<span data-ttu-id="ef6fe-116">Dále použijte [správce balíčků,](package-management.md) jako je [Paket](https://fsprojects.github.io/Paket/) `WindowsAzure.Storage` nebo [NuGet](https://www.nuget.org/) k instalaci `#r` balíčku a odkaz `WindowsAzure.Storage.dll` ve skriptu pomocí směrnice.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-116">Next, use a [package manager](package-management.md) such as [Paket](https://fsprojects.github.io/Paket/) or [NuGet](https://www.nuget.org/) to install the `WindowsAzure.Storage` package and reference `WindowsAzure.Storage.dll` in your script using a `#r` directive.</span></span>

### <a name="add-namespace-declarations"></a><span data-ttu-id="ef6fe-117">Přidání deklarací oboru názvů</span><span class="sxs-lookup"><span data-stu-id="ef6fe-117">Add namespace declarations</span></span>

<span data-ttu-id="ef6fe-118">Přidejte do horní části souboru `files.fsx` následující příkazy `open`:</span><span class="sxs-lookup"><span data-stu-id="ef6fe-118">Add the following `open` statements to the top of the `files.fsx` file:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L1-L5)]

### <a name="get-your-connection-string"></a><span data-ttu-id="ef6fe-119">Získání připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="ef6fe-119">Get your connection string</span></span>

<span data-ttu-id="ef6fe-120">Budete potřebovat připojovací řetězec Azure Storage pro tento kurz.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-120">You'll need an Azure Storage connection string for this tutorial.</span></span> <span data-ttu-id="ef6fe-121">Další informace o připojovacích řetězcích naleznete v [tématu Konfigurace připojovacích řetězců úložiště](https://docs.microsoft.com/azure/storage/storage-configure-connection-string).</span><span class="sxs-lookup"><span data-stu-id="ef6fe-121">For more information about connection strings, see [Configure Storage Connection Strings](https://docs.microsoft.com/azure/storage/storage-configure-connection-string).</span></span>

<span data-ttu-id="ef6fe-122">Pro účely kurzu zadáte připojovací řetězec do skriptu takto:</span><span class="sxs-lookup"><span data-stu-id="ef6fe-122">For the tutorial, you'll enter your connection string in your script, like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L11-L11)]

<span data-ttu-id="ef6fe-123">To se však **nedoporučuje** u skutečných projektů.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-123">However, this is **not recommended** for real projects.</span></span> <span data-ttu-id="ef6fe-124">Klíč účtu úložiště je podobný kořenovému heslu vašeho účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-124">Your storage account key is similar to the root password for your storage account.</span></span> <span data-ttu-id="ef6fe-125">Vždy klíč účtu úložiště pečlivě chraňte.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-125">Always be careful to protect your storage account key.</span></span> <span data-ttu-id="ef6fe-126">Nedávejte ho jiným uživatelům, nezakódovávejte ho ani ho neukládejte do souboru ve formátu prostého textu, který je přístupný ostatním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-126">Avoid distributing it to other users, hard-coding it, or saving it in a plain-text file that is accessible to others.</span></span> <span data-ttu-id="ef6fe-127">Klíč můžete znovu vygenerovat pomocí portálu Azure, pokud se domníváte, že byl ohrožen.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-127">You can regenerate your key using the Azure portal if you believe it may have been compromised.</span></span>

<span data-ttu-id="ef6fe-128">Pro skutečné aplikace je nejlepší způsob, jak udržovat připojovací řetězec úložiště, v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-128">For real applications, the best way to maintain your storage connection string is in a configuration file.</span></span> <span data-ttu-id="ef6fe-129">Chcete-li načíst připojovací řetězec z konfiguračního souboru, můžete to provést takto:</span><span class="sxs-lookup"><span data-stu-id="ef6fe-129">To fetch the connection string from a configuration file, you can do this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L13-L15)]

<span data-ttu-id="ef6fe-130">Použití nástroje Azure Configuration Manager není povinné.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-130">Using Azure Configuration Manager is optional.</span></span> <span data-ttu-id="ef6fe-131">Můžete také použít rozhraní API, jako je `ConfigurationManager` například typ rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-131">You can also use an API such as the .NET Framework's `ConfigurationManager` type.</span></span>

### <a name="parse-the-connection-string"></a><span data-ttu-id="ef6fe-132">Analýza připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="ef6fe-132">Parse the connection string</span></span>

<span data-ttu-id="ef6fe-133">Chcete-li analyzovat připojovací řetězec, použijte:</span><span class="sxs-lookup"><span data-stu-id="ef6fe-133">To parse the connection string, use:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L21-L22)]

<span data-ttu-id="ef6fe-134">Tím se `CloudStorageAccount`vrátí .</span><span class="sxs-lookup"><span data-stu-id="ef6fe-134">This will return a `CloudStorageAccount`.</span></span>

### <a name="create-the-file-service-client"></a><span data-ttu-id="ef6fe-135">Vytvoření klienta služby Soubor</span><span class="sxs-lookup"><span data-stu-id="ef6fe-135">Create the File service client</span></span>

<span data-ttu-id="ef6fe-136">Tento `CloudFileClient` typ umožňuje programově používat soubory uložené v úložišti souborů.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-136">The `CloudFileClient` type enables you to programmatically use files stored in File storage.</span></span> <span data-ttu-id="ef6fe-137">Tady je jeden ze způsobů, jak vytvořit klienta služby:</span><span class="sxs-lookup"><span data-stu-id="ef6fe-137">Here's one way to create the service client:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L28-L28)]

<span data-ttu-id="ef6fe-138">Nyní jste připraveni k zápisu kódu, ze kterého jsou čtena data a zapisují data do úložiště souborů.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-138">Now you are ready to write code that reads data from and writes data to File storage.</span></span>

## <a name="create-a-file-share"></a><span data-ttu-id="ef6fe-139">Vytvoření sdílené složky</span><span class="sxs-lookup"><span data-stu-id="ef6fe-139">Create a file share</span></span>

<span data-ttu-id="ef6fe-140">Tento příklad ukazuje, jak vytvořit sdílenou složku, pokud ještě neexistuje:</span><span class="sxs-lookup"><span data-stu-id="ef6fe-140">This example shows how to create a file share if it does not already exist:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L34-L35)]

## <a name="create-a-root-directory-and-a-subdirectory"></a><span data-ttu-id="ef6fe-141">Vytvoření kořenového adresáře a podadresáře</span><span class="sxs-lookup"><span data-stu-id="ef6fe-141">Create a root directory and a subdirectory</span></span>

<span data-ttu-id="ef6fe-142">Zde získáte kořenový adresář a získat podadresář kořenového adresáře.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-142">Here, you get the root directory and get a subdirectory of the root.</span></span> <span data-ttu-id="ef6fe-143">Můžete vytvořit obojí, pokud již neexistují.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-143">You create both if they don't already exist.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L41-L43)]

## <a name="upload-text-as-a-file"></a><span data-ttu-id="ef6fe-144">Nahrání textu jako souboru</span><span class="sxs-lookup"><span data-stu-id="ef6fe-144">Upload text as a file</span></span>

<span data-ttu-id="ef6fe-145">Tento příklad ukazuje, jak nahrát text jako soubor.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-145">This example shows how to upload text as a file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L49-L50)]

### <a name="download-a-file-to-a-local-copy-of-the-file"></a><span data-ttu-id="ef6fe-146">Stažení souboru do místní kopie souboru</span><span class="sxs-lookup"><span data-stu-id="ef6fe-146">Download a file to a local copy of the file</span></span>

<span data-ttu-id="ef6fe-147">Zde si stáhnete právě vytvořený soubor a připojíte obsah k místnímu souboru.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-147">Here you download the file just created, appending the contents to a local file.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L56-L56)]

### <a name="set-the-maximum-size-for-a-file-share"></a><span data-ttu-id="ef6fe-148">Nastavení maximální velikosti sdílené složky</span><span class="sxs-lookup"><span data-stu-id="ef6fe-148">Set the maximum size for a file share</span></span>

<span data-ttu-id="ef6fe-149">Dole uvedený příklad ukazuje, jak můžete zkontrolovat aktuální využití sdílené složky a jak nastavit kvótu pro sdílenou složku.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-149">The example below shows how to check the current usage for a share and how to set the quota for the share.</span></span> <span data-ttu-id="ef6fe-150">`FetchAttributes`musí být volána k `Properties`naplnění `SetProperties` sdílené složky a k šíření místních změn v úložišti souborů Azure.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-150">`FetchAttributes` must be called to populate a share's `Properties`, and `SetProperties` to propagate local changes to Azure File storage.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L62-L72)]

### <a name="generate-a-shared-access-signature-for-a-file-or-file-share"></a><span data-ttu-id="ef6fe-151">Vygenerování sdíleného přístupového podpisu pro soubor nebo sdílenou složku</span><span class="sxs-lookup"><span data-stu-id="ef6fe-151">Generate a shared access signature for a file or file share</span></span>

<span data-ttu-id="ef6fe-152">Můžete vygenerovat sdílený přístupový podpis (SAS) pro sdílenou složku nebo pro jednotlivé soubory.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-152">You can generate a shared access signature (SAS) for a file share or for an individual file.</span></span> <span data-ttu-id="ef6fe-153">Můžete taky vytvořit sdílené zásady přístupu pro sdílenou složku ke správě sdílených přístupových podpisů.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-153">You can also create a shared access policy on a file share to manage shared access signatures.</span></span> <span data-ttu-id="ef6fe-154">Vytvoření sdílených zásad přístupu se doporučuje, protože se tím nabízí způsob odvolání SAS v případě narušení jeho integrity nebo důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-154">Creating a shared access policy is recommended, as it provides a means of revoking the SAS if it should be compromised.</span></span>

<span data-ttu-id="ef6fe-155">Zde vytvoříte zásady sdíleného přístupu ve sdílené složce a pak tuto zásadu použijete k poskytnutí omezení pro SAS v souboru ve sdílené složce.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-155">Here, you create a shared access policy on a share, and then use that policy to provide the constraints for a SAS on a file in the share.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L78-L94)]

<span data-ttu-id="ef6fe-156">Další informace o vytváření a používání sdílených přístupových podpisů najdete v tématech [Použití sdílených přístupových podpisů (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1) a [Vytvoření a použití SAS se službou Blob Storage](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-2).</span><span class="sxs-lookup"><span data-stu-id="ef6fe-156">For more information about creating and using shared access signatures, see [Using Shared Access Signatures (SAS)](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-1) and [Create and use a SAS with Blob storage](https://docs.microsoft.com/azure/storage/storage-dotnet-shared-access-signature-part-2).</span></span>

### <a name="copy-files"></a><span data-ttu-id="ef6fe-157">Kopírování souborů</span><span class="sxs-lookup"><span data-stu-id="ef6fe-157">Copy files</span></span>

<span data-ttu-id="ef6fe-158">Soubor můžete zkopírovat do jiného souboru nebo do objektu blob nebo do objektu blob do souboru.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-158">You can copy a file to another file or to a blob, or a blob to a file.</span></span> <span data-ttu-id="ef6fe-159">Pokud kopírujete objekt blob do souboru nebo soubor do objektu blob, *musíte* k ověření zdrojového objektu použít sdílený přístupový podpis (SAS), a to i v případě, že kopírujete v rámci stejného účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-159">If you are copying a blob to a file, or a file to a blob, you *must* use a shared access signature (SAS) to authenticate the source object, even if you are copying within the same storage account.</span></span>

### <a name="copy-a-file-to-another-file"></a><span data-ttu-id="ef6fe-160">Kopírování souboru do jiného souboru</span><span class="sxs-lookup"><span data-stu-id="ef6fe-160">Copy a file to another file</span></span>

<span data-ttu-id="ef6fe-161">Zde zkopírujete soubor do jiného souboru ve stejné sdílené složce.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-161">Here, you copy a file to another file in the same share.</span></span> <span data-ttu-id="ef6fe-162">Protože tato operace kopírování kopíruje soubory ve stejném účtu úložiště, můžete pro kopírování použít ověření Sdíleným klíčem.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-162">Because this copy operation copies between files in the same storage account, you can use Shared Key authentication to perform the copy.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L100-L101)]

### <a name="copy-a-file-to-a-blob"></a><span data-ttu-id="ef6fe-163">Kopírování souboru do objektu blob</span><span class="sxs-lookup"><span data-stu-id="ef6fe-163">Copy a file to a blob</span></span>

<span data-ttu-id="ef6fe-164">Zde vytvoříte soubor a zkopírujete ho do objektu blob ve stejném účtu úložiště.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-164">Here, you create a file and copy it to a blob within the same storage account.</span></span> <span data-ttu-id="ef6fe-165">Vytvoříte SAS pro zdrojový soubor, který služba používá k ověření přístupu ke zdrojovému souboru během operace kopírování.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-165">You create a SAS for the source file, which the service uses to authenticate access to the source file during the copy operation.</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L107-L120)]

<span data-ttu-id="ef6fe-166">Stejným způsobem můžete kopírovat objekt blob do souboru.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-166">You can copy a blob to a file in the same way.</span></span> <span data-ttu-id="ef6fe-167">Pokud je zdrojovým objektem objekt blob, vytvořte SAS k ověření přístupu k tomuto objektu blob při kopírování.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-167">If the source object is a blob, then create a SAS to authenticate access to that blob during the copy operation.</span></span>

## <a name="troubleshooting-file-storage-using-metrics"></a><span data-ttu-id="ef6fe-168">Řešení problémů s úložištěm File pomocí metrik</span><span class="sxs-lookup"><span data-stu-id="ef6fe-168">Troubleshooting File storage using metrics</span></span>

<span data-ttu-id="ef6fe-169">Azure Storage Analytics podporuje metriky pro úložiště souborů.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-169">Azure Storage Analytics supports metrics for File storage.</span></span> <span data-ttu-id="ef6fe-170">S údaji z metriky můžete sledovat žádosti a diagnostikovat potíže.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-170">With metrics data, you can trace requests and diagnose issues.</span></span>

<span data-ttu-id="ef6fe-171">Metriky úložiště souborů můžete povolit z [webu Azure Portal](https://portal.azure.com), nebo to můžete udělat z F#, takto:</span><span class="sxs-lookup"><span data-stu-id="ef6fe-171">You can enable metrics for File storage from the [Azure portal](https://portal.azure.com), or you can do it from F# like this:</span></span>

[!code-fsharp[FileStorage](~/samples/snippets/fsharp/azure/file-storage.fsx#L126-L140)]

## <a name="next-steps"></a><span data-ttu-id="ef6fe-172">Další kroky</span><span class="sxs-lookup"><span data-stu-id="ef6fe-172">Next steps</span></span>

<span data-ttu-id="ef6fe-173">Další informace o úložišti souborů Azure najdete v těchto odkazech.</span><span class="sxs-lookup"><span data-stu-id="ef6fe-173">For more information about Azure File storage, see these links.</span></span>

### <a name="conceptual-articles-and-videos"></a><span data-ttu-id="ef6fe-174">Koncepční články a videa</span><span class="sxs-lookup"><span data-stu-id="ef6fe-174">Conceptual articles and videos</span></span>

- [<span data-ttu-id="ef6fe-175">Azure Files Storage: hladký cloudový souborový systém SMB pro Windows a Linux</span><span class="sxs-lookup"><span data-stu-id="ef6fe-175">Azure Files Storage: a frictionless cloud SMB file system for Windows and Linux</span></span>](https://azure.microsoft.com/resources/videos/azurecon-2015-azure-files-storage-a-frictionless-cloud-smb-file-system-for-windows-and-linux/)
- [<span data-ttu-id="ef6fe-176">Jak používat Azure File Storage s Linuxem</span><span class="sxs-lookup"><span data-stu-id="ef6fe-176">How to use Azure File Storage with Linux</span></span>](https://docs.microsoft.com/azure/storage/storage-how-to-use-files-linux)

### <a name="tooling-support-for-file-storage"></a><span data-ttu-id="ef6fe-177">Podpora nástrojů pro úložiště File</span><span class="sxs-lookup"><span data-stu-id="ef6fe-177">Tooling support for File storage</span></span>

- [<span data-ttu-id="ef6fe-178">Použití Azure Powershell s Azure Storage</span><span class="sxs-lookup"><span data-stu-id="ef6fe-178">Using Azure PowerShell with Azure Storage</span></span>](https://docs.microsoft.com/azure/storage/storage-powershell-guide-full)
- [<span data-ttu-id="ef6fe-179">Použití nástroje AzCopy s Microsoft Azure Storage</span><span class="sxs-lookup"><span data-stu-id="ef6fe-179">How to use AzCopy with Microsoft Azure Storage</span></span>](https://docs.microsoft.com/azure/storage/storage-use-azcopy)
- [<span data-ttu-id="ef6fe-180">Vytváření, stahování a vytváření objektů BLOB s rozhraním příkazového příkazového příkazu Azure</span><span class="sxs-lookup"><span data-stu-id="ef6fe-180">Create, download, and list blobs with Azure CLI</span></span>](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-cli#create-and-manage-file-shares)

### <a name="reference"></a><span data-ttu-id="ef6fe-181">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ef6fe-181">Reference</span></span>

- [<span data-ttu-id="ef6fe-182">Klientská knihovna úložiště pro odkaz .NET</span><span class="sxs-lookup"><span data-stu-id="ef6fe-182">Storage Client Library for .NET reference</span></span>](https://msdn.microsoft.com/library/azure/mt347887.aspx)
- [<span data-ttu-id="ef6fe-183">REST API služby File – referenční informace</span><span class="sxs-lookup"><span data-stu-id="ef6fe-183">File Service REST API reference</span></span>](/rest/api/storageservices/fileservices/File-Service-REST-API)

### <a name="blog-posts"></a><span data-ttu-id="ef6fe-184">Příspěvky na blozích</span><span class="sxs-lookup"><span data-stu-id="ef6fe-184">Blog posts</span></span>

- [<span data-ttu-id="ef6fe-185">Úložiště Azure File je nyní dostupné pro veřejnost</span><span class="sxs-lookup"><span data-stu-id="ef6fe-185">Azure File storage is now generally available</span></span>](https://azure.microsoft.com/blog/azure-file-storage-now-generally-available/)
- [<span data-ttu-id="ef6fe-186">Uvnitř Azure File Storage</span><span class="sxs-lookup"><span data-stu-id="ef6fe-186">Inside Azure File Storage</span></span>](https://azure.microsoft.com/blog/inside-azure-file-storage/)
- [<span data-ttu-id="ef6fe-187">Představujeme službu Microsoft Azure File</span><span class="sxs-lookup"><span data-stu-id="ef6fe-187">Introducing Microsoft Azure File Service</span></span>](https://docs.microsoft.com/archive/blogs/windowsazurestorage/introducing-microsoft-azure-file-service)
- [<span data-ttu-id="ef6fe-188">Nastavení trvalých připojení k Microsoft Azure Files</span><span class="sxs-lookup"><span data-stu-id="ef6fe-188">Persisting connections to Microsoft Azure Files</span></span>](https://docs.microsoft.com/archive/blogs/windowsazurestorage/persisting-connections-to-microsoft-azure-files)
