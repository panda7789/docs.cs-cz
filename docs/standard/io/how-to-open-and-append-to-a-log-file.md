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
ms.openlocfilehash: 025c35344b9262e1f2fa6da87b68e46e21a54222
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291822"
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="47d45-102">Postupy: otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="47d45-102">How to: Open and append to a log file</span></span>
<span data-ttu-id="47d45-103"><xref:System.IO.StreamWriter>a <xref:System.IO.StreamReader> zápis znaků a čtení znaků z datových proudů.</span><span class="sxs-lookup"><span data-stu-id="47d45-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="47d45-104">Následující příklad kódu otevře soubor *log. txt* pro vstup, nebo ho vytvoří, pokud neexistuje, a připojí informace protokolu na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="47d45-104">The following code example opens the *log.txt* file for input, or creates it if it doesn't exist, and appends log information to the end of the file.</span></span> <span data-ttu-id="47d45-105">Příklad následně zapíše obsah souboru do standardního výstupu pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="47d45-105">The example then writes the contents of the file to standard output for display.</span></span>

<span data-ttu-id="47d45-106">Jako alternativu k tomuto příkladu můžete ukládat informace jako jeden řetězec nebo pole řetězců a použít <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> metodu nebo k dosažení stejných funkcí.</span><span class="sxs-lookup"><span data-stu-id="47d45-106">As an alternative to this example, you could store the information as a single string or string array, and use the <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> or <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> method to achieve the same functionality.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47d45-107">Visual Basic uživatelé se mohou rozhodnout použít metody a vlastnosti poskytované <xref:Microsoft.VisualBasic.Logging.Log> třídou nebo <xref:Microsoft.VisualBasic.FileIO.FileSystem> třídou pro vytváření nebo zápis do souborů protokolu.</span><span class="sxs-lookup"><span data-stu-id="47d45-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47d45-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="47d45-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="47d45-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="47d45-109">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="47d45-110">Postupy: zobrazení výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="47d45-110">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="47d45-111">Postupy: čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="47d45-111">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="47d45-112">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="47d45-112">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="47d45-113">Postupy: zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="47d45-113">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="47d45-114">Postupy: čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="47d45-114">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="47d45-115">Postupy: zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="47d45-115">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="47d45-116">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="47d45-116">File and stream I/O</span></span>](index.md)
