---
title: Typy hodnot s povolenou hodnotou Null
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
ms.openlocfilehash: beed8262c50dc68330b8f03aa3d864ed2f8df0d5
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249679"
---
# <a name="nullable-value-types-visual-basic"></a><span data-ttu-id="48ded-102">Typy hodnot s povolenou hodnotou Null (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="48ded-102">Nullable Value Types (Visual Basic)</span></span>

<span data-ttu-id="48ded-103">Někdy pracujete s typem hodnoty, který za určitých okolností nemá definovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="48ded-103">Sometimes you work with a value type that does not have a defined value in certain circumstances.</span></span> <span data-ttu-id="48ded-104">Například pole v databázi může mít rozlišovat mezi s přiřazenou hodnotu, která je smysluplná a nemá přiřazenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="48ded-104">For example, a field in a database might have to distinguish between having an assigned value that is meaningful and not having an assigned value.</span></span> <span data-ttu-id="48ded-105">Typy hodnot lze rozšířit tak, aby jejich normální hodnoty nebo nulovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="48ded-105">Value types can be extended to take either their normal values or a null value.</span></span> <span data-ttu-id="48ded-106">Takové rozšíření se nazývá *typ s možnou hodnotou null*.</span><span class="sxs-lookup"><span data-stu-id="48ded-106">Such an extension is called a *nullable type*.</span></span>

<span data-ttu-id="48ded-107">Každý typ hodnoty s možnou <xref:System.Nullable%601> hodnotou null je vytvořen z obecné struktury.</span><span class="sxs-lookup"><span data-stu-id="48ded-107">Each nullable value type is constructed from the generic <xref:System.Nullable%601> structure.</span></span> <span data-ttu-id="48ded-108">Zvažte databázi, která sleduje pracovní aktivity.</span><span class="sxs-lookup"><span data-stu-id="48ded-108">Consider a database that tracks work-related activities.</span></span> <span data-ttu-id="48ded-109">Následující příklad vytvoří typ `Boolean` s možnou hodnotou null a deklaruje proměnnou tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="48ded-109">The following example constructs a nullable `Boolean` type and declares a variable of that type.</span></span> <span data-ttu-id="48ded-110">Prohlášení můžete napsat třemi způsoby:</span><span class="sxs-lookup"><span data-stu-id="48ded-110">You can write the declaration in three ways:</span></span>

