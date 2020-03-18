---
title: 'Postup: Zápis znaků do řetězce'
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160274"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="274ec-102">Postup: Zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="274ec-102">How to: Write characters to a string</span></span>
<span data-ttu-id="274ec-103">Následující příklady kódu zapisují znaky synchronně nebo asynchronně z pole znaků do řetězce.</span><span class="sxs-lookup"><span data-stu-id="274ec-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="274ec-104">Příklad: Zápis znaků synchronně v konzolové aplikaci</span><span class="sxs-lookup"><span data-stu-id="274ec-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="274ec-105">Následující příklad používá <xref:System.IO.StringWriter> k zápisu pět znaků <xref:System.Text.StringBuilder> synchronně do objektu.</span><span class="sxs-lookup"><span data-stu-id="274ec-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span>
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="274ec-106">Příklad: Zápis znaků asynchronně v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="274ec-106">Example: Write characters asynchronously in a WPF app</span></span>
 <span data-ttu-id="274ec-107">Dalším příkladem je kód za wpf aplikace.</span><span class="sxs-lookup"><span data-stu-id="274ec-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="274ec-108">Při načtení okna příklad asynchronně přečte <xref:System.Windows.Controls.TextBox> všechny znaky z ovládacího prvku a uloží je do pole.</span><span class="sxs-lookup"><span data-stu-id="274ec-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="274ec-109">Potom asynchronně zapíše každé písmeno nebo prázdné místo znak <xref:System.Windows.Controls.TextBlock> na samostatný řádek ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="274ec-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="274ec-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="274ec-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="274ec-111">Vstupně-tono-videa</span><span class="sxs-lookup"><span data-stu-id="274ec-111">File and stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="274ec-112">Vstupně-nosný soubor asynchronní soubor</span><span class="sxs-lookup"><span data-stu-id="274ec-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="274ec-113">Postup: Výčet adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="274ec-113">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="274ec-114">Postup: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="274ec-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="274ec-115">Postup: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="274ec-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="274ec-116">Postup: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="274ec-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="274ec-117">Postup: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="274ec-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="274ec-118">Postup: Čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="274ec-118">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
