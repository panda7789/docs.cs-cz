---
title: 'Postupy: Komprese a extrahování souborů'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a4ea4c32f5b73b283a5982f16e55a4d078171c1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55255000"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="88e54-102">Postupy: Komprese a extrahování souborů</span><span class="sxs-lookup"><span data-stu-id="88e54-102">How to: Compress and extract files</span></span>

<span data-ttu-id="88e54-103"><xref:System.IO.Compression> Obor názvů obsahuje následující typy pro kompresi a dekompresi souborů a datových proudů.</span><span class="sxs-lookup"><span data-stu-id="88e54-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="88e54-104">Můžete také používat tyto typy číst a upravovat obsah komprimovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="88e54-104">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="88e54-105">Následující příklady ukazují některé operace, které můžete provádět pomocí komprimované soubory.</span><span class="sxs-lookup"><span data-stu-id="88e54-105">The following examples show some of the operations you can perform with compressed files.</span></span>

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="88e54-106">Příklad 1: Vytváření a extrahování souboru ZIP</span><span class="sxs-lookup"><span data-stu-id="88e54-106">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="88e54-107">Následující příklad ukazuje, jak vytvořit a extrahujte komprimovaný *ZIP* souboru s použitím <xref:System.IO.Compression.ZipFile> třídy.</span><span class="sxs-lookup"><span data-stu-id="88e54-107">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="88e54-108">V příkladu zkomprimuje obsah složky do nového *ZIP* souboru a poté rozbalí zip do nové složky.</span><span class="sxs-lookup"><span data-stu-id="88e54-108">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span> 

<span data-ttu-id="88e54-109">Ke spuštění ukázky vytvořit *start* ve složce programu a přidejte do ní soubory zip.</span><span class="sxs-lookup"><span data-stu-id="88e54-109">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span> 

<span data-ttu-id="88e54-110">Pokud se zobrazí chyby sestavení "Název 'ZipFile' neexistuje v aktuálním kontextu" Přidat odkaz na `System.IO.Compression.FileSystem` sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="88e54-110">If you get the build error "The name 'ZipFile' does not exist in the current context," add a reference to the `System.IO.Compression.FileSystem` assembly to your project.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="88e54-111">Příklad 2: Extrahovat konkrétní přípony souborů</span><span class="sxs-lookup"><span data-stu-id="88e54-111">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="88e54-112">Následující příklad provede iteraci obsah existujícího *ZIP* souboru a extrahuje soubory, které mají *.txt* rozšíření.</span><span class="sxs-lookup"><span data-stu-id="88e54-112">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="88e54-113">Používá <xref:System.IO.Compression.ZipArchive> pro přístup k souboru zip a <xref:System.IO.Compression.ZipArchiveEntry> třídy ke kontrole jednotlivé položky.</span><span class="sxs-lookup"><span data-stu-id="88e54-113">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="88e54-114">Metoda rozšíření <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> pro <xref:System.IO.Compression.ZipArchiveEntry> je k dispozici v objektu <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="88e54-114">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> 

<span data-ttu-id="88e54-115">Ke spuštění ukázky, umístěte *ZIP* soubor s názvem *result.zip* ve složce program.</span><span class="sxs-lookup"><span data-stu-id="88e54-115">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="88e54-116">Po zobrazení výzvy zadejte název složky extrahujte do.</span><span class="sxs-lookup"><span data-stu-id="88e54-116">When prompted, provide a folder name to extract to.</span></span> 

<span data-ttu-id="88e54-117">Pokud se zobrazí chyby sestavení "Název 'ZipFile' neexistuje v aktuálním kontextu" Přidat odkaz na `System.IO.Compression.FileSystem` sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="88e54-117">If you get the build error "The name 'ZipFile' does not exist in the current context," add a reference to the `System.IO.Compression.FileSystem` assembly to your project.</span></span>

<span data-ttu-id="88e54-118">Pokud se zobrazí chyba "Typ"ZipArchive"je definovaný v sestavení, které se neodkazuje" Přidat odkaz na `System.IO.Compression` sestavení do projektu.</span><span class="sxs-lookup"><span data-stu-id="88e54-118">If you get the error "The type 'ZipArchive' is defined in an assembly that is not referenced," add a reference to the `System.IO.Compression` assembly to your project.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="88e54-119">Při rozzipovávání soubory, musí vyhledat škodlivý soubor cesty, které může uniknout mimo adresář, který rozbalte do.</span><span class="sxs-lookup"><span data-stu-id="88e54-119">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="88e54-120">To se označuje jako útok procházení cesty.</span><span class="sxs-lookup"><span data-stu-id="88e54-120">This is known as a path traversal attack.</span></span> <span data-ttu-id="88e54-121">Následující příklad ukazuje, jak ke kontrole cesty k souboru se škodlivým a poskytuje bezpečný způsob, jak rozbalit.</span><span class="sxs-lookup"><span data-stu-id="88e54-121">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="88e54-122">Příklad 3: Přidejte soubor do existující zip</span><span class="sxs-lookup"><span data-stu-id="88e54-122">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="88e54-123">V následujícím příkladu <xref:System.IO.Compression.ZipArchive> pro přístup k existující *ZIP* soubor a přidá soubor do něj.</span><span class="sxs-lookup"><span data-stu-id="88e54-123">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="88e54-124">Nový soubor získá komprimovaný, když přidáte do existujícího souboru zip.</span><span class="sxs-lookup"><span data-stu-id="88e54-124">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="88e54-125">Příklad 4: Komprimovat a dekomprimovat soubory .gz</span><span class="sxs-lookup"><span data-stu-id="88e54-125">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="88e54-126">Můžete také použít <xref:System.IO.Compression.GZipStream> a <xref:System.IO.Compression.DeflateStream> třídy při komprimaci a dekomprimaci dat.</span><span class="sxs-lookup"><span data-stu-id="88e54-126">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="88e54-127">Používají stejný algoritmus komprese.</span><span class="sxs-lookup"><span data-stu-id="88e54-127">They use the same compression algorithm.</span></span> <span data-ttu-id="88e54-128">Můžete dekomprimovat <xref:System.IO.Compression.GZipStream> objekty, které jsou zapsány do *.gz* souboru s použitím mnoha běžných nástrojů.</span><span class="sxs-lookup"><span data-stu-id="88e54-128">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="88e54-129">Následující příklad ukazuje, jak při komprimaci a dekomprimaci adresář souborů pomocí <xref:System.IO.Compression.GZipStream> třídy:</span><span class="sxs-lookup"><span data-stu-id="88e54-129">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="88e54-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88e54-130">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="88e54-131">Vstupně-výstupních operací souborů a datových proudů</span><span class="sxs-lookup"><span data-stu-id="88e54-131">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
