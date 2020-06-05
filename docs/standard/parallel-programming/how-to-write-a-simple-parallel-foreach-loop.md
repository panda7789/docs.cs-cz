---
title: Zápis jednoduchého paralelního programu pomocí Parallel. ForEach
description: V tomto článku se dozvíte, jak povolit datovou paralelismuy v .NET. Napište smyčku Parallel. ForEach přes libovolný zdroj dat IEnumerable nebo IEnumerable <T> .
ms.date: 02/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
ms.openlocfilehash: 59c8710a8e3fc878b2ceded8595f7f3319d4c953
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447196"
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a><span data-ttu-id="78cec-104">Postupy: zápis jednoduché smyčky Parallel. ForEach</span><span class="sxs-lookup"><span data-stu-id="78cec-104">How to: Write a simple Parallel.ForEach loop</span></span>

<span data-ttu-id="78cec-105">Tento příklad ukazuje, jak použít <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> smyčku pro povolení datové paralelismuy prostřednictvím libovolného <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> zdroje dat nebo.</span><span class="sxs-lookup"><span data-stu-id="78cec-105">This example shows how to use a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop to enable data parallelism over any <xref:System.Collections.IEnumerable?displayProperty=nameWithType> or <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> data source.</span></span>

> [!NOTE]
> <span data-ttu-id="78cec-106">Tato dokumentace používá lambda výrazy k definování delegátů v PLINQ.</span><span class="sxs-lookup"><span data-stu-id="78cec-106">This documentation uses lambda expressions to define delegates in PLINQ.</span></span> <span data-ttu-id="78cec-107">Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="78cec-107">If you are not familiar with lambda expressions in C# or Visual Basic, see [Lambda expressions in PLINQ and TPL](lambda-expressions-in-plinq-and-tpl.md).</span></span>

## <a name="example"></a><span data-ttu-id="78cec-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="78cec-108">Example</span></span>

<span data-ttu-id="78cec-109">V tomto příkladu se předpokládá, že máte ve složce *C:\Users\Public\Pictures\Sample obrázky* několik souborů. jpg a vytvoříme novou podsložku s názvem *Modified*.</span><span class="sxs-lookup"><span data-stu-id="78cec-109">This example assumes you have several .jpg files in a *C:\Users\Public\Pictures\Sample Pictures* folder and creates a new sub-folder named *Modified*.</span></span> <span data-ttu-id="78cec-110">Když spustíte příklad, otáčí se každý obrázek. jpg ve *vzorových obrázcích* a uloží se do *upraveného*.</span><span class="sxs-lookup"><span data-stu-id="78cec-110">When you run the example, it rotates each .jpg image in *Sample Pictures* and saves it to *Modified*.</span></span> <span data-ttu-id="78cec-111">V případě potřeby můžete tyto dvě cesty upravit.</span><span class="sxs-lookup"><span data-stu-id="78cec-111">You can modify the two paths as necessary.</span></span>

