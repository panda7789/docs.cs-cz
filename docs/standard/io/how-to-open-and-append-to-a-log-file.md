---
title: 'Postupy: otevření a připojení k souboru protokolu'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
ms.openlocfilehash: a549aba3a763bcfc5a3889efd65e2495eca7622c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155708"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Postupy: otevření a připojení k souboru protokolu
<xref:System.IO.StreamWriter> a <xref:System.IO.StreamReader> zápis znaků a čtení znaků z datových proudů. Následující příklad kódu otevře soubor *log. txt* pro vstup, nebo ho vytvoří, pokud neexistuje, a připojí informace protokolu na konec souboru. Příklad následně zapíše obsah souboru do standardního výstupu pro zobrazení.

Jako alternativu k tomuto příkladu můžete ukládat informace jako jeden řetězec nebo pole řetězců a použít metodu <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> nebo <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> k dosažení stejné funkce.  
  
> [!NOTE]
> Visual Basic uživatelé mohou používat metody a vlastnosti poskytované <xref:Microsoft.VisualBasic.Logging.Log> třídy nebo třídy <xref:Microsoft.VisualBasic.FileIO.FileSystem> pro vytváření nebo zápis do souborů protokolu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Postupy: zobrazení výčtu adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Postupy: čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Postupy: čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Postupy: zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Postupy: čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Postupy: zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Vstupně-výstupní operace se soubory a datovým proudem](../../../docs/standard/io/index.md)
