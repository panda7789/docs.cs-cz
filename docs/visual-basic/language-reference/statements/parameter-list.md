---
title: Seznam parametrů
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
ms.openlocfilehash: 706fc2414806db5608cce410bf4156839ec2d83e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404314"
---
# <a name="parameter-list-visual-basic"></a><span data-ttu-id="b4cf0-102">Seznam parametrů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b4cf0-102">Parameter List (Visual Basic)</span></span>

<span data-ttu-id="b4cf0-103">Určuje parametry, které procedura očekává při volání.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-103">Specifies the parameters a procedure expects when it is called.</span></span> <span data-ttu-id="b4cf0-104">Více parametrů je odděleno čárkami.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-104">Multiple parameters are separated by commas.</span></span> <span data-ttu-id="b4cf0-105">Následuje syntaxe pro jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-105">The following is the syntax for one parameter.</span></span>

## <a name="syntax"></a><span data-ttu-id="b4cf0-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4cf0-106">Syntax</span></span>

```vb
[ <attributelist> ] [ Optional ] [{ ByVal | ByRef }] [ ParamArray ]
parametername[( )] [ As parametertype ] [ = defaultvalue ]
```

## <a name="parts"></a><span data-ttu-id="b4cf0-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="b4cf0-107">Parts</span></span>

`attributelist`  
<span data-ttu-id="b4cf0-108">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-108">Optional.</span></span> <span data-ttu-id="b4cf0-109">Seznam atributů, které se vztahují na tento parametr.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-109">List of attributes that apply to this parameter.</span></span> <span data-ttu-id="b4cf0-110">[Seznam atributů](attribute-list.md) musíte uzavřít do lomených závorek (" `<` " a " `>` ").</span><span class="sxs-lookup"><span data-stu-id="b4cf0-110">You must enclose the [Attribute List](attribute-list.md) in angle brackets ("`<`" and "`>`").</span></span>

`Optional`  
<span data-ttu-id="b4cf0-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-111">Optional.</span></span> <span data-ttu-id="b4cf0-112">Určuje, že tento parametr není při volání procedury vyžadován.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-112">Specifies that this parameter is not required when the procedure is called.</span></span>

`ByVal`  
<span data-ttu-id="b4cf0-113">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-113">Optional.</span></span> <span data-ttu-id="b4cf0-114">Určuje, že procedura nemůže nahradit nebo změnit přiřazení elementu proměnné odpovídající argumentu v volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-114">Specifies that the procedure cannot replace or reassign the variable element underlying the corresponding argument in the calling code.</span></span>

`ByRef`  
<span data-ttu-id="b4cf0-115">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-115">Optional.</span></span> <span data-ttu-id="b4cf0-116">Určuje, že procedura může upravit základní prvek proměnné v volajícím kódu stejným způsobem, jako může samotný volající kód.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-116">Specifies that the procedure can modify the underlying variable element in the calling code the same way the calling code itself can.</span></span>

`ParamArray`  
<span data-ttu-id="b4cf0-117">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-117">Optional.</span></span> <span data-ttu-id="b4cf0-118">Určuje, že poslední parametr v seznamu parametrů je volitelné pole prvků zadaného datového typu.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-118">Specifies that the last parameter in the parameter list is an optional array of elements of the specified data type.</span></span> <span data-ttu-id="b4cf0-119">To umožňuje volajícímu kódu předat libovolný počet argumentů postupu.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-119">This lets the calling code pass an arbitrary number of arguments to the procedure.</span></span>

`parametername`  
<span data-ttu-id="b4cf0-120">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-120">Required.</span></span> <span data-ttu-id="b4cf0-121">Název místní proměnné představující parametr</span><span class="sxs-lookup"><span data-stu-id="b4cf0-121">Name of the local variable representing the parameter.</span></span>

`parametertype`  
<span data-ttu-id="b4cf0-122">Požadováno v `Option Strict` případě `On` , že je.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-122">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="b4cf0-123">Datový typ lokální proměnné představující parametr</span><span class="sxs-lookup"><span data-stu-id="b4cf0-123">Data type of the local variable representing the parameter.</span></span>

