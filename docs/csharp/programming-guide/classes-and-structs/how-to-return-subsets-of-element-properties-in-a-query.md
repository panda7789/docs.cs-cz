---
title: 'Postupy: Vrácení podmnožin vlastností elementu v dotazu - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: acff804d87d67bf8758b97ad04805359bb3f2e32
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586075"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="b2cc3-102">Postupy: Vrácení podmnožin vlastností elementu v dotazu (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="b2cc3-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="b2cc3-103">Použijte anonymního typu ve výrazu dotazu, pokud obě tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="b2cc3-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="b2cc3-104">Chcete vrátit jenom některé vlastnosti jednotlivých zdrojových elementů.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="b2cc3-105">Není nutné pro ukládání výsledků dotazu nad rámec metoda spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="b2cc3-106">Pokud chcete vrátit jednu vlastnost nebo pole z jednotlivých zdrojových elementů, pak tečka v můžete použít jenom `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="b2cc3-107">Například vrátit pouze `ID` jednotlivých `student`, zapisovat `select` klauzule následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b2cc3-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="b2cc3-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2cc3-108">Example</span></span>  
 <span data-ttu-id="b2cc3-109">Následující příklad ukazuje, jak použít anonymní typ, který vrátí pouze podmnožinu vlastností jednotlivých zdrojových elementů, který odpovídá zadané podmínce.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="b2cc3-110">Všimněte si, že používá anonymní typ zdrojového prvku názvy vlastností Pokud nejsou zadány žádné názvy.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="b2cc3-111">Chcete-li pojmenovat nové vlastnosti v anonymním typu, napište `select` příkaz následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="b2cc3-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="b2cc3-112">Pokud se to pokusíte v předchozím příkladu, pak bude `Console.WriteLine` musí také změňte příkaz:</span><span class="sxs-lookup"><span data-stu-id="b2cc3-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2cc3-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b2cc3-113">Compiling the Code</span></span>  
  
<span data-ttu-id="b2cc3-114">Tento kód spustit, zkopírujte a vložte do třídy C# konzolové aplikace pomocí `using` směrnice pro System.Linq.</span><span class="sxs-lookup"><span data-stu-id="b2cc3-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="b2cc3-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2cc3-115">See also</span></span>

- [<span data-ttu-id="b2cc3-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b2cc3-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b2cc3-117">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="b2cc3-117">Anonymous Types</span></span>](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [<span data-ttu-id="b2cc3-118">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="b2cc3-118">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
