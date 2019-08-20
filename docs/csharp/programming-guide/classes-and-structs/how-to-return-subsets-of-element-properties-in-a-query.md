---
title: 'Postupy: Vrácení podmnožiny vlastností elementu v dotazu – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 9238e2e312021958ad62eeba89fe8b72c113e0d7
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596844"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="62367-102">Postupy: Vrácení podmnožiny vlastností elementu v dotazu (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="62367-102">How to: Return Subsets of Element Properties in a Query (C# Programming Guide)</span></span>
<span data-ttu-id="62367-103">Použít anonymní typ ve výrazu dotazu, když platí obě tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="62367-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="62367-104">Chcete vrátit pouze některé vlastnosti každého zdrojového elementu.</span><span class="sxs-lookup"><span data-stu-id="62367-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="62367-105">Výsledky dotazu není nutné ukládat mimo rozsah metody, ve které je dotaz proveden.</span><span class="sxs-lookup"><span data-stu-id="62367-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="62367-106">Pokud chcete pouze vrátit jednu vlastnost nebo pole z každého elementu zdroje, můžete pouze použít operátor tečka v `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="62367-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="62367-107">Například pro vrácení pouze `ID` každého z nich `student`zapište `select` klauzuli následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="62367-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="62367-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="62367-108">Example</span></span>  
 <span data-ttu-id="62367-109">Následující příklad ukazuje, jak použít anonymní typ pro vrácení pouze podmnožiny vlastností každého zdrojového prvku, který odpovídá zadané podmínce.</span><span class="sxs-lookup"><span data-stu-id="62367-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="62367-110">Všimněte si, že anonymní typ používá názvy zdrojového elementu pro jeho vlastnosti, pokud nejsou zadány žádné názvy.</span><span class="sxs-lookup"><span data-stu-id="62367-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="62367-111">Chcete-li zadat nové názvy vlastností v anonymním typu, zapište `select` příkaz následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="62367-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="62367-112">Pokud to zkusíte v předchozím příkladu, `Console.WriteLine` příkaz se musí také změnit:</span><span class="sxs-lookup"><span data-stu-id="62367-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="62367-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="62367-113">Compiling the Code</span></span>  
  
<span data-ttu-id="62367-114">Chcete-li spustit tento kód, zkopírujte a vložte třídu do C# konzolové aplikace s `using` direktivou pro System. Linq.</span><span class="sxs-lookup"><span data-stu-id="62367-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="62367-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62367-115">See also</span></span>

- [<span data-ttu-id="62367-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="62367-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="62367-117">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="62367-117">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="62367-118">Výrazy dotazů LINQ</span><span class="sxs-lookup"><span data-stu-id="62367-118">LINQ Query Expressions</span></span>](../linq-query-expressions/index.md)
