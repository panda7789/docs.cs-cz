---
title: 'Postupy: čtení a zápis do nově vytvořeného datového souboru'
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
ms.openlocfilehash: 18f44af81a38a48da3115d2082ef45af39f06529
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291809"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="130c3-102">Postupy: čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="130c3-102">How to: Read and write to a newly created data file</span></span>
<span data-ttu-id="130c3-103"><xref:System.IO.BinaryWriter?displayProperty=nameWithType>Třídy a <xref:System.IO.BinaryReader?displayProperty=nameWithType> jsou používány pro zápis a čtení jiných dat než řetězců znaků.</span><span class="sxs-lookup"><span data-stu-id="130c3-103">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="130c3-104">Následující příklad ukazuje, jak vytvořit prázdný datový proud souboru, zapsat do něj data a číst z něj data.</span><span class="sxs-lookup"><span data-stu-id="130c3-104">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span>

<span data-ttu-id="130c3-105">Příklad vytvoří datový soubor s názvem *test. data* v aktuálním adresáři, vytvoří přidružené <xref:System.IO.BinaryWriter> objekty a a <xref:System.IO.BinaryReader> pomocí <xref:System.IO.BinaryWriter> objektu zapíše celá čísla 0 až 10 pro *test. data*, která na konci souboru ponechají ukazatel na soubor.</span><span class="sxs-lookup"><span data-stu-id="130c3-105">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="130c3-106"><xref:System.IO.BinaryReader>Objekt pak nastaví ukazatel na soubor zpět na počátek a přečte zadaný obsah.</span><span class="sxs-lookup"><span data-stu-id="130c3-106">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="130c3-107">IF *test. data* již v aktuálním adresáři existují, <xref:System.IO.IOException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="130c3-107">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="130c3-108">Místo toho použijte možnost režim souboru, <xref:System.IO.FileMode.Create?displayProperty=nameWithType> nikoli <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> vždy vytvořit nový soubor bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="130c3-108">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="130c3-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="130c3-109">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="130c3-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="130c3-110">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="130c3-111">Postupy: zobrazení výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="130c3-111">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="130c3-112">Postupy: otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="130c3-112">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="130c3-113">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="130c3-113">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="130c3-114">Postupy: zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="130c3-114">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="130c3-115">Postupy: čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="130c3-115">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="130c3-116">Postupy: zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="130c3-116">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="130c3-117">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="130c3-117">File and stream I/O</span></span>](index.md)