`defaultvalue`  
<span data-ttu-id="b4cf0-124">Vyžaduje se pro `Optional` parametry.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-124">Required for `Optional` parameters.</span></span> <span data-ttu-id="b4cf0-125">Libovolný konstantní nebo konstantní výraz, který je vyhodnocen jako datový typ parametru.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-125">Any constant or constant expression that evaluates to the data type of the parameter.</span></span> <span data-ttu-id="b4cf0-126">Pokud je typ `Object` , nebo třída, rozhraní, pole nebo struktura, může být výchozí hodnota pouze `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="b4cf0-126">If the type is `Object`, or a class, interface, array, or structure, the default value can only be `Nothing`.</span></span>

## <a name="remarks"></a><span data-ttu-id="b4cf0-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4cf0-127">Remarks</span></span>

<span data-ttu-id="b4cf0-128">Parametry jsou obklopeny závorkami a odděleny čárkami.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-128">Parameters are surrounded by parentheses and separated by commas.</span></span> <span data-ttu-id="b4cf0-129">Parametr lze deklarovat s libovolným datovým typem.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-129">A parameter can be declared with any data type.</span></span> <span data-ttu-id="b4cf0-130">Pokud nezadáte `parametertype` , použije se výchozí hodnota `Object` .</span><span class="sxs-lookup"><span data-stu-id="b4cf0-130">If you do not specify `parametertype`, it defaults to `Object`.</span></span>

<span data-ttu-id="b4cf0-131">Když volající kód volá proceduru, předá *argument* každému požadovanému parametru.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-131">When the calling code calls the procedure, it passes an *argument* to each required parameter.</span></span> <span data-ttu-id="b4cf0-132">Další informace najdete v tématu [rozdíly mezi parametry a argumenty](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="b4cf0-132">For more information, see [Differences Between Parameters and Arguments](../../programming-guide/language-features/procedures/differences-between-parameters-and-arguments.md).</span></span>

<span data-ttu-id="b4cf0-133">Argument, který volající kód předává každému parametru, je ukazatel na základní prvek v volajícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-133">The argument the calling code passes to each parameter is a pointer to an underlying element in the calling code.</span></span> <span data-ttu-id="b4cf0-134">Pokud je tento prvek *neproměnný* (konstanta, literál, výčet nebo výraz), není možné, aby se kód změnil.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-134">If this element is *nonvariable* (a constant, literal, enumeration, or expression), it is impossible for any code to change it.</span></span> <span data-ttu-id="b4cf0-135">Pokud se jedná o prvek *proměnné* (deklarovaná proměnná, pole, vlastnost, prvek pole nebo prvek struktury), volající kód ho může změnit.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-135">If it is a *variable* element (a declared variable, field, property, array element, or structure element), the calling code can change it.</span></span> <span data-ttu-id="b4cf0-136">Další informace naleznete v tématu [rozdíly mezi upravitelnými a neupravitelnými argumenty](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span><span class="sxs-lookup"><span data-stu-id="b4cf0-136">For more information, see [Differences Between Modifiable and Nonmodifiable Arguments](../../programming-guide/language-features/procedures/differences-between-modifiable-and-nonmodifiable-arguments.md).</span></span>

<span data-ttu-id="b4cf0-137">Pokud je předán prvek proměnné `ByRef` , může postup změnit také.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-137">If a variable element is passed `ByRef`, the procedure can change it as well.</span></span> <span data-ttu-id="b4cf0-138">Další informace naleznete v tématu [rozdíly mezi předáním argumentu podle hodnoty a podle reference](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span><span class="sxs-lookup"><span data-stu-id="b4cf0-138">For more information, see [Differences Between Passing an Argument By Value and By Reference](../../programming-guide/language-features/procedures/differences-between-passing-an-argument-by-value-and-by-reference.md).</span></span>

## <a name="rules"></a><span data-ttu-id="b4cf0-139">Pravidla</span><span class="sxs-lookup"><span data-stu-id="b4cf0-139">Rules</span></span>

- <span data-ttu-id="b4cf0-140">**Závorky.**</span><span class="sxs-lookup"><span data-stu-id="b4cf0-140">**Parentheses.**</span></span> <span data-ttu-id="b4cf0-141">Pokud zadáte seznam parametrů, je nutné jej uzavřít do závorek.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-141">If you specify a parameter list, you must enclose it in parentheses.</span></span> <span data-ttu-id="b4cf0-142">Pokud žádné parametry neexistují, můžete stále používat kulaté závorky ohraničující prázdný seznam.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-142">If there are no parameters, you can still use parentheses enclosing an empty list.</span></span> <span data-ttu-id="b4cf0-143">Tím se zlepší čitelnost kódu tím, že objasněte, že prvek je procedura.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-143">This improves the readability of your code by clarifying that the element is a procedure.</span></span>

- <span data-ttu-id="b4cf0-144">**Volitelné parametry.**</span><span class="sxs-lookup"><span data-stu-id="b4cf0-144">**Optional Parameters.**</span></span> <span data-ttu-id="b4cf0-145">Použijete-li `Optional` modifikátor u parametru, všechny následující parametry v seznamu musí být také nepovinné a deklarovány pomocí `Optional` modifikátoru.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-145">If you use the `Optional` modifier on a parameter, all subsequent parameters in the list must also be optional and be declared by using the `Optional` modifier.</span></span>

     <span data-ttu-id="b4cf0-146">Každá deklarace volitelného parametru musí zadat `defaultvalue` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-146">Every optional parameter declaration must supply the `defaultvalue` clause.</span></span>

     <span data-ttu-id="b4cf0-147">Další informace najdete v tématu [volitelné parametry](../../programming-guide/language-features/procedures/optional-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="b4cf0-147">For more information, see [Optional Parameters](../../programming-guide/language-features/procedures/optional-parameters.md).</span></span>

- <span data-ttu-id="b4cf0-148">**Pole parametrů.**</span><span class="sxs-lookup"><span data-stu-id="b4cf0-148">**Parameter Arrays.**</span></span> <span data-ttu-id="b4cf0-149">Je nutné zadat `ByVal` pro `ParamArray` parametr.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-149">You must specify `ByVal` for a `ParamArray` parameter.</span></span>

     <span data-ttu-id="b4cf0-150">`Optional` `ParamArray` Ve stejném seznamu parametrů nelze použít obojí a.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-150">You cannot use both `Optional` and `ParamArray` in the same parameter list.</span></span>

     <span data-ttu-id="b4cf0-151">Další informace naleznete v tématu [pole parametrů](../../programming-guide/language-features/procedures/parameter-arrays.md).</span><span class="sxs-lookup"><span data-stu-id="b4cf0-151">For more information, see [Parameter Arrays](../../programming-guide/language-features/procedures/parameter-arrays.md).</span></span>

- <span data-ttu-id="b4cf0-152">**Mechanismus předávání.**</span><span class="sxs-lookup"><span data-stu-id="b4cf0-152">**Passing Mechanism.**</span></span> <span data-ttu-id="b4cf0-153">Výchozím mechanismem pro každý argument je `ByVal` , což znamená, že procedura nemůže změnit základní prvek proměnné.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-153">The default mechanism for every argument is `ByVal`, which means the procedure cannot change the underlying variable element.</span></span> <span data-ttu-id="b4cf0-154">Nicméně pokud je prvek odkazový typ, může procedura změnit obsah nebo členy podkladového objektu, přestože nemůže nahradit nebo změnit přiřazení samotného objektu.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-154">However, if the element is a reference type, the procedure can modify the contents or members of the underlying object, even though it cannot replace or reassign the object itself.</span></span>

- <span data-ttu-id="b4cf0-155">**Názvy parametrů**</span><span class="sxs-lookup"><span data-stu-id="b4cf0-155">**Parameter Names.**</span></span> <span data-ttu-id="b4cf0-156">Pokud je datovým typem parametru pole, Sledujte `parametername` ihned závorky.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-156">If the parameter's data type is an array, follow `parametername` immediately by parentheses.</span></span> <span data-ttu-id="b4cf0-157">Další informace o názvech parametrů naleznete v tématu [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="b4cf0-157">For more information on parameter names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

## <a name="example"></a><span data-ttu-id="b4cf0-158">Příklad</span><span class="sxs-lookup"><span data-stu-id="b4cf0-158">Example</span></span>

<span data-ttu-id="b4cf0-159">Následující příklad ukazuje `Function` proceduru, která definuje dva parametry.</span><span class="sxs-lookup"><span data-stu-id="b4cf0-159">The following example shows a `Function` procedure that defines two parameters.</span></span>

[!code-vb[VbVbalrStatements#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#2)]

## <a name="see-also"></a><span data-ttu-id="b4cf0-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4cf0-160">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute>
- [<span data-ttu-id="b4cf0-161">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="b4cf0-161">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="b4cf0-162">Sub – příkaz</span><span class="sxs-lookup"><span data-stu-id="b4cf0-162">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="b4cf0-163">Declare – příkaz</span><span class="sxs-lookup"><span data-stu-id="b4cf0-163">Declare Statement</span></span>](declare-statement.md)
- [<span data-ttu-id="b4cf0-164">Structure – příkaz</span><span class="sxs-lookup"><span data-stu-id="b4cf0-164">Structure Statement</span></span>](structure-statement.md)
- [<span data-ttu-id="b4cf0-165">Option Strict – příkaz</span><span class="sxs-lookup"><span data-stu-id="b4cf0-165">Option Strict Statement</span></span>](option-strict-statement.md)
- [<span data-ttu-id="b4cf0-166">Přehled atributů</span><span class="sxs-lookup"><span data-stu-id="b4cf0-166">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="b4cf0-167">Postupy: Přerušení a kombinování příkazů v kódu</span><span class="sxs-lookup"><span data-stu-id="b4cf0-167">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
