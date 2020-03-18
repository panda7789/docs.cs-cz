---
title: 'Postup: Komprese a extrahování souborů'
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
ms.openlocfilehash: 5aa25e265ed6ffb613e9916414c6f2335a4aaf57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159374"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="080bc-102">Postup: Komprese a extrahování souborů</span><span class="sxs-lookup"><span data-stu-id="080bc-102">How to: Compress and extract files</span></span>

<span data-ttu-id="080bc-103">Obor <xref:System.IO.Compression> názvů obsahuje následující typy pro kompresi a dekompresi souborů a datových proudů.</span><span class="sxs-lookup"><span data-stu-id="080bc-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="080bc-104">Tyto typy můžete také použít ke čtení a úpravám obsahu komprimovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="080bc-104">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="080bc-105">Následující příklady ukazují některé operace, které lze provádět s komprimovanými soubory.</span><span class="sxs-lookup"><span data-stu-id="080bc-105">The following examples show some of the operations you can perform with compressed files.</span></span>

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="080bc-106">Příklad 1: Vytvoření a extrahování souboru ZIP</span><span class="sxs-lookup"><span data-stu-id="080bc-106">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="080bc-107">Následující příklad ukazuje, jak vytvořit a extrahovat komprimovaný soubor *ZIP* pomocí <xref:System.IO.Compression.ZipFile> třídy.</span><span class="sxs-lookup"><span data-stu-id="080bc-107">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="080bc-108">Příklad komprimuje obsah složky do nového souboru *ZIP* a potom extrahuje soubor ZIP do nové složky.</span><span class="sxs-lookup"><span data-stu-id="080bc-108">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span>

<span data-ttu-id="080bc-109">Chcete-li spustit ukázku, vytvořte *počáteční* složku ve složce programu a naplňte ji soubory, které chcete zip.</span><span class="sxs-lookup"><span data-stu-id="080bc-109">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span>

<span data-ttu-id="080bc-110">Pokud se zobrazí chyba sestavení "Název ZipFile' neexistuje v aktuálním kontextu," `System.IO.Compression.FileSystem` přidejte odkaz na sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="080bc-110">If you get the build error "The name 'ZipFile' does not exist in the current context," add a reference to the `System.IO.Compression.FileSystem` assembly to your project.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="080bc-111">Příklad 2: Extrahovat konkrétní přípony souborů</span><span class="sxs-lookup"><span data-stu-id="080bc-111">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="080bc-112">Další příklad itetuje obsah existujícího souboru *ZIP* a extrahuje soubory, které mají příponu *TXT.*</span><span class="sxs-lookup"><span data-stu-id="080bc-112">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="080bc-113">Používá třídu <xref:System.IO.Compression.ZipArchive> pro přístup k <xref:System.IO.Compression.ZipArchiveEntry> zip a třídy ke kontrole jednotlivých položek.</span><span class="sxs-lookup"><span data-stu-id="080bc-113">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="080bc-114">Metoda <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> rozšíření pro <xref:System.IO.Compression.ZipArchiveEntry> objekt je <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> k dispozici ve třídě.</span><span class="sxs-lookup"><span data-stu-id="080bc-114">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="080bc-115">Chcete-li vzorek spustit, umístěte soubor *ZIP* s názvem *result.zip* do složky programu.</span><span class="sxs-lookup"><span data-stu-id="080bc-115">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="080bc-116">Po zobrazení výzvy zadejte název složky, do které chcete extrahovat.</span><span class="sxs-lookup"><span data-stu-id="080bc-116">When prompted, provide a folder name to extract to.</span></span>

<span data-ttu-id="080bc-117">Pokud se zobrazí chyba sestavení "Název ZipFile' neexistuje v aktuálním kontextu," `System.IO.Compression.FileSystem` přidejte odkaz na sestavení projektu.</span><span class="sxs-lookup"><span data-stu-id="080bc-117">If you get the build error "The name 'ZipFile' does not exist in the current context," add a reference to the `System.IO.Compression.FileSystem` assembly to your project.</span></span>

<span data-ttu-id="080bc-118">Pokud se zobrazí chyba "Typ ZipArchive' je definován v sestavení, které není `System.IO.Compression` odkazováno," přidejte odkaz na sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="080bc-118">If you get the error "The type 'ZipArchive' is defined in an assembly that is not referenced," add a reference to the `System.IO.Compression` assembly to your project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="080bc-119">Při rozbalení souborů je nutné vyhledat škodlivé cesty k souborům, které mohou uniknout z adresáře, do kterého rozbalíte.</span><span class="sxs-lookup"><span data-stu-id="080bc-119">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="080bc-120">To se označuje jako cesta traversal útoku.</span><span class="sxs-lookup"><span data-stu-id="080bc-120">This is known as a path traversal attack.</span></span> <span data-ttu-id="080bc-121">Následující příklad ukazuje, jak zkontrolovat cesty škodlivého souboru a poskytuje bezpečný způsob, jak rozbalit.</span><span class="sxs-lookup"><span data-stu-id="080bc-121">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="080bc-122">Příklad 3: Přidání souboru do existujícího zipu</span><span class="sxs-lookup"><span data-stu-id="080bc-122">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="080bc-123">Následující příklad používá <xref:System.IO.Compression.ZipArchive> třídu pro přístup k existujícímu souboru *ZIP* a přidá k němu soubor.</span><span class="sxs-lookup"><span data-stu-id="080bc-123">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="080bc-124">Nový soubor získá komprimované při přidání do existujícího zip.</span><span class="sxs-lookup"><span data-stu-id="080bc-124">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="080bc-125">Příklad 4: Komprese a dekomprese souborů GZ</span><span class="sxs-lookup"><span data-stu-id="080bc-125">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="080bc-126">Třídy <xref:System.IO.Compression.GZipStream> a <xref:System.IO.Compression.DeflateStream> můžete také použít ke kompresi a dekompresi dat.</span><span class="sxs-lookup"><span data-stu-id="080bc-126">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="080bc-127">Používají stejný kompresní algoritmus.</span><span class="sxs-lookup"><span data-stu-id="080bc-127">They use the same compression algorithm.</span></span> <span data-ttu-id="080bc-128">Objekty, <xref:System.IO.Compression.GZipStream> které jsou zapsány do souboru *GZ,* můžete dekomprimovat pomocí mnoha běžných nástrojů.</span><span class="sxs-lookup"><span data-stu-id="080bc-128">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="080bc-129">Následující příklad ukazuje, jak komprimovat a dekomprimovat adresář souborů pomocí třídy: <xref:System.IO.Compression.GZipStream></span><span class="sxs-lookup"><span data-stu-id="080bc-129">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="080bc-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="080bc-130">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="080bc-131">Vstupně-tono-videa</span><span class="sxs-lookup"><span data-stu-id="080bc-131">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
