---
title: "&lt;&lt;= – Operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c5c36e4f91155c09d01b448777483941d018d9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-visual-basic"></a><span data-ttu-id="0d9fa-102">&lt;&lt;= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d9fa-102">&lt;&lt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="0d9fa-103">Provede aritmetický levém posun na hodnotě proměnné nebo vlastnosti a přiřadí výsledek zpět do proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0d9fa-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d9fa-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0d9fa-104">Syntax</span></span>  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="0d9fa-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="0d9fa-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="0d9fa-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0d9fa-106">Required.</span></span> <span data-ttu-id="0d9fa-107">Proměnná nebo vlastnost integrální typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).</span><span class="sxs-lookup"><span data-stu-id="0d9fa-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="0d9fa-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0d9fa-108">Required.</span></span> <span data-ttu-id="0d9fa-109">Číselný výraz datový typ, který rozšiřuje na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="0d9fa-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d9fa-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0d9fa-110">Remarks</span></span>  
 <span data-ttu-id="0d9fa-111">Element na levé straně `<<=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole.</span><span class="sxs-lookup"><span data-stu-id="0d9fa-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="0d9fa-112">Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="0d9fa-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="0d9fa-113">`<<=` Operátor nejprve provede aritmetický levém posun na hodnotě proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0d9fa-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="0d9fa-114">Operátor poté přiřadí výsledek této operace zpět do této proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0d9fa-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="0d9fa-115">Aritmetické posuny nejsou cyklické, což znamená, že služba bits přesunout mimo jeden element end výsledku nejsou znovu uvedeny na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="0d9fa-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="0d9fa-116">V aritmetické posunutí doleva jsou zahozeny bits zapuštěno mimo rozsah datového typu výsledek a pozice bit vacated na pravé straně nastaveny na nulu.</span><span class="sxs-lookup"><span data-stu-id="0d9fa-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="0d9fa-117">Přetížení</span><span class="sxs-lookup"><span data-stu-id="0d9fa-117">Overloading</span></span>  
 <span data-ttu-id="0d9fa-118">[<< Operátor](../../../visual-basic/language-reference/operators/left-shift-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="0d9fa-118">The [<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0d9fa-119">Přetížení `<<` operátor má vliv na chování `<<=` operátor.</span><span class="sxs-lookup"><span data-stu-id="0d9fa-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="0d9fa-120">Pokud váš kód používá `<<=` na třídu nebo strukturu, která přetížení `<<`, ujistěte se, pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="0d9fa-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="0d9fa-121">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0d9fa-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d9fa-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d9fa-122">Example</span></span>  
 <span data-ttu-id="0d9fa-123">Následující příklad používá `<<=` operátor se posunou bit vzor `Integer` proměnná levé ve stanoveném a přiřadit výsledek na proměnnou.</span><span class="sxs-lookup"><span data-stu-id="0d9fa-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0d9fa-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d9fa-124">See Also</span></span>  
 [<span data-ttu-id="0d9fa-125"><< – Operátor</span><span class="sxs-lookup"><span data-stu-id="0d9fa-125"><< Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-operator.md)  
 [<span data-ttu-id="0d9fa-126">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="0d9fa-126">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="0d9fa-127">Operátory bitového posunutí</span><span class="sxs-lookup"><span data-stu-id="0d9fa-127">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="0d9fa-128">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0d9fa-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="0d9fa-129">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="0d9fa-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="0d9fa-130">Příkazy</span><span class="sxs-lookup"><span data-stu-id="0d9fa-130">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
