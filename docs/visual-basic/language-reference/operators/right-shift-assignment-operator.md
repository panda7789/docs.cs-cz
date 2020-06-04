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
ms.openlocfilehash: c3afe2bcc4b9732b5afd34df1b83eaebe707b3f5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409293"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="30291-102">>>= – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30291-102">>>= Operator (Visual Basic)</span></span>
<span data-ttu-id="30291-103">Provede aritmetický pravý posun na hodnotu proměnné nebo vlastnosti a přiřadí výsledek zpátky proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="30291-103">Performs an arithmetic right shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30291-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30291-104">Syntax</span></span>  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="30291-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="30291-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="30291-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="30291-106">Required.</span></span> <span data-ttu-id="30291-107">Proměnná nebo vlastnost integrálního typu ( `SByte` , `Byte` , `Short` , `UShort` , `Integer` , `UInteger` , `Long` , nebo `ULong` ).</span><span class="sxs-lookup"><span data-stu-id="30291-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="30291-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="30291-108">Required.</span></span> <span data-ttu-id="30291-109">Číselný výraz datového typu, který se rozšiřuje na `Integer` .</span><span class="sxs-lookup"><span data-stu-id="30291-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30291-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30291-110">Remarks</span></span>  
 <span data-ttu-id="30291-111">Element na levé straně `>>=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="30291-111">The element on the left side of the `>>=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="30291-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="30291-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="30291-113">`>>=`Operátor nejprve provede aritmetický pravý posun na hodnotu proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="30291-113">The `>>=` operator first performs an arithmetic right shift on the value of the variable or property.</span></span> <span data-ttu-id="30291-114">Operátor potom přiřadí výsledek této operace zpátky k proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="30291-114">The operator then assigns the result of that operation back to the variable or property.</span></span>  
  
 <span data-ttu-id="30291-115">Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="30291-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="30291-116">V aritmetickém pravém posunu se bity po pravém horním rohu zahodí a bit umístěný nejvíce vlevo se rozšíří do bitových pozic uvolněné vlevo.</span><span class="sxs-lookup"><span data-stu-id="30291-116">In an arithmetic right shift, the bits shifted beyond the rightmost bit position are discarded, and the leftmost bit is propagated into the bit positions vacated at the left.</span></span> <span data-ttu-id="30291-117">To znamená, že pokud `variableorproperty` má zápornou hodnotu, pozice uvolněné jsou nastaveny na jednu.</span><span class="sxs-lookup"><span data-stu-id="30291-117">This means that if `variableorproperty` has a negative value, the vacated positions are set to one.</span></span> <span data-ttu-id="30291-118">Pokud `variableorproperty` je kladné, nebo pokud je jeho datový typ typu bez znaménka, pozice uvolněné jsou nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="30291-118">If `variableorproperty` is positive, or if its data type is an unsigned type, the vacated positions are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="30291-119">Přetížení</span><span class="sxs-lookup"><span data-stu-id="30291-119">Overloading</span></span>  
 <span data-ttu-id="30291-120">[Operátor>> ](right-shift-operator.md) lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="30291-120">The [>> Operator](right-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="30291-121">Přetížení `>>` operátoru ovlivňuje chování `>>=` operátoru.</span><span class="sxs-lookup"><span data-stu-id="30291-121">Overloading the `>>` operator affects the behavior of the `>>=` operator.</span></span> <span data-ttu-id="30291-122">Pokud váš kód používá `>>=` pro třídu nebo strukturu, která je přetížena `>>` , ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="30291-122">If your code uses `>>=` on a class or structure that overloads `>>`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="30291-123">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="30291-123">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="30291-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="30291-124">Example</span></span>  
 <span data-ttu-id="30291-125">Následující příklad používá `>>=` operátor k posunu bitového vzoru `Integer` proměnné přímo o zadanou hodnotu a k proměnné přiřadí výsledek.</span><span class="sxs-lookup"><span data-stu-id="30291-125">The following example uses the `>>=` operator to shift the bit pattern of an `Integer` variable right by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a><span data-ttu-id="30291-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="30291-126">See also</span></span>

- [<span data-ttu-id="30291-127">Operátor>> </span><span class="sxs-lookup"><span data-stu-id="30291-127">>> Operator</span></span>](right-shift-operator.md)
- [<span data-ttu-id="30291-128">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="30291-128">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="30291-129">Operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="30291-129">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="30291-130">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30291-130">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="30291-131">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="30291-131">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="30291-132">Příkazy</span><span class="sxs-lookup"><span data-stu-id="30291-132">Statements</span></span>](../../programming-guide/language-features/statements.md)
