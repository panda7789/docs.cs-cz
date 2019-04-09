---
title: Procedury operátoru (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 80c9a77494be95365899c6a25435fcfc5d2a7293
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175016"
---
# <a name="operator-procedures-visual-basic"></a><span data-ttu-id="3e438-102">Procedury operátoru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3e438-102">Operator Procedures (Visual Basic)</span></span>
<span data-ttu-id="3e438-103">Procedury operátoru je řada příkazů jazyka Visual Basic, které definují chování standardní – operátor (například `*`, `<>`, nebo `And`) na třídy nebo struktury, které jste definovali.</span><span class="sxs-lookup"><span data-stu-id="3e438-103">An operator procedure is a series of Visual Basic statements that define the behavior of a standard operator (such as `*`, `<>`, or `And`) on a class or structure you have defined.</span></span> <span data-ttu-id="3e438-104">To se také nazývá *přetížení operátoru*.</span><span class="sxs-lookup"><span data-stu-id="3e438-104">This is also called *operator overloading*.</span></span>  
  
## <a name="when-to-define-operator-procedures"></a><span data-ttu-id="3e438-105">Při definování procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="3e438-105">When to Define Operator Procedures</span></span>  
 <span data-ttu-id="3e438-106">Po definování třídy nebo struktury můžete deklarovat proměnné typu této třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3e438-106">When you have defined a class or structure, you can declare variables to be of the type of that class or structure.</span></span> <span data-ttu-id="3e438-107">Tato proměnná je někdy potřeba zapojit do činnosti, jako součást výrazu.</span><span class="sxs-lookup"><span data-stu-id="3e438-107">Sometimes such a variable needs to participate in an operation as part of an expression.</span></span> <span data-ttu-id="3e438-108">Chcete-li to provést, musí být operand operátoru.</span><span class="sxs-lookup"><span data-stu-id="3e438-108">To do this, it must be an operand of an operator.</span></span>  
  
 <span data-ttu-id="3e438-109">Visual Basic definuje operátory pouze na jeho základní datové typy.</span><span class="sxs-lookup"><span data-stu-id="3e438-109">Visual Basic defines operators only on its fundamental data types.</span></span> <span data-ttu-id="3e438-110">Můžete definovat chování operátoru, pokud jeden nebo oba operandy jsou typu třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3e438-110">You can define the behavior of an operator when one or both of the operands are of the type of your class or structure.</span></span>  
  
 <span data-ttu-id="3e438-111">Další informace najdete v tématu [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3e438-111">For more information, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="types-of-operator-procedure"></a><span data-ttu-id="3e438-112">Typy procedury operátora</span><span class="sxs-lookup"><span data-stu-id="3e438-112">Types of Operator Procedure</span></span>  
 <span data-ttu-id="3e438-113">Procedury operátoru může být jedna z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="3e438-113">An operator procedure can be one of the following types:</span></span>  
  
-   <span data-ttu-id="3e438-114">Definice unárního operátoru, kde se argument typu třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3e438-114">A definition of a unary operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="3e438-115">Definice binárního operátoru, kde je alespoň jeden z argumentů typu třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3e438-115">A definition of a binary operator where at least one of the arguments is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="3e438-116">Definice operátoru převodu, kde se argument typu třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3e438-116">A definition of a conversion operator where the argument is of the type of your class or structure.</span></span>  
  
-   <span data-ttu-id="3e438-117">Definice operátora převodu, který vrátí typ třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3e438-117">A definition of a conversion operator that returns the type of your class or structure.</span></span>  
  
 <span data-ttu-id="3e438-118">Operátory převodu jsou vždy Unární a vždy použijte `CType` jako operátor, definujete.</span><span class="sxs-lookup"><span data-stu-id="3e438-118">Conversion operators are always unary, and you always use `CType` as the operator you are defining.</span></span>  
  
## <a name="declaration-syntax"></a><span data-ttu-id="3e438-119">Syntaxe deklarace</span><span class="sxs-lookup"><span data-stu-id="3e438-119">Declaration Syntax</span></span>  
 <span data-ttu-id="3e438-120">Syntaxe pro deklaraci procedury operátora vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="3e438-120">The syntax for declaring an operator procedure is as follows:</span></span>  
  
 `Public Shared`   `[Widening | Narrowing]`   `Operator`  <span data-ttu-id="3e438-121">*operatorsymbol* `(` *operand1*`[,`*operand2* `]) As` *datový typ* </span><span class="sxs-lookup"><span data-stu-id="3e438-121">*operatorsymbol*  `(` *operand1*  `[,`  *operand2* `]) As`  *datatype*</span></span>  
  
 `' Statements of the operator procedure.`  
  
 `End Operator`  
  
 <span data-ttu-id="3e438-122">Můžete použít `Widening` nebo `Narrowing` – klíčové slovo pouze v typu operátoru převodu.</span><span class="sxs-lookup"><span data-stu-id="3e438-122">You use the `Widening` or `Narrowing` keyword only on a type conversion operator.</span></span> <span data-ttu-id="3e438-123">Symbol operátoru je vždy [funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md) pro operátor převodu typu.</span><span class="sxs-lookup"><span data-stu-id="3e438-123">The operator symbol is always [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) for a type conversion operator.</span></span>  
  
 <span data-ttu-id="3e438-124">Deklarace dvou operandů k definování binárním operátorem a deklarujte jeden operand unárního operátoru, včetně typu operátoru převodu definovat.</span><span class="sxs-lookup"><span data-stu-id="3e438-124">You declare two operands to define a binary operator, and you declare one operand to define a unary operator, including a type conversion operator.</span></span> <span data-ttu-id="3e438-125">Všechny operandy musí být deklarován `ByVal`.</span><span class="sxs-lookup"><span data-stu-id="3e438-125">All operands must be declared `ByVal`.</span></span>  
  
 <span data-ttu-id="3e438-126">Stejným způsobem jako deklarovat parametry pro deklaraci operandem [Sub – procedury](./sub-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="3e438-126">You declare each operand the same way you declare parameters for [Sub Procedures](./sub-procedures.md).</span></span>  
  
### <a name="data-type"></a><span data-ttu-id="3e438-127">Datový typ</span><span class="sxs-lookup"><span data-stu-id="3e438-127">Data Type</span></span>  
 <span data-ttu-id="3e438-128">Vzhledem k tomu, že definujete operátor v třídě nebo struktuře, které jste definovali, nejméně jeden z operandů musí být datový typ této třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="3e438-128">Because you are defining an operator on a class or structure you have defined, at least one of the operands must be of the data type of that class or structure.</span></span> <span data-ttu-id="3e438-129">Pro operátor převodu typu operandu nebo návratový typ musí být datového typu třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="3e438-129">For a type conversion operator, either the operand or the return type must be of the data type of the class or structure.</span></span>  
  
 <span data-ttu-id="3e438-130">Další podrobnosti najdete v tématu [Operator – příkaz](../../../../visual-basic/language-reference/statements/operator-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3e438-130">For more details, see [Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md).</span></span>  
  
## <a name="calling-syntax"></a><span data-ttu-id="3e438-131">Syntaxe volání</span><span class="sxs-lookup"><span data-stu-id="3e438-131">Calling Syntax</span></span>  
 <span data-ttu-id="3e438-132">Vyvolání procedury operátora implicitně pomocí symbol operátoru ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="3e438-132">You invoke an operator procedure implicitly by using the operator symbol in an expression.</span></span> <span data-ttu-id="3e438-133">Zadáte operandy stejným způsobem jako pro předdefinované operátory.</span><span class="sxs-lookup"><span data-stu-id="3e438-133">You supply the operands the same way you do for predefined operators.</span></span>  
  
 <span data-ttu-id="3e438-134">Syntaxe pro implicitním voláním procedury operátora vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="3e438-134">The syntax for an implicit call to an operator procedure is as follows:</span></span>  
  
 `Dim testStruct As`  *<span data-ttu-id="3e438-135">%{structurename/</span><span class="sxs-lookup"><span data-stu-id="3e438-135">structurename</span></span>*  
  
 `Dim testNewStruct As`  <span data-ttu-id="3e438-136">*%{structurename/*`= testStruct`*operatorsymbol* </span><span class="sxs-lookup"><span data-stu-id="3e438-136">*structurename*  `= testStruct`  *operatorsymbol*</span></span>  `10`  
  
### <a name="illustration-of-declaration-and-call"></a><span data-ttu-id="3e438-137">Obrázek deklarace a volání</span><span class="sxs-lookup"><span data-stu-id="3e438-137">Illustration of Declaration and Call</span></span>  
 <span data-ttu-id="3e438-138">Následující strukturu uloží hodnotu se znaménkem 128-bit jako základní části nejvyšším a nižšího řádu.</span><span class="sxs-lookup"><span data-stu-id="3e438-138">The following structure stores a signed 128-bit integer value as the constituent high-order and low-order parts.</span></span> <span data-ttu-id="3e438-139">Definuje `+` operátor přidejte dva `veryLong` hodnoty a generovat výsledném `veryLong` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3e438-139">It defines the `+` operator to add two `veryLong` values and generate a resulting `veryLong` value.</span></span>  
  
 [!code-vb[VbVbcnProcedures#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#23)]  
  
 <span data-ttu-id="3e438-140">Následující příklad ukazuje typické volání `+` operátor definován na `veryLong`.</span><span class="sxs-lookup"><span data-stu-id="3e438-140">The following example shows a typical call to the `+` operator defined on `veryLong`.</span></span>  
  
 [!code-vb[VbVbcnProcedures#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#24)]  

## <a name="see-also"></a><span data-ttu-id="3e438-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e438-141">See also</span></span>

- [<span data-ttu-id="3e438-142">Procedury</span><span class="sxs-lookup"><span data-stu-id="3e438-142">Procedures</span></span>](./index.md)
- [<span data-ttu-id="3e438-143">Procedury Sub</span><span class="sxs-lookup"><span data-stu-id="3e438-143">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="3e438-144">Procedury Function</span><span class="sxs-lookup"><span data-stu-id="3e438-144">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="3e438-145">Procedury Property</span><span class="sxs-lookup"><span data-stu-id="3e438-145">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="3e438-146">Parametry a argumenty procedury</span><span class="sxs-lookup"><span data-stu-id="3e438-146">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="3e438-147">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="3e438-147">Operator Statement</span></span>](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [<span data-ttu-id="3e438-148">Postupy: Definování operátoru</span><span class="sxs-lookup"><span data-stu-id="3e438-148">How to: Define an Operator</span></span>](./how-to-define-an-operator.md)
- [<span data-ttu-id="3e438-149">Postupy: Definování operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="3e438-149">How to: Define a Conversion Operator</span></span>](./how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="3e438-150">Postupy: Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="3e438-150">How to: Call an Operator Procedure</span></span>](./how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="3e438-151">Postupy: Použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="3e438-151">How to: Use a Class that Defines Operators</span></span>](./how-to-use-a-class-that-defines-operators.md)
