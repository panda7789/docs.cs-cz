---
title: nezaškrtnuté klíčové slovo C# – odkaz
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 6dad0dfd508fb390dd0a52d1b48d70b4c5725513
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712998"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="2d4b5-102">unchecked (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2d4b5-102">unchecked (C# Reference)</span></span>

<span data-ttu-id="2d4b5-103">Klíčové slovo `unchecked` slouží k potlačení kontroly přetečení pro aritmetické operace a převody integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="2d4b5-104">V nekontrolovaném kontextu, pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu, přetečení není označeno příznakem.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="2d4b5-105">Například vzhledem k tomu, že výpočet v následujícím příkladu je proveden v `unchecked` bloku nebo výrazu, je fakt, že výsledek je příliš velký pro celé číslo, ignorován a `int1` je přiřazena hodnota-2 147 483 639.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="2d4b5-106">Pokud je prostředí `unchecked` odebrané, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="2d4b5-107">Přetečení lze zjistit v době kompilace, protože všechny výrazy výrazu jsou konstanty.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="2d4b5-108">Výrazy, které obsahují nekonstantní podmínky, jsou ve výchozím nastavení v době kompilace a v době spuštění nezaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="2d4b5-109">Další informace o povolení kontrolovaného prostředí naleznete v tématu [checked](checked.md) .</span><span class="sxs-lookup"><span data-stu-id="2d4b5-109">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="2d4b5-110">Vzhledem k tomu, že kontrola přetečení trvá, použití nekontrolovaného kódu v situacích, kdy nehrozí nebezpečí přetečení, může zvýšit výkon.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="2d4b5-111">Pokud je ale možnost přetečení, měla by se použít kontrolované prostředí.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-111">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="2d4b5-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d4b5-112">Example</span></span>

<span data-ttu-id="2d4b5-113">Tento příklad ukazuje, jak použít klíčové slovo `unchecked`.</span><span class="sxs-lookup"><span data-stu-id="2d4b5-113">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="2d4b5-114">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d4b5-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="2d4b5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d4b5-115">See also</span></span>

- [<span data-ttu-id="2d4b5-116">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="2d4b5-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2d4b5-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2d4b5-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2d4b5-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d4b5-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2d4b5-119">Zaškrtnuto a nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="2d4b5-119">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="2d4b5-120">checked</span><span class="sxs-lookup"><span data-stu-id="2d4b5-120">checked</span></span>](checked.md)
