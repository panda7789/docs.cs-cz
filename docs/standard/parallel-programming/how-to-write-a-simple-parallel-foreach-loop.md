---
title: Napsat jednoduchý paralelní program pomocí Parallel.ForEach
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 02b94b673dc4468e68a1dadd83aab0e3bfcfaa16
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160297"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="9dc05-102">Postup: Napište jednoduchou smyčku Parallel.ForEach</span><span class="sxs-lookup"><span data-stu-id="9dc05-102">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="9dc05-103">Tento příklad ukazuje, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> jak použít smyčku k <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> povolení paralelismu dat přes všechny nebo zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="9dc05-103">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="9dc05-104">Tato dokumentace používá lambda výrazy definovat delegáty v PLINQ.</span><span class="sxs-lookup"><span data-stu-id="9dc05-104">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="9dc05-105">Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, naleznete [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="9dc05-105">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="9dc05-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="9dc05-106">Example</span></span>

<span data-ttu-id="9dc05-107">Tento příklad předpokládá, že máte několik souborů JPG ve složce *C:\Users\Public\Pictures\Sample Pictures* a vytvoří tenovou podsložku s názvem *Změněno*.</span><span class="sxs-lookup"><span data-stu-id="9dc05-107">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="9dc05-108">Při spuštění příkladu otočí každý .jpg obraz v *ukázkové obrázky* a uloží jej *do změnit*.</span><span class="sxs-lookup"><span data-stu-id="9dc05-108">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="9dc05-109">Podle potřeby můžete upravit dvě cesty.</span><span class="sxs-lookup"><span data-stu-id="9dc05-109">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="9dc05-110">Smyčka <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> funguje jako <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> smyčka.</span><span class="sxs-lookup"><span data-stu-id="9dc05-110">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="9dc05-111">Smyčka rozdělí zdrojovou kolekci a naplánuje práci na více vláknech na základě systémového prostředí.</span><span class="sxs-lookup"><span data-stu-id="9dc05-111">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="9dc05-112">Čím více procesorů v systému, tím rychlejší paralelní metoda běží.</span><span class="sxs-lookup"><span data-stu-id="9dc05-112">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="9dc05-113">Pro některé zdrojové kolekce může být sekvenční smyčka rychlejší, v závislosti na velikosti zdroje a druhu práce, kterou smyčka provádí.</span><span class="sxs-lookup"><span data-stu-id="9dc05-113">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="9dc05-114">Další informace o výkonu naleznete [v tématu Potenciální úskalí v datech a paralelismu úloh](potential-pitfalls-in-data-and-task-parallelism.md).</span><span class="sxs-lookup"><span data-stu-id="9dc05-114">For more information about performance, see [Potential pitfalls in data and task parallelism](potential-pitfalls-in-data-and-task-parallelism.md).</span></span>

<span data-ttu-id="9dc05-115">Další informace o paralelních smyčkách naleznete v [tématu How to: Write a simple Parallel.For loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="9dc05-115">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="9dc05-116">Chcete-li použít <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> s neobecnou kolekci, můžete použít metodu <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> rozšíření převést kolekci na obecnou kolekci, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9dc05-116">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="9dc05-117">Paralelní LINQ (PLINQ) můžete také použít k <xref:System.Collections.Generic.IEnumerable%601> paralelizaci zpracování zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="9dc05-117">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="9dc05-118">PLINQ umožňuje použít syntaxi deklarativního dotazu k vyjádření chování smyčky.</span><span class="sxs-lookup"><span data-stu-id="9dc05-118">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="9dc05-119">Další informace naleznete [v tématu Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="9dc05-119">For more information, see [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="9dc05-120">Kompilace a spuštění kódu</span><span class="sxs-lookup"><span data-stu-id="9dc05-120">Compile and run the code</span></span>

<span data-ttu-id="9dc05-121">Kód můžete zkompilovat jako konzolovou aplikaci pro rozhraní .NET Framework nebo jako konzolovou aplikaci pro rozhraní .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9dc05-121">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="9dc05-122">V sadě Visual Studio existují šablony aplikací visual basic a c# konzoly pro Windows Desktop a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9dc05-122">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="9dc05-123">Z příkazového řádku můžete použít příkazy rozhraní PŘÍKAZU .NET `dotnet new console` `dotnet new console -lang vb`Core (například nebo ) nebo můžete vytvořit soubor a použít kompilátor příkazového řádku pro aplikaci rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9dc05-123">From the command line, you can use either the .NET Core CLI commands (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="9dc05-124">Pro projekt .NET Core je nutné odkazovat na balíček **System.Drawing.Common** NuGet.</span><span class="sxs-lookup"><span data-stu-id="9dc05-124">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="9dc05-125">V sadě Visual Studio použijte K instalaci balíčku Správce balíčků NuGet.</span><span class="sxs-lookup"><span data-stu-id="9dc05-125">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="9dc05-126">Případně můžete přidat odkaz na balíček \*v souboru \*.csproj nebo .vbproj:</span><span class="sxs-lookup"><span data-stu-id="9dc05-126">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="9dc05-127">Chcete-li spustit aplikaci konzoly .NET `dotnet run` Core z příkazového řádku, použijte ze složky, která obsahuje vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9dc05-127">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="9dc05-128">Chcete-li spustit konzolovou aplikaci z aplikace Visual Studio, stiskněte **klávesu F5**.</span><span class="sxs-lookup"><span data-stu-id="9dc05-128">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="9dc05-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="9dc05-129">See also</span></span>

- [<span data-ttu-id="9dc05-130">Paralelismus dat</span><span class="sxs-lookup"><span data-stu-id="9dc05-130">Data parallelism</span></span>](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="9dc05-131">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="9dc05-131">Parallel programming</span></span>](../../../docs/standard/parallel-programming/index.md)
- [<span data-ttu-id="9dc05-132">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="9dc05-132">Parallel LINQ (PLINQ)</span></span>](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
