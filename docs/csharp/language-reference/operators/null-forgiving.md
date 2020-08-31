---
description: '! (null-striktní) – operátor – reference jazyka C#'
title: '! (null-striktní) – operátor – reference jazyka C#'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 7ae35f4741e1ef377b73a15066dddd243c94d8fe
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118218"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="b178a-105">!</span><span class="sxs-lookup"><span data-stu-id="b178a-105">!</span></span> <span data-ttu-id="b178a-106">(null-striktní) – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b178a-106">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="b178a-107">K dispozici v C# 8,0 a novějším, unární `!` operátor přípony je operátor null-striktní.</span><span class="sxs-lookup"><span data-stu-id="b178a-107">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="b178a-108">V povoleném [kontextu anotace s možnou hodnotou](../../nullable-references.md#nullable-annotation-context)null použijte operátor null-striktní k deklaraci, že výraz `x` typu odkazu není `null` : `x!` .</span><span class="sxs-lookup"><span data-stu-id="b178a-108">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="b178a-109">Unární operátor prefix `!` je [logický operátor negace](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="b178a-109">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="b178a-110">Operátor null-striktní nemá žádný vliv na dobu běhu.</span><span class="sxs-lookup"><span data-stu-id="b178a-110">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="b178a-111">Ovlivňuje pouze analýzu statického toku kompilátoru změnou stavu null výrazu.</span><span class="sxs-lookup"><span data-stu-id="b178a-111">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="b178a-112">V době běhu se výraz `x!` vyhodnotí jako výsledek podkladového výrazu `x` .</span><span class="sxs-lookup"><span data-stu-id="b178a-112">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

> [!NOTE]
> <span data-ttu-id="b178a-113">V C# 8 operátor null-striktní ukončí seznam předchozích operací [s hodnotou null](member-access-operators.md#null-conditional-operators--and-) .</span><span class="sxs-lookup"><span data-stu-id="b178a-113">In C# 8, the null-forgiving operator terminates the list of preceding [null-conditional](member-access-operators.md#null-conditional-operators--and-) operations.</span></span> <span data-ttu-id="b178a-114">Například výraz `x?.y!.z` je analyzován jako `(x?.y)!.z` .</span><span class="sxs-lookup"><span data-stu-id="b178a-114">For example, the expression `x?.y!.z` is parsed as `(x?.y)!.z`.</span></span> <span data-ttu-id="b178a-115">Z důvodu této interpretace `z` je vyhodnocena i `x` v případě, že je `null` , což může vést k <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="b178a-115">Due to this interpretation, `z` is evaluated even if `x` is `null`, which may result in a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="b178a-116">Další informace o funkci typů odkazů s možnou hodnotou null naleznete v tématu [typy odkazů s možnou hodnotou null](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="b178a-116">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="b178a-117">Příklady</span><span class="sxs-lookup"><span data-stu-id="b178a-117">Examples</span></span>

<span data-ttu-id="b178a-118">Jedním z případů použití operátoru null-striktní je testování logiky ověřování argumentů.</span><span class="sxs-lookup"><span data-stu-id="b178a-118">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="b178a-119">Zvažte například následující třídu:</span><span class="sxs-lookup"><span data-stu-id="b178a-119">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/shared/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="b178a-120">Pomocí [testovacího rozhraní MSTest](../../../core/testing/unit-testing-with-mstest.md)můžete vytvořit následující test logiky ověřování v konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="b178a-120">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/shared/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="b178a-121">Bez operátoru null-striktní kompilátor vygeneruje následující upozornění pro předchozí kód: `Warning CS8625: Cannot convert null literal to non-nullable reference type` .</span><span class="sxs-lookup"><span data-stu-id="b178a-121">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="b178a-122">Pomocí operátoru null-striktní informujte kompilátor, že předávání `null` je očekáváno, a neměl by se mu upozornit.</span><span class="sxs-lookup"><span data-stu-id="b178a-122">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="b178a-123">Operátor null-striktní můžete použít také v případě, že jednoznačně víte, že výraz nemůže být, `null` ale kompilátor nespravuje pro rozpoznání.</span><span class="sxs-lookup"><span data-stu-id="b178a-123">You can also use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="b178a-124">V následujícím příkladu, pokud se `IsValid` Metoda vrátí `true` , její argument není `null` a můžete ho bezpečně odkázat:</span><span class="sxs-lookup"><span data-stu-id="b178a-124">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/shared/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="b178a-125">Bez operátoru null-striktní generuje kompilátor následující upozornění pro `p.Name` kód: `Warning CS8602: Dereference of a possibly null reference` .</span><span class="sxs-lookup"><span data-stu-id="b178a-125">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="b178a-126">Pokud můžete upravit `IsValid` metodu, můžete použít atribut [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) k informování kompilátoru, že argument `IsValid` metody nemůže být, `null` když metoda vrátí `true` :</span><span class="sxs-lookup"><span data-stu-id="b178a-126">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/shared/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="b178a-127">V předchozím příkladu nemusíte používat operátor null-striktní, protože kompilátor obsahuje dostatek informací, aby bylo možné zjistit, že `p` nemůže být `null` uvnitř `if` příkazu.</span><span class="sxs-lookup"><span data-stu-id="b178a-127">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="b178a-128">Další informace o atributech, které umožňují zadat další informace o stavu null proměnné, naleznete v tématu [upgrade rozhraní API s atributy pro definování očekávání null](../attributes/nullable-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="b178a-128">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../attributes/nullable-analysis.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b178a-129">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b178a-129">C# language specification</span></span>

<span data-ttu-id="b178a-130">Další informace naleznete v části [operátor null-striktní](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) v [konceptu specifikace typů odkazů s možnou hodnotou null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="b178a-130">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b178a-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="b178a-131">See also</span></span>

- [<span data-ttu-id="b178a-132">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="b178a-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b178a-133">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="b178a-133">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="b178a-134">Kurz: návrh s použitím typů odkazů s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="b178a-134">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
