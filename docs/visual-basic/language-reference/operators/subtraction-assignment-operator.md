---
title: -= – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: 4f403cd8a28f8d9d0ba1d24b0792a352a9c961db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406402"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="b354e-102">-= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b354e-102">-= Operator (Visual Basic)</span></span>
<span data-ttu-id="b354e-103">Odečte hodnotu výrazu z hodnoty proměnné nebo vlastnosti a přiřadí výsledek proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b354e-103">Subtracts the value of an expression from the value of a variable or property and assigns the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b354e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b354e-104">Syntax</span></span>  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="b354e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b354e-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="b354e-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="b354e-106">Required.</span></span> <span data-ttu-id="b354e-107">Jakákoli číselná proměnná nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b354e-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="b354e-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="b354e-108">Required.</span></span> <span data-ttu-id="b354e-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="b354e-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b354e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b354e-110">Remarks</span></span>  
 <span data-ttu-id="b354e-111">Element na levé straně `-=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="b354e-111">The element on the left side of the `-=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="b354e-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="b354e-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="b354e-113">`-=`Operátor nejprve ododečte hodnotu výrazu (na pravé straně operátoru) z hodnoty proměnné nebo vlastnosti (na levé straně operátoru).</span><span class="sxs-lookup"><span data-stu-id="b354e-113">The `-=` operator first subtracts the value of the expression (on the right-hand side of the operator) from the value of the variable or property (on the left-hand side of the operator).</span></span> <span data-ttu-id="b354e-114">Operátor potom přiřadí výsledek této operace proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b354e-114">The operator then assigns the result of that operation to the variable or property.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b354e-115">Přetížení</span><span class="sxs-lookup"><span data-stu-id="b354e-115">Overloading</span></span>  
 <span data-ttu-id="b354e-116">[Operátor-operátor (Visual Basic)](subtraction-operator.md) může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="b354e-116">The [- Operator (Visual Basic)](subtraction-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b354e-117">Přetížení `-` operátoru ovlivňuje chování `-=` operátoru.</span><span class="sxs-lookup"><span data-stu-id="b354e-117">Overloading the `-` operator affects the behavior of the `-=` operator.</span></span> <span data-ttu-id="b354e-118">Pokud váš kód používá `-=` pro třídu nebo strukturu, která je přetížena `-` , ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="b354e-118">If your code uses `-=` on a class or structure that overloads `-`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b354e-119">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b354e-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b354e-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="b354e-120">Example</span></span>  
 <span data-ttu-id="b354e-121">Následující příklad používá `-=` operátor k odečtení jedné `Integer` proměnné od druhé a přiřazení výsledku k druhé proměnné.</span><span class="sxs-lookup"><span data-stu-id="b354e-121">The following example uses the `-=` operator to subtract one `Integer` variable from another and assign the result to the latter variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a><span data-ttu-id="b354e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="b354e-122">See also</span></span>

- [<span data-ttu-id="b354e-123">- – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b354e-123">- Operator (Visual Basic)</span></span>](subtraction-operator.md)
- [<span data-ttu-id="b354e-124">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="b354e-124">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="b354e-125">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="b354e-125">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="b354e-126">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b354e-126">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="b354e-127">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="b354e-127">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="b354e-128">Příkazy</span><span class="sxs-lookup"><span data-stu-id="b354e-128">Statements</span></span>](../../programming-guide/language-features/statements.md)
