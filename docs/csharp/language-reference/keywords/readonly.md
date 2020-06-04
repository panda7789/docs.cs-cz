---
title: ReadOnly – klíčové slovo – Reference jazyka C#
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 66a096e8831f72a2216e8ba5dd9866046504624f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368618"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="588b8-102">readonly – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="588b8-102">readonly (C# Reference)</span></span>

<span data-ttu-id="588b8-103">`readonly`Klíčové slovo je modifikátor, který lze použít ve čtyřech kontextech:</span><span class="sxs-lookup"><span data-stu-id="588b8-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="588b8-104">V [deklaraci pole](#readonly-field-example) `readonly` označuje, že přiřazení k poli může být provedeno pouze v rámci deklarace nebo v konstruktoru ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="588b8-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="588b8-105">Pole jen pro čtení se dá přiřadit a přiřadit vícekrát v rámci deklarace a konstruktoru pole.</span><span class="sxs-lookup"><span data-stu-id="588b8-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="588b8-106">`readonly`Po ukončení konstruktoru nelze pole přiřadit.</span><span class="sxs-lookup"><span data-stu-id="588b8-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="588b8-107">Toto pravidlo má různé dopady na typy hodnot a typy odkazů:</span><span class="sxs-lookup"><span data-stu-id="588b8-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="588b8-108">Vzhledem k tomu, že typy hodnot přímo obsahují svá data, pole, které je `readonly` hodnotový typ, je neměnné.</span><span class="sxs-lookup"><span data-stu-id="588b8-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="588b8-109">Vzhledem k tomu, že typy odkazů obsahují odkaz na jejich data, pole, které je `readonly` odkazový typ, musí vždy odkazovat na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="588b8-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="588b8-110">Tento objekt není neměnný.</span><span class="sxs-lookup"><span data-stu-id="588b8-110">That object isn't immutable.</span></span> <span data-ttu-id="588b8-111">`readonly`Modifikátor zabraňuje tomu, aby bylo pole nahrazeno jinou instancí typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="588b8-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="588b8-112">Modifikátor však nebrání v úpravě dat instance pole v rámci pole jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="588b8-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="588b8-113">Externě viditelný typ, který obsahuje externě viditelné pole jen pro čtení, které je proměnlivým odkazovým typem, může představovat chybu zabezpečení a může aktivovat upozornění [CA2104](/visualstudio/code-quality/ca2104) : "Nedeklarujte pouze proměnlivé odkazy typu jen pro čtení."</span><span class="sxs-lookup"><span data-stu-id="588b8-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="588b8-114">V `readonly struct` definici typu `readonly` označuje, že typ struktury je neměnný.</span><span class="sxs-lookup"><span data-stu-id="588b8-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="588b8-115">Další informace naleznete [ `readonly` v části struktura v článku](../builtin-types/struct.md#readonly-struct) [typy struktury](../builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="588b8-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="588b8-116">V deklaraci člena instance v rámci typu struktury `readonly` označuje, že člen instance neupravuje stav struktury.</span><span class="sxs-lookup"><span data-stu-id="588b8-116">In an instance member declaration within a structure type, `readonly` indicates that an instance member doesn't modify the state of the structure.</span></span> <span data-ttu-id="588b8-117">Další informace naleznete v oddílu [ `readonly` instance členů](../builtin-types/struct.md#readonly-instance-members) článku [typy struktury](../builtin-types/struct.md) .</span><span class="sxs-lookup"><span data-stu-id="588b8-117">For more information, see the [`readonly` instance members](../builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="588b8-118">V [ `ref readonly` metodě se vrátí](#ref-readonly-return-example) `readonly` modifikátor, že metoda vrátí odkaz a zápisy nejsou pro tento odkaz povoleny.</span><span class="sxs-lookup"><span data-stu-id="588b8-118">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="588b8-119">`readonly struct` `ref readonly` Kontexty a byly přidány v C# 7,2.</span><span class="sxs-lookup"><span data-stu-id="588b8-119">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="588b8-120">`readonly`Členy struktury se přidaly v C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="588b8-120">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="588b8-121">Příklad pole jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="588b8-121">Readonly field example</span></span>

