---
title: "private (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9cc8f86166888b47a758e200182d319c68ca6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="private-c-reference"></a><span data-ttu-id="f8d09-102">private (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f8d09-102">private (C# Reference)</span></span>
<span data-ttu-id="f8d09-103">`private` – Klíčové slovo je modifikátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="f8d09-103">The `private` keyword is a member access modifier.</span></span> 
   
 > <span data-ttu-id="f8d09-104">Tato stránka popisuje `private` přístup.</span><span class="sxs-lookup"><span data-stu-id="f8d09-104">This page covers `private` access.</span></span> <span data-ttu-id="f8d09-105">`private` – Klíčové slovo je také součástí [ `private protected` ](./private-protected.md) – modifikátor přístupu.</span><span class="sxs-lookup"><span data-stu-id="f8d09-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>
  
<span data-ttu-id="f8d09-106">Soukromý přístup je omezenou úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="f8d09-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="f8d09-107">Soukromé členy jsou přístupné pouze v rámci tělo třídě nebo struktuře, ve které jsou deklarovány, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="f8d09-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  

 <span data-ttu-id="f8d09-108">Vnořené typy v těle stejné lze rovněž použít tyto soukromé členy.</span><span class="sxs-lookup"><span data-stu-id="f8d09-108">Nested types in the same body can also access those private members.</span></span>  
  
 <span data-ttu-id="f8d09-109">Jedná o chybu kompilace tak, aby odkazovaly privátního člena mimo třídě nebo struktuře, ve kterém je deklarovaná.</span><span class="sxs-lookup"><span data-stu-id="f8d09-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>  
  
 <span data-ttu-id="f8d09-110">Porovnání `private` s další modifikátory přístupu, přečtěte si téma [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md) a [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="f8d09-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) and [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8d09-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8d09-111">Example</span></span>  
 <span data-ttu-id="f8d09-112">V tomto příkladu `Employee` třída obsahuje dva private členy `name` a `salary`.</span><span class="sxs-lookup"><span data-stu-id="f8d09-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="f8d09-113">Jako soukromé členy k nim být přístup s výjimkou metody člen.</span><span class="sxs-lookup"><span data-stu-id="f8d09-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="f8d09-114">Veřejné metody s názvem `GetName` a `Salary` jsou přidány do povolit řízené přístup k soukromé členy.</span><span class="sxs-lookup"><span data-stu-id="f8d09-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="f8d09-115">`name` Člen přistupuje prostřednictvím veřejná metoda a `salary` člen přistupuje prostřednictvím veřejné vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="f8d09-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="f8d09-116">(Viz [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md) Další informace.)</span><span class="sxs-lookup"><span data-stu-id="f8d09-116">(See [Properties](../../../csharp/programming-guide/classes-and-structs/properties.md) for more information.)</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f8d09-117">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f8d09-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f8d09-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8d09-118">See Also</span></span>  
 [<span data-ttu-id="f8d09-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f8d09-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f8d09-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f8d09-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f8d09-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f8d09-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f8d09-122">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="f8d09-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="f8d09-123">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="f8d09-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="f8d09-124">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="f8d09-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="f8d09-125">veřejné</span><span class="sxs-lookup"><span data-stu-id="f8d09-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="f8d09-126">chráněný</span><span class="sxs-lookup"><span data-stu-id="f8d09-126">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="f8d09-127">interní</span><span class="sxs-lookup"><span data-stu-id="f8d09-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
