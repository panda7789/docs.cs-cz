---
title: Typy hodnot s povolenou hodnotou Null (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8734114b9d657066a0ef0b2d648f0290c03b1cbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="867d8-102">Typy hodnot s povolenou hodnotou Null (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="867d8-102">Nullable Value Types (Visual Basic)</span></span>
<span data-ttu-id="867d8-103">Někdy pracujete s typ hodnoty, který nemá hodnotu definovanou v některých případech.</span><span class="sxs-lookup"><span data-stu-id="867d8-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="867d8-104">Například na pole v databázi pravděpodobně k rozlišení mezi s přiřazenou hodnotu, která je smysluplný a nemá přiřazenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="867d8-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="867d8-105">Typy hodnot lze rozšířit na převedení jejich normální hodnoty, nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="867d8-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="867d8-106">Toto rozšíření je volána *typ s možnou hodnotou Null*.</span><span class="sxs-lookup"><span data-stu-id="867d8-106">Such an extension is called a *nullable type*.</span></span>  
  
 <span data-ttu-id="867d8-107">Každý typ s možnou hodnotou Null se vytvářejí na základě obecná <xref:System.Nullable%601> struktura.</span><span class="sxs-lookup"><span data-stu-id="867d8-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="867d8-108">Vezměte v úvahu databázi, která sleduje aktivity související s práci.</span><span class="sxs-lookup"><span data-stu-id="867d8-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="867d8-109">Následující příklad vytvoří s možnou hodnotou Null `Boolean` zadejte a deklaruje proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="867d8-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="867d8-110">Můžete napsat deklaraci třemi způsoby:</span><span class="sxs-lookup"><span data-stu-id="867d8-110">You can write the declaration in three ways:</span></span>  
  
 [!code-vb[VbVbalrNullableValue#1](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_1.vb)]  
  
 <span data-ttu-id="867d8-111">Proměnná `ridesBusToWork` mohou být uloženy hodnotu `True`, hodnotu `False`, nebo vůbec žádná hodnota.</span><span class="sxs-lookup"><span data-stu-id="867d8-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="867d8-112">Počáteční výchozí hodnota je žádná hodnota, která v tomto případě by mohlo znamenat, že informace nebylo dosaženo ještě pro tohoto uživatele.</span><span class="sxs-lookup"><span data-stu-id="867d8-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="867d8-113">Naproti tomu `False` může znamenat, že byl získán informace a osoba, která není přepravují sběrnici pracovat.</span><span class="sxs-lookup"><span data-stu-id="867d8-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>  
  
 <span data-ttu-id="867d8-114">Je možné deklarovat proměnných a vlastností s typy s možnou hodnotou Null a můžou deklarovat pole elementy typu s povolenou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="867d8-114">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="867d8-115">Postupy můžou deklarovat s typy s možnou hodnotou null jako parametry, a můžete se vrátit hodnotu Null typu z `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="867d8-115">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>  
  
 <span data-ttu-id="867d8-116">Nelze vytvořit typ s možnou hodnotou Null na odkaz na typ například pole, `String`, nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="867d8-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="867d8-117">Základní typ musí být typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="867d8-117">The underlying type must be a value type.</span></span> <span data-ttu-id="867d8-118">Další informace najdete v tématu [typy hodnot a typy odkazu](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="867d8-118">For more information, see [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md).</span></span>  
  
## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="867d8-119">Použití proměnné typ s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="867d8-119">Using a Nullable Type Variable</span></span>  
 <span data-ttu-id="867d8-120">Nejdůležitější členy typu s povolenou hodnotou Null jsou jeho <xref:System.Nullable%601.HasValue%2A> a <xref:System.Nullable%601.Value%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="867d8-120">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="867d8-121">Pro proměnnou typu s povolenou hodnotou Null <xref:System.Nullable%601.HasValue%2A> zjistíte, zda proměnná obsahuje hodnotu definované.</span><span class="sxs-lookup"><span data-stu-id="867d8-121">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="867d8-122">Pokud <xref:System.Nullable%601.HasValue%2A> je `True`, si můžete přečíst hodnotu z <xref:System.Nullable%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="867d8-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="867d8-123">Všimněte si, že oba <xref:System.Nullable%601.HasValue%2A> a <xref:System.Nullable%601.Value%2A> jsou `ReadOnly` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="867d8-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>  
  
### <a name="default-values"></a><span data-ttu-id="867d8-124">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="867d8-124">Default Values</span></span>  
 <span data-ttu-id="867d8-125">Když je proměnná deklarovat s typem s možnou hodnotou Null jeho <xref:System.Nullable%601.HasValue%2A> vlastnost má výchozí hodnotu `False`.</span><span class="sxs-lookup"><span data-stu-id="867d8-125">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="867d8-126">To znamená, že ve výchozím nastavení proměnná nemá žádnou hodnotu definované, namísto výchozí hodnoty její základní typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="867d8-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="867d8-127">V následujícím příkladu, proměnná `numberOfChildren` nemá původně definovanou hodnotu, i když výchozí hodnota `Integer` typ je 0.</span><span class="sxs-lookup"><span data-stu-id="867d8-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#2](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_2.vb)]  
  
 <span data-ttu-id="867d8-128">Lze použít ke zjištění hodnotu nebo nedefinovanou hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="867d8-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="867d8-129">Pokud `numberOfChildren` měl byla deklarována jako `Integer`, by existovat žádná hodnota, která může znamenat, že informace není aktuálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="867d8-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>  
  
### <a name="storing-values"></a><span data-ttu-id="867d8-130">Ukládání hodnot</span><span class="sxs-lookup"><span data-stu-id="867d8-130">Storing Values</span></span>  
 <span data-ttu-id="867d8-131">Hodnotu můžete uložit v proměnné nebo vlastnost s možnou hodnotou Null typu obvyklým způsobem.</span><span class="sxs-lookup"><span data-stu-id="867d8-131">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="867d8-132">Následující příklad přiřadí hodnota proměnné `numberOfChildren` deklarované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="867d8-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#3](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_3.vb)]  
  
 <span data-ttu-id="867d8-133">Pokud proměnná nebo vlastnost s možnou hodnotou Null typu obsahuje hodnotu definovanou, může způsobit ji vrátit zpátky do původního stavu systému nemá přiřazenu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="867d8-133">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="867d8-134">Můžete provést nastavením proměnné nebo vlastnost, která má `Nothing`, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="867d8-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#4](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_4.vb)]  
  
> [!NOTE]
>  <span data-ttu-id="867d8-135">I když můžete přiřadit `Nothing` proměnné typu s povolenou hodnotou Null, nelze ho pro testovací `Nothing` pomocí znaménkem rovnosti.</span><span class="sxs-lookup"><span data-stu-id="867d8-135">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="867d8-136">Porovnání, které používá znaménku rovná `someVar = Nothing`, vždy se vyhodnocuje `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="867d8-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="867d8-137">Můžete otestovat proměnné <xref:System.Nullable%601.HasValue%2A> vlastnost pro `False`, nebo otestovat pomocí `Is` nebo `IsNot` operátor.</span><span class="sxs-lookup"><span data-stu-id="867d8-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>  
  
### <a name="retrieving-values"></a><span data-ttu-id="867d8-138">Načítání hodnot</span><span class="sxs-lookup"><span data-stu-id="867d8-138">Retrieving Values</span></span>  
 <span data-ttu-id="867d8-139">K načtení hodnoty proměnné typu s povolenou hodnotou Null, měli byste nejdřív otestovat jeho <xref:System.Nullable%601.HasValue%2A> vlastnost potvrďte, že má hodnotu.</span><span class="sxs-lookup"><span data-stu-id="867d8-139">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="867d8-140">Pokud se pokusíte načíst hodnotu při <xref:System.Nullable%601.HasValue%2A> je `False`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vyvolá <xref:System.InvalidOperationException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="867d8-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="867d8-141">Následující příklad ukazuje doporučeným způsobem, jak načíst proměnnou `numberOfChildren` předchozí příklady.</span><span class="sxs-lookup"><span data-stu-id="867d8-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#5](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_5.vb)]  
  
## <a name="comparing-nullable-types"></a><span data-ttu-id="867d8-142">Porovnání typy s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="867d8-142">Comparing Nullable Types</span></span>  
 <span data-ttu-id="867d8-143">Pokud s možnou hodnotou Null `Boolean` proměnné se používají v logických výrazů, výsledkem mohou být `True`, `False`, nebo `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="867d8-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="867d8-144">Následuje tabulka pravdivosti pro `And` a `Or`.</span><span class="sxs-lookup"><span data-stu-id="867d8-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="867d8-145">Protože `b1` a `b2` Teď máte tři možné hodnoty jsou devět kombinace k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="867d8-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>  
  
|<span data-ttu-id="867d8-146">B1</span><span class="sxs-lookup"><span data-stu-id="867d8-146">b1</span></span>|<span data-ttu-id="867d8-147">B2</span><span class="sxs-lookup"><span data-stu-id="867d8-147">b2</span></span>|<span data-ttu-id="867d8-148">B1 a b2</span><span class="sxs-lookup"><span data-stu-id="867d8-148">b1 And b2</span></span>|<span data-ttu-id="867d8-149">B1 nebo b2</span><span class="sxs-lookup"><span data-stu-id="867d8-149">b1 Or b2</span></span>|  
|--------|--------|---------------|--------------|  
|`Nothing`|`Nothing`|`Nothing`|`Nothing`|  
|`Nothing`|`True`|`Nothing`|`True`|  
|`Nothing`|`False`|`False`|`Nothing`|  
|`True`|`Nothing`|`Nothing`|`True`|  
|`True`|`True`|`True`|`True`|  
|`True`|`False`|`False`|`True`|  
|`False`|`Nothing`|`False`|`Nothing`|  
|`False`|`True`|`False`|`True`|  
|`False`|`False`|`False`|`False`|  
  
 <span data-ttu-id="867d8-150">Pokud je hodnota logická hodnota proměnné nebo výrazu `Nothing`, ani je `true` ani `false`.</span><span class="sxs-lookup"><span data-stu-id="867d8-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="867d8-151">Podívejte se na následující příklad.</span><span class="sxs-lookup"><span data-stu-id="867d8-151">Consider the following example.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#6](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_6.vb)]  
  
 <span data-ttu-id="867d8-152">V tomto příkladu `b1 And b2` vyhodnocuje `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="867d8-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="867d8-153">V důsledku toho `Else` klauzule se spustí v každé `If` příkaz a výstup vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="867d8-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>  
  
 `Expression is not true`  
  
 `Expression is not false`  
  
> [!NOTE]
>  <span data-ttu-id="867d8-154">`AndAlso`a `OrElse`, kteří používají krátká smyčka – vyhodnocení, musí vyhodnotit jejich druhý operandy při první vyhodnocen jako `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="867d8-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>  
  
## <a name="propagation"></a><span data-ttu-id="867d8-155">Šíření</span><span class="sxs-lookup"><span data-stu-id="867d8-155">Propagation</span></span>  
 <span data-ttu-id="867d8-156">Pokud jeden nebo oba operandy aritmetické, porovnání, shift nebo operaci typ s možnou hodnotou Null, je také výsledek operace s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="867d8-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="867d8-157">Pokud oba operandy obsahují hodnoty, které nejsou `Nothing`, operace proběhne na základní hodnoty operandy, jako kdyby ani typu s povolenou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="867d8-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="867d8-158">V následujícím příkladu, proměnné `compare1` a `sum1` jsou implicitně typované.</span><span class="sxs-lookup"><span data-stu-id="867d8-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="867d8-159">Pokud je ukazatel myši nad nimi, zobrazí se, že kompilátor odvodí pro oba dva typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="867d8-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#7](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_7.vb)]  
  
 <span data-ttu-id="867d8-160">Pokud jeden nebo oba operandy mít hodnotu `Nothing`, výsledkem bude `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="867d8-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>  
  
 [!code-vb[VbVbalrNullableValue#8](../../../../visual-basic/programming-guide/language-features/data-types/codesnippet/VisualBasic/nullable-value-types_8.vb)]  
  
## <a name="using-nullable-types-with-data"></a><span data-ttu-id="867d8-161">Použití typů s povolenou hodnotou Null s daty</span><span class="sxs-lookup"><span data-stu-id="867d8-161">Using Nullable Types with Data</span></span>  
 <span data-ttu-id="867d8-162">Databáze je jedno z vašich nejdůležitějších míst používat typy s možnou hodnotou Null.</span><span class="sxs-lookup"><span data-stu-id="867d8-162">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="867d8-163">Ne všechny databázové objekty v současné době podporují typy s možnou hodnotou Null, ale provést adaptéry generované návrháře tabulky.</span><span class="sxs-lookup"><span data-stu-id="867d8-163">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="867d8-164">Najdete v části "Podpora TableAdapter typy s možnou hodnotou Null" v [TableAdapter – přehled](/visualstudio/data-tools/tableadapter-overview).</span><span class="sxs-lookup"><span data-stu-id="867d8-164">See "TableAdapter Support for Nullable Types" in [TableAdapter Overview](/visualstudio/data-tools/tableadapter-overview).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="867d8-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="867d8-165">See Also</span></span>  
 <xref:System.InvalidOperationException>  
 <xref:System.Nullable%601.HasValue%2A>  
 [<span data-ttu-id="867d8-166">Použití typů s povolenou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="867d8-166">Using Nullable Types</span></span>](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
 [<span data-ttu-id="867d8-167">Datové typy</span><span class="sxs-lookup"><span data-stu-id="867d8-167">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="867d8-168">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="867d8-168">Value Types and Reference Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [<span data-ttu-id="867d8-169">Řešení potíží s datové typy</span><span class="sxs-lookup"><span data-stu-id="867d8-169">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="867d8-170">TableAdapter – přehled</span><span class="sxs-lookup"><span data-stu-id="867d8-170">TableAdapter Overview</span></span>](/visualstudio/data-tools/tableadapter-overview)  
 [<span data-ttu-id="867d8-171">Pokud operátor</span><span class="sxs-lookup"><span data-stu-id="867d8-171">If Operator</span></span>](../../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="867d8-172">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="867d8-172">Local Type Inference</span></span>](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="867d8-173">Is – operátor</span><span class="sxs-lookup"><span data-stu-id="867d8-173">Is Operator</span></span>](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="867d8-174">IsNot – operátor</span><span class="sxs-lookup"><span data-stu-id="867d8-174">IsNot Operator</span></span>](../../../../visual-basic/language-reference/operators/isnot-operator.md)
