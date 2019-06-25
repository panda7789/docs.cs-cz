---
title: ReadOnly – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 06/21/2018
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 4a51bb0e854de127c632c28f613a7602bf09f432
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67348014"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="68173-102">readonly – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="68173-102">readonly (C# Reference)</span></span>

<span data-ttu-id="68173-103">`readonly` – Klíčové slovo je modifikátor, který je možné ve třech kontextech:</span><span class="sxs-lookup"><span data-stu-id="68173-103">The `readonly` keyword is a modifier that can be used in three contexts:</span></span>

- <span data-ttu-id="68173-104">V [pole deklarace](#readonly-field-example), `readonly` označuje, že přiřazení pro pole může probíhat jenom jako součást deklarace nebo v konstruktoru ve stejné třídě.</span><span class="sxs-lookup"><span data-stu-id="68173-104">In a [field declaration](#readonly-field-example), `readonly` indicates that assignment to the field can only occur as part of the declaration or in a constructor in the same class.</span></span> <span data-ttu-id="68173-105">Pole jen pro čtení může být přiřazena a přiřadit více než jednou v rámci deklarace pole a konstruktor.</span><span class="sxs-lookup"><span data-stu-id="68173-105">A readonly field can be assigned and reassigned multiple times within the field declaration and constructor.</span></span> 
  
  <span data-ttu-id="68173-106">A `readonly` pole nelze přiřadit po ukončení konstruktoru nezachová.</span><span class="sxs-lookup"><span data-stu-id="68173-106">A `readonly` field cannot be assigned after the constructor exits.</span></span> <span data-ttu-id="68173-107">Který má vliv na jiné typy hodnot a odkazové typy:</span><span class="sxs-lookup"><span data-stu-id="68173-107">That has different implications for value types and reference types:</span></span>
  
  - <span data-ttu-id="68173-108">Protože hodnotové typy přímo obsahovat svá data, pole, která je `readonly` hodnotový typ je neměnný.</span><span class="sxs-lookup"><span data-stu-id="68173-108">Because value types directly contain their data, a field that is a  `readonly` value type is immutable.</span></span> 
  - <span data-ttu-id="68173-109">Protože typy odkazů obsahovat odkaz na svá data, pole, to je `readonly` musí typ odkazu vždy odkazovat na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="68173-109">Because reference types contain a reference to their data, a field that is a `readonly` reference type must always refer to the same object.</span></span> <span data-ttu-id="68173-110">Tento objekt je neměnný.</span><span class="sxs-lookup"><span data-stu-id="68173-110">That object is not immutable.</span></span> <span data-ttu-id="68173-111">`readonly` Modifikátor zabraňuje teď nahrazuje jinou instanci typu odkazu pole.</span><span class="sxs-lookup"><span data-stu-id="68173-111">The `readonly` modifier prevents the field from being replaced by a different instance of the reference type.</span></span> <span data-ttu-id="68173-112">Modifikátor však nezabraňuje data instance pole nebylo možné měnit pomocí pole jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="68173-112">However, the modifier does not prevent the instance data of the field from being modified through the read-only field.</span></span>

  > [!WARNING]
  > <span data-ttu-id="68173-113">Externě viditelný typ, který obsahuje externě viditelné pole jen pro čtení, který je proměnlivý odkazový typ může být ohrožení zabezpečení a můžou aktivovat upozornění [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types) : "Nedeklarujte čtení proměnlivé odkazové typy pouze."</span><span class="sxs-lookup"><span data-stu-id="68173-113">An externally visible type that contains an externally visible read-only field that is a mutable reference type may be a security vulnerability and may trigger warning [CA2104](/visualstudio/code-quality/ca2104-do-not-declare-read-only-mutable-reference-types) : "Do not declare read only mutable reference types."</span></span>

- <span data-ttu-id="68173-114">V [ `readonly struct` definice](#readonly-struct-example), `readonly` znamená, že `struct` je neměnný.</span><span class="sxs-lookup"><span data-stu-id="68173-114">In a [`readonly struct` definition](#readonly-struct-example), `readonly` indicates that the `struct` is immutable.</span></span>
- <span data-ttu-id="68173-115">V [ `ref readonly` metoda návratový](#ref-readonly-return-example), `readonly` modifikátor označuje, že metoda vrátí odkaz a zápisu nejsou povoleny na tento odkaz.</span><span class="sxs-lookup"><span data-stu-id="68173-115">In a [`ref readonly` method return](#ref-readonly-return-example), the `readonly` modifier indicates that method returns a reference and writes are not allowed to that reference.</span></span>

<span data-ttu-id="68173-116">Poslední dvě kontexty byly přidány v jazyce C# 7.2.</span><span class="sxs-lookup"><span data-stu-id="68173-116">The final two contexts were added in C# 7.2.</span></span>

## <a name="readonly-field-example"></a><span data-ttu-id="68173-117">Pole určené jen pro čtení, například</span><span class="sxs-lookup"><span data-stu-id="68173-117">Readonly field example</span></span>

<span data-ttu-id="68173-118">V tomto příkladu je hodnota pole `year` nelze změnit v metodě `ChangeYear`, i když je k ní přiřadí hodnota v konstruktoru třídy:</span><span class="sxs-lookup"><span data-stu-id="68173-118">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

<span data-ttu-id="68173-119">Můžete přiřadit hodnoty k `readonly` pouze v následujících kontextů:</span><span class="sxs-lookup"><span data-stu-id="68173-119">You can assign a value to a `readonly` field only in the following contexts:</span></span>

- <span data-ttu-id="68173-120">Pokud je proměnná inicializována v deklaraci, například:</span><span class="sxs-lookup"><span data-stu-id="68173-120">When the variable is initialized in the declaration, for example:</span></span>

  ```csharp
  public readonly int y = 5;
  ```

- <span data-ttu-id="68173-121">V konstruktoru instance třídy, která obsahuje deklaraci pole instance.</span><span class="sxs-lookup"><span data-stu-id="68173-121">In an instance constructor of the class that contains the instance field declaration.</span></span>
- <span data-ttu-id="68173-122">V statický konstruktor třídy, která obsahuje deklaraci statického pole.</span><span class="sxs-lookup"><span data-stu-id="68173-122">In the static constructor of the class that contains the static field declaration.</span></span>

<span data-ttu-id="68173-123">Kontexty konstruktoru jsou také pouze kontextech, ve kterých je možné předat `readonly` jako pole [si](out-parameter-modifier.md) nebo [ref](ref.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="68173-123">These constructor contexts are also the only contexts in which it is valid to pass a `readonly` field as an [out](out-parameter-modifier.md) or [ref](ref.md) parameter.</span></span>

> [!NOTE]
> <span data-ttu-id="68173-124">`readonly` – Klíčové slovo se liší od [const](const.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="68173-124">The `readonly` keyword is different from the [const](const.md) keyword.</span></span> <span data-ttu-id="68173-125">A `const` pole mohou být inicializovány pouze v deklaraci pole.</span><span class="sxs-lookup"><span data-stu-id="68173-125">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="68173-126">A `readonly` pole je možné přiřadit více než jednou v deklaraci pole a jakéhokoli konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="68173-126">A `readonly` field can be assigned multiple times in the field declaration and in any constructor.</span></span> <span data-ttu-id="68173-127">Proto `readonly` pole může mít různé hodnoty v závislosti na použitém konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="68173-127">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="68173-128">Také, zatímco `const` pole je konstantu kompilace `readonly` pole lze použít pro konstanty runtime jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="68173-128">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

<span data-ttu-id="68173-129">V předchozím příkladu, pokud použijete příkaz jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="68173-129">In the preceding example, if you use a statement like the following example:</span></span>

```csharp
p2.y = 66;        // Error
```

<span data-ttu-id="68173-130">Zobrazí se chybová zpráva kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="68173-130">you will get the compiler error message:</span></span>

`A readonly field cannot be assigned to (except in a constructor or a variable initializer)`

## <a name="readonly-struct-example"></a><span data-ttu-id="68173-131">Příklad struktury jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="68173-131">Readonly struct example</span></span>

<span data-ttu-id="68173-132">`readonly` Modifikátor `struct` definice deklaruje, že struktura **neměnné**.</span><span class="sxs-lookup"><span data-stu-id="68173-132">The `readonly` modifier on a `struct` definition declares that the struct is **immutable**.</span></span> <span data-ttu-id="68173-133">Každé pole instance `struct` musí být označen `readonly`, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="68173-133">Every instance field of the `struct` must be marked `readonly`, as shown in the following example:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyStruct)]

<span data-ttu-id="68173-134">V předchozím příkladu [automatické vlastnosti jen pro čtení](../../properties.md#read-only) k deklaraci jeho úložiště.</span><span class="sxs-lookup"><span data-stu-id="68173-134">The preceding example uses [readonly auto properties](../../properties.md#read-only) to declare its storage.</span></span> <span data-ttu-id="68173-135">Který dává pokyn kompilátoru k vytvoření `readonly` pomocná pole pro tyto vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="68173-135">That instructs the compiler to create `readonly` backing fields for those properties.</span></span> <span data-ttu-id="68173-136">Můžete také deklarovat `readonly` přímo pole:</span><span class="sxs-lookup"><span data-stu-id="68173-136">You could also declare `readonly` fields directly:</span></span>

```csharp
public readonly struct Point
{
    public readonly double X;
    public readonly double Y;

    public Point(double x, double y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}
```

<span data-ttu-id="68173-137">Přidání pole nejsou označeny `readonly` vygeneruje Chyba kompilátoru `CS8340`: "Pole instancí struktur jen pro čtení musí být jen pro čtení."</span><span class="sxs-lookup"><span data-stu-id="68173-137">Adding a field not marked `readonly` generates compiler error `CS8340`: "Instance fields of readonly structs must be readonly."</span></span>

## <a name="ref-readonly-return-example"></a><span data-ttu-id="68173-138">Příklad vrácené REF jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="68173-138">Ref readonly return example</span></span>

<span data-ttu-id="68173-139">`readonly` Modifikátor `ref return` označuje, že výsledný odkaz nelze upravit.</span><span class="sxs-lookup"><span data-stu-id="68173-139">The `readonly` modifier on a `ref return` indicates that the returned reference cannot be modified.</span></span> <span data-ttu-id="68173-140">Následující příklad vrátí odkaz na počátku.</span><span class="sxs-lookup"><span data-stu-id="68173-140">The following example returns a reference to the origin.</span></span> <span data-ttu-id="68173-141">Používá `readonly` modifikátor označuje, že volající nelze měnit původu:</span><span class="sxs-lookup"><span data-stu-id="68173-141">It uses the `readonly` modifier to indicate that callers cannot modify the origin:</span></span>

[!code-csharp[readonly struct example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]
<span data-ttu-id="68173-142">Typ vrácený nemusí být `readonly struct`.</span><span class="sxs-lookup"><span data-stu-id="68173-142">The type returned doesn't need to be a `readonly struct`.</span></span> <span data-ttu-id="68173-143">Libovolný typ, který může být vrácen `ref` může být vrácen `ref readonly`.</span><span class="sxs-lookup"><span data-stu-id="68173-143">Any type that can be returned by `ref` can be returned by `ref readonly`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="68173-144">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="68173-144">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="68173-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68173-145">See also</span></span>

- [<span data-ttu-id="68173-146">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="68173-146">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="68173-147">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="68173-147">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="68173-148">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="68173-148">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="68173-149">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="68173-149">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="68173-150">const</span><span class="sxs-lookup"><span data-stu-id="68173-150">const</span></span>](const.md)
- [<span data-ttu-id="68173-151">Pole</span><span class="sxs-lookup"><span data-stu-id="68173-151">Fields</span></span>](../../programming-guide/classes-and-structs/fields.md)
