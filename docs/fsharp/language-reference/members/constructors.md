---
title: Konstruktory
description: Naučte se definovat a používat konstruktory v F# pro vytváření a inicializaci objektů tříd a struktur.
ms.date: 05/16/2016
ms.openlocfilehash: 6769ec7fc6768090d8ae68e21946a58829b6eea0
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736852"
---
# <a name="constructors"></a><span data-ttu-id="7ecf1-103">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="7ecf1-103">Constructors</span></span>

<span data-ttu-id="7ecf1-104">Tento článek popisuje, jak definovat a používat konstruktory pro vytváření a inicializaci objektů tříd a struktur.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-104">This article describes how to define and use constructors to create and initialize class and structure objects.</span></span>

## <a name="construction-of-class-objects"></a><span data-ttu-id="7ecf1-105">Konstrukce objektů třídy</span><span class="sxs-lookup"><span data-stu-id="7ecf1-105">Construction of class objects</span></span>

<span data-ttu-id="7ecf1-106">Objekty typů třídy mají konstruktory.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-106">Objects of class types have constructors.</span></span> <span data-ttu-id="7ecf1-107">Existují dva druhy konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-107">There are two kinds of constructors.</span></span> <span data-ttu-id="7ecf1-108">Jedna je primární konstruktor, jehož parametry jsou uvedeny v závorkách hned za názvem typu.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="7ecf1-109">Pomocí klíčového slova `new` určíte jiné volitelné Další konstruktory.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="7ecf1-110">Jakékoli takové další konstruktory musí volat primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="7ecf1-111">Primární konstruktor obsahuje vazby `let` a `do`, které se zobrazí na začátku definice třídy.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="7ecf1-112">Vazba `let` deklaruje soukromá pole a metody třídy; vazba `do` spustí kód.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="7ecf1-113">Další informace o vazbách `let` v konstruktorech třídy naleznete v tématu [vazby `let` v třídách](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="7ecf1-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="7ecf1-114">Další informace o vazbách `do` v konstruktorech naleznete v tématu [bindings `do` in Classes](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="7ecf1-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="7ecf1-115">Bez ohledu na to, zda je konstruktor, který chcete volat, primární konstruktor nebo další konstruktor, lze objekty vytvořit pomocí výrazu `new` s volitelným klíčovým slovem `new`, nebo bez něj.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="7ecf1-116">Vaše objekty můžete inicializovat společně s argumenty konstruktoru, buď výpisem argumentů v pořadí a oddělenými čárkami a uzavřeny v závorkách, nebo pomocí pojmenovaných argumentů a hodnot v závorkách.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="7ecf1-117">Můžete také nastavit vlastnosti objektu během konstrukce objektu pomocí názvů vlastností a přiřazením hodnot stejným způsobem jako argumenty pojmenovaných konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="7ecf1-118">Následující kód ilustruje třídu, která má konstruktor a různé způsoby vytváření objektů:</span><span class="sxs-lookup"><span data-stu-id="7ecf1-118">The following code illustrates a class that has a constructor and various ways of creating objects:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="7ecf1-119">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="7ecf1-119">The output is as follows:</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="7ecf1-120">Konstrukce struktur</span><span class="sxs-lookup"><span data-stu-id="7ecf1-120">Construction of structures</span></span>

<span data-ttu-id="7ecf1-121">Struktury dodržují všechna pravidla tříd.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="7ecf1-122">Proto můžete mít primární konstruktor a můžete poskytnout další konstruktory pomocí `new`.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="7ecf1-123">Nicméně existuje jeden důležitý rozdíl mezi strukturami a třídami: struktury mohou mít konstruktor bez parametrů (tj. jeden bez argumentů) i v případě, že není definován žádný primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-123">However, there is one important difference between structures and classes: structures can have a parameterless constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="7ecf1-124">Konstruktor bez parametrů inicializuje všechna pole na výchozí hodnotu pro tento typ, obvykle nula nebo ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-124">The parameterless constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="7ecf1-125">Všechny konstruktory, které definujete pro struktury, musí mít alespoň jeden argument, aby nedošlo ke konfliktu s konstruktory bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the parameterless constructor.</span></span>

<span data-ttu-id="7ecf1-126">Struktury také často obsahují pole, která jsou vytvořena pomocí klíčového slova `val`; třídy mohou mít také tato pole.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="7ecf1-127">Struktury a třídy, které mají pole definovaná pomocí klíčového slova `val`, lze také inicializovat v dalších konstruktorech pomocí výrazů záznamů, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="7ecf1-128">Další informace naleznete v tématu [explicitní pole: klíčové slovo `val`](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="7ecf1-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>

## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="7ecf1-129">Provádění vedlejších účinků v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="7ecf1-129">Executing side effects in constructors</span></span>

<span data-ttu-id="7ecf1-130">Primární konstruktor ve třídě může spouštět kód v rámci vazby `do`.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="7ecf1-131">Co když ale budete muset spustit kód v dalším konstruktoru bez vazby `do`?</span><span class="sxs-lookup"><span data-stu-id="7ecf1-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="7ecf1-132">K tomu použijte klíčové slovo `then`.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="7ecf1-133">Vedlejší účinky primárního konstruktoru se pořád spouštějí.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="7ecf1-134">Výstup je proto následující:</span><span class="sxs-lookup"><span data-stu-id="7ecf1-134">Therefore, the output is as follows:</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="7ecf1-135">Osobní identifikátory v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="7ecf1-135">Self identifiers in constructors</span></span>

<span data-ttu-id="7ecf1-136">V jiných členech zadáte název pro aktuální objekt v definici každého člena.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-136">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="7ecf1-137">Identifikátor sami můžete také umístit na první řádek definice třídy pomocí klíčového slova `as` hned po parametrech konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-137">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="7ecf1-138">Následující příklad ilustruje tuto syntaxi.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-138">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="7ecf1-139">V dalších konstruktorech můžete také definovat identifikátor držitele vložením klauzule `as` přímo za parametry konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-139">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="7ecf1-140">Následující příklad ilustruje tuto syntaxi:</span><span class="sxs-lookup"><span data-stu-id="7ecf1-140">The following example illustrates this syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="7ecf1-141">K problémům může dojít při pokusu o použití objektu před jeho úplným definováním.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-141">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="7ecf1-142">Proto použití identifikátoru autoidentifier může způsobit, že kompilátor vygeneruje upozornění a vloží další kontroly, aby před inicializací objektu nebyly k dispozici členové objektu.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-142">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="7ecf1-143">V vazbách `do` primárního konstruktoru nebo po klíčovém slově `then` v dalších konstruktorech byste měli použít pouze samotný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-143">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="7ecf1-144">Název automatického identifikátoru nemusí být `this`.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-144">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="7ecf1-145">Může to být libovolný platný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-145">It can be any valid identifier.</span></span>

## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="7ecf1-146">Přiřazení hodnot k vlastnostem při inicializaci</span><span class="sxs-lookup"><span data-stu-id="7ecf1-146">Assigning values to properties at initialization</span></span>

<span data-ttu-id="7ecf1-147">Můžete přiřadit hodnoty k vlastnostem objektu třídy v inicializačním kódu připojením seznamu přiřazení formuláře `property = value` do seznamu argumentů pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-147">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="7ecf1-148">To je znázorněno v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="7ecf1-148">This is shown in the following code example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="7ecf1-149">Následující verze předchozího kódu ilustruje kombinaci běžných argumentů, volitelných argumentů a nastavení vlastností ve volání jednoho konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="7ecf1-149">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a><span data-ttu-id="7ecf1-150">Konstruktory v zděděné třídě</span><span class="sxs-lookup"><span data-stu-id="7ecf1-150">Constructors in inherited class</span></span>

<span data-ttu-id="7ecf1-151">Při dědění ze základní třídy, která má konstruktor, je nutné zadat argumenty klauzule Inherit.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-151">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="7ecf1-152">Další informace naleznete v tématu [konstruktory a dědičnost](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="7ecf1-152">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="7ecf1-153">Statické konstruktory nebo konstruktory typů</span><span class="sxs-lookup"><span data-stu-id="7ecf1-153">Static constructors or type constructors</span></span>

<span data-ttu-id="7ecf1-154">Kromě určení kódu pro vytváření objektů, statické vazby `let` a `do` mohou být vytvořeny v typech třídy, které jsou spouštěny před prvním použitím tohoto typu k provedení inicializace na úrovni typu.</span><span class="sxs-lookup"><span data-stu-id="7ecf1-154">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="7ecf1-155">Další informace naleznete v tématu [vazby `let` v třídách](let-bindings-in-classes.md) a [vazby `do` v třídách](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="7ecf1-155">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7ecf1-156">Další informace najdete v tématech</span><span class="sxs-lookup"><span data-stu-id="7ecf1-156">See also</span></span>

- [<span data-ttu-id="7ecf1-157">Pedagog</span><span class="sxs-lookup"><span data-stu-id="7ecf1-157">Members</span></span>](index.md)
