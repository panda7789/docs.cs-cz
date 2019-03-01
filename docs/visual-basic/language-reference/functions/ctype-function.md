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
ms.openlocfilehash: 8f60edb2b5e2dba15526169ef10bc05c1f50a7f1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970009"
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="a4769-102">CType – funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a4769-102">CType Function (Visual Basic)</span></span>
<span data-ttu-id="a4769-103">Vrátí výsledek explicitně převedeného výrazu na zadaný datový typ, objekt, strukturu, třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a4769-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4769-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4769-104">Syntax</span></span>  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a><span data-ttu-id="a4769-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="a4769-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="a4769-106">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="a4769-106">Any valid expression.</span></span> <span data-ttu-id="a4769-107">Pokud hodnota `expression` je mimo povolený rozsah povolený `typename`, Visual Basic vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="a4769-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>  
  
 `typename`  
 <span data-ttu-id="a4769-108">Libovolný výraz, který je platný v rámci `As` klauzule `Dim` příkazu, to znamená, že název všechny datový typ, objekt, strukturu, třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a4769-108">Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4769-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4769-109">Remarks</span></span>  
  
> [!TIP]
>  <span data-ttu-id="a4769-110">K provedení převodu typu můžete také použít následující funkce:</span><span class="sxs-lookup"><span data-stu-id="a4769-110">You can also use the following functions to perform a type conversion:</span></span>  
>   
>  -   <span data-ttu-id="a4769-111">Například zadejte funkce pro převod `CByte`, `CDbl`, a `CInt` , které provádí převod na určitý datový typ.</span><span class="sxs-lookup"><span data-stu-id="a4769-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="a4769-112">Další informace najdete v tématu [funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="a4769-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
> -   <span data-ttu-id="a4769-113">[DirectCast – operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) nebo [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="a4769-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="a4769-114">Tyto operátory vyžadují dědit z jednoho typu nebo implementaci druhého typu.</span><span class="sxs-lookup"><span data-stu-id="a4769-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="a4769-115">Poskytují poněkud vyšší výkon než `CType` při převodu do a z `Object` datového typu.</span><span class="sxs-lookup"><span data-stu-id="a4769-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>  
  
 <span data-ttu-id="a4769-116">`CType` je zkompilovaný vloženě, což znamená, že kód převodu je součástí kódu, který se vyhodnotí výraz.</span><span class="sxs-lookup"><span data-stu-id="a4769-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="a4769-117">V některých případech kód běží rychleji, protože nejsou volány žádné procedury k provedení převodu.</span><span class="sxs-lookup"><span data-stu-id="a4769-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>  
  
 <span data-ttu-id="a4769-118">Pokud není definován žádný převod z `expression` k `typename` (např. z `Integer` k `Date`), Visual Basic zobrazí zprávu Chyba kompilace.</span><span class="sxs-lookup"><span data-stu-id="a4769-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>  
  
 <span data-ttu-id="a4769-119">Pokud převod selže v době běhu, je vyvolána vhodná výjimka.</span><span class="sxs-lookup"><span data-stu-id="a4769-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="a4769-120">Pokud selže zužující převod <xref:System.OverflowException> je nejčastěji výsledkem.</span><span class="sxs-lookup"><span data-stu-id="a4769-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="a4769-121">Pokud převod není definován, <xref:System.InvalidCastException> v vyvolána.</span><span class="sxs-lookup"><span data-stu-id="a4769-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="a4769-122">Například to může nastat, když `expression` je typu `Object` a jeho typ za běhu nemá převod do `typename`.</span><span class="sxs-lookup"><span data-stu-id="a4769-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>  
  
 <span data-ttu-id="a4769-123">Pokud datový typ `expression` nebo `typename` je třída nebo struktura, které jste definovali, můžete definovat `CType` na této třídě nebo struktuře jako operátor převodu.</span><span class="sxs-lookup"><span data-stu-id="a4769-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="a4769-124">Díky tomu `CType` fungovat jako *přetížený operátor*.</span><span class="sxs-lookup"><span data-stu-id="a4769-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="a4769-125">Pokud to uděláte, můžete řídit chování převodu do a z třídy nebo struktury, včetně výjimek, které mohou být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="a4769-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="a4769-126">Přetížení</span><span class="sxs-lookup"><span data-stu-id="a4769-126">Overloading</span></span>  
 <span data-ttu-id="a4769-127">`CType` Operátoru lze také přetížit ve třídě nebo struktuře definované mimo váš kód.</span><span class="sxs-lookup"><span data-stu-id="a4769-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="a4769-128">Pokud váš kód převede do nebo z takové třídy nebo struktury, měli byste pochopit chování jeho `CType` operátor.</span><span class="sxs-lookup"><span data-stu-id="a4769-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="a4769-129">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a4769-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="converting-dynamic-objects"></a><span data-ttu-id="a4769-130">Převod dynamických objektů</span><span class="sxs-lookup"><span data-stu-id="a4769-130">Converting Dynamic Objects</span></span>  
 <span data-ttu-id="a4769-131">Uživatelem definované dynamickými konverzemi pomocí provádí převody typů dynamických objektů <xref:System.Dynamic.DynamicObject.TryConvert%2A> nebo <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="a4769-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="a4769-132">Pokud pracujete s dynamickými objekty, použijte <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> metody pro převod dynamického objektu.</span><span class="sxs-lookup"><span data-stu-id="a4769-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4769-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4769-133">Example</span></span>  
 <span data-ttu-id="a4769-134">V následujícím příkladu `CType` funkce převodu výrazu `Single` datového typu.</span><span class="sxs-lookup"><span data-stu-id="a4769-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#24)]  
  
 <span data-ttu-id="a4769-135">Další příklady najdete v tématu [implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="a4769-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4769-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4769-136">See also</span></span>
- <xref:System.OverflowException>
- <xref:System.InvalidCastException>
- [<span data-ttu-id="a4769-137">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="a4769-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="a4769-138">Převodní funkce</span><span class="sxs-lookup"><span data-stu-id="a4769-138">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [<span data-ttu-id="a4769-139">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="a4769-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="a4769-140">Postupy: Definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="a4769-140">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="a4769-141">Převod typů v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a4769-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
