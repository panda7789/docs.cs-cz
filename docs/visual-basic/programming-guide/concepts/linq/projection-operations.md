---
title: Operace projekce (Visual Basic)
ms.date: 07/20/2015
ms.assetid: b8d38e6d-21cf-4619-8dbb-94476f4badc7
ms.openlocfilehash: e2af45f9cbbed9eb88095a30e2b77a7730740898
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820981"
---
# <a name="projection-operations-visual-basic"></a><span data-ttu-id="b0515-102">Operace projekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0515-102">Projection Operations (Visual Basic)</span></span>
<span data-ttu-id="b0515-103">Projekce odkazuje na operace transformace objektu na nový formulář, který často se skládá pouze z těchto vlastností, které se následně použijí.</span><span class="sxs-lookup"><span data-stu-id="b0515-103">Projection refers to the operation of transforming an object into a new form that often consists only of those properties that will be subsequently used.</span></span> <span data-ttu-id="b0515-104">S použitím projekce, můžete vytvořit nový typ, který je sestaven z každého objektu.</span><span class="sxs-lookup"><span data-stu-id="b0515-104">By using projection, you can construct a new type that is built from each object.</span></span> <span data-ttu-id="b0515-105">Můžete vlastnosti projektu a provádění matematických funkcí na něj.</span><span class="sxs-lookup"><span data-stu-id="b0515-105">You can project a property and perform a mathematical function on it.</span></span> <span data-ttu-id="b0515-106">Můžete také promítnout na původní objekt bez provedení změn.</span><span class="sxs-lookup"><span data-stu-id="b0515-106">You can also project the original object without changing it.</span></span>  
  
 <span data-ttu-id="b0515-107">V následující části jsou uvedeny standardní metody operátoru dotazu, které provádějí projekce.</span><span class="sxs-lookup"><span data-stu-id="b0515-107">The standard query operator methods that perform projection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0515-108">Metody</span><span class="sxs-lookup"><span data-stu-id="b0515-108">Methods</span></span>  
  
|<span data-ttu-id="b0515-109">Název metody</span><span class="sxs-lookup"><span data-stu-id="b0515-109">Method Name</span></span>|<span data-ttu-id="b0515-110">Popis</span><span class="sxs-lookup"><span data-stu-id="b0515-110">Description</span></span>|<span data-ttu-id="b0515-111">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b0515-111">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="b0515-112">Další informace</span><span class="sxs-lookup"><span data-stu-id="b0515-112">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="b0515-113">Vyberte</span><span class="sxs-lookup"><span data-stu-id="b0515-113">Select</span></span>|<span data-ttu-id="b0515-114">Projekty hodnoty, které jsou založeny na funkce transformace.</span><span class="sxs-lookup"><span data-stu-id="b0515-114">Projects values that are based on a transform function.</span></span>|`Select`|<xref:System.Linq.Enumerable.Select%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Select%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="b0515-115">SelectMany</span><span class="sxs-lookup"><span data-stu-id="b0515-115">SelectMany</span></span>|<span data-ttu-id="b0515-116">Projekty pořadí hodnot, které jsou založeny na funkce transformace a sloučí je do jedné sekvence.</span><span class="sxs-lookup"><span data-stu-id="b0515-116">Projects sequences of values that are based on a transform function and then flattens them into one sequence.</span></span>|<span data-ttu-id="b0515-117">Použití více `From` klauzule</span><span class="sxs-lookup"><span data-stu-id="b0515-117">Use multiple `From` clauses</span></span>|<xref:System.Linq.Enumerable.SelectMany%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.SelectMany%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-examples"></a><span data-ttu-id="b0515-118">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="b0515-118">Query Expression Syntax Examples</span></span>  
  
### <a name="select"></a><span data-ttu-id="b0515-119">Vyberte</span><span class="sxs-lookup"><span data-stu-id="b0515-119">Select</span></span>  
 <span data-ttu-id="b0515-120">V následujícím příkladu `Select` klauzuli do projektu první písmeno každého řetězce v seznamu řetězců.</span><span class="sxs-lookup"><span data-stu-id="b0515-120">The following example uses the `Select` clause to project the first letter from each string in a list of strings.</span></span>  
  
```vb  
Dim words = New List(Of String) From {"an", "apple", "a", "day"}  
  
Dim query = From word In words   
            Select word.Substring(0, 1)  
  
Dim sb As New System.Text.StringBuilder()  
For Each letter As String In query  
    sb.AppendLine(letter)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' a  
' a  
' a  
' d  
```  
  
