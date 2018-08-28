---
title: protected (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: 2da8211ac21a5016478e7b881e7f2f9925b49cef
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2018
ms.locfileid: "43001331"
---
# <a name="protected-c-reference"></a><span data-ttu-id="ab7a2-102">protected (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ab7a2-102">protected (C# Reference)</span></span>
<span data-ttu-id="ab7a2-103">`protected` – Klíčové slovo je modifikátor přístupu členu.</span><span class="sxs-lookup"><span data-stu-id="ab7a2-103">The `protected` keyword is a member access modifier.</span></span> 

 > <span data-ttu-id="ab7a2-104">Tato stránka popisuje `protected` přístup.</span><span class="sxs-lookup"><span data-stu-id="ab7a2-104">This page covers `protected` access.</span></span> <span data-ttu-id="ab7a2-105">`protected` – Klíčové slovo je také součástí [ `protected internal` ](./protected-internal.md) a [ `private protected` ](./private-protected.md) modifikátorů přístupu.</span><span class="sxs-lookup"><span data-stu-id="ab7a2-105">The `protected` keyword is also part of the [`protected internal`](./protected-internal.md) and [`private protected`](./private-protected.md) access modifiers.</span></span> 

<span data-ttu-id="ab7a2-106">Chráněný člen je přístupný v rámci své třídy a instance odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ab7a2-106">A protected member is accessible within its class and by derived class instances.</span></span> 

<span data-ttu-id="ab7a2-107">Porovnání `protected` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ab7a2-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
  
## <a name="example"></a><span data-ttu-id="ab7a2-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab7a2-108">Example</span></span>  
 <span data-ttu-id="ab7a2-109">Chráněný člen základní třídy je přístupný v odvozené třídě pouze v případě, že dojde k přístup až po typ odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ab7a2-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="ab7a2-110">Představte si třeba následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="ab7a2-110">For example, consider the following code segment:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 <span data-ttu-id="ab7a2-111">Příkaz `a.x = 10` dojde k chybě, protože se provádí v rámci statickou metodu Main, a ne instance třídy B.</span><span class="sxs-lookup"><span data-stu-id="ab7a2-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>  
  
 <span data-ttu-id="ab7a2-112">Členy struktury nejde chránit, protože struktura nemůže dědit.</span><span class="sxs-lookup"><span data-stu-id="ab7a2-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab7a2-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab7a2-113">Example</span></span>  
 <span data-ttu-id="ab7a2-114">V tomto příkladu třída `DerivedPoint` je odvozen z `Point`.</span><span class="sxs-lookup"><span data-stu-id="ab7a2-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="ab7a2-115">Proto můžete přistupovat k chráněným členům základní třídy přímo z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ab7a2-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 <span data-ttu-id="ab7a2-116">Pokud změníte úrovně přístupu `x` a `y` k [privátní](../../../csharp/language-reference/keywords/private.md), kompilátor vydá chybové zprávy:</span><span class="sxs-lookup"><span data-stu-id="ab7a2-116">If you change the access levels of `x` and `y` to [private](../../../csharp/language-reference/keywords/private.md), the compiler will issue the error messages:</span></span>  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="ab7a2-117">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ab7a2-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## 

- [<span data-ttu-id="ab7a2-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ab7a2-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="ab7a2-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ab7a2-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="ab7a2-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ab7a2-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="ab7a2-121">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="ab7a2-121">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
- [<span data-ttu-id="ab7a2-122">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="ab7a2-122">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
- [<span data-ttu-id="ab7a2-123">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="ab7a2-123">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
- [<span data-ttu-id="ab7a2-124">public</span><span class="sxs-lookup"><span data-stu-id="ab7a2-124">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
- [<span data-ttu-id="ab7a2-125">private</span><span class="sxs-lookup"><span data-stu-id="ab7a2-125">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
- [<span data-ttu-id="ab7a2-126">internal</span><span class="sxs-lookup"><span data-stu-id="ab7a2-126">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
- <span data-ttu-id="ab7a2-127">[Zajištění zabezpečení pro klíčových slov internal virtual](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="ab7a2-127">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>