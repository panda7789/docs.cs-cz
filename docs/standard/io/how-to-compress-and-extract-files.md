---
title: 'Postupy: Komprimování a extrahování souborů'
ms.date: 03/30/2017
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
ms.openlocfilehash: f3e535e13fe91e1a5cb9c868428f5edbb9eac03f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-compress-and-extract-files"></a>Postupy: Komprimování a extrahování souborů
<xref:System.IO.Compression> Obor názvů obsahuje následující typy komprese a dekomprese souborů a datových proudů. Můžete také používat tyto typy číst a upravovat obsah komprimovaný soubor:  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 Následující příklady ukazují, některé funkce, které můžete provádět při práci s komprimovaných souborů.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak vytvořit a extrahovat komprimovaný soubor, který má příponu názvu souboru .zip pomocí <xref:System.IO.Compression.ZipFile> třídy. Ho zkomprimuje obsah složky do nového souboru .zip a pak extrahuje daný obsah do nové složky. Použít <xref:System.IO.Compression.ZipFile> třídu, musí odkazovat `System.IO.Compression.FileSystem` sestavení ve vašem projektu.  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a>Příklad  
 Další příklad ukazuje, jak k iteraci v rámci obsah existující soubor .zip a extrahujte soubory, které mají příponu .txt. Použije <xref:System.IO.Compression.ZipArchive> třídy pro přístup k existující soubor .zip a <xref:System.IO.Compression.ZipArchiveEntry> třídy Zkontrolujte jednotlivé položky v komprimovaném souboru. Používá metody rozšíření (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) pro <xref:System.IO.Compression.ZipArchiveEntry> objektu. Je k dispozici v metodě rozšíření <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> třídy. Použít <xref:System.IO.Compression.ZipFileExtensions> třídu, musí odkazovat `System.IO.Compression.FileSystem` sestavení ve vašem projektu.  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a>Příklad  
 Další příklad používá <xref:System.IO.Compression.ZipArchive> třídy pro přístup k existující soubor .zip a přidá nový soubor do zkomprimovaného souboru. Nový soubor získá komprimovány ho přidáte do existující soubor .zip.  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a>Příklad  
 Můžete také <xref:System.IO.Compression.GZipStream> a <xref:System.IO.Compression.DeflateStream> třídy při komprimaci a dekomprimaci dat. Používají stejnou algoritmus komprese. Komprimované <xref:System.IO.Compression.GZipStream> objekty, které se zapisují do souboru, který má příponu .gz můžete dekomprimovat pomocí celou řadu běžných nástrojů kromě metod od <xref:System.IO.Compression.GZipStream>. Tento příklad ukazuje, jak při komprimaci a dekomprimaci adresář souborů pomocí <xref:System.IO.Compression.GZipStream> třídy.  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)
