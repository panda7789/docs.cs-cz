---
title: nový modifikátor – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 529d77b0a66a8a3cedfe7a400af0fb34dd653322
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795167"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="d1526-102">New – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d1526-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="d1526-103">Při použití jako modifikátoru deklarace `new` klíčová slova explicitně skrývá člen, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="d1526-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="d1526-104">Když skryjete zděděného člena, odvozená verze člena nahradí verzi základní třídy.</span><span class="sxs-lookup"><span data-stu-id="d1526-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="d1526-105">I když můžete členy skrýt bez použití `new` modifikátoru, zobrazí se upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="d1526-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="d1526-106">Pokud použijete `new` příkaz k explicitnímu skrytí člena, potlačí se toto upozornění.</span><span class="sxs-lookup"><span data-stu-id="d1526-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="d1526-107">Klíčové slovo lze použít také `new` k [vytvoření instance typu](../operators/new-operator.md) nebo jako [omezení obecného typu](./new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="d1526-107">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](./new-constraint.md).</span></span>

<span data-ttu-id="d1526-108">Chcete-li skrýt zděděného člena, deklarujte ho v odvozené třídě pomocí stejného názvu člena a upravte jej pomocí `new` klíčového slova.</span><span class="sxs-lookup"><span data-stu-id="d1526-108">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="d1526-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d1526-109">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="d1526-110">V tomto příkladu `BaseC.Invoke` je skrytý nástrojem `DerivedC.Invoke` .</span><span class="sxs-lookup"><span data-stu-id="d1526-110">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="d1526-111">Pole není `x` ovlivněno, protože není skryto podobným názvem.</span><span class="sxs-lookup"><span data-stu-id="d1526-111">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="d1526-112">Název skrývání prostřednictvím dědičnosti má jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="d1526-112">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="d1526-113">Obecně konstanta, pole, vlastnost nebo typ, který je představen ve třídě nebo struktuře, skrývá všechny členy základní třídy, které sdílejí svůj název.</span><span class="sxs-lookup"><span data-stu-id="d1526-113">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="d1526-114">Existují zvláštní případy.</span><span class="sxs-lookup"><span data-stu-id="d1526-114">There are special cases.</span></span> <span data-ttu-id="d1526-115">Například pokud deklarujete nové pole s názvem `N` , které má typ, který není nevyvolatelný, a základní typ deklaruje jako `N` metodu, nové pole neskryje základní deklaraci v syntaxi vyvolání.</span><span class="sxs-lookup"><span data-stu-id="d1526-115">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="d1526-116">Další informace naleznete v oddílu [vyhledávání členů](~/_csharplang/spec/expressions.md#member-lookup) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d1526-116">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="d1526-117">Metoda zavedená ve třídě nebo struktuře skrývá vlastnosti, pole a typy, které sdílejí tento název v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="d1526-117">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="d1526-118">Také skryje všechny metody základní třídy, které mají stejnou signaturu.</span><span class="sxs-lookup"><span data-stu-id="d1526-118">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="d1526-119">Indexer zavedený ve třídě nebo struktuře skrývá všechny základní třídy indexerů, které mají stejnou signaturu.</span><span class="sxs-lookup"><span data-stu-id="d1526-119">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="d1526-120">Při použití i `new` [přepsání](override.md) u stejného člena se jedná o chybu, protože dva modifikátory mají vzájemně exkluzivní význam.</span><span class="sxs-lookup"><span data-stu-id="d1526-120">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="d1526-121">`new`Modifikátor vytvoří nového člena se stejným názvem a způsobí, že původní člen bude skrytý.</span><span class="sxs-lookup"><span data-stu-id="d1526-121">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="d1526-122">`override`Modifikátor rozšiřuje implementaci pro zděděného člena.</span><span class="sxs-lookup"><span data-stu-id="d1526-122">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="d1526-123">Použití `new` modifikátoru v deklaraci, která neskrývá zděděný člen, vygeneruje upozornění.</span><span class="sxs-lookup"><span data-stu-id="d1526-123">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="d1526-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1526-124">Example</span></span>

<span data-ttu-id="d1526-125">V tomto příkladu základní třída, `BaseC` a odvozená třída, `DerivedC` používá stejný název pole `x` , který skrývá hodnotu zděděného pole.</span><span class="sxs-lookup"><span data-stu-id="d1526-125">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="d1526-126">Příklad demonstruje použití `new` modifikátoru.</span><span class="sxs-lookup"><span data-stu-id="d1526-126">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="d1526-127">Také ukazuje, jak přistupovat ke skrytým členům základní třídy pomocí jejich plně kvalifikovaných názvů.</span><span class="sxs-lookup"><span data-stu-id="d1526-127">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="d1526-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="d1526-128">Example</span></span>

<span data-ttu-id="d1526-129">V tomto příkladu vnořená Třída skrývá třídu, která má stejný název v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="d1526-129">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="d1526-130">Tento příklad ukazuje, jak použít `new` Modifikátor k odstranění zprávy upozornění a o tom, jak přistupovat ke skrytým členům třídy pomocí jejich plně kvalifikovaných názvů.</span><span class="sxs-lookup"><span data-stu-id="d1526-130">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="d1526-131">Pokud tento modifikátor odeberete `new` , program se stále zkompiluje a spustí, ale zobrazí se toto upozornění:</span><span class="sxs-lookup"><span data-stu-id="d1526-131">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="d1526-132">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d1526-132">C# language specification</span></span>

<span data-ttu-id="d1526-133">Další informace naleznete v části [nový modifikátor](~/_csharplang/spec/classes.md#the-new-modifier) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="d1526-133">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1526-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="d1526-134">See also</span></span>

- [<span data-ttu-id="d1526-135">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d1526-135">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d1526-136">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="d1526-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d1526-137">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d1526-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d1526-138">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="d1526-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="d1526-139">Správa verzí pomocí klíčových slov override a new</span><span class="sxs-lookup"><span data-stu-id="d1526-139">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="d1526-140">Znalost, kdy použít klíčová slova override a new</span><span class="sxs-lookup"><span data-stu-id="d1526-140">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
