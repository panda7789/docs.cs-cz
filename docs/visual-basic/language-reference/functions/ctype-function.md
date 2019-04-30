---
title: CType – funkce (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
ms.openlocfilehash: dbf01263723a9e2890dab57d5ffc3d467ed250fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801676"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="af2f0-102">CType – funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af2f0-102">CType Function (Visual Basic)</span></span>

<span data-ttu-id="af2f0-103">Vrátí výsledek explicitně převedeného výrazu na zadaný datový typ, objekt, strukturu, třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="af2f0-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="af2f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af2f0-104">Syntax</span></span>

```
CType(expression, typename)
```

## <a name="parts"></a><span data-ttu-id="af2f0-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="af2f0-105">Parts</span></span>

<span data-ttu-id="af2f0-106">`expression` Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="af2f0-106">`expression` Any valid expression.</span></span> <span data-ttu-id="af2f0-107">Pokud hodnota `expression` je mimo povolený rozsah povolený `typename`, Visual Basic vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="af2f0-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>

<span data-ttu-id="af2f0-108">`typename` Libovolný výraz, který je platný v rámci `As` klauzule `Dim` příkazu, to znamená, že název všechny datový typ, objekt, strukturu, třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="af2f0-108">`typename` Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>

## <a name="remarks"></a><span data-ttu-id="af2f0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af2f0-109">Remarks</span></span>

> [!TIP]
> <span data-ttu-id="af2f0-110">K provedení převodu typu můžete také použít následující funkce:</span><span class="sxs-lookup"><span data-stu-id="af2f0-110">You can also use the following functions to perform a type conversion:</span></span>
>
> - <span data-ttu-id="af2f0-111">Například zadejte funkce pro převod `CByte`, `CDbl`, a `CInt` , které provádí převod na určitý datový typ.</span><span class="sxs-lookup"><span data-stu-id="af2f0-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="af2f0-112">Další informace najdete v tématu [funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="af2f0-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>
> - <span data-ttu-id="af2f0-113">[DirectCast – operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) nebo [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="af2f0-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="af2f0-114">Tyto operátory vyžadují dědit z jednoho typu nebo implementaci druhého typu.</span><span class="sxs-lookup"><span data-stu-id="af2f0-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="af2f0-115">Poskytují poněkud vyšší výkon než `CType` při převodu do a z `Object` datového typu.</span><span class="sxs-lookup"><span data-stu-id="af2f0-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>

<span data-ttu-id="af2f0-116">`CType` je zkompilovaný vloženě, což znamená, že kód převodu je součástí kódu, který se vyhodnotí výraz.</span><span class="sxs-lookup"><span data-stu-id="af2f0-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="af2f0-117">V některých případech kód běží rychleji, protože nejsou volány žádné procedury k provedení převodu.</span><span class="sxs-lookup"><span data-stu-id="af2f0-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>

<span data-ttu-id="af2f0-118">Pokud není definován žádný převod z `expression` k `typename` (např. z `Integer` k `Date`), Visual Basic zobrazí zprávu Chyba kompilace.</span><span class="sxs-lookup"><span data-stu-id="af2f0-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>

<span data-ttu-id="af2f0-119">Pokud převod selže v době běhu, je vyvolána vhodná výjimka.</span><span class="sxs-lookup"><span data-stu-id="af2f0-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="af2f0-120">Pokud selže zužující převod <xref:System.OverflowException> je nejčastěji výsledkem.</span><span class="sxs-lookup"><span data-stu-id="af2f0-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="af2f0-121">Pokud převod není definován, <xref:System.InvalidCastException> v vyvolána.</span><span class="sxs-lookup"><span data-stu-id="af2f0-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="af2f0-122">Například to může nastat, když `expression` je typu `Object` a jeho typ za běhu nemá převod do `typename`.</span><span class="sxs-lookup"><span data-stu-id="af2f0-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>

<span data-ttu-id="af2f0-123">Pokud datový typ `expression` nebo `typename` je třída nebo struktura, které jste definovali, můžete definovat `CType` na této třídě nebo struktuře jako operátor převodu.</span><span class="sxs-lookup"><span data-stu-id="af2f0-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="af2f0-124">Díky tomu `CType` fungovat jako *přetížený operátor*.</span><span class="sxs-lookup"><span data-stu-id="af2f0-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="af2f0-125">Pokud to uděláte, můžete řídit chování převodu do a z třídy nebo struktury, včetně výjimek, které mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="af2f0-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>

## <a name="overloading"></a><span data-ttu-id="af2f0-126">Přetížení</span><span class="sxs-lookup"><span data-stu-id="af2f0-126">Overloading</span></span>

<span data-ttu-id="af2f0-127">`CType` Operátoru lze také přetížit ve třídě nebo struktuře definované mimo váš kód.</span><span class="sxs-lookup"><span data-stu-id="af2f0-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="af2f0-128">Pokud váš kód převede do nebo z takové třídy nebo struktury, měli byste pochopit chování jeho `CType` operátor.</span><span class="sxs-lookup"><span data-stu-id="af2f0-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="af2f0-129">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="af2f0-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>

## <a name="converting-dynamic-objects"></a><span data-ttu-id="af2f0-130">Převod dynamických objektů</span><span class="sxs-lookup"><span data-stu-id="af2f0-130">Converting Dynamic Objects</span></span>

<span data-ttu-id="af2f0-131">Uživatelem definované dynamickými konverzemi pomocí provádí převody typů dynamických objektů <xref:System.Dynamic.DynamicObject.TryConvert%2A> nebo <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="af2f0-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="af2f0-132">Pokud pracujete s dynamickými objekty, použijte <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> metody pro převod dynamického objektu.</span><span class="sxs-lookup"><span data-stu-id="af2f0-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>

## <a name="example"></a><span data-ttu-id="af2f0-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="af2f0-133">Example</span></span>

<span data-ttu-id="af2f0-134">V následujícím příkladu `CType` funkce převodu výrazu `Single` datového typu.</span><span class="sxs-lookup"><span data-stu-id="af2f0-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>

[!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]

<span data-ttu-id="af2f0-135">Další příklady najdete v tématu [implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="af2f0-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="af2f0-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af2f0-136">See also</span></span>

- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="af2f0-137">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="af2f0-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="af2f0-138">Převodní funkce</span><span class="sxs-lookup"><span data-stu-id="af2f0-138">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="af2f0-139">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="af2f0-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="af2f0-140">Postupy: Definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="af2f0-140">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="af2f0-141">Převod typů v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="af2f0-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
