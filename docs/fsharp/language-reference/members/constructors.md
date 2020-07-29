---
title: Konstruktory
description: 'Naučte se definovat a používat konstruktory v jazyce F # pro vytváření a inicializaci objektů tříd a struktur.'
ms.date: 05/16/2016
ms.openlocfilehash: be8fc3f1d82a9a7c778a6d094139f14150a28813
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303436"
---
# <a name="constructors"></a><span data-ttu-id="d780a-103">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="d780a-103">Constructors</span></span>

<span data-ttu-id="d780a-104">Tento článek popisuje, jak definovat a používat konstruktory pro vytváření a inicializaci objektů tříd a struktur.</span><span class="sxs-lookup"><span data-stu-id="d780a-104">This article describes how to define and use constructors to create and initialize class and structure objects.</span></span>

## <a name="construction-of-class-objects"></a><span data-ttu-id="d780a-105">Konstrukce objektů třídy</span><span class="sxs-lookup"><span data-stu-id="d780a-105">Construction of class objects</span></span>

<span data-ttu-id="d780a-106">Objekty typů třídy mají konstruktory.</span><span class="sxs-lookup"><span data-stu-id="d780a-106">Objects of class types have constructors.</span></span> <span data-ttu-id="d780a-107">Existují dva druhy konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="d780a-107">There are two kinds of constructors.</span></span> <span data-ttu-id="d780a-108">Jedna je primární konstruktor, jehož parametry jsou uvedeny v závorkách hned za názvem typu.</span><span class="sxs-lookup"><span data-stu-id="d780a-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="d780a-109">Pomocí klíčového slova určíte jiné volitelné Další konstruktory `new` .</span><span class="sxs-lookup"><span data-stu-id="d780a-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="d780a-110">Jakékoli takové další konstruktory musí volat primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d780a-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="d780a-111">Primární konstruktor obsahuje `let` a `do` vazby, které se zobrazí na začátku definice třídy.</span><span class="sxs-lookup"><span data-stu-id="d780a-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="d780a-112">`let`Vazba deklaruje soukromá pole a metody třídy; `do` vazba spustí kód.</span><span class="sxs-lookup"><span data-stu-id="d780a-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="d780a-113">Další informace o `let` vazbách v konstruktorech třídy naleznete v tématu [ `let` Bindings in Classes](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="d780a-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="d780a-114">Další informace o `do` vazbách v konstruktorech naleznete v tématu [ `do` Bindings in Classes](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="d780a-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="d780a-115">Bez ohledu na to, zda je konstruktor, který chcete volat, primární konstruktor nebo další konstruktor, lze objekty vytvořit pomocí `new` výrazu s volitelným `new` klíčovým slovem nebo bez něj.</span><span class="sxs-lookup"><span data-stu-id="d780a-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="d780a-116">Vaše objekty můžete inicializovat společně s argumenty konstruktoru, buď výpisem argumentů v pořadí a oddělenými čárkami a uzavřeny v závorkách, nebo pomocí pojmenovaných argumentů a hodnot v závorkách.</span><span class="sxs-lookup"><span data-stu-id="d780a-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="d780a-117">Můžete také nastavit vlastnosti objektu během konstrukce objektu pomocí názvů vlastností a přiřazením hodnot stejným způsobem jako argumenty pojmenovaných konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="d780a-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="d780a-118">Následující kód ilustruje třídu, která má konstruktor a různé způsoby vytváření objektů:</span><span class="sxs-lookup"><span data-stu-id="d780a-118">The following code illustrates a class that has a constructor and various ways of creating objects:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="d780a-119">Výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="d780a-119">The output is as follows:</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="d780a-120">Konstrukce struktur</span><span class="sxs-lookup"><span data-stu-id="d780a-120">Construction of structures</span></span>

<span data-ttu-id="d780a-121">Struktury dodržují všechna pravidla tříd.</span><span class="sxs-lookup"><span data-stu-id="d780a-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="d780a-122">Proto můžete mít primární konstruktor a můžete poskytnout další konstruktory pomocí `new` .</span><span class="sxs-lookup"><span data-stu-id="d780a-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="d780a-123">Nicméně existuje jeden důležitý rozdíl mezi strukturami a třídami: struktury mohou mít konstruktor bez parametrů (tj. jeden bez argumentů) i v případě, že není definován žádný primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d780a-123">However, there is one important difference between structures and classes: structures can have a parameterless constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="d780a-124">Konstruktor bez parametrů inicializuje všechna pole na výchozí hodnotu pro tento typ, obvykle nula nebo ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="d780a-124">The parameterless constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="d780a-125">Všechny konstruktory, které definujete pro struktury, musí mít alespoň jeden argument, aby nedošlo ke konfliktu s konstruktory bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="d780a-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the parameterless constructor.</span></span>

<span data-ttu-id="d780a-126">Struktury také často obsahují pole, která jsou vytvořena pomocí `val` klíčového slova; třídy mohou také obsahovat tato pole.</span><span class="sxs-lookup"><span data-stu-id="d780a-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="d780a-127">Struktury a třídy, které mají pole definovaná pomocí `val` klíčového slova, lze také inicializovat v dalších konstruktorech pomocí výrazů záznamu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d780a-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="d780a-128">Další informace naleznete v tématu [explicitní pole: `val` klíčové slovo](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="d780a-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>

## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="d780a-129">Provádění vedlejších účinků v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="d780a-129">Executing side effects in constructors</span></span>

<span data-ttu-id="d780a-130">Primární konstruktor ve třídě může spouštět kód ve `do` vazbě.</span><span class="sxs-lookup"><span data-stu-id="d780a-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="d780a-131">Co když ale budete muset spustit kód v dalším konstruktoru bez `do` vazby?</span><span class="sxs-lookup"><span data-stu-id="d780a-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="d780a-132">K tomu použijte `then` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d780a-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="d780a-133">Vedlejší účinky primárního konstruktoru se pořád spouštějí.</span><span class="sxs-lookup"><span data-stu-id="d780a-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="d780a-134">Výstup je proto následující:</span><span class="sxs-lookup"><span data-stu-id="d780a-134">Therefore, the output is as follows:</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

<span data-ttu-id="d780a-135">Důvod, proč `then` je vyžadováno místo jiného `do` , je, že `do` klíčové slovo má svůj standardní význam pro omezení `unit` vracející výraz, pokud je k dispozici v těle dalšího konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d780a-135">The reason why `then` is required instead of another `do` is that the `do` keyword has its standard meaning of delimiting a `unit`-returning expression when present in the body of an additional constructor.</span></span> <span data-ttu-id="d780a-136">Má pouze zvláštní význam v kontextu primárních konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="d780a-136">It only has special meaning in the context of primary constructors.</span></span>

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="d780a-137">Osobní identifikátory v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="d780a-137">Self identifiers in constructors</span></span>

<span data-ttu-id="d780a-138">V jiných členech zadáte název pro aktuální objekt v definici každého člena.</span><span class="sxs-lookup"><span data-stu-id="d780a-138">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="d780a-139">Identifikátor sami můžete také umístit na první řádek definice třídy pomocí `as` klíčového slova hned za parametry konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d780a-139">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="d780a-140">Následující příklad ilustruje tuto syntaxi.</span><span class="sxs-lookup"><span data-stu-id="d780a-140">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="d780a-141">V dalších konstruktorech můžete také definovat identifikátor sami vložením `as` klauzule hned za parametry konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d780a-141">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="d780a-142">Následující příklad ilustruje tuto syntaxi:</span><span class="sxs-lookup"><span data-stu-id="d780a-142">The following example illustrates this syntax:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="d780a-143">K problémům může dojít při pokusu o použití objektu před jeho úplným definováním.</span><span class="sxs-lookup"><span data-stu-id="d780a-143">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="d780a-144">Proto použití identifikátoru autoidentifier může způsobit, že kompilátor vygeneruje upozornění a vloží další kontroly, aby před inicializací objektu nebyly k dispozici členové objektu.</span><span class="sxs-lookup"><span data-stu-id="d780a-144">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="d780a-145">V `do` vazbách primárního konstruktoru nebo za `then` klíčovým slovem v dalších konstruktorech byste měli použít pouze samotný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="d780a-145">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="d780a-146">Název automatického identifikátoru nemusí být `this` .</span><span class="sxs-lookup"><span data-stu-id="d780a-146">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="d780a-147">Může to být libovolný platný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="d780a-147">It can be any valid identifier.</span></span>

## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="d780a-148">Přiřazení hodnot k vlastnostem při inicializaci</span><span class="sxs-lookup"><span data-stu-id="d780a-148">Assigning values to properties at initialization</span></span>

<span data-ttu-id="d780a-149">Můžete přiřadit hodnoty k vlastnostem objektu třídy v inicializačním kódu připojením seznamu přiřazení formuláře `property = value` k seznamu argumentů pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d780a-149">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="d780a-150">To je znázorněno v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="d780a-150">This is shown in the following code example:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="d780a-151">Následující verze předchozího kódu ilustruje kombinaci běžných argumentů, volitelných argumentů a nastavení vlastností ve volání jednoho konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="d780a-151">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a><span data-ttu-id="d780a-152">Konstruktory v zděděné třídě</span><span class="sxs-lookup"><span data-stu-id="d780a-152">Constructors in inherited class</span></span>

<span data-ttu-id="d780a-153">Při dědění ze základní třídy, která má konstruktor, je nutné zadat argumenty klauzule Inherit.</span><span class="sxs-lookup"><span data-stu-id="d780a-153">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="d780a-154">Další informace naleznete v tématu [konstruktory a dědičnost](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="d780a-154">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="d780a-155">Statické konstruktory nebo konstruktory typů</span><span class="sxs-lookup"><span data-stu-id="d780a-155">Static constructors or type constructors</span></span>

<span data-ttu-id="d780a-156">Kromě určení kódu pro vytváření objektů, statické `let` a `do` vazby lze vytvořit v typech třídy, které jsou spouštěny před prvním použitím tohoto typu k provedení inicializace na úrovni typu.</span><span class="sxs-lookup"><span data-stu-id="d780a-156">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="d780a-157">Další informace naleznete v tématu [ `let` Bindings in Classes](let-bindings-in-classes.md) and [ `do` Bindings in Classes](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="d780a-157">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d780a-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d780a-158">See also</span></span>

- [<span data-ttu-id="d780a-159">Členové</span><span class="sxs-lookup"><span data-stu-id="d780a-159">Members</span></span>](index.md)
