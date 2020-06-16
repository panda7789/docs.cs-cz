---
title: 'Postupy: otevření a připojení k souboru protokolu'
description: Otevřete a přihlaste se k souboru protokolu pomocí tříd StreamWriter a StreamReader v rozhraní .NET, které zapisují znaky do znaků a čtou je z datových proudů.
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
ms.openlocfilehash: a66dadd24cc327824e91df733f11a23112cd384a
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769168"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Postupy: otevření a připojení k souboru protokolu
<xref:System.IO.StreamWriter>a <xref:System.IO.StreamReader> zápis znaků a čtení znaků z datových proudů. Následující příklad kódu otevře soubor *log.txt* pro vstup, nebo ho vytvoří, pokud neexistuje, a připojí informace protokolu na konec souboru. Příklad následně zapíše obsah souboru do standardního výstupu pro zobrazení.

Jako alternativu k tomuto příkladu můžete ukládat informace jako jeden řetězec nebo pole řetězců a použít <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> metodu nebo k dosažení stejných funkcí.  
  
> [!NOTE]
> Visual Basic uživatelé se mohou rozhodnout použít metody a vlastnosti poskytované <xref:Microsoft.VisualBasic.Logging.Log> třídou nebo <xref:Microsoft.VisualBasic.FileIO.FileSystem> třídou pro vytváření nebo zápis do souborů protokolu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [Postupy: zobrazení výčtu adresářů a souborů](how-to-enumerate-directories-and-files.md)  
- [Postupy: čtení a zápis do nově vytvořeného datového souboru](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [Postupy: čtení textu ze souboru](how-to-read-text-from-a-file.md)  
- [Postupy: zápis textu do souboru](how-to-write-text-to-a-file.md)  
- [Postupy: čtení znaků z řetězce](how-to-read-characters-from-a-string.md)  
- [Postupy: zápis znaků do řetězce](how-to-write-characters-to-a-string.md)  
- [Vstup/výstup souborů a streamů](index.md)
