---
title: 'Postupy: Použití třídy, která definuje operátory.'
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
ms.openlocfilehash: 9ec4b4c07910100dd02cc86e882b44aa7dbd2ced
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346041"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="a683b-102">Postupy: Použití třídy, která definuje operátory (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="a683b-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="a683b-103">Pokud používáte třídu nebo strukturu, která definuje své vlastní operátory, můžete k těmto operátorům přistupovat z Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a683b-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="a683b-104">Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.</span><span class="sxs-lookup"><span data-stu-id="a683b-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a683b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a683b-105">Example</span></span>  
 <span data-ttu-id="a683b-106">Následující příklad přistupuje k struktuře SQL <xref:System.Data.SqlTypes.SqlString>, která definuje operátory převodu ([funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md)) v obou směrech mezi řetězcem SQL a řetězcem Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a683b-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="a683b-107">Použijte `CType(`*řetězcového výrazu SQL*, `String)` pro převod řetězce sql na Visual Basic řetězec a `CType(`*Visual Basic řetězcového výrazu*, <xref:System.Data.SqlTypes.SqlString>`)` pro převod v druhém směru.</span><span class="sxs-lookup"><span data-stu-id="a683b-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="a683b-108">Struktura <xref:System.Data.SqlTypes.SqlString> definuje operátor převodu ([CType funkce](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` na <xref:System.Data.SqlTypes.SqlString> a další od <xref:System.Data.SqlTypes.SqlString> až po `String`.</span><span class="sxs-lookup"><span data-stu-id="a683b-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="a683b-109">Příkaz, který přiřazuje `title` pro `jobTitle` používá první operátor a volání funkce <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> používá sekundu.</span><span class="sxs-lookup"><span data-stu-id="a683b-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a683b-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a683b-110">Compiling the Code</span></span>  
 <span data-ttu-id="a683b-111">Ujistěte se, že třída nebo struktura, kterou používáte, definuje operátor, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="a683b-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="a683b-112">Nepředpokládají, že třída nebo struktura definovala každý operátor, který je k dispozici pro přetížení.</span><span class="sxs-lookup"><span data-stu-id="a683b-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="a683b-113">Seznam dostupných operátorů naleznete v tématu [příkaz operator](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="a683b-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="a683b-114">Zahrňte příslušný příkaz `Imports` pro řetězec SQL na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="a683b-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="a683b-115">Projekt musí mít odkazy na System. data a System. XML.</span><span class="sxs-lookup"><span data-stu-id="a683b-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a683b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a683b-116">See also</span></span>

- [<span data-ttu-id="a683b-117">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="a683b-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="a683b-118">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="a683b-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="a683b-119">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="a683b-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="a683b-120">Postupy: Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="a683b-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="a683b-121">Widening</span><span class="sxs-lookup"><span data-stu-id="a683b-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="a683b-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="a683b-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="a683b-123">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="a683b-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="a683b-124">Postupy: Definice struktury</span><span class="sxs-lookup"><span data-stu-id="a683b-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="a683b-125">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="a683b-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="a683b-126">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="a683b-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
