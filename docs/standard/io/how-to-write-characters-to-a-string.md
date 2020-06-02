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
ms.openlocfilehash: 04fc21c452258a88292a886d952353ac55573121
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288248"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="d7b67-102">Postupy: zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="d7b67-102">How to: Write characters to a string</span></span>
<span data-ttu-id="d7b67-103">Následující příklady kódu píší synchronně nebo asynchronně z pole znaků do řetězce.</span><span class="sxs-lookup"><span data-stu-id="d7b67-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="d7b67-104">Příklad: synchronní zápis znaků v konzolové aplikaci</span><span class="sxs-lookup"><span data-stu-id="d7b67-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="d7b67-105">Následující příklad používá <xref:System.IO.StringWriter> k zápisu pěti znaků synchronně do <xref:System.Text.StringBuilder> objektu.</span><span class="sxs-lookup"><span data-stu-id="d7b67-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span>
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="d7b67-106">Příklad: asynchronní zápis znaků v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="d7b67-106">Example: Write characters asynchronously in a WPF app</span></span>
 <span data-ttu-id="d7b67-107">Dalším příkladem je kód za aplikací WPF.</span><span class="sxs-lookup"><span data-stu-id="d7b67-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="d7b67-108">Při načtení okna příklad asynchronně načítá všechny znaky z <xref:System.Windows.Controls.TextBox> ovládacího prvku a ukládá je do pole.</span><span class="sxs-lookup"><span data-stu-id="d7b67-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="d7b67-109">Potom asynchronně zapisuje každé písmeno nebo prázdné znaky na samostatný řádek <xref:System.Windows.Controls.TextBlock> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d7b67-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d7b67-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7b67-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="d7b67-111">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="d7b67-111">File and stream I/O</span></span>](index.md)  
- [<span data-ttu-id="d7b67-112">Asynchronní souborový vstup-výstup</span><span class="sxs-lookup"><span data-stu-id="d7b67-112">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- [<span data-ttu-id="d7b67-113">Postupy: zobrazení výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="d7b67-113">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="d7b67-114">Postupy: čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="d7b67-114">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="d7b67-115">Postupy: otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="d7b67-115">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="d7b67-116">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="d7b67-116">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="d7b67-117">Postupy: zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="d7b67-117">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="d7b67-118">Postupy: čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="d7b67-118">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)
