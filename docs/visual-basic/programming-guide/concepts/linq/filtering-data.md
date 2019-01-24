---
title: Filtrování dat (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
ms.openlocfilehash: d65b9941ceffa7ea23c4ead192ec6b97b7b4ead8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527832"
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="11291-102">Filtrování dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11291-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="11291-103">Filtrování odkazuje na operaci omezení sady výsledků do obsahovat pouze prvky, které splňují zadanou podmínku.</span><span class="sxs-lookup"><span data-stu-id="11291-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="11291-104">Je také označován jako výběr.</span><span class="sxs-lookup"><span data-stu-id="11291-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="11291-105">Následující obrázek ukazuje výsledky filtrování posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="11291-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="11291-106">Predikát pro filtrování operace určuje, že znak musí být "A".</span><span class="sxs-lookup"><span data-stu-id="11291-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="11291-107">![Filtrování operace LINQ](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="11291-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="11291-108">V následující části jsou uvedeny standardní metody operátoru dotazu, které provádějí výběru.</span><span class="sxs-lookup"><span data-stu-id="11291-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11291-109">Metody</span><span class="sxs-lookup"><span data-stu-id="11291-109">Methods</span></span>  
  
|<span data-ttu-id="11291-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="11291-110">Method Name</span></span>|<span data-ttu-id="11291-111">Popis</span><span class="sxs-lookup"><span data-stu-id="11291-111">Description</span></span>|<span data-ttu-id="11291-112">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="11291-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="11291-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="11291-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="11291-114">OfType</span><span class="sxs-lookup"><span data-stu-id="11291-114">OfType</span></span>|<span data-ttu-id="11291-115">Vybere hodnoty v závislosti na jejich schopnost převést na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="11291-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="11291-116">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="11291-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="11291-117">Where</span><span class="sxs-lookup"><span data-stu-id="11291-117">Where</span></span>|<span data-ttu-id="11291-118">Vybere hodnoty, které jsou založeny na funkce predikátu.</span><span class="sxs-lookup"><span data-stu-id="11291-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="11291-119">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="11291-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="11291-120">V následujícím příkladu `Where` filtrovat z pole těchto řetězců, které mají určité délky.</span><span class="sxs-lookup"><span data-stu-id="11291-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11291-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11291-121">See also</span></span>
- <xref:System.Linq>
- [<span data-ttu-id="11291-122">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11291-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)
- [<span data-ttu-id="11291-123">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="11291-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)
- [<span data-ttu-id="11291-124">Postupy: Filtrování výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="11291-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)
- [<span data-ttu-id="11291-125">Postupy: Dotazu na Metadata sestavení s reflexí (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11291-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)
- [<span data-ttu-id="11291-126">Postupy: Dotaz pro soubory s konkrétním atributem či názvem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11291-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)
- [<span data-ttu-id="11291-127">Postupy: Řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="11291-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
