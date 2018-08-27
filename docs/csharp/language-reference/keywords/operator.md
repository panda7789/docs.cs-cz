---
title: klíčové slovo pro operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: c3bfada235993670bf158fe9803a09707b2b3251
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42929869"
---
# <a name="operator-c-reference"></a><span data-ttu-id="97b28-102">operator (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="97b28-102">operator (C# Reference)</span></span>

<span data-ttu-id="97b28-103">Použití `operator` – klíčové slovo přetížení předdefinovaný operátor nebo k poskytování uživatelsky definovaný převod v deklaraci třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="97b28-103">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>

## <a name="example"></a><span data-ttu-id="97b28-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="97b28-104">Example</span></span>

<span data-ttu-id="97b28-105">Níže je velmi zjednodušený třídu desetinná čísla.</span><span class="sxs-lookup"><span data-stu-id="97b28-105">The following is a very simplified class for fractional numbers.</span></span> <span data-ttu-id="97b28-106">Přetěžuje `+` a `*` operátory provádět desetinné sčítání a násobení a také poskytuje operátor převodu které převádí `Fraction` typ, který `double` typu.</span><span class="sxs-lookup"><span data-stu-id="97b28-106">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="97b28-107">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="97b28-107">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="97b28-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="97b28-108">See also</span></span>

- [<span data-ttu-id="97b28-109">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="97b28-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="97b28-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="97b28-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="97b28-111">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="97b28-111">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="97b28-112">implicit</span><span class="sxs-lookup"><span data-stu-id="97b28-112">implicit</span></span>](implicit.md)
- [<span data-ttu-id="97b28-113">explicit</span><span class="sxs-lookup"><span data-stu-id="97b28-113">explicit</span></span>](explicit.md)
- [<span data-ttu-id="97b28-114">Postupy: Implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="97b28-114">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
