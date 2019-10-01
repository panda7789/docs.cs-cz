---
title: '* – Operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*
helpviewer_keywords:
- arithmetic operators [Visual Basic], multiplication
- operators [Visual Basic], multiplication
- '* operator [Visual Basic]'
- multiplication operator [Visual Basic], syntax
- math operators [Visual Basic]
ms.assetid: 2b210382-99da-4195-89ba-b1d06f5e89ad
ms.openlocfilehash: b5b601c7604cb7ce1afaebc98b2157634a77fda4
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701095"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="89613-102">\* – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="89613-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="89613-103">Vynásobí dvě čísla.</span><span class="sxs-lookup"><span data-stu-id="89613-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89613-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89613-104">Syntax</span></span>  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="89613-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="89613-105">Parts</span></span>  
  
|<span data-ttu-id="89613-106">Termín</span><span class="sxs-lookup"><span data-stu-id="89613-106">Term</span></span>|<span data-ttu-id="89613-107">Definice</span><span class="sxs-lookup"><span data-stu-id="89613-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="89613-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="89613-108">Required.</span></span> <span data-ttu-id="89613-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="89613-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="89613-110">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="89613-110">Required.</span></span> <span data-ttu-id="89613-111">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="89613-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="89613-112">Výsledek</span><span class="sxs-lookup"><span data-stu-id="89613-112">Result</span></span>  
 <span data-ttu-id="89613-113">Výsledkem je součin `number1` a `number2`.</span><span class="sxs-lookup"><span data-stu-id="89613-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="89613-114">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="89613-114">Supported Types</span></span>  
 <span data-ttu-id="89613-115">Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="89613-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89613-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89613-116">Remarks</span></span>  
 <span data-ttu-id="89613-117">Datový typ výsledku závisí na typech operandů.</span><span class="sxs-lookup"><span data-stu-id="89613-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="89613-118">Následující tabulka ukazuje, jak je určen datový typ výsledku.</span><span class="sxs-lookup"><span data-stu-id="89613-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="89613-119">Datové typy operandů</span><span class="sxs-lookup"><span data-stu-id="89613-119">Operand data types</span></span>|<span data-ttu-id="89613-120">Výsledný datový typ</span><span class="sxs-lookup"><span data-stu-id="89613-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="89613-121">Oba výrazy jsou integrální datové typy ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger –](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ulong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)).</span><span class="sxs-lookup"><span data-stu-id="89613-121">Both expressions are integral data types ([SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md), [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md), [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md), [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="89613-122">Číselný datový typ, který je vhodný pro datové typy `number1` a `number2`.</span><span class="sxs-lookup"><span data-stu-id="89613-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="89613-123">Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="89613-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="89613-124">Oba výrazy jsou [desítkové](../../../visual-basic/language-reference/data-types/decimal-data-type.md) .</span><span class="sxs-lookup"><span data-stu-id="89613-124">Both expressions are [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="89613-125">Oba výrazy jsou [jednoduché](../../../visual-basic/language-reference/data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="89613-125">Both expressions are [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="89613-126">Jeden z výrazů je datový typ s plovoucí desetinnou čárkou (`Single` nebo [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)), ale ne oba `Single` (Poznámka `Decimal` není datový typ s plovoucí desetinnou čárkou).</span><span class="sxs-lookup"><span data-stu-id="89613-126">Either expression is a floating-point data type (`Single` or [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="89613-127">Pokud je výraz vyhodnocen jako [Nothing](../../../visual-basic/language-reference/nothing.md), bude považován za nulu.</span><span class="sxs-lookup"><span data-stu-id="89613-127">If an expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="89613-128">Přetížení</span><span class="sxs-lookup"><span data-stu-id="89613-128">Overloading</span></span>  
 <span data-ttu-id="89613-129">Operátor `*` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="89613-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="89613-130">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="89613-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="89613-131">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="89613-131">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="89613-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="89613-132">Example</span></span>  
 <span data-ttu-id="89613-133">V tomto příkladu se používá operátor `*` pro násobení dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="89613-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="89613-134">Výsledkem je součin dvou operandů.</span><span class="sxs-lookup"><span data-stu-id="89613-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="89613-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89613-135">See also</span></span>

- [<span data-ttu-id="89613-136">Operátor \*=</span><span class="sxs-lookup"><span data-stu-id="89613-136">\*= Operator</span></span>](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [<span data-ttu-id="89613-137">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="89613-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="89613-138">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89613-138">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="89613-139">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="89613-139">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="89613-140">Aritmetické operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="89613-140">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
