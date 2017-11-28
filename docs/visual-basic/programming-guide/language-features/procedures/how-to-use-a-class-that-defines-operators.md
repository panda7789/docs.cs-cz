---
title: "Postupy: Použití třídy, která definuje operátory (Visual Basic)."
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 223b3fc84fe75d1d530cd182c9332e5c663aa519
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="1a660-102">Postupy: Použití třídy, která definuje operátory (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="1a660-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="1a660-103">Pokud používáte třídu nebo strukturu, která definuje vlastní operátory, dostanete tyto operátory z [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1a660-103">If you are using a class or structure that defines its own operators, you can access those operators from [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
 <span data-ttu-id="1a660-104">Definování operátor na třídu nebo strukturu je také označován *přetížení* operátor.</span><span class="sxs-lookup"><span data-stu-id="1a660-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a660-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a660-105">Example</span></span>  
 <span data-ttu-id="1a660-106">Následující příklad používá strukturu SQL <xref:System.Data.SqlTypes.SqlString>, která definuje operátory převodu ([CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md)) v obou směrech mezi řetězec SQL a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] řetězec.</span><span class="sxs-lookup"><span data-stu-id="1a660-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) in both directions between a SQL string and a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string.</span></span> <span data-ttu-id="1a660-107">Použití `CType(` *SQL řetězcového výrazu*, `String)` převést řetězec SQL tak, aby [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] řetězci a `CType(` *řetězcového výrazu jazyka Visual Basic*, <xref:System.Data.SqlTypes.SqlString> `)` převést opačným směrem.</span><span class="sxs-lookup"><span data-stu-id="1a660-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_1.vb)]  
  
 [!code-vb[VbVbcnProcedures#31](./codesnippet/VisualBasic/how-to-use-a-class-that-defines-operators_2.vb)]  
  
 <span data-ttu-id="1a660-108"><xref:System.Data.SqlTypes.SqlString> Struktura definuje operátora převodu ([CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md)) z `String` k <xref:System.Data.SqlTypes.SqlString> a jiné z <xref:System.Data.SqlTypes.SqlString> k `String`.</span><span class="sxs-lookup"><span data-stu-id="1a660-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="1a660-109">Příkaz, který přiřazuje `title` k `jobTitle` využívá první operátor a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> volání funkce používá druhý.</span><span class="sxs-lookup"><span data-stu-id="1a660-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1a660-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1a660-110">Compiling the Code</span></span>  
 <span data-ttu-id="1a660-111">Ujistěte se, že třídu nebo strukturu, který používáte definuje operátor, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="1a660-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="1a660-112">Nepředpokládejte, že třídu nebo strukturu definovala každých operátor, který je k dispozici pro přetížení.</span><span class="sxs-lookup"><span data-stu-id="1a660-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="1a660-113">Seznam dostupných operátory najdete v tématu [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1a660-113">For a list of available operators, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="1a660-114">Zahrnout odpovídající `Imports` příkaz SQL řetězce na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlTypes>).</span><span class="sxs-lookup"><span data-stu-id="1a660-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="1a660-115">Projekt musí mít odkazy na System.Data a System.XML.</span><span class="sxs-lookup"><span data-stu-id="1a660-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a660-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a660-116">See Also</span></span>  
 [<span data-ttu-id="1a660-117">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="1a660-117">Operator Procedures</span></span>](./operator-procedures.md)  
 [<span data-ttu-id="1a660-118">Postupy: definice operátora</span><span class="sxs-lookup"><span data-stu-id="1a660-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="1a660-119">Postupy: definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="1a660-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="1a660-120">Postupy: volání procedury operátora</span><span class="sxs-lookup"><span data-stu-id="1a660-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="1a660-121">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="1a660-121">Widening</span></span>](../../../../visual-basic/language-reference/modifiers/widening.md)  
 [<span data-ttu-id="1a660-122">Zužující</span><span class="sxs-lookup"><span data-stu-id="1a660-122">Narrowing</span></span>](../../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [<span data-ttu-id="1a660-123">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="1a660-123">Structure Statement</span></span>](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="1a660-124">Postupy: definice struktury</span><span class="sxs-lookup"><span data-stu-id="1a660-124">How to: Declare a Structure</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [<span data-ttu-id="1a660-125">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="1a660-125">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="1a660-126">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="1a660-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
