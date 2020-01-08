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
ms.openlocfilehash: a977b17d4b2c797bbe38d289a57f3d9d31fa64fa
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345970"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="cc459-102">Postupy: Volání procedury operátora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cc459-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="cc459-103">Proceduru operátoru zavoláte pomocí symbolu operátoru ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="cc459-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="cc459-104">V případě operátoru převodu zavoláte [funkci CType](../../../../visual-basic/language-reference/functions/ctype-function.md) pro převod hodnoty z jednoho datového typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="cc459-104">In the case of a conversion operator, you call the [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="cc459-105">Explicitně Nevolejte procedury operátora.</span><span class="sxs-lookup"><span data-stu-id="cc459-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="cc459-106">Stačí použít operátor nebo funkci `CType` v příkazu přiřazení nebo výrazu stejným způsobem, jakým obvykle používáte operátor.</span><span class="sxs-lookup"><span data-stu-id="cc459-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="cc459-107">Visual Basic provede volání procedury operátoru.</span><span class="sxs-lookup"><span data-stu-id="cc459-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="cc459-108">Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.</span><span class="sxs-lookup"><span data-stu-id="cc459-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="cc459-109">Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="cc459-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="cc459-110">Používejte symbol operátoru ve výrazu běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="cc459-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="cc459-111">Ujistěte se, že datové typy operandů jsou vhodné pro operátor a ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cc459-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="cc459-112">Operátor přispívá k hodnotě výrazu podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="cc459-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="cc459-113">Volání procedury operátora převodu</span><span class="sxs-lookup"><span data-stu-id="cc459-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="cc459-114">Použijte `CType` uvnitř výrazu.</span><span class="sxs-lookup"><span data-stu-id="cc459-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="cc459-115">Ujistěte se, že datové typy operandů jsou vhodné pro převod a ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="cc459-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="cc459-116">`CType` volá proceduru operátora převodu a vrátí převedenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="cc459-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cc459-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="cc459-117">Example</span></span>  
 <span data-ttu-id="cc459-118">Následující příklad vytvoří dvě struktury <xref:System.TimeSpan>, přidá je dohromady a uloží výsledek do třetí <xref:System.TimeSpan> struktury.</span><span class="sxs-lookup"><span data-stu-id="cc459-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="cc459-119">Struktura <xref:System.TimeSpan> definuje procedury operátoru pro přetížení několika standardních operátorů.</span><span class="sxs-lookup"><span data-stu-id="cc459-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="cc459-120">Vzhledem k tomu, že <xref:System.TimeSpan> přetěžuje standardní operátor `+`, předchozí příklad volá proceduru operátoru při výpočtu hodnoty `combinedSpan`.</span><span class="sxs-lookup"><span data-stu-id="cc459-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="cc459-121">Příklad volání procedury operátoru konverzace naleznete v tématu [How to: Use a Class definující operátory](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="cc459-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="cc459-122">Kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cc459-122">Compile the code</span></span>  
 <span data-ttu-id="cc459-123">Ujistěte se, že třída nebo struktura, kterou používáte, definuje operátor, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="cc459-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc459-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc459-124">See also</span></span>

- [<span data-ttu-id="cc459-125">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="cc459-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="cc459-126">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="cc459-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="cc459-127">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="cc459-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="cc459-128">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="cc459-128">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="cc459-129">Widening</span><span class="sxs-lookup"><span data-stu-id="cc459-129">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="cc459-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="cc459-130">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="cc459-131">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="cc459-131">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="cc459-132">Postupy: Definice struktury</span><span class="sxs-lookup"><span data-stu-id="cc459-132">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="cc459-133">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="cc459-133">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="cc459-134">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="cc459-134">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
