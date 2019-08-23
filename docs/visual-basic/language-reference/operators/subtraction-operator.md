---
title: '- – Operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: eb34b34986613f36b624c43c04f98390ffba4fe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965856"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="24861-102">- – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24861-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="24861-103">Vrátí rozdíl mezi dvěma číselnými výrazy nebo zápornou hodnotu číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="24861-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24861-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24861-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="24861-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="24861-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="24861-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="24861-106">Required.</span></span> <span data-ttu-id="24861-107">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="24861-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="24861-108">Povinné, pokud `–` operátor nevypočítá zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="24861-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="24861-109">Libovolný číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="24861-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="24861-110">Výsledek</span><span class="sxs-lookup"><span data-stu-id="24861-110">Result</span></span>  
 <span data-ttu-id="24861-111">Výsledkem je rozdíl mezi `expression1` hodnotami a `expression2`, nebo `expression1`s hodnotou negace.</span><span class="sxs-lookup"><span data-stu-id="24861-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="24861-112">Výsledný datový typ je číselný typ odpovídající datovým typům `expression1` a. `expression2`</span><span class="sxs-lookup"><span data-stu-id="24861-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="24861-113">Podívejte se na tabulky "celočíselné aritmetické" v [datových typech výsledků operátoru](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="24861-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="24861-114">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="24861-114">Supported Types</span></span>  
 <span data-ttu-id="24861-115">Všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="24861-115">All numeric types.</span></span> <span data-ttu-id="24861-116">To zahrnuje typy unsigned a float-Point a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="24861-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24861-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24861-117">Remarks</span></span>  
 <span data-ttu-id="24861-118">V prvním použití zobrazeném v syntaxi uvedené dříve `–` je operátor *binární* aritmetický operátor odčítání pro rozdíl mezi dvěma číselnými výrazy.</span><span class="sxs-lookup"><span data-stu-id="24861-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="24861-119">Ve druhém použití zobrazeném v syntaxi, která `–` byla dříve uvedena, je operátor *unární* operátor negace pro zápornou hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="24861-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="24861-120">V tomto smyslu se negace skládá z opačného znaménka `expression1` , aby byl výsledek kladný, pokud `expression1` je záporné.</span><span class="sxs-lookup"><span data-stu-id="24861-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="24861-121">Pokud se některý výraz vyhodnotí jako [Nothing](../../../visual-basic/language-reference/nothing.md), `–` operátor ho považuje za nulu.</span><span class="sxs-lookup"><span data-stu-id="24861-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24861-122">Operátor může být přetížen, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. `–`</span><span class="sxs-lookup"><span data-stu-id="24861-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="24861-123">Pokud váš kód používá tento operátor v takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování.</span><span class="sxs-lookup"><span data-stu-id="24861-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="24861-124">Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="24861-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="24861-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="24861-125">Example</span></span>  
 <span data-ttu-id="24861-126">Následující příklad používá `–` operátor k výpočtu a vrácení rozdílu mezi dvěma čísly a pak pro negaci čísla.</span><span class="sxs-lookup"><span data-stu-id="24861-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="24861-127">Po provedení těchto příkazů `binaryResult` obsahuje 124,45 a `unaryResult` obsahuje – 334,90.</span><span class="sxs-lookup"><span data-stu-id="24861-127">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24861-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24861-128">See also</span></span>

- [<span data-ttu-id="24861-129">-= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="24861-129">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="24861-130">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="24861-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="24861-131">Priorita operátorů v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24861-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="24861-132">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="24861-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="24861-133">Aritmetické operátory v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24861-133">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
