---
title: 'Postup: Čtení textu ze souboru'
ms.date: 01/03/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
ms.openlocfilehash: 8676e5f0acd0646b4854df7dde060ec15548ec3e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155721"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="86f1a-102">Postup: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="86f1a-102">How to: Read text from a file</span></span>
<span data-ttu-id="86f1a-103">Následující příklady znázorňují způsob synchronního a asynchronního čtení textu z textového souboru pomocí rozhraní .NET pro aplikace klasické pracovní plochy.</span><span class="sxs-lookup"><span data-stu-id="86f1a-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="86f1a-104">V obou příkladech při vytváření instance <xref:System.IO.StreamReader> třídy zadáte relativní nebo absolutní cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="86f1a-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="86f1a-105">Tyto příklady kódu se nevztahují na vývoj aplikací pro univerzální Windows (UPW), protože prostředí Windows Runtime poskytuje různé typy datových proudů pro čtení a zápis do souborů.</span><span class="sxs-lookup"><span data-stu-id="86f1a-105">These code examples do not apply to developing for Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="86f1a-106">Příklad, který ukazuje, jak číst text ze souboru v aplikaci UPW, najdete v [tématu Úvodní příručka: Čtení a zápis souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="86f1a-106">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="86f1a-107">Příklady, které ukazují, jak převést mezi datovými proudy rozhraní .NET Framework a datovými proudy prostředí Windows Runtime, naleznete v [tématu How to: Convert between .NET Framework streams and Windows Runtime streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="86f1a-107">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="86f1a-108">Příklad: Synchronní čtení v konzolové aplikaci</span><span class="sxs-lookup"><span data-stu-id="86f1a-108">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="86f1a-109">Následující příklad ukazuje synchronní operaci čtení v rámci konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="86f1a-109">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="86f1a-110">Tento příklad otevře textový soubor pomocí čtečky datových proudů, zkopíruje obsah do řetězce a výstupy řetězec do konzoly.</span><span class="sxs-lookup"><span data-stu-id="86f1a-110">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="86f1a-111">Příklad předpokládá, že soubor s názvem *TestFile.txt* již existuje ve stejné složce jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="86f1a-111">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="86f1a-112">Příklad: Asynchronní čtení v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="86f1a-112">Example: Asynchronous read in a WPF app</span></span>
 <span data-ttu-id="86f1a-113">Následující příklad ukazuje asynchronní operaci čtení v aplikaci WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="86f1a-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="86f1a-114">Příklad předpokládá, že soubor s názvem *TestFile.txt* již existuje ve stejné složce jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="86f1a-114">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="86f1a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="86f1a-115">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="86f1a-116">Vstupně-nosný soubor asynchronní soubor</span><span class="sxs-lookup"><span data-stu-id="86f1a-116">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="86f1a-117">[Postup: Vytvoření výpisu adresáře](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="86f1a-117">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="86f1a-118">Úvodní příručka: Čtení a zápis souborů</span><span class="sxs-lookup"><span data-stu-id="86f1a-118">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [<span data-ttu-id="86f1a-119">Postup: Převod mezi datovými proudy rozhraní .NET Framework a Datovými proudy prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="86f1a-119">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="86f1a-120">Postup: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="86f1a-120">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="86f1a-121">Postup: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="86f1a-121">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="86f1a-122">Postup: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="86f1a-122">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="86f1a-123">Postup: Čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="86f1a-123">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="86f1a-124">Postup: Zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="86f1a-124">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="86f1a-125">Vstupně-tono-videa</span><span class="sxs-lookup"><span data-stu-id="86f1a-125">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
