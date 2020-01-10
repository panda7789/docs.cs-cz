---
title: příkaz return – C# odkaz
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: 116bad7a1f9f61311d287c575b52547d63c9e1c0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713128"
---
# <a name="return-c-reference"></a><span data-ttu-id="0d3fd-102">return (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0d3fd-102">return (C# Reference)</span></span>

<span data-ttu-id="0d3fd-103">Příkaz `return` ukončí provádění metody, ve které se vyskytuje, a vrátí řízení volající metodě.</span><span class="sxs-lookup"><span data-stu-id="0d3fd-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="0d3fd-104">Může také vracet volitelnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0d3fd-104">It can also return an optional value.</span></span> <span data-ttu-id="0d3fd-105">Pokud je metoda typu `void`, příkaz `return` lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="0d3fd-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="0d3fd-106">Pokud je příkaz return uvnitř bloku `try`, `finally` blok, pokud existuje, se spustí před tím, než se ovládací prvek vrátí volající metodě.</span><span class="sxs-lookup"><span data-stu-id="0d3fd-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="0d3fd-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d3fd-107">Example</span></span>

 <span data-ttu-id="0d3fd-108">V následujícím příkladu metoda `CalculateArea()` vrátí místní proměnnou `area` jako `double`ovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0d3fd-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="0d3fd-109">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0d3fd-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="0d3fd-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d3fd-110">See also</span></span>

- [<span data-ttu-id="0d3fd-111">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="0d3fd-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0d3fd-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0d3fd-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0d3fd-113">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0d3fd-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0d3fd-114">return – příkaz</span><span class="sxs-lookup"><span data-stu-id="0d3fd-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
