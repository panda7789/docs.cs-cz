---
title: 'Postupy: Otevření a připojení k souboru protokolu'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 921b13e057929d7d6b283b26014a4c1f195f39c9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751719"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Postupy: Otevření a připojení k souboru protokolu
<xref:System.IO.StreamWriter> a <xref:System.IO.StreamReader> znaků pro zápis a čtení znaků z datových proudů. Následující příklad kódu otevře *log.txt* souboru pro vstup, nebo ji vytvoří, pokud neexistuje a připojí informace protokolu na konec souboru. Příklad poté zapíše obsah souboru do standardního výstupu pro zobrazení. 

Jako alternativu k v tomto příkladu, můžete tyto informace uložit jako jeden řetězec nebo pole řetězců a použít <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> nebo <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> metoda dosáhnout stejné funkce.  
  
> [!NOTE]
> Uživatelé jazyka Visual Basic můžete použít metody a vlastnosti poskytované třídou <xref:Microsoft.VisualBasic.Logging.Log> třídy nebo <xref:Microsoft.VisualBasic.FileIO.FileSystem> třída pro vytvoření nebo zápis do souborů protokolu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Postupy: Vytvoření výčtu adresářů a souborů](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [Postupy: Čtení a zápis do nově vytvořeného datového souboru](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Postupy: Čtení textu ze souboru](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [Postupy: Zápis textu do souboru](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [Postupy: Čtení znaků z řetězce](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [Postupy: Zápis znaků do řetězce](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [Vstupně-výstupních operací souborů a datových proudů](../../../docs/standard/io/index.md)
