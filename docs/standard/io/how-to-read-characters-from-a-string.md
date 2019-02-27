---
title: 'Postupy: Čtení znaků z řetězce'
ms.date: 01/21/2019
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
ms.openlocfilehash: e890e4172e645e9919ea88ec5835aaed7432c0c6
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835197"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="1d739-102">Postupy: Čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="1d739-102">How to: Read characters from a string</span></span>
<span data-ttu-id="1d739-103">Následující příklady kódu ukazují, jak ke čtení znaků z řetězce synchronně nebo asynchronně.</span><span class="sxs-lookup"><span data-stu-id="1d739-103">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="1d739-104">Příklad: Čtení znaků synchronně</span><span class="sxs-lookup"><span data-stu-id="1d739-104">Example: Read characters synchronously</span></span> 
 <span data-ttu-id="1d739-105">Tento příklad načte 13 znaků synchronně z řetězce, uloží je v poli a zobrazí je.</span><span class="sxs-lookup"><span data-stu-id="1d739-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="1d739-106">Příklad poté načte zbývající znaky v řetězci, uloží je do pole, počínaje šestého prvku a zobrazí obsah pole.</span><span class="sxs-lookup"><span data-stu-id="1d739-106">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="1d739-107">Příklad: Asynchronně číst datové části znaků</span><span class="sxs-lookup"><span data-stu-id="1d739-107">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="1d739-108">Následující příklad je kódu na pozadí aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="1d739-108">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="1d739-109">Při načtení okna, v příkladu asynchronně přečte všechny znaky z <xref:System.Windows.Controls.TextBox> ovládací prvek a uloží je v poli.</span><span class="sxs-lookup"><span data-stu-id="1d739-109">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="1d739-110">Pak asynchronně zapíše každý znak písmeno, nebo prázdné znaky na samostatném řádku <xref:System.Windows.Controls.TextBlock> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1d739-110">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1d739-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d739-111">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="1d739-112">Asynchronní I/O soubory</span><span class="sxs-lookup"><span data-stu-id="1d739-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="1d739-113">[Postupy: Vytváření adresářů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="1d739-113">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="1d739-114">Postupy: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="1d739-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="1d739-115">Postupy: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="1d739-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="1d739-116">Postupy: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="1d739-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="1d739-117">Postupy: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="1d739-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="1d739-118">Postupy: Zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="1d739-118">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="1d739-119">Vstupně-výstupních operací souborů a datových proudů</span><span class="sxs-lookup"><span data-stu-id="1d739-119">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
