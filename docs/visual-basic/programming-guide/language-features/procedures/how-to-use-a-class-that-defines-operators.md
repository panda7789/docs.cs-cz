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
ms.openlocfilehash: fe15e976e6a5469f2a9d1b3521a70a3e1860fdd3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414347"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a><span data-ttu-id="efc55-102">Postupy: Použití třídy, která definuje operátory (Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="efc55-102">How to: Use a Class that Defines Operators (Visual Basic)</span></span>
<span data-ttu-id="efc55-103">Pokud používáte třídu nebo strukturu, která definuje své vlastní operátory, můžete k těmto operátorům přistupovat z Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="efc55-103">If you are using a class or structure that defines its own operators, you can access those operators from Visual Basic.</span></span>  
  
 <span data-ttu-id="efc55-104">Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.</span><span class="sxs-lookup"><span data-stu-id="efc55-104">Defining an operator on a class or structure is also called *overloading* the operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="efc55-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="efc55-105">Example</span></span>  
 <span data-ttu-id="efc55-106">Následující příklad přistupuje ke struktuře SQL <xref:System.Data.SqlTypes.SqlString> , která definuje operátory převodu ([funkce CType](../../../language-reference/functions/ctype-function.md)) v obou směrech mezi řetězcem SQL a řetězcem Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="efc55-106">The following example accesses the SQL structure <xref:System.Data.SqlTypes.SqlString>, which defines the conversion operators ([CType Function](../../../language-reference/functions/ctype-function.md)) in both directions between a SQL string and a Visual Basic string.</span></span> <span data-ttu-id="efc55-107">Použijte `CType(` *řetězcový výraz SQL* `String)` pro převod řetězce SQL na řetězec Visual Basic a řetězcový `CType(` *výraz Visual Basic* <xref:System.Data.SqlTypes.SqlString> `)` pro převod v druhém směru.</span><span class="sxs-lookup"><span data-stu-id="efc55-107">Use `CType(`*SQL string expression*, `String)` to convert a SQL string to a Visual Basic string, and `CType(`*Visual Basic string expression*, <xref:System.Data.SqlTypes.SqlString>`)` to convert in the other direction.</span></span>  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <span data-ttu-id="efc55-108"><xref:System.Data.SqlTypes.SqlString>Struktura definuje operátor převodu ([funkce CType](../../../language-reference/functions/ctype-function.md)) z `String` na <xref:System.Data.SqlTypes.SqlString> a druhý z <xref:System.Data.SqlTypes.SqlString> na `String` .</span><span class="sxs-lookup"><span data-stu-id="efc55-108">The <xref:System.Data.SqlTypes.SqlString> structure defines a conversion operator ([CType Function](../../../language-reference/functions/ctype-function.md)) from `String` to <xref:System.Data.SqlTypes.SqlString> and another from <xref:System.Data.SqlTypes.SqlString> to `String`.</span></span> <span data-ttu-id="efc55-109">Příkaz, který přiřadí `title` k `jobTitle` použití prvního operátoru a <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> volání funkce používá sekundu.</span><span class="sxs-lookup"><span data-stu-id="efc55-109">The statement that assigns `title` to `jobTitle` makes use of the first operator, and the <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A> function call uses the second.</span></span>  
  
## <a name="compile-the-code"></a><span data-ttu-id="efc55-110">Kompilovat kód</span><span class="sxs-lookup"><span data-stu-id="efc55-110">Compile the code</span></span>  
 <span data-ttu-id="efc55-111">Ujistěte se, že třída nebo struktura, kterou používáte, definuje operátor, který chcete použít.</span><span class="sxs-lookup"><span data-stu-id="efc55-111">Be sure the class or structure you are using defines the operator you want to use.</span></span> <span data-ttu-id="efc55-112">Nepředpokládají, že třída nebo struktura definovala každý operátor, který je k dispozici pro přetížení.</span><span class="sxs-lookup"><span data-stu-id="efc55-112">Do not assume that the class or structure has defined every operator available for overloading.</span></span> <span data-ttu-id="efc55-113">Seznam dostupných operátorů naleznete v tématu [příkaz operator](../../../language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="efc55-113">For a list of available operators, see [Operator Statement](../../../language-reference/statements/operator-statement.md).</span></span>  
  
 <span data-ttu-id="efc55-114">Zahrňte příslušný `Imports` příkaz pro řetězec SQL na začátku zdrojového souboru (v tomto případě <xref:System.Data.SqlTypes> ).</span><span class="sxs-lookup"><span data-stu-id="efc55-114">Include the appropriate `Imports` statement for the SQL string at the beginning of your source file (in this case <xref:System.Data.SqlTypes>).</span></span>  
  
 <span data-ttu-id="efc55-115">Projekt musí mít odkazy na System. data a System. XML.</span><span class="sxs-lookup"><span data-stu-id="efc55-115">Your project must have references to System.Data and System.XML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efc55-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="efc55-116">See also</span></span>

- [<span data-ttu-id="efc55-117">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="efc55-117">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="efc55-118">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="efc55-118">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="efc55-119">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="efc55-119">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="efc55-120">Postupy: Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="efc55-120">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="efc55-121">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="efc55-121">Widening</span></span>](../../../language-reference/modifiers/widening.md)
- [<span data-ttu-id="efc55-122">Narrowing</span><span class="sxs-lookup"><span data-stu-id="efc55-122">Narrowing</span></span>](../../../language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="efc55-123">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="efc55-123">Structure Statement</span></span>](../../../language-reference/statements/structure-statement.md)
- [<span data-ttu-id="efc55-124">Postupy: Deklarace struktury</span><span class="sxs-lookup"><span data-stu-id="efc55-124">How to: Declare a Structure</span></span>](../data-types/how-to-declare-a-structure.md)
- [<span data-ttu-id="efc55-125">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="efc55-125">Implicit and Explicit Conversions</span></span>](../data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="efc55-126">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="efc55-126">Widening and Narrowing Conversions</span></span>](../data-types/widening-and-narrowing-conversions.md)
