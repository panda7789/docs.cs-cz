---
title: 'Postupy: Čtení textu ze souboru'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa6787e018b540dbf19b6da3473b699096cc4ae3
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674396"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="6f42f-102">Postupy: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="6f42f-102">How to: Read text from a file</span></span>
<span data-ttu-id="6f42f-103">Následující příklady znázorňují způsob synchronního a asynchronního čtení textu z textového souboru pomocí rozhraní .NET pro aplikace klasické pracovní plochy.</span><span class="sxs-lookup"><span data-stu-id="6f42f-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="6f42f-104">V obou příkladech je při vytváření instance třídy <xref:System.IO.StreamReader> třídu, zadejte relativní nebo absolutní cesta k souboru.</span><span class="sxs-lookup"><span data-stu-id="6f42f-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="6f42f-105">Tyto příklady kódu se nevztahují na vývoj pro aplikace pro Universal Windows (UPW), protože modul Windows Runtime poskytuje různé stream typy pro čtení a zápis do souborů.</span><span class="sxs-lookup"><span data-stu-id="6f42f-105">These code examples do not apply to developing for Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="6f42f-106">Příklad, který znázorňuje způsob čtení textu ze souboru v aplikaci UWP, naleznete v tématu [rychlý start: Čtení a zápis do souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="6f42f-106">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="6f42f-107">Příklady, které ukazují, jak k převodu mezi datovými proudy rozhraní .NET Framework a datovými proudy Windows Runtime naleznete v tématu [jak: Převod mezi datovými proudy rozhraní .NET Framework a datovými proudy Windows Runtime](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="6f42f-107">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="6f42f-108">Příklad: Synchronní číst v konzolové aplikaci</span><span class="sxs-lookup"><span data-stu-id="6f42f-108">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="6f42f-109">Následující příklad ukazuje operaci synchronního čtení v rámci konzolové aplikace.</span><span class="sxs-lookup"><span data-stu-id="6f42f-109">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="6f42f-110">Tento příklad otevře textový soubor pomocí čtečku datového proudu, zkopíruje obsah na řetězec a vypíše řetězec do konzoly.</span><span class="sxs-lookup"><span data-stu-id="6f42f-110">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6f42f-111">Příklad předpokládá, že soubor s názvem *TestFile.txt* již existuje ve stejné složce jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="6f42f-111">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="6f42f-112">Příklad: Asynchronní čtení v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="6f42f-112">Example: Asynchronous read in a WPF app</span></span> 
 <span data-ttu-id="6f42f-113">Následující příklad ukazuje operaci asynchronního čtení v aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="6f42f-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6f42f-114">Příklad předpokládá, že soubor s názvem *TestFile.txt* již existuje ve stejné složce jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="6f42f-114">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6f42f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6f42f-115">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="6f42f-116">Asynchronní I/O soubory</span><span class="sxs-lookup"><span data-stu-id="6f42f-116">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="6f42f-117">Postupy: Vytváření adresářů</span><span class="sxs-lookup"><span data-stu-id="6f42f-117">How to: Create a directory listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
- [<span data-ttu-id="6f42f-118">Rychlý start: Čtení a zápis do souborů</span><span class="sxs-lookup"><span data-stu-id="6f42f-118">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [<span data-ttu-id="6f42f-119">Postupy: Převod mezi datovými proudy rozhraní .NET Framework a datovými proudy Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="6f42f-119">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="6f42f-120">Postupy: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="6f42f-120">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="6f42f-121">Postupy: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="6f42f-121">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="6f42f-122">Postupy: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="6f42f-122">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="6f42f-123">Postupy: Čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="6f42f-123">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="6f42f-124">Postupy: Zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="6f42f-124">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="6f42f-125">Vstupně-výstupních operací souborů a datových proudů</span><span class="sxs-lookup"><span data-stu-id="6f42f-125">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
