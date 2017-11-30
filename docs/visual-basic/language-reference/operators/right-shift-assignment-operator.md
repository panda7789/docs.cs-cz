---
title: "&gt;&gt;= – Operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7e388471b9adf424c55b1ad1042e5aed1ea8ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="83912-102">&gt;&gt;= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83912-102">&gt;&gt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="83912-103">Provede aritmetický správné posun na hodnotě proměnné nebo vlastnosti a přiřadí výsledek zpět do proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="83912-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83912-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83912-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="83912-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="83912-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="83912-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="83912-106">Required.</span></span> <span data-ttu-id="83912-107">Proměnná nebo vlastnost integrální typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).</span><span class="sxs-lookup"><span data-stu-id="83912-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="83912-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="83912-108">Required.</span></span> <span data-ttu-id="83912-109">Číselný výraz datový typ, který rozšiřuje na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="83912-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83912-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83912-110">Remarks</span></span>  
 <span data-ttu-id="83912-111">Element na levé straně `>>=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole.</span><span class="sxs-lookup"><span data-stu-id="83912-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="83912-112">Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="83912-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="83912-113">`>>=` Operátor nejprve provádí aritmetické posunutí doprava na hodnotě proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="83912-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="83912-114">Operátor poté přiřadí výsledek této operace zpět do proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="83912-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="83912-115">Aritmetické posuny nejsou cyklické, což znamená, že služba bits přesunout mimo jeden element end výsledku nejsou znovu uvedeny na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="83912-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="83912-116">V aritmetické posunutí doprava jsou zahozeny bits zapuštěno nad rámec pozici nejvíce vpravo bit a levou krajní bit rozšířena do pozice bit vacated na levé straně.</span><span class="sxs-lookup"><span data-stu-id="83912-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="83912-117">To znamená, že pokud `variableorproperty` má zápornou hodnotu vacated pozice se nastavit na jedno.</span><span class="sxs-lookup"><span data-stu-id="83912-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="83912-118">Pokud `variableorproperty` kladné, nebo pokud je jeho datový typ je typ bez znaménka, vacated pozic nastaveny na nulu.</span><span class="sxs-lookup"><span data-stu-id="83912-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="83912-119">Přetížení</span><span class="sxs-lookup"><span data-stu-id="83912-119">Overloading</span></span>  
 <span data-ttu-id="83912-120">[>> Operátor](../../../visual-basic/language-reference/operators/right-shift-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="83912-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="83912-121">Přetížení `>>` operátor má vliv na chování `>>=` operátor.</span><span class="sxs-lookup"><span data-stu-id="83912-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="83912-122">Pokud váš kód používá `>>=` na třídu nebo strukturu, která přetížení `>>`, ujistěte se, pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="83912-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="83912-123">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="83912-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="83912-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="83912-124">Example</span></span>  
 <span data-ttu-id="83912-125">Následující příklad používá `>>=` operátor se posunou bit vzor `Integer` proměnné přímo ve stanoveném a přiřadit výsledek, který má proměnná.</span><span class="sxs-lookup"><span data-stu-id="83912-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="83912-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="83912-126">See Also</span></span>  
 [<span data-ttu-id="83912-127">>> – Operátor</span><span class="sxs-lookup"><span data-stu-id="83912-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)  
 [<span data-ttu-id="83912-128">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="83912-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="83912-129">Operátory bitového posunutí</span><span class="sxs-lookup"><span data-stu-id="83912-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="83912-130">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="83912-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="83912-131">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="83912-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="83912-132">Příkazy</span><span class="sxs-lookup"><span data-stu-id="83912-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
