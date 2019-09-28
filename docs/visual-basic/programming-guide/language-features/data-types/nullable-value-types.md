---
title: Typy hodnot s možnou hodnotou null – Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.Nullable
helpviewer_keywords:
- nullable types [Visual Basic]
- '? [Visual Basic]'
- types [Visual Basic], nullable
- nullable types [Visual Basic]
- data types [Visual Basic], nullable
ms.assetid: 9ac3b602-6f96-4e6d-96f7-cd4e81c468a6
ms.openlocfilehash: 072496a560775a8f79274f1d44dd389d6ed5b40d
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351765"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="1ebc1-102">Typy hodnot s povolenou hodnotou Null (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1ebc1-102">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="1ebc1-103">Někdy pracujete s typem hodnoty, který nemá v určitých případech definovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="1ebc1-104">Například pole v databázi může být nutné rozlišovat mezi přiřazením přiřazené hodnoty, která je smysluplná a nemá přiřazenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="1ebc1-105">Typy hodnot lze rozšířit tak, aby převzaly jejich normální hodnoty nebo hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="1ebc1-106">Takové rozšíření se nazývá typ s *možnou hodnotou null*.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-106">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="1ebc1-107">Každý typ s možnou hodnotou null je vytvořen z obecné struktury <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-107">Each nullable type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="1ebc1-108">Vezměte v úvahu databázi, která sleduje aktivity související s prací.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="1ebc1-109">Následující příklad vytvoří hodnotu null typu `Boolean` a deklaruje proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="1ebc1-110">Deklaraci můžete zapsat třemi způsoby:</span><span class="sxs-lookup"><span data-stu-id="1ebc1-110">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="1ebc1-111">Proměnná `ridesBusToWork` může obsahovat hodnotu `True`, hodnotu `False` nebo vůbec žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="1ebc1-112">Počáteční výchozí hodnota není vůbec žádná hodnota, což by v tomto případě mohlo znamenat, že pro tuto osobu ještě nebyly získány informace.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="1ebc1-113">Naproti tomu `False` znamená, že informace byly získány a osoba nepracovala sběrnici, aby fungovala.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="1ebc1-114">Můžete deklarovat proměnné a vlastnosti s typy s možnou hodnotou null a můžete deklarovat pole s prvky typu s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-114">You can declare variables and properties with nullable types, and you can declare an array with elements of a nullable type.</span></span> <span data-ttu-id="1ebc1-115">Můžete deklarovat procedury s typy s možnou hodnotou null jako parametry a můžete vrátit typ s možnou hodnotou null z procedury `Function`.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-115">You can declare procedures with nullable types as parameters, and you can return a nullable type from a `Function` procedure.</span></span>

<span data-ttu-id="1ebc1-116">Typ s možnou hodnotou null nelze vytvořit v typu odkazu, jako je pole, `String` nebo třída.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="1ebc1-117">Nadřízený typ musí být hodnotový typ.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-117">The underlying type must be a value type.</span></span> <span data-ttu-id="1ebc1-118">Další informace naleznete v tématu [typy hodnot a typy odkazů](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="1ebc1-118">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="1ebc1-119">Použití proměnné typu s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="1ebc1-119">Using a Nullable Type Variable</span></span>

<span data-ttu-id="1ebc1-120">Nejdůležitějšími členy typu s možnou hodnotou null jsou vlastnosti <xref:System.Nullable%601.HasValue%2A> a <xref:System.Nullable%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-120">The most important members of a nullable type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="1ebc1-121">Pro proměnnou typu s možnou hodnotou null <xref:System.Nullable%601.HasValue%2A> oznamuje, zda proměnná obsahuje definovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-121">For a variable of a nullable type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="1ebc1-122">Pokud je <xref:System.Nullable%601.HasValue%2A> `True`, můžete si přečíst hodnotu z <xref:System.Nullable%601.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="1ebc1-123">Všimněte si, že <xref:System.Nullable%601.HasValue%2A> i <xref:System.Nullable%601.Value%2A> jsou vlastnosti `ReadOnly`.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="1ebc1-124">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="1ebc1-124">Default Values</span></span>

