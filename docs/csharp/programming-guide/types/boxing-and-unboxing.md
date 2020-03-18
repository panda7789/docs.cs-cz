---
title: Průvodce zabalením a rozbalením – programovací příručka jazyka C#
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 62df08bf4ae3580e9b8d5b3aab0697d396674ca1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76745410"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="36689-102">Zabalení a rozbalení (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="36689-102">Boxing and Unboxing (C# Programming Guide)</span></span>

<span data-ttu-id="36689-103">Zabalení je proces převodu [typu](../../language-reference/builtin-types/value-types.md) hodnoty `object` na typ nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36689-103">Boxing is the process of converting a [value type](../../language-reference/builtin-types/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="36689-104">Když běžný jazyk runtime (CLR) krabice typ hodnoty, zalomí hodnotu uvnitř <xref:System.Object?displayProperty=nameWithType> instance a uloží ji na spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="36689-104">When the common language runtime (CLR) boxes a value type, it wraps the value inside a <xref:System.Object?displayProperty=nameWithType> instance and stores it on the managed heap.</span></span> <span data-ttu-id="36689-105">Rozbalení extrahuje typ hodnoty z objektu.</span><span class="sxs-lookup"><span data-stu-id="36689-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="36689-106">Box je implicitní; rozbalení je explicitní.</span><span class="sxs-lookup"><span data-stu-id="36689-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="36689-107">Koncept zabalení a rozbalení je základem jednotného zobrazení c# systému typů, ve kterém lze hodnotu libovolného typu považovat za objekt.</span><span class="sxs-lookup"><span data-stu-id="36689-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>

<span data-ttu-id="36689-108">V následujícím příkladu je celá `i` proměnná *zabalena* `o`a přiřazena k objektu .</span><span class="sxs-lookup"><span data-stu-id="36689-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>

[!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]

<span data-ttu-id="36689-109">Objekt `o` pak může být unboxed a přiřazené k celé číslo proměnné `i`:</span><span class="sxs-lookup"><span data-stu-id="36689-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]

<span data-ttu-id="36689-110">Následující příklady ilustrují, jak se zabalení používá v c#.</span><span class="sxs-lookup"><span data-stu-id="36689-110">The following examples illustrate how boxing is used in C#.</span></span>

[!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]

## <a name="performance"></a><span data-ttu-id="36689-111">Výkon</span><span class="sxs-lookup"><span data-stu-id="36689-111">Performance</span></span>

<span data-ttu-id="36689-112">Ve vztahu k jednoduchým přiřazením jsou zabalení a rozbalení výpočtově nákladné procesy.</span><span class="sxs-lookup"><span data-stu-id="36689-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="36689-113">Pokud je typ hodnoty zabalen, musí být přidělen a vytvořen nový objekt.</span><span class="sxs-lookup"><span data-stu-id="36689-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="36689-114">V menší míře je obsazení potřebné pro rozbalení také nákladné výpočtově.</span><span class="sxs-lookup"><span data-stu-id="36689-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="36689-115">Další informace naleznete v tématu [Performance](../../../framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="36689-115">For more information, see [Performance](../../../framework/performance/performance-tips.md).</span></span>

## <a name="boxing"></a><span data-ttu-id="36689-116">Zabalení</span><span class="sxs-lookup"><span data-stu-id="36689-116">Boxing</span></span>

