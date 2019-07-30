---
title: Vlastnosti
description: Přečtěte F# si o vlastnostech, které jsou členy, kteří představují hodnoty přidružené k objektu.
ms.date: 05/16/2016
ms.openlocfilehash: c202927fd0022e042703640cd55fb632c7e36068
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627422"
---
# <a name="properties"></a><span data-ttu-id="c425d-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c425d-103">Properties</span></span>

<span data-ttu-id="c425d-104">*Vlastnosti* jsou členy, které představují hodnoty přidružené k objektu.</span><span class="sxs-lookup"><span data-stu-id="c425d-104">*Properties* are members that represent values associated with an object.</span></span>

## <a name="syntax"></a><span data-ttu-id="c425d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c425d-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="c425d-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c425d-106">Remarks</span></span>

<span data-ttu-id="c425d-107">Vlastnosti představují relaci "má" v objektově orientovaném programování reprezentující data, která jsou přidružena k instancím objektů nebo pro statické vlastnosti s typem.</span><span class="sxs-lookup"><span data-stu-id="c425d-107">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="c425d-108">Vlastnosti lze deklarovat dvěma způsoby v závislosti na tom, zda chcete explicitně zadat základní hodnotu (označovanou také jako záložní úložiště) pro vlastnost, nebo pokud chcete, aby kompilátor pro vás automaticky vygeneroval záložní úložiště.</span><span class="sxs-lookup"><span data-stu-id="c425d-108">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="c425d-109">Obecně byste měli použít explicitní způsob, pokud má vlastnost netriviální implementaci a automatický způsob, pokud je vlastnost pouze jednoduchá obálka pro hodnotu nebo proměnnou.</span><span class="sxs-lookup"><span data-stu-id="c425d-109">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="c425d-110">K deklaraci vlastnosti explicitně použijte `member` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c425d-110">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="c425d-111">Tato deklarativní syntaxe následuje syntaxí, která určuje `get` metody a `set` , také pojmenované *přistupující objekty*.</span><span class="sxs-lookup"><span data-stu-id="c425d-111">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="c425d-112">Různé formuláře explicitní syntaxe zobrazené v oddílu syntax jsou používány pro čtení a zápis, vlastnosti jen pro čtení a pouze pro zápis.</span><span class="sxs-lookup"><span data-stu-id="c425d-112">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="c425d-113">Pro vlastnosti jen pro čtení definujete pouze `get` metodu, pro vlastnosti jen pro zápis definujte `set` pouze metodu.</span><span class="sxs-lookup"><span data-stu-id="c425d-113">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="c425d-114">Všimněte si, že pokud má vlastnost `get` oba `set` i přistupující objekty, alternativní syntaxe vám umožní určit atributy a Modifikátory dostupnosti, které jsou pro každý přistupující objekt rozdílné, jak je uvedeno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c425d-114">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="c425d-115">Pro vlastnosti pro čtení a `get` zápis, které mají `set` `get` metodu a, pořadí a `set` lze obrátit.</span><span class="sxs-lookup"><span data-stu-id="c425d-115">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="c425d-116">Alternativně můžete zadat syntaxi zobrazenou pouze pro `get` a syntaxi zobrazenou pouze pro `set` místo použití kombinované syntaxe.</span><span class="sxs-lookup"><span data-stu-id="c425d-116">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="c425d-117">Díky tomu je snazší komentovat jednotlivec `get` nebo `set` metodu, pokud je to něco, co možná budete muset udělat.</span><span class="sxs-lookup"><span data-stu-id="c425d-117">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="c425d-118">Tato alternativa k použití kombinované syntaxe je uvedena v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="c425d-118">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="c425d-119">Soukromé hodnoty, které uchovávají data pro vlastnosti, se nazývají *záložní úložiště*.</span><span class="sxs-lookup"><span data-stu-id="c425d-119">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="c425d-120">Chcete-li, aby kompilátor vytvořil záložní úložiště automaticky, použijte klíčová slova `member val`, vynechejte identifikátor držitele a potom zadejte výraz pro inicializaci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c425d-120">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="c425d-121">Pokud má být vlastnost proměnlivá, zahrňte `with get, set`.</span><span class="sxs-lookup"><span data-stu-id="c425d-121">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="c425d-122">Například následující typ třídy obsahuje dvě automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c425d-122">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="c425d-123">`Property1`je jen pro čtení a je inicializována na argument poskytnutý primárnímu konstruktoru a `Property2` je nastavitelnou vlastností inicializovaným na prázdný řetězec:</span><span class="sxs-lookup"><span data-stu-id="c425d-123">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="c425d-124">Automaticky implementované vlastnosti jsou součástí inicializace typu, takže musí být zahrnuty před ostatními definicemi členů, stejně jako `let` vazby a `do` vazby v definici typu.</span><span class="sxs-lookup"><span data-stu-id="c425d-124">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="c425d-125">Všimněte si, že výraz, který inicializuje automaticky implementovanou vlastnost, je vyhodnocen pouze při inicializaci, a ne pokaždé, když je vlastnost k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c425d-125">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="c425d-126">Toto chování je v kontrastu s chováním explicitně implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c425d-126">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="c425d-127">To znamená, že kód k inicializaci těchto vlastností je přidán do konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="c425d-127">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="c425d-128">Vezměte v úvahu následující kód, který ukazuje tento rozdíl:</span><span class="sxs-lookup"><span data-stu-id="c425d-128">Consider the following code that shows this difference:</span></span>

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

