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
ms.openlocfilehash: b2a642b1187c9a08007ee1eddfa0764198fc0877
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981644"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="f8dc6-102">\<\<= Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f8dc6-102">\<\<= Operator (Visual Basic)</span></span>
<span data-ttu-id="f8dc6-103">Provede aritmetický operátor posunu vlevo na základě hodnoty proměnnou nebo vlastnost a přiřadí výsledek zpět na proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f8dc6-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8dc6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8dc6-104">Syntax</span></span>  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="f8dc6-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="f8dc6-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="f8dc6-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f8dc6-106">Required.</span></span> <span data-ttu-id="f8dc6-107">Proměnná nebo vlastnost celočíselného typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).</span><span class="sxs-lookup"><span data-stu-id="f8dc6-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="f8dc6-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="f8dc6-108">Required.</span></span> <span data-ttu-id="f8dc6-109">Číselný výraz datový typ, který rozšiřuje na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="f8dc6-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8dc6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8dc6-110">Remarks</span></span>  
 <span data-ttu-id="f8dc6-111">Element na levé straně `<<=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="f8dc6-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="f8dc6-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="f8dc6-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="f8dc6-113">`<<=` Operátor nejprve provede aritmetický operátor posunu vlevo na hodnotě proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f8dc6-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="f8dc6-114">Operátor, který se pak přiřadí výsledek této operace zpět na tuto proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f8dc6-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="f8dc6-115">Aritmetické staffhubu nejsou cyklické, což znamená, že nejsou na druhém konci znovuzavedeno bity posunuly jeden konec výsledek.</span><span class="sxs-lookup"><span data-stu-id="f8dc6-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="f8dc6-116">V aritmetických posunutí doleva bity posunuta mimo rozsah datového typu výsledku ignorovány a bitové pozice uvolněné na pravé straně jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="f8dc6-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="f8dc6-117">Přetížení</span><span class="sxs-lookup"><span data-stu-id="f8dc6-117">Overloading</span></span>  
 <span data-ttu-id="f8dc6-118">[<< Operátor](../../../visual-basic/language-reference/operators/left-shift-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="f8dc6-118">The [<< Operator](../../../visual-basic/language-reference/operators/left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="f8dc6-119">Přetížení `<<` operátor má vliv na chování `<<=` operátor.</span><span class="sxs-lookup"><span data-stu-id="f8dc6-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="f8dc6-120">Pokud váš kód používá `<<=` v třídě nebo struktuře, která přetížení `<<`, je nutné pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="f8dc6-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="f8dc6-121">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="f8dc6-121">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8dc6-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8dc6-122">Example</span></span>  
 <span data-ttu-id="f8dc6-123">V následujícím příkladu `<<=` operátor shift bitový vzor z `Integer` proměnnou zanechaný určenou dobu a přiřadit výsledek do proměnné.</span><span class="sxs-lookup"><span data-stu-id="f8dc6-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="f8dc6-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8dc6-124">See also</span></span>
- [<span data-ttu-id="f8dc6-125"><< – operátor</span><span class="sxs-lookup"><span data-stu-id="f8dc6-125"><< Operator</span></span>](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [<span data-ttu-id="f8dc6-126">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="f8dc6-126">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="f8dc6-127">Operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="f8dc6-127">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="f8dc6-128">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f8dc6-128">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="f8dc6-129">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="f8dc6-129">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="f8dc6-130">Příkazy</span><span class="sxs-lookup"><span data-stu-id="f8dc6-130">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
