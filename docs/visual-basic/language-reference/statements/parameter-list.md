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
ms.openlocfilehash: 651f08812032aa1c5aacc04fdb3d7f491f12b607
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58836282"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="fc9cc-102">Seznam parametrů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc9cc-102">Parameter List (Visual Basic)</span></span>
<span data-ttu-id="fc9cc-103">Určuje parametry, které procedura očekává, že když je volána.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="fc9cc-104">Více parametrů jsou odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="fc9cc-105">Následuje syntaxe pro jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-105">The following is the syntax for one parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc9cc-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc9cc-106">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]   
parametername[( )] [ As parametertype ] [ = defaultvalue ]  
```  
  
## <a name="parts"></a><span data-ttu-id="fc9cc-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="fc9cc-107">Parts</span></span>  
 `attributelist`  
 <span data-ttu-id="fc9cc-108">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-108">Optional.</span></span> <span data-ttu-id="fc9cc-109">Seznam atributů, které platí pro tento parametr.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="fc9cc-110">Je nutné uzavřít [seznam atributů](../../../visual-basic/language-reference/statements/attribute-list.md) v lomených závorkách ("`<`"a"`>`").</span><span class="sxs-lookup"><span data-stu-id="fc9cc-110">You must enclose the [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>  
  
 `Optional`  
 <span data-ttu-id="fc9cc-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-111">Optional.</span></span> <span data-ttu-id="fc9cc-112">Určuje, že tento parametr není povinný, při volání této procedury.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-112">Specifies that this parameter is not required when the procedure is called.</span></span>  
  
 `ByVal`  
 <span data-ttu-id="fc9cc-113">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-113">Optional.</span></span> <span data-ttu-id="fc9cc-114">Určuje, že proces nelze nahradit nebo změna přiřazení proměnné element základní odpovídající argumentu ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>  
  
 `ByRef`  
 <span data-ttu-id="fc9cc-115">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-115">Optional.</span></span> <span data-ttu-id="fc9cc-116">Určuje, že postupem můžete upravit základní prvek proměnné ve volajícím kódu stejným způsobem, který může volající kód samotné.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>  
  
 `ParamArray`  
 <span data-ttu-id="fc9cc-117">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-117">Optional.</span></span> <span data-ttu-id="fc9cc-118">Určuje, že poslední parametr v seznamu parametrů je volitelné pole prvků zadaného datového typu.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="fc9cc-119">To umožňuje předat libovolný počet argumentů, které procedura volající kód.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>  
  
 `parametername`  
 <span data-ttu-id="fc9cc-120">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-120">Required.</span></span> <span data-ttu-id="fc9cc-121">Název místní proměnnou představující parametr.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-121">Name of the local variable representing the parameter.</span></span>  
  
 `parametertype`  
 <span data-ttu-id="fc9cc-122">Požadováno pokud `Option Strict` je `On`.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="fc9cc-123">Typ dat místní proměnnou představující parametr.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-123">Data type of the local variable representing the parameter.</span></span>  
  
 `defaultvalue`  
 <span data-ttu-id="fc9cc-124">Vyžaduje se pro `Optional` parametry.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="fc9cc-125">Libovolný konstantní nebo konstantní výraz, který se vyhodnotí na datový typ parametru.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="fc9cc-126">Pokud je typ `Object`, nebo třídy, rozhraní, pole nebo struktura, výchozí hodnota může být pouze `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc9cc-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc9cc-127">Remarks</span></span>  
 <span data-ttu-id="fc9cc-128">Parametry jsou uzavřen v závorkách a odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="fc9cc-129">Parametr mohou být deklarovány pomocí libovolného datového typu.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="fc9cc-130">Pokud nezadáte `parametertype`, použije se výchozí `Object`.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>  
  
 <span data-ttu-id="fc9cc-131">Když volající kód volá proces, předá *argument* pro každý povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="fc9cc-132">Další informace najdete v tématu [rozdíly mezi parametry a argumenty](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="fc9cc-132">For more information, see [Differences Between Parameters and Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>  
  
 <span data-ttu-id="fc9cc-133">Argument, který volající kód předá ke každému parametru je ukazatel na základní element ve volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="fc9cc-134">Pokud je tento prvek *nonvariable* (konstanta, literal, výčtu nebo výraz), není možné pro jakýkoli kód ho změnit.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="fc9cc-135">Pokud se jedná *proměnnou* – element (deklarované proměnné, pole, vlastnost, prvku pole nebo element struktury), volající kód může změnit.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="fc9cc-136">Další informace najdete v tématu [rozdíly mezi upravitelnými a Neupravitelnými argumenty](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="fc9cc-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../../visual-basic/programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>  
  
 <span data-ttu-id="fc9cc-137">Pokud je předán element proměnné `ByRef`, postup lze také změnit.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="fc9cc-138">Další informace najdete v tématu [rozdíly mezi předáním argumentu podle hodnoty a podle Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="fc9cc-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../../visual-basic/programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="fc9cc-139">pravidla</span><span class="sxs-lookup"><span data-stu-id="fc9cc-139">Rules</span></span>  
  
-   <span data-ttu-id="fc9cc-140">**Závorky.**</span><span class="sxs-lookup"><span data-stu-id="fc9cc-140">**Parentheses.**</span></span> <span data-ttu-id="fc9cc-141">Pokud zadáte seznam parametrů, je nutné uzavřít do závorek.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="fc9cc-142">Pokud neexistují žádné parametry, můžete stále použít závorky uzavírající prázdný seznam.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="fc9cc-143">To zlepšuje čitelnost kódu bylo zcela zřejmé, že elementu je procedura.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>  
  
-   <span data-ttu-id="fc9cc-144">**Volitelné parametry.**</span><span class="sxs-lookup"><span data-stu-id="fc9cc-144">**Optional Parameters.**</span></span> <span data-ttu-id="fc9cc-145">Pokud používáte `Optional` modifikátor parametru, všechny následné parametry v seznamu musí být také volitelný a deklarovaná příkazem using `Optional` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>  
  
     <span data-ttu-id="fc9cc-146">Každý volitelný parametr prohlášení musí zadat `defaultvalue` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>  
  
     <span data-ttu-id="fc9cc-147">Další informace najdete v tématu [volitelné parametry](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="fc9cc-147">For more information, see [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md).</span></span>  
  
-   <span data-ttu-id="fc9cc-148">**Pole parametrů.**</span><span class="sxs-lookup"><span data-stu-id="fc9cc-148">**Parameter Arrays.**</span></span> <span data-ttu-id="fc9cc-149">Je nutné zadat `ByVal` pro `ParamArray` parametru.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>  
  
     <span data-ttu-id="fc9cc-150">Nelze použít obě `Optional` a `ParamArray` ve stejném seznamu parametrů.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>  
  
     <span data-ttu-id="fc9cc-151">Další informace najdete v tématu [pole parametrů](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="fc9cc-151">For more information, see [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md).</span></span>  
  
-   <span data-ttu-id="fc9cc-152">**Předávání mechanismus.**</span><span class="sxs-lookup"><span data-stu-id="fc9cc-152">**Passing Mechanism.**</span></span> <span data-ttu-id="fc9cc-153">Výchozí mechanismus pro každý argument je `ByVal`, což znamená, že proces nelze změnit základní prvek proměnné.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="fc9cc-154">Ale pokud elementu je typem odkazu, postup můžete upravit obsah nebo členy základní objekt, i když ho nelze nahradit nebo změna přiřazení samotného objektu.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>  
  
-   <span data-ttu-id="fc9cc-155">**Názvy parametrů.**</span><span class="sxs-lookup"><span data-stu-id="fc9cc-155">**Parameter Names.**</span></span> <span data-ttu-id="fc9cc-156">Pokud parametr datový typ je pole, postupujte podle `parametername` okamžitě v závorkách.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="fc9cc-157">Další informace o názvy parametrů najdete v tématu [deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="fc9cc-157">For more information on parameter names, see [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc9cc-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="fc9cc-158">Example</span></span>  
 <span data-ttu-id="fc9cc-159">Následující příklad ukazuje `Function` proceduru, která definuje dva parametry.</span><span class="sxs-lookup"><span data-stu-id="fc9cc-159">The following example shows a `Function` procedure that defines two parameters.</span></span>  
  
 [!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="fc9cc-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc9cc-160">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="fc9cc-161">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="fc9cc-161">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="fc9cc-162">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="fc9cc-162">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)
- [<span data-ttu-id="fc9cc-163">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="fc9cc-163">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="fc9cc-164">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="fc9cc-164">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)
- [<span data-ttu-id="fc9cc-165">Příkaz Option Strict</span><span class="sxs-lookup"><span data-stu-id="fc9cc-165">Option Strict Statement</span></span>](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [<span data-ttu-id="fc9cc-166">Přehled atributy</span><span class="sxs-lookup"><span data-stu-id="fc9cc-166">Attributes overview</span></span>](../../../visual-basic/programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="fc9cc-167">Postupy: Přerušení a kombinování příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="fc9cc-167">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
