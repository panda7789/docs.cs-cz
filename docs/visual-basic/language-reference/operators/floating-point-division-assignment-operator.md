---
title: /= – operátor
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
ms.openlocfilehash: 48ae78630aa66ad804d539f88524c456cf805889
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371242"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="af977-102">/= – operátor [Visual Basic]</span><span class="sxs-lookup"><span data-stu-id="af977-102">/= Operator (Visual Basic)</span></span>
<span data-ttu-id="af977-103">Vydělí hodnotu proměnné nebo vlastnosti hodnotou výrazu a přiřadí výsledek s plovoucí desetinnou čárkou pro proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="af977-103">Divides the value of a variable or property by the value of an expression and assigns the floating-point result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af977-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af977-104">Syntax</span></span>  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="af977-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="af977-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="af977-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="af977-106">Required.</span></span> <span data-ttu-id="af977-107">Jakákoli číselná proměnná nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="af977-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="af977-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="af977-108">Required.</span></span> <span data-ttu-id="af977-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="af977-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af977-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af977-110">Remarks</span></span>  
 <span data-ttu-id="af977-111">Element na levé straně `/=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="af977-111">The element on the left side of the `/=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="af977-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="af977-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="af977-113">`/=`Operátor nejprve rozdělí hodnotu proměnné nebo vlastnosti (na levé straně operátoru) podle hodnoty výrazu (na pravé straně operátoru) (na pravé straně operátoru).</span><span class="sxs-lookup"><span data-stu-id="af977-113">The `/=` operator first divides the value of the variable or property (on the left-hand side of the operator) by the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="af977-114">Operátor potom přiřadí výsledek s plovoucí desetinnou čárkou této operace proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="af977-114">The operator then assigns the floating-point result of that operation to the variable or property.</span></span>  
  
 <span data-ttu-id="af977-115">Tento příkaz přiřadí `Double` hodnotu proměnné nebo vlastnosti vlevo.</span><span class="sxs-lookup"><span data-stu-id="af977-115">This statement assigns a `Double` value to the variable or property on the left.</span></span> <span data-ttu-id="af977-116">Pokud `Option Strict` je `On` , `variableorproperty` musí být `Double` .</span><span class="sxs-lookup"><span data-stu-id="af977-116">If `Option Strict` is `On`, `variableorproperty` must be a `Double`.</span></span> <span data-ttu-id="af977-117">Pokud `Option Strict` je `Off` , Visual Basic provede implicitní převod a přiřadí výslednou hodnotu k `variableorproperty` , s možnou chybou v době běhu.</span><span class="sxs-lookup"><span data-stu-id="af977-117">If `Option Strict` is `Off`, Visual Basic performs an implicit conversion and assigns the resulting value to `variableorproperty`, with a possible error at run time.</span></span> <span data-ttu-id="af977-118">Další informace naleznete v tématu [rozšiřující a zužující převody](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a [příkaz Option Strict](../statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="af977-118">For more information, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) and [Option Strict Statement](../statements/option-strict-statement.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="af977-119">Přetížení</span><span class="sxs-lookup"><span data-stu-id="af977-119">Overloading</span></span>  
 <span data-ttu-id="af977-120">[Operátor/(Visual Basic)](floating-point-division-operator.md) lze *přetížit, což*znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="af977-120">The [/ Operator (Visual Basic)](floating-point-division-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="af977-121">Přetížení `/` operátoru ovlivňuje chování `/=` operátoru.</span><span class="sxs-lookup"><span data-stu-id="af977-121">Overloading the `/` operator affects the behavior of the `/=` operator.</span></span> <span data-ttu-id="af977-122">Pokud váš kód používá `/=` pro třídu nebo strukturu, která je přetížena `/` , ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="af977-122">If your code uses `/=` on a class or structure that overloads `/`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="af977-123">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="af977-123">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="af977-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="af977-124">Example</span></span>  
 <span data-ttu-id="af977-125">Následující příklad používá `/=` operátor k rozdělení jedné `Integer` proměnné za sekundu a přiřazení podílu první proměnné.</span><span class="sxs-lookup"><span data-stu-id="af977-125">The following example uses the `/=` operator to divide one `Integer` variable by a second and assign the quotient to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="af977-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="af977-126">See also</span></span>

- [<span data-ttu-id="af977-127">/– Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="af977-127">/ Operator (Visual Basic)</span></span>](floating-point-division-operator.md)
- [<span data-ttu-id="af977-128">\\= – Operátor</span><span class="sxs-lookup"><span data-stu-id="af977-128">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="af977-129">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="af977-129">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="af977-130">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="af977-130">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="af977-131">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="af977-131">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="af977-132">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="af977-132">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="af977-133">Příkazy</span><span class="sxs-lookup"><span data-stu-id="af977-133">Statements</span></span>](../../programming-guide/language-features/statements.md)