<span data-ttu-id="588b8-122">V tomto příkladu `year` nemůže být hodnota pole v metodě změněna `ChangeYear` , i když je přiřazena hodnota v konstruktoru třídy:</span><span class="sxs-lookup"><span data-stu-id="588b8-122">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](snippets/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="588b8-123">K poli můžete přiřadit hodnotu `readonly` pouze v následujících kontextech:</span><span class="sxs-lookup"><span data-stu-id="588b8-123">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="588b8-124">Když je proměnná inicializována v deklaraci, například:</span><span class="sxs-lookup"><span data-stu-id="588b8-124">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="588b8-125">V konstruktoru instance třídy, která obsahuje deklaraci pole instance.</span><span class="sxs-lookup"><span data-stu-id="588b8-125">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="588b8-126">Ve statickém konstruktoru třídy, která obsahuje deklaraci statického pole.</span><span class="sxs-lookup"><span data-stu-id="588b8-126">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="588b8-127">Tyto kontexty konstruktoru jsou také pouze kontexty, ve kterých je platný pro předání `readonly` pole jako [výstupní](out-parameter-modifier.md) parametr nebo parametr [ref](ref.md) .</span><span class="sxs-lookup"><span data-stu-id="588b8-127">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="588b8-128">`readonly`Klíčové slovo se liší od klíčového slova [const](const.md) .</span><span class="sxs-lookup"><span data-stu-id="588b8-128">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="588b8-129">`const`Pole lze inicializovat pouze v deklaraci pole.</span><span class="sxs-lookup"><span data-stu-id="588b8-129">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="588b8-130">`readonly`Pole lze přiřadit vícekrát v deklaraci pole a v jakémkoli konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="588b8-130">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="588b8-131">Proto `readonly` pole mohou mít různé hodnoty v závislosti na použitém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="588b8-131">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="588b8-132">I když `const` je pole konstanta při kompilaci, `readonly` pole lze použít pro konstanty run-time, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="588b8-132">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](snippets/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="588b8-133">V předchozím příkladu, pokud použijete příkaz jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="588b8-133">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="588b8-134">zobrazí se chybová zpráva kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="588b8-134">you'll get the compiler error message:</span></span>

<span data-ttu-id="588b8-135">**K poli jen pro čtení se nedá přiřadit (kromě případu, kdy se nachází v konstruktoru nebo inicializátoru proměnné).**</span><span class="sxs-lookup"><span data-stu-id="588b8-135">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="588b8-136">Návratový příklad pro odkaz ReadOnly</span><span class="sxs-lookup"><span data-stu-id="588b8-136">Ref readonly return example</span></span>

<span data-ttu-id="588b8-137">`readonly`Modifikátor na pozici `ref return` označuje, že vrácený odkaz nelze upravit.</span><span class="sxs-lookup"><span data-stu-id="588b8-137">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="588b8-138">Následující příklad vrátí odkaz na počátek.</span><span class="sxs-lookup"><span data-stu-id="588b8-138">The following example returns a reference to the origin.</span></span> <span data-ttu-id="588b8-139">Používá `readonly` Modifikátor k označení, že volající nemohou změnit původní:</span><span class="sxs-lookup"><span data-stu-id="588b8-139">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly return example](snippets/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="588b8-140">Vrácený typ nemusí být `readonly struct` .</span><span class="sxs-lookup"><span data-stu-id="588b8-140">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="588b8-141">Libovolný typ, který může být vrácen pomocí, `ref` může být vrácen `ref readonly` .</span><span class="sxs-lookup"><span data-stu-id="588b8-141">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="588b8-142">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="588b8-142">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="588b8-143">Můžete si také prohlédnout návrhy specifikace jazyka:</span><span class="sxs-lookup"><span data-stu-id="588b8-143">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="588b8-144">struktura ReadOnly a ReadOnly</span><span class="sxs-lookup"><span data-stu-id="588b8-144">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="588b8-145">Členové struktury jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="588b8-145">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="588b8-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="588b8-146">See also</span></span>

- [<span data-ttu-id="588b8-147">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="588b8-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="588b8-148">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="588b8-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="588b8-149">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="588b8-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="588b8-150">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="588b8-150">Modifiers</span></span>](index.md)
- [<span data-ttu-id="588b8-151">const</span><span class="sxs-lookup"><span data-stu-id="588b8-151">const</span></span>](const.md)
- [<span data-ttu-id="588b8-152">Pole</span><span class="sxs-lookup"><span data-stu-id="588b8-152">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
