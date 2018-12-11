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
ms.openlocfilehash: 058dc1d51099196559bee4ec2b96dc883e813f93
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236554"
---
# <a name="return-c-reference"></a><span data-ttu-id="902d2-102">return (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="902d2-102">return (C# Reference)</span></span>

<span data-ttu-id="902d2-103">`return` Příkaz ukončí provádění metody, ve kterém se zobrazí a vrátí řízení volající metodě.</span><span class="sxs-lookup"><span data-stu-id="902d2-103">The `return` statement terminates execution of the method in which it appears and returns control to the calling method.</span></span> <span data-ttu-id="902d2-104">Také může vrátit nepovinnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="902d2-104">It can also return an optional value.</span></span> <span data-ttu-id="902d2-105">Pokud je metoda `void` typ, `return` příkaz lze vynechat.</span><span class="sxs-lookup"><span data-stu-id="902d2-105">If the method is a `void` type, the `return` statement can be omitted.</span></span>

 <span data-ttu-id="902d2-106">Pokud je příkaz return uvnitř `try` bloku `finally` bloku, pokud existuje, budou spuštěny před ovládací prvek vrátí volajícímu metody.</span><span class="sxs-lookup"><span data-stu-id="902d2-106">If the return statement is inside a `try` block, the `finally` block, if one exists, will be executed before control returns to the calling method.</span></span>

## <a name="example"></a><span data-ttu-id="902d2-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="902d2-107">Example</span></span>

 <span data-ttu-id="902d2-108">V následujícím příkladu metoda `CalculateArea()` vrátí lokální proměnná `area` jako [double](double.md) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="902d2-108">In the following example, the method `CalculateArea()` returns the local variable `area` as a [double](double.md) value.</span></span>

[!code-csharp[csrefKeywordsJump#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsJump/CS/csrefKeywordsJump.cs#6)]  

## <a name="c-language-specification"></a><span data-ttu-id="902d2-109">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="902d2-109">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="902d2-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="902d2-110">See also</span></span>

- [<span data-ttu-id="902d2-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="902d2-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="902d2-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="902d2-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="902d2-113">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="902d2-113">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="902d2-114">return – příkaz</span><span class="sxs-lookup"><span data-stu-id="902d2-114">return Statement</span></span>](/cpp/cpp/return-statement-cpp)
- [<span data-ttu-id="902d2-115">Jump – příkazy</span><span class="sxs-lookup"><span data-stu-id="902d2-115">Jump Statements</span></span>](jump-statements.md)
