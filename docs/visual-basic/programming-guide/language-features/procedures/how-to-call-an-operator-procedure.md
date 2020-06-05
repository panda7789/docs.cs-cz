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
ms.openlocfilehash: fa2bc5417b8b917ff48502a5bd0a4daa21fab67e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388566"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a><span data-ttu-id="c40f9-102">Postupy: Volání procedury operátora (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c40f9-102">How to: Call an Operator Procedure (Visual Basic)</span></span>
<span data-ttu-id="c40f9-103">Proceduru operátoru zavoláte pomocí symbolu operátoru ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="c40f9-103">You call an operator procedure by using the operator symbol in an expression.</span></span> <span data-ttu-id="c40f9-104">V případě operátoru převodu zavoláte [funkci CType](../../../language-reference/functions/ctype-function.md) pro převod hodnoty z jednoho datového typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="c40f9-104">In the case of a conversion operator, you call the [CType Function](../../../language-reference/functions/ctype-function.md) to convert a value from one data type to another.</span></span>  
  
 <span data-ttu-id="c40f9-105">Explicitně Nevolejte procedury operátora.</span><span class="sxs-lookup"><span data-stu-id="c40f9-105">You do not call operator procedures explicitly.</span></span> <span data-ttu-id="c40f9-106">Stačí použít operátor nebo `CType` funkci v příkazu přiřazení nebo výrazu stejným způsobem, jakým obvykle používáte operátor.</span><span class="sxs-lookup"><span data-stu-id="c40f9-106">You just use the operator, or the `CType` function, in an assignment statement or an expression, the same way you ordinarily use an operator.</span></span> <span data-ttu-id="c40f9-107">Visual Basic provede volání procedury operátoru.</span><span class="sxs-lookup"><span data-stu-id="c40f9-107">Visual Basic makes the call to the operator procedure.</span></span>  
  
 <span data-ttu-id="c40f9-108">Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.</span><span class="sxs-lookup"><span data-stu-id="c40f9-108">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
### <a name="to-call-an-operator-procedure"></a><span data-ttu-id="c40f9-109">Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="c40f9-109">To call an operator procedure</span></span>  
  
1. <span data-ttu-id="c40f9-110">Používejte symbol operátoru ve výrazu běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="c40f9-110">Use the operator symbol in an expression in the ordinary way.</span></span>  
  
2. <span data-ttu-id="c40f9-111">Ujistěte se, že datové typy operandů jsou vhodné pro operátor a ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c40f9-111">Be sure the data types of the operands are appropriate for the operator, and in the correct order.</span></span>  
  
3. <span data-ttu-id="c40f9-112">Operátor přispívá k hodnotě výrazu podle očekávání.</span><span class="sxs-lookup"><span data-stu-id="c40f9-112">The operator contributes to the value of the expression as expected.</span></span>  
  
### <a name="to-call-a-conversion-operator-procedure"></a><span data-ttu-id="c40f9-113">Volání procedury operátora převodu</span><span class="sxs-lookup"><span data-stu-id="c40f9-113">To call a conversion operator procedure</span></span>  
  
1. <span data-ttu-id="c40f9-114">Použijte `CType` uvnitř výrazu.</span><span class="sxs-lookup"><span data-stu-id="c40f9-114">Use `CType` inside an expression.</span></span>  
  
2. <span data-ttu-id="c40f9-115">Ujistěte se, že datové typy operandů jsou vhodné pro převod a ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c40f9-115">Be sure the data types of the operands are appropriate for the conversion, and in the correct order.</span></span>  
  
3. <span data-ttu-id="c40f9-116">`CType`volá proceduru operátora převodu a vrátí převedenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c40f9-116">`CType` calls the conversion operator procedure and returns the converted value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c40f9-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="c40f9-117">Example</span></span>  
 <span data-ttu-id="c40f9-118">Následující příklad vytvoří dvě <xref:System.TimeSpan> struktury, přidá je dohromady a uloží výsledek do třetí <xref:System.TimeSpan> struktury.</span><span class="sxs-lookup"><span data-stu-id="c40f9-118">The following example creates two <xref:System.TimeSpan> structures, adds them together, and stores the result in a third <xref:System.TimeSpan> structure.</span></span> <span data-ttu-id="c40f9-119"><xref:System.TimeSpan>Struktura definuje procedury operátoru pro přetížení několika standardních operátorů.</span><span class="sxs-lookup"><span data-stu-id="c40f9-119">The <xref:System.TimeSpan> structure defines operator procedures to overload several standard operators.</span></span>  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <span data-ttu-id="c40f9-120">Vzhledem k tomu <xref:System.TimeSpan> , že přetěžuje `+` operátor Standard, předchozí příklad volá proceduru operátoru při výpočtu hodnoty `combinedSpan` .</span><span class="sxs-lookup"><span data-stu-id="c40f9-120">Because <xref:System.TimeSpan> overloads the standard `+` operator, the previous example calls an operator procedure when it calculates the value of `combinedSpan`.</span></span>  
  
 <span data-ttu-id="c40f9-121">Příklad volání procedury operátoru konverzace naleznete v tématu [How to: Use a Class definující operátory](./how-to-use-a-class-that-defines-operators.md).</span><span class="sxs-lookup"><span data-stu-id="c40f9-121">For an example of calling a conversation operator procedure, see [How to: Use a Class that Defines Operators](./how-to-use-a-class-that-defines-operators.md).</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="c40f9-122">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="c40f9-122">Compile the code</span></span>  
 <span data-ttu-id="c40f9-123">Ujistěte se, že třída nebo struktura, kterou používáte, definuje operátor, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="c40f9-123">Be sure the class or structure you are using defines the operator you want to use.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c40f9-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="c40f9-124">See also</span></span>

- [<span data-ttu-id="c40f9-125">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="c40f9-125">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="c40f9-126">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="c40f9-126">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="c40f9-127">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="c40f9-127">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="c40f9-128">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="c40f9-128">Operator Statement</span></span>](../../../language-reference/statements/operator-statement.md)
- [<span data-ttu-id="c40f9-129">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="c40f9-129">Widening</span></span>](../../../language-reference/modifiers/widening.md)
- [<span data-ttu-id="c40f9-130">Narrowing</span><span class="sxs-lookup"><span data-stu-id="c40f9-130">Narrowing</span></span>](../../../language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="c40f9-131">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="c40f9-131">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="c40f9-132">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="c40f9-132">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="c40f9-133">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="c40f9-133">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="c40f9-134">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="c40f9-134">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
