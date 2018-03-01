---
title: "CType – funkce (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.CType
helpviewer_keywords:
- expression conversion results
- explicit data type conversions [Visual Basic]
- CType function
- conversions [Visual Basic], expression
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d804ce75929592675068fdc434a1ba7429fa5373
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ctype-function-visual-basic"></a><span data-ttu-id="d9117-102">CType – funkce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d9117-102">CType Function (Visual Basic)</span></span>
<span data-ttu-id="d9117-103">Vrátí výsledek převodu explicitně výraz zadaný datový typ, objekt, struktura, třídu nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d9117-103">Returns the result of explicitly converting an expression to a specified data type, object, structure, class, or interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9117-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9117-104">Syntax</span></span>  
  
```  
CType(expression, typename)  
```  
  
## <a name="parts"></a><span data-ttu-id="d9117-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="d9117-105">Parts</span></span>  
 `expression`  
 <span data-ttu-id="d9117-106">Jakýkoli platný výraz.</span><span class="sxs-lookup"><span data-stu-id="d9117-106">Any valid expression.</span></span> <span data-ttu-id="d9117-107">Pokud hodnota `expression` je mimo povolený rozsah `typename`, vyvolá výjimku, Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d9117-107">If the value of `expression` is outside the range allowed by `typename`, Visual Basic throws an exception.</span></span>  
  
 `typename`  
 <span data-ttu-id="d9117-108">Libovolný výraz, který je právní v rámci `As` klauzuli v `Dim` prohlášení, to znamená, název žádné datový typ, objekt, struktura, třída nebo rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d9117-108">Any expression that is legal within an `As` clause in a `Dim` statement, that is, the name of any data type, object, structure, class, or interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9117-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d9117-109">Remarks</span></span>  
  
