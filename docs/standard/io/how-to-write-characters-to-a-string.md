---
title: 'Postupy: zápis znaků do řetězce'
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
ms.openlocfilehash: ecbfa2de2c21ff79df269f74eeddfa0738e7e25c
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160274"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="a1be2-102">Postupy: zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="a1be2-102">How to: Write characters to a string</span></span>
<span data-ttu-id="a1be2-103">Následující příklady kódu píší synchronně nebo asynchronně z pole znaků do řetězce.</span><span class="sxs-lookup"><span data-stu-id="a1be2-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="a1be2-104">Příklad: synchronní zápis znaků v konzolové aplikaci</span><span class="sxs-lookup"><span data-stu-id="a1be2-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="a1be2-105">Následující příklad používá <xref:System.IO.StringWriter> k zápisu pěti znaků synchronně do objektu <xref:System.Text.StringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="a1be2-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span>
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="a1be2-106">Příklad: asynchronní zápis znaků v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="a1be2-106">Example: Write characters asynchronously in a WPF app</span></span>
 <span data-ttu-id="a1be2-107">Dalším příkladem je kód za aplikací WPF.</span><span class="sxs-lookup"><span data-stu-id="a1be2-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="a1be2-108">Při načtení okna příklad asynchronně načítá všechny znaky z ovládacího prvku <xref:System.Windows.Controls.TextBox> a ukládá je do pole.</span><span class="sxs-lookup"><span data-stu-id="a1be2-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="a1be2-109">Potom asynchronně zapisuje každé písmeno nebo prázdné znaky na samostatný řádek ovládacího prvku <xref:System.Windows.Controls.TextBlock>.</span><span class="sxs-lookup"><span data-stu-id="a1be2-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="a1be2-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1be2-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="a1be2-111">Vstupně-výstupní operace se soubory a datovým proudem</span><span class="sxs-lookup"><span data-stu-id="a1be2-111">File and stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="a1be2-112">I/O asynchronní soubory</span><span class="sxs-lookup"><span data-stu-id="a1be2-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="a1be2-113">Postupy: zobrazení výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="a1be2-113">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="a1be2-114">Postupy: čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="a1be2-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="a1be2-115">Postupy: otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="a1be2-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="a1be2-116">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="a1be2-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="a1be2-117">Postupy: zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="a1be2-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="a1be2-118">Postupy: čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="a1be2-118">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
