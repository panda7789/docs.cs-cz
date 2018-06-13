---
title: Seznam parametrů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic code, procedures
- parameters [Visual Basic], Visual Basic
- parameters [Visual Basic], lists
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- arguments [Visual Basic], Visual Basic
- procedures [Visual Basic], parameter lists
ms.assetid: 5d737319-0c34-4df9-a23d-188fc840becd
ms.openlocfilehash: 147a2501219db9f1f1c10f9cf1a81aa395b5ec2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605053"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="6c910-102">Seznam parametrů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6c910-102">Parameter List (Visual Basic)</span></span>
<span data-ttu-id="6c910-103">Určuje parametry, které procedura očekává, že když je volána.</span><span class="sxs-lookup"><span data-stu-id="6c910-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="6c910-104">Několik parametrů jsou oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="6c910-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="6c910-105">Toto je syntaxe pro jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="6c910-105">The following is the syntax for one parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c910-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c910-106">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a><span data-ttu-id="6c910-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="6c910-107">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="6c910-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6c910-108">Optional.</span></span> <span data-ttu-id="6c910-109">Seznam atributů, které platí pro tento parametr.</span><span class="sxs-lookup"><span data-stu-id="6c910-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="6c910-110">Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách ("`<`"a"`>`").</span><span class="sxs-lookup"><span data-stu-id="6c910-110">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
 `Optional`  
 <span data-ttu-id="6c910-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6c910-111">Optional.</span></span> <span data-ttu-id="6c910-112">Určuje, že tento parametr není požadovaná při volání procedury.</span><span class="sxs-lookup"><span data-stu-id="6c910-112">Specifies that this parameter is not required when the procedure is called.</span></span>  
  
 `ByVal`  
 <span data-ttu-id="6c910-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6c910-113">Optional.</span></span> <span data-ttu-id="6c910-114">Určuje, že postup nelze nahradit nebo přiřazení proměnných element základní odpovídající argument ve volání kódu.</span><span class="sxs-lookup"><span data-stu-id="6c910-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>  
  
 `ByRef`  
 <span data-ttu-id="6c910-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6c910-115">Optional.</span></span> <span data-ttu-id="6c910-116">Určuje, že postup můžete upravit základní proměnné element v kód volání stejným způsobem, může volání samotný kód.</span><span class="sxs-lookup"><span data-stu-id="6c910-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>  
  
 `ParamArray`  
 <span data-ttu-id="6c910-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="6c910-117">Optional.</span></span> <span data-ttu-id="6c910-118">Určuje, že poslední parametr v seznamu parametrů je volitelné pole elementů zadaného datového typu.</span><span class="sxs-lookup"><span data-stu-id="6c910-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="6c910-119">To umožňuje kód volání předat libovolný počet argumentů procesu.</span><span class="sxs-lookup"><span data-stu-id="6c910-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>  
  
 `parametername`  
 <span data-ttu-id="6c910-120">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="6c910-120">Required.</span></span> <span data-ttu-id="6c910-121">Název místní proměnné reprezentující parametr.</span><span class="sxs-lookup"><span data-stu-id="6c910-121">Name of the local variable representing the parameter.</span></span>  
  
 `parametertype`  
 <span data-ttu-id="6c910-122">Požadováno pokud `Option Strict` je `On`.</span><span class="sxs-lookup"><span data-stu-id="6c910-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="6c910-123">Datový typ místní proměnné reprezentující parametr.</span><span class="sxs-lookup"><span data-stu-id="6c910-123">Data type of the local variable representing the parameter.</span></span>  
  
 `defaultvalue`  
 <span data-ttu-id="6c910-124">Vyžaduje se pro `Optional` parametry.</span><span class="sxs-lookup"><span data-stu-id="6c910-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="6c910-125">Jakýkoli konstantní nebo konstantní výraz, jehož výsledkem je datový typ parametru.</span><span class="sxs-lookup"><span data-stu-id="6c910-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="6c910-126">Pokud je typ `Object`, nebo třídu, rozhraní, pole nebo struktura, výchozí hodnota může být pouze `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="6c910-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c910-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c910-127">Remarks</span></span>  
 <span data-ttu-id="6c910-128">Parametry jsou uzavřeny v závorkách a oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="6c910-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="6c910-129">Parametr lze deklarovat s žádným typem data.</span><span class="sxs-lookup"><span data-stu-id="6c910-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="6c910-130">Pokud nezadáte `parametertype`, nastaví se jako výchozí `Object`.</span><span class="sxs-lookup"><span data-stu-id="6c910-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>  
  
 <span data-ttu-id="6c910-131">Volání kódu volá proceduru, předá *argument* pro každý požadovaný parametr.</span><span class="sxs-lookup"><span data-stu-id="6c910-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="6c910-132">Další informace najdete v tématu [rozdíly mezi parametry a argumenty](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="6c910-132">For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>  
  
 <span data-ttu-id="6c910-133">Argument, který volací kód předá každý parametr je ukazatel na základní elementu v kódu volání.</span><span class="sxs-lookup"><span data-stu-id="6c910-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="6c910-134">Pokud je tento element *nonvariable* (konstanta, literál, výčet nebo výraz), není možné, aby žádný kód ho změnit.</span><span class="sxs-lookup"><span data-stu-id="6c910-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="6c910-135">Pokud je *proměnná* – element (deklarované proměnné, pole, vlastnost, element pole nebo Struktura element), můžete ho změnit kód volání.</span><span class="sxs-lookup"><span data-stu-id="6c910-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="6c910-136">Další informace najdete v tématu [rozdíly mezi upravitelnými a Neupravitelnými argumenty](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="6c910-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>  
  
 <span data-ttu-id="6c910-137">Pokud je předán element proměnné `ByRef`, postup lze také změnit.</span><span class="sxs-lookup"><span data-stu-id="6c910-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="6c910-138">Další informace najdete v tématu [rozdíly mezi předáním argumentu podle hodnoty a podle Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="6c910-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="6c910-139">Pravidla</span><span class="sxs-lookup"><span data-stu-id="6c910-139">Rules</span></span>  
  
-   <span data-ttu-id="6c910-140">**Závorky.**</span><span class="sxs-lookup"><span data-stu-id="6c910-140">**Parentheses.**</span></span> <span data-ttu-id="6c910-141">Pokud zadáte seznam parametrů, je nutné uzavřít v závorkách.</span><span class="sxs-lookup"><span data-stu-id="6c910-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="6c910-142">Pokud neexistují žádné parametry, můžete stále závorkách obklopuje prázdný seznam.</span><span class="sxs-lookup"><span data-stu-id="6c910-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="6c910-143">Dojde tak ke zlepšení čitelnosti kódu, které toto vyjasňují, že prvek je procedury.</span><span class="sxs-lookup"><span data-stu-id="6c910-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>  
  
-   <span data-ttu-id="6c910-144">**Volitelné parametry.**</span><span class="sxs-lookup"><span data-stu-id="6c910-144">**Optional Parameters.**</span></span> <span data-ttu-id="6c910-145">Pokud použijete `Optional` modifikátor na parametr, všechny následné parametry v seznamu musí být také volitelné a deklarovat pomocí `Optional` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="6c910-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>  
  
     <span data-ttu-id="6c910-146">Musíte zadat všechny deklarace volitelný parametr `defaultvalue` klauzule.</span><span class="sxs-lookup"><span data-stu-id="6c910-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>  
  
     <span data-ttu-id="6c910-147">Další informace najdete v tématu [volitelné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="6c910-147">For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span></span>  
  
-   <span data-ttu-id="6c910-148">**Pole parametrů.**</span><span class="sxs-lookup"><span data-stu-id="6c910-148">**Parameter Arrays.**</span></span> <span data-ttu-id="6c910-149">Je nutné zadat `ByVal` pro `ParamArray` parametr.</span><span class="sxs-lookup"><span data-stu-id="6c910-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>  
  
     <span data-ttu-id="6c910-150">Nemůžete použít obě `Optional` a `ParamArray` v stejný seznam parametrů.</span><span class="sxs-lookup"><span data-stu-id="6c910-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>  
  
     <span data-ttu-id="6c910-151">Další informace najdete v tématu [pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="6c910-151">For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
-   <span data-ttu-id="6c910-152">**Mechanismus předávání.**</span><span class="sxs-lookup"><span data-stu-id="6c910-152">**Passing Mechanism.**</span></span> <span data-ttu-id="6c910-153">Výchozí mechanismus pro každý argument je `ByVal`, což znamená, postup nelze změnit základní proměnné elementu.</span><span class="sxs-lookup"><span data-stu-id="6c910-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="6c910-154">Ale pokud element je typu odkaz, postup můžete upravit obsah nebo členy podkladového objektu, i když ho nelze nahradit nebo změna přiřazení samotného objektu.</span><span class="sxs-lookup"><span data-stu-id="6c910-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>  
  
-   <span data-ttu-id="6c910-155">**Názvy parametrů.**</span><span class="sxs-lookup"><span data-stu-id="6c910-155">**Parameter Names.**</span></span> <span data-ttu-id="6c910-156">Pokud parametr datový typ pole, postupujte podle `parametername` okamžitě v závorkách.</span><span class="sxs-lookup"><span data-stu-id="6c910-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="6c910-157">Další informace o názvy parametrů najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="6c910-157">For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c910-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c910-158">Example</span></span>  
 <span data-ttu-id="6c910-159">Následující příklad ukazuje `Function` procedury, která definuje dva parametry.</span><span class="sxs-lookup"><span data-stu-id="6c910-159">The following example shows a `Function` procedure that defines two parameters.</span></span>  
  
 [!code-vb[VbVbalrStatements#2](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/parameter-list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="6c910-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c910-160">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute>  
 [<span data-ttu-id="6c910-161">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="6c910-161">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="6c910-162">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="6c910-162">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [<span data-ttu-id="6c910-163">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="6c910-163">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="6c910-164">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="6c910-164">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [<span data-ttu-id="6c910-165">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="6c910-165">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [<span data-ttu-id="6c910-166">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="6c910-166">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)  
 [<span data-ttu-id="6c910-167">Postupy: Přerušení a kombinace příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="6c910-167">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
