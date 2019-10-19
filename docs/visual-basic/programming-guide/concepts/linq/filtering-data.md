---
title: Filtrování dat (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: 27765247daa2155e685b1cd2bfccebb3216ca672
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582433"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="dab5a-102">Filtrování dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dab5a-102">Filtering Data (Visual Basic)</span></span>

<span data-ttu-id="dab5a-103">Filtrování odkazuje na operaci omezení sady výsledků tak, aby obsahovala pouze prvky, které odpovídají zadané podmínce.</span><span class="sxs-lookup"><span data-stu-id="dab5a-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="dab5a-104">Označuje se také jako výběr.</span><span class="sxs-lookup"><span data-stu-id="dab5a-104">It is also known as selection.</span></span>

<span data-ttu-id="dab5a-105">Následující ilustrace znázorňuje výsledky filtrování posloupnosti znaků.</span><span class="sxs-lookup"><span data-stu-id="dab5a-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="dab5a-106">Predikát pro operaci filtrování určuje, že znak musí být "A".</span><span class="sxs-lookup"><span data-stu-id="dab5a-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>

![Diagram, který znázorňuje operaci filtrování LINQ](./media/filtering-data/linq-filter-operation.png)

<span data-ttu-id="dab5a-108">Standardní metody operátoru dotazu, které provádějí výběr, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="dab5a-108">The standard query operator methods that perform selection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="dab5a-109">Metody</span><span class="sxs-lookup"><span data-stu-id="dab5a-109">Methods</span></span>

|<span data-ttu-id="dab5a-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="dab5a-110">Method Name</span></span>|<span data-ttu-id="dab5a-111">Popis</span><span class="sxs-lookup"><span data-stu-id="dab5a-111">Description</span></span>|<span data-ttu-id="dab5a-112">Visual Basic syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="dab5a-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="dab5a-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="dab5a-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="dab5a-114">Only</span><span class="sxs-lookup"><span data-stu-id="dab5a-114">OfType</span></span>|<span data-ttu-id="dab5a-115">Vybere hodnoty v závislosti na jejich schopnosti je přetypovat na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="dab5a-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="dab5a-116">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="dab5a-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="dab5a-117">Where</span><span class="sxs-lookup"><span data-stu-id="dab5a-117">Where</span></span>|<span data-ttu-id="dab5a-118">Vybere hodnoty, které jsou založeny na funkci predikátu.</span><span class="sxs-lookup"><span data-stu-id="dab5a-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="dab5a-119">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="dab5a-119">Query Expression Syntax Example</span></span>

<span data-ttu-id="dab5a-120">Následující příklad používá `Where` k filtrování z pole, která mají určitou délku.</span><span class="sxs-lookup"><span data-stu-id="dab5a-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>

```vb
Dim words() As String = {"the", "quick", "brown", "fox", "jumps"}

Dim query = From word In words
            Where word.Length = 3
            Select word

Dim sb As New System.Text.StringBuilder()
For Each str As String In query
    sb.AppendLine(str)
Next

' Display the results.
MsgBox(sb.ToString())

' This code produces the following output:

' the
' fox
```

## <a name="see-also"></a><span data-ttu-id="dab5a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dab5a-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="dab5a-122">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dab5a-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="dab5a-123">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="dab5a-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="dab5a-124">Postupy: filtrování výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="dab5a-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="dab5a-125">Postupy: vytvoření dotazu na metadata sestavení s reflexí (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dab5a-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="dab5a-126">Postupy: dotazování na soubory se zadaným atributem nebo názvem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dab5a-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="dab5a-127">Postupy: řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dab5a-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
