---
title: 'Postupy: komprimace a extrakce souborů'
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
ms.openlocfilehash: 28f9a0baa73f58b0a5c7f93a4b0b3ece3b87c3a5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288560"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="b5dfe-102">Postupy: komprimace a extrakce souborů</span><span class="sxs-lookup"><span data-stu-id="b5dfe-102">How to: Compress and extract files</span></span>

<span data-ttu-id="b5dfe-103"><xref:System.IO.Compression>Obor názvů obsahuje následující typy pro komprimaci a dekompresi souborů a datových proudů.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="b5dfe-104">Tyto typy můžete použít také ke čtení a úpravám obsahu komprimovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-104">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="b5dfe-105">Následující příklady znázorňují některé operace, které můžete provádět s komprimovanými soubory.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-105">The following examples show some of the operations you can perform with compressed files.</span></span> <span data-ttu-id="b5dfe-106">Tyto příklady vyžadují, aby byly do projektu přidány následující balíčky NuGet:</span><span class="sxs-lookup"><span data-stu-id="b5dfe-106">These examples require the following NuGet packages to be added to your project:</span></span>

- [<span data-ttu-id="b5dfe-107">System. IO. Compression</span><span class="sxs-lookup"><span data-stu-id="b5dfe-107">System.IO.Compression</span></span>](https://www.nuget.org/packages/System.IO.Compression)
- [<span data-ttu-id="b5dfe-108">System. IO. Compression. podřízený ZipFile</span><span class="sxs-lookup"><span data-stu-id="b5dfe-108">System.IO.Compression.ZipFile</span></span>](https://www.nuget.org/packages/System.IO.Compression.ZipFile)

<span data-ttu-id="b5dfe-109">Pokud používáte .NET Framework, přidejte do projektu odkazy na tyto dvě knihovny:</span><span class="sxs-lookup"><span data-stu-id="b5dfe-109">If you're using .NET Framework, add references to these two libraries to your project:</span></span>

- `System.IO.Compression`
- `System.IO.Compression.FileSystem`

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="b5dfe-110">Příklad 1: vytvoření a extrakce souboru. zip</span><span class="sxs-lookup"><span data-stu-id="b5dfe-110">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="b5dfe-111">Následující příklad ukazuje, jak vytvořit a extrahovat komprimovaný soubor s *příponou. zip* pomocí <xref:System.IO.Compression.ZipFile> třídy.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-111">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="b5dfe-112">V příkladu se komprimuje obsah složky do nového souboru *. zip* a pak se vyextrahuje soubor zip do nové složky.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-112">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span>

<span data-ttu-id="b5dfe-113">Ukázku spustíte tak, že ve složce programu vytvoříte složku *Start* a naplníte ji soubory do souboru ZIP.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-113">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="b5dfe-114">Příklad 2: extrakce konkrétních přípon souborů</span><span class="sxs-lookup"><span data-stu-id="b5dfe-114">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="b5dfe-115">Následující příklad prochází obsah existujícího souboru *zip* a extrahuje soubory, které mají příponu *. txt* .</span><span class="sxs-lookup"><span data-stu-id="b5dfe-115">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="b5dfe-116">Používá <xref:System.IO.Compression.ZipArchive> třídu pro přístup k souboru zip a <xref:System.IO.Compression.ZipArchiveEntry> třídu pro kontrolu jednotlivých položek.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-116">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="b5dfe-117">Metoda rozšíření <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> pro <xref:System.IO.Compression.ZipArchiveEntry> objekt je k dispozici ve <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> třídě.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-117">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="b5dfe-118">Ukázku spustíte tak, že ve složce programu umístíte soubor *. zip* s názvem *Result. zip* .</span><span class="sxs-lookup"><span data-stu-id="b5dfe-118">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="b5dfe-119">Po zobrazení výzvy zadejte název složky, do které se má extrahovat.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-119">When prompted, provide a folder name to extract to.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5dfe-120">V případě souborů rozzipovává je nutné vyhledat cesty ke škodlivým souborům, které mohou uniknout z adresáře, do kterého jste extrahováni.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-120">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="b5dfe-121">To se označuje jako útok pomocí cesty.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-121">This is known as a path traversal attack.</span></span> <span data-ttu-id="b5dfe-122">Následující příklad ukazuje, jak kontrolovat škodlivé cesty k souborům a poskytuje bezpečný způsob, jak je rozbalit.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-122">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="b5dfe-123">Příklad 3: Přidání souboru do existujícího souboru ZIP</span><span class="sxs-lookup"><span data-stu-id="b5dfe-123">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="b5dfe-124">Následující příklad používá <xref:System.IO.Compression.ZipArchive> třídu pro přístup k existujícímu souboru *. zip* a přidává do něj soubor.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-124">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="b5dfe-125">Nový soubor se komprimuje, když ho přidáte do existujícího souboru ZIP.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-125">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="b5dfe-126">Příklad 4: komprimace a dekomprese souborů GZ</span><span class="sxs-lookup"><span data-stu-id="b5dfe-126">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="b5dfe-127">Můžete také použít <xref:System.IO.Compression.GZipStream> <xref:System.IO.Compression.DeflateStream> třídy a pro komprimaci a dekomprimaci dat.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-127">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="b5dfe-128">Používají stejný kompresní algoritmus.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-128">They use the same compression algorithm.</span></span> <span data-ttu-id="b5dfe-129">Můžete dekomprimovat <xref:System.IO.Compression.GZipStream> objekty, které jsou zapsány do souboru *. gz* pomocí mnoha běžných nástrojů.</span><span class="sxs-lookup"><span data-stu-id="b5dfe-129">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="b5dfe-130">Následující příklad ukazuje, jak komprimovat a dekomprimovat adresář souborů pomocí <xref:System.IO.Compression.GZipStream> třídy:</span><span class="sxs-lookup"><span data-stu-id="b5dfe-130">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="b5dfe-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b5dfe-131">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="b5dfe-132">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="b5dfe-132">File and stream I/O</span></span>](index.md)
