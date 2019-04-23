---
title: Zápis paralelního jednoduchý program pomocí paralelní ForEach
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 599432af178031a85dea4155a8fd2923f879a600
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59427354"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="b99d3-102">Postupy: Zápis jednoduché smyčky Parallel.ForEach</span><span class="sxs-lookup"><span data-stu-id="b99d3-102">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="b99d3-103">Tento příklad ukazuje způsob použití <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> smyčky umožňující datový paralelismus nad <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="b99d3-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="b99d3-104">Tato dokumentace používá lambda výrazy k definování delegátů v PLINQ.</span><span class="sxs-lookup"><span data-stu-id="b99d3-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="b99d3-105">Pokud nejste obeznámeni s lambda výrazy v C# nebo Visual Basic, naleznete v tématu [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="b99d3-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="b99d3-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b99d3-106">Example</span></span>

<span data-ttu-id="b99d3-107">Tento příklad předpokládá, že máte několik jpg soubory *C:\Users\Public\Pictures\Sample obrázky* složku a vytvoří novou podsložku s názvem *změněné*.</span><span class="sxs-lookup"><span data-stu-id="b99d3-107">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="b99d3-108">Při spuštění v příkladu se otočí každý obrázek JPG v *vzorové obrázky* a ukládá ji do *změněné*.</span><span class="sxs-lookup"><span data-stu-id="b99d3-108">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="b99d3-109">Můžete upravit podle potřeby tyto dvě cesty.</span><span class="sxs-lookup"><span data-stu-id="b99d3-109">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="b99d3-110">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> smyčky funguje stejně jako <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> smyčky.</span><span class="sxs-lookup"><span data-stu-id="b99d3-110">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="b99d3-111">Smyčky oddílů zdrojové kolekce a plánuje práci z více vláken, které jsou založené na prostředí systému.</span><span class="sxs-lookup"><span data-stu-id="b99d3-111">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="b99d3-112">Více procesorů v systému, tím rychleji paralelní metoda pracuje.</span><span class="sxs-lookup"><span data-stu-id="b99d3-112">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="b99d3-113">Pro některé zdroje kolekce může být rychlejší, v závislosti na velikosti zdroje a na druhu práce, kterou provádí smyčky sekvenční smyčka.</span><span class="sxs-lookup"><span data-stu-id="b99d3-113">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="b99d3-114">Další informace o výkonu, naleznete v tématu [Potenciální nástrahy paralelismu dat a úloh](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span><span class="sxs-lookup"><span data-stu-id="b99d3-114">For more information about performance, see [Potential pitfalls in data and task parallelism](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)</span></span>

<span data-ttu-id="b99d3-115">Další informace o paralelních smyček, naleznete v tématu [jak: Zápis jednoduché smyčky Parallel.for](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="b99d3-115">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="b99d3-116">Chcete-li použít <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> v obecné kolekci, můžete použít <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> metodu rozšíření k převodu kolekce na obecné kolekce, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b99d3-116">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="b99d3-117">Paralelní LINQ (PLINQ) můžete také použít pro paralelní zpracování <xref:System.Collections.Generic.IEnumerable%601> zdrojů.</span><span class="sxs-lookup"><span data-stu-id="b99d3-117">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="b99d3-118">PLINQ umožňuje používat deklarativní syntaxe vyjádřit chování smyčky.</span><span class="sxs-lookup"><span data-stu-id="b99d3-118">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="b99d3-119">Další informace najdete v tématu [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="b99d3-119">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="b99d3-120">Kompilace a spuštění kódu</span><span class="sxs-lookup"><span data-stu-id="b99d3-120">Compile and run the code</span></span>

<span data-ttu-id="b99d3-121">Kód lze zkompilovat jako konzolovou aplikaci pro rozhraní .NET Framework nebo konzolové aplikace pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b99d3-121">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="b99d3-122">V sadě Visual Studio jsou jazyka Visual Basic a C# konzole šablony aplikací pro stolní počítače Windows a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b99d3-122">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="b99d3-123">Z příkazového řádku, můžete použít .NET Core a jeho nástrojů rozhraní příkazového řádku (například `dotnet new console` nebo `dotnet new console -lang vb`), nebo můžete vytvořit soubor a pomocí příkazového řádku kompilátoru pro aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b99d3-123">From the command line, you can use either .NET Core and its CLI tools (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="b99d3-124">Pro projekt .NET Core, musí odkazovat **System.Drawing.Common** balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="b99d3-124">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="b99d3-125">V sadě Visual Studio pomocí Správce balíčků NuGet nainstalujte balíček.</span><span class="sxs-lookup"><span data-stu-id="b99d3-125">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="b99d3-126">Alternativně můžete přidat odkaz na balíček ve vaší \*.csproj nebo \*souboru .vbproj:</span><span class="sxs-lookup"><span data-stu-id="b99d3-126">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>
 
```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="b99d3-127">Chcete-li spustit konzolovou aplikaci .NET Core z příkazového řádku, použijte `dotnet run` ze složky, která obsahuje vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b99d3-127">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="b99d3-128">Chcete-li spustit konzolovou aplikaci v sadě Visual Studio, stiskněte **F5**.</span><span class="sxs-lookup"><span data-stu-id="b99d3-128">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b99d3-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b99d3-129">See also</span></span>

- [<span data-ttu-id="b99d3-130">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="b99d3-130">Data parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="b99d3-131">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="b99d3-131">Parallel programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="b99d3-132">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="b99d3-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
