---
title: /= – operátor [Visual Basic]
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: d9d3fa021654d3be1b9d304beb83caa737660264
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58813987"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="81a20-102">/= – operátor [Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="81a20-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="81a20-103">Vydělí hodnotu proměnné nebo vlastnosti hodnotou výrazu a přiřadí k proměnné nebo vlastnosti výsledku s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="81a20-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81a20-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81a20-104">Syntax</span></span>  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="81a20-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="81a20-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="81a20-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="81a20-106">Required.</span></span> <span data-ttu-id="81a20-107">Všechny číselné proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="81a20-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="81a20-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="81a20-108">Required.</span></span> <span data-ttu-id="81a20-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="81a20-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81a20-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81a20-110">Remarks</span></span>  
 <span data-ttu-id="81a20-111">Element na levé straně `/=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="81a20-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="81a20-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="81a20-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="81a20-113">`/=` Operátor nejprve vydělí hodnotu proměnné nebo vlastnosti (na levé straně operátoru) hodnotu výrazu (na pravé straně operátoru).</span><span class="sxs-lookup"><span data-stu-id="81a20-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="81a20-114">Operátor, který se pak přiřadí s plovoucí desetinnou čárkou výsledek této operace na proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="81a20-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="81a20-115">Tento příkaz přiřadí `Double` hodnotu proměnné nebo vlastnosti na levé straně.</span><span class="sxs-lookup"><span data-stu-id="81a20-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="81a20-116">Pokud `Option Strict` je `On`, `variableorproperty` musí být `Double`.</span><span class="sxs-lookup"><span data-stu-id="81a20-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="81a20-117">Pokud `Option Strict` je `Off`, provádí implicitní převod jazyka Visual Basic a přiřadí výslednou hodnotu pro `variableorproperty`, s možnou chybu v době běhu.</span><span class="sxs-lookup"><span data-stu-id="81a20-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="81a20-118">Další informace najdete v tématu [Widening a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="81a20-118">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="81a20-119">Přetížení</span><span class="sxs-lookup"><span data-stu-id="81a20-119">Overloading</span></span>  
 <span data-ttu-id="81a20-120">[/ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="81a20-120">The [/ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="81a20-121">Přetížení `/` operátor má vliv na chování `/=` operátor.</span><span class="sxs-lookup"><span data-stu-id="81a20-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="81a20-122">Pokud váš kód používá `/=` v třídě nebo struktuře, která přetížení `/`, je nutné pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="81a20-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="81a20-123">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="81a20-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81a20-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="81a20-124">Example</span></span>  
 <span data-ttu-id="81a20-125">V následujícím příkladu `/=` operátor rozdělit jeden `Integer` proměnnou druhé a přiřaďte podíl první proměnné.</span><span class="sxs-lookup"><span data-stu-id="81a20-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="81a20-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81a20-126">See also</span></span>

- [<span data-ttu-id="81a20-127">/ – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81a20-127">/ Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [<span data-ttu-id="81a20-128">\\= Operator</span><span class="sxs-lookup"><span data-stu-id="81a20-128">\\= Operator</span></span>](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [<span data-ttu-id="81a20-129">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="81a20-129">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="81a20-130">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="81a20-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="81a20-131">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="81a20-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="81a20-132">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="81a20-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="81a20-133">Příkazy</span><span class="sxs-lookup"><span data-stu-id="81a20-133">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
