---
title: klíčové slovo jen pro čtení – odkaz jazyka C#
ms.date: 03/26/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 344d5e54fcd500e283c52fa7953c6366823f13f0
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345153"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="c7697-102">readonly – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c7697-102">readonly (C# Reference)</span></span>

<span data-ttu-id="c7697-103">Klíčové `readonly` slovo je modifikátor, který lze použít ve čtyřech kontextech:</span><span class="sxs-lookup"><span data-stu-id="c7697-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="c7697-104">V [deklaraci](#readonly-field-example) `readonly` pole označuje, že přiřazení k poli může nastat pouze jako součást deklarace nebo v konstruktoru ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="c7697-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="c7697-105">Pole jen pro čtení lze přiřadit a znovu přiřadit vícekrát v rámci deklarace pole a konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c7697-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="c7697-106">Pole `readonly` nelze přiřadit po ukončení konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c7697-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="c7697-107">Toto pravidlo má různé důsledky pro typy hodnot a typy odkazů:</span><span class="sxs-lookup"><span data-stu-id="c7697-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="c7697-108">Vzhledem k tomu, že typy hodnot `readonly` přímo obsahují jejich data, je pole, které je typem hodnoty, neměnné.</span><span class="sxs-lookup"><span data-stu-id="c7697-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="c7697-109">Vzhledem k tomu, že typy odkazů obsahují `readonly` odkaz na jejich data, pole, které je typem odkazu, musí vždy odkazovat na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="c7697-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="c7697-110">Ten objekt není neměnný.</span><span class="sxs-lookup"><span data-stu-id="c7697-110">That object isn't immutable.</span></span> <span data-ttu-id="c7697-111">Modifikátor `readonly` zabraňuje nahrazení pole jinou instancí typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="c7697-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="c7697-112">Modifikátor však nezabrání změně dat instance pole prostřednictvím pole jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="c7697-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="c7697-113">Externě viditelný typ, který obsahuje externě viditelné pole jen pro čtení, které je proměnlivým typem odkazu, může být chybou zabezpečení a může vyvolat upozornění [CA2104](/visualstudio/code-quality/ca2104) : "Nedeklarujte proměnlivé typy odkazů pouze pro čtení."</span><span class="sxs-lookup"><span data-stu-id="c7697-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="c7697-114">V `readonly struct` definici `readonly` typu označuje, že typ struktury je neměnný.</span><span class="sxs-lookup"><span data-stu-id="c7697-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="c7697-115">Další informace naleznete [ `readonly` v](../builtin-types/struct.md#readonly-struct) části struktura [typy struktury](../builtin-types/struct.md) článku.</span><span class="sxs-lookup"><span data-stu-id="c7697-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="c7697-116">V [ `readonly` definici](#readonly-member-examples) `readonly` člena označuje, že `struct` člen člena struktury vnitřní stav.</span><span class="sxs-lookup"><span data-stu-id="c7697-116">In a [`readonly` member definition](#readonly-member-examples), `readonly` indicates that a member of a `struct` doesn't mutate the struct's internal state.</span></span>
- <span data-ttu-id="c7697-117">V [ `ref readonly` metodě](#ref-readonly-return-example)return `readonly` modifikátor označuje, že metoda vrátí odkaz a zápisy nejsou povoleny pro tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="c7697-117">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="c7697-118">A `readonly struct` `ref readonly` kontexty byly přidány v C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="c7697-118">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="c7697-119">`readonly`členové struktury byli přidáni do jazyka C# 8.0</span><span class="sxs-lookup"><span data-stu-id="c7697-119">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="c7697-120">Příklad pole jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c7697-120">Readonly field example</span></span>

<span data-ttu-id="c7697-121">V tomto příkladu nelze `year` hodnotu pole změnit v `ChangeYear`metodě , i když je přiřazena hodnota v konstruktoru třídy:</span><span class="sxs-lookup"><span data-stu-id="c7697-121">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="c7697-122">Hodnotu `readonly` poli můžete přiřadit pouze v následujících kontextech:</span><span class="sxs-lookup"><span data-stu-id="c7697-122">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="c7697-123">Když je proměnná inicializována v deklaraci, například:</span><span class="sxs-lookup"><span data-stu-id="c7697-123">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="c7697-124">V instanci konstruktor třídy, která obsahuje deklaraci pole instance.</span><span class="sxs-lookup"><span data-stu-id="c7697-124">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="c7697-125">Ve statickém konstruktoru třídy, která obsahuje deklaraci statického pole.</span><span class="sxs-lookup"><span data-stu-id="c7697-125">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="c7697-126">Tyto kontexty konstruktoru jsou také pouze kontexty, ve `readonly` kterých je platný předat pole jako [out](out-parameter-modifier.md) nebo [ref](ref.md) parametr.</span><span class="sxs-lookup"><span data-stu-id="c7697-126">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="c7697-127">Klíčové `readonly` slovo se liší od klíčového slova [const.](const.md)</span><span class="sxs-lookup"><span data-stu-id="c7697-127">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="c7697-128">Pole `const` lze inicializovat pouze při deklaraci tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="c7697-128">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="c7697-129">Pole `readonly` lze přiřadit vícekrát v deklaraci pole a v libovolném konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c7697-129">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="c7697-130">`readonly` Pole proto mohou mít různé hodnoty v závislosti na použitém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c7697-130">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="c7697-131">Také zatímco `const` pole je konstanta v `readonly` době kompilace, pole lze použít pro konstanty za běhu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c7697-131">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="c7697-132">V předchozím příkladu, pokud použijete příkaz, jako je následující příklad:</span><span class="sxs-lookup"><span data-stu-id="c7697-132">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="c7697-133">zobrazí se chybová zpráva kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="c7697-133">you'll get the compiler error message:</span></span>

<span data-ttu-id="c7697-134">**Pole jen pro čtení nelze přiřadit (s výjimkou konstruktoru nebo proměnné inicializátoru)**</span><span class="sxs-lookup"><span data-stu-id="c7697-134">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="readonly-member-examples"></a><span data-ttu-id="c7697-135">Příklady členů pouze pro Čtení</span><span class="sxs-lookup"><span data-stu-id="c7697-135">Readonly member examples</span></span>

<span data-ttu-id="c7697-136">Jindy můžete vytvořit strukturu, která podporuje mutaci.</span><span class="sxs-lookup"><span data-stu-id="c7697-136">Other times, you may create a struct that supports mutation.</span></span> <span data-ttu-id="c7697-137">V těchto případech několik členů instance pravděpodobně nezmění vnitřní stav struktury.</span><span class="sxs-lookup"><span data-stu-id="c7697-137">In those cases, several of the instance members likely won't modify the internal state of the struct.</span></span> <span data-ttu-id="c7697-138">Tyto členy instance můžete `readonly` deklarovat pomocí modifikátoru.</span><span class="sxs-lookup"><span data-stu-id="c7697-138">You can declare those instance members with the `readonly` modifier.</span></span> <span data-ttu-id="c7697-139">Kompilátor vynucuje váš záměr.</span><span class="sxs-lookup"><span data-stu-id="c7697-139">The compiler enforces your intent.</span></span> <span data-ttu-id="c7697-140">Pokud tento člen upraví stav přímo nebo přistupuje k `readonly` členu, který není také deklarován s modifikátorem, výsledkem je chyba v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="c7697-140">If that member modifies state directly or accesses a member that isn't also declared with the `readonly` modifier, the result is a compile-time error.</span></span> <span data-ttu-id="c7697-141">Modifikátor `readonly` je `struct` platný `class` pro `interface` členy, nikoli nebo deklarace členů.</span><span class="sxs-lookup"><span data-stu-id="c7697-141">The `readonly` modifier is valid on `struct` members, not `class` or `interface` member declarations.</span></span>

<span data-ttu-id="c7697-142">Můžete získat dvě výhody `readonly` použitím modifikátoru na příslušné `struct` metody.</span><span class="sxs-lookup"><span data-stu-id="c7697-142">You gain two advantages by applying the `readonly` modifier to applicable `struct` methods.</span></span> <span data-ttu-id="c7697-143">A co je nejdůležitější, kompilátor vynucuje váš záměr.</span><span class="sxs-lookup"><span data-stu-id="c7697-143">Most importantly, the compiler enforces your intent.</span></span> <span data-ttu-id="c7697-144">Kód, který upravuje stav není platný `readonly` v metodě.</span><span class="sxs-lookup"><span data-stu-id="c7697-144">Code that modifies state isn't valid in a `readonly` method.</span></span> <span data-ttu-id="c7697-145">Kompilátor může také použít `readonly` modifikátor povolit optimalizace výkonu.</span><span class="sxs-lookup"><span data-stu-id="c7697-145">The compiler may also make use of the `readonly` modifier to enable performance optimizations.</span></span> <span data-ttu-id="c7697-146">Při `struct` velké typy `in` jsou předány odkazem, kompilátor musí generovat obrannou kopii, pokud stav struktury může být změněn.</span><span class="sxs-lookup"><span data-stu-id="c7697-146">When large `struct` types are passed by `in` reference, the compiler must generate a defensive copy if the state of the struct might be modified.</span></span> <span data-ttu-id="c7697-147">Pokud `readonly` jsou přístupné pouze členy, kompilátor nemusí vytvořit obrannou kopii.</span><span class="sxs-lookup"><span data-stu-id="c7697-147">If only `readonly` members are accessed, the compiler may not create the defensive copy.</span></span>

<span data-ttu-id="c7697-148">Modifikátor `readonly` je platný pro `struct`většinu členů , včetně <xref:System.Object?displayProperty=nameWithType>metod, které přepsat metody deklarované v .</span><span class="sxs-lookup"><span data-stu-id="c7697-148">The `readonly` modifier is valid on most members of a `struct`, including methods that override methods declared in <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c7697-149">Existují určitá omezení:</span><span class="sxs-lookup"><span data-stu-id="c7697-149">There are some restrictions:</span></span>

- <span data-ttu-id="c7697-150">Nelze deklarovat `readonly` statické metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c7697-150">You can't declare `readonly` static methods or properties.</span></span>
- <span data-ttu-id="c7697-151">Nelze deklarovat `readonly` konstruktory.</span><span class="sxs-lookup"><span data-stu-id="c7697-151">You can't declare `readonly` constructors.</span></span>

<span data-ttu-id="c7697-152">`readonly` Modifikátor můžete přidat do deklarace vlastnosti nebo indexeru:</span><span class="sxs-lookup"><span data-stu-id="c7697-152">You can add the `readonly` modifier to a property or indexer declaration:</span></span>

```csharp
readonly public int Counter
{
  get { return 0; }
  set {} // not useful, but legal
}
```

<span data-ttu-id="c7697-153">Můžete také přidat `readonly` modifikátor pro jednotlivé `get` nebo `set` přistupující objekty vlastnosti nebo indexeru:</span><span class="sxs-lookup"><span data-stu-id="c7697-153">You may also add the `readonly` modifier to individual `get` or `set` accessors of a property or indexer:</span></span>

```csharp
public int Counter
{
  readonly get { return _counter; }
  set { _counter = value; }
}
int _counter;
```

<span data-ttu-id="c7697-154">`readonly` Modifikátor nesmíte přidat do vlastnosti a jednoho nebo více přístupových objektů stejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c7697-154">You may not add the `readonly` modifier to both a property and one or more of that same property's accessors.</span></span> <span data-ttu-id="c7697-155">Stejné omezení platí pro indexery.</span><span class="sxs-lookup"><span data-stu-id="c7697-155">That same restriction applies to indexers.</span></span>

<span data-ttu-id="c7697-156">Kompilátor implicitně použije `readonly` modifikátor na automaticky implementované vlastnosti, kde kompilátor implementovaný kód nemění stav.</span><span class="sxs-lookup"><span data-stu-id="c7697-156">The compiler implicitly applies the `readonly` modifier to auto-implemented properties where the compiler implemented code doesn't modify state.</span></span> <span data-ttu-id="c7697-157">Je to ekvivalentní následujícím prohlášením:</span><span class="sxs-lookup"><span data-stu-id="c7697-157">It's equivalent to the following declarations:</span></span>

```csharp
public readonly int Index { get; }
// Or:
public int Number { readonly get; }
public string Message { readonly get; set; }
```

<span data-ttu-id="c7697-158">`readonly` Modifikátor můžete přidat v těchto umístěních, ale nebude mít žádný smysluplný účinek.</span><span class="sxs-lookup"><span data-stu-id="c7697-158">You may add the `readonly` modifier in those locations, but it will have no meaningful effect.</span></span> <span data-ttu-id="c7697-159">`readonly` Modifikátor nesmíte přidat do automaticky implementovaného nastavení vlastností nebo do automaticky implementované vlastnosti pro čtení a zápis.</span><span class="sxs-lookup"><span data-stu-id="c7697-159">You may not add the `readonly` modifier to an auto-implemented property setter, or to a read/write auto-implemented property.</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="c7697-160">Příklad vrácení pouze pro čtení od odkazu</span><span class="sxs-lookup"><span data-stu-id="c7697-160">Ref readonly return example</span></span>

<span data-ttu-id="c7697-161">Modifikátor `readonly` `ref return` na označuje, že vrácený odkaz nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="c7697-161">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="c7697-162">Následující příklad vrátí odkaz na původ.</span><span class="sxs-lookup"><span data-stu-id="c7697-162">The following example returns a reference to the origin.</span></span> <span data-ttu-id="c7697-163">Používá `readonly` modifikátor k označení, že volající nelze změnit původ:</span><span class="sxs-lookup"><span data-stu-id="c7697-163">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="c7697-164">Vrácený typ nemusí být `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="c7697-164">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="c7697-165">Libovolný typ, který `ref` může být `ref readonly`vrácena může být vrácena .</span><span class="sxs-lookup"><span data-stu-id="c7697-165">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c7697-166">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c7697-166">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="c7697-167">Můžete také zobrazit návrhy specifikace jazyka:</span><span class="sxs-lookup"><span data-stu-id="c7697-167">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="c7697-168">pouze pro čtení ref a jen pro čtení struct</span><span class="sxs-lookup"><span data-stu-id="c7697-168">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="c7697-169">jedině pro čtení členové struktury</span><span class="sxs-lookup"><span data-stu-id="c7697-169">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="c7697-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7697-170">See also</span></span>

- [<span data-ttu-id="c7697-171">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c7697-171">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c7697-172">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c7697-172">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c7697-173">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="c7697-173">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c7697-174">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="c7697-174">Modifiers</span></span>](index.md)
- [<span data-ttu-id="c7697-175">const</span><span class="sxs-lookup"><span data-stu-id="c7697-175">const</span></span>](const.md)
- [<span data-ttu-id="c7697-176">Pole</span><span class="sxs-lookup"><span data-stu-id="c7697-176">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
