---
title: ^= – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: e631cc9a484b56ee059449ca1fbd9fc69405333d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371398"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="c7137-102">^= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c7137-102">^= Operator (Visual Basic)</span></span>
<span data-ttu-id="c7137-103">Vyvolá hodnotu proměnné nebo vlastnosti na mocninu výrazu a přiřadí výsledek zpátky proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c7137-103">Raises the value of a variable or property to the power of an expression and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7137-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7137-104">Syntax</span></span>  
  
```vb  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="c7137-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c7137-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="c7137-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="c7137-106">Required.</span></span> <span data-ttu-id="c7137-107">Jakákoli číselná proměnná nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c7137-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="c7137-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="c7137-108">Required.</span></span> <span data-ttu-id="c7137-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="c7137-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c7137-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7137-110">Remarks</span></span>  
 <span data-ttu-id="c7137-111">Element na levé straně `^=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="c7137-111">The element on the left side of the `^=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="c7137-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="c7137-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="c7137-113">`^=`Operátor nejprve vyvolá hodnotu proměnné nebo vlastnosti (na levé straně operátoru) na mocninu hodnoty výrazu (na pravé straně operátoru).</span><span class="sxs-lookup"><span data-stu-id="c7137-113">The `^=` operator first raises the value of the variable or property (on the left-hand side of the operator) to the power of the value of the expression (on the right-hand side of the operator).</span></span> <span data-ttu-id="c7137-114">Operátor potom přiřadí výsledek této operace zpátky k proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c7137-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="c7137-115">Visual Basic vždy provádí umocnění v [datovém typu Double](../data-types/double-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="c7137-115">Visual Basic always performs exponentiation in the [Double Data Type](../data-types/double-data-type.md).</span></span> <span data-ttu-id="c7137-116">Operandy jiného typu jsou převedeny na `Double` a výsledek je vždy `Double` .</span><span class="sxs-lookup"><span data-stu-id="c7137-116">Operands of any different type are converted to `Double`, and the result is always `Double`.</span></span>  
  
 <span data-ttu-id="c7137-117">Hodnota `expression` může být zlomková, záporná nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="c7137-117">The value of `expression` can be fractional, negative, or both.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="c7137-118">Přetížení</span><span class="sxs-lookup"><span data-stu-id="c7137-118">Overloading</span></span>  
 <span data-ttu-id="c7137-119">[Operátor ^](exponentiation-operator.md) může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, když má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="c7137-119">The [^ Operator](exponentiation-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="c7137-120">Přetížení `^` operátoru ovlivňuje chování `^=` operátoru.</span><span class="sxs-lookup"><span data-stu-id="c7137-120">Overloading the `^` operator affects the behavior of the `^=` operator.</span></span> <span data-ttu-id="c7137-121">Pokud váš kód používá `^=` pro třídu nebo strukturu, která je přetížena `^` , ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="c7137-121">If your code uses `^=` on a class or structure that overloads `^`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="c7137-122">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="c7137-122">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7137-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7137-123">Example</span></span>  
 <span data-ttu-id="c7137-124">Následující příklad používá `^=` operátor k vyvolání hodnoty jedné `Integer` proměnné mocninou druhé proměnné a přiřazení výsledku první proměnné.</span><span class="sxs-lookup"><span data-stu-id="c7137-124">The following example uses the `^=` operator to raise the value of one `Integer` variable to the power of a second variable and assign the result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="c7137-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7137-125">See also</span></span>

- [<span data-ttu-id="c7137-126">^ – Operátor</span><span class="sxs-lookup"><span data-stu-id="c7137-126">^ Operator</span></span>](exponentiation-operator.md)
- [<span data-ttu-id="c7137-127">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="c7137-127">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="c7137-128">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="c7137-128">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="c7137-129">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7137-129">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="c7137-130">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="c7137-130">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="c7137-131">Příkazy</span><span class="sxs-lookup"><span data-stu-id="c7137-131">Statements</span></span>](../../programming-guide/language-features/statements.md)
