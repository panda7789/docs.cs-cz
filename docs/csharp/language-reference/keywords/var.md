---
title: var (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ab49a4f4fcbc990a1fd21139397d70fa9fbf5dd8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43735634"
---
# <a name="var-c-reference"></a><span data-ttu-id="62fa1-102">var (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="62fa1-102">var (C# Reference)</span></span>
<span data-ttu-id="62fa1-103">Od Visual C# 3.0, proměnné, které jsou deklarovány v oboru metoda může mít implicitní "typ" `var`.</span><span class="sxs-lookup"><span data-stu-id="62fa1-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="62fa1-104">Implicitně typovaná lokální proměnná je tak, jako kdyby měl typ deklarovaný sami, ale kompilátor Určuje typ silného typu.</span><span class="sxs-lookup"><span data-stu-id="62fa1-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="62fa1-105">Následující dvě deklarace `i` jsou funkčně ekvivalentní:</span><span class="sxs-lookup"><span data-stu-id="62fa1-105">The following two declarations of `i` are functionally equivalent:</span></span>  
  
```csharp  
var i = 10; // Implicitly typed. 
int i = 10; // Explicitly typed. 
```  
  
 <span data-ttu-id="62fa1-106">Další informace najdete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [vztahy typů v operacích dotazu LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="62fa1-106">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="62fa1-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="62fa1-107">Example</span></span>  
 <span data-ttu-id="62fa1-108">Následující příklad ukazuje dva výrazy dotazu.</span><span class="sxs-lookup"><span data-stu-id="62fa1-108">The following example shows two query expressions.</span></span> <span data-ttu-id="62fa1-109">V prvním výrazu použití `var` je povolené, ale není vyžadováno, protože typ výsledku dotazu může být explicitně nastavená jako `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="62fa1-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="62fa1-110">Nicméně ve druhém výrazu `var` umožňuje výsledek, který má být kolekci anonymních typů, a název tohoto typu není dostupná s výjimkou samotné kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="62fa1-110">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="62fa1-111">Použití `var` eliminuje požadavek na vytvoření nové třídy pro výsledek.</span><span class="sxs-lookup"><span data-stu-id="62fa1-111">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="62fa1-112">Všimněte si, že v příkladu 2, `foreach` proměnné iterace `item` musí také být implicitně typované.</span><span class="sxs-lookup"><span data-stu-id="62fa1-112">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="62fa1-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="62fa1-113">See Also</span></span>

- [<span data-ttu-id="62fa1-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="62fa1-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="62fa1-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="62fa1-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="62fa1-116">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="62fa1-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
