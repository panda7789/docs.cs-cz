---
title: 'Postupy: Volání procedury operátora (Visual Basic)'
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
ms.openlocfilehash: ab9dd9e3f9abdd8379a59ed458c47d5ec8b4f2ad
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978966"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="6883f-102">Postupy: Volání procedury operátora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6883f-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="6883f-103">Volání procedury operátora pomocí symbol operátoru ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="6883f-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="6883f-104">V případě operátor převodu, volání [funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md) převést hodnotu z jednoho datového typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="6883f-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="6883f-105">Procedury operátoru není explicitně volat.</span><span class="sxs-lookup"><span data-stu-id="6883f-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="6883f-106">Stačí použít operátor, nebo `CType` funkce v příkazu přiřazení nebo výraz, stejně jako obvykle použijete operátor.</span><span class="sxs-lookup"><span data-stu-id="6883f-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="6883f-107">Visual Basic je volání procedury operátora.</span><span class="sxs-lookup"><span data-stu-id="6883f-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="6883f-108">Definování v třídě nebo struktuře operátor se také nazývá *přetížení* operátor.</span><span class="sxs-lookup"><span data-stu-id="6883f-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="6883f-109">Volání procedury operátora</span><span class="sxs-lookup"><span data-stu-id="6883f-109">To call an operator procedure</span></span>  
  
1.  <span data-ttu-id="6883f-110">Použijte symbol operátoru ve výrazu běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="6883f-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2.  <span data-ttu-id="6883f-111">Ujistěte se, že datové typy operandů jsou vhodné pro operátor a ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6883f-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="6883f-112">Operátor, který přispívá k hodnotu výrazu podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="6883f-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="6883f-113">Volání procedury operátora převodu</span><span class="sxs-lookup"><span data-stu-id="6883f-113">To call a conversion operator procedure</span></span>  
  
1.  <span data-ttu-id="6883f-114">Použití `CType` uvnitř výrazu.</span><span class="sxs-lookup"><span data-stu-id="6883f-114">Use `CType` inside an expression.</span></span>  
  
2.  <span data-ttu-id="6883f-115">Ujistěte se, že datové typy operandů jsou vhodné pro převod a ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6883f-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3.  <span data-ttu-id="6883f-116">`CType` volání procedury operátora převodu a vrátí převedenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6883f-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6883f-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="6883f-117">Example</span></span>  
 <span data-ttu-id="6883f-118">Následující příklad vytvoří dva <xref:System.TimeSpan> struktury, přidá je dohromady a výsledek je uložen na třetí <xref:System.TimeSpan> struktury.</span><span class="sxs-lookup"><span data-stu-id="6883f-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="6883f-119"><xref:System.TimeSpan> Struktury definuje procedury operátoru přetížení několik standardních operátorů.</span><span class="sxs-lookup"><span data-stu-id="6883f-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="6883f-120">Protože <xref:System.TimeSpan> přetížení standardní `+` operátor v předchozím příkladu volání procedury operátora při výpočtu hodnoty `combinedSpan`.</span><span class="sxs-lookup"><span data-stu-id="6883f-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="6883f-121">Příklad volání procedury operátora konverzace, naleznete v tématu [jak: Použití třídy, která definuje operátory](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="6883f-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6883f-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6883f-122">Compiling the Code</span></span>  
 <span data-ttu-id="6883f-123">Ujistěte se, že třídy nebo struktury, které používáte definuje operátor, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="6883f-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6883f-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6883f-124">See also</span></span>
- [<span data-ttu-id="6883f-125">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="6883f-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="6883f-126">Postupy: Definovat operátor</span><span class="sxs-lookup"><span data-stu-id="6883f-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="6883f-127">Postupy: Definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="6883f-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="6883f-128">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="6883f-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="6883f-129">Widening</span><span class="sxs-lookup"><span data-stu-id="6883f-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="6883f-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="6883f-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="6883f-131">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="6883f-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="6883f-132">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="6883f-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="6883f-133">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="6883f-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="6883f-134">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="6883f-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
