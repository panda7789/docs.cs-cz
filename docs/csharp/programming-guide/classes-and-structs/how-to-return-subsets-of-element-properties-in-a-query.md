---
title: Jak vracet podmnožiny vlastností elementu v dotazu – Průvodce programováním v C#
description: Naučte se používat anonymní typ ve výrazu dotazu v jazyce C# pro vrácení některých vlastností každého zdrojového elementu.
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 882d94bc82527c14bd6c038f4bf574c2211b9089
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864368"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="1de5d-103">Vrácení podmnožin vlastností elementu v dotazu (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="1de5d-103">How to return subsets of element properties in a query (C# Programming Guide)</span></span>
<span data-ttu-id="1de5d-104">Použít anonymní typ ve výrazu dotazu, když platí obě tyto podmínky:</span><span class="sxs-lookup"><span data-stu-id="1de5d-104">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="1de5d-105">Chcete vrátit pouze některé vlastnosti každého zdrojového elementu.</span><span class="sxs-lookup"><span data-stu-id="1de5d-105">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="1de5d-106">Výsledky dotazu není nutné ukládat mimo rozsah metody, ve které je dotaz proveden.</span><span class="sxs-lookup"><span data-stu-id="1de5d-106">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="1de5d-107">Pokud chcete pouze vrátit jednu vlastnost nebo pole z každého elementu zdroje, můžete pouze použít operátor tečka v `select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="1de5d-107">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="1de5d-108">Například pro vrácení pouze `ID` každého z nich `student` zapište `select` klauzuli následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="1de5d-108">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="1de5d-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="1de5d-109">Example</span></span>  
 <span data-ttu-id="1de5d-110">Následující příklad ukazuje, jak použít anonymní typ pro vrácení pouze podmnožiny vlastností každého zdrojového prvku, který odpovídá zadané podmínce.</span><span class="sxs-lookup"><span data-stu-id="1de5d-110">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="1de5d-111">Všimněte si, že anonymní typ používá názvy zdrojového elementu pro jeho vlastnosti, pokud nejsou zadány žádné názvy.</span><span class="sxs-lookup"><span data-stu-id="1de5d-111">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="1de5d-112">Chcete-li zadat nové názvy vlastností v anonymním typu, zapište `select` příkaz následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="1de5d-112">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="1de5d-113">Pokud to zkusíte v předchozím příkladu, `Console.WriteLine` příkaz se musí také změnit:</span><span class="sxs-lookup"><span data-stu-id="1de5d-113">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1de5d-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1de5d-114">Compiling the Code</span></span>  
  
<span data-ttu-id="1de5d-115">Chcete-li spustit tento kód, zkopírujte a vložte třídu do konzolové aplikace v jazyce C# s `using` direktivou pro System. Linq.</span><span class="sxs-lookup"><span data-stu-id="1de5d-115">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1de5d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1de5d-116">See also</span></span>

- [<span data-ttu-id="1de5d-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="1de5d-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="1de5d-118">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="1de5d-118">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="1de5d-119">LINQ v jazyku C#</span><span class="sxs-lookup"><span data-stu-id="1de5d-119">LINQ in C#</span></span>](../../linq/index.md)
