---
title: '! (null – striktní) – odkaz C# na operátora'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 21bbf8e1253641317750b911e052ee5ff0a0d063
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036162"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="1e2eb-103">!</span><span class="sxs-lookup"><span data-stu-id="1e2eb-103">!</span></span> <span data-ttu-id="1e2eb-104">(null – striktní) – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="1e2eb-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="1e2eb-105">K dispozici v C# 8,0 a novějším, unární přípona`!`operátor je operátor null-striktní.</span><span class="sxs-lookup"><span data-stu-id="1e2eb-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="1e2eb-106">V povoleném [kontextu anotace s možnou hodnotou null](../../nullable-references.md#nullable-annotation-context)použijte operátor null-striktní k deklaraci, že výraz `x` typu odkazu není `null`: `x!`.</span><span class="sxs-lookup"><span data-stu-id="1e2eb-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="1e2eb-107">Unární předpona `!` je operátor [logické negace](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="1e2eb-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="1e2eb-108">Operátor null-striktní nemá žádný vliv na dobu běhu.</span><span class="sxs-lookup"><span data-stu-id="1e2eb-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="1e2eb-109">Ovlivňuje pouze analýzu statického toku kompilátoru změnou stavu null výrazu.</span><span class="sxs-lookup"><span data-stu-id="1e2eb-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="1e2eb-110">V době běhu je výraz `x!` vyhodnocen jako výsledek podkladového výrazu `x`.</span><span class="sxs-lookup"><span data-stu-id="1e2eb-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="1e2eb-111">Další informace o funkci typů odkazů s možnou hodnotou null naleznete v tématu [typy odkazů s možnou hodnotou null](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="1e2eb-111">For more information about the nullable reference types feature, see [Nullable reference types](../../nullable-references.md).</span></span>

## <a name="examples"></a><span data-ttu-id="1e2eb-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="1e2eb-112">Examples</span></span>

<span data-ttu-id="1e2eb-113">Jedním z případů použití operátoru null-striktní je testování logiky ověřování argumentů.</span><span class="sxs-lookup"><span data-stu-id="1e2eb-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="1e2eb-114">Zvažte například následující třídu:</span><span class="sxs-lookup"><span data-stu-id="1e2eb-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="1e2eb-115">Pomocí [testovacího rozhraní MSTest](../../../core/testing/unit-testing-with-mstest.md)můžete vytvořit následující test logiky ověřování v konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="1e2eb-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="1e2eb-116">Bez operátoru null-striktní kompilátor vygeneruje následující upozornění pro předchozí kód: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span><span class="sxs-lookup"><span data-stu-id="1e2eb-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="1e2eb-117">Pomocí operátoru null-striktní informujte kompilátor, který předává `null` je očekáván a neměl by se mu upozornit.</span><span class="sxs-lookup"><span data-stu-id="1e2eb-117">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="1e2eb-118">Operátor null-striktní můžete použít také v případě, že jednoznačně víte, že výraz nemůže být `null`, ale kompilátor nespravuje pro rozpoznání.</span><span class="sxs-lookup"><span data-stu-id="1e2eb-118">You also can use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="1e2eb-119">V následujícím příkladu, pokud metoda `IsValid` vrátí `true`, jeho argument není `null` a můžete ho bezpečně odkázat:</span><span class="sxs-lookup"><span data-stu-id="1e2eb-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="1e2eb-120">Bez operátoru null-striktní kompilátor vygeneruje následující upozornění pro kód `p.Name`: `Warning CS8602: Dereference of a possibly null reference`.</span><span class="sxs-lookup"><span data-stu-id="1e2eb-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="1e2eb-121">Pokud můžete upravit metodu `IsValid`, můžete použít atribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) k informování kompilátoru, že argument metody `IsValid` nemůže být `null`, pokud metoda vrátí `true`:</span><span class="sxs-lookup"><span data-stu-id="1e2eb-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="1e2eb-122">V předchozím příkladu nemusíte používat operátor null-striktní, protože kompilátor má dostatek informací, aby zjistil, že `p` nelze v příkazu `if` `null`.</span><span class="sxs-lookup"><span data-stu-id="1e2eb-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="1e2eb-123">Další informace o atributech, které umožňují zadat další informace o stavu null proměnné, naleznete v tématu [upgrade rozhraní API s atributy pro definování očekávání null](../../nullable-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="1e2eb-123">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1e2eb-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1e2eb-124">C# language specification</span></span>

<span data-ttu-id="1e2eb-125">Další informace naleznete v části [operátor null-striktní](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) v [konceptu specifikace typů odkazů s možnou hodnotou null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="1e2eb-125">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1e2eb-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e2eb-126">See also</span></span>

- [<span data-ttu-id="1e2eb-127">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="1e2eb-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1e2eb-128">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1e2eb-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="1e2eb-129">Kurz: návrh s použitím typů odkazů s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="1e2eb-129">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
