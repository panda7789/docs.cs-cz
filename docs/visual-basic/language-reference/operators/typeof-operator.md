---
title: TypeOf – operátor (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 7162fcc24595bbb16d268d5d9e1ea4d82f6e67fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829860"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="0f905-102">TypeOf – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0f905-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="0f905-103">Porovná proměnné odkazu na objekt k datovému typu.</span><span class="sxs-lookup"><span data-stu-id="0f905-103">Compares an object reference variable to a data type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f905-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0f905-104">Syntax</span></span>  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="0f905-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="0f905-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="0f905-106">Vrátí.</span><span class="sxs-lookup"><span data-stu-id="0f905-106">Returned.</span></span> <span data-ttu-id="0f905-107">A `Boolean` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0f905-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="0f905-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0f905-108">Required.</span></span> <span data-ttu-id="0f905-109">Libovolný výraz, který se vyhodnotí na typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="0f905-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="0f905-110">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0f905-110">Required.</span></span> <span data-ttu-id="0f905-111">Všechna data, zadejte název.</span><span class="sxs-lookup"><span data-stu-id="0f905-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0f905-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0f905-112">Remarks</span></span>  
 <span data-ttu-id="0f905-113">`TypeOf` Operátor určuje, zda za běhu typ `objectexpression` je kompatibilní s `typename`.</span><span class="sxs-lookup"><span data-stu-id="0f905-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="0f905-114">Kompatibilita závisí na typu kategorie `typename`.</span><span class="sxs-lookup"><span data-stu-id="0f905-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="0f905-115">Následující tabulka ukazuje, jak se určují kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="0f905-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="0f905-116">Typ kategorie `typename`</span><span class="sxs-lookup"><span data-stu-id="0f905-116">Type category of `typename`</span></span>|<span data-ttu-id="0f905-117">Kritérium kompatibility</span><span class="sxs-lookup"><span data-stu-id="0f905-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="0f905-118">Třída</span><span class="sxs-lookup"><span data-stu-id="0f905-118">Class</span></span>|<span data-ttu-id="0f905-119">`objectexpression` je typu `typename` nebo dědí z `typename`</span><span class="sxs-lookup"><span data-stu-id="0f905-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="0f905-120">Struktura</span><span class="sxs-lookup"><span data-stu-id="0f905-120">Structure</span></span>|<span data-ttu-id="0f905-121">`objectexpression` je typu `typename`</span><span class="sxs-lookup"><span data-stu-id="0f905-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="0f905-122">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="0f905-122">Interface</span></span>|<span data-ttu-id="0f905-123">`objectexpression` implementuje `typename` nebo dědí z třídy, která implementuje `typename`</span><span class="sxs-lookup"><span data-stu-id="0f905-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="0f905-124">Pokud typ za běhu `objectexpression` splňuje kritéria kompatibility `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="0f905-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="0f905-125">V opačném případě `result` je `False`.</span><span class="sxs-lookup"><span data-stu-id="0f905-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="0f905-126">Pokud `objectexpression` má hodnotu null, pak `TypeOf`... `Is` vrátí `False`, a... `IsNot` vrátí `True`.</span><span class="sxs-lookup"><span data-stu-id="0f905-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="0f905-127">`TypeOf` je vždy použito s `Is` – klíčové slovo k vytvoření `TypeOf`... `Is` výrazu, nebo se `IsNot` – klíčové slovo k vytvoření `TypeOf`... `IsNot` výrazu.</span><span class="sxs-lookup"><span data-stu-id="0f905-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f905-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="0f905-128">Example</span></span>  
 <span data-ttu-id="0f905-129">Následující příklad používá `TypeOf`... `Is` výrazy pro testování kompatibility typ dvou objektů referenční proměnné s různými datovými typy.</span><span class="sxs-lookup"><span data-stu-id="0f905-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="0f905-130">Proměnná `refInteger` je za běhu typu `Integer`.</span><span class="sxs-lookup"><span data-stu-id="0f905-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="0f905-131">Je kompatibilní s `Integer` , ale ne s `Double`.</span><span class="sxs-lookup"><span data-stu-id="0f905-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="0f905-132">Proměnná `refForm` je za běhu typu <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="0f905-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="0f905-133">Je kompatibilní s <xref:System.Windows.Forms.Form> protože jeho typ, který je s <xref:System.Windows.Forms.Control> protože <xref:System.Windows.Forms.Form> dědí z <xref:System.Windows.Forms.Control>a s <xref:System.ComponentModel.IComponent> protože <xref:System.Windows.Forms.Form> dědí z <xref:System.ComponentModel.Component>, který implementuje <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="0f905-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="0f905-134">Ale `refForm` není kompatibilní s <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="0f905-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f905-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0f905-135">See also</span></span>

- [<span data-ttu-id="0f905-136">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="0f905-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="0f905-137">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="0f905-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="0f905-138">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f905-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="0f905-139">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f905-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="0f905-140">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="0f905-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="0f905-141">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="0f905-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
