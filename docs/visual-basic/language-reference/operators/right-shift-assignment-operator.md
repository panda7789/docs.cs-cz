---
title: '&gt;&gt;= – Operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: d0c0ea819741f80e30e55a960b1187699898a3bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604104"
---
# <a name="gtgt-operator-visual-basic"></a><span data-ttu-id="ce909-102">&gt;&gt;= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce909-102">&gt;&gt;= Operator (Visual Basic)</span></span>
<span data-ttu-id="ce909-103">Provede aritmetický správné posun na hodnotě proměnné nebo vlastnosti a přiřadí výsledek zpět do proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ce909-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce909-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce909-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="ce909-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ce909-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="ce909-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ce909-106">Required.</span></span> <span data-ttu-id="ce909-107">Proměnná nebo vlastnost integrální typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).</span><span class="sxs-lookup"><span data-stu-id="ce909-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="ce909-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="ce909-108">Required.</span></span> <span data-ttu-id="ce909-109">Číselný výraz datový typ, který rozšiřuje na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ce909-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce909-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce909-110">Remarks</span></span>  
 <span data-ttu-id="ce909-111">Element na levé straně `>>=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole.</span><span class="sxs-lookup"><span data-stu-id="ce909-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="ce909-112">Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="ce909-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="ce909-113">`>>=` Operátor nejprve provádí aritmetické posunutí doprava na hodnotě proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ce909-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="ce909-114">Operátor poté přiřadí výsledek této operace zpět do proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ce909-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="ce909-115">Aritmetické posuny nejsou cyklické, což znamená, že služba bits přesunout mimo jeden element end výsledku nejsou znovu uvedeny na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="ce909-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="ce909-116">V aritmetické posunutí doprava jsou zahozeny bits zapuštěno nad rámec pozici nejvíce vpravo bit a levou krajní bit rozšířena do pozice bit vacated na levé straně.</span><span class="sxs-lookup"><span data-stu-id="ce909-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="ce909-117">To znamená, že pokud `variableorproperty` má zápornou hodnotu vacated pozice se nastavit na jedno.</span><span class="sxs-lookup"><span data-stu-id="ce909-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="ce909-118">Pokud `variableorproperty` kladné, nebo pokud je jeho datový typ je typ bez znaménka, vacated pozic nastaveny na nulu.</span><span class="sxs-lookup"><span data-stu-id="ce909-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="ce909-119">Přetížení</span><span class="sxs-lookup"><span data-stu-id="ce909-119">Overloading</span></span>  
 <span data-ttu-id="ce909-120">[>> Operátor](../../../visual-basic/language-reference/operators/right-shift-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="ce909-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="ce909-121">Přetížení `>>` operátor má vliv na chování `>>=` operátor.</span><span class="sxs-lookup"><span data-stu-id="ce909-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="ce909-122">Pokud váš kód používá `>>=` na třídu nebo strukturu, která přetížení `>>`, ujistěte se, pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="ce909-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="ce909-123">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="ce909-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce909-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce909-124">Example</span></span>  
 <span data-ttu-id="ce909-125">Následující příklad používá `>>=` operátor se posunou bit vzor `Integer` proměnné přímo ve stanoveném a přiřadit výsledek, který má proměnná.</span><span class="sxs-lookup"><span data-stu-id="ce909-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="ce909-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce909-126">See Also</span></span>  
 [<span data-ttu-id="ce909-127">>> – operátor</span><span class="sxs-lookup"><span data-stu-id="ce909-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)  
 [<span data-ttu-id="ce909-128">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="ce909-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<span data-ttu-id="ce909-129">Operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="ce909-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [<span data-ttu-id="ce909-130">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ce909-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="ce909-131">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="ce909-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="ce909-132">Příkazy</span><span class="sxs-lookup"><span data-stu-id="ce909-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
