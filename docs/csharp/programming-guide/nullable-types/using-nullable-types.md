---
title: "Použití typů s povolenou hodnotou Null (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c8a42392bbcd2e53c54ff4c13bf98c048262ae4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-nullable-types-c-programming-guide"></a><span data-ttu-id="30962-102">Použití typů s povolenou hodnotou Null (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="30962-102">Using Nullable Types (C# Programming Guide)</span></span>
<span data-ttu-id="30962-103">Typy s možnou hodnotou Null může představovat všechny hodnoty základní typ a další [null](../../../csharp/language-reference/keywords/null.md) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="30962-103">Nullable types can represent all the values of an underlying type, and an additional [null](../../../csharp/language-reference/keywords/null.md) value.</span></span> <span data-ttu-id="30962-104">Typy s možnou hodnotou Null jsou deklarované v jednom ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="30962-104">Nullable types are declared in one of two ways:</span></span>  
  
 `System.Nullable<T> variable`  
  
 <span data-ttu-id="30962-105">-nebo-</span><span class="sxs-lookup"><span data-stu-id="30962-105">-or-</span></span>  
  
 `T? variable`  
  
 <span data-ttu-id="30962-106">`T`je základní typ typ s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="30962-106">`T` is the underlying type of the nullable type.</span></span> <span data-ttu-id="30962-107">`T`může být libovolný typ hodnoty včetně `struct`; nemůže být odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="30962-107">`T` can be any value type including `struct`; it cannot be a reference type.</span></span>  
  
 <span data-ttu-id="30962-108">Příklad může při použití typu s povolenou hodnotou Null, zvažte, jak obyčejnou Logická proměnná může mít dvě hodnoty: true a false.</span><span class="sxs-lookup"><span data-stu-id="30962-108">For an example of when you might use a nullable type, consider how an ordinary Boolean variable can have two values: true and false.</span></span> <span data-ttu-id="30962-109">Neexistuje žádná hodnota, která označuje, že "undefined".</span><span class="sxs-lookup"><span data-stu-id="30962-109">There is no value that signifies "undefined".</span></span> <span data-ttu-id="30962-110">V mnoha aplikacích programování zejména databáze interakce, proměnné se může objevit v nedefinované stavu.</span><span class="sxs-lookup"><span data-stu-id="30962-110">In many programming applications, most notably database interactions, variables can occur in an undefined state.</span></span> <span data-ttu-id="30962-111">Například na pole v databázi mohou obsahovat hodnoty true nebo false, ale žádná hodnota může obsahovat také vůbec.</span><span class="sxs-lookup"><span data-stu-id="30962-111">For example, a field in a database may contain the values true or false, but it may also contain no value at all.</span></span> <span data-ttu-id="30962-112">Podobně odkazové typy může být nastaven na `null` indikující, že nejsou inicializovány.</span><span class="sxs-lookup"><span data-stu-id="30962-112">Similarly, reference types can be set to `null` to indicate that they are not initialized.</span></span>  
  
 <span data-ttu-id="30962-113">Tento rozdíl lze vytvořit velmi programovací pracovní s další proměnné, které se používají k ukládání informací o stavu, použití speciální hodnoty a tak dále.</span><span class="sxs-lookup"><span data-stu-id="30962-113">This disparity can create extra programming work, with additional variables used to store state information, the use of special values, and so on.</span></span> <span data-ttu-id="30962-114">Typ s možnou hodnotou Null modifikátor umožňuje C# k vytvoření typu hodnoty proměnné, které označují nedefinovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="30962-114">The nullable type modifier enables C# to create value-type variables that indicate an undefined value.</span></span>  
  
## <a name="examples-of-nullable-types"></a><span data-ttu-id="30962-115">Příklady typů s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="30962-115">Examples of Nullable Types</span></span>  
 <span data-ttu-id="30962-116">Libovolný typ hodnoty slouží jako základ pro typ s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="30962-116">Any value type may be used as the basis for a nullable type.</span></span> <span data-ttu-id="30962-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="30962-117">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## <a name="the-members-of-nullable-types"></a><span data-ttu-id="30962-118">Členové typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="30962-118">The Members of Nullable Types</span></span>  
 <span data-ttu-id="30962-119">Každá instance typu s povolenou hodnotou Null má dvě veřejné vlastnosti jen pro čtení:</span><span class="sxs-lookup"><span data-stu-id="30962-119">Each instance of a nullable type has two public read-only properties:</span></span>  
  
-   `HasValue`  
  
     <span data-ttu-id="30962-120">`HasValue`je typu `bool`.</span><span class="sxs-lookup"><span data-stu-id="30962-120">`HasValue` is of type `bool`.</span></span> <span data-ttu-id="30962-121">Je nastaven na hodnotu `true` Pokud proměnná obsahuje hodnotu než null.</span><span class="sxs-lookup"><span data-stu-id="30962-121">It is set to `true` when the variable contains a non-null value.</span></span>  
  
-   `Value`  
  
     <span data-ttu-id="30962-122">`Value`je stejného typu jako nadřazený typ.</span><span class="sxs-lookup"><span data-stu-id="30962-122">`Value` is of the same type as the underlying type.</span></span> <span data-ttu-id="30962-123">Pokud `HasValue` je `true`, `Value` obsahuje hodnotu smysluplný.</span><span class="sxs-lookup"><span data-stu-id="30962-123">If `HasValue` is `true`, `Value` contains a meaningful value.</span></span> <span data-ttu-id="30962-124">Pokud `HasValue` je `false`, přístupu k `Value` vyvolá výjimku <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="30962-124">If `HasValue` is `false`, accessing `Value` will throw a <xref:System.InvalidOperationException>.</span></span>  
  
 <span data-ttu-id="30962-125">V tomto příkladu `HasValue` člen se používá k ověření, zda proměnná obsahuje hodnotu, než se pokusí ji zobrazit.</span><span class="sxs-lookup"><span data-stu-id="30962-125">In this example, the `HasValue` member is used to test whether the variable contains a value before it tries to display it.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 <span data-ttu-id="30962-126">Testování pro hodnotu lze také provést jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="30962-126">Testing for a value can also be done as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## <a name="explicit-conversions"></a><span data-ttu-id="30962-127">Explicitní převody</span><span class="sxs-lookup"><span data-stu-id="30962-127">Explicit Conversions</span></span>  
 <span data-ttu-id="30962-128">Typ s možnou hodnotou Null lze převést na typu regulární explicitně s přetypování nebo pomocí `Value` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="30962-128">A nullable type can be cast to a regular type, either explicitly with a cast, or by using the `Value` property.</span></span> <span data-ttu-id="30962-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="30962-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 <span data-ttu-id="30962-130">Pokud definovaná uživatelem definovaný převod mezi dvěma datovými typy, stejné převod mohou sloužit také s možnou hodnotou Null verze těchto datových typů.</span><span class="sxs-lookup"><span data-stu-id="30962-130">If a user-defined conversion is defined between two data types, the same conversion can also be used with the nullable versions of these data types.</span></span>  
  
## <a name="implicit-conversions"></a><span data-ttu-id="30962-131">Implicitní převody</span><span class="sxs-lookup"><span data-stu-id="30962-131">Implicit Conversions</span></span>  
 <span data-ttu-id="30962-132">Proměnná typu s povolenou hodnotou Null lze nastavit na hodnotu null s `null` – klíčové slovo, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="30962-132">A variable of nullable type can be set to null with the `null` keyword, as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 <span data-ttu-id="30962-133">Je implicitní převod z typu obyčejnou na typ s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="30962-133">The conversion from an ordinary type to a nullable type, is implicit.</span></span>  
  
 [!code-csharp[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## <a name="operators"></a><span data-ttu-id="30962-134">Operátory</span><span class="sxs-lookup"><span data-stu-id="30962-134">Operators</span></span>  
 <span data-ttu-id="30962-135">Předdefinované Unární a binární operátory a uživatelem definované operátory, které existují u typů hodnot může také použít pro typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="30962-135">The predefined unary and binary operators and any user-defined operators that exist for value types may also be used by nullable types.</span></span> <span data-ttu-id="30962-136">Tyto operátory vytvořit hodnotu null, pokud operandy jsou null. operátor, jinak používá obsažené hodnotu vypočítat výsledek.</span><span class="sxs-lookup"><span data-stu-id="30962-136">These operators produce a null value if the operands are null; otherwise, the operator uses the contained value to calculate the result.</span></span> <span data-ttu-id="30962-137">Příklad:</span><span class="sxs-lookup"><span data-stu-id="30962-137">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 <span data-ttu-id="30962-138">Při provádění porovnávání s typy s možnou hodnotou Null, pokud jeden z typů s povolenou hodnotou Null hodnotu null a dalších není všechny porovnání vyhodnocení `false` s výjimkou `!=` (nerovná).</span><span class="sxs-lookup"><span data-stu-id="30962-138">When you perform comparisons with nullable types, if the value of one of the nullable types is null and the other is not, all comparisons evaluate to `false` except for `!=` (not equal).</span></span> <span data-ttu-id="30962-139">Je důležité, abyste předpokládat, že vzhledem k tomu, že konkrétní porovnání vrátí `false`, opačném případě vrátí `true`.</span><span class="sxs-lookup"><span data-stu-id="30962-139">It is important not to assume that because a particular comparison returns `false`, the opposite case returns `true`.</span></span> <span data-ttu-id="30962-140">V následujícím příkladu 10 není větší než je menší než ani rovnat na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="30962-140">In the following example, 10 is not greater than, less than, nor equal to null.</span></span> <span data-ttu-id="30962-141">Pouze `num1 != num2` vyhodnocuje `true`.</span><span class="sxs-lookup"><span data-stu-id="30962-141">Only `num1 != num2` evaluates to `true`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 <span data-ttu-id="30962-142">Porovnání rovnosti dva typy s možnou hodnotou Null, které jsou oba hodnotu null se vyhodnocuje `true`.</span><span class="sxs-lookup"><span data-stu-id="30962-142">An equality comparison of two nullable types that are both null evaluates to `true`.</span></span>  
  
## <a name="the--operator"></a><span data-ttu-id="30962-143">Na??</span><span class="sxs-lookup"><span data-stu-id="30962-143">The ??</span></span> <span data-ttu-id="30962-144">Operátor</span><span class="sxs-lookup"><span data-stu-id="30962-144">Operator</span></span>  
 <span data-ttu-id="30962-145">`??` Operátor definuje výchozí hodnotu, která je vrácena, pokud typ s možnou hodnotou Null se přiřadí k použití hodnot Null typu.</span><span class="sxs-lookup"><span data-stu-id="30962-145">The `??` operator defines a default value that is returned when a nullable type is assigned to a non-nullable type.</span></span>  
  
 [!code-csharp[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 <span data-ttu-id="30962-146">Tento operátor. můžete také použít s více typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="30962-146">This operator can also be used with multiple nullable types.</span></span> <span data-ttu-id="30962-147">Příklad:</span><span class="sxs-lookup"><span data-stu-id="30962-147">For example:</span></span>  
  
 [!code-csharp[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## <a name="the-bool-type"></a><span data-ttu-id="30962-148">Bool? Typ</span><span class="sxs-lookup"><span data-stu-id="30962-148">The bool? type</span></span>  
 <span data-ttu-id="30962-149">`bool?` Typ s možnou hodnotou Null může obsahovat tři různé hodnoty: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) a [null](../../../csharp/language-reference/keywords/null.md).</span><span class="sxs-lookup"><span data-stu-id="30962-149">The `bool?` nullable type can contain three different values: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) and [null](../../../csharp/language-reference/keywords/null.md).</span></span> <span data-ttu-id="30962-150">Informace o tom, jak převést z bool? bool, najdete v tématu [postupy: bezpečné přetypování z bool? na bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span><span class="sxs-lookup"><span data-stu-id="30962-150">For information about how to cast from a bool? to a bool, see [How to: Safely Cast from bool? to bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).</span></span>  
  
 <span data-ttu-id="30962-151">S možnou hodnotou Null logické hodnoty jsou stejné jako logická hodnota proměnné typ, který se používá v systému SQL.</span><span class="sxs-lookup"><span data-stu-id="30962-151">Nullable Booleans are like the Boolean variable type that is used in SQL.</span></span> <span data-ttu-id="30962-152">Zajistit, aby výsledky vyprodukované `&` a `|` operátory jsou konzistentní s typem Boolean s hodnotou tři v SQL, jsou k dispozici následující předdefinované operátory:</span><span class="sxs-lookup"><span data-stu-id="30962-152">To ensure that the results produced by the `&` and `|` operators are consistent with the three-valued Boolean type in SQL, the following predefined operators are provided:</span></span>  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 <span data-ttu-id="30962-153">Výsledky těchto operátorů jsou uvedené v následující tabulce:</span><span class="sxs-lookup"><span data-stu-id="30962-153">The results of these operators are listed in the following table:</span></span>  
  
|<span data-ttu-id="30962-154">X</span><span class="sxs-lookup"><span data-stu-id="30962-154">X</span></span>|<span data-ttu-id="30962-155">y</span><span class="sxs-lookup"><span data-stu-id="30962-155">y</span></span>|<span data-ttu-id="30962-156">x a y</span><span class="sxs-lookup"><span data-stu-id="30962-156">x&y</span></span>|<span data-ttu-id="30962-157">x &#124; y</span><span class="sxs-lookup"><span data-stu-id="30962-157">x&#124;y</span></span>|  
|-------|-------|---------|--------------|  
|<span data-ttu-id="30962-158">true</span><span class="sxs-lookup"><span data-stu-id="30962-158">true</span></span>|<span data-ttu-id="30962-159">true</span><span class="sxs-lookup"><span data-stu-id="30962-159">true</span></span>|<span data-ttu-id="30962-160">true</span><span class="sxs-lookup"><span data-stu-id="30962-160">true</span></span>|<span data-ttu-id="30962-161">true</span><span class="sxs-lookup"><span data-stu-id="30962-161">true</span></span>|  
|<span data-ttu-id="30962-162">true</span><span class="sxs-lookup"><span data-stu-id="30962-162">true</span></span>|<span data-ttu-id="30962-163">false</span><span class="sxs-lookup"><span data-stu-id="30962-163">false</span></span>|<span data-ttu-id="30962-164">false</span><span class="sxs-lookup"><span data-stu-id="30962-164">false</span></span>|<span data-ttu-id="30962-165">true</span><span class="sxs-lookup"><span data-stu-id="30962-165">true</span></span>|  
|<span data-ttu-id="30962-166">true</span><span class="sxs-lookup"><span data-stu-id="30962-166">true</span></span>|<span data-ttu-id="30962-167">null</span><span class="sxs-lookup"><span data-stu-id="30962-167">null</span></span>|<span data-ttu-id="30962-168">null</span><span class="sxs-lookup"><span data-stu-id="30962-168">null</span></span>|<span data-ttu-id="30962-169">true</span><span class="sxs-lookup"><span data-stu-id="30962-169">true</span></span>|  
|<span data-ttu-id="30962-170">false</span><span class="sxs-lookup"><span data-stu-id="30962-170">false</span></span>|<span data-ttu-id="30962-171">true</span><span class="sxs-lookup"><span data-stu-id="30962-171">true</span></span>|<span data-ttu-id="30962-172">false</span><span class="sxs-lookup"><span data-stu-id="30962-172">false</span></span>|<span data-ttu-id="30962-173">true</span><span class="sxs-lookup"><span data-stu-id="30962-173">true</span></span>|  
|<span data-ttu-id="30962-174">false</span><span class="sxs-lookup"><span data-stu-id="30962-174">false</span></span>|<span data-ttu-id="30962-175">false</span><span class="sxs-lookup"><span data-stu-id="30962-175">false</span></span>|<span data-ttu-id="30962-176">false</span><span class="sxs-lookup"><span data-stu-id="30962-176">false</span></span>|<span data-ttu-id="30962-177">false</span><span class="sxs-lookup"><span data-stu-id="30962-177">false</span></span>|  
|<span data-ttu-id="30962-178">false</span><span class="sxs-lookup"><span data-stu-id="30962-178">false</span></span>|<span data-ttu-id="30962-179">null</span><span class="sxs-lookup"><span data-stu-id="30962-179">null</span></span>|<span data-ttu-id="30962-180">false</span><span class="sxs-lookup"><span data-stu-id="30962-180">false</span></span>|<span data-ttu-id="30962-181">null</span><span class="sxs-lookup"><span data-stu-id="30962-181">null</span></span>|  
|<span data-ttu-id="30962-182">null</span><span class="sxs-lookup"><span data-stu-id="30962-182">null</span></span>|<span data-ttu-id="30962-183">true</span><span class="sxs-lookup"><span data-stu-id="30962-183">true</span></span>|<span data-ttu-id="30962-184">null</span><span class="sxs-lookup"><span data-stu-id="30962-184">null</span></span>|<span data-ttu-id="30962-185">true</span><span class="sxs-lookup"><span data-stu-id="30962-185">true</span></span>|  
|<span data-ttu-id="30962-186">null</span><span class="sxs-lookup"><span data-stu-id="30962-186">null</span></span>|<span data-ttu-id="30962-187">false</span><span class="sxs-lookup"><span data-stu-id="30962-187">false</span></span>|<span data-ttu-id="30962-188">false</span><span class="sxs-lookup"><span data-stu-id="30962-188">false</span></span>|<span data-ttu-id="30962-189">null</span><span class="sxs-lookup"><span data-stu-id="30962-189">null</span></span>|  
|<span data-ttu-id="30962-190">null</span><span class="sxs-lookup"><span data-stu-id="30962-190">null</span></span>|<span data-ttu-id="30962-191">null</span><span class="sxs-lookup"><span data-stu-id="30962-191">null</span></span>|<span data-ttu-id="30962-192">null</span><span class="sxs-lookup"><span data-stu-id="30962-192">null</span></span>|<span data-ttu-id="30962-193">null</span><span class="sxs-lookup"><span data-stu-id="30962-193">null</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30962-194">Viz také</span><span class="sxs-lookup"><span data-stu-id="30962-194">See Also</span></span>  
 [<span data-ttu-id="30962-195">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="30962-195">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="30962-196">Typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="30962-196">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="30962-197">Zabalení typů s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="30962-197">Boxing Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
 [<span data-ttu-id="30962-198">Typy hodnot s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="30962-198">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
