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
# <a name="how-to-compress-and-extract-files"></a>Postupy: komprese a extrahování souborů

<xref:System.IO.Compression> Obor názvů obsahuje následující typy pro kompresi a dekompresi souborů a datových proudů. Můžete také používat tyto typy číst a upravovat obsah komprimovaného souboru:

- <xref:System.IO.Compression.ZipFile>

- <xref:System.IO.Compression.ZipArchive>

- <xref:System.IO.Compression.ZipArchiveEntry>

- <xref:System.IO.Compression.DeflateStream>

- <xref:System.IO.Compression.GZipStream>

Následující příklady ukazují některé funkce, které můžete provést při práci s komprimovanými soubory.

## <a name="example-1---create-and-extract-a-zip-file"></a>Příklad 1 – vytváření a extrahování souboru ZIP

Následující příklad ukazuje, jak vytvořit a extrahujte komprimovaný soubor, který má příponu názvu souboru .zip s použitím <xref:System.IO.Compression.ZipFile> třídy. Zkomprimuje obsah složky do nového souboru ZIP a následně extrahuje daný obsah do nové složky. Použít <xref:System.IO.Compression.ZipFile> třídy, musí odkazovat `System.IO.Compression.FileSystem` sestavení ve vašem projektu.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2---extract-specific-file-extensions"></a>Příklad 2 - Extract konkrétní přípony souborů

Následující příklad ukazuje, jak k iteraci v rámci obsah k existujícímu souboru ZIP a rozbalit soubory, které mají příponu .txt. Používá <xref:System.IO.Compression.ZipArchive> pro přístup k existující soubor .zip a <xref:System.IO.Compression.ZipArchiveEntry> třídy ke kontrole jednotlivých záznamů v komprimovaném souboru. Používá metodu rozšíření (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) pro <xref:System.IO.Compression.ZipArchiveEntry> objektu. Metoda rozšíření je k dispozici v <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> třídy. Použít <xref:System.IO.Compression.ZipFileExtensions> třídy, musí odkazovat `System.IO.Compression.FileSystem` sestavení ve vašem projektu.

> [!IMPORTANT]
> Při rozzipovávání soubory, musí vyhledat škodlivý soubor cesty, které může uniknout mimo adresáře, ve kterém mají být extrahovány do. To se označuje jako útok procházení cesty.

Následující příklad ukazuje, jak ke kontrole cesty k souboru se škodlivým a poskytuje bezpečný způsob, jak rozbalit:

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3---add-a-new-file-to-an-existing-zip-file"></a>Příklad 3 – Přidání nového souboru na existující soubor .zip

V následujícím příkladu <xref:System.IO.Compression.ZipArchive> tříd pro přístup k existující soubor .zip a přidá nový soubor do komprimovaného souboru. Nový soubor získá komprimované přidáte existující soubor .zip.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4---compress-and-decompress-a-directory-of-gz-files"></a>Příklad 4 - komprimovat a dekomprimovat adresář .gz souborů

Můžete také použít <xref:System.IO.Compression.GZipStream> a <xref:System.IO.Compression.DeflateStream> třídy při komprimaci a dekomprimaci dat. Používají stejný algoritmus komprese. Komprimované <xref:System.IO.Compression.GZipStream> objekty, které jsou zapsány do souboru s příponou .gz můžete s použitím mnoha běžných nástrojů kromě metod poskytovaných parametrem dekomprimovat <xref:System.IO.Compression.GZipStream>. Následující příklad ukazuje, jak při komprimaci a dekomprimaci adresář souborů pomocí <xref:System.IO.Compression.GZipStream> třídy:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Viz také:

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)
