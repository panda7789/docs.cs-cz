---
title: New – modifikátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 675369936b9f90620b03365104255a622855fa9f
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401789"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="73853-102">New – modifikátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="73853-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="73853-103">Při použití jako modifikátoru deklarace `new` – klíčové slovo explicitně skryje člena, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="73853-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="73853-104">Při skrytí zděděného člena, odvozená verze člena nahradí verzi základní třídy.</span><span class="sxs-lookup"><span data-stu-id="73853-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="73853-105">Ačkoli můžete skrýt členy, bez použití `new` modifikátor, zobrazí se upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="73853-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="73853-106">Pokud používáte `new` pro explicitní skrytí člena, potlačí toto upozornění.</span><span class="sxs-lookup"><span data-stu-id="73853-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="73853-107">Můžete také použít `new` – klíčové slovo do [vytvořit instanci typu](../operators/new-operator.md) nebo stejně jako [omezení obecného typu](../keywords/new-constraint.md).</span><span class="sxs-lookup"><span data-stu-id="73853-107">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](../keywords/new-constraint.md).</span></span>

<span data-ttu-id="73853-108">Chcete-li skrýt zděděného člena, deklarujte ho v odvozené třídě pomocí stejného názvu členu a upravte jej pomocí `new` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="73853-108">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="73853-109">Příklad:</span><span class="sxs-lookup"><span data-stu-id="73853-109">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="73853-110">V tomto příkladu `BaseC.Invoke` je skryt `DerivedC.Invoke`.</span><span class="sxs-lookup"><span data-stu-id="73853-110">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="73853-111">Pole `x` nemá vliv, protože není skryté podobným názvem.</span><span class="sxs-lookup"><span data-stu-id="73853-111">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="73853-112">Skrytí názvu prostřednictvím dědičnosti má jednu z následujících forem:</span><span class="sxs-lookup"><span data-stu-id="73853-112">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="73853-113">Obecně konstanta, pole, vlastnost nebo typ, který se používá ve třídě nebo struktuře skryje všechny členy základní třídy, které sdílejí její název.</span><span class="sxs-lookup"><span data-stu-id="73853-113">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="73853-114">Existují zvláštní případy.</span><span class="sxs-lookup"><span data-stu-id="73853-114">There are special cases.</span></span> <span data-ttu-id="73853-115">Například, pokud deklarujete novou položku s názvem `N` mít typ, který není nevyvolatelný a základní typ deklaruje `N` na metodu, nové pole neskryje základní deklaraci v syntaxi vyvolání.</span><span class="sxs-lookup"><span data-stu-id="73853-115">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="73853-116">Další informace najdete v tématu [člen vyhledávání](~/_csharplang/spec/expressions.md#member-lookup) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="73853-116">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="73853-117">Metody zavedené ve třídě nebo struktuře skryjí vlastnosti polí a typů, které sdílejí tento název v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="73853-117">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="73853-118">Skryje také všechny metody základní třídy, které mají stejnou signaturu.</span><span class="sxs-lookup"><span data-stu-id="73853-118">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="73853-119">Indexer zavedený ve třídě nebo struktuře skryje všechny základní třídy indexerů, které mají stejnou signaturu.</span><span class="sxs-lookup"><span data-stu-id="73853-119">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="73853-120">Jedná se o chybu, chcete-li použít `new` a [přepsat](override.md) na stejný člen, protože dva Modifikátory mají vzájemně vylučují význam.</span><span class="sxs-lookup"><span data-stu-id="73853-120">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="73853-121">`new` Modifikátor vytvoří nový člen se stejným názvem a způsobí, že původní člen bude skrytý.</span><span class="sxs-lookup"><span data-stu-id="73853-121">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="73853-122">`override` Modifikátor rozšiřuje implementaci pro zděděného člena.</span><span class="sxs-lookup"><span data-stu-id="73853-122">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="73853-123">Použití `new` modifikátor v deklaraci, která neskryje zděděného člena, vygeneruje upozornění.</span><span class="sxs-lookup"><span data-stu-id="73853-123">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="73853-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="73853-124">Example</span></span>

<span data-ttu-id="73853-125">V tomto příkladu základní třída `BaseC`a odvozená třída `DerivedC`, použijte stejný název pole `x`, který skryje hodnotu zděděného pole.</span><span class="sxs-lookup"><span data-stu-id="73853-125">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="73853-126">Tento příklad ukazuje použití `new` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="73853-126">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="73853-127">Také ukazuje, jak přistupovat ke skrytým členům základní třídy pomocí jejich plně kvalifikovaných názvů.</span><span class="sxs-lookup"><span data-stu-id="73853-127">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="73853-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="73853-128">Example</span></span>

<span data-ttu-id="73853-129">V tomto příkladu vnořené třídy skryjí třídu, která má stejný název v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="73853-129">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="73853-130">Tento příklad ukazuje, jak používat `new` modifikátor k vyloučení upozornění a jak přistupovat ke skrytým členům třídy pomocí jejich plně kvalifikovaných názvů.</span><span class="sxs-lookup"><span data-stu-id="73853-130">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="73853-131">Pokud odeberete `new` modifikátor, program bude stále kompilace a spuštění, ale zobrazí se následující upozornění:</span><span class="sxs-lookup"><span data-stu-id="73853-131">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="73853-132">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="73853-132">C# language specification</span></span>

<span data-ttu-id="73853-133">Další informace najdete v tématu [new – modifikátor](~/_csharplang/spec/classes.md#the-new-modifier) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="73853-133">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="73853-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73853-134">See also</span></span>

- [<span data-ttu-id="73853-135">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="73853-135">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="73853-136">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="73853-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="73853-137">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="73853-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="73853-138">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="73853-138">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="73853-139">Správa verzí pomocí klíčových slov override a new</span><span class="sxs-lookup"><span data-stu-id="73853-139">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="73853-140">Znalost, kdy použít klíčová slova override a new</span><span class="sxs-lookup"><span data-stu-id="73853-140">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
