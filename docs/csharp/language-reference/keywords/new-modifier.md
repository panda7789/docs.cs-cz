---
title: nový modifikátor – C# referenční informace
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 082cd37eca6b5de1251d73a5483665f8a98b0132
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422671"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="9a1fa-102">New – modifikátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="9a1fa-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="9a1fa-103">Při použití jako modifikátor deklarace klíčová slova `new` explicitně skrývá člen, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="9a1fa-104">Když skryjete zděděného člena, odvozená verze člena nahradí verzi základní třídy.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="9a1fa-105">I když můžete členy skrýt bez použití modifikátoru `new`, zobrazí se upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="9a1fa-106">Použijete-li `new` k explicitnímu skrytí člena, potlačí toto upozornění.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="9a1fa-107">Můžete také použít klíčové slovo `new` pro [vytvoření instance typu](../operators/new-operator.md) nebo jako [omezení obecného typu](./new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="9a1fa-107">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](./new-constraint.md).</span></span>

<span data-ttu-id="9a1fa-108">Chcete-li skrýt zděděného člena, deklarujte ho v odvozené třídě pomocí stejného názvu člena a upravte jej pomocí klíčového slova `new`.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-108">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="9a1fa-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="9a1fa-109">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="9a1fa-110">V tomto příkladu je `BaseC.Invoke` skrytý pomocí `DerivedC.Invoke`.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-110">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="9a1fa-111">Pole `x` není ovlivněno, protože není skryté podobným názvem.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-111">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="9a1fa-112">Název skrývání prostřednictvím dědičnosti má jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="9a1fa-112">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="9a1fa-113">Obecně konstanta, pole, vlastnost nebo typ, který je představen ve třídě nebo struktuře, skrývá všechny členy základní třídy, které sdílejí svůj název.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-113">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="9a1fa-114">Existují zvláštní případy.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-114">There are special cases.</span></span> <span data-ttu-id="9a1fa-115">Například pokud deklarujete nové pole s názvem `N`, že má typ, který není nevyvolatelný, a základní typ deklaruje `N` jako metodu, nové pole neskryje základní deklaraci v syntaxi vyvolání.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-115">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="9a1fa-116">Další informace naleznete v oddílu [vyhledávání členů](~/_csharplang/spec/expressions.md#member-lookup) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9a1fa-116">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="9a1fa-117">Metoda zavedená ve třídě nebo struktuře skrývá vlastnosti, pole a typy, které sdílejí tento název v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-117">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="9a1fa-118">Také skryje všechny metody základní třídy, které mají stejnou signaturu.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-118">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="9a1fa-119">Indexer zavedený ve třídě nebo struktuře skrývá všechny základní třídy indexerů, které mají stejnou signaturu.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-119">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="9a1fa-120">Použití `new` i [přepsání](override.md) u stejného člena je chybné, protože dva modifikátory mají vzájemně se vylučující významy.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-120">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="9a1fa-121">Modifikátor `new` vytvoří nového člena se stejným názvem a způsobí, že původní člen bude skrytý.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-121">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="9a1fa-122">Modifikátor `override` rozšiřuje implementaci zděděného člena.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-122">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="9a1fa-123">Použití modifikátoru `new` v deklaraci, která neskrývá zděděný člen, vygeneruje upozornění.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-123">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="9a1fa-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a1fa-124">Example</span></span>

<span data-ttu-id="9a1fa-125">V tomto příkladu základní třída, `BaseC`a odvozená třída `DerivedC`, používají stejný název pole `x`, který skrývá hodnotu zděděného pole.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-125">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="9a1fa-126">Příklad ukazuje použití modifikátoru `new`.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-126">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="9a1fa-127">Také ukazuje, jak přistupovat ke skrytým členům základní třídy pomocí jejich plně kvalifikovaných názvů.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-127">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="9a1fa-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="9a1fa-128">Example</span></span>

<span data-ttu-id="9a1fa-129">V tomto příkladu vnořená Třída skrývá třídu, která má stejný název v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-129">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="9a1fa-130">Příklad ukazuje, jak použít modifikátor `new` k eliminaci zprávy upozornění a o tom, jak přistupovat ke skrytým členům třídy pomocí jejich plně kvalifikovaných názvů.</span><span class="sxs-lookup"><span data-stu-id="9a1fa-130">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="9a1fa-131">Pokud odeberete modifikátor `new`, program se stále zkompiluje a spustí, ale zobrazí se toto upozornění:</span><span class="sxs-lookup"><span data-stu-id="9a1fa-131">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="9a1fa-132">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9a1fa-132">C# language specification</span></span>

<span data-ttu-id="9a1fa-133">Další informace naleznete v části [nový modifikátor](~/_csharplang/spec/classes.md#the-new-modifier) v [ C# tématu Specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9a1fa-133">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9a1fa-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a1fa-134">See also</span></span>

- [<span data-ttu-id="9a1fa-135">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="9a1fa-135">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="9a1fa-136">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9a1fa-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9a1fa-137">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9a1fa-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9a1fa-138">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="9a1fa-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="9a1fa-139">Správa verzí pomocí klíčových slov override a new</span><span class="sxs-lookup"><span data-stu-id="9a1fa-139">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="9a1fa-140">Znalost, kdy použít klíčová slova override a new</span><span class="sxs-lookup"><span data-stu-id="9a1fa-140">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
