---
title: <<= – operátor
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
ms.openlocfilehash: ff7cbb02a9a10dbe11450491e93fd85fd77b44ba
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84370658"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="b1742-102">\<\<= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b1742-102">\<\<= Operator (Visual Basic)</span></span>
<span data-ttu-id="b1742-103">Provede aritmetický levý posun na hodnotu proměnné nebo vlastnosti a přiřadí výsledek zpátky proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b1742-103">Performs an arithmetic left shift on the value of a variable or property and assigns the result back to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1742-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1742-104">Syntax</span></span>  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a><span data-ttu-id="b1742-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b1742-105">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="b1742-106">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="b1742-106">Required.</span></span> <span data-ttu-id="b1742-107">Proměnná nebo vlastnost integrálního typu ( `SByte` , `Byte` , `Short` , `UShort` , `Integer` , `UInteger` , `Long` , nebo `ULong` ).</span><span class="sxs-lookup"><span data-stu-id="b1742-107">Variable or property of an integral type (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, or `ULong`).</span></span>  
  
 `amount`  
 <span data-ttu-id="b1742-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="b1742-108">Required.</span></span> <span data-ttu-id="b1742-109">Číselný výraz datového typu, který se rozšiřuje na `Integer` .</span><span class="sxs-lookup"><span data-stu-id="b1742-109">Numeric expression of a data type that widens to `Integer`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1742-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1742-110">Remarks</span></span>  
 <span data-ttu-id="b1742-111">Element na levé straně `<<=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole.</span><span class="sxs-lookup"><span data-stu-id="b1742-111">The element on the left side of the `<<=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="b1742-112">Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="b1742-112">The variable or property cannot be [ReadOnly](../modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="b1742-113">`<<=`Operátor nejprve provede aritmetický levý posun na hodnotu proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b1742-113">The `<<=` operator first performs an arithmetic left shift on the value of the variable or property.</span></span> <span data-ttu-id="b1742-114">Operátor potom přiřadí výsledek této operace zpátky k této proměnné nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b1742-114">The operator then assigns the result of that operation back to that variable or property.</span></span>  
  
 <span data-ttu-id="b1742-115">Aritmetické posuny nejsou cyklické, což znamená, že bity posunuté o jeden konec výsledku nejsou znovu zavedeny na druhém konci.</span><span class="sxs-lookup"><span data-stu-id="b1742-115">Arithmetic shifts are not circular, which means the bits shifted off one end of the result are not reintroduced at the other end.</span></span> <span data-ttu-id="b1742-116">V aritmetickém levém Shift se bity, které přesahují rozsah výsledných dat, zahodí a bitové pozice uvolněné na pravé straně mají nastavenou hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="b1742-116">In an arithmetic left shift, the bits shifted beyond the range of the result data type are discarded, and the bit positions vacated on the right are set to zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="b1742-117">Přetížení</span><span class="sxs-lookup"><span data-stu-id="b1742-117">Overloading</span></span>  
 <span data-ttu-id="b1742-118">[Operátor<< ](left-shift-operator.md) lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="b1742-118">The [<< Operator](left-shift-operator.md) can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="b1742-119">Přetížení `<<` operátoru ovlivňuje chování `<<=` operátoru.</span><span class="sxs-lookup"><span data-stu-id="b1742-119">Overloading the `<<` operator affects the behavior of the `<<=` operator.</span></span> <span data-ttu-id="b1742-120">Pokud váš kód používá `<<=` pro třídu nebo strukturu, která je přetížena `<<` , ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="b1742-120">If your code uses `<<=` on a class or structure that overloads `<<`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="b1742-121">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="b1742-121">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1742-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="b1742-122">Example</span></span>  
 <span data-ttu-id="b1742-123">Následující příklad používá `<<=` operátor k posunu bitového vzoru `Integer` proměnné vlevo o zadanou hodnotu a přiřazení výsledku proměnné.</span><span class="sxs-lookup"><span data-stu-id="b1742-123">The following example uses the `<<=` operator to shift the bit pattern of an `Integer` variable left by the specified amount and assign the result to the variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a><span data-ttu-id="b1742-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1742-124">See also</span></span>

- [<span data-ttu-id="b1742-125">Operátor<< </span><span class="sxs-lookup"><span data-stu-id="b1742-125"><< Operator</span></span>](left-shift-operator.md)
- [<span data-ttu-id="b1742-126">Operátory přiřazení</span><span class="sxs-lookup"><span data-stu-id="b1742-126">Assignment Operators</span></span>](assignment-operators.md)
- [<span data-ttu-id="b1742-127">Operátory bitového posunu</span><span class="sxs-lookup"><span data-stu-id="b1742-127">Bit Shift Operators</span></span>](bit-shift-operators.md)
- [<span data-ttu-id="b1742-128">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b1742-128">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="b1742-129">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="b1742-129">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="b1742-130">Příkazy</span><span class="sxs-lookup"><span data-stu-id="b1742-130">Statements</span></span>](../../programming-guide/language-features/statements.md)
