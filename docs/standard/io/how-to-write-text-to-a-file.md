---
title: 'Postup: Zápis textu do souboru'
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
ms.openlocfilehash: ba1c1815f0e49c02d1f0ee3c48ba01b7c2f5e727
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160245"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="d1464-102">Postup: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="d1464-102">How to: Write text to a file</span></span>
<span data-ttu-id="d1464-103">Toto téma ukazuje různé způsoby zápisu textu do souboru aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="d1464-103">This topic shows different ways to write text to a file for a .NET app.</span></span>

<span data-ttu-id="d1464-104">Následující třídy a metody se obvykle používají k zápisu textu do souboru:</span><span class="sxs-lookup"><span data-stu-id="d1464-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="d1464-105"><xref:System.IO.StreamWriter>obsahuje metody pro zápis do souboru<xref:System.IO.StreamWriter.Write%2A> <xref:System.IO.TextWriter.WriteLine%2A>synchronně ( a )<xref:System.IO.StreamWriter.WriteAsync%2A> <xref:System.IO.StreamWriter.WriteLineAsync%2A>nebo asynchronně ( a ).</span><span class="sxs-lookup"><span data-stu-id="d1464-105"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="d1464-106"><xref:System.IO.File>Poskytuje statické metody pro zápis textu <xref:System.IO.File.WriteAllLines%2A> do <xref:System.IO.File.WriteAllText%2A>souboru, například a , <xref:System.IO.File.AppendAllLines%2A>nebo <xref:System.IO.File.AppendAllText%2A>pro <xref:System.IO.File.AppendText%2A>připojení textu k souboru, například , a .</span><span class="sxs-lookup"><span data-stu-id="d1464-106"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="d1464-107"><xref:System.IO.Path>je pro řetězce, které mají informace o cestě k souboru nebo adresáři.</span><span class="sxs-lookup"><span data-stu-id="d1464-107"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="d1464-108">Obsahuje metodu <xref:System.IO.Path.Combine%2A> a v rozhraní .NET Core 2.1 a novější metody <xref:System.IO.Path.Join%2A> a, <xref:System.IO.Path.TryJoin%2A> které umožňují zřetězení řetězců k vytvoření cesty k souboru nebo adresáři.</span><span class="sxs-lookup"><span data-stu-id="d1464-108">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="d1464-109">Následující příklady ukazují pouze minimální množství kódu potřebné.</span><span class="sxs-lookup"><span data-stu-id="d1464-109">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="d1464-110">Aplikace reálného světa obvykle poskytuje robustnější kontrolu chyb a zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="d1464-110">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="d1464-111">Příklad: Synchronně psát text s StreamWriter</span><span class="sxs-lookup"><span data-stu-id="d1464-111">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="d1464-112">Následující příklad ukazuje, jak <xref:System.IO.StreamWriter> použít třídu synchronně psát text do nového souboru po jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="d1464-112">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="d1464-113">Vzhledem <xref:System.IO.StreamWriter> k tomu, že objekt `using` je deklarován a instancivaci v příkazu, <xref:System.IO.StreamWriter.Dispose%2A> metoda je vyvolána, která automaticky vyprázdní a zavře datový proud.</span><span class="sxs-lookup"><span data-stu-id="d1464-113">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="d1464-114">Příklad: Synchronně připojit text s StreamWriter</span><span class="sxs-lookup"><span data-stu-id="d1464-114">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="d1464-115">Následující příklad ukazuje, jak <xref:System.IO.StreamWriter> použít třídu synchronně připojit text do textového souboru vytvořeného v prvním příkladu.</span><span class="sxs-lookup"><span data-stu-id="d1464-115">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="d1464-116">Příklad: Asynchronně psát text s StreamWriter</span><span class="sxs-lookup"><span data-stu-id="d1464-116">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="d1464-117">Následující příklad ukazuje, jak asynchronně zapisovat text <xref:System.IO.StreamWriter> do nového souboru pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="d1464-117">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="d1464-118">Chcete-li <xref:System.IO.StreamWriter.WriteAsync%2A> vyvolat metodu, volání `async` metody musí být v rámci metody.</span><span class="sxs-lookup"><span data-stu-id="d1464-118">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="d1464-119">Příklad Jazyka C# vyžaduje c# 7.1 nebo `async` novější, který přidává podporu pro modifikátor na vstupní bod programu.</span><span class="sxs-lookup"><span data-stu-id="d1464-119">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span>

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="d1464-120">Příklad: Zápis a připojení textu s třídou File</span><span class="sxs-lookup"><span data-stu-id="d1464-120">Example: Write and append text with the File class</span></span>

<span data-ttu-id="d1464-121">Následující příklad ukazuje, jak psát text do nového souboru a připojit <xref:System.IO.File> nové řádky textu do stejného souboru pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="d1464-121">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="d1464-122">Metody <xref:System.IO.File.WriteAllText%2A> <xref:System.IO.File.AppendAllLines%2A> a automaticky otevírají a zavírají soubor.</span><span class="sxs-lookup"><span data-stu-id="d1464-122">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="d1464-123">Pokud cesta, kterou <xref:System.IO.File.WriteAllText%2A> zadáte k metodě již existuje, soubor je přepsán.</span><span class="sxs-lookup"><span data-stu-id="d1464-123">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)]
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="d1464-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1464-124">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d1464-125">Postup: Výčet adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="d1464-125">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="d1464-126">Postup: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="d1464-126">How to: Read and write to a newly-created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="d1464-127">Postup: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="d1464-127">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="d1464-128">Postup: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="d1464-128">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="d1464-129">Vstupně-tono-videa</span><span class="sxs-lookup"><span data-stu-id="d1464-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
