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
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="d1a52-102">Postupy: otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="d1a52-102">How to: Open and append to a log file</span></span>
<span data-ttu-id="d1a52-103"><xref:System.IO.StreamWriter> a <xref:System.IO.StreamReader> zápis znaků a čtení znaků z datových proudů.</span><span class="sxs-lookup"><span data-stu-id="d1a52-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="d1a52-104">Následující příklad kódu otevře soubor *log. txt* pro vstup, nebo ho vytvoří, pokud neexistuje, a připojí informace protokolu na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="d1a52-104">The following code example opens the *log.txt* file for input, or creates it if it doesn't exist, and appends log information to the end of the file.</span></span> <span data-ttu-id="d1a52-105">Příklad následně zapíše obsah souboru do standardního výstupu pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="d1a52-105">The example then writes the contents of the file to standard output for display.</span></span>

<span data-ttu-id="d1a52-106">Jako alternativu k tomuto příkladu můžete ukládat informace jako jeden řetězec nebo pole řetězců a použít metodu <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> nebo <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> k dosažení stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="d1a52-106">As an alternative to this example, you could store the information as a single string or string array, and use the <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> or <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> method to achieve the same functionality.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1a52-107">Visual Basic uživatelé mohou používat metody a vlastnosti poskytované <xref:Microsoft.VisualBasic.Logging.Log> třídy nebo třídy <xref:Microsoft.VisualBasic.FileIO.FileSystem> pro vytváření nebo zápis do souborů protokolu.</span><span class="sxs-lookup"><span data-stu-id="d1a52-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1a52-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1a52-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d1a52-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1a52-109">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="d1a52-110">Postupy: zobrazení výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="d1a52-110">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="d1a52-111">Postupy: čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="d1a52-111">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="d1a52-112">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="d1a52-112">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="d1a52-113">Postupy: zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="d1a52-113">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="d1a52-114">Postupy: čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="d1a52-114">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="d1a52-115">Postupy: zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="d1a52-115">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="d1a52-116">Vstupně-výstupní operace se soubory a datovým proudem</span><span class="sxs-lookup"><span data-stu-id="d1a52-116">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