> [!TIP]
>  <span data-ttu-id="d9117-110">Následující funkce můžete využít taky k převodu typu:</span><span class="sxs-lookup"><span data-stu-id="d9117-110">You can also use the following functions to perform a type conversion:</span></span>  
>   
>  -   <span data-ttu-id="d9117-111">Zadejte například funkce pro převod `CByte`, `CDbl`, a `CInt` , proveďte převod na typ konkrétní.</span><span class="sxs-lookup"><span data-stu-id="d9117-111">Type conversion functions such as `CByte`, `CDbl`, and `CInt` that perform a conversion to a specific data type.</span></span> <span data-ttu-id="d9117-112">Další informace najdete v tématu [funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="d9117-112">For more information, see [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md).</span></span>  
> -   <span data-ttu-id="d9117-113">[DirectCast – operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) nebo [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d9117-113">[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) or [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span> <span data-ttu-id="d9117-114">Tyto operátory požadovat, aby jeden typ dědí nebo implementovat v případě druhého typu.</span><span class="sxs-lookup"><span data-stu-id="d9117-114">These operators require that one type inherit from or implement the other type.</span></span> <span data-ttu-id="d9117-115">Poskytují poněkud lepší výkon než `CType` při převodu do a z `Object` datového typu.</span><span class="sxs-lookup"><span data-stu-id="d9117-115">They can provide somewhat better performance than `CType` when converting to and from the `Object` data type.</span></span>  
  
 <span data-ttu-id="d9117-116">`CType`je zkompilovaná vložená, což znamená, že převod kódu je součástí kód, který se vyhodnotí výraz.</span><span class="sxs-lookup"><span data-stu-id="d9117-116">`CType` is compiled inline, which means that the conversion code is part of the code that evaluates the expression.</span></span> <span data-ttu-id="d9117-117">V některých případech kód spustí rychleji, protože žádné procedury se nazývají provést převod.</span><span class="sxs-lookup"><span data-stu-id="d9117-117">In some cases, the code runs faster because no procedures are called to perform the conversion.</span></span>  
  
 <span data-ttu-id="d9117-118">Pokud je definovaný žádný převod z `expression` k `typename` (například z `Integer` k `Date`), Visual Basic zobrazí kompilaci chybová zpráva.</span><span class="sxs-lookup"><span data-stu-id="d9117-118">If no conversion is defined from `expression` to `typename` (for example, from `Integer` to `Date`), Visual Basic displays a compile-time error message.</span></span>  
  
 <span data-ttu-id="d9117-119">Pokud se nezdaří převod za běhu, je vyvolána příslušné výjimky.</span><span class="sxs-lookup"><span data-stu-id="d9117-119">If a conversion fails at run time, the appropriate exception is thrown.</span></span> <span data-ttu-id="d9117-120">Pokud se zužující převod nezdaří, <xref:System.OverflowException> nejběžnější výsledek.</span><span class="sxs-lookup"><span data-stu-id="d9117-120">If a narrowing conversion fails, an <xref:System.OverflowException> is the most common result.</span></span> <span data-ttu-id="d9117-121">Pokud není definován, převod <xref:System.InvalidCastException> v vyvolána.</span><span class="sxs-lookup"><span data-stu-id="d9117-121">If the conversion is undefined, an <xref:System.InvalidCastException> in thrown.</span></span> <span data-ttu-id="d9117-122">Například k tomu může dojít, pokud `expression` je typu `Object` a její typ spuštění nemá žádný převod do `typename`.</span><span class="sxs-lookup"><span data-stu-id="d9117-122">For example, this can happen  if `expression` is of type `Object` and its run-time type has no conversion to `typename`.</span></span>  
  
 <span data-ttu-id="d9117-123">Pokud datový typ `expression` nebo `typename` je třídu nebo strukturu, které jste definovali, můžete definovat `CType` na tuto třídu nebo strukturu jako operátor převodu.</span><span class="sxs-lookup"><span data-stu-id="d9117-123">If the data type of `expression` or `typename` is a class or structure you've defined, you can define `CType` on that class or structure as a conversion operator.</span></span> <span data-ttu-id="d9117-124">Díky tomu `CType` fungovat jako *přetížený operátor*.</span><span class="sxs-lookup"><span data-stu-id="d9117-124">This makes `CType` act as an *overloaded operator*.</span></span> <span data-ttu-id="d9117-125">Pokud to uděláte, můžete řídit chování převod na a z třídy nebo struktura, včetně výjimky, které může být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="d9117-125">If you do this, you can control the behavior of conversions to and from your class or structure, including the exceptions that can be thrown.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="d9117-126">Přetížení</span><span class="sxs-lookup"><span data-stu-id="d9117-126">Overloading</span></span>  
 <span data-ttu-id="d9117-127">`CType` Operátor mohou být přetíženy také na třídu nebo strukturu definované mimo váš kód.</span><span class="sxs-lookup"><span data-stu-id="d9117-127">The `CType` operator can also be overloaded on a class or structure defined outside your code.</span></span> <span data-ttu-id="d9117-128">Pokud váš kód převede do nebo z takových třídu nebo strukturu, ujistěte se, pochopit chování jeho `CType` operátor.</span><span class="sxs-lookup"><span data-stu-id="d9117-128">If your code converts to or from such a class or structure, be sure you understand the behavior of its `CType` operator.</span></span> <span data-ttu-id="d9117-129">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="d9117-129">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="converting-dynamic-objects"></a><span data-ttu-id="d9117-130">Převedení dynamických objektů</span><span class="sxs-lookup"><span data-stu-id="d9117-130">Converting Dynamic Objects</span></span>  
 <span data-ttu-id="d9117-131">Převody typů objektů dynamické provádí dynamické převody definovaný uživatelem, které používají <xref:System.Dynamic.DynamicObject.TryConvert%2A> nebo <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d9117-131">Type conversions of dynamic objects are performed by user-defined dynamic conversions that use the <xref:System.Dynamic.DynamicObject.TryConvert%2A> or <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> methods.</span></span> <span data-ttu-id="d9117-132">Pokud pracujete s dynamickými objekty, použijte <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> způsobů, jak převést dynamický objekt.</span><span class="sxs-lookup"><span data-stu-id="d9117-132">If you're working with dynamic objects, use the <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> method to convert the dynamic object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9117-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9117-133">Example</span></span>  
 <span data-ttu-id="d9117-134">Následující příklad používá `CType` funkce pro převod výraz, který se `Single` datového typu.</span><span class="sxs-lookup"><span data-stu-id="d9117-134">The following example uses the `CType` function to convert an expression to the `Single` data type.</span></span>  
  
 [!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]  
  
 <span data-ttu-id="d9117-135">Další příklady najdete v tématu [implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="d9117-135">For additional examples, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9117-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9117-136">See Also</span></span>  
 <xref:System.OverflowException>  
 <xref:System.InvalidCastException>  
 [<span data-ttu-id="d9117-137">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="d9117-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="d9117-138">Převodní funkce</span><span class="sxs-lookup"><span data-stu-id="d9117-138">Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [<span data-ttu-id="d9117-139">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="d9117-139">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="d9117-140">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="d9117-140">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="d9117-141">Převod typů v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d9117-141">Type Conversion in the .NET Framework</span></span>](../../../standard/base-types/type-conversion.md)
