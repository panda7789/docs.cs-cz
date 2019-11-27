---
title: Filtrování dat
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: 81e207e451055fb2952e4bf393db067f0851afb4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353483"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="8c09e-102">Filtrování dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c09e-102">Filtering Data (Visual Basic)</span></span>

<span data-ttu-id="8c09e-103">Filtrování odkazuje na operaci omezení sady výsledků tak, aby obsahovala pouze prvky, které odpovídají zadané podmínce.</span><span class="sxs-lookup"><span data-stu-id="8c09e-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="8c09e-104">Označuje se také jako výběr.</span><span class="sxs-lookup"><span data-stu-id="8c09e-104">It is also known as selection.</span></span>

<span data-ttu-id="8c09e-105">Následující ilustrace znázorňuje výsledky filtrování posloupnosti znaků.</span><span class="sxs-lookup"><span data-stu-id="8c09e-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="8c09e-106">Predikát pro operaci filtrování určuje, že znak musí být "A".</span><span class="sxs-lookup"><span data-stu-id="8c09e-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>

![Diagram, který znázorňuje operaci filtrování LINQ](./media/filtering-data/linq-filter-operation.png)

<span data-ttu-id="8c09e-108">Standardní metody operátoru dotazu, které provádějí výběr, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="8c09e-108">The standard query operator methods that perform selection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="8c09e-109">Metody</span><span class="sxs-lookup"><span data-stu-id="8c09e-109">Methods</span></span>

|<span data-ttu-id="8c09e-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="8c09e-110">Method Name</span></span>|<span data-ttu-id="8c09e-111">Popis</span><span class="sxs-lookup"><span data-stu-id="8c09e-111">Description</span></span>|<span data-ttu-id="8c09e-112">Visual Basic syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="8c09e-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="8c09e-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="8c09e-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="8c09e-114">Only</span><span class="sxs-lookup"><span data-stu-id="8c09e-114">OfType</span></span>|<span data-ttu-id="8c09e-115">Vybere hodnoty v závislosti na jejich schopnosti je přetypovat na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="8c09e-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="8c09e-116">Není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8c09e-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="8c09e-117">Where</span><span class="sxs-lookup"><span data-stu-id="8c09e-117">Where</span></span>|<span data-ttu-id="8c09e-118">Vybere hodnoty, které jsou založeny na funkci predikátu.</span><span class="sxs-lookup"><span data-stu-id="8c09e-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="8c09e-119">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="8c09e-119">Query Expression Syntax Example</span></span>

<span data-ttu-id="8c09e-120">Následující příklad používá `Where` k filtrování z pole, která mají určitou délku.</span><span class="sxs-lookup"><span data-stu-id="8c09e-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8c09e-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c09e-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="8c09e-122">Přehled standardních operátorů dotazů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c09e-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="8c09e-123">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="8c09e-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="8c09e-124">Postupy: filtrování výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="8c09e-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="8c09e-125">Postupy: vytvoření dotazu na metadata sestavení s reflexí (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c09e-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="8c09e-126">Postupy: dotazování na soubory se zadaným atributem nebo názvem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c09e-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="8c09e-127">Postupy: řazení nebo filtrování textových dat podle libovolného slova nebo pole (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8c09e-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
