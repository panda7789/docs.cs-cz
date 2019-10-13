---
title: '! (null – striktní) – odkaz C# na operátora'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: cf941e5e3fa3fc6313ef8b2ff5c176aec68c1e6b
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291723"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="5e193-103">!</span><span class="sxs-lookup"><span data-stu-id="5e193-103">!</span></span> <span data-ttu-id="5e193-104">(null – striktní) – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="5e193-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="5e193-105">K dispozici v C# 8,0 a novějším, unární přípona @no__t operátor-1 je operátor null-striktní.</span><span class="sxs-lookup"><span data-stu-id="5e193-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="5e193-106">V povoleném [kontextu anotace s možnou hodnotou](../../nullable-references.md#nullable-annotation-context)null použijte operátor null-striktní k deklaraci, že výraz `x` typu odkazu není null: `x!`.</span><span class="sxs-lookup"><span data-stu-id="5e193-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't null: `x!`.</span></span> <span data-ttu-id="5e193-107">Unární předpona `!` operátor je [logický operátor negace](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="5e193-107">The unary prefix `!` operator is a [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="5e193-108">Operátor null-striktní nemá žádný vliv na dobu běhu.</span><span class="sxs-lookup"><span data-stu-id="5e193-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="5e193-109">Ovlivňuje pouze analýzu statického toku kompilátoru změnou stavu null výrazu.</span><span class="sxs-lookup"><span data-stu-id="5e193-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="5e193-110">V době běhu je výraz `x!` vyhodnocen jako výsledek podkladového výrazu `x`.</span><span class="sxs-lookup"><span data-stu-id="5e193-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="5e193-111">Další informace o funkci typů odkazů s možnou hodnotou null naleznete v tématu [typy odkazů s možnou hodnotou null](../../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="5e193-111">For more information about the nullable reference types feature, see [Nullable reference types](../../nullable-references.md).</span></span>

## <a name="examples"></a><span data-ttu-id="5e193-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="5e193-112">Examples</span></span>

<span data-ttu-id="5e193-113">Jedním z případů použití operátoru null-striktní je testování logiky ověřování argumentů.</span><span class="sxs-lookup"><span data-stu-id="5e193-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="5e193-114">Zvažte například následující třídu:</span><span class="sxs-lookup"><span data-stu-id="5e193-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="5e193-115">Pomocí [testovacího rozhraní MSTest](../../../core/testing/unit-testing-with-mstest.md)můžete vytvořit následující test logiky ověřování v konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="5e193-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="5e193-116">Bez operátoru null-striktní kompilátor vygeneruje následující upozornění pro předchozí kód: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span><span class="sxs-lookup"><span data-stu-id="5e193-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="5e193-117">Při použití operátoru null-striktní můžete kompilátoru sdělit, že se očekává předávání `null` a neměla by se jim upozornit.</span><span class="sxs-lookup"><span data-stu-id="5e193-117">With the use of the null-forgiving operator, you let the compiler know that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="5e193-118">Operátor null-striktní můžete použít také v případě, že jednoznačně víte, že výraz nemůže být `null`, ale kompilátor nespravuje pro rozpoznání.</span><span class="sxs-lookup"><span data-stu-id="5e193-118">You also can use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="5e193-119">V následujícím příkladu, pokud metoda `IsValid` vrátí `true`, jeho argument není `null` a můžete ho bezpečně odkázat:</span><span class="sxs-lookup"><span data-stu-id="5e193-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="5e193-120">Bez operátoru null-striktní kompilátor vygeneruje následující upozornění pro kód `p.Name`: `Warning CS8602: Dereference of a possibly null reference.`.</span><span class="sxs-lookup"><span data-stu-id="5e193-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference.`.</span></span>

<span data-ttu-id="5e193-121">Pokud můžete upravit metodu `IsValid`, můžete použít atribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) , aby kompilátor věděl, že argument metody `IsValid` nemůže být `null`, pokud metoda vrátí `true`:</span><span class="sxs-lookup"><span data-stu-id="5e193-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to let the compiler know that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](~/samples/csharp/language-reference/operators/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="5e193-122">V předchozím příkladu nemusíte používat operátor null-striktní, protože kompilátor má dostatek informací, aby zjistil, že `p` nelze v příkazu `if` `null`.</span><span class="sxs-lookup"><span data-stu-id="5e193-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="5e193-123">Další informace o atributech, které umožňují zadat další informace o stavu null proměnné, naleznete v tématu [upgrade rozhraní API s atributy pro definování očekávání null](../../nullable-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="5e193-123">For more information about the attributes that allow you to specify additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5e193-124">Další informace najdete v tématech</span><span class="sxs-lookup"><span data-stu-id="5e193-124">See also</span></span>

- [<span data-ttu-id="5e193-125">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="5e193-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5e193-126">C#logické</span><span class="sxs-lookup"><span data-stu-id="5e193-126">C# operators</span></span>](index.md)
- [<span data-ttu-id="5e193-127">Kurz: návrh s použitím typů odkazů s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="5e193-127">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
