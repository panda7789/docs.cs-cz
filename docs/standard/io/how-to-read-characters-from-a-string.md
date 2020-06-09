---
title: 'Postupy: čtení znaků z řetězce'
description: Naučte se číst znaky z řetězce v .NET. Zobrazit příklady znaku synchronního a asynchronního čtení.
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
ms.openlocfilehash: 40ff144e0899f3560805a31fa76f391afaeccd67
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594839"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="b8ee5-104">Postupy: čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="b8ee5-104">How to: Read characters from a string</span></span>
<span data-ttu-id="b8ee5-105">Následující příklady kódu znázorňují, jak číst znaky synchronně nebo asynchronně z řetězce.</span><span class="sxs-lookup"><span data-stu-id="b8ee5-105">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="b8ee5-106">Příklad: synchronní čtení znaků</span><span class="sxs-lookup"><span data-stu-id="b8ee5-106">Example: Read characters synchronously</span></span>
 <span data-ttu-id="b8ee5-107">Tento příklad načte 13 znaků synchronně z řetězce, uloží je do pole a zobrazí je.</span><span class="sxs-lookup"><span data-stu-id="b8ee5-107">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="b8ee5-108">Příklad přečte zbytek znaků v řetězci, uloží je do pole začínajícího na šestém prvku a zobrazí obsah pole.</span><span class="sxs-lookup"><span data-stu-id="b8ee5-108">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="b8ee5-109">Příklad: asynchronní čtení znaků</span><span class="sxs-lookup"><span data-stu-id="b8ee5-109">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="b8ee5-110">Dalším příkladem je kód za aplikací WPF.</span><span class="sxs-lookup"><span data-stu-id="b8ee5-110">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="b8ee5-111">Při načtení okna příklad asynchronně načítá všechny znaky z <xref:System.Windows.Controls.TextBox> ovládacího prvku a ukládá je do pole.</span><span class="sxs-lookup"><span data-stu-id="b8ee5-111">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="b8ee5-112">Potom asynchronně zapisuje každé písmeno nebo prázdné znaky na samostatný řádek <xref:System.Windows.Controls.TextBlock> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b8ee5-112">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b8ee5-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8ee5-113">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="b8ee5-114">Asynchronní souborový vstup-výstup</span><span class="sxs-lookup"><span data-stu-id="b8ee5-114">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="b8ee5-115">[Postupy: vytvoření seznamu adresářů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b8ee5-115">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="b8ee5-116">Postupy: čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="b8ee5-116">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="b8ee5-117">Postupy: otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="b8ee5-117">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="b8ee5-118">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="b8ee5-118">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="b8ee5-119">Postupy: zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="b8ee5-119">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="b8ee5-120">Postupy: zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="b8ee5-120">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="b8ee5-121">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="b8ee5-121">File and stream I/O</span></span>](index.md)
