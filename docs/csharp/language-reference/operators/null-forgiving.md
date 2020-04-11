---
title: '! (null-odpouštějící) operátor - C# odkaz'
ms.date: 10/11/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- null-forgiving operator [C#]
- '! operator [C#]'
ms.openlocfilehash: 658043f8d5e149064f6da328657b2ccef9b5da94
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121447"
---
# <a name="-null-forgiving-operator-c-reference"></a><span data-ttu-id="83bfa-103">!</span><span class="sxs-lookup"><span data-stu-id="83bfa-103">!</span></span> <span data-ttu-id="83bfa-104">(null-odpouštějící) operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="83bfa-104">(null-forgiving) operator (C# reference)</span></span>

<span data-ttu-id="83bfa-105">K dispozici v C# 8.0 a `!` novější unární přípona operátor je operátor null odpouštějící.</span><span class="sxs-lookup"><span data-stu-id="83bfa-105">Available in C# 8.0 and later, the unary postfix `!` operator is the null-forgiving operator.</span></span> <span data-ttu-id="83bfa-106">V povoleném [kontextu poznámky s možnou hodnotou null](../../nullable-references.md#nullable-annotation-context)použijete `x` operátor null-odpouštějící k prohlášení, že výraz typu odkazu není `null`: `x!`.</span><span class="sxs-lookup"><span data-stu-id="83bfa-106">In an enabled [nullable annotation context](../../nullable-references.md#nullable-annotation-context), you use the null-forgiving operator to declare that expression `x` of a reference type isn't `null`: `x!`.</span></span> <span data-ttu-id="83bfa-107">Operátor unární `!` předpony je [logický operátor negace](boolean-logical-operators.md#logical-negation-operator-).</span><span class="sxs-lookup"><span data-stu-id="83bfa-107">The unary prefix `!` operator is the [logical negation operator](boolean-logical-operators.md#logical-negation-operator-).</span></span>

<span data-ttu-id="83bfa-108">Operátor null odpouštějící nemá žádný vliv v době běhu.</span><span class="sxs-lookup"><span data-stu-id="83bfa-108">The null-forgiving operator has no effect at run time.</span></span> <span data-ttu-id="83bfa-109">Ovlivňuje pouze analýzu statického toku kompilátoru změnou stavu null výrazu.</span><span class="sxs-lookup"><span data-stu-id="83bfa-109">It only affects the compiler's static flow analysis by changing the null state of the expression.</span></span> <span data-ttu-id="83bfa-110">Za běhu výraz `x!` vyhodnotí výsledek základní `x`výraz .</span><span class="sxs-lookup"><span data-stu-id="83bfa-110">At run time, expression `x!` evaluates to the result of the underlying expression `x`.</span></span>

<span data-ttu-id="83bfa-111">Další informace o funkci typů odkazů s možnou hodnotou null naleznete v [tématu Nullable reference types](../builtin-types/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="83bfa-111">For more information about the nullable reference types feature, see [Nullable reference types](../builtin-types/nullable-reference-types.md).</span></span>

## <a name="examples"></a><span data-ttu-id="83bfa-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="83bfa-112">Examples</span></span>

<span data-ttu-id="83bfa-113">Jedním z případů použití operátoru null odpouštějící je testování logiky ověřování argument.</span><span class="sxs-lookup"><span data-stu-id="83bfa-113">One of the use cases of the null-forgiving operator is in testing the argument validation logic.</span></span> <span data-ttu-id="83bfa-114">Zvažte například následující třídu:</span><span class="sxs-lookup"><span data-stu-id="83bfa-114">For example, consider the following class:</span></span>

[!code-csharp[Person class](snippets/NullForgivingOperator.cs#PersonClass)]

<span data-ttu-id="83bfa-115">Pomocí [testovacího rámce MSTest](../../../core/testing/unit-testing-with-mstest.md)můžete vytvořit následující test pro logiku ověření v konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="83bfa-115">Using the [MSTest test framework](../../../core/testing/unit-testing-with-mstest.md), you can create the following test for the validation logic in the constructor:</span></span>

[!code-csharp[Person test](snippets/NullForgivingOperator.cs#TestPerson)]

<span data-ttu-id="83bfa-116">Bez operátoru null-forgiving kompilátor vygeneruje následující upozornění `Warning CS8625: Cannot convert null literal to non-nullable reference type`pro předchozí kód: .</span><span class="sxs-lookup"><span data-stu-id="83bfa-116">Without the null-forgiving operator, the compiler generates the following warning for the preceding code: `Warning CS8625: Cannot convert null literal to non-nullable reference type`.</span></span> <span data-ttu-id="83bfa-117">Pomocí operátoru null odpouštějící, informujete kompilátor, že předávání `null` je očekáváno a nemělo by být upozorněno.</span><span class="sxs-lookup"><span data-stu-id="83bfa-117">By using the null-forgiving operator, you inform the compiler that passing `null` is expected and shouldn't be warned about.</span></span>

<span data-ttu-id="83bfa-118">Můžete také použít operátor null odpouštějící, když určitě `null` víte, že výraz nemůže být, ale kompilátor nepodaří rozpoznat, že.</span><span class="sxs-lookup"><span data-stu-id="83bfa-118">You also can use the null-forgiving operator when you definitely know that an expression cannot be `null` but the compiler doesn't manage to recognize that.</span></span> <span data-ttu-id="83bfa-119">V následujícím příkladu, `IsValid` pokud `true`metoda vrátí `null` , její argument není a můžete bezpečně dereference:</span><span class="sxs-lookup"><span data-stu-id="83bfa-119">In the following example, if the `IsValid` method returns `true`, its argument is not `null` and you can safely dereference it:</span></span>

[!code-csharp[Use null-forgiving operator](snippets/NullForgivingOperator.cs#UseNullForgiving)]

<span data-ttu-id="83bfa-120">Bez operátoru null-forgiving kompilátor generuje následující `p.Name` upozornění `Warning CS8602: Dereference of a possibly null reference`pro kód: .</span><span class="sxs-lookup"><span data-stu-id="83bfa-120">Without the null-forgiving operator, the compiler generates the following warning for the `p.Name` code: `Warning CS8602: Dereference of a possibly null reference`.</span></span>

<span data-ttu-id="83bfa-121">Pokud můžete změnit `IsValid` metodu, můžete použít [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) atribut informovat kompilátor, že argument `IsValid` metody nemůže být, `null` když metoda vrátí `true`:</span><span class="sxs-lookup"><span data-stu-id="83bfa-121">If you can modify the `IsValid` method, you can use the [NotNullWhen](xref:System.Diagnostics.CodeAnalysis.NotNullWhenAttribute) attribute to inform the compiler that an argument of the `IsValid` method cannot be `null` when the method returns `true`:</span></span>

[!code-csharp[Use an attribute](snippets/NullForgivingOperator.cs#UseAttribute)]

<span data-ttu-id="83bfa-122">V předchozím příkladu není nutné použít operátor null odpouštějící, protože kompilátor má `p` dostatek `null` informací `if` k zjistíní, že nemůže být uvnitř příkazu.</span><span class="sxs-lookup"><span data-stu-id="83bfa-122">In the preceding example, you don't need to use the null-forgiving operator because the compiler has enough information to find out that `p` cannot be `null` inside the `if` statement.</span></span> <span data-ttu-id="83bfa-123">Další informace o atributech, které umožňují poskytnout další informace o stavu null proměnné, naleznete v [tématu Upgrade api s atributy definovat očekávání null](../../nullable-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="83bfa-123">For more information about the attributes that allow you to provide additional information about the null state of a variable, see [Upgrade APIs with attributes to define null expectations](../../nullable-attributes.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="83bfa-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="83bfa-124">C# language specification</span></span>

<span data-ttu-id="83bfa-125">Další informace naleznete [v části operátor odpouštějící nula](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) v [návrhu specifikace referenčních typů s možnou hodnotou null](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span><span class="sxs-lookup"><span data-stu-id="83bfa-125">For more information, see [The null-forgiving operator](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md#the-null-forgiving-operator) section of the [draft of the nullable reference types specification](~/_csharplang/proposals/csharp-8.0/nullable-reference-types-specification.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="83bfa-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="83bfa-126">See also</span></span>

- [<span data-ttu-id="83bfa-127">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="83bfa-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="83bfa-128">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="83bfa-128">C# operators</span></span>](index.md)
- [<span data-ttu-id="83bfa-129">Kurz: Návrh s typy odkazů s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="83bfa-129">Tutorial: Design with nullable reference types</span></span>](../../tutorials/nullable-reference-types.md)
