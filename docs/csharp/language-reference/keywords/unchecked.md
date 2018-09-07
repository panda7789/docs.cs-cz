---
title: unchecked (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: daccd7916a9f81f26f468ab0f64833d9537cff8e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44066919"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="7a75d-102">unchecked (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7a75d-102">unchecked (C# Reference)</span></span>
<span data-ttu-id="7a75d-103">`unchecked` – Klíčové slovo se používá k potlačení kontroly přetečení pro aritmetické operace s celými čísly a převody.</span><span class="sxs-lookup"><span data-stu-id="7a75d-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>  
  
 <span data-ttu-id="7a75d-104">Nekontrolovaném kontextu Pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu přetečení, není označena.</span><span class="sxs-lookup"><span data-stu-id="7a75d-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="7a75d-105">Například protože výpočet v následujícím příkladu se provádí v `unchecked` bloku nebo výraz, skutečnost, že je výsledek příliš velký pro celé číslo se ignoruje, a `int1` je přiřazena hodnota-2,147,483,639.</span><span class="sxs-lookup"><span data-stu-id="7a75d-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_1.cs)]  
  
 <span data-ttu-id="7a75d-106">Pokud `unchecked` se odebere prostředí, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="7a75d-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="7a75d-107">Přetečení lze zjistit v době kompilace, protože všechny podmínky výrazu jsou konstanty.</span><span class="sxs-lookup"><span data-stu-id="7a75d-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>  
  
 <span data-ttu-id="7a75d-108">Výrazy, které obsahují nekonstantní podmínky jsou ve výchozím nastavení zaškrtnuté políčko v době kompilace a čas spuštění.</span><span class="sxs-lookup"><span data-stu-id="7a75d-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="7a75d-109">Zobrazit [zaškrtnutí](../../../csharp/language-reference/keywords/checked.md) informace o povolení kontrolované prostředí.</span><span class="sxs-lookup"><span data-stu-id="7a75d-109">See [checked](../../../csharp/language-reference/keywords/checked.md) for information about enabling a checked environment.</span></span>  
  
 <span data-ttu-id="7a75d-110">Protože kontrole pro přetečení trvá určitou dobu, použití nezaškrtnuto kódu v situacích, ve kterých je nehrozí nebezpečí přetečení může zlepšit výkon.</span><span class="sxs-lookup"><span data-stu-id="7a75d-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="7a75d-111">Ale pokud přetečení je možné, by měl použít kontrolované prostředí.</span><span class="sxs-lookup"><span data-stu-id="7a75d-111">However, if overflow is a possibility, a checked environment should be used.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a75d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a75d-112">Example</span></span>  
 <span data-ttu-id="7a75d-113">Tento příklad ukazuje způsob použití `unchecked` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="7a75d-113">This sample shows how to use the `unchecked` keyword.</span></span>  
  
 [!code-csharp[csrefKeywordsChecked#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/unchecked_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="7a75d-114">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7a75d-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7a75d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a75d-115">See Also</span></span>

- [<span data-ttu-id="7a75d-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7a75d-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="7a75d-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7a75d-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="7a75d-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7a75d-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="7a75d-119">Zaškrtnuto a nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="7a75d-119">Checked and Unchecked</span></span>](../../../csharp/language-reference/keywords/checked-and-unchecked.md)  
- [<span data-ttu-id="7a75d-120">checked</span><span class="sxs-lookup"><span data-stu-id="7a75d-120">checked</span></span>](../../../csharp/language-reference/keywords/checked.md)
