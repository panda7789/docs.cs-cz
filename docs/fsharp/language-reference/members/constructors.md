---
title: Konstruktory
description: Naučte se definovat a používat konstruktory v F# pro vytváření a inicializaci objektů tříd a struktur.
ms.date: 05/16/2016
ms.openlocfilehash: c25fdcb95c2873eb69a94f30c87735e5c04d391b
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627592"
---
# <a name="constructors"></a><span data-ttu-id="14051-103">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="14051-103">Constructors</span></span>

<span data-ttu-id="14051-104">Toto téma popisuje, jak definovat a používat konstruktory pro vytváření a inicializaci objektů tříd a struktur.</span><span class="sxs-lookup"><span data-stu-id="14051-104">This topic describes how to define and use constructors to create and initialize class and structure objects.</span></span>

## <a name="construction-of-class-objects"></a><span data-ttu-id="14051-105">Konstrukce objektů třídy</span><span class="sxs-lookup"><span data-stu-id="14051-105">Construction of Class Objects</span></span>

<span data-ttu-id="14051-106">Objekty typů třídy mají konstruktory.</span><span class="sxs-lookup"><span data-stu-id="14051-106">Objects of class types have constructors.</span></span> <span data-ttu-id="14051-107">Existují dva druhy konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="14051-107">There are two kinds of constructors.</span></span> <span data-ttu-id="14051-108">Jedna je primární konstruktor, jehož parametry jsou uvedeny v závorkách hned za názvem typu.</span><span class="sxs-lookup"><span data-stu-id="14051-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="14051-109">Pomocí `new` klíčového slova určíte jiné volitelné Další konstruktory.</span><span class="sxs-lookup"><span data-stu-id="14051-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="14051-110">Jakékoli takové další konstruktory musí volat primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="14051-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="14051-111">Primární konstruktor obsahuje `let` a `do` vazby, které se zobrazí na začátku definice třídy.</span><span class="sxs-lookup"><span data-stu-id="14051-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="14051-112">Vazba deklaruje soukromá pole a metody třídy `do` ; vazba spustí kód. `let`</span><span class="sxs-lookup"><span data-stu-id="14051-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="14051-113">Další informace o `let` vazbách v konstruktorech třídy naleznete v tématu [ `let` Bindings in Classes](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="14051-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="14051-114">Další informace o `do` vazbách v konstruktorech naleznete v tématu [ `do` Bindings in Classes](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="14051-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="14051-115">Bez ohledu na to, zda je konstruktor, který chcete volat, primární konstruktor nebo další konstruktor, lze objekty vytvořit pomocí `new` výrazu s volitelným `new` klíčovým slovem nebo bez něj.</span><span class="sxs-lookup"><span data-stu-id="14051-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="14051-116">Vaše objekty můžete inicializovat společně s argumenty konstruktoru, buď výpisem argumentů v pořadí a oddělenými čárkami a uzavřeny v závorkách, nebo pomocí pojmenovaných argumentů a hodnot v závorkách.</span><span class="sxs-lookup"><span data-stu-id="14051-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="14051-117">Můžete také nastavit vlastnosti objektu během konstrukce objektu pomocí názvů vlastností a přiřazením hodnot stejným způsobem jako argumenty pojmenovaných konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="14051-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="14051-118">Následující kód ilustruje třídu, která má konstruktor a různé způsoby vytváření objektů.</span><span class="sxs-lookup"><span data-stu-id="14051-118">The following code illustrates a class that has a constructor and various ways of creating objects.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="14051-119">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="14051-119">The output is as follows.</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="14051-120">Konstrukce struktur</span><span class="sxs-lookup"><span data-stu-id="14051-120">Construction of Structures</span></span>

<span data-ttu-id="14051-121">Struktury dodržují všechna pravidla tříd.</span><span class="sxs-lookup"><span data-stu-id="14051-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="14051-122">Proto můžete mít primární konstruktor a můžete poskytnout další konstruktory pomocí `new`.</span><span class="sxs-lookup"><span data-stu-id="14051-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="14051-123">Nicméně existuje jeden důležitý rozdíl mezi strukturami a třídami: struktury mohou mít konstruktor bez parametrů (tj. jeden bez argumentů) i v případě, že není definován žádný primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="14051-123">However, there is one important difference between structures and classes: structures can have a parameterless constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="14051-124">Konstruktor bez parametrů inicializuje všechna pole na výchozí hodnotu pro tento typ, obvykle nula nebo ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="14051-124">The parameterless constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="14051-125">Všechny konstruktory, které definujete pro struktury, musí mít alespoň jeden argument, aby nedošlo ke konfliktu s výchozím konstruktorem.</span><span class="sxs-lookup"><span data-stu-id="14051-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the default constructor.</span></span>

<span data-ttu-id="14051-126">Struktury také často obsahují pole, která jsou vytvořena pomocí `val` klíčového slova; třídy mohou také obsahovat tato pole.</span><span class="sxs-lookup"><span data-stu-id="14051-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="14051-127">Struktury a třídy, které mají pole definovaná pomocí `val` klíčového slova, lze také inicializovat v dalších konstruktorech pomocí výrazů záznamu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="14051-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="14051-128">Další informace najdete v tématu [explicitní pole: `val` Klíčové slovo](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="14051-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>

## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="14051-129">Provádění vedlejších účinků v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="14051-129">Executing Side Effects in Constructors</span></span>

<span data-ttu-id="14051-130">Primární konstruktor ve třídě může spouštět kód ve `do` vazbě.</span><span class="sxs-lookup"><span data-stu-id="14051-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="14051-131">Co když ale budete muset spustit kód v dalším konstruktoru bez `do` vazby?</span><span class="sxs-lookup"><span data-stu-id="14051-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="14051-132">K tomu použijte `then` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="14051-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="14051-133">Vedlejší účinky primárního konstruktoru se pořád spouštějí.</span><span class="sxs-lookup"><span data-stu-id="14051-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="14051-134">Výstup je proto následující:</span><span class="sxs-lookup"><span data-stu-id="14051-134">Therefore, the output is as follows.</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="14051-135">Osobní identifikátory v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="14051-135">Self Identifiers in Constructors</span></span>

<span data-ttu-id="14051-136">V jiných členech zadáte název pro aktuální objekt v definici každého člena.</span><span class="sxs-lookup"><span data-stu-id="14051-136">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="14051-137">Identifikátor sami můžete také umístit na první řádek definice třídy pomocí `as` klíčového slova hned za parametry konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="14051-137">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="14051-138">Následující příklad ilustruje tuto syntaxi.</span><span class="sxs-lookup"><span data-stu-id="14051-138">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="14051-139">V dalších konstruktorech můžete také definovat identifikátor sami vložením `as` klauzule hned za parametry konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="14051-139">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="14051-140">Následující příklad ilustruje tuto syntaxi.</span><span class="sxs-lookup"><span data-stu-id="14051-140">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="14051-141">K problémům může dojít při pokusu o použití objektu před jeho úplným definováním.</span><span class="sxs-lookup"><span data-stu-id="14051-141">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="14051-142">Proto použití identifikátoru autoidentifier může způsobit, že kompilátor vygeneruje upozornění a vloží další kontroly, aby před inicializací objektu nebyly k dispozici členové objektu.</span><span class="sxs-lookup"><span data-stu-id="14051-142">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="14051-143">V `do` vazbách primárního konstruktoru nebo `then` za klíčovým slovem v dalších konstruktorech byste měli použít pouze samotný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="14051-143">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="14051-144">Název automatického identifikátoru nemusí být `this`.</span><span class="sxs-lookup"><span data-stu-id="14051-144">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="14051-145">Může to být libovolný platný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="14051-145">It can be any valid identifier.</span></span>

## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="14051-146">Přiřazení hodnot k vlastnostem při inicializaci</span><span class="sxs-lookup"><span data-stu-id="14051-146">Assigning Values to Properties at Initialization</span></span>

<span data-ttu-id="14051-147">Můžete přiřadit hodnoty k vlastnostem objektu třídy v inicializačním kódu připojením seznamu přiřazení formuláře `property = value` k seznamu argumentů pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="14051-147">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="14051-148">Toto je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="14051-148">This is shown in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="14051-149">Následující verze předchozího kódu ilustruje kombinaci běžných argumentů, volitelných argumentů a nastavení vlastností v jednom volání konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="14051-149">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a><span data-ttu-id="14051-150">Konstruktory v zděděné třídě</span><span class="sxs-lookup"><span data-stu-id="14051-150">Constructors in inherited class</span></span>

<span data-ttu-id="14051-151">Při dědění ze základní třídy, která má konstruktor, je nutné zadat argumenty klauzule Inherit.</span><span class="sxs-lookup"><span data-stu-id="14051-151">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="14051-152">Další informace naleznete v tématu [konstruktory a dědičnost](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="14051-152">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="14051-153">Statické konstruktory nebo konstruktory typů</span><span class="sxs-lookup"><span data-stu-id="14051-153">Static Constructors or Type Constructors</span></span>

<span data-ttu-id="14051-154">Kromě určení kódu pro vytváření objektů, statické `let` a `do` vazby lze vytvořit v typech třídy, které jsou spouštěny před prvním použitím tohoto typu k provedení inicializace na úrovni typu.</span><span class="sxs-lookup"><span data-stu-id="14051-154">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="14051-155">Další informace naleznete v tématu [ `let` Bindings in Classes](let-bindings-in-classes.md) and [ `do` Bindings in Classes](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="14051-155">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="14051-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14051-156">See also</span></span>

- [<span data-ttu-id="14051-157">Členové</span><span class="sxs-lookup"><span data-stu-id="14051-157">Members</span></span>](index.md)
