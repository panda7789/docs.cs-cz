---
title: '- Operátor (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4ffb7c96fe95e73dc857a15608df94ed8468f9df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="0cdf7-102">- – operátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0cdf7-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="0cdf7-103">Vrátí rozdíl mezi dvou numerických výrazů nebo zápornou hodnotu číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cdf7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cdf7-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="0cdf7-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="0cdf7-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="0cdf7-106">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-106">Required.</span></span> <span data-ttu-id="0cdf7-107">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="0cdf7-108">Vyžaduje, pokud `–` operátor je výpočet zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="0cdf7-109">Jakýkoli číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="0cdf7-110">Výsledek</span><span class="sxs-lookup"><span data-stu-id="0cdf7-110">Result</span></span>  
 <span data-ttu-id="0cdf7-111">Výsledkem je rozdíl mezi `expression1` a `expression2`, nebo posunut hodnotu `expression1`.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="0cdf7-112">Datový typ výsledků je vhodné pro datové typy číselného typu `expression1` a `expression2`.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="0cdf7-113">Podívejte se na tabulky "Celočíselné aritmetiky" v [typy výsledků operátoru Data](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="0cdf7-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="0cdf7-114">Podporované typy</span><span class="sxs-lookup"><span data-stu-id="0cdf7-114">Supported Types</span></span>  
 <span data-ttu-id="0cdf7-115">Všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-115">All numeric types.</span></span> <span data-ttu-id="0cdf7-116">To zahrnuje typy bez znaménka a s plovoucí desetinnou čárkou a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0cdf7-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0cdf7-117">Remarks</span></span>  
 <span data-ttu-id="0cdf7-118">V prvním použití zobrazí v syntaxi výše uvedený `–` operátor je *binární* operátor odčítání aritmetické pro rozdíl mezi dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="0cdf7-119">Druhý využití znázorněno v syntaxi výše uvedený `–` operátor je *unární* operátor negace pro zápornou hodnotu výrazu.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="0cdf7-120">V tomto smyslu negace se skládá z Prohodit znaménko `expression1` tak, aby výsledkem je kladné Pokud `expression1` záporné.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="0cdf7-121">Pokud výraz vyhodnocen jako [nic](../../../visual-basic/language-reference/nothing.md), `–` operátor se považuje za nula.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0cdf7-122">`–` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="0cdf7-123">Pokud váš kód používá tento operátor. v takových třídu nebo strukturu, ujistěte se, že rozumíte své Předefinovaná chování.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="0cdf7-124">Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="0cdf7-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cdf7-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="0cdf7-125">Example</span></span>  
 <span data-ttu-id="0cdf7-126">Následující příklad používá `–` operátor vypočítat a vrátí rozdíl dvou čísel a pak negate číslo.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]  
  
 <span data-ttu-id="0cdf7-127">Po provedení těchto příkazech `binaryResult` obsahuje 124.45 a `unaryResult` obsahuje –334.90.</span><span class="sxs-lookup"><span data-stu-id="0cdf7-127">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cdf7-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cdf7-128">See Also</span></span>  
 <span data-ttu-id="0cdf7-129">[-= – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="0cdf7-129">[-= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md) [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md)</span></span>  
 [<span data-ttu-id="0cdf7-130">Priorita operátorů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0cdf7-130">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="0cdf7-131">Operátory uvedené podle funkce</span><span class="sxs-lookup"><span data-stu-id="0cdf7-131">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="0cdf7-132">Aritmetické operátory v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0cdf7-132">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
