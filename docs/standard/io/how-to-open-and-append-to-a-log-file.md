---
title: 'Postupy: Otevření a připojení k souboru protokolu'
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cd2d13a49d9b696541ac278b9f1847c8e4a48cf1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Postupy: Otevření a připojení k souboru protokolu
<xref:System.IO.StreamWriter> a <xref:System.IO.StreamReader> zapisuje a čtení znaků z datových proudů. Následující příklad kódu otevře `log.txt` souboru pro vstup, nebo vytvoří soubor, pokud ještě neexistuje a připojí informace na konec souboru. Obsah souboru pak zapsány do standardního výstupního pro zobrazení. Jako alternativu k tento příklad informace může být uložený jako jeden řetězec nebo pole řetězců a <xref:System.IO.File.WriteAllText%2A> nebo <xref:System.IO.File.WriteAllLines%2A> metodu lze použít k dosažení stejné funkce.  
  
> [!NOTE]
>  Uživatelé jazyka Visual Basic rozhodnout použít metody a vlastnosti poskytované <xref:Microsoft.VisualBasic.Logging.Log> třídy nebo <xref:Microsoft.VisualBasic.FileIO.FileSystem> třídu pro vytvoření nebo zápis do souborů protokolu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [Postupy: Vytvoření výčtu adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [Postupy: Čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [Postupy: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [Postupy: Čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [Postupy: Zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [Vstup/výstup souborů a streamů](../../../docs/standard/io/index.md)