<span data-ttu-id="36689-117">Zabalení se používá k ukládání typů hodnot v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="36689-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="36689-118">Zabalení je implicitní převod [typu](../../language-reference/builtin-types/value-types.md) `object` hodnoty na typ nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36689-118">Boxing is an implicit conversion of a [value type](../../language-reference/builtin-types/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="36689-119">Zabalení typu hodnoty přidělí instanci objektu na haldě a zkopíruje hodnotu do nového objektu.</span><span class="sxs-lookup"><span data-stu-id="36689-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>

<span data-ttu-id="36689-120">Zvažte následující deklaraci proměnné typu hodnoty:</span><span class="sxs-lookup"><span data-stu-id="36689-120">Consider the following declaration of a value-type variable:</span></span>

[!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]

<span data-ttu-id="36689-121">Následující příkaz implicitně použije operaci zabalení `i`proměnné :</span><span class="sxs-lookup"><span data-stu-id="36689-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>

[!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]

<span data-ttu-id="36689-122">Výsledkem tohoto příkazu je `o`vytvoření odkazu na objekt , v zásobníku, který odkazuje na hodnotu typu `int`, na haldě.</span><span class="sxs-lookup"><span data-stu-id="36689-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="36689-123">Tato hodnota je kopií hodnoty typu hodnoty přiřazené proměnné `i`.</span><span class="sxs-lookup"><span data-stu-id="36689-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="36689-124">Rozdíl mezi těmito dvěma proměnnými `i` a `o`, je znázorněn na následujícím obrázku převodu zabalení:</span><span class="sxs-lookup"><span data-stu-id="36689-124">The difference between the two variables, `i` and `o`, is illustrated in the following image of boxing conversion:</span></span>

![Obrázek znázorňující rozdíl mezi proměnnými i a o.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)

<span data-ttu-id="36689-126">Je také možné provést zabalení explicitně jako v následujícím příkladu, ale explicitní zabalení není nikdy vyžadováno:</span><span class="sxs-lookup"><span data-stu-id="36689-126">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>

[!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]

## <a name="description"></a><span data-ttu-id="36689-127">Popis</span><span class="sxs-lookup"><span data-stu-id="36689-127">Description</span></span>

<span data-ttu-id="36689-128">Tento příklad převede celou `i` proměnnou `o` na objekt pomocí zabalení.</span><span class="sxs-lookup"><span data-stu-id="36689-128">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="36689-129">Poté se hodnota uložená `i` v `123` proměnné `456`změní z na .</span><span class="sxs-lookup"><span data-stu-id="36689-129">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="36689-130">Příklad ukazuje, že původní typ hodnoty a zabalený objekt používají samostatná umístění paměti, a proto mohou ukládat různé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36689-130">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>

## <a name="example"></a><span data-ttu-id="36689-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="36689-131">Example</span></span>

[!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]

## <a name="unboxing"></a><span data-ttu-id="36689-132">Unboxing</span><span class="sxs-lookup"><span data-stu-id="36689-132">Unboxing</span></span>

<span data-ttu-id="36689-133">Rozbalení je explicitní převod `object` z typu na [typ hodnoty](../../language-reference/builtin-types/value-types.md) nebo z typu rozhraní na typ hodnoty, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="36689-133">Unboxing is an explicit conversion from the type `object` to a [value type](../../language-reference/builtin-types/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="36689-134">Operace rozbalení se skládá z:</span><span class="sxs-lookup"><span data-stu-id="36689-134">An unboxing operation consists of:</span></span>

- <span data-ttu-id="36689-135">Kontrola instance objektu a ujistěte se, že se jedná o zabalenou hodnotu daného typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36689-135">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>

- <span data-ttu-id="36689-136">Kopírování hodnoty z instance do proměnné typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36689-136">Copying the value from the instance into the value-type variable.</span></span>

<span data-ttu-id="36689-137">Následující příkazy ukazují operace zabalení i rozbalení:</span><span class="sxs-lookup"><span data-stu-id="36689-137">The following statements demonstrate both boxing and unboxing operations:</span></span>

[!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]

<span data-ttu-id="36689-138">Následující obrázek ukazuje výsledek předchozích prohlášení:</span><span class="sxs-lookup"><span data-stu-id="36689-138">The following figure demonstrates the result of the previous statements:</span></span>

![Obrázek znázorňující převod rozbalení.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)

<span data-ttu-id="36689-140">Pro unboxing typů hodnot úspěšné za běhu, musí být položka, která je unboxed odkaz na objekt, který byl dříve vytvořen zabalením instance tohoto typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36689-140">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="36689-141">Pokus o zrušení `null` rozesbalení způsobí. <xref:System.NullReferenceException></span><span class="sxs-lookup"><span data-stu-id="36689-141">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="36689-142">Pokus o zrušení pole odkazu na nekompatibilní <xref:System.InvalidCastException>typ hodnoty způsobí, že .</span><span class="sxs-lookup"><span data-stu-id="36689-142">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>

## <a name="example"></a><span data-ttu-id="36689-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="36689-143">Example</span></span>

<span data-ttu-id="36689-144">Následující příklad ukazuje případ neplatné unboxing a `InvalidCastException`výsledné .</span><span class="sxs-lookup"><span data-stu-id="36689-144">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="36689-145">Použití `try` `catch`a , zobrazí se chybová zpráva, když dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="36689-145">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>

[!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]

<span data-ttu-id="36689-146">Tento program vyvodí:</span><span class="sxs-lookup"><span data-stu-id="36689-146">This program outputs:</span></span>

`Specified cast is not valid. Error: Incorrect unboxing.`

<span data-ttu-id="36689-147">Pokud změníte příkaz:</span><span class="sxs-lookup"><span data-stu-id="36689-147">If you change the statement:</span></span>

```csharp
int j = (short) o;
```

<span data-ttu-id="36689-148">na:</span><span class="sxs-lookup"><span data-stu-id="36689-148">to:</span></span>

```csharp
int j = (int) o;
```

<span data-ttu-id="36689-149">konverze bude provedena, a dostanete výstup:</span><span class="sxs-lookup"><span data-stu-id="36689-149">the conversion will be performed, and you will get the output:</span></span>

`Unboxing OK.`

## <a name="c-language-specification"></a><span data-ttu-id="36689-150">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="36689-150">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="36689-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="36689-151">See also</span></span>

- [<span data-ttu-id="36689-152">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="36689-152">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="36689-153">Referenční typy</span><span class="sxs-lookup"><span data-stu-id="36689-153">Reference types</span></span>](../../language-reference/keywords/reference-types.md)
- [<span data-ttu-id="36689-154">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="36689-154">Value types</span></span>](../../language-reference/builtin-types/value-types.md)
