---
title: TypeOf – operátor
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
ms.openlocfilehash: 0cce36073b53442bce63f966f3bd94bd5d70d2a8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406323"
---
# <a name="typeof-operator-visual-basic"></a><span data-ttu-id="14474-102">TypeOf – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="14474-102">TypeOf Operator (Visual Basic)</span></span>
<span data-ttu-id="14474-103">Kontroluje, zda typ modulu runtime výsledku výrazu je kompatibilní s typem zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="14474-103">Checks whether the runtime type of an expression's result is type-compatible with the specified type.</span></span>
  
## <a name="syntax"></a><span data-ttu-id="14474-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14474-104">Syntax</span></span>  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a><span data-ttu-id="14474-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="14474-105">Parts</span></span>  
 `result`  
 <span data-ttu-id="14474-106">Vrátil.</span><span class="sxs-lookup"><span data-stu-id="14474-106">Returned.</span></span> <span data-ttu-id="14474-107">`Boolean`Hodnota.</span><span class="sxs-lookup"><span data-stu-id="14474-107">A `Boolean` value.</span></span>  
  
 `objectexpression`  
 <span data-ttu-id="14474-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="14474-108">Required.</span></span> <span data-ttu-id="14474-109">Libovolný výraz, který je vyhodnocen jako typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="14474-109">Any expression that evaluates to a reference type.</span></span>  
  
 `typename`  
 <span data-ttu-id="14474-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="14474-110">Required.</span></span> <span data-ttu-id="14474-111">Libovolný název datového typu.</span><span class="sxs-lookup"><span data-stu-id="14474-111">Any data type name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="14474-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14474-112">Remarks</span></span>  
 <span data-ttu-id="14474-113">`TypeOf`Operátor určuje, zda je běhový typ `objectexpression` kompatibilní s `typename` .</span><span class="sxs-lookup"><span data-stu-id="14474-113">The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`.</span></span> <span data-ttu-id="14474-114">Kompatibilita závisí na kategorii typu v `typename` .</span><span class="sxs-lookup"><span data-stu-id="14474-114">The compatibility depends on the type category of `typename`.</span></span> <span data-ttu-id="14474-115">Následující tabulka ukazuje, jak je určována kompatibilita.</span><span class="sxs-lookup"><span data-stu-id="14474-115">The following table shows how compatibility is determined.</span></span>  
  
|<span data-ttu-id="14474-116">Kategorie typu`typename`</span><span class="sxs-lookup"><span data-stu-id="14474-116">Type category of `typename`</span></span>|<span data-ttu-id="14474-117">Kritérium kompatibility</span><span class="sxs-lookup"><span data-stu-id="14474-117">Compatibility criterion</span></span>|  
|---------------------------------|-----------------------------|  
|<span data-ttu-id="14474-118">Třída</span><span class="sxs-lookup"><span data-stu-id="14474-118">Class</span></span>|<span data-ttu-id="14474-119">`objectexpression`je typu `typename` nebo dědí z`typename`</span><span class="sxs-lookup"><span data-stu-id="14474-119">`objectexpression` is of type `typename` or inherits from `typename`</span></span>|  
|<span data-ttu-id="14474-120">Struktura</span><span class="sxs-lookup"><span data-stu-id="14474-120">Structure</span></span>|<span data-ttu-id="14474-121">`objectexpression`je typu`typename`</span><span class="sxs-lookup"><span data-stu-id="14474-121">`objectexpression` is of type `typename`</span></span>|  
|<span data-ttu-id="14474-122">Rozhraní</span><span class="sxs-lookup"><span data-stu-id="14474-122">Interface</span></span>|<span data-ttu-id="14474-123">`objectexpression`implementuje `typename` nebo dědí z třídy, která implementuje`typename`</span><span class="sxs-lookup"><span data-stu-id="14474-123">`objectexpression` implements `typename` or inherits from a class that implements `typename`</span></span>|  
  
 <span data-ttu-id="14474-124">Pokud typ běhu `objectexpression` splňuje kritéria kompatibility, `result` je `True` .</span><span class="sxs-lookup"><span data-stu-id="14474-124">If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`.</span></span> <span data-ttu-id="14474-125">V opačném případě `result` je `False` .</span><span class="sxs-lookup"><span data-stu-id="14474-125">Otherwise, `result` is `False`.</span></span>  <span data-ttu-id="14474-126">Pokud `objectexpression` je null, pak `TypeOf` ... `Is` vrátí `False` a... `IsNot` vrátí `True` .</span><span class="sxs-lookup"><span data-stu-id="14474-126">If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.</span></span>  
  
 <span data-ttu-id="14474-127">`TypeOf`se vždy používá s `Is` klíčovým slovem k sestavení `TypeOf` výrazu... `Is` nebo s `IsNot` klíčovým slovem pro sestavení `TypeOf` výrazu... `IsNot` .</span><span class="sxs-lookup"><span data-stu-id="14474-127">`TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14474-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="14474-128">Example</span></span>  
 <span data-ttu-id="14474-129">Následující příklad používá `TypeOf` výrazy... `Is` k otestování kompatibility typů dvou proměnných odkazů na objekty s různými datovými typy.</span><span class="sxs-lookup"><span data-stu-id="14474-129">The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.</span></span>  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 <span data-ttu-id="14474-130">Proměnná `refInteger` má běhový typ `Integer` .</span><span class="sxs-lookup"><span data-stu-id="14474-130">The variable `refInteger` has a run-time type of `Integer`.</span></span> <span data-ttu-id="14474-131">Je kompatibilní s, `Integer` ale ne s `Double` .</span><span class="sxs-lookup"><span data-stu-id="14474-131">It is compatible with `Integer` but not with `Double`.</span></span> <span data-ttu-id="14474-132">Proměnná `refForm` má běhový typ <xref:System.Windows.Forms.Form> .</span><span class="sxs-lookup"><span data-stu-id="14474-132">The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>.</span></span> <span data-ttu-id="14474-133">Je kompatibilní s, <xref:System.Windows.Forms.Form> protože to je jeho typ s, <xref:System.Windows.Forms.Control> protože <xref:System.Windows.Forms.Form> dědí z, <xref:System.Windows.Forms.Control> a s, <xref:System.ComponentModel.IComponent> protože <xref:System.Windows.Forms.Form> dědí z <xref:System.ComponentModel.Component> , který implementuje <xref:System.ComponentModel.IComponent> .</span><span class="sxs-lookup"><span data-stu-id="14474-133">It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>.</span></span> <span data-ttu-id="14474-134">Není však `refForm` kompatibilní se systémem <xref:System.Windows.Forms.Label> .</span><span class="sxs-lookup"><span data-stu-id="14474-134">However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14474-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="14474-135">See also</span></span>

- [<span data-ttu-id="14474-136">Is – operátor</span><span class="sxs-lookup"><span data-stu-id="14474-136">Is Operator</span></span>](is-operator.md)
- [<span data-ttu-id="14474-137">IsNot – operátor</span><span class="sxs-lookup"><span data-stu-id="14474-137">IsNot Operator</span></span>](isnot-operator.md)
- [<span data-ttu-id="14474-138">Operátory porovnání v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="14474-138">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="14474-139">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="14474-139">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="14474-140">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="14474-140">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="14474-141">Operátory a výrazy</span><span class="sxs-lookup"><span data-stu-id="14474-141">Operators and Expressions</span></span>](../../programming-guide/language-features/operators-and-expressions/index.md)
