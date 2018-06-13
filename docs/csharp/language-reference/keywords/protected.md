---
title: protected (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: a3115fe82b452f52ee75cf222302ece0fc67b330
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269567"
---
# <a name="protected-c-reference"></a><span data-ttu-id="aabd2-102">protected (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="aabd2-102">protected (C# Reference)</span></span>
<span data-ttu-id="aabd2-103">`protected` – Klíčové slovo je modifikátor přístupu členů.</span><span class="sxs-lookup"><span data-stu-id="aabd2-103">The `protected` keyword is a member access modifier.</span></span> 

 > <span data-ttu-id="aabd2-104">Tato stránka popisuje `protected` přístup.</span><span class="sxs-lookup"><span data-stu-id="aabd2-104">This page covers `protected` access.</span></span> <span data-ttu-id="aabd2-105">`protected` – Klíčové slovo je také součástí [ `protected internal` ](./protected-internal.md) a [ `private protected` ](./private-protected.md) přístup modifikátory.</span><span class="sxs-lookup"><span data-stu-id="aabd2-105">The `protected` keyword is also part of the [`protected internal`](./protected-internal.md) and [`private protected`](./private-protected.md) access modifiers.</span></span> 

<span data-ttu-id="aabd2-106">Chráněný člen je přístupný v rámci své třídy a instance odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="aabd2-106">A protected member is accessible within its class and by derived class instances.</span></span> 

<span data-ttu-id="aabd2-107">Porovnání `protected` s další modifikátory přístupu, přečtěte si téma [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="aabd2-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
  
## <a name="example"></a><span data-ttu-id="aabd2-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="aabd2-108">Example</span></span>  
 <span data-ttu-id="aabd2-109">Chráněný člen základní třídy je dostupné v odvozené třídě pouze v případě, že dojde k přístupu prostřednictvím typu odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="aabd2-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="aabd2-110">Zvažte například následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="aabd2-110">For example, consider the following code segment:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 <span data-ttu-id="aabd2-111">Příkaz `a.x = 10` vygeneruje chybu, protože se provádí v rámci statickou metodu Main, a ne instance třídy B.</span><span class="sxs-lookup"><span data-stu-id="aabd2-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>  
  
 <span data-ttu-id="aabd2-112">Členové struktury nelze chránit, protože nelze zděděná struct.</span><span class="sxs-lookup"><span data-stu-id="aabd2-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aabd2-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="aabd2-113">Example</span></span>  
 <span data-ttu-id="aabd2-114">V tomto příkladu třída `DerivedPoint` je odvozený od `Point`.</span><span class="sxs-lookup"><span data-stu-id="aabd2-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="aabd2-115">Proto můžete přistupovat chráněné členy základní třídy přímo z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="aabd2-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 <span data-ttu-id="aabd2-116">Pokud změníte úrovněmi přístupu `x` a `y` k [privátní](../../../csharp/language-reference/keywords/private.md), kompilátor vydá chybové zprávy:</span><span class="sxs-lookup"><span data-stu-id="aabd2-116">If you change the access levels of `x` and `y` to [private](../../../csharp/language-reference/keywords/private.md), the compiler will issue the error messages:</span></span>  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="aabd2-117">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aabd2-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aabd2-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="aabd2-118">See Also</span></span>  
 [<span data-ttu-id="aabd2-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aabd2-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="aabd2-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="aabd2-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="aabd2-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="aabd2-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="aabd2-122">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="aabd2-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="aabd2-123">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="aabd2-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="aabd2-124">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="aabd2-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="aabd2-125">public</span><span class="sxs-lookup"><span data-stu-id="aabd2-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="aabd2-126">private</span><span class="sxs-lookup"><span data-stu-id="aabd2-126">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="aabd2-127">internal</span><span class="sxs-lookup"><span data-stu-id="aabd2-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 <span data-ttu-id="aabd2-128">[Otázky zabezpečení pro interní virtuální klíčová slova](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="aabd2-128">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>