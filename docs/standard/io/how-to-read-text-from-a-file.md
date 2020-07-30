---
title: 'Postupy: čtení textu ze souboru'
description: V tomto článku najdete příklady způsobu synchronního nebo asynchronního čtení textu z textového souboru pomocí třídy StreamReader v rozhraní .NET pro aplikace klasické pracovní plochy.
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
ms.openlocfilehash: 0d8dfae67ede779a611204fb333a19defcaee8e6
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382123"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="022e4-103">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="022e4-103">How to: Read text from a file</span></span>
<span data-ttu-id="022e4-104">Následující příklady znázorňují způsob synchronního a asynchronního čtení textu z textového souboru pomocí rozhraní .NET pro aplikace klasické pracovní plochy.</span><span class="sxs-lookup"><span data-stu-id="022e4-104">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="022e4-105">V obou příkladech můžete při vytváření instance <xref:System.IO.StreamReader> třídy zadat relativní nebo absolutní cestu k souboru.</span><span class="sxs-lookup"><span data-stu-id="022e4-105">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="022e4-106">Tyto příklady kódu se nevztahují na vývoj aplikací pro univerzální platformu Windows (UWP), protože prostředí Windows Runtime poskytuje různé typy datových proudů pro čtení a zápis do souborů.</span><span class="sxs-lookup"><span data-stu-id="022e4-106">These code examples do not apply to developing for Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="022e4-107">Příklad, který ukazuje, jak číst text ze souboru v aplikaci UWP, najdete v tématu [rychlý Start: čtení a zápis souborů](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span><span class="sxs-lookup"><span data-stu-id="022e4-107">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="022e4-108">Příklady, které ukazují, jak převést mezi datovými proudy .NET Framework a prostředí Windows Runtime datových proudů, naleznete v tématu [How to: Convert between .NET Framework Streams and prostředí Windows Runtime Streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span><span class="sxs-lookup"><span data-stu-id="022e4-108">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="022e4-109">Příklad: synchronní čtení v konzolové aplikaci</span><span class="sxs-lookup"><span data-stu-id="022e4-109">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="022e4-110">Následující příklad ukazuje synchronní operaci čtení v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="022e4-110">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="022e4-111">Tento příklad otevře textový soubor pomocí čtečky datových proudů, zkopíruje obsah do řetězce a vytvoří výstup řetězce do konzoly.</span><span class="sxs-lookup"><span data-stu-id="022e4-111">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="022e4-112">Příklad předpokládá, že soubor s názvem *TestFile.txt* již existuje ve stejné složce jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="022e4-112">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/sync-console/Program.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/sync-console/Program.vb":::
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="022e4-113">Příklad: asynchronní čtení v aplikaci WPF</span><span class="sxs-lookup"><span data-stu-id="022e4-113">Example: Asynchronous read in a WPF app</span></span>
 <span data-ttu-id="022e4-114">Následující příklad ukazuje asynchronní operaci čtení v aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="022e4-114">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="022e4-115">Příklad předpokládá, že soubor s názvem *TestFile.txt* již existuje ve stejné složce jako aplikace.</span><span class="sxs-lookup"><span data-stu-id="022e4-115">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

:::code language="csharp" source="snippets/how-to-read-text-from-a-file/csharp/async-wpf/MainWindow.xaml.cs":::
:::code language="vb" source="snippets/how-to-read-text-from-a-file/vb/async-wpf/MainWindow.xaml.vb":::
  
## <a name="see-also"></a><span data-ttu-id="022e4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="022e4-116">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="022e4-117">Asynchronní souborový vstup-výstup</span><span class="sxs-lookup"><span data-stu-id="022e4-117">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="022e4-118">[Postupy: vytvoření seznamu adresářů](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="022e4-118">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="022e4-119">Rychlý Start: čtení a zápis souborů</span><span class="sxs-lookup"><span data-stu-id="022e4-119">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [<span data-ttu-id="022e4-120">Postupy: převod mezi .NET Frameworkmi proudy a datovými proudy prostředí Windows Runtime</span><span class="sxs-lookup"><span data-stu-id="022e4-120">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="022e4-121">Postupy: čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="022e4-121">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="022e4-122">Postupy: otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="022e4-122">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="022e4-123">Postupy: zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="022e4-123">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="022e4-124">Postupy: čtení znaků z řetězce</span><span class="sxs-lookup"><span data-stu-id="022e4-124">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="022e4-125">Postupy: zápis znaků do řetězce</span><span class="sxs-lookup"><span data-stu-id="022e4-125">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="022e4-126">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="022e4-126">File and stream I/O</span></span>](index.md)
