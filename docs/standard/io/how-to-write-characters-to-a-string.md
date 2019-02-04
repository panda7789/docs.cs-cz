---
title: 'Postupy: Zápis znaků do řetězce'
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb35c61b34fa571f35da6691ebe7fa2516eb2df1
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674747"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="9e5bd-102">Postupy: Zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="9e5bd-102">How to: Write characters to a string</span></span>
<span data-ttu-id="9e5bd-103">Následující příklady kódu zápis znaků synchronně nebo asynchronně z pole znaků do řetězce.</span><span class="sxs-lookup"><span data-stu-id="9e5bd-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="9e5bd-104">Příklad: Zápis znaků synchronně v konzolové aplikaci</span><span class="sxs-lookup"><span data-stu-id="9e5bd-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="9e5bd-105">V následujícím příkladu <xref:System.IO.StringWriter> pro zápis synchronně do pěti znaků <xref:System.Text.StringBuilder> objektu.</span><span class="sxs-lookup"><span data-stu-id="9e5bd-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span> 
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="9e5bd-106">Příklad: Zápis znaků asynchronně v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="9e5bd-106">Example: Write characters asynchronously in a WPF app</span></span> 
 <span data-ttu-id="9e5bd-107">Následující příklad je kódu na pozadí aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="9e5bd-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="9e5bd-108">Při načtení okna, v příkladu asynchronně přečte všechny znaky z <xref:System.Windows.Controls.TextBox> ovládací prvek a uloží je v poli.</span><span class="sxs-lookup"><span data-stu-id="9e5bd-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="9e5bd-109">Pak asynchronně zapíše každý znak písmeno, nebo prázdné znaky na samostatném řádku <xref:System.Windows.Controls.TextBlock> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9e5bd-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9e5bd-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e5bd-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="9e5bd-111">Vstupně-výstupních operací souborů a datových proudů</span><span class="sxs-lookup"><span data-stu-id="9e5bd-111">File and stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="9e5bd-112">Asynchronní I/O soubory</span><span class="sxs-lookup"><span data-stu-id="9e5bd-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="9e5bd-113">Postupy: Vytvoření výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="9e5bd-113">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="9e5bd-114">Postupy: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="9e5bd-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="9e5bd-115">Postupy: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="9e5bd-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="9e5bd-116">Postupy: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="9e5bd-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="9e5bd-117">Postupy: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="9e5bd-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="9e5bd-118">Postupy: Čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="9e5bd-118">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
