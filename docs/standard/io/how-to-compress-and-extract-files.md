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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61752031"
---
# <a name="how-to-compress-and-extract-files"></a>Postupy: Komprese a extrahování souborů

<xref:System.IO.Compression> Obor názvů obsahuje následující typy pro kompresi a dekompresi souborů a datových proudů. Můžete také používat tyto typy číst a upravovat obsah komprimovaného souboru.

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

Následující příklady ukazují některé operace, které můžete provádět pomocí komprimované soubory.

## <a name="example-1-create-and-extract-a-zip-file"></a>Příklad 1: Vytváření a extrahování souboru ZIP

Následující příklad ukazuje, jak vytvořit a extrahujte komprimovaný *ZIP* souboru s použitím <xref:System.IO.Compression.ZipFile> třídy. V příkladu zkomprimuje obsah složky do nového *ZIP* souboru a poté rozbalí zip do nové složky. 

Ke spuštění ukázky vytvořit *start* ve složce programu a přidejte do ní soubory zip. 

Pokud se zobrazí chyby sestavení "Název 'ZipFile' neexistuje v aktuálním kontextu" Přidat odkaz na `System.IO.Compression.FileSystem` sestavení do projektu.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a>Příklad 2: Extrahovat konkrétní přípony souborů

Následující příklad provede iteraci obsah existujícího *ZIP* souboru a extrahuje soubory, které mají *.txt* rozšíření. Používá <xref:System.IO.Compression.ZipArchive> pro přístup k souboru zip a <xref:System.IO.Compression.ZipArchiveEntry> třídy ke kontrole jednotlivé položky. Metoda rozšíření <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> pro <xref:System.IO.Compression.ZipArchiveEntry> je k dispozici v objektu <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> třídy. 

Ke spuštění ukázky, umístěte *ZIP* soubor s názvem *result.zip* ve složce program. Po zobrazení výzvy zadejte název složky extrahujte do. 

Pokud se zobrazí chyby sestavení "Název 'ZipFile' neexistuje v aktuálním kontextu" Přidat odkaz na `System.IO.Compression.FileSystem` sestavení do projektu.

Pokud se zobrazí chyba "Typ"ZipArchive"je definovaný v sestavení, které se neodkazuje" Přidat odkaz na `System.IO.Compression` sestavení do projektu. 

> [!IMPORTANT]
> Při rozzipovávání soubory, musí vyhledat škodlivý soubor cesty, které může uniknout mimo adresář, který rozbalte do. To se označuje jako útok procházení cesty. Následující příklad ukazuje, jak ke kontrole cesty k souboru se škodlivým a poskytuje bezpečný způsob, jak rozbalit.

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a>Příklad 3: Přidejte soubor do existující zip

V následujícím příkladu <xref:System.IO.Compression.ZipArchive> pro přístup k existující *ZIP* soubor a přidá soubor do něj. Nový soubor získá komprimovaný, když přidáte do existujícího souboru zip.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a>Příklad 4: Komprimovat a dekomprimovat soubory .gz

Můžete také použít <xref:System.IO.Compression.GZipStream> a <xref:System.IO.Compression.DeflateStream> třídy při komprimaci a dekomprimaci dat. Používají stejný algoritmus komprese. Můžete dekomprimovat <xref:System.IO.Compression.GZipStream> objekty, které jsou zapsány do *.gz* souboru s použitím mnoha běžných nástrojů. Následující příklad ukazuje, jak při komprimaci a dekomprimaci adresář souborů pomocí <xref:System.IO.Compression.GZipStream> třídy:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Viz také:

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [Vstupně-výstupních operací souborů a datových proudů](../../../docs/standard/io/index.md)
