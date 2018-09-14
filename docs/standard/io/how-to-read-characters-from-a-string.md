---
title: 'Postupy: Čtení znaků z řetězce'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET Framework], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 13a57f8ea7db91e5357ecfb20c4e907f2706f78d
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45592916"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="4a7fc-102">Postupy: Čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="4a7fc-102">How to: Read Characters from a String</span></span>
<span data-ttu-id="4a7fc-103">Následující příklady kódu ukazují, jak synchronního a asynchronního čtení znaků z řetězce.</span><span class="sxs-lookup"><span data-stu-id="4a7fc-103">The following code examples show how to read characters synchronously and asynchronously from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a7fc-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4a7fc-104">Example</span></span>  
 <span data-ttu-id="4a7fc-105">Tento příklad načte 13 znaků synchronně z řetězce, uloží je v poli a zobrazí tyto znaky.</span><span class="sxs-lookup"><span data-stu-id="4a7fc-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays those characters.</span></span> <span data-ttu-id="4a7fc-106">Je pak přečte zbývající znaky v řetězci, uloží je do pole, počínaje šestého prvku a zobrazí obsah pole.</span><span class="sxs-lookup"><span data-stu-id="4a7fc-106">It then reads the remaining characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="4a7fc-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="4a7fc-107">Example</span></span>  
 <span data-ttu-id="4a7fc-108">Následující příklad načte všechny znaky asynchronně z <xref:System.Windows.Controls.TextBox> ovládací prvek a uloží je v poli.</span><span class="sxs-lookup"><span data-stu-id="4a7fc-108">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="4a7fc-109">Pak asynchronně zapíše každý znak písmeno, nebo prázdné znaky na samostatném řádku, za nímž následuje koncem řádku <xref:System.Windows.Controls.TextBlock> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="4a7fc-109">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="4a7fc-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4a7fc-110">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="4a7fc-111">Asynchronní vstupně-výstupní operace se soubory</span><span class="sxs-lookup"><span data-stu-id="4a7fc-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="4a7fc-112">NIB: Postupy: vytvoření adresářů</span><span class="sxs-lookup"><span data-stu-id="4a7fc-112">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
- [<span data-ttu-id="4a7fc-113">Postupy: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="4a7fc-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="4a7fc-114">Postupy: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="4a7fc-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="4a7fc-115">Postupy: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="4a7fc-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="4a7fc-116">Postupy: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="4a7fc-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="4a7fc-117">Postupy: Zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="4a7fc-117">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="4a7fc-118">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="4a7fc-118">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
