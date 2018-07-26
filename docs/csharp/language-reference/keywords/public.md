---
title: public (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 9bef5d076d9ab84aa15e2cdec2d176db8d1ac82b
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960241"
---
# <a name="public-c-reference"></a><span data-ttu-id="11ec8-102">public (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="11ec8-102">public (C# Reference)</span></span>
<span data-ttu-id="11ec8-103">`public` – Klíčové slovo je modifikátor přístupu pro typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="11ec8-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="11ec8-104">Veřejný přístup je nejvíce omezující úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="11ec8-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="11ec8-105">Neexistují žádná omezení na přístup k veřejným členům, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="11ec8-105">There are no restrictions on accessing public members, as in this example:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 <span data-ttu-id="11ec8-106">Zobrazit [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) a [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="11ec8-106">See [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11ec8-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="11ec8-107">Example</span></span>  
 <span data-ttu-id="11ec8-108">V následujícím příkladu se deklarovat dvě třídy, `PointTest` a `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="11ec8-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="11ec8-109">Veřejné členy `x` a `y` z `PointTest` přistupují přímo z `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="11ec8-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 <span data-ttu-id="11ec8-110">Pokud změníte `public` úroveň přístupu k [privátní](../../../csharp/language-reference/keywords/private.md) nebo [chráněné](../../../csharp/language-reference/keywords/protected.md), zobrazí se chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="11ec8-110">If you change the `public` access level to [private](../../../csharp/language-reference/keywords/private.md) or [protected](../../../csharp/language-reference/keywords/protected.md), you will get the error message:</span></span>  
  
 <span data-ttu-id="11ec8-111">"PointTest.y" je vzhledem k úrovni ochrany nepřístupný.</span><span class="sxs-lookup"><span data-stu-id="11ec8-111">'PointTest.y' is inaccessible due to its protection level.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="11ec8-112">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="11ec8-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="11ec8-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="11ec8-113">See Also</span></span>  
 [<span data-ttu-id="11ec8-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="11ec8-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="11ec8-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="11ec8-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="11ec8-116">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="11ec8-116">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="11ec8-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="11ec8-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="11ec8-118">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="11ec8-118">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="11ec8-119">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="11ec8-119">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="11ec8-120">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="11ec8-120">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="11ec8-121">private</span><span class="sxs-lookup"><span data-stu-id="11ec8-121">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="11ec8-122">protected</span><span class="sxs-lookup"><span data-stu-id="11ec8-122">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="11ec8-123">internal</span><span class="sxs-lookup"><span data-stu-id="11ec8-123">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
