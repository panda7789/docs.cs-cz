---
title: příkaz return - odkaz jazyka C#
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713128"
---
# <a name="return-c-reference"></a><span data-ttu-id="7524d-102">return (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7524d-102">return (C# Reference)</span></span>

<span data-ttu-id="7524d-103">Příkaz `return` ukončí provádění metody, ve kterém se zobrazí a vrátí ovládací prvek volající metody.</span><span class="sxs-lookup"><span data-stu-id="7524d-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="7524d-104">Může také vrátit volitelnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7524d-104">It can also return an optional value.</span></span> <span data-ttu-id="7524d-105">Pokud je metoda `void` typu, `return` příkaz lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="7524d-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="7524d-106">Pokud návrat ový příkaz `try` je `finally` uvnitř bloku, blok, pokud existuje, bude proveden před ovládací prvek vrátí do volající metody.</span><span class="sxs-lookup"><span data-stu-id="7524d-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="7524d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="7524d-107">Example</span></span>

 <span data-ttu-id="7524d-108">V následujícím příkladu `CalculateArea()` vrátí metoda `area` místní `double` proměnnou jako hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7524d-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="7524d-109">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7524d-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7524d-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="7524d-110">See also</span></span>

- [<span data-ttu-id="7524d-111">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7524d-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7524d-112">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7524d-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7524d-113">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="7524d-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7524d-114">return – příkaz</span><span class="sxs-lookup"><span data-stu-id="7524d-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
