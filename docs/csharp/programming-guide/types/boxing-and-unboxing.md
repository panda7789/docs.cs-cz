---
title: Zabalení a rozbalení - C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- cs.boxing
helpviewer_keywords:
- C# language, boxing
- C# language, unboxing
- unboxing [C#]
- boxing [C#]
ms.assetid: 8da9bbf4-bce9-4b08-b2e5-f64c11c56514
ms.openlocfilehash: 8340d05b18c4fb19e9ba8f8ecffa5657b7febd79
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201752"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="912b2-102">Zabalení a rozbalení (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="912b2-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="912b2-103">Zabalení je proces převodu [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) typu `object` nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="912b2-103">Boxing is the process of converting a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="912b2-104">Když modul CLR pole typu hodnoty, obtéká hodnotu uvnitř System.Object a uloží ji na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="912b2-104">When the CLR boxes a value type, it wraps the value inside a System.Object and stores it on the managed heap.</span></span> <span data-ttu-id="912b2-105">Rozbalení extrahuje typ hodnoty z objektu.</span><span class="sxs-lookup"><span data-stu-id="912b2-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="912b2-106">Zabalení je implicitní; Rozbalení je explicitní.</span><span class="sxs-lookup"><span data-stu-id="912b2-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="912b2-107">Pojem zabalení a rozbalení základem sjednocené zobrazení C# systému typů, ve kterém lze považovat hodnotu libovolného typu za objekt.</span><span class="sxs-lookup"><span data-stu-id="912b2-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="912b2-108">V následujícím příkladu proměnná integer `i` je *boxed* a přiřazené k objektu `o`.</span><span class="sxs-lookup"><span data-stu-id="912b2-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]  
  
 <span data-ttu-id="912b2-109">Objekt `o` lze potom rozbalit a přiřadit k proměnné celého čísla `i`:</span><span class="sxs-lookup"><span data-stu-id="912b2-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]  
  
 <span data-ttu-id="912b2-110">Následující příklady ilustrují použití zabalení v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="912b2-110">The following examples illustrate how boxing is used in C#.</span></span>  
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="performance"></a><span data-ttu-id="912b2-111">Výkon</span><span class="sxs-lookup"><span data-stu-id="912b2-111">Performance</span></span>  
 <span data-ttu-id="912b2-112">Vzhledem k jednoduchým přiřazením jsou zabalení a rozbalení výpočetně náročné procesy.</span><span class="sxs-lookup"><span data-stu-id="912b2-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="912b2-113">Když je typ hodnoty v poli, musí být přiděleny a konstruovány nový objekt.</span><span class="sxs-lookup"><span data-stu-id="912b2-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="912b2-114">V menší míře je přetypování potřebné pro rozbalení je také nákladné výpočetně.</span><span class="sxs-lookup"><span data-stu-id="912b2-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="912b2-115">Další informace najdete v tématu [výkonu](../../../../docs/framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="912b2-115">For more information, see [Performance](../../../../docs/framework/performance/performance-tips.md).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="912b2-116">Zabalení</span><span class="sxs-lookup"><span data-stu-id="912b2-116">Boxing</span></span>  
 <span data-ttu-id="912b2-117">Zabalení slouží k uložení typů hodnot haldy uvolňování.</span><span class="sxs-lookup"><span data-stu-id="912b2-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="912b2-118">Zabalení je implicitní převod [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) typu `object` nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="912b2-118">Boxing is an implicit conversion of a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="912b2-119">Zabalení typu hodnoty přiděluje instance objektu na haldě a kopíruje hodnotu do nového objektu.</span><span class="sxs-lookup"><span data-stu-id="912b2-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="912b2-120">Vezměte v úvahu následující deklarace proměnné hodnotového typu:</span><span class="sxs-lookup"><span data-stu-id="912b2-120">Consider the following declaration of a value-type variable:</span></span>  
  
 [!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]  
  
 <span data-ttu-id="912b2-121">Následující příkaz se implicitně týká operace zabalení pro proměnnou `i`:</span><span class="sxs-lookup"><span data-stu-id="912b2-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]  
  
 <span data-ttu-id="912b2-122">Výsledkem tohoto příkazu je vytvoření odkazu na objekt `o`, v zásobníku, který odkazuje na hodnotu typu `int`, na haldě.</span><span class="sxs-lookup"><span data-stu-id="912b2-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="912b2-123">Tuto hodnotu je kopií hodnoty hodnotového typu přiřazena k proměnné `i`.</span><span class="sxs-lookup"><span data-stu-id="912b2-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="912b2-124">Rozdíl mezi dvěma proměnnými, `i` a `o`, je znázorněn na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="912b2-124">The difference between the two variables, `i` and `o`, is illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="912b2-125">![BoxingConversion – grafika](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="912b2-125">![BoxingConversion graphic](../../../csharp/programming-guide/types/media/vcboxingconversion.gif "vcBoxingConversion")</span></span>  
<span data-ttu-id="912b2-126">Převod na uzavřené určení</span><span class="sxs-lookup"><span data-stu-id="912b2-126">Boxing Conversion</span></span>  
  
 <span data-ttu-id="912b2-127">Je také možné provést zabalení explicitně jako v následujícím příkladu, ale nikdy není vyžadováno explicitní zabalení:</span><span class="sxs-lookup"><span data-stu-id="912b2-127">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 [!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]  
  
## <a name="description"></a><span data-ttu-id="912b2-128">Popis</span><span class="sxs-lookup"><span data-stu-id="912b2-128">Description</span></span>  
 <span data-ttu-id="912b2-129">V tomto příkladu se převede celočíselná proměnná `i` objektu `o` pomocí uzavřeného určení.</span><span class="sxs-lookup"><span data-stu-id="912b2-129">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="912b2-130">Následně je hodnota uložená v proměnné `i` se změnil z `123` k `456`.</span><span class="sxs-lookup"><span data-stu-id="912b2-130">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="912b2-131">Příklad ukazuje, že typ původní hodnoty a zabalený objekt používají samostatná paměťová místa a proto mohou uchovávat různé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="912b2-131">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="912b2-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="912b2-132">Example</span></span>  
 [!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]  
  
## <a name="unboxing"></a><span data-ttu-id="912b2-133">Rozbalení</span><span class="sxs-lookup"><span data-stu-id="912b2-133">Unboxing</span></span>  
 <span data-ttu-id="912b2-134">Rozbalení je explicitní převod z typu `object` k [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) nebo z typu rozhraní na typ hodnoty, která implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="912b2-134">Unboxing is an explicit conversion from the type `object` to a [value type](../../../csharp/language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="912b2-135">Operace rozbalení se skládá ze:</span><span class="sxs-lookup"><span data-stu-id="912b2-135">An unboxing operation consists of:</span></span>  
  
-   <span data-ttu-id="912b2-136">Kontrola instance objektu, abyste měli jistotu, že se jedná o zabalenou hodnotu daného typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="912b2-136">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
-   <span data-ttu-id="912b2-137">Kopírování hodnoty z instance do proměnné typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="912b2-137">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="912b2-138">Následující příkazy ukazují operace zabalení a rozbalení:</span><span class="sxs-lookup"><span data-stu-id="912b2-138">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 [!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]  
  
 <span data-ttu-id="912b2-139">Následující obrázek ukazuje výsledek předchozích příkazů.</span><span class="sxs-lookup"><span data-stu-id="912b2-139">The following figure demonstrates the result of the previous statements.</span></span>  
  
 <span data-ttu-id="912b2-140">![Obrázek rozbalení převod](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span><span class="sxs-lookup"><span data-stu-id="912b2-140">![UnBoxing Conversion graphic](../../../csharp/programming-guide/types/media/vcunboxingconversion.gif "vcUnBoxingConversion")</span></span>  
<span data-ttu-id="912b2-141">Převod rozbalením</span><span class="sxs-lookup"><span data-stu-id="912b2-141">Unboxing Conversion</span></span>  
  
 <span data-ttu-id="912b2-142">Pro rozbalení typů hodnot v době spuštění úspěšné, musí být rozbalená položka odkazem na objekt, který byl dříve vytvořen zabalením instance tohoto typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="912b2-142">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="912b2-143">Při pokusu o rozbalení `null` způsobí, že <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="912b2-143">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="912b2-144">Při pokusu o vybalení odkazu na nekompatibilní hodnotu způsobí typ <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="912b2-144">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="912b2-145">Příklad</span><span class="sxs-lookup"><span data-stu-id="912b2-145">Example</span></span>  
 <span data-ttu-id="912b2-146">Následující příklad ukazuje případ neplatného rozbalení a výsledné `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="912b2-146">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="912b2-147">Pomocí `try` a `catch`, když dojde k chybě, zobrazí se chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="912b2-147">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 [!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]  
  
 <span data-ttu-id="912b2-148">Výstup tohoto programu:</span><span class="sxs-lookup"><span data-stu-id="912b2-148">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="912b2-149">Pokud změníte příkaz:</span><span class="sxs-lookup"><span data-stu-id="912b2-149">If you change the statement:</span></span>  
  
```csharp
int j = (short) o;  
```  
  
 <span data-ttu-id="912b2-150">na</span><span class="sxs-lookup"><span data-stu-id="912b2-150">to:</span></span>  
  
```csharp
int j = (int) o;  
```  
  
 <span data-ttu-id="912b2-151">Převod se provede, a zobrazí se výstup:</span><span class="sxs-lookup"><span data-stu-id="912b2-151">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="912b2-152">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="912b2-152">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="912b2-153">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="912b2-153">Related Sections</span></span>  
 <span data-ttu-id="912b2-154">Další informace:</span><span class="sxs-lookup"><span data-stu-id="912b2-154">For more information:</span></span>  
  
-   [<span data-ttu-id="912b2-155">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="912b2-155">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="912b2-156">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="912b2-156">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a><span data-ttu-id="912b2-157">Viz také:</span><span class="sxs-lookup"><span data-stu-id="912b2-157">See also</span></span>

- [<span data-ttu-id="912b2-158">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="912b2-158">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
