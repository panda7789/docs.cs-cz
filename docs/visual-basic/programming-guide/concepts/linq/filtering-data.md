---
title: "Filtrování dat (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7749519a-7edc-49fe-aef9-6a353864af6c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 31e3a4729a98e1f4b588cd415a15fff270587234
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="filtering-data-visual-basic"></a><span data-ttu-id="40627-102">Filtrování dat (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40627-102">Filtering Data (Visual Basic)</span></span>
<span data-ttu-id="40627-103">Filtrování odkazuje na operaci omezit tak, aby obsahovala pouze elementy, které splňují zadanou podmínku sadu výsledků dotazu.</span><span class="sxs-lookup"><span data-stu-id="40627-103">Filtering refers to the operation of restricting the result set to contain only those elements that satisfy a specified condition.</span></span> <span data-ttu-id="40627-104">Je také označované jako výběr.</span><span class="sxs-lookup"><span data-stu-id="40627-104">It is also known as selection.</span></span>  
  
 <span data-ttu-id="40627-105">Následující obrázek znázorňuje výsledky filtrování posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="40627-105">The following illustration shows the results of filtering a sequence of characters.</span></span> <span data-ttu-id="40627-106">Predikát pro filtrování operaci Určuje, že znak musí být "A".</span><span class="sxs-lookup"><span data-stu-id="40627-106">The predicate for the filtering operation specifies that the character must be 'A'.</span></span>  
  
 <span data-ttu-id="40627-107">![LINQ filtrování operaci](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span><span class="sxs-lookup"><span data-stu-id="40627-107">![LINQ Filtering Operation](../../../../csharp/programming-guide/concepts/linq/media/linq_filter.png "LINQ_Filter")</span></span>  
  
 <span data-ttu-id="40627-108">Operátor metody standardní dotazu, které provedení výběru jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="40627-108">The standard query operator methods that perform selection are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40627-109">Metody</span><span class="sxs-lookup"><span data-stu-id="40627-109">Methods</span></span>  
  
|<span data-ttu-id="40627-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="40627-110">Method Name</span></span>|<span data-ttu-id="40627-111">Popis</span><span class="sxs-lookup"><span data-stu-id="40627-111">Description</span></span>|<span data-ttu-id="40627-112">Syntaxe výrazu dotazu jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="40627-112">Visual Basic Query Expression Syntax</span></span>|<span data-ttu-id="40627-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="40627-113">More Information</span></span>|  
|-----------------|-----------------|------------------------------------------|----------------------|  
|<span data-ttu-id="40627-114">OfType</span><span class="sxs-lookup"><span data-stu-id="40627-114">OfType</span></span>|<span data-ttu-id="40627-115">Vybere hodnoty, v závislosti na jejich schopnost převést na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="40627-115">Selects values, depending on their ability to be cast to a specified type.</span></span>|<span data-ttu-id="40627-116">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="40627-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.OfType%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.OfType%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="40627-117">Where</span><span class="sxs-lookup"><span data-stu-id="40627-117">Where</span></span>|<span data-ttu-id="40627-118">Vybere hodnoty, které jsou založeny na funkce predikátu.</span><span class="sxs-lookup"><span data-stu-id="40627-118">Selects values that are based on a predicate function.</span></span>|`Where`|<xref:System.Linq.Enumerable.Where%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Where%2A?displayProperty=nameWithType>|  
  
## <a name="query-expression-syntax-example"></a><span data-ttu-id="40627-119">Příklad syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="40627-119">Query Expression Syntax Example</span></span>  
 <span data-ttu-id="40627-120">Následující příklad používá `Where` vyfiltrujete z pole tyto řetězce, které mají určité délky.</span><span class="sxs-lookup"><span data-stu-id="40627-120">The following example uses the `Where` to filter from an array those strings that have a specific length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="40627-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="40627-121">See Also</span></span>  
 <xref:System.Linq>  
 [<span data-ttu-id="40627-122">Přehled standardních operátorů dotazu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40627-122">Standard Query Operators Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 [<span data-ttu-id="40627-123">Kde – klauzule</span><span class="sxs-lookup"><span data-stu-id="40627-123">Where Clause</span></span>](../../../../visual-basic/language-reference/queries/where-clause.md)  
 [<span data-ttu-id="40627-124">Postupy: filtrování výsledků dotazu</span><span class="sxs-lookup"><span data-stu-id="40627-124">How to: Filter Query Results</span></span>](../../../../visual-basic/programming-guide/language-features/linq/how-to-filter-query-results-by-using-linq.md)  
 [<span data-ttu-id="40627-125">Postupy: vytvoření dotazu na Metadata sestavení s reflexí (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40627-125">How to: Query An Assembly's Metadata with Reflection (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-an-assembly-s-metadata-with-reflection-linq.md)  
 [<span data-ttu-id="40627-126">Postupy: dotaz pro soubory s konkrétním atributem či názvem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40627-126">How to: Query for Files with a Specified Attribute or Name (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-query-for-files-with-a-specified-attribute-or-name.md)  
 [<span data-ttu-id="40627-127">Postupy: řazení nebo filtrování textových dat podle libovolného slova či pole (LINQ) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="40627-127">How to: Sort or Filter Text Data by Any Word or Field (LINQ) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/how-to-sort-or-filter-text-data-by-any-word-or-field-linq.md)
