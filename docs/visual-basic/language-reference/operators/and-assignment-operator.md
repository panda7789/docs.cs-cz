---
title: '&amp;= Operator (Visual Basic)'
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
ms.openlocfilehash: a79e779d8fcf549daeabc494e0a55deee30b5d22
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835463"
---
# <a name="amp-operator-visual-basic"></a><span data-ttu-id="30dd0-102">&amp;= Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30dd0-102">&amp;= Operator (Visual Basic)</span></span>
<span data-ttu-id="30dd0-103">Zřetězí `String` výraz, který se `String` proměnnou nebo vlastnost a výsledek přiřadí proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="30dd0-103">Concatenates a `String` expression to a `String` variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30dd0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30dd0-104">Syntax</span></span>  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="30dd0-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="30dd0-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="30dd0-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="30dd0-106">Required.</span></span> <span data-ttu-id="30dd0-107">Žádné `String` proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="30dd0-107">Any `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="30dd0-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="30dd0-108">Required.</span></span> <span data-ttu-id="30dd0-109">Žádné `String` výrazu.</span><span class="sxs-lookup"><span data-stu-id="30dd0-109">Any `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30dd0-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30dd0-110">Remarks</span></span>  
 <span data-ttu-id="30dd0-111">Element na levé straně `&=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="30dd0-111">The element on the left side of the `&=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="30dd0-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="30dd0-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span> <span data-ttu-id="30dd0-113">`&=` Operátor zřetězí `String` výraz na jeho právo `String` proměnnou nebo vlastnost na levé straně a výsledek přiřadí proměnné nebo vlastnosti na levé straně.</span><span class="sxs-lookup"><span data-stu-id="30dd0-113">The `&=` operator concatenates the `String` expression on its right to the `String` variable or property on its left, and assigns the result to the variable or property on its left.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="30dd0-114">Přetížení</span><span class="sxs-lookup"><span data-stu-id="30dd0-114">Overloading</span></span>  
 <span data-ttu-id="30dd0-115">[& – Operátor](../../../visual-basic/language-reference/operators/concatenation-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="30dd0-115">The [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="30dd0-116">Přetížení `&` operátor má vliv na chování `&=` operátor.</span><span class="sxs-lookup"><span data-stu-id="30dd0-116">Overloading the `&` operator affects the behavior of the `&=` operator.</span></span> <span data-ttu-id="30dd0-117">Pokud váš kód používá `&=` v třídě nebo struktuře, která přetížení `&`, je nutné pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="30dd0-117">If your code uses `&=` on a class or structure that overloads `&`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="30dd0-118">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="30dd0-118">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="30dd0-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="30dd0-119">Example</span></span>  
 <span data-ttu-id="30dd0-120">V následujícím příkladu `&=` operátoru pro zřetězení dvou `String` proměnné a přiřadit výsledek, který má první proměnné.</span><span class="sxs-lookup"><span data-stu-id="30dd0-120">The following example uses the `&=` operator to concatenate two `String` variables and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="30dd0-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30dd0-121">See also</span></span>

- [<span data-ttu-id="30dd0-122">& – operátor</span><span class="sxs-lookup"><span data-stu-id="30dd0-122">& Operator</span></span>](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [<span data-ttu-id="30dd0-123">+= – operátor</span><span class="sxs-lookup"><span data-stu-id="30dd0-123">+= Operator</span></span>](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [<span data-ttu-id="30dd0-124">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="30dd0-124">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="30dd0-125">Operátory zřetězení</span><span class="sxs-lookup"><span data-stu-id="30dd0-125">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="30dd0-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30dd0-126">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="30dd0-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="30dd0-127">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="30dd0-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="30dd0-128">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
