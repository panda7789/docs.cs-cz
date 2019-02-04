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
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674838"
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="f938e-102">Postupy: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="f938e-102">How to: Open and append to a log file</span></span>
<span data-ttu-id="f938e-103"><xref:System.IO.StreamWriter> a <xref:System.IO.StreamReader> znaků pro zápis a čtení znaků z datových proudů.</span><span class="sxs-lookup"><span data-stu-id="f938e-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="f938e-104">Následující příklad kódu otevře *log.txt* souboru pro vstup, nebo ji vytvoří, pokud neexistuje a připojí informace protokolu na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="f938e-104">The following code example opens the *log.txt* file for input, or creates it if it doesn't exist, and appends log information to the end of the file.</span></span> <span data-ttu-id="f938e-105">Příklad poté zapíše obsah souboru do standardního výstupu pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="f938e-105">The example then writes the contents of the file to standard output for display.</span></span> 

<span data-ttu-id="f938e-106">Jako alternativu k v tomto příkladu, můžete tyto informace uložit jako jeden řetězec nebo pole řetězců a použít <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> nebo <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> metoda dosáhnout stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="f938e-106">As an alternative to this example, you could store the information as a single string or string array, and use the <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> or <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> method to achieve the same functionality.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f938e-107">Uživatelé jazyka Visual Basic můžete použít metody a vlastnosti poskytované třídou <xref:Microsoft.VisualBasic.Logging.Log> třídy nebo <xref:Microsoft.VisualBasic.FileIO.FileSystem> třída pro vytvoření nebo zápis do souborů protokolu.</span><span class="sxs-lookup"><span data-stu-id="f938e-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f938e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="f938e-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f938e-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f938e-109">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="f938e-110">Postupy: Vytvoření výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="f938e-110">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="f938e-111">Postupy: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="f938e-111">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="f938e-112">Postupy: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="f938e-112">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="f938e-113">Postupy: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="f938e-113">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="f938e-114">Postupy: Čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="f938e-114">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="f938e-115">Postupy: Zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="f938e-115">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="f938e-116">Vstupně-výstupních operací souborů a datových proudů</span><span class="sxs-lookup"><span data-stu-id="f938e-116">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
