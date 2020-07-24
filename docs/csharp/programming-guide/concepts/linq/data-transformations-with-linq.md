---
title: Transformace dat pomocí LINQ (C#)
description: Naučte se používat dotazy LINQ v jazyce C# k transformaci dat. Můžete upravit sekvenci pomocí řazení a seskupování a vytvořit nové typy pomocí klauzule SELECT.
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], data transformations
- source elements [LINQ in C#]
- joining multiple inputs [LINQ in C#]
- multiple outputs for one output sequence [LINQ in C#]
- subset of source elements [LINQ in C#]
- data sources [LINQ in C#], data transformations
- data transformations [LINQ in C#]
ms.assetid: 674eae9e-bc72-4a88-aed3-802b45b25811
ms.openlocfilehash: 6844cf2aa589f7516a9e40bc604c5f907ec6d311
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2020
ms.locfileid: "87104013"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="e4757-104">Transformace dat pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="e4757-104">Data Transformations with LINQ (C#)</span></span>
<span data-ttu-id="e4757-105">Dotaz integrovaný na jazyku (LINQ) není pouze o načítání dat.</span><span class="sxs-lookup"><span data-stu-id="e4757-105">Language-Integrated Query (LINQ) is not only about retrieving data.</span></span> <span data-ttu-id="e4757-106">Je to také výkonný nástroj pro transformaci dat.</span><span class="sxs-lookup"><span data-stu-id="e4757-106">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="e4757-107">Pomocí dotazu LINQ můžete jako vstup použít zdrojovou sekvenci a upravit ji mnoha způsoby, abyste mohli vytvořit novou výstupní sekvenci.</span><span class="sxs-lookup"><span data-stu-id="e4757-107">By using a LINQ query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="e4757-108">Samotnou sekvenci můžete změnit, aniž byste museli měnit prvky řazením a seskupením.</span><span class="sxs-lookup"><span data-stu-id="e4757-108">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="e4757-109">Ale pravděpodobně nejúčinnější funkce dotazů LINQ je schopnost vytvářet nové typy.</span><span class="sxs-lookup"><span data-stu-id="e4757-109">But perhaps the most powerful feature of LINQ queries is the ability to create new types.</span></span> <span data-ttu-id="e4757-110">To je dosaženo v klauzuli [Select](../../../language-reference/keywords/select-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="e4757-110">This is accomplished in the [select](../../../language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="e4757-111">Můžete například provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="e4757-111">For example, you can perform the following tasks:</span></span>  
  
- <span data-ttu-id="e4757-112">Sloučí více vstupních sekvencí do jedné výstupní sekvence, která má nový typ.</span><span class="sxs-lookup"><span data-stu-id="e4757-112">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
- <span data-ttu-id="e4757-113">Vytvořte výstupní sekvence, jejichž prvky se skládají pouze z jedné nebo několika vlastností každého prvku ve zdrojové sekvenci.</span><span class="sxs-lookup"><span data-stu-id="e4757-113">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
- <span data-ttu-id="e4757-114">Vytvořte výstupní sekvence, jejichž prvky se skládají z výsledků operací provedených ve zdrojových datech.</span><span class="sxs-lookup"><span data-stu-id="e4757-114">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
- <span data-ttu-id="e4757-115">Vytvořte výstupní sekvence v jiném formátu.</span><span class="sxs-lookup"><span data-stu-id="e4757-115">Create output sequences in a different format.</span></span> <span data-ttu-id="e4757-116">Můžete například transformovat data z řádků nebo textových souborů SQL do XML.</span><span class="sxs-lookup"><span data-stu-id="e4757-116">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="e4757-117">Jsou to jenom několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="e4757-117">These are just several examples.</span></span> <span data-ttu-id="e4757-118">Tyto transformace je samozřejmě možné v jednom dotazu zkombinovat různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="e4757-118">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="e4757-119">Kromě toho se výstupní sekvence jednoho dotazu dá použít jako vstupní sekvence nového dotazu.</span><span class="sxs-lookup"><span data-stu-id="e4757-119">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="e4757-120">Spojování více vstupů do jedné výstupní sekvence</span><span class="sxs-lookup"><span data-stu-id="e4757-120">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="e4757-121">Dotaz LINQ můžete použít k vytvoření výstupní sekvence, která obsahuje prvky z více než jedné vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="e4757-121">You can use a LINQ query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="e4757-122">Následující příklad ukazuje, jak kombinovat dvě datové struktury v paměti, ale stejné zásady lze použít pro kombinování dat z XML nebo SQL nebo datových zdrojů.</span><span class="sxs-lookup"><span data-stu-id="e4757-122">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="e4757-123">Předpokládejme následující dva typy tříd:</span><span class="sxs-lookup"><span data-stu-id="e4757-123">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="e4757-124">Následující příklad ukazuje dotaz:</span><span class="sxs-lookup"><span data-stu-id="e4757-124">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="e4757-125">Další informace najdete v tématu [klauzule JOIN](../../../language-reference/keywords/join-clause.md) a [klauzule SELECT](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="e4757-125">For more information, see [join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="e4757-126">Výběr podmnožiny jednotlivých zdrojových elementů</span><span class="sxs-lookup"><span data-stu-id="e4757-126">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="e4757-127">Existují dva hlavní způsoby, jak vybrat podmnožinu každého prvku ve zdrojové sekvenci:</span><span class="sxs-lookup"><span data-stu-id="e4757-127">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="e4757-128">Chcete-li vybrat pouze jednoho člena zdrojového prvku, použijte operaci tečka.</span><span class="sxs-lookup"><span data-stu-id="e4757-128">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="e4757-129">V následujícím příkladu Předpokládejme, že `Customer` objekt obsahuje několik veřejných vlastností včetně řetězce s názvem `City` .</span><span class="sxs-lookup"><span data-stu-id="e4757-129">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="e4757-130">Při spuštění tento dotaz vytvoří výstupní sekvenci řetězců.</span><span class="sxs-lookup"><span data-stu-id="e4757-130">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="e4757-131">Chcete-li vytvořit prvky, které obsahují více než jednu vlastnost ze zdrojového elementu, můžete použít inicializátor objektu s pojmenovaným objektem nebo anonymním typem.</span><span class="sxs-lookup"><span data-stu-id="e4757-131">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="e4757-132">Následující příklad ukazuje použití anonymního typu k zapouzdření dvou vlastností z každého `Customer` prvku:</span><span class="sxs-lookup"><span data-stu-id="e4757-132">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="e4757-133">Další informace naleznete v tématu [Inicializátory objektů a kolekcí](../../classes-and-structs/object-and-collection-initializers.md) a [anonymní typy](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="e4757-133">For more information, see [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="e4757-134">Transformace objektů v paměti do jazyka XML</span><span class="sxs-lookup"><span data-stu-id="e4757-134">Transforming in-Memory Objects into XML</span></span>  
 <span data-ttu-id="e4757-135">Dotazy LINQ usnadňují transformaci dat mezi datovými strukturami v paměti, databázemi SQL, ADO.NET datasadami a datovými proudy XML nebo dokumenty.</span><span class="sxs-lookup"><span data-stu-id="e4757-135">LINQ queries make it easy to transform data between in-memory data structures, SQL databases, ADO.NET Datasets and XML streams or documents.</span></span> <span data-ttu-id="e4757-136">Následující příklad transformuje objekty v datové struktuře v paměti do elementů XML.</span><span class="sxs-lookup"><span data-stu-id="e4757-136">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="e4757-137">Kód generuje následující výstup XML:</span><span class="sxs-lookup"><span data-stu-id="e4757-137">The code produces the following XML output:</span></span>  
  
```xml  
<Root>  
  <student>  
    <First>Svetlana</First>  
    <Last>Omelchenko</Last>  
    <Scores>97,92,81,60</Scores>  
  </student>  
  <student>  
    <First>Claire</First>  
    <Last>O'Donnell</Last>  
    <Scores>75,84,91,39</Scores>  
  </student>  
  <student>  
    <First>Sven</First>  
    <Last>Mortensen</Last>  
    <Scores>88,94,65,91</Scores>  
  </student>  
</Root>  
```  
  
 <span data-ttu-id="e4757-138">Další informace naleznete v tématu [vytváření stromů XML v jazyce C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="e4757-138">For more information, see [Creating XML Trees in C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="e4757-139">Provádění operací se zdrojovými elementy</span><span class="sxs-lookup"><span data-stu-id="e4757-139">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="e4757-140">Výstupní sekvence nemusí obsahovat žádné elementy nebo vlastnosti elementu ze zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="e4757-140">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="e4757-141">Výstupem může být například sekvence hodnot, které jsou vypočítány pomocí zdrojového prvku jako vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="e4757-141">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span>

 <span data-ttu-id="e4757-142">Následující dotaz provede sekvenci čísel reprezentujících poloměry kroužků, vypočítá oblast pro každý poloměr a vrátí výstupní sekvenci obsahující řetězce naformátované pomocí počítané oblasti.</span><span class="sxs-lookup"><span data-stu-id="e4757-142">The following query will take a sequence of numbers that represent radii of circles, calculate the area for each radius, and return an output sequence containing strings formatted with the calculated area.</span></span>

 <span data-ttu-id="e4757-143">Každý řetězec výstupní sekvence bude formátován pomocí [interpolace řetězce](../../../language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="e4757-143">Each string for the output sequence will be formatted using [string interpolation](../../../language-reference/tokens/interpolated.md).</span></span> <span data-ttu-id="e4757-144">Interpolovaná řetězcová událost bude mít `$` před otevírací uvozovkou řetězce a operace může být provedena v rámci složených závorek umístěných uvnitř interpolované řetězcové řetězce.</span><span class="sxs-lookup"><span data-stu-id="e4757-144">An interpolated string will have a `$` in front of the string's opening quotation mark, and operations can be performed within curly braces placed inside the interpolated string.</span></span> <span data-ttu-id="e4757-145">Po provedení těchto operací budou výsledky zřetězeny.</span><span class="sxs-lookup"><span data-stu-id="e4757-145">Once those operations are performed, the results will be concatenated.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e4757-146">Volání metod ve výrazech dotazů není podporováno, pokud bude dotaz přeložen do jiné domény.</span><span class="sxs-lookup"><span data-stu-id="e4757-146">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="e4757-147">Například nemůžete volat běžnou metodu jazyka C# v, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] protože pro ni SQL Server nemá žádný kontext.</span><span class="sxs-lookup"><span data-stu-id="e4757-147">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="e4757-148">Uložené procedury však lze namapovat na metody a volat je.</span><span class="sxs-lookup"><span data-stu-id="e4757-148">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="e4757-149">Další informace najdete v tématu [uložené procedury](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="e4757-149">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="e4757-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4757-150">See also</span></span>

- [<span data-ttu-id="e4757-151">LINQ (Language-Integrated Query) (C#)</span><span class="sxs-lookup"><span data-stu-id="e4757-151">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="e4757-152">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="e4757-152">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="e4757-153">LINQ na DataSet</span><span class="sxs-lookup"><span data-stu-id="e4757-153">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="e4757-154">LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="e4757-154">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)
- [<span data-ttu-id="e4757-155">Výrazy dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="e4757-155">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="e4757-156">select – klauzule (C#)</span><span class="sxs-lookup"><span data-stu-id="e4757-156">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
