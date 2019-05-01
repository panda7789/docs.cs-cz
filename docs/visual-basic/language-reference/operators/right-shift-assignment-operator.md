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
ms.openlocfilehash: 1076ce62077391f2c88ebdd621d1dbd6fb40d647
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982381"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="1c146-102">>>= Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c146-102">>>= Operator (Visual Basic)</span></span>
<span data-ttu-id="1c146-103">Provede aritmetický posunutí doprava na základě hodnoty proměnnou nebo vlastnost a přiřadí výsledek zpět na proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1c146-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c146-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c146-104">Syntax</span></span>  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="1c146-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="1c146-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="1c146-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1c146-106">Required.</span></span> <span data-ttu-id="1c146-107">Proměnná nebo vlastnost celočíselného typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).</span><span class="sxs-lookup"><span data-stu-id="1c146-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="1c146-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="1c146-108">Required.</span></span> <span data-ttu-id="1c146-109">Číselný výraz datový typ, který rozšiřuje na `Integer`.</span><span class="sxs-lookup"><span data-stu-id="1c146-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c146-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c146-110">Remarks</span></span>  
 <span data-ttu-id="1c146-111">Element na levé straně `>>=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="1c146-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="1c146-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="1c146-112">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="1c146-113">`>>=` Operátor nejprve provádí aritmetické posunutí doprava na hodnotě proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1c146-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="1c146-114">Operátor, který se pak přiřadí výsledek této operace zpět na proměnnou nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1c146-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="1c146-115">Aritmetické staffhubu nejsou cyklické, což znamená, že nejsou na druhém konci znovuzavedeno bity posunuly jeden konec výsledek.</span><span class="sxs-lookup"><span data-stu-id="1c146-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="1c146-116">V aritmetické posunutí doprava bity posunuta nad rámec úplně vpravo bitová pozice se zahodí a bit nejvíce vlevo je postoupena do bitové pozice uvolněné na levé straně.</span><span class="sxs-lookup"><span data-stu-id="1c146-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="1c146-117">To znamená, že pokud `variableorproperty` má zápornou hodnotu uvolněných pozic jsou nastavené na jednu.</span><span class="sxs-lookup"><span data-stu-id="1c146-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="1c146-118">Pokud `variableorproperty` kladné, nebo pokud je jeho datový typ je typ bez znaménka, uvolněných pozic nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="1c146-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="1c146-119">Přetížení</span><span class="sxs-lookup"><span data-stu-id="1c146-119">Overloading</span></span>  
 <span data-ttu-id="1c146-120">[>> Operátor](../../../visual-basic/language-reference/operators/right-shift-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="1c146-120">The [>> Operator](../../../visual-basic/language-reference/operators/right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="1c146-121">Přetížení `>>` operátor má vliv na chování `>>=` operátor.</span><span class="sxs-lookup"><span data-stu-id="1c146-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="1c146-122">Pokud váš kód používá `>>=` v třídě nebo struktuře, která přetížení `>>`, je nutné pochopit jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="1c146-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="1c146-123">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="1c146-123">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c146-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c146-124">Example</span></span>  
 <span data-ttu-id="1c146-125">V následujícím příkladu `>>=` operátor shift bitový vzor z `Integer` proměnnou přímo na určenou dobu a přiřadit výsledek do proměnné.</span><span class="sxs-lookup"><span data-stu-id="1c146-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="1c146-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1c146-126">See also</span></span>

- [<span data-ttu-id="1c146-127">>> – operátor</span><span class="sxs-lookup"><span data-stu-id="1c146-127">>> Operator</span></span>](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [<span data-ttu-id="1c146-128">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="1c146-128">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="1c146-129">Operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="1c146-129">Bit Shift Operators</span></span>](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [<span data-ttu-id="1c146-130">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1c146-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="1c146-131">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="1c146-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="1c146-132">Příkazy</span><span class="sxs-lookup"><span data-stu-id="1c146-132">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
