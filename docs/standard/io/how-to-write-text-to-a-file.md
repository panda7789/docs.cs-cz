---
title: 'Postupy: Zápis textu do souboru'
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59b33c24c2821d0aef17f5feb67c1178810b939e
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647786"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="b8f3d-102">Postupy: Zápis textu do souboru</span><span class="sxs-lookup"><span data-stu-id="b8f3d-102">How to: Write text to a file</span></span>
<span data-ttu-id="b8f3d-103">Toto téma ukazuje různé způsoby zápisu textu do souborů pro aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-103">This topic shows different ways to write text to a file for a .NET app.</span></span> 

<span data-ttu-id="b8f3d-104">Následující třídy a metody se obvykle používají k zápisu textu do souboru:</span><span class="sxs-lookup"><span data-stu-id="b8f3d-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
- <span data-ttu-id="b8f3d-105"><xref:System.IO.StreamWriter> obsahuje metody pro zápis do souboru synchronně (<xref:System.IO.StreamWriter.Write%2A> a <xref:System.IO.TextWriter.WriteLine%2A>) nebo asynchronně (<xref:System.IO.StreamWriter.WriteAsync%2A> a <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span><span class="sxs-lookup"><span data-stu-id="b8f3d-105"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
- <span data-ttu-id="b8f3d-106"><xref:System.IO.File> poskytuje statické metody pro zápis textu do souboru, například <xref:System.IO.File.WriteAllLines%2A> a <xref:System.IO.File.WriteAllText%2A>, nebo přidat text do souboru, například <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, a <xref:System.IO.File.AppendText%2A>.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-106"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="b8f3d-107"><xref:System.IO.Path> slouží k řetězci, které obsahují informace o cestě souboru nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-107"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="b8f3d-108">Obsahuje <xref:System.IO.Path.Combine%2A> metoda a, v .NET Core 2.1 a později, <xref:System.IO.Path.Join%2A> a <xref:System.IO.Path.TryJoin%2A> metody, které umožňují zřetězení řetězců k sestavení cesty k souboru nebo adresáře.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-108">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="b8f3d-109">Následující příklady ukazují jenom minimální množství kódu, které jsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-109">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="b8f3d-110">Reálné aplikace obvykle poskytuje robustnější kontroly chyb a zpracování výjimek.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-110">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="b8f3d-111">Příklad: Synchronně napsat text pomocí třídy StreamWriter</span><span class="sxs-lookup"><span data-stu-id="b8f3d-111">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="b8f3d-112">Následující příklad ukazuje způsob použití <xref:System.IO.StreamWriter> tříd synchronně zápisu textu na nový řádek jeden soubor současně.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-112">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="b8f3d-113">Protože <xref:System.IO.StreamWriter> objekt je deklarovaný a instance v `using` příkaz, <xref:System.IO.StreamWriter.Dispose%2A> je vyvolána metoda, která automaticky vyprázdní a zavře datový proud.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-113">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="b8f3d-114">Příklad: Synchronně připojit text pomocí třídy StreamWriter</span><span class="sxs-lookup"><span data-stu-id="b8f3d-114">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="b8f3d-115">Následující příklad ukazuje způsob použití <xref:System.IO.StreamWriter> tříd synchronně přidat text do textového souboru vytvořeného v prvním příkladu.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-115">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>   

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="b8f3d-116">Příklad: Asynchronně napsat text pomocí třídy StreamWriter</span><span class="sxs-lookup"><span data-stu-id="b8f3d-116">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="b8f3d-117">Následující příklad ukazuje způsob asynchronního zápisu textu do nového souboru pomocí <xref:System.IO.StreamWriter> třídy.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-117">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="b8f3d-118">K vyvolání <xref:System.IO.StreamWriter.WriteAsync%2A> metody volání metody, které musí být v rámci `async` metody.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-118">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="b8f3d-119">C# Příklad vyžaduje C# 7.1 nebo novější, který přidává podporu pro `async` modifikátor na vstupní bod programu.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-119">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span> 

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="b8f3d-120">Příklad: Zapsat a připojit text pomocí třídy souboru</span><span class="sxs-lookup"><span data-stu-id="b8f3d-120">Example: Write and append text with the File class</span></span>

<span data-ttu-id="b8f3d-121">Následující příklad ukazuje, jak zápis textu do nového souboru a přidávat nové řádky textu do stejného souboru pomocí <xref:System.IO.File> třídy.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-121">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="b8f3d-122"><xref:System.IO.File.WriteAllText%2A> a <xref:System.IO.File.AppendAllLines%2A> metod otevřete a zavřete soubor automaticky.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-122">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="b8f3d-123">Pokud cesta poskytnete <xref:System.IO.File.WriteAllText%2A> metoda již existuje, přepíše se.</span><span class="sxs-lookup"><span data-stu-id="b8f3d-123">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="b8f3d-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8f3d-124">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b8f3d-125">Postupy: Vytvoření výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="b8f3d-125">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="b8f3d-126">Postupy: Čtení a zápis do nově vytvořeného datového souboru</span><span class="sxs-lookup"><span data-stu-id="b8f3d-126">How to: Read and write to a newly-created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="b8f3d-127">Postupy: Otevření a připojení k souboru protokolu</span><span class="sxs-lookup"><span data-stu-id="b8f3d-127">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="b8f3d-128">Postupy: Čtení textu ze souboru</span><span class="sxs-lookup"><span data-stu-id="b8f3d-128">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="b8f3d-129">Vstupně-výstupních operací souborů a datových proudů</span><span class="sxs-lookup"><span data-stu-id="b8f3d-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)