[!code-vb[VbVbalrNullableValue#1](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#1)]

<span data-ttu-id="48ded-111">Proměnná `ridesBusToWork` může obsahovat `True`hodnotu `False`, hodnotu nebo vůbec žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="48ded-111">The variable `ridesBusToWork` can hold a value of `True`, a value of `False`, or no value at all.</span></span> <span data-ttu-id="48ded-112">Jeho počáteční výchozí hodnota není vůbec žádná hodnota, což by v tomto případě mohlo znamenat, že informace ještě nebyly získány pro tuto osobu.</span><span class="sxs-lookup"><span data-stu-id="48ded-112">Its initial default value is no value at all, which in this case could mean that the information has not yet been obtained for this person.</span></span> <span data-ttu-id="48ded-113">Naproti tomu `False` by mohlo znamenat, že informace byly získány a osoba nejezdí autobusem do práce.</span><span class="sxs-lookup"><span data-stu-id="48ded-113">In contrast, `False` could mean that the information has been obtained and the person does not ride the bus to work.</span></span>

<span data-ttu-id="48ded-114">Můžete deklarovat proměnné a vlastnosti s typy hodnot s hodnotou s hodnotou null a můžete deklarovat pole s prvky typu hodnoty s možnou hodnotou, kterou lze hodnotit.</span><span class="sxs-lookup"><span data-stu-id="48ded-114">You can declare variables and properties with nullable value types, and you can declare an array with elements of a nullable value type.</span></span> <span data-ttu-id="48ded-115">Můžete deklarovat procedury s nulovými typy hodnot jako parametry `Function` a můžete vrátit typ hodnoty s možnou hodnotou s možnou hodnotou z procedury.</span><span class="sxs-lookup"><span data-stu-id="48ded-115">You can declare procedures with nullable value types as parameters, and you can return a nullable value type from a `Function` procedure.</span></span>

<span data-ttu-id="48ded-116">Nelze vytvořit typ s možnou hodnotou null pro `String`typ odkazu, jako je například pole, nebo třída.</span><span class="sxs-lookup"><span data-stu-id="48ded-116">You cannot construct a nullable type on a reference type such as an array, a `String`, or a class.</span></span> <span data-ttu-id="48ded-117">Základní typ musí být typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="48ded-117">The underlying type must be a value type.</span></span> <span data-ttu-id="48ded-118">Další informace naleznete [v tématu Typy hodnot a typy odkazů](value-types-and-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="48ded-118">For more information, see [Value Types and Reference Types](value-types-and-reference-types.md).</span></span>

## <a name="using-a-nullable-type-variable"></a><span data-ttu-id="48ded-119">Použití proměnné typu s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="48ded-119">Using a Nullable Type Variable</span></span>

<span data-ttu-id="48ded-120">Nejdůležitější členy typu hodnoty s možnou <xref:System.Nullable%601.HasValue%2A> <xref:System.Nullable%601.Value%2A> hodnotou s možnou hodnotou jsou jeho a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="48ded-120">The most important members of a nullable value type are its <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> properties.</span></span> <span data-ttu-id="48ded-121">Pro proměnnou typu hodnoty s <xref:System.Nullable%601.HasValue%2A> možnou hodnotou s možnou hodnotou s hodnotou s hodnou hodnotou se dozvíte, zda proměnná obsahuje definovanou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="48ded-121">For a variable of a nullable value type, <xref:System.Nullable%601.HasValue%2A> tells you whether the variable contains a defined value.</span></span> <span data-ttu-id="48ded-122">Pokud <xref:System.Nullable%601.HasValue%2A> `True`je , můžete číst <xref:System.Nullable%601.Value%2A>hodnotu z .</span><span class="sxs-lookup"><span data-stu-id="48ded-122">If <xref:System.Nullable%601.HasValue%2A> is `True`, you can read the value from <xref:System.Nullable%601.Value%2A>.</span></span> <span data-ttu-id="48ded-123">Všimněte <xref:System.Nullable%601.HasValue%2A> si, že oba a <xref:System.Nullable%601.Value%2A> jsou `ReadOnly` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="48ded-123">Note that both <xref:System.Nullable%601.HasValue%2A> and <xref:System.Nullable%601.Value%2A> are `ReadOnly` properties.</span></span>

### <a name="default-values"></a><span data-ttu-id="48ded-124">Výchozí hodnoty</span><span class="sxs-lookup"><span data-stu-id="48ded-124">Default Values</span></span>

<span data-ttu-id="48ded-125">Když deklarujete proměnnou s <xref:System.Nullable%601.HasValue%2A> hodnotou s `False`hodnotou s hodnotou s hodnotou s hodnotou s hodnotou null, její vlastnost má výchozí hodnotu .</span><span class="sxs-lookup"><span data-stu-id="48ded-125">When you declare a variable with a nullable value type, its <xref:System.Nullable%601.HasValue%2A> property has a default value of `False`.</span></span> <span data-ttu-id="48ded-126">To znamená, že proměnná nemá ve výchozím nastavení žádnou definovanou hodnotu namísto výchozí hodnoty jejího základního typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="48ded-126">This means that by default the variable has no defined value, instead of the default value of its underlying value type.</span></span> <span data-ttu-id="48ded-127">V následujícím příkladu `numberOfChildren` proměnná zpočátku nemá žádnou definovanou `Integer` hodnotu, i když výchozí hodnota typu je 0.</span><span class="sxs-lookup"><span data-stu-id="48ded-127">In the following example, the variable `numberOfChildren` initially has no defined value, even though the default value of the `Integer` type is 0.</span></span>

[!code-vb[VbVbalrNullableValue#2](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#2)]

<span data-ttu-id="48ded-128">Hodnota null je užitečná k označení nedefinované nebo neznámé hodnoty.</span><span class="sxs-lookup"><span data-stu-id="48ded-128">A null value is useful to indicate an undefined or unknown value.</span></span> <span data-ttu-id="48ded-129">Pokud `numberOfChildren` by byla `Integer`deklarována jako , neexistovala by žádná hodnota, která by mohla naznačovat, že informace nejsou v současné době k dispozici.</span><span class="sxs-lookup"><span data-stu-id="48ded-129">If `numberOfChildren` had been declared as `Integer`, there would be no value that could indicate that the information is not currently available.</span></span>

### <a name="storing-values"></a><span data-ttu-id="48ded-130">Ukládání hodnot</span><span class="sxs-lookup"><span data-stu-id="48ded-130">Storing Values</span></span>

<span data-ttu-id="48ded-131">Hodnotu uložte do proměnné nebo vlastnosti typu hodnoty s možnou hodnotou s možnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="48ded-131">You store a value in a variable or property of a nullable value type in the typical way.</span></span> <span data-ttu-id="48ded-132">Následující příklad přiřadí hodnotu `numberOfChildren` proměnné deklarované v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="48ded-132">The following example assigns a value to the variable `numberOfChildren` declared in the previous example.</span></span>

[!code-vb[VbVbalrNullableValue#3](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#3)]

<span data-ttu-id="48ded-133">Pokud proměnná nebo vlastnost typu hodnoty s možnou hodnotou s možnou hodnotou null obsahuje definovanou hodnotu, můžete způsobit, že se vrátí do původního stavu, kdy nemá přiřazenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="48ded-133">If a variable or property of a nullable value type contains a defined value, you can cause it to revert to its initial state of not having a value assigned.</span></span> <span data-ttu-id="48ded-134">To lze provést nastavením proměnné `Nothing`nebo vlastnosti na , jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="48ded-134">You do this by setting the variable or property to `Nothing`, as the following example shows.</span></span>

[!code-vb[VbVbalrNullableValue#4](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#4)]

> [!NOTE]
> <span data-ttu-id="48ded-135">I když `Nothing` můžete přiřadit proměnné typu hodnoty s možnou `Nothing` hodnotou, kterou lze použít pomocí rovnítku.</span><span class="sxs-lookup"><span data-stu-id="48ded-135">Although you can assign `Nothing` to a variable of a nullable value type, you cannot test it for `Nothing` by using the equal sign.</span></span> <span data-ttu-id="48ded-136">Porovnání, které používá `someVar = Nothing`znaménko `Nothing`rovná se , vždy vyhodnotí na .</span><span class="sxs-lookup"><span data-stu-id="48ded-136">Comparison that uses the equal sign, `someVar = Nothing`, always evaluates to `Nothing`.</span></span> <span data-ttu-id="48ded-137">Můžete <xref:System.Nullable%601.HasValue%2A> otestovat vlastnost proměnné `False`pro , nebo `Is` test `IsNot` pomocí operátoru nebo.</span><span class="sxs-lookup"><span data-stu-id="48ded-137">You can test the variable's <xref:System.Nullable%601.HasValue%2A> property for `False`, or test by using the `Is` or `IsNot` operator.</span></span>

### <a name="retrieving-values"></a><span data-ttu-id="48ded-138">Načítání hodnot</span><span class="sxs-lookup"><span data-stu-id="48ded-138">Retrieving Values</span></span>

<span data-ttu-id="48ded-139">Chcete-li načíst hodnotu proměnné typu hodnoty s možnou hodnotou s možnou hodnotou, měli byste nejprve otestovat její <xref:System.Nullable%601.HasValue%2A> vlastnost a potvrdit, že má hodnotu.</span><span class="sxs-lookup"><span data-stu-id="48ded-139">To retrieve the value of a variable of a nullable value type, you should first test its <xref:System.Nullable%601.HasValue%2A> property to confirm that it has a value.</span></span> <span data-ttu-id="48ded-140">Pokud se pokusíte číst <xref:System.Nullable%601.HasValue%2A> `False`hodnotu, když <xref:System.InvalidOperationException> je , Visual Basic vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="48ded-140">If you try to read the value when <xref:System.Nullable%601.HasValue%2A> is `False`, Visual Basic throws an <xref:System.InvalidOperationException> exception.</span></span> <span data-ttu-id="48ded-141">Následující příklad ukazuje doporučený způsob čtení `numberOfChildren` proměnné předchozích příkladů.</span><span class="sxs-lookup"><span data-stu-id="48ded-141">The following example shows the recommended way to read the variable `numberOfChildren` of the previous examples.</span></span>

[!code-vb[VbVbalrNullableValue#5](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#5)]

## <a name="comparing-nullable-types"></a><span data-ttu-id="48ded-142">Porovnání typů s možnou hodnotou Null</span><span class="sxs-lookup"><span data-stu-id="48ded-142">Comparing Nullable Types</span></span>

<span data-ttu-id="48ded-143">Pokud jsou `Boolean` v logických výrazech použity proměnné `True`s `False`možnou hodnotou null, může být výsledkem , nebo `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="48ded-143">When nullable `Boolean` variables are used in Boolean expressions, the result can be `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="48ded-144">Následuje tabulka pravdy `And` pro `Or`a .</span><span class="sxs-lookup"><span data-stu-id="48ded-144">The following is the truth table for `And` and `Or`.</span></span> <span data-ttu-id="48ded-145">Protože `b1` `b2` a nyní mají tři možné hodnoty, existuje devět kombinací k vyhodnocení.</span><span class="sxs-lookup"><span data-stu-id="48ded-145">Because `b1` and `b2` now have three possible values, there are nine combinations to evaluate.</span></span>

|<span data-ttu-id="48ded-146">b1</span><span class="sxs-lookup"><span data-stu-id="48ded-146">b1</span></span>|<span data-ttu-id="48ded-147">B2</span><span class="sxs-lookup"><span data-stu-id="48ded-147">b2</span></span>|<span data-ttu-id="48ded-148">b1 A b2</span><span class="sxs-lookup"><span data-stu-id="48ded-148">b1 And b2</span></span>|<span data-ttu-id="48ded-149">b1 nebo b2</span><span class="sxs-lookup"><span data-stu-id="48ded-149">b1 Or b2</span></span>|
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

<span data-ttu-id="48ded-150">Pokud je `Nothing`hodnota boolean proměnné nebo výrazu `true` , `false`není ani ani .</span><span class="sxs-lookup"><span data-stu-id="48ded-150">When the value of a Boolean variable or expression is `Nothing`, it is neither `true` nor `false`.</span></span> <span data-ttu-id="48ded-151">Představte si následující příklad.</span><span class="sxs-lookup"><span data-stu-id="48ded-151">Consider the following example.</span></span>

[!code-vb[VbVbalrNullableValue#6](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#6)]

<span data-ttu-id="48ded-152">V tomto `b1 And b2` příkladu `Nothing`vyhodnotí .</span><span class="sxs-lookup"><span data-stu-id="48ded-152">In this example, `b1 And b2` evaluates to `Nothing`.</span></span> <span data-ttu-id="48ded-153">V důsledku toho `Else` je klauzule `If` provedena v každém příkazu a výstup je následující:</span><span class="sxs-lookup"><span data-stu-id="48ded-153">As a result, the `Else` clause is executed in each `If` statement, and the output is as follows:</span></span>

`Expression is not true`

`Expression is not false`

> [!NOTE]
> <span data-ttu-id="48ded-154">`AndAlso`a `OrElse`, které používají zkrat hodnocení, musí vyhodnotit jejich druhé `Nothing`operandy, když první vyhodnotí na .</span><span class="sxs-lookup"><span data-stu-id="48ded-154">`AndAlso` and `OrElse`, which use short-circuit evaluation, must evaluate their second operands when the first evaluates to `Nothing`.</span></span>

## <a name="propagation"></a><span data-ttu-id="48ded-155">Šíření</span><span class="sxs-lookup"><span data-stu-id="48ded-155">Propagation</span></span>

<span data-ttu-id="48ded-156">Pokud jeden nebo oba operandy operace aritmetiky, porovnání, shift nebo typu je typ s hodnotou s možnou hodnotou s hodnotou s možnou hodnotou, je výsledkem operace také typ hodnoty s možnou hodnotou s možnou hodnotou s možnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="48ded-156">If one or both of the operands of an arithmetic, comparison, shift, or type operation is a nullable value type, the result of the operation is also a nullable value type.</span></span> <span data-ttu-id="48ded-157">Pokud oba operandy mají `Nothing`hodnoty, které nejsou , operace se provádí na základní hodnoty operandů, jako by ani byl typ hodnoty s možnou hodnotou s hodnotou.</span><span class="sxs-lookup"><span data-stu-id="48ded-157">If both operands have values that are not `Nothing`, the operation is performed on the underlying values of the operands, as if neither were a nullable value type.</span></span> <span data-ttu-id="48ded-158">V následujícím příkladu `compare1` proměnné `sum1` a jsou implicitně zadány.</span><span class="sxs-lookup"><span data-stu-id="48ded-158">In the following example, variables `compare1` and `sum1` are implicitly typed.</span></span> <span data-ttu-id="48ded-159">Pokud na ně položíte ukazatel myši, uvidíte, že kompilátor odvodí typy hodnot s možnou hodnotou s možnou hodnotou pro oba.</span><span class="sxs-lookup"><span data-stu-id="48ded-159">If you rest the mouse pointer over them, you will see that the compiler infers nullable value types for both of them.</span></span>

[!code-vb[VbVbalrNullableValue#7](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#7)]

<span data-ttu-id="48ded-160">Pokud jeden nebo oba operandy `Nothing`mají hodnotu `Nothing`, bude výsledkem .</span><span class="sxs-lookup"><span data-stu-id="48ded-160">If one or both operands have a value of `Nothing`, the result will be `Nothing`.</span></span>

[!code-vb[VbVbalrNullableValue#8](../../../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrNullableValue/VB/Class1.vb#8)]

## <a name="using-nullable-types-with-data"></a><span data-ttu-id="48ded-161">Použití typů s hodnotou Null s daty</span><span class="sxs-lookup"><span data-stu-id="48ded-161">Using Nullable Types with Data</span></span>

<span data-ttu-id="48ded-162">Databáze je jedním z nejdůležitějších míst pro použití typů hodnot s možnou hodnotou s možnou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="48ded-162">A database is one of the most important places to use nullable value types.</span></span> <span data-ttu-id="48ded-163">Ne všechny databázové objekty aktuálně podporují typy hodnot s možnou hodnotou null, ale adaptéry tabulky generované návrhářem.</span><span class="sxs-lookup"><span data-stu-id="48ded-163">Not all database objects currently support nullable value types, but the designer-generated table adapters do.</span></span> <span data-ttu-id="48ded-164">Viz [Podpora tableadapter pro typy s možnou hodnotou null](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span><span class="sxs-lookup"><span data-stu-id="48ded-164">See [TableAdapter support for nullable types](/visualstudio/data-tools/fill-datasets-by-using-tableadapters#tableadapter-support-for-nullable-types).</span></span>

## <a name="see-also"></a><span data-ttu-id="48ded-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="48ded-165">See also</span></span>

- <xref:System.InvalidOperationException>
- <xref:System.Nullable%601.HasValue%2A>
- [<span data-ttu-id="48ded-166">Datové typy</span><span class="sxs-lookup"><span data-stu-id="48ded-166">Data Types</span></span>](index.md)
- [<span data-ttu-id="48ded-167">Typy hodnot a odkazové typy</span><span class="sxs-lookup"><span data-stu-id="48ded-167">Value Types and Reference Types</span></span>](value-types-and-reference-types.md)
- [<span data-ttu-id="48ded-168">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="48ded-168">Troubleshooting Data Types</span></span>](troubleshooting-data-types.md)
- [<span data-ttu-id="48ded-169">Vyplnění datových sad pomocí objektů TableAdapter</span><span class="sxs-lookup"><span data-stu-id="48ded-169">Fill datasets by using TableAdapters</span></span>](/visualstudio/data-tools/fill-datasets-by-using-tableadapters)
- [<span data-ttu-id="48ded-170">Operátor If</span><span class="sxs-lookup"><span data-stu-id="48ded-170">If Operator</span></span>](../../../language-reference/operators/if-operator.md)
- [<span data-ttu-id="48ded-171">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="48ded-171">Local Type Inference</span></span>](../variables/local-type-inference.md)
- [<span data-ttu-id="48ded-172">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="48ded-172">Is Operator</span></span>](../../../language-reference/operators/is-operator.md)
- [<span data-ttu-id="48ded-173">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="48ded-173">IsNot Operator</span></span>](../../../language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="48ded-174">Typy hodnot s hodnotou s hodnotou null (C#)</span><span class="sxs-lookup"><span data-stu-id="48ded-174">Nullable Value Types (C#)</span></span>](../../../../csharp/language-reference/builtin-types/nullable-value-types.md)
