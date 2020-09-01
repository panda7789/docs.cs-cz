---
description: nezaškrtnuté klíčové slovo – Reference jazyka C#
title: nezaškrtnuté klíčové slovo – Reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: bb66639e3657b247b9ebcad1594daf1f57a5c76b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141982"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="a7e74-103">unchecked (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a7e74-103">unchecked (C# Reference)</span></span>

<span data-ttu-id="a7e74-104">`unchecked`Klíčové slovo slouží k potlačení kontroly přetečení pro aritmetické operace a převody integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="a7e74-104">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="a7e74-105">V nekontrolovaném kontextu, pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu, přetečení není označeno příznakem.</span><span class="sxs-lookup"><span data-stu-id="a7e74-105">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="a7e74-106">Například vzhledem k tomu, že výpočet v následujícím příkladu je proveden v `unchecked` bloku nebo výrazu, je fakt, že výsledek je příliš velký pro celé číslo, ignorován a `int1` je přiřazena hodnota-2 147 483 639.</span><span class="sxs-lookup"><span data-stu-id="a7e74-106">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="a7e74-107">Pokud `unchecked` je prostředí odebráno, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="a7e74-107">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="a7e74-108">Přetečení lze zjistit v době kompilace, protože všechny výrazy výrazu jsou konstanty.</span><span class="sxs-lookup"><span data-stu-id="a7e74-108">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="a7e74-109">Výrazy, které obsahují nekonstantní podmínky, jsou ve výchozím nastavení v době kompilace a v době spuštění nezaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="a7e74-109">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="a7e74-110">Další informace o povolení kontrolovaného prostředí naleznete v tématu [checked](checked.md) .</span><span class="sxs-lookup"><span data-stu-id="a7e74-110">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="a7e74-111">Vzhledem k tomu, že kontrola přetečení trvá, použití nekontrolovaného kódu v situacích, kdy nehrozí nebezpečí přetečení, může zvýšit výkon.</span><span class="sxs-lookup"><span data-stu-id="a7e74-111">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="a7e74-112">Pokud je ale možnost přetečení, měla by se použít kontrolované prostředí.</span><span class="sxs-lookup"><span data-stu-id="a7e74-112">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="a7e74-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7e74-113">Example</span></span>

<span data-ttu-id="a7e74-114">Tato ukázka ukazuje, jak použít `unchecked` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="a7e74-114">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="a7e74-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a7e74-115">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a7e74-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7e74-116">See also</span></span>

- [<span data-ttu-id="a7e74-117">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a7e74-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a7e74-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a7e74-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a7e74-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a7e74-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a7e74-120">Checked a Unchecked</span><span class="sxs-lookup"><span data-stu-id="a7e74-120">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="a7e74-121">kontrolovaný</span><span class="sxs-lookup"><span data-stu-id="a7e74-121">checked</span></span>](checked.md)
