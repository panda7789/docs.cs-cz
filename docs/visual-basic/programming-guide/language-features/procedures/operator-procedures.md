---
title: "Procedury operátoru (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Visual Basic code, procedures
- procedures [Visual Basic], operator
- Visual Basic code, operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
ms.assetid: 8c513d38-246b-4fb7-8b75-29e1364e555b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 865695731dd591b0c48f4416814fa97edf4ea42e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="5e79b-102">Procedury operátoru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5e79b-102">Operator Procedures (Visual Basic)</span></span>
<span data-ttu-id="5e79b-103">Procedury operátora je řada [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] příkazy, které definují chování standardní operátoru (například `*`, `<>`, nebo `And`) na třídu nebo strukturu jste definovali.</span><span class="sxs-lookup"><span data-stu-id="5e79b-103">An operator procedure is a series of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="5e79b-104">To se označuje taky jako *přetížení operátoru*.</span><span class="sxs-lookup"><span data-stu-id="5e79b-104">This is also called *operator overloading*.</span></span>  
  
## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="5e79b-105">Při definování procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="5e79b-105">When to Define Operator Procedures</span></span>  
 <span data-ttu-id="5e79b-106">Pokud jste definovali třídu nebo strukturu, můžou deklarovat proměnné, které chcete být typu třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="5e79b-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="5e79b-107">V některých případech musí tuto proměnnou součástí operace v rámci výrazu.</span><span class="sxs-lookup"><span data-stu-id="5e79b-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="5e79b-108">Chcete-li to provést, musí být operand operátoru.</span><span class="sxs-lookup"><span data-stu-id="5e79b-108">To do this, it must be an operand of an operator.</span></span>  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="5e79b-109">Definuje operátory jenom na jeho základní datové typy.</span><span class="sxs-lookup"><span data-stu-id="5e79b-109"> defines operators only on its fundamental data types.</span></span> <span data-ttu-id="5e79b-110">Můžete definovat chování operátor Pokud jeden nebo oba operandy jsou typu třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="5e79b-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="5e79b-111">Další informace najdete v tématu [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5e79b-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="types-of-operator-procedure"></a><span data-ttu-id="5e79b-112">Typy procedury operátora</span><span class="sxs-lookup"><span data-stu-id="5e79b-112">Types of Operator Procedure</span></span>  
 <span data-ttu-id="5e79b-113">Procedury operátora může být jedna z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="5e79b-113">An operator procedure can be one of the following types:</span></span>  
  
