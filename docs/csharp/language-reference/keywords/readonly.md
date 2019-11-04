---
title: ReadOnly – odkaz C# na klíčové slovo
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 30419200cfce785d7fcbbf59650241580a1f0ce4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73454960"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="437fa-102">readonly – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="437fa-102">readonly (C# Reference)</span></span>

<span data-ttu-id="437fa-103">Klíčové slovo `readonly` je modifikátor, který lze použít ve čtyřech kontextech:</span><span class="sxs-lookup"><span data-stu-id="437fa-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="437fa-104">V [deklaraci pole](#readonly-field-example)`readonly` označuje, že přiřazení k poli může být provedeno pouze jako součást deklarace nebo v konstruktoru ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="437fa-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="437fa-105">Pole jen pro čtení se dá přiřadit a přiřadit vícekrát v rámci deklarace a konstruktoru pole.</span><span class="sxs-lookup"><span data-stu-id="437fa-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span> 
  
  <span data-ttu-id="437fa-106">Po ukončení konstruktoru nelze přiřadit pole `readonly`.</span><span class="sxs-lookup"><span data-stu-id="437fa-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="437fa-107">Toto pravidlo má různé dopady na typy hodnot a typy odkazů:</span><span class="sxs-lookup"><span data-stu-id="437fa-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="437fa-108">Vzhledem k tomu, že typy hodnot přímo obsahují svá data, pole, které je typu `readonly` hodnoty, je neměnné.</span><span class="sxs-lookup"><span data-stu-id="437fa-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span> 
  - <span data-ttu-id="437fa-109">Vzhledem k tomu, že typy odkazů obsahují odkaz na svá data, pole, které je `readonly` odkazový typ, musí vždy odkazovat na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="437fa-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="437fa-110">Tento objekt není neměnný.</span><span class="sxs-lookup"><span data-stu-id="437fa-110">That object isn't immutable.</span></span> <span data-ttu-id="437fa-111">Modifikátor `readonly` zabraňuje tomu, aby se pole nahradilo jinou instancí typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="437fa-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="437fa-112">Modifikátor však nebrání v úpravě dat instance pole v rámci pole jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="437fa-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="437fa-113">Externě viditelný typ, který obsahuje externě viditelné pole jen pro čtení, které je proměnlivým odkazovým typem, může představovat chybu zabezpečení a může aktivovat upozornění [CA2104](/visualstudio/code-quality/ca2104) : "Nedeklarujte pouze proměnlivé odkazy typu jen pro čtení."</span><span class="sxs-lookup"><span data-stu-id="437fa-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="437fa-114">V [definici`readonly struct`](#readonly-struct-example)`readonly` označuje, že `struct` je neměnný.</span><span class="sxs-lookup"><span data-stu-id="437fa-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="437fa-115">V [definici člena`readonly`](#readonly-member-examples)`readonly` označuje, že člen `struct` není obdobou vnitřního stavu struktury.</span><span class="sxs-lookup"><span data-stu-id="437fa-115">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="437fa-116">V [`ref readonly` metoda vrátí](#ref-readonly-return-example)modifikátor `readonly`, že metoda vrátí odkaz a zápisy nejsou pro tento odkaz povoleny.</span><span class="sxs-lookup"><span data-stu-id="437fa-116">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="437fa-117">Do C# 7,2 se přidaly kontexty `readonly struct` a `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="437fa-117">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="437fa-118">členy `readonly` struktury byly přidány v C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="437fa-118">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="437fa-119">Příklad pole jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="437fa-119">Readonly field example</span></span>

<span data-ttu-id="437fa-120">V tomto příkladu nelze hodnotu pole `year` změnit v `ChangeYear`metody, a to i v případě, že je přiřazena hodnota v konstruktoru třídy:</span><span class="sxs-lookup"><span data-stu-id="437fa-120">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="437fa-121">`readonly` poli můžete přiřadit hodnotu pouze v následujících kontextech:</span><span class="sxs-lookup"><span data-stu-id="437fa-121">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="437fa-122">Když je proměnná inicializována v deklaraci, například:</span><span class="sxs-lookup"><span data-stu-id="437fa-122">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="437fa-123">V konstruktoru instance třídy, která obsahuje deklaraci pole instance.</span><span class="sxs-lookup"><span data-stu-id="437fa-123">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="437fa-124">Ve statickém konstruktoru třídy, která obsahuje deklaraci statického pole.</span><span class="sxs-lookup"><span data-stu-id="437fa-124">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="437fa-125">Tyto kontexty konstruktoru jsou také pouze kontexty, ve kterých je platný pro předání pole `readonly` jako parametr [out](out-parameter-modifier.md) nebo [ref](ref.md) .</span><span class="sxs-lookup"><span data-stu-id="437fa-125">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="437fa-126">Klíčové slovo `readonly` se liší od klíčového slova [const](const.md) .</span><span class="sxs-lookup"><span data-stu-id="437fa-126">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="437fa-127">Pole `const` lze inicializovat pouze v deklaraci pole.</span><span class="sxs-lookup"><span data-stu-id="437fa-127">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="437fa-128">Pole `readonly` lze v deklaraci pole a v jakémkoli konstruktoru přiřadit vícekrát.</span><span class="sxs-lookup"><span data-stu-id="437fa-128">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="437fa-129">Proto `readonly` pole mohou mít různé hodnoty v závislosti na použitém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="437fa-129">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="437fa-130">I když `const` pole je konstanta při kompilaci, pole `readonly` lze použít pro konstanty za běhu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="437fa-130">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="437fa-131">V předchozím příkladu, pokud použijete příkaz jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="437fa-131">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="437fa-132">zobrazí se chybová zpráva kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="437fa-132">you'll get the compiler error message:</span></span>

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a><span data-ttu-id="437fa-133">Příklad struktury jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="437fa-133">Readonly struct example</span></span>

<span data-ttu-id="437fa-134">Modifikátor `readonly` v definici `struct` deklaruje, že struktura není **proměnlivá**.</span><span class="sxs-lookup"><span data-stu-id="437fa-134">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="437fa-135">Každé pole instance `struct` musí být označeno `readonly`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="437fa-135">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="437fa-136">Předchozí příklad používá pro deklaraci svého úložiště [Automatické vlastnosti ReadOnly](../../properties.md#read-only) .</span><span class="sxs-lookup"><span data-stu-id="437fa-136">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="437fa-137">Který instruuje kompilátor, aby vytvořil `readonly` pro tyto vlastnosti pole zálohování.</span><span class="sxs-lookup"><span data-stu-id="437fa-137">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="437fa-138">Můžete také deklarovat `readonly` pole přímo:</span><span class="sxs-lookup"><span data-stu-id="437fa-138">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="437fa-139">Přidání pole, které není označeno `readonly` generuje chybu kompilátoru `CS8340`: "pole instancí struktur jen pro čtení musí být jen pro čtení."</span><span class="sxs-lookup"><span data-stu-id="437fa-139">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="437fa-140">Příklady členů jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="437fa-140">Readonly member examples</span></span>

<span data-ttu-id="437fa-141">Jindy můžete vytvořit strukturu, která podporuje mutace.</span><span class="sxs-lookup"><span data-stu-id="437fa-141">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="437fa-142">V těchto případech některé členy instance nejspíš nemění vnitřní stav struktury.</span><span class="sxs-lookup"><span data-stu-id="437fa-142">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="437fa-143">Tyto členy instance můžete deklarovat pomocí modifikátoru `readonly`.</span><span class="sxs-lookup"><span data-stu-id="437fa-143">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="437fa-144">Kompilátor vynutil váš záměr.</span><span class="sxs-lookup"><span data-stu-id="437fa-144">The compiler enforces your intent.</span></span> <span data-ttu-id="437fa-145">Pokud tento člen mění stav přímo nebo přistupuje ke členu, který není deklarován také pomocí modifikátoru `readonly`, výsledkem je chyba při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="437fa-145">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="437fa-146">Modifikátor `readonly` je platný pro členy `struct`, nikoli `class` nebo `interface` deklarace členů.</span><span class="sxs-lookup"><span data-stu-id="437fa-146">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="437fa-147">Pokud použijete modifikátor `readonly` na příslušné `struct` metody, získáte dvě výhody.</span><span class="sxs-lookup"><span data-stu-id="437fa-147">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="437fa-148">Co je nejdůležitější, kompilátor vynutil váš záměr.</span><span class="sxs-lookup"><span data-stu-id="437fa-148">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="437fa-149">Kód, který mění stav, není platný v metodě `readonly`.</span><span class="sxs-lookup"><span data-stu-id="437fa-149">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="437fa-150">Kompilátor může také využít modifikátor `readonly` k povolení optimalizace výkonu.</span><span class="sxs-lookup"><span data-stu-id="437fa-150">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="437fa-151">Pokud jsou typy velkých `struct` předány odkazem `in`, kompilátor musí vygenerovat obrannou linií kopii, pokud je možné změnit stav struktury.</span><span class="sxs-lookup"><span data-stu-id="437fa-151">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="437fa-152">Pokud jsou k dispozici pouze `readonly` členové, kompilátor nemůže vytvořit kopii obrannou linií.</span><span class="sxs-lookup"><span data-stu-id="437fa-152">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="437fa-153">Modifikátor `readonly` je platný pro většinu členů `struct`, včetně metod, které přepíší metody deklarované v <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="437fa-153">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="437fa-154">Existují určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="437fa-154">There are some restrictions:</span></span>

- <span data-ttu-id="437fa-155">Nemůžete deklarovat `readonly` statických členů.</span><span class="sxs-lookup"><span data-stu-id="437fa-155">You can't declare `readonly` static members.</span></span>
- <span data-ttu-id="437fa-156">Nelze deklarovat `readonly` konstruktory.</span><span class="sxs-lookup"><span data-stu-id="437fa-156">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="437fa-157">Můžete přidat modifikátor `readonly` k vlastnosti nebo deklaraci indexeru:</span><span class="sxs-lookup"><span data-stu-id="437fa-157">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="437fa-158">Můžete také přidat modifikátor `readonly` k jednotlivým `get` nebo `set` přistupující objekty vlastnosti nebo indexeru:</span><span class="sxs-lookup"><span data-stu-id="437fa-158">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="437fa-159">Modifikátor `readonly` nemůžete přidat do vlastnosti i do jedné nebo více z těchto přístupových objektů stejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="437fa-159">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="437fa-160">Stejné omezení platí i pro indexery.</span><span class="sxs-lookup"><span data-stu-id="437fa-160">That same restriction applies to indexers.</span></span>

<span data-ttu-id="437fa-161">Kompilátor implicitně aplikuje modifikátor `readonly` na automaticky implementované vlastnosti, kde kód implementovaný kompilátorem nemění stav.</span><span class="sxs-lookup"><span data-stu-id="437fa-161">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="437fa-162">Je ekvivalentem následujících deklarací:</span><span class="sxs-lookup"><span data-stu-id="437fa-162">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
``` 

<span data-ttu-id="437fa-163">V těchto umístěních můžete přidat modifikátor `readonly`, ale nebude mít žádný smysluplný efekt.</span><span class="sxs-lookup"><span data-stu-id="437fa-163">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="437fa-164">Nemůžete přidat modifikátor `readonly` k automatické implementaci vlastnosti setter nebo k automaticky implementované vlastnosti pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="437fa-164">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="437fa-165">Návratový příklad pro odkaz ReadOnly</span><span class="sxs-lookup"><span data-stu-id="437fa-165">Ref readonly return example</span></span>

<span data-ttu-id="437fa-166">Modifikátor `readonly` u `ref return` označuje, že vrácený odkaz nejde upravit.</span><span class="sxs-lookup"><span data-stu-id="437fa-166">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="437fa-167">Následující příklad vrátí odkaz na počátek.</span><span class="sxs-lookup"><span data-stu-id="437fa-167">The following example returns a reference to the origin.</span></span> <span data-ttu-id="437fa-168">Používá modifikátor `readonly` k označení, že volající nemohou upravovat původní:</span><span class="sxs-lookup"><span data-stu-id="437fa-168">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="437fa-169">Vrácený typ nemusí být `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="437fa-169">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="437fa-170">Všechny typy, které mohou být vráceny `ref` mohou být vráceny pomocí `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="437fa-170">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="437fa-171">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="437fa-171">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="437fa-172">Můžete si také prohlédnout návrhy specifikace jazyka:</span><span class="sxs-lookup"><span data-stu-id="437fa-172">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="437fa-173">struktura ReadOnly a ReadOnly</span><span class="sxs-lookup"><span data-stu-id="437fa-173">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="437fa-174">Členové struktury jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="437fa-174">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="437fa-175">Viz také:</span><span class="sxs-lookup"><span data-stu-id="437fa-175">See also</span></span>

- [<span data-ttu-id="437fa-176">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="437fa-176">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="437fa-177">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="437fa-177">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="437fa-178">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="437fa-178">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="437fa-179">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="437fa-179">Modifiers</span></span>](index.md)
- [<span data-ttu-id="437fa-180">const</span><span class="sxs-lookup"><span data-stu-id="437fa-180">const</span></span>](const.md)
- [<span data-ttu-id="437fa-181">Pole</span><span class="sxs-lookup"><span data-stu-id="437fa-181">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
