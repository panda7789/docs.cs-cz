---
title: '* Operátor'
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
ms.openlocfilehash: f1a7653fb3006ab3c9736ec168a8c5ea028f4763
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409313"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="7fa66-102">\* – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7fa66-102">\* Operator (Visual Basic)</span></span>
<span data-ttu-id="7fa66-103">Vynásobí dvě čísla.</span><span class="sxs-lookup"><span data-stu-id="7fa66-103">Multiplies two numbers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7fa66-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7fa66-104">Syntax</span></span>  
  
```vb  
number1 * number2  
```  
  
## <a name="parts"></a><span data-ttu-id="7fa66-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="7fa66-105">Parts</span></span>  
  
|<span data-ttu-id="7fa66-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="7fa66-106">Term</span></span>|<span data-ttu-id="7fa66-107">Definice</span><span class="sxs-lookup"><span data-stu-id="7fa66-107">Definition</span></span>|  
|---|---|  
|`number1`|<span data-ttu-id="7fa66-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7fa66-108">Required.</span></span> <span data-ttu-id="7fa66-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="7fa66-109">Any numeric expression.</span></span>|  
|`number2`|<span data-ttu-id="7fa66-110">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7fa66-110">Required.</span></span> <span data-ttu-id="7fa66-111">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="7fa66-111">Any numeric expression.</span></span>|  
  
## <a name="result"></a><span data-ttu-id="7fa66-112">Výsledek</span><span class="sxs-lookup"><span data-stu-id="7fa66-112">Result</span></span>  
 <span data-ttu-id="7fa66-113">Výsledkem je produkt `number1` a `number2` .</span><span class="sxs-lookup"><span data-stu-id="7fa66-113">The result is the product of `number1` and `number2`.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="7fa66-114">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="7fa66-114">Supported Types</span></span>  
 <span data-ttu-id="7fa66-115">Všechny číselné typy, včetně typů unsigned a float-Point a `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="7fa66-115">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7fa66-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7fa66-116">Remarks</span></span>  
 <span data-ttu-id="7fa66-117">Datový typ výsledku závisí na typech operandů.</span><span class="sxs-lookup"><span data-stu-id="7fa66-117">The data type of the result depends on the types of the operands.</span></span> <span data-ttu-id="7fa66-118">Následující tabulka ukazuje, jak je určen datový typ výsledku.</span><span class="sxs-lookup"><span data-stu-id="7fa66-118">The following table shows how the data type of the result is determined.</span></span>  
  
|<span data-ttu-id="7fa66-119">Datové typy operandů</span><span class="sxs-lookup"><span data-stu-id="7fa66-119">Operand data types</span></span>|<span data-ttu-id="7fa66-120">Výsledný datový typ</span><span class="sxs-lookup"><span data-stu-id="7fa66-120">Result data type</span></span>|  
|---|---|  
|<span data-ttu-id="7fa66-121">Oba výrazy jsou integrální datové typy ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger –](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ulong](../data-types/ulong-data-type.md)).</span><span class="sxs-lookup"><span data-stu-id="7fa66-121">Both expressions are integral data types ([SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md), [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md), [Integer](../data-types/integer-data-type.md), [UInteger](../data-types/uinteger-data-type.md), [Long](../data-types/long-data-type.md), [ULong](../data-types/ulong-data-type.md))</span></span>|<span data-ttu-id="7fa66-122">Číselný datový typ, který je vhodný pro datové typy `number1` a `number2` .</span><span class="sxs-lookup"><span data-stu-id="7fa66-122">A numeric data type appropriate for the data types of `number1` and `number2`.</span></span> <span data-ttu-id="7fa66-123">Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="7fa66-123">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>|  
|<span data-ttu-id="7fa66-124">Oba výrazy jsou [desítkové](../data-types/decimal-data-type.md) .</span><span class="sxs-lookup"><span data-stu-id="7fa66-124">Both expressions are [Decimal](../data-types/decimal-data-type.md)</span></span>|`Decimal`|  
|<span data-ttu-id="7fa66-125">Oba výrazy jsou [jednoduché](../data-types/single-data-type.md)</span><span class="sxs-lookup"><span data-stu-id="7fa66-125">Both expressions are [Single](../data-types/single-data-type.md)</span></span>|`Single`|  
|<span data-ttu-id="7fa66-126">Jeden z výrazů je datový typ s plovoucí desetinnou čárkou ( `Single` nebo [Double](../data-types/double-data-type.md)), ale ne oba `Single` (Poznámka `Decimal` není datový typ s plovoucí desetinnou čárkou).</span><span class="sxs-lookup"><span data-stu-id="7fa66-126">Either expression is a floating-point data type (`Single` or [Double](../data-types/double-data-type.md)) but not both `Single` (note `Decimal` is not a floating-point data type)</span></span>|`Double`|  
  
 <span data-ttu-id="7fa66-127">Pokud je výraz vyhodnocen jako [Nothing](../nothing.md), bude považován za nulu.</span><span class="sxs-lookup"><span data-stu-id="7fa66-127">If an expression evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="7fa66-128">Přetížení</span><span class="sxs-lookup"><span data-stu-id="7fa66-128">Overloading</span></span>  
 <span data-ttu-id="7fa66-129">`*`Operátor může být *přetížen*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="7fa66-129">The `*` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="7fa66-130">Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="7fa66-130">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="7fa66-131">Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="7fa66-131">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fa66-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="7fa66-132">Example</span></span>  
 <span data-ttu-id="7fa66-133">V tomto příkladu se používá `*` operátor k násobení dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="7fa66-133">This example uses the `*` operator to multiply two numbers.</span></span> <span data-ttu-id="7fa66-134">Výsledkem je součin dvou operandů.</span><span class="sxs-lookup"><span data-stu-id="7fa66-134">The result is the product of the two operands.</span></span>  
  
 [!code-vb[VbVbalrOperators#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="7fa66-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="7fa66-135">See also</span></span>

- [<span data-ttu-id="7fa66-136">\* = – Operátor</span><span class="sxs-lookup"><span data-stu-id="7fa66-136">\*= Operator</span></span>](multiplication-assignment-operator.md)
- [<span data-ttu-id="7fa66-137">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="7fa66-137">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="7fa66-138">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7fa66-138">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="7fa66-139">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="7fa66-139">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="7fa66-140">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7fa66-140">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
