---
title: 'Postupy: komprimace a extrakce souborů'
description: Komprimovat & extrahuje soubory pomocí System. IO. Compression. Podívejte se na příklady použití podřízený ZipFile, ZipArchive, ZipArchiveEntry, DeflateStream & GZipStream.
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
ms.openlocfilehash: c13f464432aa6f67136d3a844bdeda256e7ab9b6
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769233"
---
# <a name="how-to-compress-and-extract-files"></a>Postupy: komprimace a extrakce souborů

<xref:System.IO.Compression>Obor názvů obsahuje následující typy pro komprimaci a dekompresi souborů a datových proudů. Tyto typy můžete použít také ke čtení a úpravám obsahu komprimovaného souboru.

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

Následující příklady znázorňují některé operace, které můžete provádět s komprimovanými soubory. Tyto příklady vyžadují, aby byly do projektu přidány následující balíčky NuGet:

- [System. IO. Compression](https://www.nuget.org/packages/System.IO.Compression)
- [SouborSystem.IO.Compression.Zip](https://www.nuget.org/packages/System.IO.Compression.ZipFile)

Pokud používáte .NET Framework, přidejte do projektu odkazy na tyto dvě knihovny:

- `System.IO.Compression`
- `System.IO.Compression.FileSystem`

## <a name="example-1-create-and-extract-a-zip-file"></a>Příklad 1: vytvoření a extrakce souboru. zip

Následující příklad ukazuje, jak vytvořit a extrahovat komprimovaný soubor s *příponou. zip* pomocí <xref:System.IO.Compression.ZipFile> třídy. V příkladu se komprimuje obsah složky do nového souboru *. zip* a pak se vyextrahuje soubor zip do nové složky.

Ukázku spustíte tak, že ve složce programu vytvoříte složku *Start* a naplníte ji soubory do souboru ZIP.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a>Příklad 2: extrakce konkrétních přípon souborů

Následující příklad prochází obsah existujícího souboru *zip* a extrahuje soubory, které mají příponu *. txt* . Používá <xref:System.IO.Compression.ZipArchive> třídu pro přístup k souboru zip a <xref:System.IO.Compression.ZipArchiveEntry> třídu pro kontrolu jednotlivých položek. Metoda rozšíření <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> pro <xref:System.IO.Compression.ZipArchiveEntry> objekt je k dispozici ve <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> třídě.

Ukázku spustíte tak, že ve složce programu umístíte soubor *. zip* s názvem *result.zip* . Po zobrazení výzvy zadejte název složky, do které se má extrahovat.

> [!IMPORTANT]
> V případě souborů rozzipovává je nutné vyhledat cesty ke škodlivým souborům, které mohou uniknout z adresáře, do kterého jste extrahováni. To se označuje jako útok pomocí cesty. Následující příklad ukazuje, jak kontrolovat škodlivé cesty k souborům a poskytuje bezpečný způsob, jak je rozbalit.

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a>Příklad 3: Přidání souboru do existujícího souboru ZIP

Následující příklad používá <xref:System.IO.Compression.ZipArchive> třídu pro přístup k existujícímu souboru *. zip* a přidává do něj soubor. Nový soubor se komprimuje, když ho přidáte do existujícího souboru ZIP.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a>Příklad 4: komprimace a dekomprese souborů GZ

Můžete také použít <xref:System.IO.Compression.GZipStream> <xref:System.IO.Compression.DeflateStream> třídy a pro komprimaci a dekomprimaci dat. Používají stejný kompresní algoritmus. Můžete dekomprimovat <xref:System.IO.Compression.GZipStream> objekty, které jsou zapsány do souboru *. gz* pomocí mnoha běžných nástrojů. Následující příklad ukazuje, jak komprimovat a dekomprimovat adresář souborů pomocí <xref:System.IO.Compression.GZipStream> třídy:

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Viz také

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [Vstup/výstup souborů a streamů](index.md)
