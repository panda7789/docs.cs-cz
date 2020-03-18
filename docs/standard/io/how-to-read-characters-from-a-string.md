---
title: 'Postup: Čtení znaků z řetězce'
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
ms.openlocfilehash: ed267ad62e46f6216c94906df1bcefb0684ab51b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155760"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="ac2ea-102">Postup: Čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="ac2ea-102">How to: Read characters from a string</span></span>
<span data-ttu-id="ac2ea-103">Následující příklady kódu ukazují, jak číst znaky synchronně nebo asynchronně z řetězce.</span><span class="sxs-lookup"><span data-stu-id="ac2ea-103">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="ac2ea-104">Příklad: Synchronní čtení znaků</span><span class="sxs-lookup"><span data-stu-id="ac2ea-104">Example: Read characters synchronously</span></span>
 <span data-ttu-id="ac2ea-105">Tento příklad přečte 13 znaků synchronně z řetězce, uloží je do pole a zobrazí je.</span><span class="sxs-lookup"><span data-stu-id="ac2ea-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="ac2ea-106">Příklad pak přečte zbytek znaků v řetězci, uloží je do pole začínající na šestý prvek a zobrazí obsah pole.</span><span class="sxs-lookup"><span data-stu-id="ac2ea-106">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="ac2ea-107">Příklad: Čtení znaků asynchronně</span><span class="sxs-lookup"><span data-stu-id="ac2ea-107">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="ac2ea-108">Dalším příkladem je kód za wpf aplikace.</span><span class="sxs-lookup"><span data-stu-id="ac2ea-108">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="ac2ea-109">Při načtení okna příklad asynchronně přečte <xref:System.Windows.Controls.TextBox> všechny znaky z ovládacího prvku a uloží je do pole.</span><span class="sxs-lookup"><span data-stu-id="ac2ea-109">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="ac2ea-110">Potom asynchronně zapíše každé písmeno nebo prázdné místo znak <xref:System.Windows.Controls.TextBlock> na samostatný řádek ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ac2ea-110">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ac2ea-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="ac2ea-111">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="ac2ea-112">Vstupně-nosný soubor asynchronní soubor</span><span class="sxs-lookup"><span data-stu-id="ac2ea-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="ac2ea-113">[Postup: Vytvoření výpisu adresáře](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ac2ea-113">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="ac2ea-114">Postup: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="ac2ea-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="ac2ea-115">Postup: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="ac2ea-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="ac2ea-116">Postup: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="ac2ea-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="ac2ea-117">Postup: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="ac2ea-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="ac2ea-118">Postup: Zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="ac2ea-118">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="ac2ea-119">Vstupně-tono-videa</span><span class="sxs-lookup"><span data-stu-id="ac2ea-119">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
