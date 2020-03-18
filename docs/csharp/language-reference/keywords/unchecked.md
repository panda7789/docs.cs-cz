---
title: nezaškrtnuté klíčové slovo – odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 6dad0dfd508fb390dd0a52d1b48d70b4c5725513
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712998"
---
# <a name="unchecked-c-reference"></a><span data-ttu-id="71f64-102">unchecked (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="71f64-102">unchecked (C# Reference)</span></span>

<span data-ttu-id="71f64-103">Klíčové `unchecked` slovo se používá k potlačení kontroly přetečení pro integrální typ aritmetické operace a převody.</span><span class="sxs-lookup"><span data-stu-id="71f64-103">The `unchecked` keyword is used to suppress overflow-checking for integral-type arithmetic operations and conversions.</span></span>

<span data-ttu-id="71f64-104">V nekontrolovaném kontextu, pokud výraz vytvoří hodnotu, která je mimo rozsah cílového typu, přetečení není označeno příznakem.</span><span class="sxs-lookup"><span data-stu-id="71f64-104">In an unchecked context, if an expression produces a value that is outside the range of the destination type, the overflow is not flagged.</span></span> <span data-ttu-id="71f64-105">Například protože výpočet v následujícím příkladu `unchecked` se provádí v bloku nebo výrazu, skutečnost, že výsledek je `int1` příliš velký pro celé číslo je ignorována a je přiřazena hodnota -2,147,483,639.</span><span class="sxs-lookup"><span data-stu-id="71f64-105">For example, because the calculation in the following example is performed in an `unchecked` block or expression, the fact that the result is too large for an integer is ignored, and `int1` is assigned the value -2,147,483,639.</span></span>

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

<span data-ttu-id="71f64-106">Pokud `unchecked` je prostředí odebráno, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="71f64-106">If the `unchecked` environment is removed, a compilation error occurs.</span></span> <span data-ttu-id="71f64-107">Přetečení lze zjistit v době kompilace, protože všechny podmínky výrazu jsou konstanty.</span><span class="sxs-lookup"><span data-stu-id="71f64-107">The overflow can be detected at compile time because all the terms of the expression are constants.</span></span>

<span data-ttu-id="71f64-108">Výrazy, které obsahují nekonstantní termíny, jsou ve výchozím nastavení nezaškrtnuté v době kompilace a běhu.</span><span class="sxs-lookup"><span data-stu-id="71f64-108">Expressions that contain non-constant terms are unchecked by default at compile time and run time.</span></span> <span data-ttu-id="71f64-109">Informace o povolení kontrolovaného prostředí naleznete [v tématu Zaškrtnuto](checked.md) je.</span><span class="sxs-lookup"><span data-stu-id="71f64-109">See [checked](checked.md) for information about enabling a checked environment.</span></span>

<span data-ttu-id="71f64-110">Vzhledem k tomu, že kontrola přetečení vyžaduje čas, použití nekontrolovaného kódu v situacích, kdy neexistuje žádné nebezpečí přetečení může zlepšit výkon.</span><span class="sxs-lookup"><span data-stu-id="71f64-110">Because checking for overflow takes time, the use of unchecked code in situations where there is no danger of overflow might improve performance.</span></span> <span data-ttu-id="71f64-111">Pokud je však možné přetečení, je třeba použít kontrolované prostředí.</span><span class="sxs-lookup"><span data-stu-id="71f64-111">However, if overflow is a possibility, a checked environment should be used.</span></span>

## <a name="example"></a><span data-ttu-id="71f64-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="71f64-112">Example</span></span>

<span data-ttu-id="71f64-113">Tato ukázka ukazuje, `unchecked` jak používat klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="71f64-113">This sample shows how to use the `unchecked` keyword.</span></span>

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a><span data-ttu-id="71f64-114">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="71f64-114">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="71f64-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="71f64-115">See also</span></span>

- [<span data-ttu-id="71f64-116">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="71f64-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="71f64-117">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="71f64-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="71f64-118">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="71f64-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="71f64-119">Checked a Unchecked</span><span class="sxs-lookup"><span data-stu-id="71f64-119">Checked and Unchecked</span></span>](checked-and-unchecked.md)
- [<span data-ttu-id="71f64-120">Kontrolovány</span><span class="sxs-lookup"><span data-stu-id="71f64-120">checked</span></span>](checked.md)
