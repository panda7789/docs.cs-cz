---
title: '&amp;= – operátor'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: 8668bfcbf32bb34b422efe8116bbd12a2d80b1d4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350269"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="33a8a-102">&amp;= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33a8a-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="33a8a-103">Zřetězí výraz `String` na `String` proměnnou nebo vlastnost a přiřadí výsledek proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="33a8a-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33a8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33a8a-104">Syntax</span></span>  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="33a8a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="33a8a-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="33a8a-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="33a8a-106">Required.</span></span> <span data-ttu-id="33a8a-107">Jakákoli `String` proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="33a8a-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="33a8a-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="33a8a-108">Required.</span></span> <span data-ttu-id="33a8a-109">Libovolný výraz `String`.</span><span class="sxs-lookup"><span data-stu-id="33a8a-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33a8a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33a8a-110">Remarks</span></span>  
 <span data-ttu-id="33a8a-111">Element na levé straně operátoru `&=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="33a8a-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="33a8a-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="33a8a-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="33a8a-113">Operátor `&=` zřetězí výraz `String` na základě jeho práva na `String` proměnnou nebo vlastnost nalevo a přiřadí výsledek proměnné nebo vlastnosti na levé straně.</span><span class="sxs-lookup"><span data-stu-id="33a8a-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="33a8a-114">Přetížení</span><span class="sxs-lookup"><span data-stu-id="33a8a-114">Overloading</span></span>  
 <span data-ttu-id="33a8a-115">[Operátor &](../../../visual-basic/language-reference/operators/concatenation-operator.md) lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="33a8a-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="33a8a-116">Přetížení operátoru `&` má vliv na chování operátoru `&=`.</span><span class="sxs-lookup"><span data-stu-id="33a8a-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="33a8a-117">Pokud váš kód používá `&=` ve třídě nebo struktuře, která přetěžuje `&`, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="33a8a-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="33a8a-118">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="33a8a-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="33a8a-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="33a8a-119">Example</span></span>  
 <span data-ttu-id="33a8a-120">Následující příklad používá operátor `&=` k zřetězení dvou proměnných `String` a přiřazení výsledku první proměnné.</span><span class="sxs-lookup"><span data-stu-id="33a8a-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="33a8a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33a8a-121">See also</span></span>

- [<span data-ttu-id="33a8a-122">& – operátor</span><span class="sxs-lookup"><span data-stu-id="33a8a-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="33a8a-123">+= – operátor</span><span class="sxs-lookup"><span data-stu-id="33a8a-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="33a8a-124">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="33a8a-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="33a8a-125">Operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="33a8a-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="33a8a-126">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="33a8a-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="33a8a-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="33a8a-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="33a8a-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="33a8a-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
