---
title: 'Postupy: Volání procedury operátora (Visual Basic)'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 21545f2488bfabd0abc9c6e316d21bbc4d5aeb91
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="825ce-102">Postupy: Volání procedury operátora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="825ce-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="825ce-103">Symbol operátoru ve výrazu můžete volání procedury operátora.</span><span class="sxs-lookup"><span data-stu-id="825ce-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="825ce-104">V případě operátora převodu, zavoláte [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md) převést hodnotu z jednoho datového typu.</span><span class="sxs-lookup"><span data-stu-id="825ce-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="825ce-105">Procedury operátoru není volána explicitně.</span><span class="sxs-lookup"><span data-stu-id="825ce-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="825ce-106">Stačí použít operátor nebo `CType` funkce v příkazu přiřazení nebo výraz, stejně jako běžně použít operátor.</span><span class="sxs-lookup"><span data-stu-id="825ce-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="825ce-107">Visual Basic umožňuje volání procedury operátora.</span><span class="sxs-lookup"><span data-stu-id="825ce-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="825ce-108">Definování operátor na třídu nebo strukturu je také označován *přetížení* operátor.</span><span class="sxs-lookup"><span data-stu-id="825ce-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="825ce-109">K volání procedury operátora</span><span class="sxs-lookup"><span data-stu-id="825ce-109">To call an operator procedure</span></span>  
  
1.  <span data-ttu-id="825ce-110">Symbol operátoru používejte ve výrazu běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="825ce-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2.  <span data-ttu-id="825ce-111">Ujistěte se, že datové typy operandy jsou vhodné pro operátor a ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="825ce-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="825ce-112">Operátor přispívá k hodnotu výrazu podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="825ce-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="825ce-113">K volání procedury operátora převodu</span><span class="sxs-lookup"><span data-stu-id="825ce-113">To call a conversion operator procedure</span></span>  
  
1.  <span data-ttu-id="825ce-114">Použití `CType` uvnitř výrazu.</span><span class="sxs-lookup"><span data-stu-id="825ce-114">Use `CType` inside an expression.</span></span>  
  
2.  <span data-ttu-id="825ce-115">Ujistěte se, že datové typy operandy jsou vhodné pro převod a ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="825ce-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="825ce-116">`CType` volání procedury operátora převodu a vrátí převedenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="825ce-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="825ce-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="825ce-117">Example</span></span>  
 <span data-ttu-id="825ce-118">Následující příklad vytvoří dvě <xref:System.TimeSpan> struktury, přidá je dohromady a výsledek je uložen ve třetí <xref:System.TimeSpan> struktura.</span><span class="sxs-lookup"><span data-stu-id="825ce-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="825ce-119"><xref:System.TimeSpan> Struktura definuje postup operátor přetížení několik standardní operátory.</span><span class="sxs-lookup"><span data-stu-id="825ce-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](./codesnippet/VisualBasic/how-to-call-an-operator-procedure_1.vb)]  
  
 <span data-ttu-id="825ce-120">Protože <xref:System.TimeSpan> přetížení standardní `+` operátor, předchozí příklad volání procedury operátora při výpočtu hodnotu `combinedSpan`.</span><span class="sxs-lookup"><span data-stu-id="825ce-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="825ce-121">Příklad volání procedury operátora konverzace, naleznete v části [postupy: použití třídy, že definuje operátory](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="825ce-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="825ce-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="825ce-122">Compiling the Code</span></span>  
 <span data-ttu-id="825ce-123">Ujistěte se, že třídu nebo strukturu, který používáte definuje operátor, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="825ce-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825ce-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="825ce-124">See Also</span></span>  
 [<span data-ttu-id="825ce-125">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="825ce-125">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="825ce-126">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="825ce-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="825ce-127">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="825ce-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="825ce-128">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="825ce-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="825ce-129">Widening</span><span class="sxs-lookup"><span data-stu-id="825ce-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="825ce-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="825ce-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="825ce-131">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="825ce-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="825ce-132">Postupy: Definice struktury</span><span class="sxs-lookup"><span data-stu-id="825ce-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="825ce-133">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="825ce-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="825ce-134">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="825ce-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
