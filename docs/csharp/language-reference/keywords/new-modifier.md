---
description: nový modifikátor – Referenční dokumentace jazyka C#
title: nový modifikátor – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 2da0a360868250169fb16380c80bf32c4b335d7a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139408"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="98842-103">New – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="98842-103">new modifier (C# Reference)</span></span>

<span data-ttu-id="98842-104">Při použití jako modifikátoru deklarace `new` klíčová slova explicitně skrývá člen, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="98842-104">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="98842-105">Když skryjete zděděného člena, odvozená verze člena nahradí verzi základní třídy.</span><span class="sxs-lookup"><span data-stu-id="98842-105">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="98842-106">I když můžete členy skrýt bez použití `new` modifikátoru, zobrazí se upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="98842-106">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="98842-107">Pokud použijete `new` příkaz k explicitnímu skrytí člena, potlačí se toto upozornění.</span><span class="sxs-lookup"><span data-stu-id="98842-107">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="98842-108">Klíčové slovo lze použít také `new` k [vytvoření instance typu](../operators/new-operator.md) nebo jako [omezení obecného typu](./new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="98842-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](./new-constraint.md).</span></span>

<span data-ttu-id="98842-109">Chcete-li skrýt zděděného člena, deklarujte ho v odvozené třídě pomocí stejného názvu člena a upravte jej pomocí `new` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="98842-109">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="98842-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="98842-110">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="98842-111">V tomto příkladu `BaseC.Invoke` je skrytý nástrojem `DerivedC.Invoke` .</span><span class="sxs-lookup"><span data-stu-id="98842-111">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="98842-112">Pole není `x` ovlivněno, protože není skryto podobným názvem.</span><span class="sxs-lookup"><span data-stu-id="98842-112">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="98842-113">Název skrývání prostřednictvím dědičnosti má jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="98842-113">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="98842-114">Obecně konstanta, pole, vlastnost nebo typ, který je představen ve třídě nebo struktuře, skrývá všechny členy základní třídy, které sdílejí svůj název.</span><span class="sxs-lookup"><span data-stu-id="98842-114">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="98842-115">Existují zvláštní případy.</span><span class="sxs-lookup"><span data-stu-id="98842-115">There are special cases.</span></span> <span data-ttu-id="98842-116">Například pokud deklarujete nové pole s názvem `N` , které má typ, který není nevyvolatelný, a základní typ deklaruje jako `N` metodu, nové pole neskryje základní deklaraci v syntaxi vyvolání.</span><span class="sxs-lookup"><span data-stu-id="98842-116">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="98842-117">Další informace naleznete v oddílu [vyhledávání členů](~/_csharplang/spec/expressions.md#member-lookup) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="98842-117">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="98842-118">Metoda zavedená ve třídě nebo struktuře skrývá vlastnosti, pole a typy, které sdílejí tento název v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="98842-118">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="98842-119">Také skryje všechny metody základní třídy, které mají stejnou signaturu.</span><span class="sxs-lookup"><span data-stu-id="98842-119">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="98842-120">Indexer zavedený ve třídě nebo struktuře skrývá všechny základní třídy indexerů, které mají stejnou signaturu.</span><span class="sxs-lookup"><span data-stu-id="98842-120">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="98842-121">Při použití i `new` [přepsání](override.md) u stejného člena se jedná o chybu, protože dva modifikátory mají vzájemně exkluzivní význam.</span><span class="sxs-lookup"><span data-stu-id="98842-121">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="98842-122">`new`Modifikátor vytvoří nového člena se stejným názvem a způsobí, že původní člen bude skrytý.</span><span class="sxs-lookup"><span data-stu-id="98842-122">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="98842-123">`override`Modifikátor rozšiřuje implementaci pro zděděného člena.</span><span class="sxs-lookup"><span data-stu-id="98842-123">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="98842-124">Použití `new` modifikátoru v deklaraci, která neskrývá zděděný člen, vygeneruje upozornění.</span><span class="sxs-lookup"><span data-stu-id="98842-124">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="98842-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="98842-125">Example</span></span>

<span data-ttu-id="98842-126">V tomto příkladu základní třída, `BaseC` a odvozená třída, `DerivedC` používá stejný název pole `x` , který skrývá hodnotu zděděného pole.</span><span class="sxs-lookup"><span data-stu-id="98842-126">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="98842-127">Příklad demonstruje použití `new` modifikátoru.</span><span class="sxs-lookup"><span data-stu-id="98842-127">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="98842-128">Také ukazuje, jak přistupovat ke skrytým členům základní třídy pomocí jejich plně kvalifikovaných názvů.</span><span class="sxs-lookup"><span data-stu-id="98842-128">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="98842-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="98842-129">Example</span></span>

<span data-ttu-id="98842-130">V tomto příkladu vnořená Třída skrývá třídu, která má stejný název v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="98842-130">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="98842-131">Tento příklad ukazuje, jak použít `new` Modifikátor k odstranění zprávy upozornění a o tom, jak přistupovat ke skrytým členům třídy pomocí jejich plně kvalifikovaných názvů.</span><span class="sxs-lookup"><span data-stu-id="98842-131">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="98842-132">Pokud tento modifikátor odeberete `new` , program se stále zkompiluje a spustí, ale zobrazí se toto upozornění:</span><span class="sxs-lookup"><span data-stu-id="98842-132">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="98842-133">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="98842-133">C# language specification</span></span>

<span data-ttu-id="98842-134">Další informace naleznete v části [nový modifikátor](~/_csharplang/spec/classes.md#the-new-modifier) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="98842-134">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="98842-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="98842-135">See also</span></span>

- [<span data-ttu-id="98842-136">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="98842-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="98842-137">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="98842-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="98842-138">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="98842-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="98842-139">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="98842-139">Modifiers</span></span>](index.md)
- [<span data-ttu-id="98842-140">Správa verzí pomocí klíčových slov override a new</span><span class="sxs-lookup"><span data-stu-id="98842-140">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="98842-141">Znalost, kdy použít klíčová slova override a new</span><span class="sxs-lookup"><span data-stu-id="98842-141">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
