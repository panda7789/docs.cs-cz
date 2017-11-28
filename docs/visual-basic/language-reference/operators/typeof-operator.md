---
title: "TypeOf – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 51bd2af7af28aa229fa62770c5b92d31e461333b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="ee297-102">TypeOf – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ee297-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="ee297-103">Porovná proměnná odkaz objektu k datovému typu.</span><span class="sxs-lookup"><span data-stu-id="ee297-103">Compares an object reference variable to a data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee297-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ee297-104">Syntax</span></span>  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="ee297-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ee297-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="ee297-106">Vrátí.</span><span class="sxs-lookup"><span data-stu-id="ee297-106">Returned.</span></span> <span data-ttu-id="ee297-107">A `Boolean` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ee297-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="ee297-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ee297-108">Required.</span></span> <span data-ttu-id="ee297-109">Jakýkoli výraz, jehož výsledkem odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="ee297-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="ee297-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ee297-110">Required.</span></span> <span data-ttu-id="ee297-111">Všechna data, zadejte název.</span><span class="sxs-lookup"><span data-stu-id="ee297-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee297-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee297-112">Remarks</span></span>  
 <span data-ttu-id="ee297-113">`TypeOf` Operátor určuje, zda běhu typ `objectexpression` je kompatibilní s `typename`.</span><span class="sxs-lookup"><span data-stu-id="ee297-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="ee297-114">Kompatibility závisí na typu kategorii `typename`.</span><span class="sxs-lookup"><span data-stu-id="ee297-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="ee297-115">Následující tabulka uvádí, jakým způsobem je určován kompatibility.</span><span class="sxs-lookup"><span data-stu-id="ee297-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="ee297-116">Typ kategorie`typename`</span><span class="sxs-lookup"><span data-stu-id="ee297-116">Type category of `typename`</span></span>|<span data-ttu-id="ee297-117">Kritérium kompatibility</span><span class="sxs-lookup"><span data-stu-id="ee297-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="ee297-118">Třída</span><span class="sxs-lookup"><span data-stu-id="ee297-118">Class</span></span>|<span data-ttu-id="ee297-119">`objectexpression`je typu `typename` nebo dědí z`typename`</span><span class="sxs-lookup"><span data-stu-id="ee297-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="ee297-120">Struktura</span><span class="sxs-lookup"><span data-stu-id="ee297-120">Structure</span></span>|<span data-ttu-id="ee297-121">`objectexpression`je typu`typename`</span><span class="sxs-lookup"><span data-stu-id="ee297-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="ee297-122">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="ee297-122">Interface</span></span>|<span data-ttu-id="ee297-123">`objectexpression`implementuje `typename` nebo dědí z třídy, který implementuje`typename`</span><span class="sxs-lookup"><span data-stu-id="ee297-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="ee297-124">Pokud běhu typ `objectexpression` splňuje kritéria kompatibility `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="ee297-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="ee297-125">V opačném `result` je `False`.</span><span class="sxs-lookup"><span data-stu-id="ee297-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="ee297-126">Pokud `objectexpression` má hodnotu null, pak `TypeOf`... `Is` vrátí `False`, a... `IsNot` vrátí `True`.</span><span class="sxs-lookup"><span data-stu-id="ee297-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="ee297-127">`TypeOf`vždy používá s `Is` – klíčové slovo vytvořit `TypeOf`... `Is` výrazu, nebo pomocí `IsNot` – klíčové slovo vytvořit `TypeOf`... `IsNot` výraz.</span><span class="sxs-lookup"><span data-stu-id="ee297-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee297-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee297-128">Example</span></span>  
 <span data-ttu-id="ee297-129">Následující příklad používá `TypeOf`... `Is` výrazy pro testování kompatibility typu dva objektu referenční proměnné s různými datovými typy.</span><span class="sxs-lookup"><span data-stu-id="ee297-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]  
  
 <span data-ttu-id="ee297-130">Proměnná `refInteger` má typ spuštění `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ee297-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="ee297-131">Je kompatibilní s `Integer` , ale ne při `Double`.</span><span class="sxs-lookup"><span data-stu-id="ee297-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="ee297-132">Proměnná `refForm` má typ spuštění <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="ee297-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="ee297-133">Je kompatibilní s <xref:System.Windows.Forms.Form> je její typ se totiž <xref:System.Windows.Forms.Control> protože <xref:System.Windows.Forms.Form> dědí z <xref:System.Windows.Forms.Control>a s <xref:System.ComponentModel.IComponent> protože <xref:System.Windows.Forms.Form> dědí z <xref:System.ComponentModel.Component>, který implementuje <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="ee297-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="ee297-134">Ale `refForm` není kompatibilní s <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="ee297-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee297-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee297-135">See Also</span></span>  
 [<span data-ttu-id="ee297-136">Is – operátor</span><span class="sxs-lookup"><span data-stu-id="ee297-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)  
 [<span data-ttu-id="ee297-137">IsNot – operátor</span><span class="sxs-lookup"><span data-stu-id="ee297-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [<span data-ttu-id="ee297-138">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee297-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [<span data-ttu-id="ee297-139">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee297-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="ee297-140">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="ee297-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="ee297-141">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="ee297-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
