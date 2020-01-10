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
ms.openlocfilehash: 42b758eeb36a4c319c3e1f24676cb600d580902e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706605"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="73873-102">Postupy: zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="73873-102">How to: Write text to a file</span></span>
<span data-ttu-id="73873-103">V tomto tématu se dozvíte o různých způsobech zápisu textu do souboru pro aplikaci .NET.</span><span class="sxs-lookup"><span data-stu-id="73873-103">This topic shows different ways to write text to a file for a .NET app.</span></span> 

<span data-ttu-id="73873-104">Následující třídy a metody se obvykle používají k zápisu textu do souboru:</span><span class="sxs-lookup"><span data-stu-id="73873-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="73873-105"><xref:System.IO.StreamWriter> obsahuje metody pro synchronně zapisování do souboru (<xref:System.IO.StreamWriter.Write%2A> a <xref:System.IO.TextWriter.WriteLine%2A>) nebo asynchronně (<xref:System.IO.StreamWriter.WriteAsync%2A> a <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="73873-105"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="73873-106"><xref:System.IO.File> poskytuje statické metody pro zápis textu do souboru, například <xref:System.IO.File.WriteAllLines%2A> a <xref:System.IO.File.WriteAllText%2A>, nebo pro přidání textu do souboru, například <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>a <xref:System.IO.File.AppendText%2A>.</span><span class="sxs-lookup"><span data-stu-id="73873-106"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="73873-107"><xref:System.IO.Path> je pro řetězce, které obsahují informace o cestě k souboru nebo adresáři.</span><span class="sxs-lookup"><span data-stu-id="73873-107"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="73873-108">Obsahuje metodu <xref:System.IO.Path.Combine%2A> a v .NET Core 2,1 a novějších metodách <xref:System.IO.Path.Join%2A> a <xref:System.IO.Path.TryJoin%2A>, které umožňují zřetězení řetězců k sestavení cesty k souboru nebo adresáři.</span><span class="sxs-lookup"><span data-stu-id="73873-108">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="73873-109">Následující příklady znázorňují pouze minimální požadovaný kód.</span><span class="sxs-lookup"><span data-stu-id="73873-109">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="73873-110">Reálné aplikace obvykle poskytují robustnější kontrolu chyb a zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="73873-110">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="73873-111">Příklad: synchronní zápis textu pomocí StreamWriter</span><span class="sxs-lookup"><span data-stu-id="73873-111">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="73873-112">Následující příklad ukazuje, jak použít třídu <xref:System.IO.StreamWriter> k synchronnímu zápisu textu do nového souboru po jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="73873-112">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="73873-113">Vzhledem k tomu, že objekt <xref:System.IO.StreamWriter> je deklarován a vytvořen v příkazu `using`, je vyvolána metoda <xref:System.IO.StreamWriter.Dispose%2A>, která automaticky vyprázdní a uzavře datový proud.</span><span class="sxs-lookup"><span data-stu-id="73873-113">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="73873-114">Příklad: synchronní připojení textu pomocí StreamWriter</span><span class="sxs-lookup"><span data-stu-id="73873-114">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="73873-115">Následující příklad ukazuje, jak použít třídu <xref:System.IO.StreamWriter> k synchronnímu připojení textu k textovému souboru vytvořenému v prvním příkladu.</span><span class="sxs-lookup"><span data-stu-id="73873-115">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>   

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="73873-116">Příklad: asynchronní zápis textu pomocí StreamWriter</span><span class="sxs-lookup"><span data-stu-id="73873-116">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="73873-117">Následující příklad ukazuje, jak asynchronně zapisovat text do nového souboru pomocí třídy <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="73873-117">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="73873-118">Chcete-li vyvolat metodu <xref:System.IO.StreamWriter.WriteAsync%2A>, musí být volání metody v rámci metody `async`.</span><span class="sxs-lookup"><span data-stu-id="73873-118">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="73873-119">C# Příklad vyžaduje C# 7,1 nebo novější, který přidává podporu modifikátoru `async` v vstupním bodě programu.</span><span class="sxs-lookup"><span data-stu-id="73873-119">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span> 

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="73873-120">Příklad: zápis a přidávání textu pomocí třídy File</span><span class="sxs-lookup"><span data-stu-id="73873-120">Example: Write and append text with the File class</span></span>

<span data-ttu-id="73873-121">Následující příklad ukazuje, jak napsat text do nového souboru a připojit nové řádky textu ke stejnému souboru pomocí třídy <xref:System.IO.File>.</span><span class="sxs-lookup"><span data-stu-id="73873-121">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="73873-122">Metody <xref:System.IO.File.WriteAllText%2A> a <xref:System.IO.File.AppendAllLines%2A> otevřou a zavřou soubor automaticky.</span><span class="sxs-lookup"><span data-stu-id="73873-122">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="73873-123">Pokud cesta, kterou zadáte do metody <xref:System.IO.File.WriteAllText%2A>, již existuje, soubor bude přepsán.</span><span class="sxs-lookup"><span data-stu-id="73873-123">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="73873-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73873-124">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="73873-125">Postupy: zobrazení výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="73873-125">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="73873-126">Postupy: čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="73873-126">How to: Read and write to a newly-created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="73873-127">Postupy: otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="73873-127">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="73873-128">Postupy: čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="73873-128">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="73873-129">Vstupně-výstupní operace se soubory a datovým proudem</span><span class="sxs-lookup"><span data-stu-id="73873-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
