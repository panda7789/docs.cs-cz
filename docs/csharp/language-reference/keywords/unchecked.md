---
title: nezaškrtnuté klíčové slovo C# – odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: c31f1243b1394bfe826b02c14c73faf402640849
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608412"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="5e5a2-102">unchecked (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5e5a2-102">unchecked (C# Reference)</span></span>

<span data-ttu-id="5e5a2-103">`unchecked` Klíčové slovo slouží k potlačení kontroly přetečení pro aritmetické operace a převody integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="5e5a2-104">V nekontrolovaném kontextu, pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu, přetečení není označeno příznakem.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="5e5a2-105">Například vzhledem k tomu, že výpočet v následujícím příkladu je proveden v `unchecked` bloku nebo výrazu, je fakt, že výsledek je příliš velký pro celé číslo, ignorován a `int1` je přiřazena hodnota-2 147 483 639.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="5e5a2-106">Pokud je `unchecked` prostředí odebráno, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="5e5a2-107">Přetečení lze zjistit v době kompilace, protože všechny výrazy výrazu jsou konstanty.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="5e5a2-108">Výrazy, které obsahují nekonstantní podmínky, jsou ve výchozím nastavení v době kompilace a v době spuštění nezaškrtnuté.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="5e5a2-109">Další informace o povolení kontrolovaného prostředí naleznete v tématu [checked](checked.md) .</span><span class="sxs-lookup"><span data-stu-id="5e5a2-109">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="5e5a2-110">Vzhledem k tomu, že kontrola přetečení trvá, použití nekontrolovaného kódu v situacích, kdy nehrozí nebezpečí přetečení, může zvýšit výkon.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="5e5a2-111">Pokud je ale možnost přetečení, měla by se použít kontrolované prostředí.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-111">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="5e5a2-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e5a2-112">Example</span></span>

<span data-ttu-id="5e5a2-113">Tato ukázka ukazuje, jak použít `unchecked` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="5e5a2-113">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="5e5a2-114">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5e5a2-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="5e5a2-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e5a2-115">See also</span></span>

- [<span data-ttu-id="5e5a2-116">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="5e5a2-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5e5a2-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5e5a2-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5e5a2-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5e5a2-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5e5a2-119">Zaškrtnuto a nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="5e5a2-119">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="5e5a2-120">checked</span><span class="sxs-lookup"><span data-stu-id="5e5a2-120">checked</span></span>](checked.md)
