---
title: 'Postupy: Volání procedury operátora'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: a685be7cc3b346b271413e2c29faae5a839313f4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74340248"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="77a59-102">Postupy: Volání procedury operátora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="77a59-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="77a59-103">Proceduru operátoru zavoláte pomocí symbolu operátoru ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="77a59-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="77a59-104">V případě operátoru převodu zavoláte [funkci CType](../../../../visual-basic/language-reference/functions/ctype-function.md) pro převod hodnoty z jednoho datového typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="77a59-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="77a59-105">Explicitně Nevolejte procedury operátora.</span><span class="sxs-lookup"><span data-stu-id="77a59-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="77a59-106">Stačí použít operátor nebo funkci `CType` v příkazu přiřazení nebo výrazu stejným způsobem, jakým obvykle používáte operátor.</span><span class="sxs-lookup"><span data-stu-id="77a59-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="77a59-107">Visual Basic provede volání procedury operátoru.</span><span class="sxs-lookup"><span data-stu-id="77a59-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="77a59-108">Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.</span><span class="sxs-lookup"><span data-stu-id="77a59-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="77a59-109">Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="77a59-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="77a59-110">Používejte symbol operátoru ve výrazu běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="77a59-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="77a59-111">Ujistěte se, že datové typy operandů jsou vhodné pro operátor a ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="77a59-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="77a59-112">Operátor přispívá k hodnotě výrazu podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="77a59-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="77a59-113">Volání procedury operátora převodu</span><span class="sxs-lookup"><span data-stu-id="77a59-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="77a59-114">Použijte `CType` uvnitř výrazu.</span><span class="sxs-lookup"><span data-stu-id="77a59-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="77a59-115">Ujistěte se, že datové typy operandů jsou vhodné pro převod a ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="77a59-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="77a59-116">`CType` volá proceduru operátora převodu a vrátí převedenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="77a59-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77a59-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="77a59-117">Example</span></span>  
 <span data-ttu-id="77a59-118">Následující příklad vytvoří dvě struktury <xref:System.TimeSpan>, přidá je dohromady a uloží výsledek do třetí <xref:System.TimeSpan> struktury.</span><span class="sxs-lookup"><span data-stu-id="77a59-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="77a59-119">Struktura <xref:System.TimeSpan> definuje procedury operátoru pro přetížení několika standardních operátorů.</span><span class="sxs-lookup"><span data-stu-id="77a59-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="77a59-120">Vzhledem k tomu, že <xref:System.TimeSpan> přetěžuje standardní operátor `+`, předchozí příklad volá proceduru operátoru při výpočtu hodnoty `combinedSpan`.</span><span class="sxs-lookup"><span data-stu-id="77a59-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="77a59-121">Příklad volání procedury operátoru konverzace naleznete v tématu [How to: Use a Class definující operátory](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="77a59-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="77a59-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="77a59-122">Compiling the Code</span></span>  
 <span data-ttu-id="77a59-123">Ujistěte se, že třída nebo struktura, kterou používáte, definuje operátor, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="77a59-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77a59-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77a59-124">See also</span></span>

- [<span data-ttu-id="77a59-125">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="77a59-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="77a59-126">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="77a59-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="77a59-127">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="77a59-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="77a59-128">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="77a59-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="77a59-129">Widening</span><span class="sxs-lookup"><span data-stu-id="77a59-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="77a59-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="77a59-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="77a59-131">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="77a59-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="77a59-132">Postupy: Definice struktury</span><span class="sxs-lookup"><span data-stu-id="77a59-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="77a59-133">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="77a59-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="77a59-134">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="77a59-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