[!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
[!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]

<span data-ttu-id="78cec-112"><xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType>Smyčka funguje jako <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> smyčka.</span><span class="sxs-lookup"><span data-stu-id="78cec-112">A <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop works like a <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> loop.</span></span> <span data-ttu-id="78cec-113">Smyčka rozdělí zdrojovou kolekci a naplánuje práci na více vláknech na základě prostředí systému.</span><span class="sxs-lookup"><span data-stu-id="78cec-113">The loop partitions the source collection and schedules the work on multiple threads based on the system environment.</span></span> <span data-ttu-id="78cec-114">Čím více procesorů v systému, tím rychleji se spustí paralelní metoda.</span><span class="sxs-lookup"><span data-stu-id="78cec-114">The more processors on the system, the faster the parallel method runs.</span></span> <span data-ttu-id="78cec-115">U některých zdrojových kolekcí může být sekvenční smyčka rychlejší v závislosti na velikosti zdroje a druhu práce, kterou smyčka provádí.</span><span class="sxs-lookup"><span data-stu-id="78cec-115">For some source collections, a sequential loop may be faster, depending on the size of the source and the kind of work the loop performs.</span></span> <span data-ttu-id="78cec-116">Další informace o výkonu najdete v tématu [potenciální nástrah v datech a paralelismuch Tasks](potential-pitfalls-in-data-and-task-parallelism.md).</span><span class="sxs-lookup"><span data-stu-id="78cec-116">For more information about performance, see [Potential pitfalls in data and task parallelism](potential-pitfalls-in-data-and-task-parallelism.md).</span></span>

<span data-ttu-id="78cec-117">Další informace o paralelních smyčkách naleznete v tématu [How to: Write a Simple Parallel. for Loop](how-to-write-a-simple-parallel-for-loop.md).</span><span class="sxs-lookup"><span data-stu-id="78cec-117">For more information about parallel loops, see [How to: Write a simple Parallel.For loop](how-to-write-a-simple-parallel-for-loop.md).</span></span>

<span data-ttu-id="78cec-118">Pro použití <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> s neobecnou kolekcí můžete použít <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> metodu rozšíření pro převod kolekce na obecnou kolekci, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="78cec-118">To use <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> with a non-generic collection, you can use the <xref:System.Linq.Enumerable.Cast%2A?displayProperty=nameWithType> extension method to convert the collection to a generic collection, as shown in the following example:</span></span>

[!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
[!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]

<span data-ttu-id="78cec-119">K paralelizovat zpracování zdrojů dat můžete také použít Paralelní LINQ (PLINQ) <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="78cec-119">You can also use Parallel LINQ (PLINQ) to parallelize processing of <xref:System.Collections.Generic.IEnumerable%601> data sources.</span></span> <span data-ttu-id="78cec-120">PLINQ umožňuje použít syntax deklarativního dotazu k vyjádření chování smyčky.</span><span class="sxs-lookup"><span data-stu-id="78cec-120">PLINQ enables you to use declarative query syntax to express the loop behavior.</span></span> <span data-ttu-id="78cec-121">Další informace naleznete v tématu [PARALLEL LINQ (PLINQ)](introduction-to-plinq.md).</span><span class="sxs-lookup"><span data-stu-id="78cec-121">For more information, see [Parallel LINQ (PLINQ)](introduction-to-plinq.md).</span></span>

## <a name="compile-and-run-the-code"></a><span data-ttu-id="78cec-122">Zkompilovat a spustit kód</span><span class="sxs-lookup"><span data-stu-id="78cec-122">Compile and run the code</span></span>

<span data-ttu-id="78cec-123">Kód můžete zkompilovat jako konzolovou aplikaci pro .NET Framework nebo jako konzolovou aplikaci pro .NET Core.</span><span class="sxs-lookup"><span data-stu-id="78cec-123">You can compile the code as a console application for .NET Framework or as a console application for .NET Core.</span></span>

<span data-ttu-id="78cec-124">V aplikaci Visual Studio jsou k dispozici šablony konzolové aplikace Visual Basic a C# pro Windows Desktop a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="78cec-124">In Visual Studio, there are Visual Basic and C# console application templates for Windows Desktop and .NET Core.</span></span>

<span data-ttu-id="78cec-125">Z příkazového řádku můžete použít buď příkazy .NET Core CLI (například `dotnet new console` nebo `dotnet new console -lang vb` ), nebo můžete vytvořit soubor a použít kompilátor příkazového řádku pro .NET Framework aplikace.</span><span class="sxs-lookup"><span data-stu-id="78cec-125">From the command line, you can use either the .NET Core CLI commands (for example, `dotnet new console` or `dotnet new console -lang vb`), or you can create the file and use the command-line compiler for a .NET Framework application.</span></span>

<span data-ttu-id="78cec-126">V případě projektu .NET Core musíte odkazovat na balíček NuGet **System. Drawing. Common** .</span><span class="sxs-lookup"><span data-stu-id="78cec-126">For a .NET Core project, you must reference the **System.Drawing.Common** NuGet package.</span></span> <span data-ttu-id="78cec-127">V aplikaci Visual Studio použijte Správce balíčků NuGet k instalaci balíčku.</span><span class="sxs-lookup"><span data-stu-id="78cec-127">In Visual Studio, use the NuGet Package Manager to install the package.</span></span> <span data-ttu-id="78cec-128">Alternativně můžete do \* souboru. csproj nebo. vbproj přidat odkaz na balíček \* :</span><span class="sxs-lookup"><span data-stu-id="78cec-128">Alternatively, you can add a reference to the package in your \*.csproj or \*.vbproj file:</span></span>

```xml
<ItemGroup>
     <PackageReference Include="System.Drawing.Common" Version="4.5.1" />
</ItemGroup>
```

<span data-ttu-id="78cec-129">Chcete-li spustit konzolovou aplikaci .NET Core z příkazového řádku, použijte `dotnet run` ze složky, která obsahuje vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="78cec-129">To run a .NET Core console application from the command line, use `dotnet run` from the folder that contains your application.</span></span>

<span data-ttu-id="78cec-130">Chcete-li spustit konzolovou aplikaci ze sady Visual Studio, stiskněte klávesu **F5**.</span><span class="sxs-lookup"><span data-stu-id="78cec-130">To run your console application from Visual Studio, press **F5**.</span></span>

## <a name="see-also"></a><span data-ttu-id="78cec-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="78cec-131">See also</span></span>

- [<span data-ttu-id="78cec-132">Datový paralelismus</span><span class="sxs-lookup"><span data-stu-id="78cec-132">Data parallelism</span></span>](data-parallelism-task-parallel-library.md)
- [<span data-ttu-id="78cec-133">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="78cec-133">Parallel programming</span></span>](index.md)
- [<span data-ttu-id="78cec-134">Paralelní LINQ (PLINQ)</span><span class="sxs-lookup"><span data-stu-id="78cec-134">Parallel LINQ (PLINQ)</span></span>](introduction-to-plinq.md)