<span data-ttu-id="1ebc1-125">Pokud deklarujete proměnnou s typem s možnou hodnotou null, má vlastnost <xref:System.Nullable%601.HasValue%2A> výchozí hodnotu `False`.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-125">When you declare a variable with a nullable type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="1ebc1-126">To znamená, že ve výchozím nastavení proměnná nemá žádnou definovanou hodnotu namísto výchozí hodnoty svého základního typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="1ebc1-127">V následujícím příkladu proměnná `numberOfChildren` zpočátku nemá definovanou hodnotu, i když je výchozí hodnota `Integer` typu 0.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="1ebc1-128">Hodnota null je užitečná k označení nedefinované nebo neznámé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="1ebc1-129">Pokud byla `numberOfChildren` deklarována jako `Integer`, neexistuje žádná hodnota, která by mohla znamenat, že informace nejsou aktuálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="1ebc1-130">Ukládání hodnot</span><span class="sxs-lookup"><span data-stu-id="1ebc1-130">Storing Values</span></span>

<span data-ttu-id="1ebc1-131">Hodnotu můžete v proměnné nebo vlastnosti typu s možnou hodnotou null ukládat obvyklým způsobem.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-131">You store a value in a variable or property of a nullable type in the typical way.</span></span> <span data-ttu-id="1ebc1-132">Následující příklad přiřadí hodnotu proměnné `numberOfChildren` deklarované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="1ebc1-133">Pokud proměnná nebo vlastnost typu s možnou hodnotou null obsahuje definovanou hodnotu, můžete to způsobit, že se vrátí do svého počátečního stavu, který nemá přiřazenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-133">If a variable or property of a nullable type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="1ebc1-134">Provedete to tak, že nastavíte proměnnou nebo vlastnost na `Nothing`, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="1ebc1-135">I když můžete přiřadit `Nothing` proměnné typu s možnou hodnotou null, nemůžete ji otestovat pro `Nothing` pomocí znaménka rovná se.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-135">Although you can assign `Nothing` to a variable of a nullable type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="1ebc1-136">Porovnání, které používá znaménko rovná se, `someVar = Nothing`, vždy vyhodnocuje jako `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="1ebc1-137">Vlastnost <xref:System.Nullable%601.HasValue%2A> proměnné lze otestovat pro `False` nebo test pomocí operátoru `Is` nebo `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="1ebc1-138">Načítání hodnot</span><span class="sxs-lookup"><span data-stu-id="1ebc1-138">Retrieving Values</span></span>

<span data-ttu-id="1ebc1-139">Chcete-li načíst hodnotu proměnné typu s možnou hodnotou null, měli byste nejprve otestovat jeho vlastnost <xref:System.Nullable%601.HasValue%2A> a potvrdit, že má hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-139">To retrieve the value of a variable of a nullable type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="1ebc1-140">Pokud se pokusíte načíst hodnotu, když <xref:System.Nullable%601.HasValue%2A> je `False`, Visual Basic vyvolá výjimku <xref:System.InvalidOperationException>.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="1ebc1-141">Následující příklad ukazuje doporučený způsob, jak číst proměnnou `numberOfChildren` předchozích příkladů.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="1ebc1-142">Porovnání typů s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="1ebc1-142">Comparing Nullable Types</span></span>