-   <span data-ttu-id="5e79b-114">Definice unární operátor kde argument je typu třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="5e79b-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="5e79b-115">Definice binární operátor kde alespoň jeden z argumentů je typu třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="5e79b-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="5e79b-116">Definice operátora převodu kde argument je typu třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="5e79b-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="5e79b-117">Definice operátora převodu, který vrátí typ třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="5e79b-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>  
  
 <span data-ttu-id="5e79b-118">Operátory převodu jsou vždy Unární a vždy používat `CType` jako operátor definujete.</span><span class="sxs-lookup"><span data-stu-id="5e79b-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="5e79b-119">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="5e79b-119">Declaration Syntax</span></span>  
 <span data-ttu-id="5e79b-120">Syntaxe deklarace procedury operátora vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="5e79b-120">The syntax for declaring an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="5e79b-121">`Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol* `(` *operand1*`[,`*operand2* `]) As` *datový typ* </span><span class="sxs-lookup"><span data-stu-id="5e79b-121">`Public Shared`   `[Widening | Narrowing]`   `Operator`  *operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span></span>  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 <span data-ttu-id="5e79b-122">Můžete použít `Widening` nebo `Narrowing` – klíčové slovo pouze na operátor převodu typu.</span><span class="sxs-lookup"><span data-stu-id="5e79b-122">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="5e79b-123">Symbol operátoru je vždy [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md) pro operátor převodu typu.</span><span class="sxs-lookup"><span data-stu-id="5e79b-123">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>  
  
 <span data-ttu-id="5e79b-124">Deklarování dva operandy k definování binární operátor a deklarovat jeden operand k definování unární operátor, včetně operátor převodu typu.</span><span class="sxs-lookup"><span data-stu-id="5e79b-124">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="5e79b-125">Je nutné deklarovat všechny operandy `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="5e79b-125">All operands must be declared `ByVal`.</span></span>  
  
 <span data-ttu-id="5e79b-126">Deklarovat stejným způsobem jako deklarovat parametry pro každý operand [Sub – procedury](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5e79b-126">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="5e79b-127">Datový typ</span><span class="sxs-lookup"><span data-stu-id="5e79b-127">Data Type</span></span>  
 <span data-ttu-id="5e79b-128">Vzhledem k tomu, že definujete operátor na třídu nebo strukturu, které jste definovali, alespoň jeden z operandy musí být data typu třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="5e79b-128">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="5e79b-129">Pro operátor převodu typu musí být buď operand nebo návratový typ datového typu třídy nebo struktura.</span><span class="sxs-lookup"><span data-stu-id="5e79b-129">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>  
  
 <span data-ttu-id="5e79b-130">Další podrobnosti najdete v tématu [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5e79b-130">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="5e79b-131">Syntaxe volání</span><span class="sxs-lookup"><span data-stu-id="5e79b-131">Calling Syntax</span></span>  
 <span data-ttu-id="5e79b-132">Vyvolání procedury operátora implicitně pomocí symbol operátoru ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="5e79b-132">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="5e79b-133">Můžete zadat operandy stejným způsobem můžete udělat pro předdefinované operátory.</span><span class="sxs-lookup"><span data-stu-id="5e79b-133">You supply the operands the same way you do for predefined operators.</span></span>  
  
 <span data-ttu-id="5e79b-134">Syntaxe implicitní volání procedury operátora vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="5e79b-134">The syntax for an implicit call to an operator procedure is as follows:</span></span>  
  
 <span data-ttu-id="5e79b-135">`Dim testStruct As`  *%{structurename/*</span><span class="sxs-lookup"><span data-stu-id="5e79b-135">`Dim testStruct As`  *structurename*</span></span>  
  
 <span data-ttu-id="5e79b-136">`Dim testNewStruct As`  *%{structurename/*`= testStruct`*operatorsymbol*   `10`</span><span class="sxs-lookup"><span data-stu-id="5e79b-136">`Dim testNewStruct As`  *structurename*  `= testStruct`  *operatorsymbol*  `10`</span></span>  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="5e79b-137">Obrázek deklarace a volání</span><span class="sxs-lookup"><span data-stu-id="5e79b-137">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="5e79b-138">Následující strukturu ukládá hodnotu číslo se znaménkem 128-bit jako základních horní a nejnižší částí.</span><span class="sxs-lookup"><span data-stu-id="5e79b-138">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="5e79b-139">Definuje, `+` operátor přidat dva `veryLong` hodnoty a generovat výsledném `veryLong` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5e79b-139">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>  
  
 [!code-vb[VbVbcnProcedures#23](./codesnippet/VisualBasic/operator-procedures_1.vb)]  
  
 <span data-ttu-id="5e79b-140">Následující příklad ukazuje typické volání `+` operátor definované na `veryLong`.</span><span class="sxs-lookup"><span data-stu-id="5e79b-140">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#24](./codesnippet/VisualBasic/operator-procedures_2.vb)]  
  
 <span data-ttu-id="5e79b-141">Další informace a příklady naleznete v tématu [operátor přetížení Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span><span class="sxs-lookup"><span data-stu-id="5e79b-141">For more information and examples, see [Operator Overloading in Visual Basic 2005](http://go.microsoft.com/fwlink/?LinkId=101703).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e79b-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e79b-142">See Also</span></span>  
 [<span data-ttu-id="5e79b-143">Postupy</span><span class="sxs-lookup"><span data-stu-id="5e79b-143">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="5e79b-144">Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="5e79b-144">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="5e79b-145">Function – procedury</span><span class="sxs-lookup"><span data-stu-id="5e79b-145">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="5e79b-146">Procedury vlastností</span><span class="sxs-lookup"><span data-stu-id="5e79b-146">Property Procedures</span></span>](./property-procedures.md)  
 [<span data-ttu-id="5e79b-147">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="5e79b-147">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)  
 [<span data-ttu-id="5e79b-148">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="5e79b-148">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [<span data-ttu-id="5e79b-149">Postupy: definice operátora</span><span class="sxs-lookup"><span data-stu-id="5e79b-149">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)  
 [<span data-ttu-id="5e79b-150">Postupy: definice operátora převodu</span><span class="sxs-lookup"><span data-stu-id="5e79b-150">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)  
 [<span data-ttu-id="5e79b-151">Postupy: volání procedury operátora</span><span class="sxs-lookup"><span data-stu-id="5e79b-151">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)  
 [<span data-ttu-id="5e79b-152">Postupy: použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="5e79b-152">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
