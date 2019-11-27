---
title: '>>= – operátor'
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
ms.openlocfilehash: cad021c7730782d6233c60841483df7173308dc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351997"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="8395c-102">> > = – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8395c-102">>>= Operator (Visual Basic)</span></span>
<span data-ttu-id="8395c-103">Provede aritmetický pravý posun na hodnotu proměnné nebo vlastnosti a přiřadí výsledek zpátky proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8395c-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8395c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8395c-104">Syntax</span></span>  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="8395c-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="8395c-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="8395c-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="8395c-106">Required.</span></span> <span data-ttu-id="8395c-107">Proměnná nebo vlastnost integrálního typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`nebo `ULong`).</span><span class="sxs-lookup"><span data-stu-id="8395c-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="8395c-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="8395c-108">Required.</span></span> <span data-ttu-id="8395c-109">Číselný výraz datového typu, který se rozšíří na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="8395c-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8395c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8395c-110">Remarks</span></span>  
 <span data-ttu-id="8395c-111">Element na levé straně operátoru `>>=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="8395c-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="8395c-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="8395c-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="8395c-113">Operátor `>>=` nejprve provede aritmetický pravý posun na hodnotu proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8395c-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="8395c-114">Operátor potom přiřadí výsledek této operace zpátky k proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8395c-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="8395c-115">Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="8395c-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="8395c-116">V aritmetickém pravém posunu se bity po pravém horním rohu zahodí a bit umístěný nejvíce vlevo se rozšíří do bitových pozic uvolněné vlevo.</span><span class="sxs-lookup"><span data-stu-id="8395c-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="8395c-117">To znamená, že pokud má `variableorproperty` zápornou hodnotu, pozice uvolněné jsou nastaveny na jednu.</span><span class="sxs-lookup"><span data-stu-id="8395c-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="8395c-118">Pokud je `variableorproperty` pozitivní, nebo pokud je jeho datový typ typu bez znaménka, pozice uvolněné jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="8395c-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="8395c-119">Přetížení</span><span class="sxs-lookup"><span data-stu-id="8395c-119">Overloading</span></span>  
 <span data-ttu-id="8395c-120">[Operátor > >](../../../visual-basic/language-reference/operators/right-shift-operator.md) může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, když má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="8395c-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="8395c-121">Přetížení operátoru `>>` má vliv na chování operátoru `>>=`.</span><span class="sxs-lookup"><span data-stu-id="8395c-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="8395c-122">Pokud váš kód používá `>>=` ve třídě nebo struktuře, která přetěžuje `>>`, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="8395c-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="8395c-123">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="8395c-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8395c-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="8395c-124">Example</span></span>  
 <span data-ttu-id="8395c-125">Následující příklad používá operátor `>>=` k posunutí bitového vzoru `Integer` proměnné přímo o zadanou hodnotu a přiřazení výsledku proměnné.</span><span class="sxs-lookup"><span data-stu-id="8395c-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="8395c-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8395c-126">See also</span></span>

- [<span data-ttu-id="8395c-127">>> – operátor</span><span class="sxs-lookup"><span data-stu-id="8395c-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [<span data-ttu-id="8395c-128">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="8395c-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="8395c-129">Operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="8395c-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="8395c-130">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8395c-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="8395c-131">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="8395c-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="8395c-132">Příkazy</span><span class="sxs-lookup"><span data-stu-id="8395c-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
