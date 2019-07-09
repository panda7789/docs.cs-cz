---
title: Return – příkaz - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- return_CSharpKeyword
- return
helpviewer_keywords:
- return statement [C#]
- return keyword [C#]
ms.assetid: 6da6e152-5b58-4448-8f3f-470dd0617ecd
ms.openlocfilehash: a845ce257bf7f0cf0e64d6815b2278f6cec946e7
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661618"
---
# <a name="return-c-reference"></a><span data-ttu-id="12a05-102">return (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="12a05-102">return (C# Reference)</span></span>

<span data-ttu-id="12a05-103">`return` Příkaz ukončí provádění metody, ve kterém se zobrazí a vrátí řízení volající metodě.</span><span class="sxs-lookup"><span data-stu-id="12a05-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="12a05-104">Také může vrátit nepovinnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="12a05-104">It can also return an optional value.</span></span> <span data-ttu-id="12a05-105">Pokud je metoda `void` typ, `return` příkaz lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="12a05-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="12a05-106">Pokud je příkaz return uvnitř `try` bloku `finally` bloku, pokud existuje, budou spuštěny před ovládací prvek vrátí volajícímu metody.</span><span class="sxs-lookup"><span data-stu-id="12a05-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="12a05-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="12a05-107">Example</span></span>

 <span data-ttu-id="12a05-108">V následujícím příkladu metoda `CalculateArea()` vrátí lokální proměnná `area` jako `double` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="12a05-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a `double` value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="12a05-109">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="12a05-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="12a05-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12a05-110">See also</span></span>

- [<span data-ttu-id="12a05-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="12a05-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="12a05-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="12a05-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="12a05-113">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="12a05-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="12a05-114">return – příkaz</span><span class="sxs-lookup"><span data-stu-id="12a05-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
