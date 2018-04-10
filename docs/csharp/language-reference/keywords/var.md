---
title: var (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
caps.latest.revision: 13
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e0df25eb46bb769214412646d0ac3a7a576b3b73
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="var-c-reference"></a><span data-ttu-id="ae86e-102">var (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ae86e-102">var (C# Reference)</span></span>
<span data-ttu-id="ae86e-103">Od verze Visual C# 3.0, proměnné, které jsou deklarované v oboru metoda může mít implicitní "typ" `var`.</span><span class="sxs-lookup"><span data-stu-id="ae86e-103">Beginning in Visual C# 3.0, variables that are declared at method scope can have an implicit "type" `var`.</span></span> <span data-ttu-id="ae86e-104">Implicitně typovaná místní proměnné je silného typu stejně, jako kdyby měl typ deklarovaný sami, ale kompilátor Určuje typ.</span><span class="sxs-lookup"><span data-stu-id="ae86e-104">An implicitly typed local variable is strongly typed just as if you had declared the type yourself, but the compiler determines the type.</span></span> <span data-ttu-id="ae86e-105">Následujících dvou prohlášení `i` stejné funkce:</span><span class="sxs-lookup"><span data-stu-id="ae86e-105">The following two declarations of `i` are functionally equivalent:</span></span>  
  
```  
var i = 10; // implicitly typed  
int i = 10; //explicitly typed  
```  
  
 <span data-ttu-id="ae86e-106">Další informace najdete v tématu [implicitně typované lokální proměnné](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [vztahy typů v operacích dotazu LINQ](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span><span class="sxs-lookup"><span data-stu-id="ae86e-106">For more information, see [Implicitly Typed Local Variables](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) and [Type Relationships in LINQ Query Operations](../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae86e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae86e-107">Example</span></span>  
 <span data-ttu-id="ae86e-108">Následující příklad ukazuje dva výrazy dotazů.</span><span class="sxs-lookup"><span data-stu-id="ae86e-108">The following example shows two query expressions.</span></span> <span data-ttu-id="ae86e-109">V prvním výrazu, použití `var` je povoleno, ale není vyžadována, protože typ výsledku dotazu může být výslovně uvedeny jako `IEnumerable<string>`.</span><span class="sxs-lookup"><span data-stu-id="ae86e-109">In the first expression, the use of `var` is permitted but is not required, because the type of the query result can be stated explicitly as an `IEnumerable<string>`.</span></span> <span data-ttu-id="ae86e-110">Ale v druhý výraz `var` umožňuje výsledek, který má být kolekce anonymní typy a název tohoto typu není přístupný kromě kompilátoru sám sebe.</span><span class="sxs-lookup"><span data-stu-id="ae86e-110">However, in the second expression, `var` allows the result to be a collection of anonymous types, and the name of that type is not accessible except to the compiler itself.</span></span> <span data-ttu-id="ae86e-111">Použití `var` eliminuje požadavek na vytvoření nové třídy pro výsledek.</span><span class="sxs-lookup"><span data-stu-id="ae86e-111">Use of `var` eliminates the requirement to create a new class for the result.</span></span> <span data-ttu-id="ae86e-112">Všimněte si, že v příkladu č. 2, `foreach` proměnné iterace `item` musí také být implicitně typované.</span><span class="sxs-lookup"><span data-stu-id="ae86e-112">Note that in Example #2, the `foreach` iteration variable `item` must also be implicitly typed.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#18](../../../csharp/language-reference/keywords/codesnippet/CSharp/var_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ae86e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae86e-113">See Also</span></span>  
 [<span data-ttu-id="ae86e-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ae86e-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ae86e-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ae86e-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ae86e-116">Implicitně typované lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="ae86e-116">Implicitly Typed Local Variables</span></span>](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
