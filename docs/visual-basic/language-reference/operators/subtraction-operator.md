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
ms.openlocfilehash: 8526f632b7e54c03bd16c3af70375179cd7cf277
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724470"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="869a4-102">- – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="869a4-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="869a4-103">Vrátí rozdíl dvou numerických výrazů nebo zápornou hodnotu číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="869a4-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="869a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="869a4-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="869a4-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="869a4-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="869a4-106">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="869a4-106">Required.</span></span> <span data-ttu-id="869a4-107">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="869a4-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="869a4-108">Vyžaduje se, pokud `–` operátor je výpočet zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="869a4-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="869a4-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="869a4-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="869a4-110">Výsledek</span><span class="sxs-lookup"><span data-stu-id="869a4-110">Result</span></span>  
 <span data-ttu-id="869a4-111">Výsledkem je rozdíl mezi `expression1` a `expression2`, nebo hodnotu negovaným čítačem `expression1`.</span><span class="sxs-lookup"><span data-stu-id="869a4-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="869a4-112">Datový typ výsledku je vhodný pro datové typy číselného typu `expression1` a `expression2`.</span><span class="sxs-lookup"><span data-stu-id="869a4-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="869a4-113">Viz "Celočíselné aritmetiky" tabulky v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="869a4-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="869a4-114">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="869a4-114">Supported Types</span></span>  
 <span data-ttu-id="869a4-115">Všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="869a4-115">All numeric types.</span></span> <span data-ttu-id="869a4-116">Jedná se o typy bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="869a4-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="869a4-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="869a4-117">Remarks</span></span>  
 <span data-ttu-id="869a4-118">V prvním využití je znázorněno v syntaxi uvedenému výše `–` operátor je *binární* operátor aritmetické odčítání pro rozdíl dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="869a4-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="869a4-119">V druhém využití je znázorněno v syntaxi uvedenému výše `–` operátor je *unární* operátor negace záporné hodnoty výrazu.</span><span class="sxs-lookup"><span data-stu-id="869a4-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="869a4-120">V tomto smyslu negaci se skládá z vrácení znaménko `expression1` tak, aby, výsledek je kladný Pokud `expression1` je záporný.</span><span class="sxs-lookup"><span data-stu-id="869a4-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="869a4-121">Pokud je výraz vyhodnocen jako [nic](../../../visual-basic/language-reference/nothing.md), `–` operátor zpracovává jako nula.</span><span class="sxs-lookup"><span data-stu-id="869a4-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="869a4-122">`–` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="869a4-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="869a4-123">Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="869a4-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="869a4-124">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="869a4-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="869a4-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="869a4-125">Example</span></span>  
 <span data-ttu-id="869a4-126">V následujícím příkladu `–` operátor vypočítá a vrátí rozdíl dvou čísel a který se má negovat číslo.</span><span class="sxs-lookup"><span data-stu-id="869a4-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 <span data-ttu-id="869a4-127">Po spuštění těchto příkazů `binaryResult` obsahuje 124.45 a `unaryResult` obsahuje –334.90.</span><span class="sxs-lookup"><span data-stu-id="869a4-127">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="869a4-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="869a4-128">See also</span></span>
- [<span data-ttu-id="869a4-129">-= – Operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="869a4-129">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="869a4-130">Aritmetické operátory</span><span class="sxs-lookup"><span data-stu-id="869a4-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="869a4-131">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="869a4-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="869a4-132">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="869a4-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="869a4-133">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="869a4-133">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
