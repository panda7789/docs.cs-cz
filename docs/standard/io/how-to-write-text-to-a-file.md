---
title: 'Postupy: zápis textu do souboru'
ms.date: 01/04/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
ms.openlocfilehash: 395344accf5be416fbcc527e51ba83408f9c5810
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291731"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="80ec9-102">Postupy: zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="80ec9-102">How to: Write text to a file</span></span>
<span data-ttu-id="80ec9-103">V tomto tématu se dozvíte o různých způsobech zápisu textu do souboru pro aplikaci .NET.</span><span class="sxs-lookup"><span data-stu-id="80ec9-103">This topic shows different ways to write text to a file for a .NET app.</span></span>

<span data-ttu-id="80ec9-104">Následující třídy a metody se obvykle používají k zápisu textu do souboru:</span><span class="sxs-lookup"><span data-stu-id="80ec9-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="80ec9-105"><xref:System.IO.StreamWriter>obsahuje metody, jak zapisovat do souboru synchronně ( <xref:System.IO.StreamWriter.Write%2A> a <xref:System.IO.TextWriter.WriteLine%2A> ) nebo asynchronně ( <xref:System.IO.StreamWriter.WriteAsync%2A> a <xref:System.IO.StreamWriter.WriteLineAsync%2A> ).</span><span class="sxs-lookup"><span data-stu-id="80ec9-105"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="80ec9-106"><xref:System.IO.File>poskytuje statické metody pro zápis textu do souboru, například <xref:System.IO.File.WriteAllLines%2A> a <xref:System.IO.File.WriteAllText%2A> , nebo k přidání textu do souboru, například, <xref:System.IO.File.AppendAllLines%2A> <xref:System.IO.File.AppendAllText%2A> a <xref:System.IO.File.AppendText%2A> .</span><span class="sxs-lookup"><span data-stu-id="80ec9-106"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="80ec9-107"><xref:System.IO.Path>je pro řetězce, které obsahují informace o cestě k souboru nebo adresáři.</span><span class="sxs-lookup"><span data-stu-id="80ec9-107"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="80ec9-108">Obsahuje metodu a <xref:System.IO.Path.Combine%2A> v rozhraní .NET Core 2,1 a novějších <xref:System.IO.Path.Join%2A> <xref:System.IO.Path.TryJoin%2A> metody a, které umožňují zřetězení řetězců k sestavení cesty k souboru nebo adresáři.</span><span class="sxs-lookup"><span data-stu-id="80ec9-108">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="80ec9-109">Následující příklady znázorňují pouze minimální požadovaný kód.</span><span class="sxs-lookup"><span data-stu-id="80ec9-109">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="80ec9-110">Reálné aplikace obvykle poskytují robustnější kontrolu chyb a zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="80ec9-110">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="80ec9-111">Příklad: synchronní zápis textu pomocí StreamWriter</span><span class="sxs-lookup"><span data-stu-id="80ec9-111">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="80ec9-112">Následující příklad ukazuje, jak použít <xref:System.IO.StreamWriter> třídu k synchronnímu zápisu textu do nového souboru po jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="80ec9-112">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="80ec9-113">Vzhledem k tomu, že <xref:System.IO.StreamWriter> objekt je deklarován a vytvořen v `using` příkazu, je <xref:System.IO.StreamWriter.Dispose%2A> vyvolána metoda, která automaticky vyprázdní a uzavře datový proud.</span><span class="sxs-lookup"><span data-stu-id="80ec9-113">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="80ec9-114">Příklad: synchronní připojení textu pomocí StreamWriter</span><span class="sxs-lookup"><span data-stu-id="80ec9-114">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="80ec9-115">Následující příklad ukazuje, jak použít <xref:System.IO.StreamWriter> třídu k synchronnímu připojení textu k textovému souboru vytvořenému v prvním příkladu.</span><span class="sxs-lookup"><span data-stu-id="80ec9-115">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="80ec9-116">Příklad: asynchronní zápis textu pomocí StreamWriter</span><span class="sxs-lookup"><span data-stu-id="80ec9-116">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="80ec9-117">Následující příklad ukazuje, jak asynchronně zapisovat text do nového souboru pomocí <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="80ec9-117">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="80ec9-118">Chcete-li vyvolat <xref:System.IO.StreamWriter.WriteAsync%2A> metodu, musí být volání metody v rámci `async` metody.</span><span class="sxs-lookup"><span data-stu-id="80ec9-118">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="80ec9-119">Příklad jazyka C# vyžaduje C# 7,1 nebo novější, který přidává podporu `async` modifikátoru v vstupním bodě programu.</span><span class="sxs-lookup"><span data-stu-id="80ec9-119">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="80ec9-120">Příklad: zápis a přidávání textu pomocí třídy File</span><span class="sxs-lookup"><span data-stu-id="80ec9-120">Example: Write and append text with the File class</span></span>

<span data-ttu-id="80ec9-121">Následující příklad ukazuje, jak napsat text do nového souboru a připojit nové řádky textu ke stejnému souboru pomocí <xref:System.IO.File> třídy.</span><span class="sxs-lookup"><span data-stu-id="80ec9-121">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="80ec9-122"><xref:System.IO.File.WriteAllText%2A>Metody a <xref:System.IO.File.AppendAllLines%2A> otevřou a zavřou soubor automaticky.</span><span class="sxs-lookup"><span data-stu-id="80ec9-122">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="80ec9-123">Pokud cesta, kterou zadáte do <xref:System.IO.File.WriteAllText%2A> metody, již existuje, je soubor přepsán.</span><span class="sxs-lookup"><span data-stu-id="80ec9-123">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="80ec9-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="80ec9-124">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="80ec9-125">Postupy: zobrazení výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="80ec9-125">How to: Enumerate directories and files</span></span>](how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="80ec9-126">Postupy: čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="80ec9-126">How to: Read and write to a newly-created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="80ec9-127">Postupy: otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="80ec9-127">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="80ec9-128">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="80ec9-128">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)
- [<span data-ttu-id="80ec9-129">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="80ec9-129">File and stream I/O</span></span>](index.md)
