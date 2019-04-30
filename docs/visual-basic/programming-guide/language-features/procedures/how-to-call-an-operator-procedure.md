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
ms.openlocfilehash: d68781aa12ab7c1c717031ca252c5f3120649edc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863932"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="415f8-102">Postupy: Volání procedury operátora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="415f8-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="415f8-103">Volání procedury operátora pomocí symbol operátoru ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="415f8-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="415f8-104">V případě operátor převodu, volání [funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md) převést hodnotu z jednoho datového typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="415f8-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="415f8-105">Procedury operátoru není explicitně volat.</span><span class="sxs-lookup"><span data-stu-id="415f8-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="415f8-106">Stačí použít operátor, nebo `CType` funkce v příkazu přiřazení nebo výraz, stejně jako obvykle použijete operátor.</span><span class="sxs-lookup"><span data-stu-id="415f8-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="415f8-107">Visual Basic je volání procedury operátora.</span><span class="sxs-lookup"><span data-stu-id="415f8-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="415f8-108">Definování v třídě nebo struktuře operátor se také nazývá *přetížení* operátor.</span><span class="sxs-lookup"><span data-stu-id="415f8-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="415f8-109">Volání procedury operátora</span><span class="sxs-lookup"><span data-stu-id="415f8-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="415f8-110">Použijte symbol operátoru ve výrazu běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="415f8-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="415f8-111">Ujistěte se, že datové typy operandů jsou vhodné pro operátor a ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="415f8-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="415f8-112">Operátor, který přispívá k hodnotu výrazu podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="415f8-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="415f8-113">Volání procedury operátora převodu</span><span class="sxs-lookup"><span data-stu-id="415f8-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="415f8-114">Použití `CType` uvnitř výrazu.</span><span class="sxs-lookup"><span data-stu-id="415f8-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="415f8-115">Ujistěte se, že datové typy operandů jsou vhodné pro převod a ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="415f8-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="415f8-116">`CType` volání procedury operátora převodu a vrátí převedenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="415f8-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="415f8-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="415f8-117">Example</span></span>  
 <span data-ttu-id="415f8-118">Následující příklad vytvoří dva <xref:System.TimeSpan> struktury, přidá je dohromady a výsledek je uložen na třetí <xref:System.TimeSpan> struktury.</span><span class="sxs-lookup"><span data-stu-id="415f8-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="415f8-119"><xref:System.TimeSpan> Struktury definuje procedury operátoru přetížení několik standardních operátorů.</span><span class="sxs-lookup"><span data-stu-id="415f8-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="415f8-120">Protože <xref:System.TimeSpan> přetížení standardní `+` operátor v předchozím příkladu volání procedury operátora při výpočtu hodnoty `combinedSpan`.</span><span class="sxs-lookup"><span data-stu-id="415f8-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="415f8-121">Příklad volání procedury operátora konverzace, naleznete v tématu [jak: Použití třídy, která definuje operátory](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="415f8-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="415f8-122">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="415f8-122">Compiling the Code</span></span>  
 <span data-ttu-id="415f8-123">Ujistěte se, že třídy nebo struktury, které používáte definuje operátor, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="415f8-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="415f8-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="415f8-124">See also</span></span>

- [<span data-ttu-id="415f8-125">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="415f8-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="415f8-126">Postupy: Definovat operátor</span><span class="sxs-lookup"><span data-stu-id="415f8-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="415f8-127">Postupy: Definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="415f8-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="415f8-128">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="415f8-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="415f8-129">Widening</span><span class="sxs-lookup"><span data-stu-id="415f8-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="415f8-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="415f8-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="415f8-131">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="415f8-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="415f8-132">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="415f8-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="415f8-133">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="415f8-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="415f8-134">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="415f8-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
