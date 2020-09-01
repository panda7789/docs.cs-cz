---
description: Return – příkaz – reference jazyka C#
title: Return – příkaz – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 486db846304c0972942ff58f3d5b276083681abe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136995"
---
# <a name="return-c-reference"></a><span data-ttu-id="bc430-103">return (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bc430-103">return (C# Reference)</span></span>

<span data-ttu-id="bc430-104">`return`Příkaz ukončí provádění metody, ve které se vyskytuje, a vrátí řízení volající metodě.</span><span class="sxs-lookup"><span data-stu-id="bc430-104">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="bc430-105">Může také vracet volitelnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bc430-105">It can also return an optional value.</span></span> <span data-ttu-id="bc430-106">Pokud je metoda `void` typu, je `return` možné příkaz vynechat.</span><span class="sxs-lookup"><span data-stu-id="bc430-106">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="bc430-107">Pokud je příkaz return uvnitř bloku, `try` `finally` blok, pokud existuje, bude proveden před tím, než se ovládací prvek vrátí volající metodě.</span><span class="sxs-lookup"><span data-stu-id="bc430-107">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="bc430-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc430-108">Example</span></span>

 <span data-ttu-id="bc430-109">V následujícím příkladu metoda `CalculateArea()` vrátí místní proměnnou `area` jako `double` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bc430-109">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="bc430-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bc430-110">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="bc430-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc430-111">See also</span></span>

- [<span data-ttu-id="bc430-112">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bc430-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bc430-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="bc430-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bc430-114">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bc430-114">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="bc430-115">Return – příkaz</span><span class="sxs-lookup"><span data-stu-id="bc430-115">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
