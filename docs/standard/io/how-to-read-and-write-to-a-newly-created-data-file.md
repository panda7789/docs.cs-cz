---
title: 'Postup: Čtení a zápis do nově vytvořeného datového souboru'
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
ms.openlocfilehash: 3772aeeb25d1251a13fde2a0e51a913e5e39eabc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155747"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="322c4-102">Postup: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="322c4-102">How to: Read and write to a newly created data file</span></span>
<span data-ttu-id="322c4-103"><xref:System.IO.BinaryWriter?displayProperty=nameWithType> Třídy <xref:System.IO.BinaryReader?displayProperty=nameWithType> a se používají pro zápis a čtení dat jiných než řetězce znaků.</span><span class="sxs-lookup"><span data-stu-id="322c4-103">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="322c4-104">Následující příklad ukazuje, jak vytvořit prázdný datový proud souboru, zapisovat do něj data a číst data z něj.</span><span class="sxs-lookup"><span data-stu-id="322c4-104">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span>

<span data-ttu-id="322c4-105">V příkladu se vytvoří datový soubor s názvem *Test.data* v aktuálním adresáři, <xref:System.IO.BinaryWriter> vytvoří přidružené a <xref:System.IO.BinaryReader> objekty a použije <xref:System.IO.BinaryWriter> objekt k zápisu celá čísla 0 až 10 do *Test.data*, který ponechává ukazatel souboru na konci souboru.</span><span class="sxs-lookup"><span data-stu-id="322c4-105">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="322c4-106">Objekt <xref:System.IO.BinaryReader> pak nastaví ukazatel souboru zpět na počátek a přečte zadaný obsah.</span><span class="sxs-lookup"><span data-stu-id="322c4-106">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="322c4-107">Pokud *Test.data* již existuje v aktuálním adresáři, je vyvolána <xref:System.IO.IOException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="322c4-107">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="322c4-108">Použijte možnost <xref:System.IO.FileMode.Create?displayProperty=nameWithType> režimu <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> souboru, nikoli vždy vytvořit nový soubor bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="322c4-108">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="322c4-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="322c4-109">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="322c4-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="322c4-110">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="322c4-111">Postup: Výčet adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="322c4-111">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="322c4-112">Postup: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="322c4-112">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="322c4-113">Postup: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="322c4-113">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="322c4-114">Postup: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="322c4-114">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="322c4-115">Postup: Čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="322c4-115">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="322c4-116">Postup: Zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="322c4-116">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="322c4-117">Vstupně-tono-videa</span><span class="sxs-lookup"><span data-stu-id="322c4-117">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
