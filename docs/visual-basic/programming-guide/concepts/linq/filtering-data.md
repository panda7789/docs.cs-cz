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
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="1bcdb-102">Filtering Data (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bcdb-102">Filtering Data (Visual Basic)</span></span>

<span data-ttu-id="1bcdb-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span><span class="sxs-lookup"><span data-stu-id="1bcdb-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="1bcdb-104">It is also known as selection.</span><span class="sxs-lookup"><span data-stu-id="1bcdb-104">It is also known as selection.</span></span>

<span data-ttu-id="1bcdb-105">The following illustration shows the results of filtering a sequence of characters.</span><span class="sxs-lookup"><span data-stu-id="1bcdb-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="1bcdb-106">The predicate for the filtering operation specifies that the character must be 'A'.</span><span class="sxs-lookup"><span data-stu-id="1bcdb-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>

![Diagram that shows a LINQ filtering operation](./media/filtering-data/linq-filter-operation.png)

<span data-ttu-id="1bcdb-108">The standard query operator methods that perform selection are listed in the following section.</span><span class="sxs-lookup"><span data-stu-id="1bcdb-108">The standard query operator methods that perform selection are listed in the following section.</span></span>

## <a name="methods"></a><span data-ttu-id="1bcdb-109">Metody</span><span class="sxs-lookup"><span data-stu-id="1bcdb-109">Methods</span></span>

|<span data-ttu-id="1bcdb-110">Method Name</span><span class="sxs-lookup"><span data-stu-id="1bcdb-110">Method Name</span></span>|<span data-ttu-id="1bcdb-111">Popis</span><span class="sxs-lookup"><span data-stu-id="1bcdb-111">Description</span></span>|<span data-ttu-id="1bcdb-112">Visual Basic Query Expression Syntax</span><span class="sxs-lookup"><span data-stu-id="1bcdb-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="1bcdb-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="1bcdb-113">More Information</span></span>|
|-----------------|-----------------|------------------------------------------|----------------------|
|<span data-ttu-id="1bcdb-114">OfType</span><span class="sxs-lookup"><span data-stu-id="1bcdb-114">OfType</span></span>|<span data-ttu-id="1bcdb-115">Selects values, depending on their ability to be cast to a specified type.</span><span class="sxs-lookup"><span data-stu-id="1bcdb-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="1bcdb-116">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="1bcdb-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|
|<span data-ttu-id="1bcdb-117">Where</span><span class="sxs-lookup"><span data-stu-id="1bcdb-117">Where</span></span>|<span data-ttu-id="1bcdb-118">Selects values that are based on a predicate function.</span><span class="sxs-lookup"><span data-stu-id="1bcdb-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|

## <a name="query-expression-syntax-example"></a><span data-ttu-id="1bcdb-119">Query Expression Syntax Example</span><span class="sxs-lookup"><span data-stu-id="1bcdb-119">Query Expression Syntax Example</span></span>

<span data-ttu-id="1bcdb-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span><span class="sxs-lookup"><span data-stu-id="1bcdb-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1bcdb-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1bcdb-121">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="1bcdb-122">Standard Query Operators Overview (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bcdb-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="1bcdb-123">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="1bcdb-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="1bcdb-124">How to: Filter Query Results</span><span class="sxs-lookup"><span data-stu-id="1bcdb-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="1bcdb-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bcdb-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="1bcdb-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bcdb-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="1bcdb-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1bcdb-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
