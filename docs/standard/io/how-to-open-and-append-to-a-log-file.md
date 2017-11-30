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
ms.openlocfilehash: 60c31339231405a1cbbb98dae37d36ad3c3709c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="40ea2-102">Postupy: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="40ea2-102">How to: Open and Append to a Log File</span></span>
<span data-ttu-id="40ea2-103"><xref:System.IO.StreamWriter>a <xref:System.IO.StreamReader> zapisuje a čtení znaků z datových proudů.</span><span class="sxs-lookup"><span data-stu-id="40ea2-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="40ea2-104">Následující příklad kódu otevře `log.txt` souboru pro vstup, nebo vytvoří soubor, pokud ještě neexistuje a připojí informace na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="40ea2-104">The following code example opens the `log.txt` file for input, or creates the file if it does not already exist, and appends information to the end of the file.</span></span> <span data-ttu-id="40ea2-105">Obsah souboru pak zapsány do standardního výstupního pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="40ea2-105">The contents of the file are then written to standard output for display.</span></span> <span data-ttu-id="40ea2-106">Jako alternativu k tento příklad informace může být uložený jako jeden řetězec nebo pole řetězců a <xref:System.IO.File.WriteAllText%2A> nebo <xref:System.IO.File.WriteAllLines%2A> metodu lze použít k dosažení stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="40ea2-106">As an alternative to this example, the information could be stored as a single string or string array, and the <xref:System.IO.File.WriteAllText%2A> or <xref:System.IO.File.WriteAllLines%2A> method could be used to achieve the same functionality.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="40ea2-107">Uživatelé jazyka Visual Basic rozhodnout použít metody a vlastnosti poskytované <xref:Microsoft.VisualBasic.Logging.Log> třídy nebo <xref:Microsoft.VisualBasic.FileIO.FileSystem> třídu pro vytvoření nebo zápis do souborů protokolu.</span><span class="sxs-lookup"><span data-stu-id="40ea2-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40ea2-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="40ea2-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="40ea2-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="40ea2-109">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="40ea2-110">Postupy: vytvoření výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="40ea2-110">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="40ea2-111">Postupy: čtení a zápisu do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="40ea2-111">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="40ea2-112">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="40ea2-112">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="40ea2-113">Postupy: zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="40ea2-113">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="40ea2-114">Postupy: čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="40ea2-114">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="40ea2-115">Postupy: zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="40ea2-115">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="40ea2-116">Souborová služba a datový proud I-O</span><span class="sxs-lookup"><span data-stu-id="40ea2-116">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
