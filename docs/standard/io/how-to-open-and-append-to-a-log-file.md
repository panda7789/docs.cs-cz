---
title: "Postupy: Otevření a připojení k souboru protokolu"
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
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 333b20adee4ea2826a1fc6795a39490dca1af843
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-open-and-append-to-a-log-file"></a>Postupy: Otevření a připojení k souboru protokolu
<xref:System.IO.StreamWriter>a <xref:System.IO.StreamReader> zapisuje a čtení znaků z datových proudů. Následující příklad kódu otevře `log.txt` souboru pro vstup, nebo vytvoří soubor, pokud ještě neexistuje a připojí informace na konec souboru. Obsah souboru pak zapsány do standardního výstupního pro zobrazení. Jako alternativu k tento příklad informace může být uložený jako jeden řetězec nebo pole řetězců a <xref:System.IO.File.WriteAllText%2A> nebo <xref:System.IO.File.WriteAllLines%2A> metodu lze použít k dosažení stejné funkce.  
  
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
 [Souborová služba a datový proud I-O](../../../docs/standard/io/index.md)
