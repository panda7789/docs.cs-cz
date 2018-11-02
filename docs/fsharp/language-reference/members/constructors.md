---
title: Konstruktory (F#)
description: 'Zjistěte, jak definovat a používat konstruktory v jazyce F # k vytvoření a inicializaci objektů třídy a struktury.'
ms.date: 05/16/2016
ms.openlocfilehash: ff2463f890034cce0bbaa85d9a5c93e50427cd03
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "45743914"
---
# <a name="constructors"></a><span data-ttu-id="e5b7e-103">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="e5b7e-103">Constructors</span></span>

<span data-ttu-id="e5b7e-104">Toto téma popisuje, jak definovat a používat konstruktory vytváření a inicializace objektů třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-104">This topic describes how to define and use constructors to create and initialize class and structure objects.</span></span>

## <a name="construction-of-class-objects"></a><span data-ttu-id="e5b7e-105">Vytváření objektů tříd</span><span class="sxs-lookup"><span data-stu-id="e5b7e-105">Construction of Class Objects</span></span>

<span data-ttu-id="e5b7e-106">Objekty typů třídy mají konstruktory.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-106">Objects of class types have constructors.</span></span> <span data-ttu-id="e5b7e-107">Existují dva typy konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-107">There are two kinds of constructors.</span></span> <span data-ttu-id="e5b7e-108">Jeden je primární konstruktor, jehož parametry se zobrazí v závorkách hned za název typu.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="e5b7e-109">Zadejte jiné, volitelné další konstruktory s použitím `new` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="e5b7e-110">Tyto další konstruktory musí volat primárnímu konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="e5b7e-111">Primární konstruktor obsahuje `let` a `do` vazby, které se zobrazí na začátku definice třídy.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="e5b7e-112">A `let` vazba deklaruje privátním polím a metodám třídy; `do` vazby spustí kód.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="e5b7e-113">Další informace o `let` vazby v konstruktorech tříd naleznete v tématu [ `let` vazby ve třídách](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="e5b7e-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="e5b7e-114">Další informace o `do` vazby v konstruktorech, naleznete v tématu [ `do` vazby ve třídách](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="e5b7e-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="e5b7e-115">Bez ohledu na to, jestli chcete volat konstruktor primárnímu konstruktoru nebo dodatečném konstruktoru, můžete vytvořit objekty pomocí `new` výrazu, s nebo bez něj nepovinný `new` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="e5b7e-116">Inicializace objektů spolu s argumenty konstruktoru, buď uvedením argumentů v pořadí a oddělené čárkami a uzavřeny v závorkách, nebo pomocí pojmenovaných argumentů a hodnoty v závorkách.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="e5b7e-117">Můžete také nastavit vlastnosti pro objekt během konstrukce objektu pomocí názvů vlastností a přiřazuje hodnoty stejným způsobem, jako pojmenované argumenty konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="e5b7e-118">Následující kód ukazuje třídu, která má konstruktor a různé způsoby vytváření objektů.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-118">The following code illustrates a class that has a constructor and various ways of creating objects.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="e5b7e-119">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-119">The output is as follows.</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="e5b7e-120">Vytváření struktur</span><span class="sxs-lookup"><span data-stu-id="e5b7e-120">Construction of Structures</span></span>

<span data-ttu-id="e5b7e-121">Struktury postupujte podle všech pravidel tříd.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="e5b7e-122">Proto může mít primárnímu konstruktoru, a můžete poskytnout další konstruktory pomocí `new`.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="e5b7e-123">Existuje ale jeden důležitý rozdíl mezi strukturami a třídami: struktury mohou mít výchozí konstruktor (to znamená, jeden bez argumentů) i v případě, že je definován žádný primární konstruktor.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-123">However, there is one important difference between structures and classes: structures can have a default constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="e5b7e-124">Výchozí konstruktor inicializuje všechna pole na výchozí hodnotu pro daný typ, obvykle nula nebo jeho ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-124">The default constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="e5b7e-125">Žádné konstruktory, které definujete pro struktury musí mít aspoň jeden argument, aby se nepřekrývaly s výchozím konstruktorem.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the default constructor.</span></span>

<span data-ttu-id="e5b7e-126">Navíc struktury často obsahuje pole, která se vytvářejí pomocí `val` – klíčové slovo; třídy mohou také mít tato pole.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="e5b7e-127">Struktury a třídy, které mají pole definovaná pomocí `val` – klíčové slovo může být navíc inicializované v konstruktorech další s využitím výrazy záznamu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="e5b7e-128">Další informace najdete v tématu [explicitní pole: `val` – klíčové slovo](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="e5b7e-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>

## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="e5b7e-129">Provádění vedlejší účinky v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="e5b7e-129">Executing Side Effects in Constructors</span></span>

<span data-ttu-id="e5b7e-130">Primární konstruktoru ve třídě může spustit kód v `do` vazby.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="e5b7e-131">Ale co kdybyste měli ke spouštění kódu vytvořeného v dodatečném konstruktoru, aniž by `do` vazbu?</span><span class="sxs-lookup"><span data-stu-id="e5b7e-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="e5b7e-132">K tomuto účelu můžete použít `then` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="e5b7e-133">Vedlejší účinky primárního konstruktoru stále spustit.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="e5b7e-134">Proto výstup vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-134">Therefore, the output is as follows.</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="e5b7e-135">Self – identifikátory v konstruktorech</span><span class="sxs-lookup"><span data-stu-id="e5b7e-135">Self Identifiers in Constructors</span></span>

<span data-ttu-id="e5b7e-136">V jiných členů zadejte název pro aktuální objekt v definici každého člena.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-136">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="e5b7e-137">Vlastní identifikátor lze také umístit na první řádek definice třídy pomocí `as` – klíčové slovo hned za parametry konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-137">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="e5b7e-138">Následující příklad ukazuje tuto syntaxi.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-138">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="e5b7e-139">V další konstruktory, můžete také definovat vlastní identifikátor vložením `as` klauzule hned po parametry konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-139">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="e5b7e-140">Následující příklad ukazuje tuto syntaxi.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-140">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="e5b7e-141">Při pokusu o použití objektu předtím, než je plně definována, může dojít k problémům.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-141">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="e5b7e-142">Použití identifikátoru samotného proto může způsobit kompilátor vygeneruje upozornění a vložit další kontroly k zajištění, že členové objektu nejsou přístupná před objekt je inicializován.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-142">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="e5b7e-143">Vlastní identifikátor v byste měli používat jenom `do` vazby primárního konstruktoru, nebo po `then` – klíčové slovo v dalších konstruktory.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-143">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="e5b7e-144">Název identifikátoru samotného nemusí být `this`.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-144">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="e5b7e-145">Může být libovolný platný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-145">It can be any valid identifier.</span></span>

## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="e5b7e-146">Přiřazení hodnoty k vlastnostem při inicializaci</span><span class="sxs-lookup"><span data-stu-id="e5b7e-146">Assigning Values to Properties at Initialization</span></span>

<span data-ttu-id="e5b7e-147">Můžete přiřadit hodnoty k vlastnostem objektu třídy v inicializační kód přidáním seznam přiřazení formuláře `property = value` na seznam argumentů pro konstruktor.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-147">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="e5b7e-148">To je ukázáno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-148">This is shown in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="e5b7e-149">Následující verze předchozího kódu ukazuje kombinace běžné argumenty, volitelné argumenty a nastavení vlastností ve volání jeden konstruktor.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-149">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a><span data-ttu-id="e5b7e-150">Konstruktory ve zděděné třídě</span><span class="sxs-lookup"><span data-stu-id="e5b7e-150">Constructors in inherited class</span></span>

<span data-ttu-id="e5b7e-151">Při dědění ze základní třídy, která má konstruktor, je nutné zadat argumenty v klauzuli zdědit.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-151">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="e5b7e-152">Další informace najdete v tématu [konstruktory a dědičnost](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="e5b7e-152">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="e5b7e-153">Statické konstruktory nebo konstruktory typu</span><span class="sxs-lookup"><span data-stu-id="e5b7e-153">Static Constructors or Type Constructors</span></span>

<span data-ttu-id="e5b7e-154">Kromě zadání kódu pro vytváření objektů, statické `let` a `do` se můžou vytvořit vazby ve typy tříd, které se provedou předtím, než typ poprvé použila k provedení inicializace na úrovni typu.</span><span class="sxs-lookup"><span data-stu-id="e5b7e-154">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="e5b7e-155">Další informace najdete v tématu [ `let` vazby ve třídách](let-bindings-in-classes.md) a [ `do` vazby ve třídách](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="e5b7e-155">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5b7e-156">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5b7e-156">See also</span></span>

- [<span data-ttu-id="e5b7e-157">Členové</span><span class="sxs-lookup"><span data-stu-id="e5b7e-157">Members</span></span>](index.md)
