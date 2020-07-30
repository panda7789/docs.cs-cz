---
title: Zabalení a rozbalení – Průvodce programováním v C#
description: Přečtěte si o zabalení a rozbalení v programování v jazyce C#. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 5a5bfcc79de8ba3ff66ca8aab9d86d69d89f9221
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380693"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="7a168-104">Zabalení a rozbalení (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="7a168-104">Boxing and Unboxing (C# Programming Guide)</span></span>

<span data-ttu-id="7a168-105">Zabalení je proces převodu [typu hodnoty](../../language-reference/builtin-types/value-types.md) na typ `object` nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7a168-105">Boxing is the process of converting a [value type](../../language-reference/builtin-types/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="7a168-106">Když pole modulu CLR (Common Language Runtime) obsahuje typ hodnoty, zabalí hodnotu uvnitř <xref:System.Object?displayProperty=nameWithType> instance a uloží ji na spravovanou haldu.</span><span class="sxs-lookup"><span data-stu-id="7a168-106">When the common language runtime (CLR) boxes a value type, it wraps the value inside a <xref:System.Object?displayProperty=nameWithType> instance and stores it on the managed heap.</span></span> <span data-ttu-id="7a168-107">Rozbalení extrahuje typ hodnoty z objektu.</span><span class="sxs-lookup"><span data-stu-id="7a168-107">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="7a168-108">Zabalení je implicitní; rozbalení je explicitní.</span><span class="sxs-lookup"><span data-stu-id="7a168-108">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="7a168-109">Pojem zabalení a rozbalení je základem sjednoceného zobrazení systému typů, ve kterém může být hodnota libovolného typu považována za objekt.</span><span class="sxs-lookup"><span data-stu-id="7a168-109">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>

<span data-ttu-id="7a168-110">V následujícím příkladu je proměnná typu Integer `i` *zabalená* a přiřazená objektu `o` .</span><span class="sxs-lookup"><span data-stu-id="7a168-110">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

<span data-ttu-id="7a168-111">Objekt `o` pak může být nezabalený a přiřazený celočíselné proměnné `i` :</span><span class="sxs-lookup"><span data-stu-id="7a168-111">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

<span data-ttu-id="7a168-112">Následující příklady ilustrují, jak se používá zabalení v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="7a168-112">The following examples illustrate how boxing is used in C#.</span></span>

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a><span data-ttu-id="7a168-113">Výkon</span><span class="sxs-lookup"><span data-stu-id="7a168-113">Performance</span></span>

