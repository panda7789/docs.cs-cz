---
title: 'Postupy: komprese a extrahování souborů'
ms.date: 06/06/2018
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
ms.openlocfilehash: 669936d15cfe1ea125ed36ffdfcfd093b6aacbe1
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46492584"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="505e6-102">Postupy: komprese a extrahování souborů</span><span class="sxs-lookup"><span data-stu-id="505e6-102">How to: Compress and extract files</span></span>

<span data-ttu-id="505e6-103"><xref:System.IO.Compression> Obor názvů obsahuje následující typy pro kompresi a dekompresi souborů a datových proudů.</span><span class="sxs-lookup"><span data-stu-id="505e6-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="505e6-104">Můžete také používat tyto typy číst a upravovat obsah komprimovaného souboru:</span><span class="sxs-lookup"><span data-stu-id="505e6-104">You can also use these types to read and modify the contents of a compressed file:</span></span>

- <xref:System.IO.Compression.ZipFile>

- <xref:System.IO.Compression.ZipArchive>

- <xref:System.IO.Compression.ZipArchiveEntry>

- <xref:System.IO.Compression.DeflateStream>

- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="505e6-105">Následující příklady ukazují některé funkce, které můžete provést při práci s komprimovanými soubory.</span><span class="sxs-lookup"><span data-stu-id="505e6-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>

## <a name="example-1---create-and-extract-a-zip-file"></a><span data-ttu-id="505e6-106">Příklad 1 – vytváření a extrahování souboru ZIP</span><span class="sxs-lookup"><span data-stu-id="505e6-106">Example 1 - Create and extract a .zip file</span></span>

<span data-ttu-id="505e6-107">Následující příklad ukazuje, jak vytvořit a extrahujte komprimovaný soubor, který má příponu názvu souboru .zip s použitím <xref:System.IO.Compression.ZipFile> třídy.</span><span class="sxs-lookup"><span data-stu-id="505e6-107">The following example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="505e6-108">Zkomprimuje obsah složky do nového souboru ZIP a následně extrahuje daný obsah do nové složky.</span><span class="sxs-lookup"><span data-stu-id="505e6-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="505e6-109">Použít <xref:System.IO.Compression.ZipFile> třídy, musí odkazovat `System.IO.Compression.FileSystem` sestavení ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="505e6-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2---extract-specific-file-extensions"></a><span data-ttu-id="505e6-110">Příklad 2 - Extract konkrétní přípony souborů</span><span class="sxs-lookup"><span data-stu-id="505e6-110">Example 2 - Extract specific file extensions</span></span>

<span data-ttu-id="505e6-111">Následující příklad ukazuje, jak k iteraci v rámci obsah k existujícímu souboru ZIP a rozbalit soubory, které mají příponu .txt.</span><span class="sxs-lookup"><span data-stu-id="505e6-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="505e6-112">Používá <xref:System.IO.Compression.ZipArchive> pro přístup k existující soubor .zip a <xref:System.IO.Compression.ZipArchiveEntry> třídy ke kontrole jednotlivých záznamů v komprimovaném souboru.</span><span class="sxs-lookup"><span data-stu-id="505e6-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="505e6-113">Používá metodu rozšíření (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) pro <xref:System.IO.Compression.ZipArchiveEntry> objektu.</span><span class="sxs-lookup"><span data-stu-id="505e6-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="505e6-114">Metoda rozšíření je k dispozici v <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="505e6-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="505e6-115">Použít <xref:System.IO.Compression.ZipFileExtensions> třídy, musí odkazovat `System.IO.Compression.FileSystem` sestavení ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="505e6-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="505e6-116">Při rozzipovávání soubory, musí vyhledat škodlivý soubor cesty, které může uniknout mimo adresáře, ve kterém mají být extrahovány do.</span><span class="sxs-lookup"><span data-stu-id="505e6-116">When unzipping files, you must look for malicious file paths which can escape out of the directory where you want to unzip into.</span></span> <span data-ttu-id="505e6-117">To se označuje jako útok procházení cesty.</span><span class="sxs-lookup"><span data-stu-id="505e6-117">This is known as a path traversal attack.</span></span>

<span data-ttu-id="505e6-118">Následující příklad ukazuje, jak ke kontrole cesty k souboru se škodlivým a poskytuje bezpečný způsob, jak rozbalit:</span><span class="sxs-lookup"><span data-stu-id="505e6-118">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip:</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3---add-a-new-file-to-an-existing-zip-file"></a><span data-ttu-id="505e6-119">Příklad 3 – Přidání nového souboru na existující soubor .zip</span><span class="sxs-lookup"><span data-stu-id="505e6-119">Example 3 - Add a new file to an existing .zip file</span></span>

<span data-ttu-id="505e6-120">V následujícím příkladu <xref:System.IO.Compression.ZipArchive> tříd pro přístup k existující soubor .zip a přidá nový soubor do komprimovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="505e6-120">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="505e6-121">Nový soubor získá komprimované přidáte existující soubor .zip.</span><span class="sxs-lookup"><span data-stu-id="505e6-121">The new file gets compressed when you add it to the existing .zip file.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4---compress-and-decompress-a-directory-of-gz-files"></a><span data-ttu-id="505e6-122">Příklad 4 - komprimovat a dekomprimovat adresář .gz souborů</span><span class="sxs-lookup"><span data-stu-id="505e6-122">Example 4 - Compress and decompress a directory of .gz files</span></span>

<span data-ttu-id="505e6-123">Můžete také použít <xref:System.IO.Compression.GZipStream> a <xref:System.IO.Compression.DeflateStream> třídy při komprimaci a dekomprimaci dat.</span><span class="sxs-lookup"><span data-stu-id="505e6-123">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="505e6-124">Používají stejný algoritmus komprese.</span><span class="sxs-lookup"><span data-stu-id="505e6-124">They use the same compression algorithm.</span></span> <span data-ttu-id="505e6-125">Komprimované <xref:System.IO.Compression.GZipStream> objekty, které jsou zapsány do souboru s příponou .gz můžete s použitím mnoha běžných nástrojů kromě metod poskytovaných parametrem dekomprimovat <xref:System.IO.Compression.GZipStream>.</span><span class="sxs-lookup"><span data-stu-id="505e6-125">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="505e6-126">Následující příklad ukazuje, jak při komprimaci a dekomprimaci adresář souborů pomocí <xref:System.IO.Compression.GZipStream> třídy:</span><span class="sxs-lookup"><span data-stu-id="505e6-126">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="505e6-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="505e6-127">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="505e6-128">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="505e6-128">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