### <a name="selectmany"></a><span data-ttu-id="b0515-121">SelectMany</span><span class="sxs-lookup"><span data-stu-id="b0515-121">SelectMany</span></span>  
 <span data-ttu-id="b0515-122">Následující příklad používá více `From` klauzule do projektu všechna slova ze každý řetězec v seznamu řetězců.</span><span class="sxs-lookup"><span data-stu-id="b0515-122">The following example uses multiple `From` clauses to project each word from each string in a list of strings.</span></span>  
  
```vb  
Dim phrases = New List(Of String) From {"an apple a day", "the quick brown fox"}  
  
Dim query = From phrase In phrases   
            From word In phrase.Split(" "c)   
            Select word  
  
Dim sb As New System.Text.StringBuilder()  
For Each str As String In query  
    sb.AppendLine(str)  
Next  
  
' Display the output.  
MsgBox(sb.ToString())  
  
' This code produces the following output:  
  
' an  
' apple  
' a  
' day  
' the  
' quick  
' brown  
' fox  
```  
  
## <a name="select-versus-selectmany"></a><span data-ttu-id="b0515-123">Vyberte a operátor SelectMany</span><span class="sxs-lookup"><span data-stu-id="b0515-123">Select versus SelectMany</span></span>  
 <span data-ttu-id="b0515-124">Práce z obou `Select()` a `SelectMany()` je výsledná hodnota (nebo hodnoty) ze zdrojové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b0515-124">The work of both `Select()` and `SelectMany()` is to produce a result value (or values) from source values.</span></span> <span data-ttu-id="b0515-125">`Select()` vytvoří jednu výslednou hodnotu pro každou zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b0515-125">`Select()` produces one result value for every source value.</span></span> <span data-ttu-id="b0515-126">Celkový výsledek je proto kolekci, která má stejný počet prvků jako zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="b0515-126">The overall result is therefore a collection that has the same number of elements as the source collection.</span></span> <span data-ttu-id="b0515-127">Naproti tomu `SelectMany()` jeden celkový výsledek, který obsahuje zřetězených podřízené kolekce od všech hodnot zdroje.</span><span class="sxs-lookup"><span data-stu-id="b0515-127">In contrast, `SelectMany()` produces a single overall result that contains concatenated sub-collections from each source value.</span></span> <span data-ttu-id="b0515-128">Funkce transformace, která je předána jako argument `SelectMany()` musí vracet vyčíslitelné posloupnost hodnot pro každou zdrojovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b0515-128">The transform function that is passed as an argument to `SelectMany()` must return an enumerable sequence of values for each source value.</span></span> <span data-ttu-id="b0515-129">Tyto vyčíslitelné sekvence jsou pak zřetězeny podle `SelectMany()` vytvořte jedno velké pořadí.</span><span class="sxs-lookup"><span data-stu-id="b0515-129">These enumerable sequences are then concatenated by `SelectMany()` to create one large sequence.</span></span>  
  
 <span data-ttu-id="b0515-130">Následující dva obrázky ukazují konceptuální rozdíl mezi akcemi z těchto dvou metod.</span><span class="sxs-lookup"><span data-stu-id="b0515-130">The following two illustrations show the conceptual difference between the actions of these two methods.</span></span> <span data-ttu-id="b0515-131">V obou případech se předpokládá, že funkce selektor (transformace) vybere z každé zdrojové hodnoty pole květin.</span><span class="sxs-lookup"><span data-stu-id="b0515-131">In each case, assume that the selector (transform) function selects the array of flowers from each source value.</span></span>  
  
 <span data-ttu-id="b0515-132">Tento obrázek znázorňuje, jak `Select()` vrátí kolekci, která má stejný počet prvků jako zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="b0515-132">This illustration depicts how `Select()` returns a collection that has the same number of elements as the source collection.</span></span>  
  
 ![Obrázek znázorňující, akce Select&#40;&#41;](./media/projection-operations/select-action-graphic.png)  
  
 <span data-ttu-id="b0515-134">Tento obrázek znázorňuje, jak `SelectMany()` zřetězí zprostředkující pořadí polí do jedné hodnoty konečný výsledek, který obsahuje každou hodnotu z každé zprostředkující pole.</span><span class="sxs-lookup"><span data-stu-id="b0515-134">This illustration depicts how `SelectMany()` concatenates the intermediate sequence of arrays into one final result value that contains each value from each intermediate array.</span></span>  
  
 ![Obrázek znázorňující akce operátor SelectMany&#40;&#41;.](./media/projection-operations/select-many-action-graphic.png )  
  
### <a name="code-example"></a><span data-ttu-id="b0515-136">Příklad kódu</span><span class="sxs-lookup"><span data-stu-id="b0515-136">Code Example</span></span>  
 <span data-ttu-id="b0515-137">Následující příklad porovnává chování `Select()` a `SelectMany()`.</span><span class="sxs-lookup"><span data-stu-id="b0515-137">The following example compares the behavior of `Select()` and `SelectMany()`.</span></span> <span data-ttu-id="b0515-138">Kód vytvoří "kytice" květin díky první dvě položky z každého seznam názvů květinu ve zdrojové kolekce.</span><span class="sxs-lookup"><span data-stu-id="b0515-138">The code creates a "bouquet" of flowers by taking the first two items from each list of flower names in the source collection.</span></span> <span data-ttu-id="b0515-139">V tomto příkladu "jedna hodnota", který funkce transformace <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> používá, je samotný kolekci hodnot.</span><span class="sxs-lookup"><span data-stu-id="b0515-139">In this example, the "single value" that the transform function <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%29> uses is itself a collection of values.</span></span> <span data-ttu-id="b0515-140">To vyžaduje, aby nadbytečné `For Each` smyčky, aby bylo možné vytvořit výčet každého řetězce v každé dílčí sekvenci.</span><span class="sxs-lookup"><span data-stu-id="b0515-140">This requires the extra `For Each` loop in order to enumerate each string in each sub-sequence.</span></span>  
  
```vb  
Class Bouquet  
    Public Flowers As List(Of String)  
End Class  
  
Sub SelectVsSelectMany()  
    Dim bouquets = New List(Of Bouquet) From {   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"sunflower", "daisy", "daffodil", "larkspur"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"tulip", "rose", "orchid"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"gladiolis", "lily", "snapdragon", "aster", "protea"})},   
        New Bouquet With {.Flowers = New List(Of String)(New String() {"larkspur", "lilac", "iris", "dahlia"})}}  
  
    Dim output As New System.Text.StringBuilder  
  
    ' Select()  
    Dim query1 = bouquets.Select(Function(b) b.Flowers)  
  
    output.AppendLine("Using Select():")  
    For Each flowerList In query1  
        For Each str As String In flowerList  
            output.AppendLine(str)  
        Next  
    Next  
  
    ' SelectMany()  
    Dim query2 = bouquets.SelectMany(Function(b) b.Flowers)  
  
    output.AppendLine(vbCrLf & "Using SelectMany():")  
    For Each str As String In query2  
        output.AppendLine(str)  
    Next  
  
    ' Display the output  
    MsgBox(output.ToString())  
  
    ' This code produces the following output:  
    '  
    ' Using Select():  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
    ' Using SelectMany()  
    ' sunflower  
    ' daisy  
    ' daffodil  
    ' larkspur  
    ' tulip  
    ' rose  
    ' orchid  
    ' gladiolis  
    ' lily  
    ' snapdragon  
    ' aster  
    ' protea  
    ' larkspur  
    ' lilac  
    ' iris  
    ' dahlia  
  
End Sub  
```  
  
## <a name="see-also"></a><span data-ttu-id="b0515-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0515-141">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="b0515-142">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0515-142">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="b0515-143">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="b0515-143">Select Clause</span></span>](../../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="b0515-144">Postupy: Kombinace dat s LINQ pomocí spojení</span><span class="sxs-lookup"><span data-stu-id="b0515-144">How to: Combine Data with Joins</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-combine-data-with-linq-by-using-joins.md)
- [<span data-ttu-id="b0515-145">Postupy: Vyplňování kolekcí objektů z více zdrojů (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0515-145">How to: Populate Object Collections from Multiple Sources (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-populate-object-collections-from-multiple-sources-linq.md)
- [<span data-ttu-id="b0515-146">Postupy: Vrácení výsledku dotazu LINQ jako specifického typu</span><span class="sxs-lookup"><span data-stu-id="b0515-146">How to: Return a LINQ Query Result as a Specific Type</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-return-a-linq-query-result-as-a-specific-type.md)
- [<span data-ttu-id="b0515-147">Postupy: Rozdělení souboru na více souborů pomocí skupin (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b0515-147">How to: Split a File Into Many Files by Using Groups (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-split-a-file-into-many-files-by-using-groups-linq.md)
