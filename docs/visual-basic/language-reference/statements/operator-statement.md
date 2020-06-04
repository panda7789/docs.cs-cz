---
title: Operator – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: f9e6ffe5a49715592399321ab471d73826e05d8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404392"
---
# <a name="operator-statement"></a><span data-ttu-id="8db0b-102">Operator – příkaz</span><span class="sxs-lookup"><span data-stu-id="8db0b-102">Operator Statement</span></span>

<span data-ttu-id="8db0b-103">Deklaruje symbol operátoru, operandy a kód, který definuje proceduru operátoru pro třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="8db0b-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="8db0b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8db0b-104">Syntax</span></span>

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a><span data-ttu-id="8db0b-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="8db0b-105">Parts</span></span>

`attrlist`  
<span data-ttu-id="8db0b-106">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="8db0b-106">Optional.</span></span> <span data-ttu-id="8db0b-107">Viz [seznam atributů](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="8db0b-107">See [Attribute List](attribute-list.md).</span></span>

`Public`  
<span data-ttu-id="8db0b-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="8db0b-108">Required.</span></span> <span data-ttu-id="8db0b-109">Označuje, že tato procedura operátoru má [veřejný](../modifiers/public.md) přístup.</span><span class="sxs-lookup"><span data-stu-id="8db0b-109">Indicates that this operator procedure has [Public](../modifiers/public.md) access.</span></span>

`Overloads`  
<span data-ttu-id="8db0b-110">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="8db0b-110">Optional.</span></span> <span data-ttu-id="8db0b-111">Viz [přetížení](../modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="8db0b-111">See [Overloads](../modifiers/overloads.md).</span></span>

`Shared`  
<span data-ttu-id="8db0b-112">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="8db0b-112">Required.</span></span> <span data-ttu-id="8db0b-113">Označuje, že procedura tohoto operátoru je [sdílená](../modifiers/shared.md) procedura.</span><span class="sxs-lookup"><span data-stu-id="8db0b-113">Indicates that this operator procedure is a [Shared](../modifiers/shared.md) procedure.</span></span>

`Shadows`  
<span data-ttu-id="8db0b-114">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="8db0b-114">Optional.</span></span> <span data-ttu-id="8db0b-115">Viz [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="8db0b-115">See [Shadows](../modifiers/shadows.md).</span></span>

`Widening`  
<span data-ttu-id="8db0b-116">Požadováno pro operátor převodu, pokud nezadáte `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="8db0b-117">Označuje, že tato procedura operátora definuje [rozšiřující](../modifiers/widening.md) převod.</span><span class="sxs-lookup"><span data-stu-id="8db0b-117">Indicates that this operator procedure defines a [Widening](../modifiers/widening.md) conversion.</span></span> <span data-ttu-id="8db0b-118">Viz "rozšiřující a zúžené převody" na této stránce s technickou pomocí.</span><span class="sxs-lookup"><span data-stu-id="8db0b-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`Narrowing`  
<span data-ttu-id="8db0b-119">Požadováno pro operátor převodu, pokud nezadáte `Widening` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="8db0b-120">Označuje, že tato procedura operátora definuje [zužující](../modifiers/narrowing.md) převod.</span><span class="sxs-lookup"><span data-stu-id="8db0b-120">Indicates that this operator procedure defines a [Narrowing](../modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="8db0b-121">Viz "rozšiřující a zúžené převody" na této stránce s technickou pomocí.</span><span class="sxs-lookup"><span data-stu-id="8db0b-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`operatorsymbol`  
<span data-ttu-id="8db0b-122">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="8db0b-122">Required.</span></span> <span data-ttu-id="8db0b-123">Symbol nebo identifikátor operátoru, který definuje tento operátor procedury.</span><span class="sxs-lookup"><span data-stu-id="8db0b-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>

`operand1`  
<span data-ttu-id="8db0b-124">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="8db0b-124">Required.</span></span> <span data-ttu-id="8db0b-125">Název a typ jednoho operandu unárního operátoru (včetně operátoru převodu) nebo levého operandu binárního operátoru.</span><span class="sxs-lookup"><span data-stu-id="8db0b-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>

`operand2`  
<span data-ttu-id="8db0b-126">Vyžaduje se pro binární operátory.</span><span class="sxs-lookup"><span data-stu-id="8db0b-126">Required for binary operators.</span></span> <span data-ttu-id="8db0b-127">Název a typ pravého operandu binárního operátoru.</span><span class="sxs-lookup"><span data-stu-id="8db0b-127">The name and type of the right operand of a binary operator.</span></span>

<span data-ttu-id="8db0b-128">`operand1`a `operand2` mají následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="8db0b-128">`operand1` and `operand2` have the following syntax and parts:</span></span>

`[ ByVal ] operandname [ As operandtype ]`

|<span data-ttu-id="8db0b-129">Část</span><span class="sxs-lookup"><span data-stu-id="8db0b-129">Part</span></span>|<span data-ttu-id="8db0b-130">Description</span><span class="sxs-lookup"><span data-stu-id="8db0b-130">Description</span></span>|
|----------|-----------------|
|`ByVal`|<span data-ttu-id="8db0b-131">Volitelné, ale mechanismus předávání musí být [ByVal](../modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="8db0b-131">Optional, but the passing mechanism must be [ByVal](../modifiers/byval.md).</span></span>|
|`operandname`|<span data-ttu-id="8db0b-132">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="8db0b-132">Required.</span></span> <span data-ttu-id="8db0b-133">Název proměnné představující tento operand</span><span class="sxs-lookup"><span data-stu-id="8db0b-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="8db0b-134">Viz [deklarované názvy elementů](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="8db0b-134">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`operandtype`|<span data-ttu-id="8db0b-135">Volitelné `Option Strict` , pokud není `On` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="8db0b-136">Datový typ tohoto operandu.</span><span class="sxs-lookup"><span data-stu-id="8db0b-136">Data type of this operand.</span></span>|

`type`  
<span data-ttu-id="8db0b-137">Volitelné `Option Strict` , pokud není `On` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="8db0b-138">Datový typ hodnoty, kterou procedura operátor vrátí</span><span class="sxs-lookup"><span data-stu-id="8db0b-138">Data type of the value the operator procedure returns.</span></span>

`statements`  
<span data-ttu-id="8db0b-139">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="8db0b-139">Optional.</span></span> <span data-ttu-id="8db0b-140">Blok příkazů, které spouští proceduru operátoru.</span><span class="sxs-lookup"><span data-stu-id="8db0b-140">Block of statements that the operator procedure runs.</span></span>

`returnvalue`  
<span data-ttu-id="8db0b-141">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="8db0b-141">Required.</span></span> <span data-ttu-id="8db0b-142">Hodnota, kterou procedura operátor vrátí na volající kód.</span><span class="sxs-lookup"><span data-stu-id="8db0b-142">The value that the operator procedure returns to the calling code.</span></span>

<span data-ttu-id="8db0b-143">`End` `Operator`</span><span class="sxs-lookup"><span data-stu-id="8db0b-143">`End` `Operator`</span></span>  
<span data-ttu-id="8db0b-144">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="8db0b-144">Required.</span></span> <span data-ttu-id="8db0b-145">Ukončí definici této procedury operátoru.</span><span class="sxs-lookup"><span data-stu-id="8db0b-145">Terminates the definition of this operator procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="8db0b-146">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8db0b-146">Remarks</span></span>

<span data-ttu-id="8db0b-147">Můžete použít `Operator` pouze ve třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="8db0b-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="8db0b-148">To znamená, že *kontext deklarace* pro operátor nemůže být zdrojový soubor, obor názvů, modul, rozhraní, procedura nebo blok.</span><span class="sxs-lookup"><span data-stu-id="8db0b-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="8db0b-149">Další informace najdete v tématu [deklarace kontextů a výchozích úrovní přístupu](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8db0b-149">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="8db0b-150">Všechny operátory musí být `Public Shared` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="8db0b-151">Nemůžete zadat `ByRef` , `Optional` nebo `ParamArray` pro žádný operand.</span><span class="sxs-lookup"><span data-stu-id="8db0b-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>

<span data-ttu-id="8db0b-152">Symbol operátoru ani identifikátor nelze použít pro uložení návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8db0b-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="8db0b-153">Je nutné použít `Return` příkaz a musí zadat hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8db0b-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="8db0b-154">Libovolný počet `Return` příkazů se může objevit kdekoli v proceduře.</span><span class="sxs-lookup"><span data-stu-id="8db0b-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>

<span data-ttu-id="8db0b-155">Definováním operátoru tímto způsobem se říká *přetížení operátoru*, bez ohledu na to, jestli používáte `Overloads` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="8db0b-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="8db0b-156">V následující tabulce jsou uvedeny operátory, které můžete definovat.</span><span class="sxs-lookup"><span data-stu-id="8db0b-156">The following table lists the operators you can define.</span></span>

|<span data-ttu-id="8db0b-157">Typ</span><span class="sxs-lookup"><span data-stu-id="8db0b-157">Type</span></span>|<span data-ttu-id="8db0b-158">Operátory</span><span class="sxs-lookup"><span data-stu-id="8db0b-158">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="8db0b-159">Unární</span><span class="sxs-lookup"><span data-stu-id="8db0b-159">Unary</span></span>|<span data-ttu-id="8db0b-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="8db0b-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="8db0b-161">Binární</span><span class="sxs-lookup"><span data-stu-id="8db0b-161">Binary</span></span>|<span data-ttu-id="8db0b-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="8db0b-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="8db0b-163">Převod (Unární)</span><span class="sxs-lookup"><span data-stu-id="8db0b-163">Conversion (unary)</span></span>|`CType`|

<span data-ttu-id="8db0b-164">Všimněte si, že `=` operátor v binárním seznamu je operátor porovnání, nikoli operátor přiřazení.</span><span class="sxs-lookup"><span data-stu-id="8db0b-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

<span data-ttu-id="8db0b-165">Při definování `CType` musíte zadat buď `Widening` nebo `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>

## <a name="matched-pairs"></a><span data-ttu-id="8db0b-166">Spárované páry</span><span class="sxs-lookup"><span data-stu-id="8db0b-166">Matched Pairs</span></span>

<span data-ttu-id="8db0b-167">Je nutné definovat určité operátory jako spárované páry.</span><span class="sxs-lookup"><span data-stu-id="8db0b-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="8db0b-168">Pokud definujete některý z operátorů takového páru, je nutné definovat i další.</span><span class="sxs-lookup"><span data-stu-id="8db0b-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="8db0b-169">Spárované páry jsou následující:</span><span class="sxs-lookup"><span data-stu-id="8db0b-169">The matched pairs are the following:</span></span>

- <span data-ttu-id="8db0b-170">`=` a `<>`</span><span class="sxs-lookup"><span data-stu-id="8db0b-170">`=` and `<>`</span></span>

- <span data-ttu-id="8db0b-171">`>` a `<`</span><span class="sxs-lookup"><span data-stu-id="8db0b-171">`>` and `<`</span></span>

- <span data-ttu-id="8db0b-172">`>=` a `<=`</span><span class="sxs-lookup"><span data-stu-id="8db0b-172">`>=` and `<=`</span></span>

- <span data-ttu-id="8db0b-173">`IsTrue` a `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="8db0b-173">`IsTrue` and `IsFalse`</span></span>

## <a name="data-type-restrictions"></a><span data-ttu-id="8db0b-174">Omezení datového typu</span><span class="sxs-lookup"><span data-stu-id="8db0b-174">Data Type Restrictions</span></span>

<span data-ttu-id="8db0b-175">Každý operátor, který definujete, musí zahrnovat třídu nebo strukturu, na které definujete.</span><span class="sxs-lookup"><span data-stu-id="8db0b-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="8db0b-176">To znamená, že třída nebo struktura se musí objevit jako datový typ následujících:</span><span class="sxs-lookup"><span data-stu-id="8db0b-176">This means that the class or structure must appear as the data type of the following:</span></span>

- <span data-ttu-id="8db0b-177">Operand unárního operátoru.</span><span class="sxs-lookup"><span data-stu-id="8db0b-177">The operand of a unary operator.</span></span>

- <span data-ttu-id="8db0b-178">Nejméně jeden z operandů binárního operátoru.</span><span class="sxs-lookup"><span data-stu-id="8db0b-178">At least one of the operands of a binary operator.</span></span>

- <span data-ttu-id="8db0b-179">Buď operand, nebo návratový typ operátoru převodu.</span><span class="sxs-lookup"><span data-stu-id="8db0b-179">Either the operand or the return type of a conversion operator.</span></span>

 <span data-ttu-id="8db0b-180">Některé operátory mají další omezení datového typu, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="8db0b-180">Certain operators have additional data type restrictions, as follows:</span></span>

- <span data-ttu-id="8db0b-181">Definujete-li `IsTrue` `IsFalse` operátory a, musí oba vracet `Boolean` typ.</span><span class="sxs-lookup"><span data-stu-id="8db0b-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>

- <span data-ttu-id="8db0b-182">Definujete-li `<<` `>>` operátory a, musí obě určovat `Integer` typ pro `operandtype` `operand2` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>

<span data-ttu-id="8db0b-183">Návratový typ nemusí odpovídat typu žádného operandu.</span><span class="sxs-lookup"><span data-stu-id="8db0b-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="8db0b-184">Například operátor porovnání, jako `=` je nebo, `<>` může vracet `Boolean` i v případě, že žádný operand není `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>

## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="8db0b-185">Logické a bitové operátory</span><span class="sxs-lookup"><span data-stu-id="8db0b-185">Logical and Bitwise Operators</span></span>

<span data-ttu-id="8db0b-186">`And`Operátory, `Or` , `Not` a `Xor` mohou v Visual Basic provádět buď logické, nebo bitové operace.</span><span class="sxs-lookup"><span data-stu-id="8db0b-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="8db0b-187">Pokud však definujete jeden z těchto operátorů pro třídu nebo strukturu, můžete definovat pouze jeho bitovou operaci.</span><span class="sxs-lookup"><span data-stu-id="8db0b-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>

<span data-ttu-id="8db0b-188">Operátor nelze definovat `AndAlso` přímo pomocí `Operator` příkazu.</span><span class="sxs-lookup"><span data-stu-id="8db0b-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="8db0b-189">Můžete však použít, `AndAlso` Pokud splňujete následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="8db0b-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>

- <span data-ttu-id="8db0b-190">Definovali jste `And` stejné typy operandů, které chcete použít pro `AndAlso` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>

- <span data-ttu-id="8db0b-191">Vaše definice `And` vrátí stejný typ jako třída nebo struktura, na které jste ji definovali.</span><span class="sxs-lookup"><span data-stu-id="8db0b-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>

- <span data-ttu-id="8db0b-192">Definovali jste `IsFalse` operátor na třídě nebo struktuře, na které jste definovali `And` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>

<span data-ttu-id="8db0b-193">Podobně můžete použít, `OrElse` Pokud jste definovali `Or` na stejných operandech, s návratovým typem třídy nebo struktury a jste definovali `IsTrue` pro třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="8db0b-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>

## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="8db0b-194">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="8db0b-194">Widening and Narrowing Conversions</span></span>

<span data-ttu-id="8db0b-195">*Rozšiřující převod* v době běhu vždy proběhne úspěšně, zatímco *zužující převod* může v době běhu selhat.</span><span class="sxs-lookup"><span data-stu-id="8db0b-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="8db0b-196">Další informace najdete v tématu [rozšiřování a zúžení převodů](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="8db0b-196">For more information, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="8db0b-197">Pokud deklarujete postup převodu `Widening` , váš kód procedury nesmí generovat žádné chyby.</span><span class="sxs-lookup"><span data-stu-id="8db0b-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="8db0b-198">To znamená následující:</span><span class="sxs-lookup"><span data-stu-id="8db0b-198">This means the following:</span></span>

- <span data-ttu-id="8db0b-199">Vždy musí vracet platnou hodnotu typu `type` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-199">It must always return a valid value of type `type`.</span></span>

- <span data-ttu-id="8db0b-200">Musí zpracovat všechny možné výjimky a jiné chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="8db0b-200">It must handle all possible exceptions and other error conditions.</span></span>

- <span data-ttu-id="8db0b-201">Musí zpracovat jakékoli návratové chyby ze všech procedur, které volá.</span><span class="sxs-lookup"><span data-stu-id="8db0b-201">It must handle any error returns from any procedures it calls.</span></span>

<span data-ttu-id="8db0b-202">Pokud existuje možnost, že postup převodu nemusí být úspěšný nebo že může způsobit neošetřenou výjimku, musíte deklarovat, aby byl `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>

## <a name="example"></a><span data-ttu-id="8db0b-203">Příklad</span><span class="sxs-lookup"><span data-stu-id="8db0b-203">Example</span></span>

<span data-ttu-id="8db0b-204">Následující příklad kódu používá `Operator` příkaz k definování obrysu struktury, která obsahuje procedury operátoru pro `And` operátory,, a `Or` `IsFalse` `IsTrue` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="8db0b-205">`And`a `Or` každá z nich přijímá dva operandy typu `abc` a návratového typu `abc` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="8db0b-206">`IsFalse`a `IsTrue` každý z nich vezme jeden operand typu `abc` a vrátí `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="8db0b-207">Tyto definice umožňují, aby volající kód používal `And` , `AndAlso` , `Or` a `OrElse` s operandy typu `abc` .</span><span class="sxs-lookup"><span data-stu-id="8db0b-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a><span data-ttu-id="8db0b-208">Viz také</span><span class="sxs-lookup"><span data-stu-id="8db0b-208">See also</span></span>

- [<span data-ttu-id="8db0b-209">IsFalse – operátor</span><span class="sxs-lookup"><span data-stu-id="8db0b-209">IsFalse Operator</span></span>](../operators/isfalse-operator.md)
- [<span data-ttu-id="8db0b-210">IsTrue – operátor</span><span class="sxs-lookup"><span data-stu-id="8db0b-210">IsTrue Operator</span></span>](../operators/istrue-operator.md)
- [<span data-ttu-id="8db0b-211">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="8db0b-211">Widening</span></span>](../modifiers/widening.md)
- [<span data-ttu-id="8db0b-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="8db0b-212">Narrowing</span></span>](../modifiers/narrowing.md)
- [<span data-ttu-id="8db0b-213">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="8db0b-213">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="8db0b-214">Procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="8db0b-214">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="8db0b-215">Postupy: Definice operátoru</span><span class="sxs-lookup"><span data-stu-id="8db0b-215">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="8db0b-216">Postupy: Definice operátoru převodu</span><span class="sxs-lookup"><span data-stu-id="8db0b-216">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="8db0b-217">Postupy: Volání procedury operátoru</span><span class="sxs-lookup"><span data-stu-id="8db0b-217">How to: Call an Operator Procedure</span></span>](../../programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="8db0b-218">Postupy: Použití třídy, která definuje operátory</span><span class="sxs-lookup"><span data-stu-id="8db0b-218">How to: Use a Class that Defines Operators</span></span>](../../programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