<span data-ttu-id="1ebc1-143">Pokud jsou v logických výrazech použity proměnné s hodnotou null `Boolean`, výsledek může být `True`, `False` nebo `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="1ebc1-144">Následuje tabulka pravdy pro `And` a `Or`.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="1ebc1-145">Vzhledem k tomu, že `b1` a `b2` nyní mají tři možné hodnoty, jsou vyhodnoceny devět kombinací.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="1ebc1-146">b1</span><span class="sxs-lookup"><span data-stu-id="1ebc1-146">b1</span></span>|<span data-ttu-id="1ebc1-147">b2</span><span class="sxs-lookup"><span data-stu-id="1ebc1-147">b2</span></span>|<span data-ttu-id="1ebc1-148">B1 a B2</span><span class="sxs-lookup"><span data-stu-id="1ebc1-148">b1 And b2</span></span>|<span data-ttu-id="1ebc1-149">B1 nebo B2</span><span class="sxs-lookup"><span data-stu-id="1ebc1-149">b1 Or b2</span></span>|
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

<span data-ttu-id="1ebc1-150">Pokud je hodnota logické proměnné nebo výrazu `Nothing`, není to ani `true` ani `false`.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="1ebc1-151">Vezměte v úvahu následující příklad.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-151">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="1ebc1-152">V tomto příkladu je `b1 And b2` vyhodnocena jako `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="1ebc1-153">V důsledku toho klauzule `Else` se spustí v každém příkazu `If` a výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="1ebc1-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="1ebc1-154">`AndAlso` a `OrElse`, které používají testování na základě krátkého okruhu, musí při prvním vyhodnocení na `Nothing` vyhodnotit jejich druhý operand.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="1ebc1-155">Šíření</span><span class="sxs-lookup"><span data-stu-id="1ebc1-155">Propagation</span></span>

<span data-ttu-id="1ebc1-156">V případě, že jeden nebo oba operandy aritmetické operace, porovnání, posunu nebo typu může mít hodnotu null, výsledek operace je také možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is nullable, the result of the operation is also nullable.</span></span> <span data-ttu-id="1ebc1-157">Pokud mají oba operandy hodnoty, které nejsou `Nothing`, operace se provádí na podkladových hodnotách operandů, jako by nebyl typ s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable type.</span></span> <span data-ttu-id="1ebc1-158">V následujícím příkladu jsou proměnné `compare1` a `sum1` implicitně typované.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="1ebc1-159">Pokud ponecháte ukazatel myši nad nimi, uvidíte, že kompilátor odvodí u obou z nich typy s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="1ebc1-160">Pokud jeden nebo oba operandy mají hodnotu `Nothing`, výsledek bude `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="1ebc1-161">Použití typů s povolenou hodnotou null s daty</span><span class="sxs-lookup"><span data-stu-id="1ebc1-161">Using Nullable Types with Data</span></span>

<span data-ttu-id="1ebc1-162">Databáze je jedním z nejdůležitějších míst pro použití typů s možnou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-162">A database is one of the most important places to use nullable types.</span></span> <span data-ttu-id="1ebc1-163">Ne všechny objekty databáze aktuálně podporují typy s možnou hodnotou null, ale adaptéry tabulek vygenerované návrhářem.</span><span class="sxs-lookup"><span data-stu-id="1ebc1-163">Not all database objects currently support nullable types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="1ebc1-164">Viz [Podpora TableAdapter pro typy s možnou hodnotou null](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span><span class="sxs-lookup"><span data-stu-id="1ebc1-164">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ebc1-165">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ebc1-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="1ebc1-166">Datové typy</span><span class="sxs-lookup"><span data-stu-id="1ebc1-166">Data Types</span></span>](index.md)
- [<span data-ttu-id="1ebc1-167">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="1ebc1-167">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="1ebc1-168">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="1ebc1-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="1ebc1-169">Vyplnění datových sad pomocí objektů TableAdapter</span><span class="sxs-lookup"><span data-stu-id="1ebc1-169">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="1ebc1-170">Operátor If</span><span class="sxs-lookup"><span data-stu-id="1ebc1-170">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="1ebc1-171">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="1ebc1-171">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="1ebc1-172">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="1ebc1-172">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="1ebc1-173">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="1ebc1-173">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="1ebc1-174">Použití typů s možnouC#hodnotou null ()</span><span class="sxs-lookup"><span data-stu-id="1ebc1-174">Using Nullable Value Types (C#)</span></span>](../../../../csharp/programming-guide/nullable-types/using-nullable-types.md)
