---
title: 'Postupy: čtení textu ze souboru'
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
ms.openlocfilehash: c46ccaf70d4d1aec030fb61bd8b2924d986e19d1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291757"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="341cd-102">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="341cd-102">How to: Read text from a file</span></span>
<span data-ttu-id="341cd-103">Následující příklady znázorňují způsob synchronního a asynchronního čtení textu z textového souboru pomocí rozhraní .NET pro aplikace klasické pracovní plochy.</span><span class="sxs-lookup"><span data-stu-id="341cd-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="341cd-104">V obou příkladech můžete při vytváření instance <xref:System.IO.StreamReader> třídy zadat relativní nebo absolutní cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="341cd-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="341cd-105">Tyto příklady kódu se nevztahují na vývoj aplikací pro univerzální platformu Windows (UWP), protože prostředí Windows Runtime poskytuje různé typy datových proudů pro čtení a zápis do souborů.</span><span class="sxs-lookup"><span data-stu-id="341cd-105">These code examples do not apply to developing for Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="341cd-106">Příklad, který ukazuje, jak číst text ze souboru v aplikaci UWP, najdete v tématu [rychlý Start: čtení a zápis souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="341cd-106">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="341cd-107">Příklady, které ukazují, jak převést mezi datovými proudy .NET Framework a prostředí Windows Runtime datových proudů, naleznete v tématu [How to: Convert between .NET Framework Streams and prostředí Windows Runtime Streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="341cd-107">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="341cd-108">Příklad: synchronní čtení v konzolové aplikaci</span><span class="sxs-lookup"><span data-stu-id="341cd-108">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="341cd-109">Následující příklad ukazuje synchronní operaci čtení v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="341cd-109">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="341cd-110">Tento příklad otevře textový soubor pomocí čtečky datových proudů, zkopíruje obsah do řetězce a vytvoří výstup řetězce do konzoly.</span><span class="sxs-lookup"><span data-stu-id="341cd-110">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="341cd-111">V příkladu se předpokládá, že soubor s názvem *Testfile. txt* už existuje ve stejné složce jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="341cd-111">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="341cd-112">Příklad: asynchronní čtení v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="341cd-112">Example: Asynchronous read in a WPF app</span></span>
 <span data-ttu-id="341cd-113">Následující příklad ukazuje asynchronní operaci čtení v aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="341cd-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="341cd-114">V příkladu se předpokládá, že soubor s názvem *Testfile. txt* už existuje ve stejné složce jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="341cd-114">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="341cd-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="341cd-115">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="341cd-116">Asynchronní souborový vstup-výstup</span><span class="sxs-lookup"><span data-stu-id="341cd-116">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="341cd-117">[Postupy: vytvoření seznamu adresářů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="341cd-117">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="341cd-118">Rychlý Start: čtení a zápis souborů</span><span class="sxs-lookup"><span data-stu-id="341cd-118">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [<span data-ttu-id="341cd-119">Postupy: převod mezi .NET Frameworkmi proudy a datovými proudy prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="341cd-119">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="341cd-120">Postupy: čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="341cd-120">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="341cd-121">Postupy: otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="341cd-121">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="341cd-122">Postupy: zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="341cd-122">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="341cd-123">Postupy: čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="341cd-123">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="341cd-124">Postupy: zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="341cd-124">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="341cd-125">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="341cd-125">File and stream I/O</span></span>](index.md)
