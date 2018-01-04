---
title: "Postupy: Komprimování a extrahování souborů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 33c9249692998aea8c22ddbf75a5a9b7bdf28708
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="9429b-102">Postupy: Komprimování a extrahování souborů</span><span class="sxs-lookup"><span data-stu-id="9429b-102">How to: Compress and Extract Files</span></span>
<span data-ttu-id="9429b-103"><xref:System.IO.Compression> Obor názvů obsahuje následující typy komprese a dekomprese souborů a datových proudů.</span><span class="sxs-lookup"><span data-stu-id="9429b-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="9429b-104">Můžete také používat tyto typy číst a upravovat obsah komprimovaný soubor:</span><span class="sxs-lookup"><span data-stu-id="9429b-104">You can also use these types to read and modify the contents of a compressed file:</span></span>  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 <span data-ttu-id="9429b-105">Následující příklady ukazují, některé funkce, které můžete provádět při práci s komprimovaných souborů.</span><span class="sxs-lookup"><span data-stu-id="9429b-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9429b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="9429b-106">Example</span></span>  
 <span data-ttu-id="9429b-107">Tento příklad ukazuje, jak vytvořit a extrahovat komprimovaný soubor, který má příponu názvu souboru .zip pomocí <xref:System.IO.Compression.ZipFile> třídy.</span><span class="sxs-lookup"><span data-stu-id="9429b-107">This example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="9429b-108">Ho zkomprimuje obsah složky do nového souboru .zip a pak extrahuje daný obsah do nové složky.</span><span class="sxs-lookup"><span data-stu-id="9429b-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="9429b-109">Použít <xref:System.IO.Compression.ZipFile> třídu, musí odkazovat `System.IO.Compression.FileSystem` sestavení ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="9429b-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="9429b-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="9429b-110">Example</span></span>  
 <span data-ttu-id="9429b-111">Další příklad ukazuje, jak k iteraci v rámci obsah existující soubor .zip a extrahujte soubory, které mají příponu .txt.</span><span class="sxs-lookup"><span data-stu-id="9429b-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="9429b-112">Použije <xref:System.IO.Compression.ZipArchive> třídy pro přístup k existující soubor .zip a <xref:System.IO.Compression.ZipArchiveEntry> třídy Zkontrolujte jednotlivé položky v komprimovaném souboru.</span><span class="sxs-lookup"><span data-stu-id="9429b-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="9429b-113">Používá metody rozšíření (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) pro <xref:System.IO.Compression.ZipArchiveEntry> objektu.</span><span class="sxs-lookup"><span data-stu-id="9429b-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="9429b-114">Je k dispozici v metodě rozšíření <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="9429b-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="9429b-115">Použít <xref:System.IO.Compression.ZipFileExtensions> třídu, musí odkazovat `System.IO.Compression.FileSystem` sestavení ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="9429b-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="9429b-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="9429b-116">Example</span></span>  
 <span data-ttu-id="9429b-117">Další příklad používá <xref:System.IO.Compression.ZipArchive> třídy pro přístup k existující soubor .zip a přidá nový soubor do zkomprimovaného souboru.</span><span class="sxs-lookup"><span data-stu-id="9429b-117">The next example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="9429b-118">Nový soubor získá komprimovány ho přidáte do existující soubor .zip.</span><span class="sxs-lookup"><span data-stu-id="9429b-118">The new file gets compressed when you add it to the existing .zip file.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="9429b-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="9429b-119">Example</span></span>  
 <span data-ttu-id="9429b-120">Můžete také <xref:System.IO.Compression.GZipStream> a <xref:System.IO.Compression.DeflateStream> třídy při komprimaci a dekomprimaci dat.</span><span class="sxs-lookup"><span data-stu-id="9429b-120">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="9429b-121">Používají stejnou algoritmus komprese.</span><span class="sxs-lookup"><span data-stu-id="9429b-121">They use the same compression algorithm.</span></span> <span data-ttu-id="9429b-122">Komprimované <xref:System.IO.Compression.GZipStream> objekty, které se zapisují do souboru, který má příponu .gz můžete dekomprimovat pomocí celou řadu běžných nástrojů kromě metod od <xref:System.IO.Compression.GZipStream>.</span><span class="sxs-lookup"><span data-stu-id="9429b-122">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="9429b-123">Tento příklad ukazuje, jak při komprimaci a dekomprimaci adresář souborů pomocí <xref:System.IO.Compression.GZipStream> třídy.</span><span class="sxs-lookup"><span data-stu-id="9429b-123">This example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class.</span></span>  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9429b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="9429b-124">See Also</span></span>  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [<span data-ttu-id="9429b-125">Souborová služba a datový proud I-O</span><span class="sxs-lookup"><span data-stu-id="9429b-125">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
