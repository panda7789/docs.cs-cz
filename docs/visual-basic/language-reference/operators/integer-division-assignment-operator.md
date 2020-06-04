---
title: '\= – operátor'
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: a546d8b0c9b3852386970f80d3da96794da2351c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370944"
---
# <a name="-operator"></a><span data-ttu-id="87556-102">\\= – Operátor</span><span class="sxs-lookup"><span data-stu-id="87556-102">\\= Operator</span></span>
<span data-ttu-id="87556-103">Vydělí hodnotu proměnné nebo vlastnosti hodnotou výrazu a přiřadí celočíselný výsledek proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="87556-103">Divides the value of a variable or property by the value of an expression and assigns the integer result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87556-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87556-104">Syntax</span></span>  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a><span data-ttu-id="87556-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="87556-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="87556-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="87556-106">Required.</span></span> <span data-ttu-id="87556-107">Jakákoli číselná proměnná nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="87556-107">Any numeric variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="87556-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="87556-108">Required.</span></span> <span data-ttu-id="87556-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="87556-109">Any numeric expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87556-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87556-110">Remarks</span></span>  
 <span data-ttu-id="87556-111">Element na levé straně `\=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="87556-111">The element on the left side of the `\=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="87556-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="87556-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="87556-113">`\=`Operátor rozdělí hodnotu proměnné nebo vlastnosti na levé straně hodnotou vpravo a přiřadí celočíselný výsledek proměnné nebo vlastnosti na levé straně.</span><span class="sxs-lookup"><span data-stu-id="87556-113">The `\=` operator divides the value of a variable or property on its left by the value on its right, and assigns the integer result to the variable or property on its left</span></span>  
  
 <span data-ttu-id="87556-114">Další informace o celočíselném dělení naleznete v tématu [operátor \ (Visual Basic)](integer-division-operator.md).</span><span class="sxs-lookup"><span data-stu-id="87556-114">For further information on integer division, see [\ Operator (Visual Basic)](integer-division-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="87556-115">Přetížení</span><span class="sxs-lookup"><span data-stu-id="87556-115">Overloading</span></span>  
 <span data-ttu-id="87556-116">`\`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="87556-116">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="87556-117">Přetížení `\` operátoru ovlivňuje chování `\=` operátoru.</span><span class="sxs-lookup"><span data-stu-id="87556-117">Overloading the `\` operator affects the behavior of the `\=` operator.</span></span> <span data-ttu-id="87556-118">Pokud váš kód používá `\=` pro třídu nebo strukturu, která je přetížena `\` , ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="87556-118">If your code uses `\=` on a class or structure that overloads `\`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="87556-119">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="87556-119">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="87556-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="87556-120">Example</span></span>  
 <span data-ttu-id="87556-121">Následující příklad používá `\=` operátor k rozdělení jedné `Integer` proměnné za sekundu a přiřazení celého výsledku k první proměnné.</span><span class="sxs-lookup"><span data-stu-id="87556-121">The following example uses the `\=` operator to divide one `Integer` variable by a second and assign the integer result to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="87556-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="87556-122">See also</span></span>

- [<span data-ttu-id="87556-123">\ – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87556-123">\ Operator (Visual Basic)</span></span>](integer-division-operator.md)
- [<span data-ttu-id="87556-124">/= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87556-124">/= Operator (Visual Basic)</span></span>](floating-point-division-assignment-operator.md)
- [<span data-ttu-id="87556-125">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="87556-125">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="87556-126">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="87556-126">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="87556-127">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="87556-127">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="87556-128">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="87556-128">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="87556-129">Příkazy</span><span class="sxs-lookup"><span data-stu-id="87556-129">Statements</span></span>](../../programming-guide/language-features/statements.md)
