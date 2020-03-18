---
title: Vrácení podmnožiny vlastností elementu v dotazu – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 27a2626fc46307a7195040adf746d8d8757d2f82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714860"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="72935-102">Vrácení podmnožiny vlastností elementu v dotazu (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="72935-102">How to return subsets of element properties in a query (C# Programming Guide)</span></span>
<span data-ttu-id="72935-103">Pokud platí obě tyto podmínky, použijte ve výrazu dotazu anonymní typ:</span><span class="sxs-lookup"><span data-stu-id="72935-103">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="72935-104">Chcete vrátit pouze některé vlastnosti každého zdrojového prvku.</span><span class="sxs-lookup"><span data-stu-id="72935-104">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="72935-105">Není třeba ukládat výsledky dotazu mimo rozsah metody, ve kterém je dotaz spuštěn.</span><span class="sxs-lookup"><span data-stu-id="72935-105">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="72935-106">Pokud chcete vrátit pouze jednu vlastnost nebo pole z každého zdrojového prvku, `select` můžete použít operátor tečka v klauzuli.</span><span class="sxs-lookup"><span data-stu-id="72935-106">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="72935-107">Chcete-li například `ID` vrátit `student`pouze každý `select` z nich , napište klauzuli takto:</span><span class="sxs-lookup"><span data-stu-id="72935-107">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="72935-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="72935-108">Example</span></span>  
 <span data-ttu-id="72935-109">Následující příklad ukazuje, jak pomocí anonymního typu vrátit pouze podmnožinu vlastností každého zdrojového prvku, který odpovídá zadané podmínce.</span><span class="sxs-lookup"><span data-stu-id="72935-109">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="72935-110">Všimněte si, že anonymní typ používá názvy zdrojového prvku pro jeho vlastnosti, pokud nejsou zadány žádné názvy.</span><span class="sxs-lookup"><span data-stu-id="72935-110">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="72935-111">Chcete-li vlastnostem anonymního typu přidělit `select` nové názvy, napište příkaz takto:</span><span class="sxs-lookup"><span data-stu-id="72935-111">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="72935-112">Pokud se pokusíte v předchozím `Console.WriteLine` příkladu, pak příkaz musí také změnit:</span><span class="sxs-lookup"><span data-stu-id="72935-112">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="72935-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="72935-113">Compiling the Code</span></span>  
  
<span data-ttu-id="72935-114">Chcete-li spustit tento kód, zkopírujte a vložte `using` třídu do aplikace konzoly Jazyka C# se směrnicí pro System.Linq.</span><span class="sxs-lookup"><span data-stu-id="72935-114">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="72935-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="72935-115">See also</span></span>

- [<span data-ttu-id="72935-116">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="72935-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="72935-117">Anonymní typy</span><span class="sxs-lookup"><span data-stu-id="72935-117">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="72935-118">LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="72935-118">LINQ in C#</span></span>](../../linq/index.md)