<span data-ttu-id="7a168-114">Ve vztahu k jednoduchým přiřazením se zabalení a rozbalení počítají jako výpočetní náročné procesy.</span><span class="sxs-lookup"><span data-stu-id="7a168-114">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="7a168-115">Když je hodnotový typ v krabici, musí být přidělen a vytvořen nový objekt.</span><span class="sxs-lookup"><span data-stu-id="7a168-115">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="7a168-116">V menší míře je přetypování vyžadované pro rozbalení také nákladné výpočetní.</span><span class="sxs-lookup"><span data-stu-id="7a168-116">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="7a168-117">Další informace najdete v tématu [výkon](../../../framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="7a168-117">For more information, see [Performance](../../../framework/performance/performance-tips.md).</span></span>

## <a name="boxing"></a><span data-ttu-id="7a168-118">Zabalení</span><span class="sxs-lookup"><span data-stu-id="7a168-118">Boxing</span></span>

<span data-ttu-id="7a168-119">Zabalení se používá k ukládání typů hodnot v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7a168-119">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="7a168-120">Zabalení je implicitní převod [typu hodnoty](../../language-reference/builtin-types/value-types.md) na typ `object` nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7a168-120">Boxing is an implicit conversion of a [value type](../../language-reference/builtin-types/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="7a168-121">Zabalení typu hodnoty přiděluje instanci objektu na haldě a zkopíruje hodnotu do nového objektu.</span><span class="sxs-lookup"><span data-stu-id="7a168-121">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>

<span data-ttu-id="7a168-122">Zvažte následující deklaraci proměnné typu hodnoty:</span><span class="sxs-lookup"><span data-stu-id="7a168-122">Consider the following declaration of a value-type variable:</span></span>

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

<span data-ttu-id="7a168-123">Následující příkaz implicitně aplikuje operaci zabalení na proměnnou `i` :</span><span class="sxs-lookup"><span data-stu-id="7a168-123">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

<span data-ttu-id="7a168-124">Výsledek tohoto příkazu vytváří odkaz `o` na objekt v zásobníku, který odkazuje na hodnotu typu `int` , na haldě.</span><span class="sxs-lookup"><span data-stu-id="7a168-124">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="7a168-125">Tato hodnota je kopií hodnoty typu hodnoty přiřazené proměnné `i` .</span><span class="sxs-lookup"><span data-stu-id="7a168-125">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="7a168-126">Rozdíl mezi dvěma proměnnými `i` a `o` , je znázorněno na následujícím obrázku převodu zabalení:</span><span class="sxs-lookup"><span data-stu-id="7a168-126">The difference between the two variables, `i` and `o`, is illustrated in the following image of boxing conversion:</span></span>

![Obrázek znázorňující rozdíl mezi proměnnými i a o.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

<span data-ttu-id="7a168-128">Je také možné provést zabalení explicitně jako v následujícím příkladu, ale explicitní zabalení není nikdy vyžadováno:</span><span class="sxs-lookup"><span data-stu-id="7a168-128">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a><span data-ttu-id="7a168-129">Popis</span><span class="sxs-lookup"><span data-stu-id="7a168-129">Description</span></span>

<span data-ttu-id="7a168-130">Tento příklad převede proměnnou celého čísla `i` na objekt `o` pomocí zabalení.</span><span class="sxs-lookup"><span data-stu-id="7a168-130">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="7a168-131">Pak se hodnota uložená v proměnné `i` změní z `123` na `456` .</span><span class="sxs-lookup"><span data-stu-id="7a168-131">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="7a168-132">Příklad ukazuje, že původní typ hodnoty a zabalený objekt používají oddělené umístění paměti, a proto může ukládat jiné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7a168-132">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>

## <a name="example"></a><span data-ttu-id="7a168-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a168-133">Example</span></span>

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a><span data-ttu-id="7a168-134">Rozbalení</span><span class="sxs-lookup"><span data-stu-id="7a168-134">Unboxing</span></span>

<span data-ttu-id="7a168-135">Rozbalení je explicitní převod z typu `object` na [typ hodnoty](../../language-reference/builtin-types/value-types.md) nebo z typu rozhraní na typ hodnoty, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7a168-135">Unboxing is an explicit conversion from the type `object` to a [value type](../../language-reference/builtin-types/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="7a168-136">Rozbalení operace se skládá z těchto:</span><span class="sxs-lookup"><span data-stu-id="7a168-136">An unboxing operation consists of:</span></span>

- <span data-ttu-id="7a168-137">Kontrola instance objektu, aby se zajistilo, že se jedná o zabalenou hodnotu daného typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7a168-137">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>

- <span data-ttu-id="7a168-138">Zkopírování hodnoty z instance do proměnné typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7a168-138">Copying the value from the instance into the value-type variable.</span></span>

<span data-ttu-id="7a168-139">Následující příkazy ukazují operace zabalení a rozbalení:</span><span class="sxs-lookup"><span data-stu-id="7a168-139">The following statements demonstrate both boxing and unboxing operations:</span></span>

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

<span data-ttu-id="7a168-140">Následující obrázek ukazuje výsledek předchozích příkazů:</span><span class="sxs-lookup"><span data-stu-id="7a168-140">The following figure demonstrates the result of the previous statements:</span></span>

![Obrázek znázorňující převod rozbalení](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

<span data-ttu-id="7a168-142">Pro rozbalení typů hodnot, které mají být v době běhu úspěšné, musí být položka unboxed odkaz na objekt, který byl dříve vytvořen zabalením instance daného typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7a168-142">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="7a168-143">Pokus o unbox `null` způsobí <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="7a168-143">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="7a168-144">Pokus o unbox odkazu na nekompatibilní typ hodnoty způsobí <xref:System.InvalidCastException> .</span><span class="sxs-lookup"><span data-stu-id="7a168-144">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>

## <a name="example"></a><span data-ttu-id="7a168-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a168-145">Example</span></span>

<span data-ttu-id="7a168-146">Následující příklad ukazuje případ neplatného rozbalení a výsledného `InvalidCastException` .</span><span class="sxs-lookup"><span data-stu-id="7a168-146">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="7a168-147">`try`Při použití a se `catch` zobrazí chybová zpráva, když dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="7a168-147">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

<span data-ttu-id="7a168-148">Výstup tohoto programu:</span><span class="sxs-lookup"><span data-stu-id="7a168-148">This program outputs:</span></span>

`Specified cast is not valid. Error: Incorrect unboxing.`

<span data-ttu-id="7a168-149">Pokud změníte příkaz:</span><span class="sxs-lookup"><span data-stu-id="7a168-149">If you change the statement:</span></span>

```csharp
int j = (short) o;
```

<span data-ttu-id="7a168-150">na</span><span class="sxs-lookup"><span data-stu-id="7a168-150">to:</span></span>

```csharp
int j = (int) o;
```

<span data-ttu-id="7a168-151">provede se převod a zobrazí se výstup:</span><span class="sxs-lookup"><span data-stu-id="7a168-151">the conversion will be performed, and you will get the output:</span></span>

`Unboxing OK.`

## <a name="c-language-specification"></a><span data-ttu-id="7a168-152">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7a168-152">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="7a168-153">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a168-153">See also</span></span>

- [<span data-ttu-id="7a168-154">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="7a168-154">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="7a168-155">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="7a168-155">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="7a168-156">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="7a168-156">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
