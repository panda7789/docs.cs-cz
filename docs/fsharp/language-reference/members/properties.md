---
title: Vlastnosti (F#)
description: Další informace o F# vlastnosti, které jsou členy, které představují hodnoty přidružené k objektu.
ms.date: 05/16/2016
ms.openlocfilehash: 75d21415b44ccc1c26ef5f478d5f5de20c3412e8
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50197922"
---
# <a name="properties"></a><span data-ttu-id="b4d86-103">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b4d86-103">Properties</span></span>

<span data-ttu-id="b4d86-104">*Vlastnosti* jsou členy, které představují hodnoty přidružené k objektu.</span><span class="sxs-lookup"><span data-stu-id="b4d86-104">*Properties* are members that represent values associated with an object.</span></span>

## <a name="syntax"></a><span data-ttu-id="b4d86-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4d86-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="b4d86-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4d86-106">Remarks</span></span>

<span data-ttu-id="b4d86-107">Vlastnosti představují "má" relace v objektově orientované programování, představující data, která souvisí s instancí objektů nebo statických vlastností s typem.</span><span class="sxs-lookup"><span data-stu-id="b4d86-107">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="b4d86-108">Můžete deklarovat vlastnosti dvěma způsoby v závislosti na tom, jestli chcete explicitně zadat zdrojovou hodnotu (také nazývané záložní úložiště) pro vlastnost, nebo pokud budete chtít povolit kompilátor automaticky generovat záložní úložiště pro vás.</span><span class="sxs-lookup"><span data-stu-id="b4d86-108">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="b4d86-109">Obecně platí měli byste použít více explicitní způsob, pokud má vlastnost nejsou v netriviálních implementace a automatický způsob při vlastnost je stejně jednoduchá obálka pro hodnotu nebo proměnnou.</span><span class="sxs-lookup"><span data-stu-id="b4d86-109">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="b4d86-110">Chcete-li explicitně deklarovat vlastnost, použijte `member` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="b4d86-110">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="b4d86-111">Tato deklarativní syntaxe je následována syntaxi, která určuje, `get` a `set` metody, také s názvem *přistupující objekty*.</span><span class="sxs-lookup"><span data-stu-id="b4d86-111">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="b4d86-112">Různé formy explicitní syntaxe uvedené v části Syntaxe se používají pro vlastnosti jen pro čtení a zápisu jen pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="b4d86-112">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="b4d86-113">Pro vlastnosti jen pro čtení, můžete definovat pouze `get` metoda; pouze pro vlastnosti jen pro zápis, definovat `set` metoda.</span><span class="sxs-lookup"><span data-stu-id="b4d86-113">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="b4d86-114">Všimněte si, že pokud má vlastnost obě `get` a `set` přístupové objekty, alternativní syntaxi vám umožní určit atributy a modifikátory dostupnosti, které se liší pro každý přistupující objekt, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b4d86-114">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="b4d86-115">Pro vlastnosti čtení/zápis, které mají obojí `get` a `set` metody, pořadí `get` a `set` je možné vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="b4d86-115">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="b4d86-116">Alternativně můžete poskytnout tomu syntaxe uvedená pro `get` pouze a syntaxe pro `set` pouze místo kombinované syntaxe.</span><span class="sxs-lookup"><span data-stu-id="b4d86-116">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="b4d86-117">To usnadňuje Odkomentujte jednotlivých `get` nebo `set` metodu, pokud je to něco možná bude potřeba provést.</span><span class="sxs-lookup"><span data-stu-id="b4d86-117">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="b4d86-118">Tuto alternativu k použití kombinované syntaxe se zobrazí v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b4d86-118">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="b4d86-119">Soukromé hodnoty tohoto uchování dat pro vlastnosti se nazývají *zálohování úložišť*.</span><span class="sxs-lookup"><span data-stu-id="b4d86-119">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="b4d86-120">Pokud chcete, aby kompilátor automaticky vytvořit záložní úložiště, pomocí klíčových slov `member val`, vynechejte vlastní identifikátor a pak zadejte výraz k inicializaci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b4d86-120">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="b4d86-121">Pokud je vlastnost má být proměnlivá, obsahovat `with get, set`.</span><span class="sxs-lookup"><span data-stu-id="b4d86-121">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="b4d86-122">Například následující typ třída obsahuje dva automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b4d86-122">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="b4d86-123">`Property1` je jen pro čtení a je inicializován na argumentu poskytnutému metodě primárnímu konstruktoru a `Property2` je nastavitelnou vlastnost inicializovat na prázdný řetězec:</span><span class="sxs-lookup"><span data-stu-id="b4d86-123">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="b4d86-124">Automaticky implementované vlastnosti jsou součástí inicializace typu, takže musí být obsažena před další definice členů stejně jako `let` vazby a `do` vazby v definici typu.</span><span class="sxs-lookup"><span data-stu-id="b4d86-124">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="b4d86-125">Všimněte si, že výraz, který inicializuje automaticky implementovanou vlastnost je vyhodnocen pouze při inicializaci, a ne vždy, když přistupuje k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b4d86-125">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="b4d86-126">Toto chování se liší od chování explicitně implementovaná vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b4d86-126">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="b4d86-127">Co to efektivně znamená, že kód pro inicializaci tyto vlastnosti se přidá do konstruktoru třídy.</span><span class="sxs-lookup"><span data-stu-id="b4d86-127">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="b4d86-128">Vezměte v úvahu následující kód, který ukazuje rozdíl:</span><span class="sxs-lookup"><span data-stu-id="b4d86-128">Consider the following code that shows this difference:</span></span>

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

<span data-ttu-id="b4d86-129">**Output**</span><span class="sxs-lookup"><span data-stu-id="b4d86-129">**Output**</span></span>

```
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="b4d86-130">Výstup předcházejícího kódu ukazuje, že hodnota AutoProperty beze změny při volání opakovaně, že ExplicitProperty změní pokaždé, když je volána.</span><span class="sxs-lookup"><span data-stu-id="b4d86-130">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="b4d86-131">Tento příklad ukazuje, že výraz pro automaticky implementovanou vlastnost není vyhodnocen pokaždé, když, jako je metoda getter pro explicitní vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b4d86-131">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>

>[!WARNING]
<span data-ttu-id="b4d86-132">Existují některé knihovny, jako je například rozhraní Entity Framework (`System.Data.Entity`), které provádí vlastní operace v konstruktory základní třídy, které nefungují dobře v inicializaci automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b4d86-132">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="b4d86-133">V těchto případech použijte explicitní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b4d86-133">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="b4d86-134">Vlastnosti můžou být členy třídy, struktury, rozlišovaná sjednocení, záznamy, rozhraní a rozšíření typu a lze také definovat v objektových výrazech.</span><span class="sxs-lookup"><span data-stu-id="b4d86-134">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="b4d86-135">Atributy lze použít k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b4d86-135">Attributes can be applied to properties.</span></span> <span data-ttu-id="b4d86-136">Použijte atribut na vlastnost, zapisovat atribut na samostatný řádek před vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b4d86-136">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="b4d86-137">Další informace najdete v tématu [atributy](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="b4d86-137">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="b4d86-138">Ve výchozím nastavení jsou veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b4d86-138">By default, properties are public.</span></span> <span data-ttu-id="b4d86-139">Modifikátory dostupnosti lze použít také k vlastnostem.</span><span class="sxs-lookup"><span data-stu-id="b4d86-139">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="b4d86-140">Použít modifikátor přístupnosti, vraťte ho bezprostředně před název vlastnosti, pokud je určená k použití pro obě `get` a `set` metody; přidat před `get` a `set` klíčová slova, pokud je různou přístupností. vyžaduje se pro každý přistupující objekt.</span><span class="sxs-lookup"><span data-stu-id="b4d86-140">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="b4d86-141">*Modifikátor dostupnosti* může být jedna z následujících akcí: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="b4d86-141">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="b4d86-142">Další informace najdete v tématu [řízení přístupu](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="b4d86-142">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="b4d86-143">Implementace vlastnosti provádějí pokaždé, když přistupuje k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b4d86-143">Property implementations are executed each time a property is accessed.</span></span>

## <a name="static-and-instance-properties"></a><span data-ttu-id="b4d86-144">Statické a vlastnosti Instance</span><span class="sxs-lookup"><span data-stu-id="b4d86-144">Static and Instance Properties</span></span>

<span data-ttu-id="b4d86-145">Vlastnosti mohou být statické nebo vlastnosti instance.</span><span class="sxs-lookup"><span data-stu-id="b4d86-145">Properties can be static or instance properties.</span></span> <span data-ttu-id="b4d86-146">Statické vlastnosti může být vyvolána bez instance a používají se pro hodnoty přidružené k typu, nikoli se jednotlivé objekty.</span><span class="sxs-lookup"><span data-stu-id="b4d86-146">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="b4d86-147">Statické vlastnosti vynechejte vlastní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="b4d86-147">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="b4d86-148">Je vyžadován pro vlastnosti instance vlastní identifikátor.</span><span class="sxs-lookup"><span data-stu-id="b4d86-148">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="b4d86-149">Následující definice statickou vlastnost je založena na situaci, ve kterém máte statické pole `myStaticValue` , který je záložní úložiště pro vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b4d86-149">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="b4d86-150">Vlastnosti může být také jako pole, v takovém případě se nazývají *indexovaných vlastností*.</span><span class="sxs-lookup"><span data-stu-id="b4d86-150">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="b4d86-151">Další informace najdete v tématu [indexované vlastnosti](indexed-properties.md).</span><span class="sxs-lookup"><span data-stu-id="b4d86-151">For more information, see [Indexed Properties](indexed-properties.md).</span></span>

## <a name="type-annotation-for-properties"></a><span data-ttu-id="b4d86-152">Anotace typu vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b4d86-152">Type Annotation for Properties</span></span>

<span data-ttu-id="b4d86-153">V mnoha případech kompilátor má dostatek informací k odvození typu vlastnosti z typu záložního úložiště, ale typ můžete explicitně nastavit tak, že přidáte anotaci typu.</span><span class="sxs-lookup"><span data-stu-id="b4d86-153">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="b4d86-154">Pomocí vlastnosti přístupové objekty set</span><span class="sxs-lookup"><span data-stu-id="b4d86-154">Using Property set Accessors</span></span>

<span data-ttu-id="b4d86-155">Můžete nastavit vlastnosti, které poskytují `set` přístupové objekty pomocí `<-` operátor.</span><span class="sxs-lookup"><span data-stu-id="b4d86-155">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="b4d86-156">Výstup je **20**.</span><span class="sxs-lookup"><span data-stu-id="b4d86-156">The output is **20**.</span></span>

## <a name="abstract-properties"></a><span data-ttu-id="b4d86-157">Abstraktní vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b4d86-157">Abstract Properties</span></span>

<span data-ttu-id="b4d86-158">Vlastnosti mohou být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="b4d86-158">Properties can be abstract.</span></span> <span data-ttu-id="b4d86-159">Stejně jako u metod, `abstract` právě znamená, že je virtuální odeslání přidružený k vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b4d86-159">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="b4d86-160">Může být abstraktních a vlastností skutečně abstract, to znamená bez definice ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="b4d86-160">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="b4d86-161">Třída, která obsahuje tato vlastnost je proto abstraktní třídu.</span><span class="sxs-lookup"><span data-stu-id="b4d86-161">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="b4d86-162">Abstraktní Alternativně právě může znamenat, že vlastnost je virtuální a v takovém případě definice musí existovat ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="b4d86-162">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="b4d86-163">Všimněte si, že abstraktních a vlastností nesmí být privátní, a pokud jeden přistupující objekt je abstraktní, ostatní musí také být abstraktní.</span><span class="sxs-lookup"><span data-stu-id="b4d86-163">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="b4d86-164">Další informace o abstraktních tříd naleznete v tématu [abstraktní třídy](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="b4d86-164">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="b4d86-165">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4d86-165">See also</span></span>

- [<span data-ttu-id="b4d86-166">Členové</span><span class="sxs-lookup"><span data-stu-id="b4d86-166">Members</span></span>](index.md)
- [<span data-ttu-id="b4d86-167">Metody</span><span class="sxs-lookup"><span data-stu-id="b4d86-167">Methods</span></span>](methods.md)
