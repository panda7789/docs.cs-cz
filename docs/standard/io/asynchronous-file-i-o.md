---
title: Asynchronní I/O soubory
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET Framework], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b045ad7e9a808b3e2b8d89750001ec9c4a33c005
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/18/2019
ms.locfileid: "67170761"
---
# <a name="asynchronous-file-io"></a><span data-ttu-id="14b62-102">Asynchronní I/O soubory</span><span class="sxs-lookup"><span data-stu-id="14b62-102">Asynchronous File I/O</span></span>

<span data-ttu-id="14b62-103">Asynchronní operace umožňují provádět vstupně-výstupní operace náročné na prostředky bez blokování hlavního vlákna.</span><span class="sxs-lookup"><span data-stu-id="14b62-103">Asynchronous operations enable you to perform resource-intensive I/O operations without blocking the main thread.</span></span> <span data-ttu-id="14b62-104">Toto posouzení výkonu je obzvláště důležité v [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace nebo aplikace klasické pracovní plochy, kde časově náročná operace může zablokovat vlákno uživatelského rozhraní a ujistěte se, aplikace se pak jeví jako nefunkční.</span><span class="sxs-lookup"><span data-stu-id="14b62-104">This performance consideration is particularly important in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app or desktop app where a time-consuming stream operation can block the UI thread and make your app appear as if it is not working.</span></span>

<span data-ttu-id="14b62-105">Od verze rozhraní .NET Framework 4.5, zahrnují vstupně-výstupní typy asynchronní metody pro zjednodušení asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="14b62-105">Starting with the .NET Framework 4.5, the I/O types include async methods to simplify asynchronous operations.</span></span> <span data-ttu-id="14b62-106">Asynchronní metoda obsahuje v názvu parametr `Async`, jako například <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A> a <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span><span class="sxs-lookup"><span data-stu-id="14b62-106">An async method contains `Async` in its name, such as <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A>, and <xref:System.IO.TextReader.ReadToEndAsync%2A>.</span></span> <span data-ttu-id="14b62-107">Asynchronní metody jsou implementovány ve třídách datových proudů, jako například <xref:System.IO.Stream>, <xref:System.IO.FileStream> a <xref:System.IO.MemoryStream>, a ve třídách, které se používají pro čtení nebo zápis datových proudů, jako například <xref:System.IO.TextReader> a <xref:System.IO.TextWriter>.</span><span class="sxs-lookup"><span data-stu-id="14b62-107">These async methods are implemented on stream classes, such as <xref:System.IO.Stream>, <xref:System.IO.FileStream>, and <xref:System.IO.MemoryStream>, and on classes that are used for reading from or writing to streams, such <xref:System.IO.TextReader> and <xref:System.IO.TextWriter>.</span></span>

<span data-ttu-id="14b62-108">V rozhraní .NET Framework 4 a předchozích verzích je pro implementaci asynchronních vstupně-výstupních operací nutné použít metody, jako jsou <xref:System.IO.Stream.BeginRead%2A> a <xref:System.IO.Stream.EndRead%2A>.</span><span class="sxs-lookup"><span data-stu-id="14b62-108">In the .NET Framework 4 and earlier versions, you have to use methods such as <xref:System.IO.Stream.BeginRead%2A> and <xref:System.IO.Stream.EndRead%2A> to implement asynchronous I/O operations.</span></span> <span data-ttu-id="14b62-109">Tyto metody jsou stále k dispozici v rozhraní .NET Framework 4.5 důvodu podpory původního kódu; však asynchronní metody umožňují snadnější implementaci asynchronních operací vstupně-výstupních operací.</span><span class="sxs-lookup"><span data-stu-id="14b62-109">These methods are still available in the .NET Framework 4.5 to support legacy code; however, the async methods help you implement asynchronous I/O operations more easily.</span></span>

<span data-ttu-id="14b62-110">C# a Visual Basic mají dvě klíčová slova pro asynchronní programování:</span><span class="sxs-lookup"><span data-stu-id="14b62-110">C# and Visual Basic each have two keywords for asynchronous programming:</span></span>

- <span data-ttu-id="14b62-111">Modifikátor `Async` (Visual Basic) nebo `async` (jazyk C#), který se používá pro označení metody, jež obsahuje asynchronní operaci.</span><span class="sxs-lookup"><span data-stu-id="14b62-111">`Async` (Visual Basic) or `async` (C#) modifier, which is used to mark a method that contains an asynchronous operation.</span></span>

- <span data-ttu-id="14b62-112">Modifikátor `Await` (Visual Basic) nebo `await` (jazyk C#), který se používá pro výsledek asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="14b62-112">`Await` (Visual Basic) or `await` (C#) operator, which is applied to the result of an async method.</span></span>

<span data-ttu-id="14b62-113">Pro implementaci asynchronních vstupně-výstupních operací je třeba použít klíčová slova spolu s asynchronními metodami, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="14b62-113">To implement asynchronous I/O operations, use these keywords in conjunction with the async methods, as shown in the following examples.</span></span> <span data-ttu-id="14b62-114">Další informace najdete v tématu [asynchronní programování pomocí modifikátoru async a operátoru await (C#)](../../csharp/programming-guide/concepts/async/index.md) nebo [Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="14b62-114">For more information, see [Asynchronous programming with async and await (C#)](../../csharp/programming-guide/concepts/async/index.md) or [Asynchronous Programming with Async and Await (Visual Basic)](../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="14b62-115">Následující příklad znázorňuje, jakým způsobem lze objekty <xref:System.IO.FileStream> použít pro asynchronní kopírování souborů z jednoho adresáře do druhého.</span><span class="sxs-lookup"><span data-stu-id="14b62-115">The following example demonstrates how to use two <xref:System.IO.FileStream> objects to copy files asynchronously from one directory to another.</span></span> <span data-ttu-id="14b62-116">Je třeba poznamenat, že obslužná rutina <xref:System.Web.UI.WebControls.Button.Click> pro ovládací prvek <xref:System.Windows.Controls.Button> je označena modifikátorem `async`, jelikož volá asynchronní metodu.</span><span class="sxs-lookup"><span data-stu-id="14b62-116">Notice that the <xref:System.Web.UI.WebControls.Button.Click> event handler for the <xref:System.Windows.Controls.Button> control is marked with the `async` modifier because it calls an asynchronous method.</span></span>

[!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
[!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]

<span data-ttu-id="14b62-117">Následující příklad se podobá předchozímu příkladu, ale pro asynchronní čtení a zápis obsahu textového souboru používá objekty <xref:System.IO.StreamReader> a <xref:System.IO.StreamWriter>.</span><span class="sxs-lookup"><span data-stu-id="14b62-117">The next example is similar to the previous one but uses <xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> objects to read and write the contents of a text file asynchronously.</span></span>

[!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
[!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]

<span data-ttu-id="14b62-118">Následující příklad znázorňuje soubor kódu na pozadí a soubor XAML, které se používají pro otevření souboru jako <xref:System.IO.Stream> v aplikaci pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] a jehož obsah se přečte pomocí instance třídy <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="14b62-118">The next example shows the code-behind file and the XAML file that are used to open a file as a <xref:System.IO.Stream> in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, and read its contents by using an instance of the <xref:System.IO.StreamReader> class.</span></span> <span data-ttu-id="14b62-119">Pro otevření souboru jako datového proudu a přečtení jeho obsahu se používají asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="14b62-119">It uses asynchronous methods to open the file as a stream and to read its contents.</span></span>

[!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
[!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]

[!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]

## <a name="see-also"></a><span data-ttu-id="14b62-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14b62-120">See also</span></span>

- <xref:System.IO.Stream>
- [<span data-ttu-id="14b62-121">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="14b62-121">File and Stream I/O</span></span>](index.md)
- [<span data-ttu-id="14b62-122">Asynchronní programování pomocí modifikátoru async a operátoru await (C#)</span><span class="sxs-lookup"><span data-stu-id="14b62-122">Asynchronous programming with async and await (C#)</span></span>](../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="14b62-123">Asynchronní programování pomocí modifikátoru Async a operátoru Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14b62-123">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
