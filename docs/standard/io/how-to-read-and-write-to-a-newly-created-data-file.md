---
title: 'Postupy: čtení a zápis do nově vytvořeného datového souboru'
description: Přečtěte si, jak číst a zapisovat do nově vytvořeného datového souboru v rozhraní .NET pomocí tříd System. IO. BinaryReader a System. IO. BinaryWriter.
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
ms.openlocfilehash: 9a6b2985b7f532476c0f4c0f998d710f95e55d3a
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769155"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="be2ec-103">Postupy: čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="be2ec-103">How to: Read and write to a newly created data file</span></span>
<span data-ttu-id="be2ec-104"><xref:System.IO.BinaryWriter?displayProperty=nameWithType>Třídy a <xref:System.IO.BinaryReader?displayProperty=nameWithType> jsou používány pro zápis a čtení jiných dat než řetězců znaků.</span><span class="sxs-lookup"><span data-stu-id="be2ec-104">The <xref:System.IO.BinaryWriter?displayProperty=nameWithType> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data other than character strings.</span></span> <span data-ttu-id="be2ec-105">Následující příklad ukazuje, jak vytvořit prázdný datový proud souboru, zapsat do něj data a číst z něj data.</span><span class="sxs-lookup"><span data-stu-id="be2ec-105">The following example shows how to create an empty file stream, write data to it, and read data from it.</span></span>

<span data-ttu-id="be2ec-106">Příklad vytvoří datový soubor s názvem *test. data* v aktuálním adresáři, vytvoří přidružené <xref:System.IO.BinaryWriter> objekty a a <xref:System.IO.BinaryReader> pomocí <xref:System.IO.BinaryWriter> objektu zapíše celá čísla 0 až 10 pro *test. data*, která na konci souboru ponechají ukazatel na soubor.</span><span class="sxs-lookup"><span data-stu-id="be2ec-106">The example creates a data file called *Test.data* in the current directory, creates the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects, and uses the <xref:System.IO.BinaryWriter> object to write the integers 0 through 10 to *Test.data*, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="be2ec-107"><xref:System.IO.BinaryReader>Objekt pak nastaví ukazatel na soubor zpět na počátek a přečte zadaný obsah.</span><span class="sxs-lookup"><span data-stu-id="be2ec-107">The <xref:System.IO.BinaryReader> object then sets the file pointer back to the origin and reads out the specified content.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be2ec-108">IF *test. data* již v aktuálním adresáři existují, <xref:System.IO.IOException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="be2ec-108">If *Test.data* already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="be2ec-109">Místo toho použijte možnost režim souboru, <xref:System.IO.FileMode.Create?displayProperty=nameWithType> nikoli <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> vždy vytvořit nový soubor bez vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="be2ec-109">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> rather than <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType> to always create a new file without throwing an exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be2ec-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="be2ec-110">Example</span></span>  
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="be2ec-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="be2ec-111">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="be2ec-112">Postupy: zobrazení výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="be2ec-112">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="be2ec-113">Postupy: otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="be2ec-113">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="be2ec-114">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="be2ec-114">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="be2ec-115">Postupy: zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="be2ec-115">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="be2ec-116">Postupy: čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="be2ec-116">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="be2ec-117">Postupy: zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="be2ec-117">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="be2ec-118">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="be2ec-118">File and stream I/O</span></span>](index.md)
