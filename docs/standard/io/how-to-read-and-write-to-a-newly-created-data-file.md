---
title: 'Postupy: Čtení a zápis do nově vytvořeného datového souboru'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 065907ae0d4a38ff2ef68de6025251e28220ee96
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674617"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="a9145-102">Postupy: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="a9145-102">How to: Read and write to a newly created data file</span></span>
<span data-ttu-id="a9145-103"><xref:System.IO.BinaryWriter?displayProperty=nameWithType> a <xref:System.IO.BinaryReader?displayProperty=nameWithType> třídy se používají pro zápis a čtení dat než řetězců znaků.</span><span class="sxs-lookup"><span data-stu-id="a9145-103">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="a9145-104">Následující příklad ukazuje, jak vytvořit prázdný soubor proud, zápis dat do a z něj číst data.</span><span class="sxs-lookup"><span data-stu-id="a9145-104">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span> 

<span data-ttu-id="a9145-105">V příkladu se vytvoří datový soubor s názvem *Test.data* v aktuálním adresáři vytvoří přidružený <xref:System.IO.BinaryWriter> a <xref:System.IO.BinaryReader> objekty a používá <xref:System.IO.BinaryWriter> objekt k zápisu celých čísel 0 až 10 *Test.data*, které nechá ukazatel na soubor na konci souboru.</span><span class="sxs-lookup"><span data-stu-id="a9145-105">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="a9145-106"><xref:System.IO.BinaryReader> Objekt pak nastaví ukazatele souboru zpět k původu a přečte zadaný obsah.</span><span class="sxs-lookup"><span data-stu-id="a9145-106">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9145-107">Pokud *Test.data* již existuje v aktuálním adresáři <xref:System.IO.IOException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="a9145-107">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="a9145-108">Použijte volbu režimu souboru <xref:System.IO.FileMode.Create?displayProperty=nameWithType> spíše než <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> vždy vytvořit nový soubor bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="a9145-108">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9145-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a9145-109">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="a9145-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9145-110">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="a9145-111">Postupy: Vytvoření výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="a9145-111">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="a9145-112">Postupy: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="a9145-112">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="a9145-113">Postupy: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="a9145-113">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="a9145-114">Postupy: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="a9145-114">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="a9145-115">Postupy: Čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="a9145-115">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="a9145-116">Postupy: Zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="a9145-116">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="a9145-117">Vstupně-výstupních operací souborů a datových proudů</span><span class="sxs-lookup"><span data-stu-id="a9145-117">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
