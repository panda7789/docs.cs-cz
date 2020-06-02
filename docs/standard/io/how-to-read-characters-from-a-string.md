---
title: 'Postupy: čtení znaků z řetězce'
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
ms.openlocfilehash: 6d32e9c5f89dba7590958bae6cc0489f104cd19a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291770"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="7db38-102">Postupy: čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="7db38-102">How to: Read characters from a string</span></span>
<span data-ttu-id="7db38-103">Následující příklady kódu znázorňují, jak číst znaky synchronně nebo asynchronně z řetězce.</span><span class="sxs-lookup"><span data-stu-id="7db38-103">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="7db38-104">Příklad: synchronní čtení znaků</span><span class="sxs-lookup"><span data-stu-id="7db38-104">Example: Read characters synchronously</span></span>
 <span data-ttu-id="7db38-105">Tento příklad načte 13 znaků synchronně z řetězce, uloží je do pole a zobrazí je.</span><span class="sxs-lookup"><span data-stu-id="7db38-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="7db38-106">Příklad přečte zbytek znaků v řetězci, uloží je do pole začínajícího na šestém prvku a zobrazí obsah pole.</span><span class="sxs-lookup"><span data-stu-id="7db38-106">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="7db38-107">Příklad: asynchronní čtení znaků</span><span class="sxs-lookup"><span data-stu-id="7db38-107">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="7db38-108">Dalším příkladem je kód za aplikací WPF.</span><span class="sxs-lookup"><span data-stu-id="7db38-108">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="7db38-109">Při načtení okna příklad asynchronně načítá všechny znaky z <xref:System.Windows.Controls.TextBox> ovládacího prvku a ukládá je do pole.</span><span class="sxs-lookup"><span data-stu-id="7db38-109">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="7db38-110">Potom asynchronně zapisuje každé písmeno nebo prázdné znaky na samostatný řádek <xref:System.Windows.Controls.TextBlock> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7db38-110">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="7db38-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="7db38-111">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="7db38-112">Asynchronní souborový vstup-výstup</span><span class="sxs-lookup"><span data-stu-id="7db38-112">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="7db38-113">[Postupy: vytvoření seznamu adresářů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7db38-113">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="7db38-114">Postupy: čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="7db38-114">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="7db38-115">Postupy: otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="7db38-115">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="7db38-116">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="7db38-116">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="7db38-117">Postupy: zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="7db38-117">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="7db38-118">Postupy: zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="7db38-118">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="7db38-119">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="7db38-119">File and stream I/O</span></span>](index.md)
