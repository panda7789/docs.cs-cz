---
title: 'Postupy: Použití třídy, která definuje operátory (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: bd512adf2f06ed0fbd3d36ed3175a0928bf1c57c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61863490"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="1a040-102">Postupy: Použití třídy, která definuje operátory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1a040-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="1a040-103">Pokud používáte třídu nebo strukturu, která definuje vlastní operátory, můžete tyto operátory přistupovat z jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1a040-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="1a040-104">Definování v třídě nebo struktuře operátor se také nazývá *přetížení* operátor.</span><span class="sxs-lookup"><span data-stu-id="1a040-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a040-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a040-105">Example</span></span>  
 <span data-ttu-id="1a040-106">Následující příklad přistupuje k SQL struktura <xref:System.Data.SqlTypes.SqlString>, která definuje operátory převodu ([funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) v obou směrech mezi řetězec jazyka Visual Basic a řetězec SQL.</span><span class="sxs-lookup"><span data-stu-id="1a040-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="1a040-107">Použití `CType(` *SQL řetězcového výrazu*, `String)` pro převod řetězce SQL na řetězec jazyka Visual Basic a `CType(` *výraz řetězce jazyka Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` pro převod opačným směrem.</span><span class="sxs-lookup"><span data-stu-id="1a040-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="1a040-108"><xref:System.Data.SqlTypes.SqlString> Struktury definuje operátor převodu ([CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` k <xref:System.Data.SqlTypes.SqlString> a druhý z <xref:System.Data.SqlTypes.SqlString> k `String`.</span><span class="sxs-lookup"><span data-stu-id="1a040-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="1a040-109">Příkaz, který přiřazuje `title` k `jobTitle` využívá první operátor a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> druhý používá volání funkce.</span><span class="sxs-lookup"><span data-stu-id="1a040-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1a040-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1a040-110">Compiling the Code</span></span>  
 <span data-ttu-id="1a040-111">Ujistěte se, že třídy nebo struktury, které používáte definuje operátor, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="1a040-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="1a040-112">Nepředpokládejte, že každý operátor, který je k dispozici pro přetížení definoval třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="1a040-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="1a040-113">Seznam dostupných operátorů najdete v tématu [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1a040-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="1a040-114">Zahrnout odpovídající `Imports` příkaz pro řetězec SQL na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="1a040-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="1a040-115">Váš projekt musí obsahovat odkazy na System.Data a System.XML.</span><span class="sxs-lookup"><span data-stu-id="1a040-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a040-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a040-116">See also</span></span>

- [<span data-ttu-id="1a040-117">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="1a040-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="1a040-118">Postupy: Definovat operátor</span><span class="sxs-lookup"><span data-stu-id="1a040-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="1a040-119">Postupy: Definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="1a040-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="1a040-120">Postupy: Volání procedury operátora</span><span class="sxs-lookup"><span data-stu-id="1a040-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="1a040-121">Widening</span><span class="sxs-lookup"><span data-stu-id="1a040-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="1a040-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="1a040-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="1a040-123">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="1a040-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="1a040-124">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="1a040-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="1a040-125">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="1a040-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="1a040-126">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="1a040-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
