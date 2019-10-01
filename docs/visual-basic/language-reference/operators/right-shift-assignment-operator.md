---
title: '>>= – operátor (Visual Basic)'
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
ms.openlocfilehash: 08d4e251a96ca387a709319e752351db6825d9e8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701348"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="4775a-102">> > = – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4775a-102">>>= Operator (Visual Basic)</span></span>
<span data-ttu-id="4775a-103">Provede aritmetický pravý posun na hodnotu proměnné nebo vlastnosti a přiřadí výsledek zpátky proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4775a-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4775a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4775a-104">Syntax</span></span>  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="4775a-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="4775a-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="4775a-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4775a-106">Required.</span></span> <span data-ttu-id="4775a-107">Proměnná nebo vlastnost integrálního typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` nebo `ULong`).</span><span class="sxs-lookup"><span data-stu-id="4775a-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="4775a-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="4775a-108">Required.</span></span> <span data-ttu-id="4775a-109">Číselný výraz datového typu, který se rozšíří na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="4775a-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4775a-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4775a-110">Remarks</span></span>  
 <span data-ttu-id="4775a-111">Element na levé straně operátoru `>>=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="4775a-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="4775a-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="4775a-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="4775a-113">Operátor `>>=` nejprve provede aritmetický pravý posun na hodnotu proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4775a-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="4775a-114">Operátor potom přiřadí výsledek této operace zpátky k proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4775a-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="4775a-115">Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="4775a-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="4775a-116">V aritmetickém pravém posunu se bity po pravém horním rohu zahodí a bit umístěný nejvíce vlevo se rozšíří do bitových pozic uvolněné vlevo.</span><span class="sxs-lookup"><span data-stu-id="4775a-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="4775a-117">To znamená, že pokud `variableorproperty` má zápornou hodnotu, pozice uvolněné jsou nastaveny na jednu.</span><span class="sxs-lookup"><span data-stu-id="4775a-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="4775a-118">Pokud je `variableorproperty` kladné, nebo pokud je jeho datový typ typu bez znaménka, pozice uvolněné jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="4775a-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="4775a-119">Přetížení</span><span class="sxs-lookup"><span data-stu-id="4775a-119">Overloading</span></span>  
 <span data-ttu-id="4775a-120">[Operátor > >](../../../visual-basic/language-reference/operators/right-shift-operator.md) může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, když má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="4775a-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="4775a-121">Přetížení operátoru `>>` má vliv na chování operátoru `>>=`.</span><span class="sxs-lookup"><span data-stu-id="4775a-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="4775a-122">Pokud váš kód používá `>>=` na třídě nebo struktuře, která přetěžuje `>>`, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="4775a-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="4775a-123">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="4775a-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4775a-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="4775a-124">Example</span></span>  
 <span data-ttu-id="4775a-125">Následující příklad používá operátor `>>=` k posunu bitového vzoru proměnné `Integer` o zadanou hodnotu a přiřazení výsledku proměnné.</span><span class="sxs-lookup"><span data-stu-id="4775a-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="4775a-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4775a-126">See also</span></span>

- [<span data-ttu-id="4775a-127">Operátor >></span><span class="sxs-lookup"><span data-stu-id="4775a-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [<span data-ttu-id="4775a-128">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="4775a-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="4775a-129">Operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="4775a-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="4775a-130">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4775a-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="4775a-131">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="4775a-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="4775a-132">Příkazy</span><span class="sxs-lookup"><span data-stu-id="4775a-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
