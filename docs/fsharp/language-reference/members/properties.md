---
title: Vlastnosti (F#)
description: "Další informace o F # vlastnosti, které jsou členy, které reprezentují hodnoty přidružené k objektu."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 98b363a5-ee6a-4b7b-b8ae-b244f2a0b316
ms.openlocfilehash: 53b93b20310c557ad9c30226bc08f85cbf2f3010
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="properties"></a><span data-ttu-id="a35cf-104">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a35cf-104">Properties</span></span>

<span data-ttu-id="a35cf-105">*Vlastnosti* jsou členy, které reprezentují hodnoty přidružené k objektu.</span><span class="sxs-lookup"><span data-stu-id="a35cf-105">*Properties* are members that represent values associated with an object.</span></span>


## <a name="syntax"></a><span data-ttu-id="a35cf-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a35cf-106">Syntax</span></span>

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a><span data-ttu-id="a35cf-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a35cf-107">Remarks</span></span>
<span data-ttu-id="a35cf-108">Vlastnosti představují "má" vztahu v rámci objektově orientované programování reprezentující data, která souvisí s instancí objektů nebo statických vlastností s typem.</span><span class="sxs-lookup"><span data-stu-id="a35cf-108">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="a35cf-109">Vlastnosti dvěma způsoby v závislosti na tom, jestli chcete explicitně zadat základní hodnotu (označovanou taky jako úložiště zálohování) pro vlastnost, nebo pokud chcete povolit kompilátor automaticky generuje úložiště zálohování pro vás můžou deklarovat.</span><span class="sxs-lookup"><span data-stu-id="a35cf-109">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="a35cf-110">Obecně byste měli použít podrobnější způsob, pokud má vlastnost netriviální implementace a automatické způsob při vlastnost je stejně jednoduché obálku pro hodnota nebo proměnná.</span><span class="sxs-lookup"><span data-stu-id="a35cf-110">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="a35cf-111">Chcete-li explicitně deklarace vlastnosti, použijte `member` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="a35cf-111">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="a35cf-112">Tato deklarativní syntaxe následuje syntaxi, která určuje, `get` a `set` metody, také s názvem *přístupové objekty*.</span><span class="sxs-lookup"><span data-stu-id="a35cf-112">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="a35cf-113">Vlastnosti jen pro čtení a zápisu jen pro čtení a zápis, se používají různé formy explicitní syntaxi uvedenou v části syntaxe.</span><span class="sxs-lookup"><span data-stu-id="a35cf-113">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="a35cf-114">Vlastnosti jen pro čtení, můžete definovat jenom `get` metoda; pouze pro vlastnosti jen pro zápis, definovat `set` metoda.</span><span class="sxs-lookup"><span data-stu-id="a35cf-114">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="a35cf-115">Všimněte si, že pokud má vlastnost obě `get` a `set` přístupových objektů, alternativní syntaxe umožňuje určit atributy a modifikátory usnadnění, které se liší pro každý přistupující objekt, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a35cf-115">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="a35cf-116">Pro vlastnosti čtení/zápisu, které oba `get` a `set` metoda, pořadí `get` a `set` lze vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="a35cf-116">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="a35cf-117">Alternativně můžete zadat syntaxi uvedenou pro `get` pouze a syntaxe pro `set` pouze místo použití kombinované syntaxe.</span><span class="sxs-lookup"><span data-stu-id="a35cf-117">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="a35cf-118">To usnadňuje komentář jednotlivých `get` nebo `set` metodu, pokud je něco možná budete muset provést.</span><span class="sxs-lookup"><span data-stu-id="a35cf-118">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="a35cf-119">Následující kód ukazuje tento alternativu k použití kombinované syntaxe.</span><span class="sxs-lookup"><span data-stu-id="a35cf-119">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="a35cf-120">Soukromé hodnoty tohoto uchování data pro vlastnosti se nazývají *záložnímu úložišti*.</span><span class="sxs-lookup"><span data-stu-id="a35cf-120">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="a35cf-121">Pokud chcete, aby kompilátoru záložní úložiště vytvářet automaticky, použijte klíčová slova `member val`, vynechejte vlastní identifikátor, a zadejte výraz k inicializaci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a35cf-121">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="a35cf-122">Pokud má-li být měnitelný vlastnost, zahrnout `with get, set`.</span><span class="sxs-lookup"><span data-stu-id="a35cf-122">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="a35cf-123">Například následující typ třídy obsahuje dvě automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a35cf-123">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="a35cf-124">`Property1`je jen pro čtení a je inicializováno argument poskytnutý primární konstruktoru, a `Property2` se nastavit vlastnost inicializovat na prázdný řetězec:</span><span class="sxs-lookup"><span data-stu-id="a35cf-124">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="a35cf-125">Automaticky implementované vlastnosti jsou součástí inicializace typu, proto musí být obsažena před jiné definice člen podobně jako `let` vazby a `do` vazby v definici typu.</span><span class="sxs-lookup"><span data-stu-id="a35cf-125">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="a35cf-126">Všimněte si, že výraz, který inicializuje automaticky implementované vlastnosti je Vyhodnocená jenom po inicializaci a není pokaždé, když vlastnost přistupuje.</span><span class="sxs-lookup"><span data-stu-id="a35cf-126">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="a35cf-127">Toto chování se liší od chování – explicitně implementovaná vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a35cf-127">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="a35cf-128">Co to znamená, je, že kód pro inicializaci tyto vlastnosti se přidá do konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="a35cf-128">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="a35cf-129">Vezměte v úvahu následující kód, který ukazuje tento rozdíl:</span><span class="sxs-lookup"><span data-stu-id="a35cf-129">Consider the following code that shows this difference:</span></span>

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.AutoProperty = %d" class1.AutoProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
printfn "class1.ExplicitProperty = %d" class1.ExplicitProperty
```

<span data-ttu-id="a35cf-130">**Výstup**</span><span class="sxs-lookup"><span data-stu-id="a35cf-130">**Output**</span></span>

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="a35cf-131">Výstup předchozí kód ukazuje, že hodnota AutoProperty je beze změny při volání opakovaně, zatímco ExplicitProperty změní pokaždé, když je volána.</span><span class="sxs-lookup"><span data-stu-id="a35cf-131">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="a35cf-132">To znamená, že výraz automaticky implementované vlastnosti není vyhodnocen pokaždé, když, jako je metoda getter pro explicitní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a35cf-132">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>


>[!WARNING]
<span data-ttu-id="a35cf-133">Existují některé knihovny, například rozhraní Entity Framework (`System.Data.Entity`), provádění vlastních operací v konstruktorech základní třídu, která nejsou dobře fungují s inicializace automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a35cf-133">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="a35cf-134">V takových případech použijte explicitní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a35cf-134">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="a35cf-135">Vlastnosti mohou být členy třídy, struktury, rozlišovaná sjednocení, záznamy, rozhraní a typ rozšíření a může být také definováno v objektové výrazy.</span><span class="sxs-lookup"><span data-stu-id="a35cf-135">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="a35cf-136">Atributy lze použít jako vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a35cf-136">Attributes can be applied to properties.</span></span> <span data-ttu-id="a35cf-137">Použít atribut na vlastnost, zapište na samostatném řádku před vlastnost atribut.</span><span class="sxs-lookup"><span data-stu-id="a35cf-137">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="a35cf-138">Další informace najdete v tématu [atributy](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a35cf-138">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="a35cf-139">Ve výchozím nastavení jsou veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a35cf-139">By default, properties are public.</span></span> <span data-ttu-id="a35cf-140">Modifikátory usnadnění přístupu lze použít také k vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="a35cf-140">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="a35cf-141">Použít usnadnění modifikátor, přidejte ho bezprostředně před název vlastnosti, pokud smyslem je chcete použít pro obě `get` a `set` metody; přidejte ho před `get` a `set` klíčová slova, pokud je jiný pro usnadnění přístupu vyžaduje se pro každý přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="a35cf-141">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="a35cf-142">*Modifikátor dostupnosti* může být jedna z následujících: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="a35cf-142">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="a35cf-143">Další informace najdete v tématu [řízení přístupu](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="a35cf-143">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="a35cf-144">Vlastnost implementace jsou spouštěny pokaždé, když vlastnost přistupuje.</span><span class="sxs-lookup"><span data-stu-id="a35cf-144">Property implementations are executed each time a property is accessed.</span></span>


## <a name="static-and-instance-properties"></a><span data-ttu-id="a35cf-145">Statické a instanci vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a35cf-145">Static and Instance Properties</span></span>
<span data-ttu-id="a35cf-146">Vlastnosti můžou být statické nebo vlastnosti instance.</span><span class="sxs-lookup"><span data-stu-id="a35cf-146">Properties can be static or instance properties.</span></span> <span data-ttu-id="a35cf-147">Statické vlastnosti může být volána bez instance a jsou používány pro hodnoty související s typem, ne při jednotlivých objektů.</span><span class="sxs-lookup"><span data-stu-id="a35cf-147">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="a35cf-148">Statické vlastnosti vynechejte vlastní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="a35cf-148">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="a35cf-149">Je vyžadován pro vlastnosti instance vlastní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="a35cf-149">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="a35cf-150">Následující definice statické vlastnosti je založena na situaci, ve kterém máte statické pole `myStaticValue` tedy úložiště zálohování pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a35cf-150">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="a35cf-151">Vlastnosti může být také jako pole, v takovém případě se nazývají *indexovaných vlastností*.</span><span class="sxs-lookup"><span data-stu-id="a35cf-151">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="a35cf-152">Další informace najdete v tématu [indexované vlastnosti](indexed-properties.md).</span><span class="sxs-lookup"><span data-stu-id="a35cf-152">For more information, see [Indexed Properties](indexed-properties.md).</span></span>


## <a name="type-annotation-for-properties"></a><span data-ttu-id="a35cf-153">Anotaci typu vlastností</span><span class="sxs-lookup"><span data-stu-id="a35cf-153">Type Annotation for Properties</span></span>
<span data-ttu-id="a35cf-154">V mnoha případech kompilátor má dostatek informací k odvození typu vlastnosti z typu záložnímu úložišti, ale můžete nastavit typ explicitně přidáním anotaci typu.</span><span class="sxs-lookup"><span data-stu-id="a35cf-154">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="a35cf-155">Pomocí vlastnosti nastavení přístupových objektů</span><span class="sxs-lookup"><span data-stu-id="a35cf-155">Using Property set Accessors</span></span>
<span data-ttu-id="a35cf-156">Můžete nastavit vlastnosti, které poskytují `set` přístupových objektů pomocí `<-` operátor.</span><span class="sxs-lookup"><span data-stu-id="a35cf-156">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="a35cf-157">Výstupem je **20**.</span><span class="sxs-lookup"><span data-stu-id="a35cf-157">The output is **20**.</span></span>


## <a name="abstract-properties"></a><span data-ttu-id="a35cf-158">Abstraktní vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a35cf-158">Abstract Properties</span></span>
<span data-ttu-id="a35cf-159">Vlastnosti mohou být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="a35cf-159">Properties can be abstract.</span></span> <span data-ttu-id="a35cf-160">Stejně jako u metod `abstract` právě znamená, že je virtuální odesílání přidružená vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a35cf-160">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="a35cf-161">Abstraktní vlastnosti mohou být skutečně abstraktní, to znamená, bez definice ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="a35cf-161">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="a35cf-162">Třída, která obsahuje tato vlastnost je proto abstraktní třídu.</span><span class="sxs-lookup"><span data-stu-id="a35cf-162">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="a35cf-163">Abstraktní Alternativně můžete znamenají právě, že je vlastnost virtuální a definice v takovém případě musí být součástí stejné třídy.</span><span class="sxs-lookup"><span data-stu-id="a35cf-163">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="a35cf-164">Všimněte si, že abstraktních a vlastností nesmí být privátní, a pokud jednoho přístupového objektu je abstraktní, dalších také musí být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="a35cf-164">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="a35cf-165">Další informace o abstraktní třídy najdete v tématu [abstraktní třídy](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="a35cf-165">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="a35cf-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="a35cf-166">See Also</span></span>
[<span data-ttu-id="a35cf-167">Členy</span><span class="sxs-lookup"><span data-stu-id="a35cf-167">Members</span></span>](index.md)

[<span data-ttu-id="a35cf-168">Metody</span><span class="sxs-lookup"><span data-stu-id="a35cf-168">Methods</span></span>](methods.md)
