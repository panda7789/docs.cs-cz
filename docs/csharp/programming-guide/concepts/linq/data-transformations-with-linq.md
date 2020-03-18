---
title: Transformace dat pomocí LINQ (C#)
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
ms.openlocfilehash: 393e3bd24c4bc8b89064e01e1048b24254f5f83b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635948"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="7a128-102">Transformace dat pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="7a128-102">Data Transformations with LINQ (C#)</span></span>
<span data-ttu-id="7a128-103">Jazykově integrovaný dotaz (LINQ) není jen o načítání dat.</span><span class="sxs-lookup"><span data-stu-id="7a128-103">Language-Integrated Query (LINQ) is not only about retrieving data.</span></span> <span data-ttu-id="7a128-104">Je to také mocný nástroj pro transformaci dat.</span><span class="sxs-lookup"><span data-stu-id="7a128-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="7a128-105">Pomocí dotazu LINQ můžete použít zdrojovou sekvenci jako vstup a upravit ji mnoha způsoby k vytvoření nové výstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="7a128-105">By using a LINQ query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="7a128-106">Samotnou sekvenci můžete upravit bez úprav samotných prvků řazením a seskupováním.</span><span class="sxs-lookup"><span data-stu-id="7a128-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="7a128-107">Ale možná nejsilnější funkce linq dotazů je schopnost vytvářet nové typy.</span><span class="sxs-lookup"><span data-stu-id="7a128-107">But perhaps the most powerful feature of LINQ queries is the ability to create new types.</span></span> <span data-ttu-id="7a128-108">To je dosaženo v [select](../../../language-reference/keywords/select-clause.md) klauzule.</span><span class="sxs-lookup"><span data-stu-id="7a128-108">This is accomplished in the [select](../../../language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="7a128-109">Můžete například provádět následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="7a128-109">For example, you can perform the following tasks:</span></span>  
  
- <span data-ttu-id="7a128-110">Sloučit více vstupních sekvencí do jedné výstupní sekvence, která má nový typ.</span><span class="sxs-lookup"><span data-stu-id="7a128-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
- <span data-ttu-id="7a128-111">Vytvořte výstupní sekvence, jejichž prvky se skládají pouze z jedné nebo několika vlastností každého prvku ve zdrojové sekvenci.</span><span class="sxs-lookup"><span data-stu-id="7a128-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
- <span data-ttu-id="7a128-112">Vytvořte výstupní sekvence, jejichž prvky se skládají z výsledků operací prováděných na zdrojových datech.</span><span class="sxs-lookup"><span data-stu-id="7a128-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
- <span data-ttu-id="7a128-113">Vytvořte výstupní sekvence v jiném formátu.</span><span class="sxs-lookup"><span data-stu-id="7a128-113">Create output sequences in a different format.</span></span> <span data-ttu-id="7a128-114">Můžete například transformovat data z řádků SQL nebo textových souborů do xml.</span><span class="sxs-lookup"><span data-stu-id="7a128-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="7a128-115">To je jen několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="7a128-115">These are just several examples.</span></span> <span data-ttu-id="7a128-116">Samozřejmě tyto transformace lze kombinovat různými způsoby ve stejném dotazu.</span><span class="sxs-lookup"><span data-stu-id="7a128-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="7a128-117">Kromě toho výstupní sekvence jednoho dotazu lze použít jako vstupní sekvence pro nový dotaz.</span><span class="sxs-lookup"><span data-stu-id="7a128-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="7a128-118">Spojování více vstupů do jedné výstupní sekvence</span><span class="sxs-lookup"><span data-stu-id="7a128-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="7a128-119">Dotaz LINQ můžete použít k vytvoření výstupní sekvence, která obsahuje prvky z více než jedné vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="7a128-119">You can use a LINQ query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="7a128-120">Následující příklad ukazuje, jak kombinovat dvě datové struktury v paměti, ale stejné principy lze použít ke kombinování dat ze zdrojů XML nebo SQL nebo DataSet.</span><span class="sxs-lookup"><span data-stu-id="7a128-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="7a128-121">Předpokládejme následující dva typy tříd:</span><span class="sxs-lookup"><span data-stu-id="7a128-121">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="7a128-122">Následující příklad ukazuje dotaz:</span><span class="sxs-lookup"><span data-stu-id="7a128-122">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="7a128-123">Další informace naleznete v [tématu join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="7a128-123">For more information, see [join clause](../../../language-reference/keywords/join-clause.md) and [select clause](../../../language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="7a128-124">Výběr podmnožiny jednotlivých zdrojových elementů</span><span class="sxs-lookup"><span data-stu-id="7a128-124">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="7a128-125">Existují dva primární způsoby, jak vybrat podmnožinu každého prvku ve zdrojové sekvenci:</span><span class="sxs-lookup"><span data-stu-id="7a128-125">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="7a128-126">Chcete-li vybrat pouze jeden člen zdrojového prvku, použijte tečkovou operaci.</span><span class="sxs-lookup"><span data-stu-id="7a128-126">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="7a128-127">V následujícím příkladu předpokládejme, že `Customer` objekt obsahuje `City`několik veřejných vlastností včetně řetězce s názvem .</span><span class="sxs-lookup"><span data-stu-id="7a128-127">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="7a128-128">Při spuštění tohoto dotazu vytvoří výstupní posloupnost řetězců.</span><span class="sxs-lookup"><span data-stu-id="7a128-128">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="7a128-129">Chcete-li vytvořit prvky, které obsahují více než jednu vlastnost ze zdrojového prvku, můžete použít inicializátor objektu s pojmenovaným objektem nebo anonymním typem.</span><span class="sxs-lookup"><span data-stu-id="7a128-129">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="7a128-130">Následující příklad ukazuje použití anonymního typu k zapouzdření dvou vlastností z každého `Customer` prvku:</span><span class="sxs-lookup"><span data-stu-id="7a128-130">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="7a128-131">Další informace naleznete v [tématu Objekt a kolekce Inicializátory](../../classes-and-structs/object-and-collection-initializers.md) a [anonymní typy](../../classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="7a128-131">For more information, see [Object and Collection Initializers](../../classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="7a128-132">Transformace objektů v paměti do jazyka XML</span><span class="sxs-lookup"><span data-stu-id="7a128-132">Transforming in-Memory Objects into XML</span></span>  
 <span data-ttu-id="7a128-133">Dotazy LINQ usnadňují transformaci dat mezi datovými strukturami v paměti, databázemi SQL, ADO.NET datovými sadami a datovými proudy XML nebo dokumenty.</span><span class="sxs-lookup"><span data-stu-id="7a128-133">LINQ queries make it easy to transform data between in-memory data structures, SQL databases, ADO.NET Datasets and XML streams or documents.</span></span> <span data-ttu-id="7a128-134">Následující příklad transformuje objekty v datové struktuře v paměti na elementy XML.</span><span class="sxs-lookup"><span data-stu-id="7a128-134">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="7a128-135">Kód vytváří následující výstup XML:</span><span class="sxs-lookup"><span data-stu-id="7a128-135">The code produces the following XML output:</span></span>  
  
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
  
 <span data-ttu-id="7a128-136">Další informace naleznete [v tématu Creating XML Trees in C# (LINQ to XML).](./creating-xml-trees-linq-to-xml-2.md)</span><span class="sxs-lookup"><span data-stu-id="7a128-136">For more information, see [Creating XML Trees in C# (LINQ to XML)](./creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="7a128-137">Provádění operací se zdrojovými elementy</span><span class="sxs-lookup"><span data-stu-id="7a128-137">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="7a128-138">Výstupní sekvence nemusí obsahovat žádné prvky nebo vlastnosti elementu ze zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="7a128-138">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="7a128-139">Výstup může být místo toho posloupnost hodnot, která je vypočítána pomocí zdrojových prvků jako vstupních argumentů.</span><span class="sxs-lookup"><span data-stu-id="7a128-139">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span> <span data-ttu-id="7a128-140">Následující jednoduchý dotaz, když je spuštěn, výstupy posloupnost řetězců, jejichž hodnoty představují výpočet `double`na základě zdrojové sekvence prvků typu .</span><span class="sxs-lookup"><span data-stu-id="7a128-140">The following simple query, when it is executed, outputs a sequence of strings whose values represent a calculation based on the source sequence of elements of type `double`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7a128-141">Volání metod ve výrazech dotazu není podporováno, pokud bude dotaz přeložen do jiné domény.</span><span class="sxs-lookup"><span data-stu-id="7a128-141">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="7a128-142">Například nelze volat běžné c# [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] metoda v protože SQL Server nemá žádný kontext pro něj.</span><span class="sxs-lookup"><span data-stu-id="7a128-142">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="7a128-143">Uložené procedury však můžete mapovat na metody a volat je.</span><span class="sxs-lookup"><span data-stu-id="7a128-143">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="7a128-144">Další informace naleznete [v tématu Uložené procedury](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7a128-144">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="7a128-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a128-145">See also</span></span>

- [<span data-ttu-id="7a128-146">Dotaz integrovaný jazykem (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7a128-146">Language-Integrated Query (LINQ) (C#)</span></span>](./index.md)
- [<span data-ttu-id="7a128-147">Technologie LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7a128-147">LINQ to SQL</span></span>](../../../../framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="7a128-148">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="7a128-148">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="7a128-149">LINQ do XML (C#)</span><span class="sxs-lookup"><span data-stu-id="7a128-149">LINQ to XML (C#)</span></span>](./linq-to-xml-overview.md)
- [<span data-ttu-id="7a128-150">Výrazy dotazu LINQ</span><span class="sxs-lookup"><span data-stu-id="7a128-150">LINQ Query Expressions</span></span>](../../../linq/index.md)
- [<span data-ttu-id="7a128-151">select – klauzule</span><span class="sxs-lookup"><span data-stu-id="7a128-151">select clause</span></span>](../../../language-reference/keywords/select-clause.md)
