---
title: CType – funkce
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: 88d609146648fe1b0c3124b99a65e85293fc0707
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406427"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="416d6-102">CType – funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="416d6-102">CType Function (Visual Basic)</span></span>

<span data-ttu-id="416d6-103">Vrátí výsledek explicitního převodu výrazu na zadaný datový typ, objekt, strukturu, třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="416d6-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="416d6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="416d6-104">Syntax</span></span>

```vb
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="416d6-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="416d6-105">Parts</span></span>

<span data-ttu-id="416d6-106">`expression`Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="416d6-106">`expression` Any valid expression.</span></span> <span data-ttu-id="416d6-107">Pokud `expression` je hodnota mimo rozsah povolený `typename` , Visual Basic vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="416d6-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="416d6-108">`typename`Libovolný výraz, který je platný v rámci `As` klauzule v `Dim` příkazu, to znamená název libovolného datového typu, objektu, struktury, třídy nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="416d6-108">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="416d6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="416d6-109">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="416d6-110">K provedení převodu typu můžete použít taky následující funkce:</span><span class="sxs-lookup"><span data-stu-id="416d6-110">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="416d6-111">Funkce pro převod typů `CByte` , například, `CDbl` a `CInt` , které provádějí převod na konkrétní datový typ.</span><span class="sxs-lookup"><span data-stu-id="416d6-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="416d6-112">Další informace najdete v tématu [funkce pro převod typů](type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="416d6-112">For more information, see [Type Conversion Functions](type-conversion-functions.md).</span></span>
> - <span data-ttu-id="416d6-113">[Operátor DirectCast](../operators/directcast-operator.md) nebo [operátor TryCast](../operators/trycast-operator.md)</span><span class="sxs-lookup"><span data-stu-id="416d6-113">[DirectCast Operator](../operators/directcast-operator.md) or [TryCast Operator](../operators/trycast-operator.md).</span></span> <span data-ttu-id="416d6-114">Tyto operátory vyžadují, aby jeden typ dědil z nebo implementoval jiný typ.</span><span class="sxs-lookup"><span data-stu-id="416d6-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="416d6-115">Můžou poskytovat poněkud lepší výkon než `CType` při převodu do a z `Object` datového typu.</span><span class="sxs-lookup"><span data-stu-id="416d6-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="416d6-116">`CType`je zkompilována jako vložená, což znamená, že kód převodu je součástí kódu, který vyhodnocuje výraz.</span><span class="sxs-lookup"><span data-stu-id="416d6-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="416d6-117">V některých případech kód běží rychleji, protože pro provedení převodu nejsou volány žádné procedury.</span><span class="sxs-lookup"><span data-stu-id="416d6-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="416d6-118">Pokud není definován žádný převod z `expression` na `typename` (například z `Integer` na `Date` ), Visual Basic zobrazí chybovou zprávu při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="416d6-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="416d6-119">Pokud se převod v době běhu nezdařil, je vyvolána příslušná výjimka.</span><span class="sxs-lookup"><span data-stu-id="416d6-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="416d6-120">V případě neúspěchu zužujícího převodu <xref:System.OverflowException> je nejčastější výsledek.</span><span class="sxs-lookup"><span data-stu-id="416d6-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="416d6-121">Pokud převod není definován, je <xref:System.InvalidCastException> vyvolána.</span><span class="sxs-lookup"><span data-stu-id="416d6-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="416d6-122">Například k tomu může dojít, pokud `expression` je typ `Object` a jeho typ za běhu nemá konverzi na `typename` .</span><span class="sxs-lookup"><span data-stu-id="416d6-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="416d6-123">Pokud datový typ `expression` nebo `typename` je třída nebo struktura, kterou jste definovali, můžete definovat `CType` v této třídě nebo struktuře jako operátor převodu.</span><span class="sxs-lookup"><span data-stu-id="416d6-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="416d6-124">To slouží `CType` jako *přetížený operátor*.</span><span class="sxs-lookup"><span data-stu-id="416d6-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="416d6-125">Pokud to uděláte, můžete řídit chování převodu do a z vaší třídy nebo struktury, včetně výjimek, které mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="416d6-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="416d6-126">Přetížení</span><span class="sxs-lookup"><span data-stu-id="416d6-126">Overloading</span></span>

<span data-ttu-id="416d6-127">`CType`Operátor může být také přetížen pro třídu nebo strukturu definovanou mimo váš kód.</span><span class="sxs-lookup"><span data-stu-id="416d6-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="416d6-128">Pokud se váš kód převede na nebo z takové třídy nebo struktury, ujistěte se, že rozumíte chování `CType` operátoru.</span><span class="sxs-lookup"><span data-stu-id="416d6-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="416d6-129">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="416d6-129">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="416d6-130">Převod dynamických objektů</span><span class="sxs-lookup"><span data-stu-id="416d6-130">Converting Dynamic Objects</span></span>

<span data-ttu-id="416d6-131">Převody typů dynamických objektů jsou prováděny uživatelsky definovanými dynamickými převody, které používají <xref:System.Dynamic.DynamicObject.TryConvert%2A> <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> metody nebo.</span><span class="sxs-lookup"><span data-stu-id="416d6-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="416d6-132">Pokud pracujete s dynamickými objekty, použijte <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> metodu pro převod dynamického objektu.</span><span class="sxs-lookup"><span data-stu-id="416d6-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="416d6-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="416d6-133">Example</span></span>

<span data-ttu-id="416d6-134">Následující příklad používá `CType` funkci k převodu výrazu na `Single` datový typ.</span><span class="sxs-lookup"><span data-stu-id="416d6-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="416d6-135">Další příklady naleznete v tématu [implicitní a explicitní převody](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="416d6-135">For additional examples, see [Implicit and Explicit Conversions](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="416d6-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="416d6-136">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="416d6-137">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="416d6-137">Type Conversion Functions</span></span>](type-conversion-functions.md)
- [<span data-ttu-id="416d6-138">Převodní funkce</span><span class="sxs-lookup"><span data-stu-id="416d6-138">Conversion Functions</span></span>](conversion-functions.md)
- [<span data-ttu-id="416d6-139">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="416d6-139">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="416d6-140">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="416d6-140">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="416d6-141">Převod typů v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="416d6-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
