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
ms.openlocfilehash: c6028f524a16b836310f0c8d564205244515cdc9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701286"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="30c5a-102">TypeOf – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30c5a-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="30c5a-103">Kontroluje, zda typ modulu runtime výsledku výrazu je kompatibilní s typem zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="30c5a-103">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="30c5a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30c5a-104">Syntax</span></span>  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="30c5a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="30c5a-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="30c5a-106">Vrátil.</span><span class="sxs-lookup"><span data-stu-id="30c5a-106">Returned.</span></span> <span data-ttu-id="30c5a-107">Hodnota `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="30c5a-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="30c5a-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="30c5a-108">Required.</span></span> <span data-ttu-id="30c5a-109">Libovolný výraz, který je vyhodnocen jako typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="30c5a-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="30c5a-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="30c5a-110">Required.</span></span> <span data-ttu-id="30c5a-111">Libovolný název datového typu.</span><span class="sxs-lookup"><span data-stu-id="30c5a-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30c5a-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30c5a-112">Remarks</span></span>  
 <span data-ttu-id="30c5a-113">Operátor `TypeOf` určuje, zda je běhový typ `objectexpression` kompatibilní s `typename`.</span><span class="sxs-lookup"><span data-stu-id="30c5a-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="30c5a-114">Kompatibilita závisí na kategorii typu `typename`.</span><span class="sxs-lookup"><span data-stu-id="30c5a-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="30c5a-115">Následující tabulka ukazuje, jak je určována kompatibilita.</span><span class="sxs-lookup"><span data-stu-id="30c5a-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="30c5a-116">Typ kategorie `typename`</span><span class="sxs-lookup"><span data-stu-id="30c5a-116">Type category of `typename`</span></span>|<span data-ttu-id="30c5a-117">Kritérium kompatibility</span><span class="sxs-lookup"><span data-stu-id="30c5a-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="30c5a-118">Třída</span><span class="sxs-lookup"><span data-stu-id="30c5a-118">Class</span></span>|<span data-ttu-id="30c5a-119">`objectexpression` je typu `typename` nebo dědí z `typename`.</span><span class="sxs-lookup"><span data-stu-id="30c5a-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="30c5a-120">Struktura</span><span class="sxs-lookup"><span data-stu-id="30c5a-120">Structure</span></span>|<span data-ttu-id="30c5a-121">`objectexpression` je typu `typename`.</span><span class="sxs-lookup"><span data-stu-id="30c5a-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="30c5a-122">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="30c5a-122">Interface</span></span>|<span data-ttu-id="30c5a-123">`objectexpression` implementuje `typename` nebo dědí ze třídy, která implementuje `typename`.</span><span class="sxs-lookup"><span data-stu-id="30c5a-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="30c5a-124">Pokud typ běhu `objectexpression` splňuje kritérium kompatibility, `result` je `True`.</span><span class="sxs-lookup"><span data-stu-id="30c5a-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="30c5a-125">V opačném případě `result` `False`.</span><span class="sxs-lookup"><span data-stu-id="30c5a-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="30c5a-126">Pokud je hodnota `objectexpression` null, pak `TypeOf`... `Is` vrátí `False` a... `IsNot` vrátí `True`.</span><span class="sxs-lookup"><span data-stu-id="30c5a-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="30c5a-127">`TypeOf` se vždy používá s klíčovým slovem `Is` k vytvoření výrazu `TypeOf`... `Is` nebo pomocí klíčového slova `IsNot` pro vytvoření výrazu `TypeOf`... `IsNot`.</span><span class="sxs-lookup"><span data-stu-id="30c5a-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30c5a-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="30c5a-128">Example</span></span>  
 <span data-ttu-id="30c5a-129">V následujícím příkladu jsou použity výrazy `TypeOf`... `Is` k otestování kompatibility typů dvou proměnných odkazu na objekt s různými datovými typy.</span><span class="sxs-lookup"><span data-stu-id="30c5a-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="30c5a-130">Proměnná `refInteger` má běhový typ `Integer`.</span><span class="sxs-lookup"><span data-stu-id="30c5a-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="30c5a-131">Je kompatibilní s `Integer`, ale ne s `Double`.</span><span class="sxs-lookup"><span data-stu-id="30c5a-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="30c5a-132">Proměnná `refForm` má běhový typ <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="30c5a-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="30c5a-133">Je kompatibilní s <xref:System.Windows.Forms.Form>, protože to je jeho typ s <xref:System.Windows.Forms.Control>, protože <xref:System.Windows.Forms.Form> dědí od <xref:System.Windows.Forms.Control> a <xref:System.ComponentModel.IComponent>, protože <xref:System.Windows.Forms.Form> dědí z <xref:System.ComponentModel.Component>, které implementuje <xref:System.ComponentModel.IComponent>.</span><span class="sxs-lookup"><span data-stu-id="30c5a-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="30c5a-134">@No__t-0 však není kompatibilní s <xref:System.Windows.Forms.Label>.</span><span class="sxs-lookup"><span data-stu-id="30c5a-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30c5a-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30c5a-135">See also</span></span>

- [<span data-ttu-id="30c5a-136">Operátor Is</span><span class="sxs-lookup"><span data-stu-id="30c5a-136">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="30c5a-137">Operátor IsNot</span><span class="sxs-lookup"><span data-stu-id="30c5a-137">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="30c5a-138">Operátory porovnávání v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30c5a-138">Comparison Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="30c5a-139">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30c5a-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="30c5a-140">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="30c5a-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="30c5a-141">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="30c5a-141">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
