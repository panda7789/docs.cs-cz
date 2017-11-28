---
title: "Postupy: Definování parametru pro proceduru (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c909cfe1b45a42aae91948917f310474575f225
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a><span data-ttu-id="f313c-102">Postupy: Definování parametru pro proceduru (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f313c-102">How to: Define a Parameter for a Procedure (Visual Basic)</span></span>
<span data-ttu-id="f313c-103">A *parametr* umožňuje volací kód, který předat hodnotu k postupu při jeho volání.</span><span class="sxs-lookup"><span data-stu-id="f313c-103">A *parameter* allows the calling code to pass a value to the procedure when it calls it.</span></span> <span data-ttu-id="f313c-104">Každý parametr pro proceduru deklarovat stejným způsobem jako deklarovat proměnnou, zadat jeho název a datový typ.</span><span class="sxs-lookup"><span data-stu-id="f313c-104">You declare each parameter for a procedure the same way you declare a variable, specifying its name and data type.</span></span> <span data-ttu-id="f313c-105">Můžete také zadat mechanismus předávání, a zda se jedná o volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="f313c-105">You also specify the passing mechanism, and whether the parameter is optional.</span></span>  
  
 <span data-ttu-id="f313c-106">Další informace najdete v tématu [parametry a argumenty procedury](./procedure-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="f313c-106">For more information, see [Procedure Parameters and Arguments](./procedure-parameters-and-arguments.md).</span></span>  
  
### <a name="to-define-a-procedure-parameter"></a><span data-ttu-id="f313c-107">Chcete-li definovat parametru procedury</span><span class="sxs-lookup"><span data-stu-id="f313c-107">To define a procedure parameter</span></span>  
  
1.  <span data-ttu-id="f313c-108">V deklaraci postup přidejte název parametru do seznamu parametrů postupu, oddělení z dalších parametrů čárkami.</span><span class="sxs-lookup"><span data-stu-id="f313c-108">In the procedure declaration, add the parameter name to the procedure's parameter list, separating it from other parameters by commas.</span></span>  
  
2.  <span data-ttu-id="f313c-109">Rozhodněte, datový typ parametru.</span><span class="sxs-lookup"><span data-stu-id="f313c-109">Decide the data type of the parameter.</span></span>  
  
3.  <span data-ttu-id="f313c-110">Postupujte podle názvu parametru s `As` klauzule k určení datového typu.</span><span class="sxs-lookup"><span data-stu-id="f313c-110">Follow the parameter name with an `As` clause to specify the data type.</span></span>  
  
4.  <span data-ttu-id="f313c-111">Rozhodněte, které chcete pro parametr mechanismus předávání.</span><span class="sxs-lookup"><span data-stu-id="f313c-111">Decide the passing mechanism you want for the parameter.</span></span> <span data-ttu-id="f313c-112">Za normálních okolností předání parametru podle hodnoty, pokud chcete, aby postup nebudete moct změnit jeho hodnota v volání kódu.</span><span class="sxs-lookup"><span data-stu-id="f313c-112">Normally you pass a parameter by value, unless you want the procedure to be able to change its value in the calling code.</span></span>  
  
5.  <span data-ttu-id="f313c-113">Zadejte před název parametru [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) k určení mechanismus předávání.</span><span class="sxs-lookup"><span data-stu-id="f313c-113">Precede the parameter name with [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) or [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) to specify the passing mechanism.</span></span> <span data-ttu-id="f313c-114">Další informace najdete v tématu [rozdíly mezi předáním argumentu podle hodnoty a podle Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="f313c-114">For more information, see [Differences Between Passing an Argument By Value and By Reference](./differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
6.  <span data-ttu-id="f313c-115">Pokud se jedná o volitelný parametr, předcházet mechanismus předávání s [volitelné](../../../../visual-basic/language-reference/modifiers/optional.md) a postupujte podle pokynů datový typ parametru symbol rovná se (`=`) a výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f313c-115">If the parameter is optional, precede the passing mechanism with [Optional](../../../../visual-basic/language-reference/modifiers/optional.md) and follow the parameter data type with an equal sign (`=`) and a default value.</span></span>  
  
     <span data-ttu-id="f313c-116">V následujícím příkladu definuje obrys `Sub` postupu se třemi parametry.</span><span class="sxs-lookup"><span data-stu-id="f313c-116">The following example defines the outline of a `Sub` procedure with three parameters.</span></span> <span data-ttu-id="f313c-117">První dvě jsou povinné a třetí je volitelné.</span><span class="sxs-lookup"><span data-stu-id="f313c-117">The first two are required and the third is optional.</span></span> <span data-ttu-id="f313c-118">Deklarace parametru se v seznamu parametrů oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="f313c-118">The parameter declarations are separated in the parameter list by commas.</span></span>  
  
     [!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     <span data-ttu-id="f313c-119">První parametr přijme `customer` objekt, a `updateCustomer` můžete přímo aktualizovat proměnnou předaný `c` protože argument předaný [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span><span class="sxs-lookup"><span data-stu-id="f313c-119">The first parameter accepts a `customer` object, and `updateCustomer` can directly update the variable passed to `c` because the argument is passed [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md).</span></span> <span data-ttu-id="f313c-120">Postup nejde změnit hodnoty poslední dva argumenty, protože jsou předávány [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="f313c-120">The procedure cannot change the values of the last two arguments because they are passed [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).</span></span>  
  
     <span data-ttu-id="f313c-121">Pokud kód volání neposkytuje hodnotu `level` parametr [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nastaví na výchozí hodnotu 0.</span><span class="sxs-lookup"><span data-stu-id="f313c-121">If the calling code does not supply a value for the `level` parameter, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] sets it to the default value of 0.</span></span>  
  
     <span data-ttu-id="f313c-122">Pokud kontrola typu přepínače ([Option Strict – příkaz](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) je `Off`, `As` klauzule je volitelný, když definujete parametr.</span><span class="sxs-lookup"><span data-stu-id="f313c-122">If the type checking switch ([Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) is `Off`, the `As` clause is optional when you define a parameter.</span></span> <span data-ttu-id="f313c-123">Ale pokud žádné jeden parametr se používá `As` klauzule, všechny z nich musí používat ho.</span><span class="sxs-lookup"><span data-stu-id="f313c-123">However, if any one parameter uses an `As` clause, all of them must use it.</span></span> <span data-ttu-id="f313c-124">Pokud je typ kontroly přepínač `On`, `As` je vyžadována pro každý parametr definice klauzule.</span><span class="sxs-lookup"><span data-stu-id="f313c-124">If the type checking switch is `On`, the `As` clause is required for every parameter definition.</span></span>  
  
     <span data-ttu-id="f313c-125">Určení typů dat pro všechny programovací elementy se označuje jako *silného typování*.</span><span class="sxs-lookup"><span data-stu-id="f313c-125">Specifying data types for all your programming elements is known as *strong typing*.</span></span> <span data-ttu-id="f313c-126">Když nastavíte `Option Strict On`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vynucuje silného typování.</span><span class="sxs-lookup"><span data-stu-id="f313c-126">When you set `Option Strict On`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] enforces strong typing.</span></span> <span data-ttu-id="f313c-127">Toto nastavení se důrazně doporučuje, z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="f313c-127">This is strongly recommended, for the following reasons:</span></span>  
  
    -   <span data-ttu-id="f313c-128">Umožňuje podporu technologie IntelliSense pro proměnné a parametry.</span><span class="sxs-lookup"><span data-stu-id="f313c-128">It enables IntelliSense support for your variables and parameters.</span></span> <span data-ttu-id="f313c-129">To umožňuje zobrazit jejich vlastnosti a ostatní členové při psaní do vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="f313c-129">This allows you to see their properties and other members as you type in your code.</span></span>  
  
    -   <span data-ttu-id="f313c-130">To umožňuje kompilátoru provést kontrola typu.</span><span class="sxs-lookup"><span data-stu-id="f313c-130">It allows the compiler to perform type checking.</span></span> <span data-ttu-id="f313c-131">To pomáhá catch příkazy, které může selhat v době běhu z důvodu chyby jako např. přetečení.</span><span class="sxs-lookup"><span data-stu-id="f313c-131">This helps catch statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="f313c-132">Volání metody také zachytávalo na objekty, které je nepodporují.</span><span class="sxs-lookup"><span data-stu-id="f313c-132">It also catches calls to methods on objects that do not support them.</span></span>  
  
    -   <span data-ttu-id="f313c-133">Výsledkem rychlejší provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="f313c-133">It results in faster execution of your code.</span></span> <span data-ttu-id="f313c-134">Jedním z důvodů je, že pokud nezadáte datový typ pro element programování [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilátoru přiřadí ji `Object` typu.</span><span class="sxs-lookup"><span data-stu-id="f313c-134">One reason for this is that if you do not specify a data type for a programming element, the [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] compiler assigns it the `Object` type.</span></span> <span data-ttu-id="f313c-135">Zkompilovaný kód možná muset převést přepínat mezi `Object` a dalších typů dat, které sníží výkon.</span><span class="sxs-lookup"><span data-stu-id="f313c-135">Your compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f313c-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="f313c-136">See Also</span></span>  
 [<span data-ttu-id="f313c-137">Postupy</span><span class="sxs-lookup"><span data-stu-id="f313c-137">Procedures</span></span>](./index.md)  
 [<span data-ttu-id="f313c-138">Sub – procedury</span><span class="sxs-lookup"><span data-stu-id="f313c-138">Sub Procedures</span></span>](./sub-procedures.md)  
 [<span data-ttu-id="f313c-139">Function – procedury</span><span class="sxs-lookup"><span data-stu-id="f313c-139">Function Procedures</span></span>](./function-procedures.md)  
 [<span data-ttu-id="f313c-140">Postupy: předání argumentů proceduře</span><span class="sxs-lookup"><span data-stu-id="f313c-140">How to: Pass Arguments to a Procedure</span></span>](./how-to-pass-arguments-to-a-procedure.md)  
 [<span data-ttu-id="f313c-141">Předávání argumentů podle hodnoty a podle Reference</span><span class="sxs-lookup"><span data-stu-id="f313c-141">Passing Arguments by Value and by Reference</span></span>](./passing-arguments-by-value-and-by-reference.md)  
 [<span data-ttu-id="f313c-142">Rekurzivní procedury</span><span class="sxs-lookup"><span data-stu-id="f313c-142">Recursive Procedures</span></span>](./recursive-procedures.md)  
 [<span data-ttu-id="f313c-143">Přetížení procedury</span><span class="sxs-lookup"><span data-stu-id="f313c-143">Procedure Overloading</span></span>](./procedure-overloading.md)  
 [<span data-ttu-id="f313c-144">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="f313c-144">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [<span data-ttu-id="f313c-145">Objektově orientované programování</span><span class="sxs-lookup"><span data-stu-id="f313c-145">Object-Oriented Programming</span></span>](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
