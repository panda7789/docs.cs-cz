---
title: Zabalení a rozbalení (Průvodce programováním v C#)
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: eff5f05aa8b5081069b9e0f2f5f152669afaea18
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208355"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="67f7b-102">Zabalení a rozbalení (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="67f7b-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="67f7b-103">Zabalení je proces převodu [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) typu `object` nebo k libovolnému typu rozhraní implementované tento typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="67f7b-103">Boxing is the process of converting a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="67f7b-104">Když modulu CLR oknech typ hodnoty, zabalí hodnotu uvnitř System.Object a uloží je v spravovaná halda.</span><span class="sxs-lookup"><span data-stu-id="67f7b-104">When the CLR boxes a value type, it wraps the value inside a System.Object and stores it on the managed heap.</span></span> <span data-ttu-id="67f7b-105">Rozbalení extrahuje typ hodnoty z objektu.</span><span class="sxs-lookup"><span data-stu-id="67f7b-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="67f7b-106">Zabalení je implicitní; Rozbalení je explicitní.</span><span class="sxs-lookup"><span data-stu-id="67f7b-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="67f7b-107">Koncept zabalení a rozbalení základem zobrazení jazyka C# unified typ systému, ve kterém lze hodnotu libovolného typu zacházet jako objekt.</span><span class="sxs-lookup"><span data-stu-id="67f7b-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="67f7b-108">V následujícím příkladu, proměnná s celým číslem `i` je *do pole* a přiřazené k objektu `o`.</span><span class="sxs-lookup"><span data-stu-id="67f7b-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#14](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_1.cs)]  
  
 <span data-ttu-id="67f7b-109">Objekt `o` lze poté nezabalený a přiřazená proměnná s celým číslem `i`:</span><span class="sxs-lookup"><span data-stu-id="67f7b-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#15](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_2.cs)]  
  
 <span data-ttu-id="67f7b-110">Následující příklady ilustrují použití zabalení v C#.</span><span class="sxs-lookup"><span data-stu-id="67f7b-110">The following examples illustrate how boxing is used in C#.</span></span>  
  
 [!code-csharp[csProgGuideTypes#47](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_3.cs)]  
  
## <a name="performance"></a><span data-ttu-id="67f7b-111">Výkon</span><span class="sxs-lookup"><span data-stu-id="67f7b-111">Performance</span></span>  
 <span data-ttu-id="67f7b-112">Ve vztahu k jednoduché přiřazení zabalení a rozbalení jsou náročné procesy.</span><span class="sxs-lookup"><span data-stu-id="67f7b-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="67f7b-113">Pokud je do pole zadejte hodnotu, musí být nový objekt přidělené a zkonstruovat.</span><span class="sxs-lookup"><span data-stu-id="67f7b-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="67f7b-114">V menší míře přetypování požadované pro rozbalení je také nákladné u.</span><span class="sxs-lookup"><span data-stu-id="67f7b-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="67f7b-115">Další informace najdete v tématu [výkonu](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).</span><span class="sxs-lookup"><span data-stu-id="67f7b-115">For more information, see [Performance](https://msdn.microsoft.com/library/ms173196(VS.110).aspx).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="67f7b-116">Zabalení</span><span class="sxs-lookup"><span data-stu-id="67f7b-116">Boxing</span></span>  
 <span data-ttu-id="67f7b-117">Zabalení slouží k uložení hodnotové typy v haldě uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="67f7b-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="67f7b-118">Zabalení je implicitní převod [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) typu `object` nebo k libovolnému typu rozhraní implementované tento typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="67f7b-118">Boxing is an implicit conversion of a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="67f7b-119">Zabalení typu hodnoty přiděluje instanci objektu v haldě a hodnota zkopírována do nového objektu.</span><span class="sxs-lookup"><span data-stu-id="67f7b-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="67f7b-120">Vezměte v úvahu následující deklaraci typu hodnoty proměnné:</span><span class="sxs-lookup"><span data-stu-id="67f7b-120">Consider the following declaration of a value-type variable:</span></span>  
  
 [!code-csharp[csProgGuideTypes#17](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_4.cs)]  
  
 <span data-ttu-id="67f7b-121">Operace zabalení na proměnnou implicitně platí následující příkaz `i`:</span><span class="sxs-lookup"><span data-stu-id="67f7b-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#18](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_5.cs)]  
  
 <span data-ttu-id="67f7b-122">Výsledek tohoto prohlášení vytváří odkaz na objekt `o`, v zásobníku, která odkazuje na hodnotu typu `int`, v haldě.</span><span class="sxs-lookup"><span data-stu-id="67f7b-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="67f7b-123">Tato hodnota je kopii typ hodnoty hodnotu přiřazenou proměnné `i`.</span><span class="sxs-lookup"><span data-stu-id="67f7b-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="67f7b-124">Rozdíl mezi dvě proměnné, `i` a `o`, je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="67f7b-124">The difference between the two variables, `i` and `o`, is illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="67f7b-125">![BoxingConversion – grafika](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="67f7b-125">![BoxingConversion graphic](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span></span>  
<span data-ttu-id="67f7b-126">Převod zabalení</span><span class="sxs-lookup"><span data-stu-id="67f7b-126">Boxing Conversion</span></span>  
  
 <span data-ttu-id="67f7b-127">Je také možné provést zabalení explicitně jako v následujícím příkladu, ale explicitní zabalení je nutná nikdy:</span><span class="sxs-lookup"><span data-stu-id="67f7b-127">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 [!code-csharp[csProgGuideTypes#19](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_6.cs)]  
  
## <a name="description"></a><span data-ttu-id="67f7b-128">Popis</span><span class="sxs-lookup"><span data-stu-id="67f7b-128">Description</span></span>  
 <span data-ttu-id="67f7b-129">Tento příklad převede proměnná typu integer `i` do objektu `o` s použitím zabalení.</span><span class="sxs-lookup"><span data-stu-id="67f7b-129">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="67f7b-130">Potom s hodnotou uloženou v proměnné `i` změněn z `123` k `456`.</span><span class="sxs-lookup"><span data-stu-id="67f7b-130">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="67f7b-131">Příklad ukazuje, že původní typ hodnoty a objekt zabalené použít samostatnou paměť umístění a proto můžete ukládat různé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="67f7b-131">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67f7b-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="67f7b-132">Example</span></span>  
 [!code-csharp[csProgGuideTypes#16](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_7.cs)]  
  
## <a name="unboxing"></a><span data-ttu-id="67f7b-133">Rozbalení</span><span class="sxs-lookup"><span data-stu-id="67f7b-133">Unboxing</span></span>  
 <span data-ttu-id="67f7b-134">Rozbalení je explicitní převod z typu `object` k [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) nebo z typu rozhraní na typ hodnoty, který implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="67f7b-134">Unboxing is an explicit conversion from the type `object` to a [value type](../../../csharp/language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="67f7b-135">Rozbalení operace se skládá z:</span><span class="sxs-lookup"><span data-stu-id="67f7b-135">An unboxing operation consists of:</span></span>  
  
-   <span data-ttu-id="67f7b-136">Kontrola instance objektu a ujistěte se, že se jedná o zabalené hodnoty typu předané hodnoty.</span><span class="sxs-lookup"><span data-stu-id="67f7b-136">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
-   <span data-ttu-id="67f7b-137">Kopírování hodnotu z instance do proměnné typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="67f7b-137">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="67f7b-138">Následující příkazy ukazují, jak zabalení a rozbalení operace:</span><span class="sxs-lookup"><span data-stu-id="67f7b-138">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 [!code-csharp[csProgGuideTypes#21](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_8.cs)]  
  
 <span data-ttu-id="67f7b-139">Následující obrázek ukazuje výsledek předchozí příkazy.</span><span class="sxs-lookup"><span data-stu-id="67f7b-139">The following figure demonstrates the result of the previous statements.</span></span>  
  
 <span data-ttu-id="67f7b-140">![Rozbalení převod obrázku](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="67f7b-140">![UnBoxing Conversion graphic](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span></span>  
<span data-ttu-id="67f7b-141">Převodu rozbalení</span><span class="sxs-lookup"><span data-stu-id="67f7b-141">Unboxing Conversion</span></span>  
  
 <span data-ttu-id="67f7b-142">Položka se nezabalený rozbalení typů hodnot v době běhu proběhla úspěšně, musí být odkaz na objekt, který byl dříve vytvořen zabalení instance tohoto typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="67f7b-142">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="67f7b-143">Probíhá pokus o unbox `null` způsobí, že <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="67f7b-143">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="67f7b-144">Probíhá pokus o unbox – odkaz na nekompatibilní hodnotu typu příčiny <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="67f7b-144">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67f7b-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="67f7b-145">Example</span></span>  
 <span data-ttu-id="67f7b-146">Následující příklad ukazuje rozbalení neplatný případ a výsledná `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="67f7b-146">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="67f7b-147">Pomocí `try` a `catch`, chybová zpráva se zobrazí, když dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="67f7b-147">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 [!code-csharp[csProgGuideTypes#20](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/boxing-and-unboxing_9.cs)]  
  
 <span data-ttu-id="67f7b-148">Tento program výstupy:</span><span class="sxs-lookup"><span data-stu-id="67f7b-148">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="67f7b-149">Pokud změníte příkaz:</span><span class="sxs-lookup"><span data-stu-id="67f7b-149">If you change the statement:</span></span>  
  
```  
int j = (short) o;  
```  
  
 <span data-ttu-id="67f7b-150">na</span><span class="sxs-lookup"><span data-stu-id="67f7b-150">to:</span></span>  
  
```  
int j = (int) o;  
```  
  
 <span data-ttu-id="67f7b-151">Převod se provede, a zobrazí se výstup:</span><span class="sxs-lookup"><span data-stu-id="67f7b-151">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="67f7b-152">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="67f7b-152">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="67f7b-153">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="67f7b-153">Related Sections</span></span>  
 <span data-ttu-id="67f7b-154">Další informace:</span><span class="sxs-lookup"><span data-stu-id="67f7b-154">For more information:</span></span>  
  
-   [<span data-ttu-id="67f7b-155">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="67f7b-155">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="67f7b-156">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="67f7b-156">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a><span data-ttu-id="67f7b-157">Viz také</span><span class="sxs-lookup"><span data-stu-id="67f7b-157">See Also</span></span>  
 [<span data-ttu-id="67f7b-158">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="67f7b-158">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
