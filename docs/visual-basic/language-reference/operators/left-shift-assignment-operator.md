---
title: <<= Operator (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: da2b5ca0b7538d77c3c8d8bc7d45712d656ce63a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768313"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="b2457-102">\<\<= Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2457-102">\<\<= Operator (Visual Basic)</span></span>
<span data-ttu-id="b2457-103">Provede aritmetický operátor posunu vlevo na základě hodnoty proměnnou nebo vlastnost a přiřadí výsledek zpět na proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b2457-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2457-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b2457-104">Syntax</span></span>  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="b2457-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b2457-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="b2457-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b2457-106">Required.</span></span> <span data-ttu-id="b2457-107">Proměnná nebo vlastnost celočíselného typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).</span><span class="sxs-lookup"><span data-stu-id="b2457-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="b2457-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b2457-108">Required.</span></span> <span data-ttu-id="b2457-109">Číselný výraz datový typ, který rozšiřuje na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="b2457-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2457-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2457-110">Remarks</span></span>  
 <span data-ttu-id="b2457-111">Element na levé straně `<<=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="b2457-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="b2457-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="b2457-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="b2457-113">`<<=` Operátor nejprve provede aritmetický operátor posunu vlevo na hodnotě proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b2457-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="b2457-114">Operátor, který se pak přiřadí výsledek této operace zpět na tuto proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b2457-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="b2457-115">Aritmetické staffhubu nejsou cyklické, což znamená, že nejsou na druhém konci znovuzavedeno bity posunuly jeden konec výsledek.</span><span class="sxs-lookup"><span data-stu-id="b2457-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="b2457-116">V aritmetických posunutí doleva bity posunuta mimo rozsah datového typu výsledku ignorovány a bitové pozice uvolněné na pravé straně jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="b2457-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b2457-117">Přetížení</span><span class="sxs-lookup"><span data-stu-id="b2457-117">Overloading</span></span>  
 <span data-ttu-id="b2457-118">[<< Operátor](../../../visual-basic/language-reference/operators/left-shift-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="b2457-118">The [<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b2457-119">Přetížení `<<` operátor má vliv na chování `<<=` operátor.</span><span class="sxs-lookup"><span data-stu-id="b2457-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="b2457-120">Pokud váš kód používá `<<=` v třídě nebo struktuře, která přetížení `<<`, je nutné pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="b2457-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b2457-121">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b2457-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2457-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2457-122">Example</span></span>  
 <span data-ttu-id="b2457-123">V následujícím příkladu `<<=` operátor shift bitový vzor z `Integer` proměnnou zanechaný určenou dobu a přiřadit výsledek do proměnné.</span><span class="sxs-lookup"><span data-stu-id="b2457-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="b2457-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2457-124">See also</span></span>

- [<span data-ttu-id="b2457-125"><< – operátor</span><span class="sxs-lookup"><span data-stu-id="b2457-125"><< Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [<span data-ttu-id="b2457-126">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="b2457-126">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="b2457-127">Operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="b2457-127">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="b2457-128">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b2457-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="b2457-129">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="b2457-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="b2457-130">Příkazy</span><span class="sxs-lookup"><span data-stu-id="b2457-130">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
