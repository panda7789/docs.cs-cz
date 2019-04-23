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
ms.openlocfilehash: 5928478518b0bc1eb498381567d52d5ddba4d8b7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326057"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="bd879-102">Transformace dat pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="bd879-102">Data Transformations with LINQ (C#)</span></span>
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] <span data-ttu-id="bd879-103">není jenom o načítání dat</span><span class="sxs-lookup"><span data-stu-id="bd879-103">is not only about retrieving data.</span></span> <span data-ttu-id="bd879-104">Je také výkonné nástroje pro transformaci dat.</span><span class="sxs-lookup"><span data-stu-id="bd879-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="bd879-105">Pomocí [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu, můžete použít zdrojové sekvence, stejně jako vstup a upravit v mnoha způsoby, jak vytvořit nové pořadí výstupu.</span><span class="sxs-lookup"><span data-stu-id="bd879-105">By using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="bd879-106">Můžete změnit pořadí samotné beze změny samotné prvky řazení a seskupení.</span><span class="sxs-lookup"><span data-stu-id="bd879-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="bd879-107">Ale možná procesorově nejvýkonnější funkce [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazů je schopnost vytvářet nové typy.</span><span class="sxs-lookup"><span data-stu-id="bd879-107">But perhaps the most powerful feature of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries is the ability to create new types.</span></span> <span data-ttu-id="bd879-108">To lze provést v [vyberte](../../../../csharp/language-reference/keywords/select-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="bd879-108">This is accomplished in the [select](../../../../csharp/language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="bd879-109">Například můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="bd879-109">For example, you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="bd879-110">Na jednu výstupní sekvenci, která má nový typ sloučení více vstupních sekvencí.</span><span class="sxs-lookup"><span data-stu-id="bd879-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
-   <span data-ttu-id="bd879-111">Vytvoření výstupní sekvence, jehož prvky jsou tvořeny pouze jednu nebo několik vlastností jednotlivých prvků ve zdrojové sekvenci.</span><span class="sxs-lookup"><span data-stu-id="bd879-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
-   <span data-ttu-id="bd879-112">Výstup pořadí, jehož prvky jsou tvořeny výsledky operace provedené na zdroj dat vytvořte.</span><span class="sxs-lookup"><span data-stu-id="bd879-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
-   <span data-ttu-id="bd879-113">Vytváření pořadí výstup do jiného formátu.</span><span class="sxs-lookup"><span data-stu-id="bd879-113">Create output sequences in a different format.</span></span> <span data-ttu-id="bd879-114">Například můžete transformovat data z SQL řádků nebo textové soubory do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="bd879-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="bd879-115">Toto jsou jen několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="bd879-115">These are just several examples.</span></span> <span data-ttu-id="bd879-116">Samozřejmě tyto transformace zkombinovat ve stejném dotazu různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="bd879-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="bd879-117">Kromě toho výstup posloupnost jeden dotaz slouží jako vstupní sekvence pro nový dotaz.</span><span class="sxs-lookup"><span data-stu-id="bd879-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="bd879-118">Spojování více vstupů do jedné výstupní sekvence</span><span class="sxs-lookup"><span data-stu-id="bd879-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="bd879-119">Můžete použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz, který vytvořit výstupní sekvenci, která obsahuje elementy z více než jeden vstupní sekvence.</span><span class="sxs-lookup"><span data-stu-id="bd879-119">You can use a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="bd879-120">Následující příklad ukazuje, jak kombinovat dvě struktury dat v paměti, ale stejné zásady můžete použít u kombinovat data ze zdroje XML nebo SQL nebo datové sady.</span><span class="sxs-lookup"><span data-stu-id="bd879-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="bd879-121">Předpokládejme následující typy dvou tříd:</span><span class="sxs-lookup"><span data-stu-id="bd879-121">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#7)]  
  
 <span data-ttu-id="bd879-122">Následující příklad ukazuje dotaz:</span><span class="sxs-lookup"><span data-stu-id="bd879-122">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#8)]  
  
 <span data-ttu-id="bd879-123">Další informace najdete v tématu [klauzule join](../../../../csharp/language-reference/keywords/join-clause.md) a [klauzule select](../../../../csharp/language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="bd879-123">For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md) and [select clause](../../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="bd879-124">Výběr podmnožiny jednotlivých zdrojových elementů</span><span class="sxs-lookup"><span data-stu-id="bd879-124">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="bd879-125">Existují dva základní způsoby, které vyberou podmnožinu každý prvek ve zdrojové sekvenci:</span><span class="sxs-lookup"><span data-stu-id="bd879-125">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1. <span data-ttu-id="bd879-126">Vybrat jen jeden člen zdrojového prvku, pomocí operace tečkou.</span><span class="sxs-lookup"><span data-stu-id="bd879-126">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="bd879-127">V následujícím příkladu se předpokládá, že `Customer` objekt obsahuje několik veřejných vlastností, včetně řetězec s názvem `City`.</span><span class="sxs-lookup"><span data-stu-id="bd879-127">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="bd879-128">Při spuštění, tento dotaz vytvoří výstup posloupnost řetězců.</span><span class="sxs-lookup"><span data-stu-id="bd879-128">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```csharp
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2. <span data-ttu-id="bd879-129">Pokud chcete vytvořit prvky, které obsahují více než jednu vlastnost ze zdrojového elementu, můžete inicializátoru objektu pojmenovaný objekt nebo anonymního typu.</span><span class="sxs-lookup"><span data-stu-id="bd879-129">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="bd879-130">Následující příklad ukazuje použití anonymní typ k zapouzdření dvě vlastnosti z každého `Customer` element:</span><span class="sxs-lookup"><span data-stu-id="bd879-130">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```csharp
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="bd879-131">Další informace najdete v tématu [inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) a [anonymní typy](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="bd879-131">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="bd879-132">Transformace objektů v paměti do jazyka XML</span><span class="sxs-lookup"><span data-stu-id="bd879-132">Transforming in-Memory Objects into XML</span></span>  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="bd879-133">dotazy umožňují snadno transformovat data mezi struktury dat v paměti, databází SQL, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] datové sady a XML datových proudů nebo dokumenty.</span><span class="sxs-lookup"><span data-stu-id="bd879-133">queries make it easy to transform data between in-memory data structures, SQL databases, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] Datasets and XML streams or documents.</span></span> <span data-ttu-id="bd879-134">V následujícím příkladu transformace objektů v struktury dat v paměti do elementů XML.</span><span class="sxs-lookup"><span data-stu-id="bd879-134">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#9)]  
  
 <span data-ttu-id="bd879-135">Kód vytvoří následující výstup XML:</span><span class="sxs-lookup"><span data-stu-id="bd879-135">The code produces the following XML output:</span></span>  
  
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
  
 <span data-ttu-id="bd879-136">Další informace najdete v tématu [vytváření stromů XML v jazyce C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="bd879-136">For more information, see [Creating XML Trees in C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="bd879-137">Provádění operací se zdrojovými elementy</span><span class="sxs-lookup"><span data-stu-id="bd879-137">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="bd879-138">Výstupní sekvenci nemusí obsahovat všechny prvky nebo element vlastnosti ze zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="bd879-138">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="bd879-139">Výstup může být místo toho sekvenci hodnot, které je vypočítán s použitím zdrojové prvky jako vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="bd879-139">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span> <span data-ttu-id="bd879-140">Následující jednoduchý dotaz, pokud je spuštěn, výstupy sekvencí řetězců, jehož hodnoty představují podle zdrojové sekvence prvků typu výpočtu `double`.</span><span class="sxs-lookup"><span data-stu-id="bd879-140">The following simple query, when it is executed, outputs a sequence of strings whose values represent a calculation based on the source sequence of elements of type `double`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd879-141">Volání metody ve výrazech dotazů není podporováno, pokud dotaz bude fungovat některé jiné domény.</span><span class="sxs-lookup"><span data-stu-id="bd879-141">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="bd879-142">Například nelze volat běžné metody jazyka C# [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] vzhledem k tomu, že systém SQL Server nemá žádný kontext pro něj.</span><span class="sxs-lookup"><span data-stu-id="bd879-142">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="bd879-143">Můžete ale mapování uložené procedury k metodám a volat.</span><span class="sxs-lookup"><span data-stu-id="bd879-143">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="bd879-144">Další informace najdete v tématu [uložené procedury](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="bd879-144">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#10)]  
  
## <a name="see-also"></a><span data-ttu-id="bd879-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd879-145">See also</span></span>

- [<span data-ttu-id="bd879-146">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="bd879-146">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="bd879-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="bd879-147">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)
- [<span data-ttu-id="bd879-148">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="bd879-148">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)
- [<span data-ttu-id="bd879-149">Technologie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="bd879-149">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)
- [<span data-ttu-id="bd879-150">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="bd879-150">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="bd879-151">select – klauzule</span><span class="sxs-lookup"><span data-stu-id="bd879-151">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)
