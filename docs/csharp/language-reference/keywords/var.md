---
title: "var (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords: var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d2be56243f9c4ddafb3903d14fa6d6f9cb0e2f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="var-c-reference"></a><span data-ttu-id="208cb-102">var (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="208cb-102">var (C# Reference)</span></span>
<span data-ttu-id="208cb-103">Od verze Visual C# 3.0, proměnné, které jsou deklarované v oboru metoda může mít implicitní "typ" `var`.</span><span class="sxs-lookup"><span data-stu-id="208cb-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="208cb-104">Implicitně typovaná místní proměnné je silného typu stejně, jako kdyby měl typ deklarovaný sami, ale kompilátor Určuje typ.</span><span class="sxs-lookup"><span data-stu-id="208cb-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="208cb-105">Následujících dvou prohlášení `i` stejné funkce:</span><span class="sxs-lookup"><span data-stu-id="208cb-105">The following two declarations of `i` are functionally equivalent:</span></span>  
  
```  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 <span data-ttu-id="208cb-106">Další informace najdete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [vztahy typů v operacích dotazu LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="208cb-106">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="208cb-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="208cb-107">Example</span></span>  
 <span data-ttu-id="208cb-108">Následující příklad ukazuje dva výrazy dotazů.</span><span class="sxs-lookup"><span data-stu-id="208cb-108">The following example shows two query expressions.</span></span> <span data-ttu-id="208cb-109">V prvním výrazu, použití `var` je povoleno, ale není vyžadována, protože typ výsledku dotazu může být výslovně uvedeny jako `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="208cb-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="208cb-110">Ale v druhý výraz `var` musí použít, protože výsledek je kolekce anonymní typy a název tohoto typu není přístupný kromě kompilátoru sám sebe.</span><span class="sxs-lookup"><span data-stu-id="208cb-110">However, in the second expression, `var` must be used because the result is a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="208cb-111">Všimněte si, že v příkladu č. 2, `foreach` proměnné iterace `item` musí také být implicitně typované.</span><span class="sxs-lookup"><span data-stu-id="208cb-111">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="208cb-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="208cb-112">See Also</span></span>  
 [<span data-ttu-id="208cb-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="208cb-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="208cb-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="208cb-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="208cb-115">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="208cb-115">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