<span data-ttu-id="c425d-129">**Output**</span><span class="sxs-lookup"><span data-stu-id="c425d-129">**Output**</span></span>

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="c425d-130">Výstup předcházejícího kódu ukazuje, že hodnota autoproperty není při opakovaném volání změněna, zatímco ExplicitProperty se mění pokaždé, když je volána.</span><span class="sxs-lookup"><span data-stu-id="c425d-130">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="c425d-131">To ukazuje, že výraz pro automaticky implementovanou vlastnost není vyhodnocen pokaždé, jak je metoda getter pro vlastnost Explicit.</span><span class="sxs-lookup"><span data-stu-id="c425d-131">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>

>[!WARNING]
><span data-ttu-id="c425d-132">Existují některé knihovny, například Entity Framework (`System.Data.Entity`), které provádějí vlastní operace v konstruktorech základní třídy, které nefungují dobře s inicializací automaticky implementovaných vlastností.</span><span class="sxs-lookup"><span data-stu-id="c425d-132">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="c425d-133">V těchto případech se pokuste použít explicitní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c425d-133">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="c425d-134">Vlastnosti mohou být členy tříd, struktur, rozlišených sjednocení, záznamů, rozhraní a přípon typů a lze také definovat ve výrazech objektů.</span><span class="sxs-lookup"><span data-stu-id="c425d-134">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="c425d-135">Atributy lze použít pro vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c425d-135">Attributes can be applied to properties.</span></span> <span data-ttu-id="c425d-136">Chcete-li použít atribut na vlastnost, napište atribut na samostatném řádku před vlastností.</span><span class="sxs-lookup"><span data-stu-id="c425d-136">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="c425d-137">Další informace najdete v tématu [atributy](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="c425d-137">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="c425d-138">Ve výchozím nastavení jsou vlastnosti veřejné.</span><span class="sxs-lookup"><span data-stu-id="c425d-138">By default, properties are public.</span></span> <span data-ttu-id="c425d-139">Modifikátory dostupnosti lze použít také pro vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c425d-139">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="c425d-140">Chcete-li použít modifikátor přístupnosti, přidejte jej těsně před název vlastnosti, pokud má `get` být použita pro metody a `set` `get` ; přidejte před klíčovým slovem a `set` , pokud je různá přístupnost vyžaduje se pro každý přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="c425d-140">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="c425d-141">*Modifikátor* přístupnosti může být jedna z následujících: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="c425d-141">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="c425d-142">Další informace najdete v tématu [Access Control](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="c425d-142">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="c425d-143">Implementace vlastností jsou spouštěny pokaždé, když je k vlastnosti přistupovaná.</span><span class="sxs-lookup"><span data-stu-id="c425d-143">Property implementations are executed each time a property is accessed.</span></span>

## <a name="static-and-instance-properties"></a><span data-ttu-id="c425d-144">Statické a vlastnosti instance</span><span class="sxs-lookup"><span data-stu-id="c425d-144">Static and Instance Properties</span></span>

<span data-ttu-id="c425d-145">Vlastnosti mohou být statické nebo vlastnosti instance.</span><span class="sxs-lookup"><span data-stu-id="c425d-145">Properties can be static or instance properties.</span></span> <span data-ttu-id="c425d-146">Statické vlastnosti lze vyvolat bez instance a jsou použity pro hodnoty přidružené k typu, nikoli s jednotlivými objekty.</span><span class="sxs-lookup"><span data-stu-id="c425d-146">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="c425d-147">V případě statických vlastností vynechejte identifikátor držitele.</span><span class="sxs-lookup"><span data-stu-id="c425d-147">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="c425d-148">Pro vlastnosti instance je vyžadován samočinný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="c425d-148">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="c425d-149">Následující definice statických vlastností je založena na scénáři, ve kterém máte statické pole `myStaticValue` , které je záložním úložištěm pro danou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c425d-149">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="c425d-150">Vlastnosti mohou být také typu pole. v takovém případě se nazývají *indexované vlastnosti*.</span><span class="sxs-lookup"><span data-stu-id="c425d-150">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="c425d-151">Další informace najdete v tématu [indexované vlastnosti](indexed-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c425d-151">For more information, see [Indexed Properties](indexed-properties.md).</span></span>

## <a name="type-annotation-for-properties"></a><span data-ttu-id="c425d-152">Anotace typu pro vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c425d-152">Type Annotation for Properties</span></span>

<span data-ttu-id="c425d-153">V mnoha případech má kompilátor dostatek informací pro odvození typu vlastnosti z typu záložního úložiště, ale můžete nastavit typ explicitně přidáním anotace typu.</span><span class="sxs-lookup"><span data-stu-id="c425d-153">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="c425d-154">Použití přístupových objektů sady vlastností</span><span class="sxs-lookup"><span data-stu-id="c425d-154">Using Property set Accessors</span></span>

<span data-ttu-id="c425d-155">Můžete nastavit vlastnosti, které poskytují `set` přístupové objekty `<-` pomocí operátoru.</span><span class="sxs-lookup"><span data-stu-id="c425d-155">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="c425d-156">Výstup je **20**.</span><span class="sxs-lookup"><span data-stu-id="c425d-156">The output is **20**.</span></span>

## <a name="abstract-properties"></a><span data-ttu-id="c425d-157">Abstraktní vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c425d-157">Abstract Properties</span></span>

<span data-ttu-id="c425d-158">Vlastnosti mohou být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="c425d-158">Properties can be abstract.</span></span> <span data-ttu-id="c425d-159">Stejně jako u metod `abstract` stačí pouze, když je k této vlastnosti přidruženo virtuální odeslání.</span><span class="sxs-lookup"><span data-stu-id="c425d-159">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="c425d-160">Abstraktní vlastnosti mohou být skutečně abstraktní, to znamená bez definice ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="c425d-160">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="c425d-161">Třída, která obsahuje taková vlastnost, je tedy abstraktní třída.</span><span class="sxs-lookup"><span data-stu-id="c425d-161">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="c425d-162">Alternativně může abstraktní pouze znamenat, že vlastnost je virtuální a v takovém případě musí být definice přítomna ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="c425d-162">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="c425d-163">Všimněte si, že abstraktní vlastnosti nesmí být privátní a pokud je jeden přistupující objekt abstraktní, druhý musí být také abstraktní.</span><span class="sxs-lookup"><span data-stu-id="c425d-163">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="c425d-164">Další informace o abstraktních třídách naleznete v tématu [abstraktní třídy](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="c425d-164">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="c425d-165">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c425d-165">See also</span></span>

- [<span data-ttu-id="c425d-166">Členové</span><span class="sxs-lookup"><span data-stu-id="c425d-166">Members</span></span>](index.md)
- [<span data-ttu-id="c425d-167">Metody</span><span class="sxs-lookup"><span data-stu-id="c425d-167">Methods</span></span>](methods.md)
