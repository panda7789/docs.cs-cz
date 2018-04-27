---
title: 'Postupy: Použití třídy, která definuje operátory (Visual Basic).'
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
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7e0bcfaeca638dfabb841a9e935b872f76fdf957
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="ef9bc-102">Postupy: Použití třídy, která definuje operátory (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="ef9bc-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="ef9bc-103">Pokud používáte třídu nebo strukturu, která definuje vlastní operátory, můžete tyto operátory přistupovat z jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ef9bc-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="ef9bc-104">Definování operátor na třídu nebo strukturu je také označován *přetížení* operátor.</span><span class="sxs-lookup"><span data-stu-id="ef9bc-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef9bc-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ef9bc-105">Example</span></span>  
 <span data-ttu-id="ef9bc-106">Následující příklad používá strukturu SQL <xref:System.Data.SqlTypes.SqlString>, která definuje operátory převodu ([CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md)) v obou směrech mezi řetězec jazyka Visual Basic a řetězec SQL.</span><span class="sxs-lookup"><span data-stu-id="ef9bc-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="ef9bc-107">Použití `CType(` *SQL řetězcového výrazu*, `String)` převést řetězec SQL na řetězec jazyka Visual Basic a `CType(` *řetězcového výrazu jazyka Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` převést opačným směrem.</span><span class="sxs-lookup"><span data-stu-id="ef9bc-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <span data-ttu-id="ef9bc-108"><xref:System.Data.SqlTypes.SqlString> Struktura definuje operátora převodu ([CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` k <xref:System.Data.SqlTypes.SqlString> a jiné z <xref:System.Data.SqlTypes.SqlString> k `String`.</span><span class="sxs-lookup"><span data-stu-id="ef9bc-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="ef9bc-109">Příkaz, který přiřazuje `title` k `jobTitle` využívá první operátor a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> volání funkce používá druhý.</span><span class="sxs-lookup"><span data-stu-id="ef9bc-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ef9bc-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ef9bc-110">Compiling the Code</span></span>  
 <span data-ttu-id="ef9bc-111">Ujistěte se, že třídu nebo strukturu, který používáte definuje operátor, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="ef9bc-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="ef9bc-112">Nepředpokládejte, že třídu nebo strukturu definovala každých operátor, který je k dispozici pro přetížení.</span><span class="sxs-lookup"><span data-stu-id="ef9bc-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="ef9bc-113">Seznam dostupných operátory najdete v tématu [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ef9bc-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="ef9bc-114">Zahrnout odpovídající `Imports` příkaz SQL řetězce na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="ef9bc-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="ef9bc-115">Projekt musí mít odkazy na System.Data a System.XML.</span><span class="sxs-lookup"><span data-stu-id="ef9bc-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef9bc-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef9bc-116">See Also</span></span>  
 [<span data-ttu-id="ef9bc-117">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="ef9bc-117">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="ef9bc-118">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="ef9bc-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="ef9bc-119">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="ef9bc-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="ef9bc-120">Postupy: Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="ef9bc-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="ef9bc-121">Widening</span><span class="sxs-lookup"><span data-stu-id="ef9bc-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="ef9bc-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="ef9bc-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="ef9bc-123">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="ef9bc-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="ef9bc-124">Postupy: Definice struktury</span><span class="sxs-lookup"><span data-stu-id="ef9bc-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="ef9bc-125">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="ef9bc-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="ef9bc-126">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="ef9bc-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
