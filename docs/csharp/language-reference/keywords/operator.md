---
title: Operator – klíčové slovo - C# odkaz
ms.custom: seodec18
description: Zjistěte, jak přetížení předdefinovaný operátor C#
ms.date: 08/27/2018
f1_keywords:
- operator_CSharpKeyword
- operator
helpviewer_keywords:
- operator keyword [C#]
ms.assetid: 59218cce-e90e-42f6-a6bb-30300981b86a
ms.openlocfilehash: cdc052da4457a59cc66848780e944ccf203acf39
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235584"
---
# <a name="operator-c-reference"></a><span data-ttu-id="7b24b-103">operator (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7b24b-103">operator (C# Reference)</span></span>

<span data-ttu-id="7b24b-104">Použití `operator` – klíčové slovo přetížení předdefinovaný operátor nebo k poskytování uživatelsky definovaný převod v deklaraci třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="7b24b-104">Use the `operator` keyword to overload a built-in operator or to provide a user-defined conversion in a class or struct declaration.</span></span>

<span data-ttu-id="7b24b-105">Přetížení operátoru na vlastní třídy nebo struktury, vytvoříte v odpovídající typ deklarace operátoru.</span><span class="sxs-lookup"><span data-stu-id="7b24b-105">To overload an operator on a custom class or struct, you create an operator declaration in the corresponding type.</span></span> <span data-ttu-id="7b24b-106">Deklarace operátor, který přetěžuje předdefinovaný operátor C# musí splňovat následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="7b24b-106">The operator declaration that overloads a built-in C# operator must satisfy the following rules:</span></span>

- <span data-ttu-id="7b24b-107">To zahrnuje i `public` a `static` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="7b24b-107">It includes both a `public` and a `static` modifier.</span></span>
- <span data-ttu-id="7b24b-108">Zahrnuje `operator X` kde `X` je název nebo symbol přetížení operátoru.</span><span class="sxs-lookup"><span data-stu-id="7b24b-108">It includes `operator X` where `X` is the name or symbol of the operator being overloaded.</span></span>
- <span data-ttu-id="7b24b-109">Unární operátory mít jeden parametr a binární operátory mají dva parametry.</span><span class="sxs-lookup"><span data-stu-id="7b24b-109">Unary operators have one parameter, and binary operators have two parameters.</span></span> <span data-ttu-id="7b24b-110">V každém případě alespoň jeden parametr musí být stejného typu jako třída nebo struktura, která deklaruje operátor.</span><span class="sxs-lookup"><span data-stu-id="7b24b-110">In each case, at least one parameter must be the same type as the class or struct that declares the operator.</span></span>

<span data-ttu-id="7b24b-111">Informace o tom, jak definovat operátory převodu, najdete v článku [explicitní](explicit.md) a [implicitní](implicit.md) články – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="7b24b-111">For information about how to define conversion operators, see the [explicit](explicit.md) and [implicit](implicit.md) keyword articles.</span></span>

<span data-ttu-id="7b24b-112">Přehled, které mohou být přetíženy operátory jazyka C# najdete v tématu [přetížitelné operátory](../../programming-guide/statements-expressions-operators/overloadable-operators.md) článku.</span><span class="sxs-lookup"><span data-stu-id="7b24b-112">For an overview of the C# operators that can be overloaded, see the [Overloadable operators](../../programming-guide/statements-expressions-operators/overloadable-operators.md) article.</span></span>

## <a name="example"></a><span data-ttu-id="7b24b-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="7b24b-113">Example</span></span>

<span data-ttu-id="7b24b-114">Následující příklad definuje `Fraction` typ, který představuje desetinná čísla.</span><span class="sxs-lookup"><span data-stu-id="7b24b-114">The following example defines a `Fraction` type that represents fractional numbers.</span></span> <span data-ttu-id="7b24b-115">Přetěžuje `+` a `*` operátory provádět desetinné sčítání a násobení a také poskytuje operátor převodu které převádí `Fraction` typ, který `double` typu.</span><span class="sxs-lookup"><span data-stu-id="7b24b-115">It overloads the `+` and `*` operators to perform fractional addition and multiplication, and also provides a conversion operator that converts a `Fraction` type to a `double` type.</span></span>

[!code-csharp[csrefKeywordsConversion#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="7b24b-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7b24b-116">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7b24b-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b24b-117">See also</span></span>

- [<span data-ttu-id="7b24b-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7b24b-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7b24b-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7b24b-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7b24b-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7b24b-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="7b24b-121">implicit</span><span class="sxs-lookup"><span data-stu-id="7b24b-121">implicit</span></span>](implicit.md)
- [<span data-ttu-id="7b24b-122">explicit</span><span class="sxs-lookup"><span data-stu-id="7b24b-122">explicit</span></span>](explicit.md)
- [<span data-ttu-id="7b24b-123">Přetížitelné operátory</span><span class="sxs-lookup"><span data-stu-id="7b24b-123">Overloadable operators</span></span>](../../programming-guide/statements-expressions-operators/overloadable-operators.md)
- [<span data-ttu-id="7b24b-124">Postupy: Implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="7b24b-124">How to: Implement User-Defined Conversions Between Structs</span></span>](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
