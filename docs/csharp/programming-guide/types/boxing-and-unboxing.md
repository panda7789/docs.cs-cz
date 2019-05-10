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
ms.openlocfilehash: 5db3d759daec273a29dccfeff9879d0edcc9a269
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595021"
---
# <a name="boxing-and-unboxing-c-programming-guide"></a><span data-ttu-id="50d59-102">Zabalení a rozbalení (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="50d59-102">Boxing and Unboxing (C# Programming Guide)</span></span>
<span data-ttu-id="50d59-103">Zabalení je proces převodu [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) typu `object` nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="50d59-103">Boxing is the process of converting a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="50d59-104">Když modul CLR pole typu hodnoty, obtéká hodnotu uvnitř System.Object a uloží ji na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="50d59-104">When the CLR boxes a value type, it wraps the value inside a System.Object and stores it on the managed heap.</span></span> <span data-ttu-id="50d59-105">Rozbalení extrahuje typ hodnoty z objektu.</span><span class="sxs-lookup"><span data-stu-id="50d59-105">Unboxing extracts the value type from the object.</span></span> <span data-ttu-id="50d59-106">Zabalení je implicitní; Rozbalení je explicitní.</span><span class="sxs-lookup"><span data-stu-id="50d59-106">Boxing is implicit; unboxing is explicit.</span></span> <span data-ttu-id="50d59-107">Pojem zabalení a rozbalení základem sjednocené zobrazení C# systému typů, ve kterém lze považovat hodnotu libovolného typu za objekt.</span><span class="sxs-lookup"><span data-stu-id="50d59-107">The concept of boxing and unboxing underlies the C# unified view of the type system in which a value of any type can be treated as an object.</span></span>  
  
 <span data-ttu-id="50d59-108">V následujícím příkladu proměnná integer `i` je *boxed* a přiřazené k objektu `o`.</span><span class="sxs-lookup"><span data-stu-id="50d59-108">In the following example, the integer variable `i` is *boxed* and assigned to object `o`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#14)]  
  
 <span data-ttu-id="50d59-109">Objekt `o` lze potom rozbalit a přiřadit k proměnné celého čísla `i`:</span><span class="sxs-lookup"><span data-stu-id="50d59-109">The object `o` can then be unboxed and assigned to integer variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#15)]  
  
 <span data-ttu-id="50d59-110">Následující příklady ilustrují použití zabalení v jazyce C#.</span><span class="sxs-lookup"><span data-stu-id="50d59-110">The following examples illustrate how boxing is used in C#.</span></span>  
  
 [!code-csharp[csProgGuideTypes#47](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#47)]  
  
## <a name="performance"></a><span data-ttu-id="50d59-111">Výkon</span><span class="sxs-lookup"><span data-stu-id="50d59-111">Performance</span></span>  
 <span data-ttu-id="50d59-112">Vzhledem k jednoduchým přiřazením jsou zabalení a rozbalení výpočetně náročné procesy.</span><span class="sxs-lookup"><span data-stu-id="50d59-112">In relation to simple assignments, boxing and unboxing are computationally expensive processes.</span></span> <span data-ttu-id="50d59-113">Když je typ hodnoty v poli, musí být přiděleny a konstruovány nový objekt.</span><span class="sxs-lookup"><span data-stu-id="50d59-113">When a value type is boxed, a new object must be allocated and constructed.</span></span> <span data-ttu-id="50d59-114">V menší míře je přetypování potřebné pro rozbalení je také nákladné výpočetně.</span><span class="sxs-lookup"><span data-stu-id="50d59-114">To a lesser degree, the cast required for unboxing is also expensive computationally.</span></span> <span data-ttu-id="50d59-115">Další informace najdete v tématu [výkonu](../../../../docs/framework/performance/performance-tips.md).</span><span class="sxs-lookup"><span data-stu-id="50d59-115">For more information, see [Performance](../../../../docs/framework/performance/performance-tips.md).</span></span>  
  
## <a name="boxing"></a><span data-ttu-id="50d59-116">Zabalení</span><span class="sxs-lookup"><span data-stu-id="50d59-116">Boxing</span></span>  
 <span data-ttu-id="50d59-117">Zabalení slouží k uložení typů hodnot haldy uvolňování.</span><span class="sxs-lookup"><span data-stu-id="50d59-117">Boxing is used to store value types in the garbage-collected heap.</span></span> <span data-ttu-id="50d59-118">Zabalení je implicitní převod [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) typu `object` nebo na libovolný typ rozhraní implementovaný tímto typem hodnoty.</span><span class="sxs-lookup"><span data-stu-id="50d59-118">Boxing is an implicit conversion of a [value type](../../../csharp/language-reference/keywords/value-types.md) to the type `object` or to any interface type implemented by this value type.</span></span> <span data-ttu-id="50d59-119">Zabalení typu hodnoty přiděluje instance objektu na haldě a kopíruje hodnotu do nového objektu.</span><span class="sxs-lookup"><span data-stu-id="50d59-119">Boxing a value type allocates an object instance on the heap and copies the value into the new object.</span></span>  
  
 <span data-ttu-id="50d59-120">Vezměte v úvahu následující deklarace proměnné hodnotového typu:</span><span class="sxs-lookup"><span data-stu-id="50d59-120">Consider the following declaration of a value-type variable:</span></span>  
  
 [!code-csharp[csProgGuideTypes#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#17)]  
  
 <span data-ttu-id="50d59-121">Následující příkaz se implicitně týká operace zabalení pro proměnnou `i`:</span><span class="sxs-lookup"><span data-stu-id="50d59-121">The following statement implicitly applies the boxing operation on the variable `i`:</span></span>  
  
 [!code-csharp[csProgGuideTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#18)]  
  
 <span data-ttu-id="50d59-122">Výsledkem tohoto příkazu je vytvoření odkazu na objekt `o`, v zásobníku, který odkazuje na hodnotu typu `int`, na haldě.</span><span class="sxs-lookup"><span data-stu-id="50d59-122">The result of this statement is creating an object reference `o`, on the stack, that references a value of the type `int`, on the heap.</span></span> <span data-ttu-id="50d59-123">Tuto hodnotu je kopií hodnoty hodnotového typu přiřazena k proměnné `i`.</span><span class="sxs-lookup"><span data-stu-id="50d59-123">This value is a copy of the value-type value assigned to the variable `i`.</span></span> <span data-ttu-id="50d59-124">Rozdíl mezi dvěma proměnnými, `i` a `o`, je znázorněn na následujícím obrázku převod na uzavřené určení:</span><span class="sxs-lookup"><span data-stu-id="50d59-124">The difference between the two variables, `i` and `o`, is illustrated in the following image of boxing conversion:</span></span>  
  
 ![Obrázek znázorňující rozdíl mezi i a o proměnné.](./media/boxing-and-unboxing/boxing-operation-i-o-variables.gif)    
  
 <span data-ttu-id="50d59-126">Je také možné provést zabalení explicitně jako v následujícím příkladu, ale nikdy není vyžadováno explicitní zabalení:</span><span class="sxs-lookup"><span data-stu-id="50d59-126">It is also possible to perform the boxing explicitly as in the following example, but explicit boxing is never required:</span></span>  
  
 [!code-csharp[csProgGuideTypes#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#19)]  
  
## <a name="description"></a><span data-ttu-id="50d59-127">Popis</span><span class="sxs-lookup"><span data-stu-id="50d59-127">Description</span></span>  
 <span data-ttu-id="50d59-128">V tomto příkladu se převede celočíselná proměnná `i` objektu `o` pomocí uzavřeného určení.</span><span class="sxs-lookup"><span data-stu-id="50d59-128">This example converts an integer variable `i` to an object `o` by using boxing.</span></span> <span data-ttu-id="50d59-129">Následně je hodnota uložená v proměnné `i` se změnil z `123` k `456`.</span><span class="sxs-lookup"><span data-stu-id="50d59-129">Then, the value stored in the variable `i` is changed from `123` to `456`.</span></span> <span data-ttu-id="50d59-130">Příklad ukazuje, že typ původní hodnoty a zabalený objekt používají samostatná paměťová místa a proto mohou uchovávat různé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="50d59-130">The example shows that the original value type and the boxed object use separate memory locations, and therefore can store different values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50d59-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="50d59-131">Example</span></span>  
 [!code-csharp[csProgGuideTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#16)]  
  
## <a name="unboxing"></a><span data-ttu-id="50d59-132">Rozbalení</span><span class="sxs-lookup"><span data-stu-id="50d59-132">Unboxing</span></span>  
 <span data-ttu-id="50d59-133">Rozbalení je explicitní převod z typu `object` k [typ hodnoty](../../../csharp/language-reference/keywords/value-types.md) nebo z typu rozhraní na typ hodnoty, která implementuje rozhraní.</span><span class="sxs-lookup"><span data-stu-id="50d59-133">Unboxing is an explicit conversion from the type `object` to a [value type](../../../csharp/language-reference/keywords/value-types.md) or from an interface type to a value type that implements the interface.</span></span> <span data-ttu-id="50d59-134">Operace rozbalení se skládá ze:</span><span class="sxs-lookup"><span data-stu-id="50d59-134">An unboxing operation consists of:</span></span>  
  
- <span data-ttu-id="50d59-135">Kontrola instance objektu, abyste měli jistotu, že se jedná o zabalenou hodnotu daného typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="50d59-135">Checking the object instance to make sure that it is a boxed value of the given value type.</span></span>  
  
- <span data-ttu-id="50d59-136">Kopírování hodnoty z instance do proměnné typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="50d59-136">Copying the value from the instance into the value-type variable.</span></span>  
  
 <span data-ttu-id="50d59-137">Následující příkazy ukazují operace zabalení a rozbalení:</span><span class="sxs-lookup"><span data-stu-id="50d59-137">The following statements demonstrate both boxing and unboxing operations:</span></span>  
  
 [!code-csharp[csProgGuideTypes#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#21)]  
  
 <span data-ttu-id="50d59-138">Následující obrázek ukazuje výsledek předchozích příkazů:</span><span class="sxs-lookup"><span data-stu-id="50d59-138">The following figure demonstrates the result of the previous statements:</span></span> 
  
 ![Obrázek znázorňující unboxingového převodu.](./media/boxing-and-unboxing/unboxing-conversion-operation.gif)
  
 <span data-ttu-id="50d59-140">Pro rozbalení typů hodnot v době spuštění úspěšné, musí být rozbalená položka odkazem na objekt, který byl dříve vytvořen zabalením instance tohoto typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="50d59-140">For the unboxing of value types to succeed at run time, the item being unboxed must be a reference to an object that was previously created by boxing an instance of that value type.</span></span> <span data-ttu-id="50d59-141">Při pokusu o rozbalení `null` způsobí, že <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="50d59-141">Attempting to unbox `null` causes a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="50d59-142">Při pokusu o vybalení odkazu na nekompatibilní hodnotu způsobí typ <xref:System.InvalidCastException>.</span><span class="sxs-lookup"><span data-stu-id="50d59-142">Attempting to unbox a reference to an incompatible value type causes an <xref:System.InvalidCastException>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50d59-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="50d59-143">Example</span></span>  
 <span data-ttu-id="50d59-144">Následující příklad ukazuje případ neplatného rozbalení a výsledné `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="50d59-144">The following example demonstrates a case of invalid unboxing and the resulting `InvalidCastException`.</span></span> <span data-ttu-id="50d59-145">Pomocí `try` a `catch`, když dojde k chybě, zobrazí se chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="50d59-145">Using `try` and `catch`, an error message is displayed when the error occurs.</span></span>  
  
 [!code-csharp[csProgGuideTypes#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#20)]  
  
 <span data-ttu-id="50d59-146">Výstup tohoto programu:</span><span class="sxs-lookup"><span data-stu-id="50d59-146">This program outputs:</span></span>  
  
 `Specified cast is not valid. Error: Incorrect unboxing.`  
  
 <span data-ttu-id="50d59-147">Pokud změníte příkaz:</span><span class="sxs-lookup"><span data-stu-id="50d59-147">If you change the statement:</span></span>  
  
```csharp
int j = (short) o;  
```  
  
 <span data-ttu-id="50d59-148">na</span><span class="sxs-lookup"><span data-stu-id="50d59-148">to:</span></span>  
  
```csharp
int j = (int) o;  
```  
  
 <span data-ttu-id="50d59-149">Převod se provede, a zobrazí se výstup:</span><span class="sxs-lookup"><span data-stu-id="50d59-149">the conversion will be performed, and you will get the output:</span></span>  
  
 `Unboxing OK.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="50d59-150">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="50d59-150">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="related-sections"></a><span data-ttu-id="50d59-151">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="50d59-151">Related Sections</span></span>  
 <span data-ttu-id="50d59-152">Další informace:</span><span class="sxs-lookup"><span data-stu-id="50d59-152">For more information:</span></span>  
  
- [<span data-ttu-id="50d59-153">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="50d59-153">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
- [<span data-ttu-id="50d59-154">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="50d59-154">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
## <a name="see-also"></a><span data-ttu-id="50d59-155">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50d59-155">See also</span></span>

- [<span data-ttu-id="50d59-156">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="50d59-156">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
