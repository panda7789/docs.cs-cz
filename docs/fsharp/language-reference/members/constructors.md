---
title: Konstruktory (F#)
description: "Zjistěte, jak definovat a použít konstruktory v jazyce F # k vytvoření a inicializace třídy a struktury objektů."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: e0da2250-29de-4145-a1be-e5faff080759
ms.openlocfilehash: 60ed93f1c1dc15e99465d969c9e4fd3e61c28ffa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="constructors"></a><span data-ttu-id="d11f9-104">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="d11f9-104">Constructors</span></span>

<span data-ttu-id="d11f9-105">Toto téma popisuje, jak definovat a použít k vytvoření a inicializace objektů třídy a struktury konstruktory.</span><span class="sxs-lookup"><span data-stu-id="d11f9-105">This topic describes how to define and use constructors to create and initialize class and structure objects.</span></span>


## <a name="construction-of-class-objects"></a><span data-ttu-id="d11f9-106">Konstrukce objektů – třída</span><span class="sxs-lookup"><span data-stu-id="d11f9-106">Construction of Class Objects</span></span>
<span data-ttu-id="d11f9-107">Objekty třídy typů mít konstruktory.</span><span class="sxs-lookup"><span data-stu-id="d11f9-107">Objects of class types have constructors.</span></span> <span data-ttu-id="d11f9-108">Existují dva druhy konstruktory.</span><span class="sxs-lookup"><span data-stu-id="d11f9-108">There are two kinds of constructors.</span></span> <span data-ttu-id="d11f9-109">Jeden je primární konstruktoru, jejíž parametry se zobrazí v závorkách bezprostředně za název typu.</span><span class="sxs-lookup"><span data-stu-id="d11f9-109">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="d11f9-110">Zadejte jiné, volitelné další konstruktory pomocí `new` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d11f9-110">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="d11f9-111">Tyto další konstruktory musí volat primární konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d11f9-111">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="d11f9-112">Obsahuje primární konstruktor `let` a `do` vazby, které se zobrazují na začátku definici třídy.</span><span class="sxs-lookup"><span data-stu-id="d11f9-112">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="d11f9-113">A `let` vazba deklaruje privátním polím a metody třídy; `do` vazby spustí kód.</span><span class="sxs-lookup"><span data-stu-id="d11f9-113">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="d11f9-114">Další informace o `let` vazby v konstruktorech třídy, najdete v části [ `let` vazby do ve třídách](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="d11f9-114">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="d11f9-115">Další informace o `do` vazby v konstruktorech, najdete v části [ `do` vazby do ve třídách](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="d11f9-115">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="d11f9-116">Bez ohledu na to, jestli je konstruktor, který chcete použít primární konstruktor nebo další konstruktor, můžete vytvořit objekty pomocí `new` výraz s nebo bez volitelné `new` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d11f9-116">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="d11f9-117">Inicializace objektů vašeho společně s argumenty konstruktoru, buď tak, že uvedete argumenty v pořadí a oddělených čárkami a uzavřený v závorkách, nebo pomocí pojmenované argumenty a hodnoty v závorkách.</span><span class="sxs-lookup"><span data-stu-id="d11f9-117">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="d11f9-118">Můžete také nastavit vlastnosti objektu během vytváření objektu pomocí názvů vlastností a přiřazení hodnoty, stejně jako použít s názvem argumenty konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="d11f9-118">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="d11f9-119">Následující kód ukazuje třídu, která má konstruktor a různé způsoby vytváření objektů.</span><span class="sxs-lookup"><span data-stu-id="d11f9-119">The following code illustrates a class that has a constructor and various ways of creating objects.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="d11f9-120">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="d11f9-120">The output is as follows.</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="d11f9-121">Vytváření struktur</span><span class="sxs-lookup"><span data-stu-id="d11f9-121">Construction of Structures</span></span>
<span data-ttu-id="d11f9-122">Struktury podle všechna pravidla tříd.</span><span class="sxs-lookup"><span data-stu-id="d11f9-122">Structures follow all the rules of classes.</span></span> <span data-ttu-id="d11f9-123">Proto může mít primární konstruktor a můžete poskytnout další konstruktory pomocí `new`.</span><span class="sxs-lookup"><span data-stu-id="d11f9-123">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="d11f9-124">Nicméně je důležitý rozdíl mezi struktury a třídy: struktury může mít výchozí konstruktor (to znamená, jeden bez argumentů), i když je definovaný žádný primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d11f9-124">However, there is one important difference between structures and classes: structures can have a default constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="d11f9-125">Výchozí konstruktor inicializuje všechna pole na výchozí hodnotu pro tento typ, obvykle nula nebo jeho ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="d11f9-125">The default constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="d11f9-126">Všechny konstruktory, které definujete pro struktury musí mít alespoň jeden argument, tak, aby nedošlo ke konfliktu s výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d11f9-126">Any constructors that you define for structures must have at least one argument so that they do not conflict with the default constructor.</span></span>

<span data-ttu-id="d11f9-127">Navíc struktury mají často pole, které jsou vytvořené pomocí `val` – klíčové slovo; třídy může mít tato pole.</span><span class="sxs-lookup"><span data-stu-id="d11f9-127">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="d11f9-128">Struktury a třídy, které mají pole definovaná pomocí `val` – klíčové slovo může být navíc inicializované v konstruktorech další pomocí záznamu výrazy, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d11f9-128">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="d11f9-129">Další informace najdete v tématu [explicitní pole: `val` – klíčové slovo](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="d11f9-129">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>


## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="d11f9-130">Provádění vedlejší účinky v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="d11f9-130">Executing Side Effects in Constructors</span></span>
<span data-ttu-id="d11f9-131">Primární konstruktor v třídě může spustit kód `do` vazby.</span><span class="sxs-lookup"><span data-stu-id="d11f9-131">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="d11f9-132">Ale co když máte bez spuštění kódu v další konstruktoru, `do` vazbu?</span><span class="sxs-lookup"><span data-stu-id="d11f9-132">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="d11f9-133">K tomuto účelu použijete `then` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="d11f9-133">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="d11f9-134">Vedlejší efekty primární konstruktoru spustit.</span><span class="sxs-lookup"><span data-stu-id="d11f9-134">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="d11f9-135">Proto výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="d11f9-135">Therefore, the output is as follows.</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="d11f9-136">Self – identifikátory v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="d11f9-136">Self Identifiers in Constructors</span></span>
<span data-ttu-id="d11f9-137">V další členy zadejte název pro aktuální objekt v definici u každého člena.</span><span class="sxs-lookup"><span data-stu-id="d11f9-137">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="d11f9-138">Vlastní identifikátor můžete také umístit na první řádek definice třídy pomocí `as` – klíčové slovo okamžitě následující parametry konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d11f9-138">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="d11f9-139">Následující příklad ilustruje tuto syntaxi.</span><span class="sxs-lookup"><span data-stu-id="d11f9-139">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="d11f9-140">V další konstruktory, můžete také definovat vlastní identifikátor umístěním `as` klauzule hned po parametry konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d11f9-140">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="d11f9-141">Následující příklad ilustruje tuto syntaxi.</span><span class="sxs-lookup"><span data-stu-id="d11f9-141">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="d11f9-142">Problémy může dojít, když se pokusíte použít objekt předtím, než je plně definována.</span><span class="sxs-lookup"><span data-stu-id="d11f9-142">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="d11f9-143">Použití vlastní identifikátor proto může způsobit kompilátor posílat upozornění a další kontroly, aby se zajistilo, že členové objektu nejsou přístupné před inicializací objekt vložit.</span><span class="sxs-lookup"><span data-stu-id="d11f9-143">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="d11f9-144">Vlastní identifikátor v byste měli používat jenom `do` vazby primární konstruktoru, nebo po `then` – klíčové slovo v další konstruktory.</span><span class="sxs-lookup"><span data-stu-id="d11f9-144">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="d11f9-145">Název vlastní identifikátor nemusí být `this`.</span><span class="sxs-lookup"><span data-stu-id="d11f9-145">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="d11f9-146">Může být libovolný platný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="d11f9-146">It can be any valid identifier.</span></span>


## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="d11f9-147">Přiřazení hodnoty k vlastnosti v inicializace</span><span class="sxs-lookup"><span data-stu-id="d11f9-147">Assigning Values to Properties at Initialization</span></span>
<span data-ttu-id="d11f9-148">Můžete přiřadit hodnoty k vlastnosti objektu třídy v kódu inicializace připojením seznam přiřazení formuláře `property = value` na seznam argumentů pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d11f9-148">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="d11f9-149">To je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="d11f9-149">This is shown in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="d11f9-150">Následující verze předchozí kód ukazuje kombinace obyčejnou argumenty nepovinné argumenty a nastavení vlastností ve volání jednoho konstruktor.</span><span class="sxs-lookup"><span data-stu-id="d11f9-150">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]
    
## <a name="constructors-in-inherited-class"></a><span data-ttu-id="d11f9-151">Konstruktory v zděděné třídy</span><span class="sxs-lookup"><span data-stu-id="d11f9-151">Constructors in inherited class</span></span>
<span data-ttu-id="d11f9-152">Když je zděděný z databáze třídu, která má konstruktor, je nutné zadat v klauzuli inherit její argumenty.</span><span class="sxs-lookup"><span data-stu-id="d11f9-152">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="d11f9-153">Další informace najdete v tématu [konstruktory a dědičnost](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="d11f9-153">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="d11f9-154">Statické konstruktory nebo konstruktory typu</span><span class="sxs-lookup"><span data-stu-id="d11f9-154">Static Constructors or Type Constructors</span></span>
<span data-ttu-id="d11f9-155">Kromě určení kód pro vytváření objektů, statické `let` a `do` vazby mohou být vytvořeny v typy tříd, které se spouští před typ poprvé použila k provedení inicializace na úrovni typu.</span><span class="sxs-lookup"><span data-stu-id="d11f9-155">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="d11f9-156">Další informace najdete v tématu [ `let` vazby do ve třídách](let-bindings-in-classes.md) a [ `do` vazby do ve třídách](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="d11f9-156">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d11f9-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="d11f9-157">See Also</span></span>
[<span data-ttu-id="d11f9-158">Členy</span><span class="sxs-lookup"><span data-stu-id="d11f9-158">Members</span></span>](index.md)
