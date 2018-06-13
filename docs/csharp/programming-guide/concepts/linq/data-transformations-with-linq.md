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
ms.openlocfilehash: c165f78c53cec0417d39320580b812ff01fef68b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33333255"
---
# <a name="data-transformations-with-linq-c"></a><span data-ttu-id="421c9-102">Transformace dat pomocí LINQ (C#)</span><span class="sxs-lookup"><span data-stu-id="421c9-102">Data Transformations with LINQ (C#)</span></span>
[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]<span data-ttu-id="421c9-103"> není jenom o načtení dat.</span><span class="sxs-lookup"><span data-stu-id="421c9-103"> is not only about retrieving data.</span></span> <span data-ttu-id="421c9-104">Je také výkonný nástroj pro převod data.</span><span class="sxs-lookup"><span data-stu-id="421c9-104">It is also a powerful tool for transforming data.</span></span> <span data-ttu-id="421c9-105">Pomocí [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazu, můžete použít zdrojové sekvence jako vstup a upravit v mnoho způsobů, jak vytvořit nové pořadí výstup.</span><span class="sxs-lookup"><span data-stu-id="421c9-105">By using a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query, you can use a source sequence as input and modify it in many ways to create a new output sequence.</span></span> <span data-ttu-id="421c9-106">Můžete upravit pořadí samotné beze změny samotné prvky řazení a seskupování.</span><span class="sxs-lookup"><span data-stu-id="421c9-106">You can modify the sequence itself without modifying the elements themselves by sorting and grouping.</span></span> <span data-ttu-id="421c9-107">Ale možná nejúčinnějších funkci [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy je schopnost vytvářet nové typy.</span><span class="sxs-lookup"><span data-stu-id="421c9-107">But perhaps the most powerful feature of [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries is the ability to create new types.</span></span> <span data-ttu-id="421c9-108">To lze provést v [vyberte](../../../../csharp/language-reference/keywords/select-clause.md) klauzule.</span><span class="sxs-lookup"><span data-stu-id="421c9-108">This is accomplished in the [select](../../../../csharp/language-reference/keywords/select-clause.md) clause.</span></span> <span data-ttu-id="421c9-109">Například můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="421c9-109">For example, you can perform the following tasks:</span></span>  
  
-   <span data-ttu-id="421c9-110">Sloučit více vstupních sekvencí do jediného výstupu pořadí, které má nového typu.</span><span class="sxs-lookup"><span data-stu-id="421c9-110">Merge multiple input sequences into a single output sequence that has a new type.</span></span>  
  
-   <span data-ttu-id="421c9-111">Vytvoření výstupní pořadí, jehož elementy obsahovat pouze jednu nebo několik vlastností jednotlivých prvků v zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="421c9-111">Create output sequences whose elements consist of only one or several properties of each element in the source sequence.</span></span>  
  
-   <span data-ttu-id="421c9-112">Výstup pořadí, jehož elementy jsou tvořeny výsledky operace provedené na zdroji dat vytvořte.</span><span class="sxs-lookup"><span data-stu-id="421c9-112">Create output sequences whose elements consist of the results of operations performed on the source data.</span></span>  
  
-   <span data-ttu-id="421c9-113">Vytvořte pořadí výstup do jiného formátu.</span><span class="sxs-lookup"><span data-stu-id="421c9-113">Create output sequences in a different format.</span></span> <span data-ttu-id="421c9-114">Například můžete převést data z textových souborů nebo SQL řádků do souboru XML.</span><span class="sxs-lookup"><span data-stu-id="421c9-114">For example, you can transform data from SQL rows or text files into XML.</span></span>  
  
 <span data-ttu-id="421c9-115">Jsou to jenom několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="421c9-115">These are just several examples.</span></span> <span data-ttu-id="421c9-116">Samozřejmě tyto transformace lze spojovat různými způsoby v jednom dotazu.</span><span class="sxs-lookup"><span data-stu-id="421c9-116">Of course, these transformations can be combined in various ways in the same query.</span></span> <span data-ttu-id="421c9-117">Kromě toho výstup pořadí jeden dotaz slouží jako vstupní pořadí pro nový dotaz.</span><span class="sxs-lookup"><span data-stu-id="421c9-117">Furthermore, the output sequence of one query can be used as the input sequence for a new query.</span></span>  
  
## <a name="joining-multiple-inputs-into-one-output-sequence"></a><span data-ttu-id="421c9-118">Spojování více vstupů do jedné výstupní sekvence</span><span class="sxs-lookup"><span data-stu-id="421c9-118">Joining Multiple Inputs into One Output Sequence</span></span>  
 <span data-ttu-id="421c9-119">Můžete použít [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotaz k vytvoření výstupní sekvenci, která obsahuje elementy z více než jeden vstupní pořadí.</span><span class="sxs-lookup"><span data-stu-id="421c9-119">You can use a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to create an output sequence that contains elements from more than one input sequence.</span></span> <span data-ttu-id="421c9-120">Následující příklad ukazuje, jak kombinovat dvě struktury dat v paměti, ale lze použít stejné zásady kombinovat data ze zdroje XML nebo SQL nebo datovou sadu.</span><span class="sxs-lookup"><span data-stu-id="421c9-120">The following example shows how to combine two in-memory data structures, but the same principles can be applied to combine data from XML or SQL or DataSet sources.</span></span> <span data-ttu-id="421c9-121">Předpokládejme následující typy dvě třídy:</span><span class="sxs-lookup"><span data-stu-id="421c9-121">Assume the following two class types:</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#7](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_1.cs)]  
  
 <span data-ttu-id="421c9-122">Následující příklad ukazuje dotaz:</span><span class="sxs-lookup"><span data-stu-id="421c9-122">The following example shows the query:</span></span>  
  
 [!code-csharp[CSLinqGettingStarted#8](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_2.cs)]  
  
 <span data-ttu-id="421c9-123">Další informace najdete v tématu [klauzuli join](../../../../csharp/language-reference/keywords/join-clause.md) a [klauzuli select](../../../../csharp/language-reference/keywords/select-clause.md).</span><span class="sxs-lookup"><span data-stu-id="421c9-123">For more information, see [join clause](../../../../csharp/language-reference/keywords/join-clause.md) and [select clause](../../../../csharp/language-reference/keywords/select-clause.md).</span></span>  
  
## <a name="selecting-a-subset-of-each-source-element"></a><span data-ttu-id="421c9-124">Výběr podmnožiny jednotlivých zdrojových elementů</span><span class="sxs-lookup"><span data-stu-id="421c9-124">Selecting a Subset of each Source Element</span></span>  
 <span data-ttu-id="421c9-125">Existují dva způsoby primární vybrat podmnožinu každý prvek v pořadí zdroje:</span><span class="sxs-lookup"><span data-stu-id="421c9-125">There are two primary ways to select a subset of each element in the source sequence:</span></span>  
  
1.  <span data-ttu-id="421c9-126">Vyberte pouze jednu členem source element, použijte operaci tečkou.</span><span class="sxs-lookup"><span data-stu-id="421c9-126">To select just one member of the source element, use the dot operation.</span></span> <span data-ttu-id="421c9-127">V následujícím příkladu předpokládáme, že `Customer` objekt obsahuje několik veřejné vlastnosti včetně řetězec s názvem `City`.</span><span class="sxs-lookup"><span data-stu-id="421c9-127">In the following example, assume that a `Customer` object contains several public properties including a string named `City`.</span></span> <span data-ttu-id="421c9-128">Po provedení tohoto dotazu vytvoří v výstupní sekvenci řetězců.</span><span class="sxs-lookup"><span data-stu-id="421c9-128">When executed, this query will produce an output sequence of strings.</span></span>  
  
    ```  
    var query = from cust in Customers  
                select cust.City;  
    ```  
  
2.  <span data-ttu-id="421c9-129">K vytváření prvků, které obsahují více než jednu vlastnost z source element, můžete použít buď objekt s názvem, nebo anonymní typ inicializátoru objektu.</span><span class="sxs-lookup"><span data-stu-id="421c9-129">To create elements that contain more than one property from the source element, you can use an object initializer with either a named object or an anonymous type.</span></span> <span data-ttu-id="421c9-130">Následující příklad ukazuje použití anonymní typ k zapouzdření dvě vlastnosti z každé `Customer` element:</span><span class="sxs-lookup"><span data-stu-id="421c9-130">The following example shows the use of an anonymous type to encapsulate two properties from each `Customer` element:</span></span>  
  
    ```  
    var query = from cust in Customer  
                select new {Name = cust.Name, City = cust.City};  
    ```  
  
 <span data-ttu-id="421c9-131">Další informace najdete v tématu [inicializátory objektu a kolekce](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) a [anonymní typy](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span><span class="sxs-lookup"><span data-stu-id="421c9-131">For more information, see [Object and Collection Initializers](../../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md) and [Anonymous Types](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).</span></span>  
  
## <a name="transforming-in-memory-objects-into-xml"></a><span data-ttu-id="421c9-132">Transformace objektů v paměti do jazyka XML</span><span class="sxs-lookup"><span data-stu-id="421c9-132">Transforming in-Memory Objects into XML</span></span>  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]<span data-ttu-id="421c9-133"> dotazy usnadňují transformace dat mezi v paměti datové struktury, databází SQL, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] datových sad a XML datové proudy nebo dokumenty.</span><span class="sxs-lookup"><span data-stu-id="421c9-133"> queries make it easy to transform data between in-memory data structures, SQL databases, [!INCLUDE[vstecado](~/includes/vstecado-md.md)] Datasets and XML streams or documents.</span></span> <span data-ttu-id="421c9-134">Následující příklad transformuje objekty v strukturu dat v paměti do elementů XML.</span><span class="sxs-lookup"><span data-stu-id="421c9-134">The following example transforms objects in an in-memory data structure into XML elements.</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#9](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_3.cs)]  
  
 <span data-ttu-id="421c9-135">Kód vytvoří následující výstup XML:</span><span class="sxs-lookup"><span data-stu-id="421c9-135">The code produces the following XML output:</span></span>  
  
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
  
 <span data-ttu-id="421c9-136">Další informace najdete v tématu [vytváření stromů XML v jazyce C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="421c9-136">For more information, see [Creating XML Trees in C# (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees-linq-to-xml-2.md).</span></span>  
  
## <a name="performing-operations-on-source-elements"></a><span data-ttu-id="421c9-137">Provádění operací se zdrojovými elementy</span><span class="sxs-lookup"><span data-stu-id="421c9-137">Performing Operations on Source Elements</span></span>  
 <span data-ttu-id="421c9-138">Výstupní sekvenci nemusí obsahovat všechny prvky nebo vlastností elementů ze zdrojové sekvence.</span><span class="sxs-lookup"><span data-stu-id="421c9-138">An output sequence might not contain any elements or element properties from the source sequence.</span></span> <span data-ttu-id="421c9-139">Výstup může být místo toho pořadí hodnot, který se počítá pomocí zdrojové elementy jako vstupní argumenty.</span><span class="sxs-lookup"><span data-stu-id="421c9-139">The output might instead be a sequence of values that is computed by using the source elements as input arguments.</span></span> <span data-ttu-id="421c9-140">Tento jednoduchý dotaz, při spuštění, výstupy posloupnosti řetězců, jejichž hodnoty představují výpočtu podle pořadí zdrojové elementy typu `double`.</span><span class="sxs-lookup"><span data-stu-id="421c9-140">The following simple query, when it is executed, outputs a sequence of strings whose values represent a calculation based on the source sequence of elements of type `double`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="421c9-141">Volání metody ve výrazech dotazů není podporováno, pokud dotaz bude převeden na některé jiné domény.</span><span class="sxs-lookup"><span data-stu-id="421c9-141">Calling methods in query expressions is not supported if the query will be translated into some other domain.</span></span> <span data-ttu-id="421c9-142">Například nelze volat obyčejnou metoda C# [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] protože SQL Server nemá žádný kontext pro ni.</span><span class="sxs-lookup"><span data-stu-id="421c9-142">For example, you cannot call an ordinary C# method in [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] because SQL Server has no context for it.</span></span> <span data-ttu-id="421c9-143">Můžete však mapovat uložené procedury metody a ty volání.</span><span class="sxs-lookup"><span data-stu-id="421c9-143">However, you can map stored procedures to methods and call those.</span></span> <span data-ttu-id="421c9-144">Další informace najdete v tématu [uložené procedury](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="421c9-144">For more information, see [Stored Procedures](../../../../framework/data/adonet/sql/linq/stored-procedures.md).</span></span>  
  
 [!code-csharp[CsLINQGettingStarted#10](../../../../csharp/programming-guide/concepts/linq/codesnippet/CSharp/data-transformations-with-linq_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="421c9-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="421c9-145">See Also</span></span>  
 [<span data-ttu-id="421c9-146">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="421c9-146">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 [<span data-ttu-id="421c9-147">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="421c9-147">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 [<span data-ttu-id="421c9-148">LINQ to DataSet</span><span class="sxs-lookup"><span data-stu-id="421c9-148">LINQ to DataSet</span></span>](../../../../framework/data/adonet/linq-to-dataset.md)  
 [<span data-ttu-id="421c9-149">Technologie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="421c9-149">LINQ to XML (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml.md)  
 [<span data-ttu-id="421c9-150">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="421c9-150">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 [<span data-ttu-id="421c9-151">select – klauzule</span><span class="sxs-lookup"><span data-stu-id="421c9-151">select clause</span></span>](../../../../csharp/language-reference/keywords/select-clause.md)
