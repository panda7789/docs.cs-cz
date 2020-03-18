---
title: nový modifikátor - Odkaz jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 6c4fedd469efb79f91780dff26da89b586de2d1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713334"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="cd781-102">nový modifikátor (Odkaz C#</span><span class="sxs-lookup"><span data-stu-id="cd781-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="cd781-103">Při použití jako modifikátor deklarace `new` klíčové slovo explicitně skryje člen, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="cd781-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="cd781-104">Když skryjete zděděný člen, odvozená verze člena nahradí verzi základní třídy.</span><span class="sxs-lookup"><span data-stu-id="cd781-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="cd781-105">I když můžete skrýt `new` členy bez použití modifikátoru, dostanete upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="cd781-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="cd781-106">Pokud slouží `new` k explicitnímu skrytí člena, potlačí toto upozornění.</span><span class="sxs-lookup"><span data-stu-id="cd781-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="cd781-107">Klíčové slovo můžete také použít k vytvoření instance typu nebo jako [omezení obecného typu](./new-constraint.md). [create an instance of a type](../operators/new-operator.md) `new`</span><span class="sxs-lookup"><span data-stu-id="cd781-107">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](./new-constraint.md).</span></span>

<span data-ttu-id="cd781-108">Chcete-li skrýt zděděný člen, deklarujte jej v odvozené `new` třídě pomocí stejného názvu člena a upravte jej pomocí klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="cd781-108">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="cd781-109">Například:</span><span class="sxs-lookup"><span data-stu-id="cd781-109">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="cd781-110">V tomto `BaseC.Invoke` příkladu `DerivedC.Invoke`je skrytý .</span><span class="sxs-lookup"><span data-stu-id="cd781-110">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="cd781-111">Pole `x` není ovlivněno, protože není skryto podobným názvem.</span><span class="sxs-lookup"><span data-stu-id="cd781-111">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="cd781-112">Název skrytí prostřednictvím dědičnosti má jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="cd781-112">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="cd781-113">Obecně konstanta, pole, vlastnost nebo typ, který je zaveden ve třídě nebo struktuře, skryje všechny členy základní třídy, kteří sdílejí jeho název.</span><span class="sxs-lookup"><span data-stu-id="cd781-113">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="cd781-114">Existují zvláštní případy.</span><span class="sxs-lookup"><span data-stu-id="cd781-114">There are special cases.</span></span> <span data-ttu-id="cd781-115">Pokud například deklarujete `N` nové pole s názvem typu, který není neodvolatelný, a základní typ deklaruje `N` jako metodu, nové pole neskryje základní deklaraci v syntaxi vyvolání.</span><span class="sxs-lookup"><span data-stu-id="cd781-115">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="cd781-116">Další informace naleznete v části [Vyhledávání členů](~/_csharplang/spec/expressions.md#member-lookup) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="cd781-116">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="cd781-117">Metoda zavedená ve třídě nebo struktuře skryje vlastnosti, pole a typy, které sdílejí tento název v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="cd781-117">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="cd781-118">Také skryje všechny metody základní třídy, které mají stejný podpis.</span><span class="sxs-lookup"><span data-stu-id="cd781-118">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="cd781-119">Indexer zavedený ve třídě nebo struktuře skryje všechny indexery základní třídy, které mají stejný podpis.</span><span class="sxs-lookup"><span data-stu-id="cd781-119">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="cd781-120">Je chyba použít oba `new` a [přepsat](override.md) na stejný člen, protože dva modifikátory mají vzájemně se vylučující významy.</span><span class="sxs-lookup"><span data-stu-id="cd781-120">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="cd781-121">Modifikátor `new` vytvoří nový člen se stejným názvem a způsobí, že původní člen se stane skrytým.</span><span class="sxs-lookup"><span data-stu-id="cd781-121">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="cd781-122">Modifikátor `override` rozšiřuje implementaci pro zděděný člen.</span><span class="sxs-lookup"><span data-stu-id="cd781-122">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="cd781-123">Použití `new` modifikátor v deklaraci, která neskrývá zděděný člen generuje upozornění.</span><span class="sxs-lookup"><span data-stu-id="cd781-123">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="cd781-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd781-124">Example</span></span>

<span data-ttu-id="cd781-125">V tomto příkladu základní `BaseC`třída , a `DerivedC`odvozené třídy `x`, použijte stejný název pole , který skryje hodnotu zděděného pole.</span><span class="sxs-lookup"><span data-stu-id="cd781-125">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="cd781-126">Příklad ukazuje použití modifikátoru. `new`</span><span class="sxs-lookup"><span data-stu-id="cd781-126">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="cd781-127">Také ukazuje, jak získat přístup ke skrytým členům základní třídy pomocí jejich plně kvalifikovaných názvů.</span><span class="sxs-lookup"><span data-stu-id="cd781-127">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="cd781-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd781-128">Example</span></span>

<span data-ttu-id="cd781-129">V tomto příkladu vnořená třída skryje třídu, která má stejný název v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="cd781-129">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="cd781-130">Příklad ukazuje, jak pomocí `new` modifikátoru eliminovat varovné zprávy a jak získat přístup ke skrytým členům třídy pomocí jejich plně kvalifikované názvy.</span><span class="sxs-lookup"><span data-stu-id="cd781-130">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="cd781-131">Pokud `new` modifikátor odeberete, program se bude stále zkompilovat a spustit, ale zobrazí se následující upozornění:</span><span class="sxs-lookup"><span data-stu-id="cd781-131">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="cd781-132">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cd781-132">C# language specification</span></span>

<span data-ttu-id="cd781-133">Další informace naleznete [v části Nový modifikátor](~/_csharplang/spec/classes.md#the-new-modifier) specifikace jazyka [C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="cd781-133">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cd781-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd781-134">See also</span></span>

- [<span data-ttu-id="cd781-135">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cd781-135">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="cd781-136">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cd781-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cd781-137">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="cd781-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cd781-138">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="cd781-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="cd781-139">Správa verzí pomocí klíčových slov override a new</span><span class="sxs-lookup"><span data-stu-id="cd781-139">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="cd781-140">Znalost, kdy použít klíčová slova override a new</span><span class="sxs-lookup"><span data-stu-id="cd781-140">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
