---
title: klíčové slovo jen pro čtení – odkaz jazyka C#
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 03b0aa63eda3e7a9d8745baaa33479fd5e85b01b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389061"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="1c8a7-102">readonly – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1c8a7-102">readonly (C# Reference)</span></span>

<span data-ttu-id="1c8a7-103">Klíčové `readonly` slovo je modifikátor, který lze použít ve čtyřech kontextech:</span><span class="sxs-lookup"><span data-stu-id="1c8a7-103">The `readonly` keyword is a modifier that can be used in four contexts:</span></span>

- <span data-ttu-id="1c8a7-104">V [deklaraci](#readonly-field-example) `readonly` pole označuje, že přiřazení k poli může nastat pouze jako součást deklarace nebo v konstruktoru ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="1c8a7-105">Pole jen pro čtení lze přiřadit a znovu přiřadit vícekrát v rámci deklarace pole a konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span>
  
  <span data-ttu-id="1c8a7-106">Pole `readonly` nelze přiřadit po ukončení konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-106">A `readonly` field can't be assigned after the constructor exits.</span></span> <span data-ttu-id="1c8a7-107">Toto pravidlo má různé důsledky pro typy hodnot a typy odkazů:</span><span class="sxs-lookup"><span data-stu-id="1c8a7-107">This rule has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="1c8a7-108">Vzhledem k tomu, že typy hodnot `readonly` přímo obsahují jejich data, je pole, které je typem hodnoty, neměnné.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span>
  - <span data-ttu-id="1c8a7-109">Vzhledem k tomu, že typy odkazů obsahují `readonly` odkaz na jejich data, pole, které je typem odkazu, musí vždy odkazovat na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="1c8a7-110">Ten objekt není neměnný.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-110">That object isn't immutable.</span></span> <span data-ttu-id="1c8a7-111">Modifikátor `readonly` zabraňuje nahrazení pole jinou instancí typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="1c8a7-112">Modifikátor však nezabrání změně dat instance pole prostřednictvím pole jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-112">However, the modifier doesn't prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="1c8a7-113">Externě viditelný typ, který obsahuje externě viditelné pole jen pro čtení, které je proměnlivým typem odkazu, může být chybou zabezpečení a může vyvolat upozornění [CA2104](/visualstudio/code-quality/ca2104) : "Nedeklarujte proměnlivé typy odkazů pouze pro čtení."</span><span class="sxs-lookup"><span data-stu-id="1c8a7-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="1c8a7-114">V `readonly struct` definici `readonly` typu označuje, že typ struktury je neměnný.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-114">In a `readonly struct` type definition, `readonly` indicates that the structure type is immutable.</span></span> <span data-ttu-id="1c8a7-115">Další informace naleznete [ `readonly` v](../builtin-types/struct.md#readonly-struct) části struktura [typy struktury](../builtin-types/struct.md) článku.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-115">For more information, see the [`readonly` struct](../builtin-types/struct.md#readonly-struct) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="1c8a7-116">V deklaraci instance člen v `readonly` rámci typu struktury označuje, že člen instance nemění stav struktury.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-116">In an instance member declaration within a structure type, `readonly` indicates that an instance member doesn't modify the state of the structure.</span></span> <span data-ttu-id="1c8a7-117">Další informace naleznete [ `readonly` ](../builtin-types/struct.md#readonly-instance-members) v části členové instance v článku [Typy struktury.](../builtin-types/struct.md)</span><span class="sxs-lookup"><span data-stu-id="1c8a7-117">For more information, see the [`readonly` instance members](../builtin-types/struct.md#readonly-instance-members) section of the [Structure types](../builtin-types/struct.md) article.</span></span>
- <span data-ttu-id="1c8a7-118">V [ `ref readonly` metodě](#ref-readonly-return-example)return `readonly` modifikátor označuje, že metoda vrátí odkaz a zápisy nejsou povoleny pro tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-118">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes aren't allowed to that reference.</span></span>

<span data-ttu-id="1c8a7-119">A `readonly struct` `ref readonly` kontexty byly přidány v C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-119">The `readonly struct` and `ref readonly` contexts were added in C# 7.2.</span></span> <span data-ttu-id="1c8a7-120">`readonly`členové struktury byli přidáni do jazyka C# 8.0</span><span class="sxs-lookup"><span data-stu-id="1c8a7-120">`readonly` struct members were added in C# 8.0</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="1c8a7-121">Příklad pole jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1c8a7-121">Readonly field example</span></span>

<span data-ttu-id="1c8a7-122">V tomto příkladu nelze `year` hodnotu pole změnit v `ChangeYear`metodě , i když je přiřazena hodnota v konstruktoru třídy:</span><span class="sxs-lookup"><span data-stu-id="1c8a7-122">In this example, the value of the field `year` can't be changed in the method `ChangeYear`, even though it's assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="1c8a7-123">Hodnotu `readonly` poli můžete přiřadit pouze v následujících kontextech:</span><span class="sxs-lookup"><span data-stu-id="1c8a7-123">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="1c8a7-124">Když je proměnná inicializována v deklaraci, například:</span><span class="sxs-lookup"><span data-stu-id="1c8a7-124">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="1c8a7-125">V instanci konstruktor třídy, která obsahuje deklaraci pole instance.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-125">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="1c8a7-126">Ve statickém konstruktoru třídy, která obsahuje deklaraci statického pole.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-126">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="1c8a7-127">Tyto kontexty konstruktoru jsou také pouze kontexty, ve `readonly` kterých je platný předat pole jako [out](out-parameter-modifier.md) nebo [ref](ref.md) parametr.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-127">These constructor contexts are also the only contexts in which it's valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="1c8a7-128">Klíčové `readonly` slovo se liší od klíčového slova [const.](const.md)</span><span class="sxs-lookup"><span data-stu-id="1c8a7-128">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="1c8a7-129">Pole `const` lze inicializovat pouze při deklaraci tohoto pole.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-129">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="1c8a7-130">Pole `readonly` lze přiřadit vícekrát v deklaraci pole a v libovolném konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-130">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="1c8a7-131">`readonly` Pole proto mohou mít různé hodnoty v závislosti na použitém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-131">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="1c8a7-132">Také zatímco `const` pole je konstanta v `readonly` době kompilace, pole lze použít pro konstanty za běhu jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1c8a7-132">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for run-time constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="1c8a7-133">V předchozím příkladu, pokud použijete příkaz, jako je následující příklad:</span><span class="sxs-lookup"><span data-stu-id="1c8a7-133">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="1c8a7-134">zobrazí se chybová zpráva kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="1c8a7-134">you'll get the compiler error message:</span></span>

<span data-ttu-id="1c8a7-135">**Pole jen pro čtení nelze přiřadit (s výjimkou konstruktoru nebo proměnné inicializátoru)**</span><span class="sxs-lookup"><span data-stu-id="1c8a7-135">**A readonly field cannot be assigned to (except in a constructor or a variable initializer)**</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="1c8a7-136">Příklad vrácení pouze pro čtení od odkazu</span><span class="sxs-lookup"><span data-stu-id="1c8a7-136">Ref readonly return example</span></span>

<span data-ttu-id="1c8a7-137">Modifikátor `readonly` `ref return` na označuje, že vrácený odkaz nelze změnit.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-137">The `readonly` modifier on a `ref return` indicates that the returned reference can't be modified.</span></span> <span data-ttu-id="1c8a7-138">Následující příklad vrátí odkaz na původ.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-138">The following example returns a reference to the origin.</span></span> <span data-ttu-id="1c8a7-139">Používá `readonly` modifikátor k označení, že volající nelze změnit původ:</span><span class="sxs-lookup"><span data-stu-id="1c8a7-139">It uses the `readonly` modifier to indicate that callers can't modify the origin:</span></span>

[!code-csharp[readonly return example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

<span data-ttu-id="1c8a7-140">Vrácený typ nemusí být `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="1c8a7-140">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="1c8a7-141">Libovolný typ, který `ref` může být `ref readonly`vrácena může být vrácena .</span><span class="sxs-lookup"><span data-stu-id="1c8a7-141">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1c8a7-142">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1c8a7-142">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

<span data-ttu-id="1c8a7-143">Můžete také zobrazit návrhy specifikace jazyka:</span><span class="sxs-lookup"><span data-stu-id="1c8a7-143">You can also see the language specification proposals:</span></span>

- [<span data-ttu-id="1c8a7-144">pouze pro čtení ref a jen pro čtení struct</span><span class="sxs-lookup"><span data-stu-id="1c8a7-144">readonly ref and readonly struct</span></span>](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [<span data-ttu-id="1c8a7-145">jedině pro čtení členové struktury</span><span class="sxs-lookup"><span data-stu-id="1c8a7-145">readonly struct members</span></span>](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a><span data-ttu-id="1c8a7-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c8a7-146">See also</span></span>

- [<span data-ttu-id="1c8a7-147">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1c8a7-147">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1c8a7-148">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1c8a7-148">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1c8a7-149">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="1c8a7-149">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1c8a7-150">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="1c8a7-150">Modifiers</span></span>](index.md)
- [<span data-ttu-id="1c8a7-151">const</span><span class="sxs-lookup"><span data-stu-id="1c8a7-151">const</span></span>](const.md)
- [<span data-ttu-id="1c8a7-152">Pole</span><span class="sxs-lookup"><span data-stu-id="1c8a7-152">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
