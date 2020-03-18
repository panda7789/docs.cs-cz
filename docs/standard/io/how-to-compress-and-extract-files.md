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
# <a name="how-to-compress-and-extract-files"></a>Postup: Komprese a extrahování souborů

Obor <xref:System.IO.Compression> názvů obsahuje následující typy pro kompresi a dekompresi souborů a datových proudů. Tyto typy můžete také použít ke čtení a úpravám obsahu komprimovaného souboru.

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

Následující příklady ukazují některé operace, které lze provádět s komprimovanými soubory.

## <a name="example-1-create-and-extract-a-zip-file"></a>Příklad 1: Vytvoření a extrahování souboru ZIP

Následující příklad ukazuje, jak vytvořit a extrahovat komprimovaný soubor *ZIP* pomocí <xref:System.IO.Compression.ZipFile> třídy. Příklad komprimuje obsah složky do nového souboru *ZIP* a potom extrahuje soubor ZIP do nové složky.

Chcete-li spustit ukázku, vytvořte *počáteční* složku ve složce programu a naplňte ji soubory, které chcete zip.

Pokud se zobrazí chyba sestavení "Název ZipFile' neexistuje v aktuálním kontextu," `System.IO.Compression.FileSystem` přidejte odkaz na sestavení projektu.

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a>Příklad 2: Extrahovat konkrétní přípony souborů

Další příklad itetuje obsah existujícího souboru *ZIP* a extrahuje soubory, které mají příponu *TXT.* Používá třídu <xref:System.IO.Compression.ZipArchive> pro přístup k <xref:System.IO.Compression.ZipArchiveEntry> zip a třídy ke kontrole jednotlivých položek. Metoda <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> rozšíření pro <xref:System.IO.Compression.ZipArchiveEntry> objekt je <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> k dispozici ve třídě.

Chcete-li vzorek spustit, umístěte soubor *ZIP* s názvem *result.zip* do složky programu. Po zobrazení výzvy zadejte název složky, do které chcete extrahovat.

Pokud se zobrazí chyba sestavení "Název ZipFile' neexistuje v aktuálním kontextu," `System.IO.Compression.FileSystem` přidejte odkaz na sestavení projektu.

Pokud se zobrazí chyba "Typ ZipArchive' je definován v sestavení, které není `System.IO.Compression` odkazováno," přidejte odkaz na sestavení do projektu.

> [!IMPORTANT]
> Při rozbalení souborů je nutné vyhledat škodlivé cesty k souborům, které mohou uniknout z adresáře, do kterého rozbalíte. To se označuje jako cesta traversal útoku. Následující příklad ukazuje, jak zkontrolovat cesty škodlivého souboru a poskytuje bezpečný způsob, jak rozbalit.

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a>Příklad 3: Přidání souboru do existujícího zipu

Následující příklad používá <xref:System.IO.Compression.ZipArchive> třídu pro přístup k existujícímu souboru *ZIP* a přidá k němu soubor. Nový soubor získá komprimované při přidání do existujícího zip.

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a>Příklad 4: Komprese a dekomprese souborů GZ

Třídy <xref:System.IO.Compression.GZipStream> a <xref:System.IO.Compression.DeflateStream> můžete také použít ke kompresi a dekompresi dat. Používají stejný kompresní algoritmus. Objekty, <xref:System.IO.Compression.GZipStream> které jsou zapsány do souboru *GZ,* můžete dekomprimovat pomocí mnoha běžných nástrojů. Následující příklad ukazuje, jak komprimovat a dekomprimovat adresář souborů pomocí třídy: <xref:System.IO.Compression.GZipStream>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a>Viz také

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [Vstupně-tono-videa](../../../docs/standard/io/index.md)
